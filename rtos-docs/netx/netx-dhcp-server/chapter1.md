---
title: 第 1 章 - Azure RTOS NetX DHCP サーバーの概要
description: アプリケーションでは、IP アドレスを動的に要求して取得するために、Azure RTOS NetX DHCP サーバーとの通信が確立されます。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 17438a20ad3da64c88c3d6bb19a4887c2c6e354e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811609"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-server"></a>第 1 章 - Azure RTOS NetX DHCP サーバーの概要

NetX では、アプリケーションの IP アドレスは、*nx_ip_create* サービス呼び出しに対して指定されるパラメーターの 1 つです。 アプリケーションによって IP アドレスが静的に、またはユーザーの構成によって認識されている場合、IP アドレスを指定しても問題はありません。 ただし、アプリケーションで IP アドレスを認識していないか関知していない場合もあります。 そのような場合は、*nx_ip_create* 関数にゼロの IP アドレスを指定する必要があります。アプリケーションによって、IP アドレスを動的に要求して取得するために、Azure RTOS NetX DHCP サーバーとの通信が確立されます。

## <a name="dynamic-ip-address-assignment"></a>動的な IP アドレスの割り当て

ネットワークから動的な IP アドレスを取得するために使用される基本サービスは、逆アドレス解決プロトコル (RARP) です。 このプロトコルは ARP に似ていますが、別のネットワーク ノードの MAC アドレスを見つけるのではなく、自身の IP アドレスを取得するように設計されています。 低レベルの RARP メッセージは、ローカル ネットワーク上でブロードキャストされます。RARP 応答 (動的に割り当てられた IP アドレスを含む) に応答するのはネットワーク上のサーバーの責任です。

RARP では IP アドレスを動的に割り当てるためのサービスが提供されますが、いくつかの短所があります。 最も明白な欠点は、RARP では IP アドレスの動的割り当てのみが提供されることです。 ほとんどの場合、デバイスがネットワークに適切に参加するためには、さらに情報が必要となります。 IP アドレスに加えて、ほとんどのデバイスではネットワーク マスクとゲートウェイ IP アドレスが必要です。 DNS サーバーの IP アドレスとその他のネットワーク情報が必要な場合もあります。 RARP には、この情報を提供する機能がありません。

## <a name="rarp-alternatives"></a>RARP の代替

RARP の欠点を克服するために、研究者によって、ブートストラップ プロトコル (BOOTP) と呼ばれるより包括的な IP アドレス割り当てメカニズムが開発されました。 このプロトコルでは、IP アドレスを動的に割り当てることができ、追加の重要なネットワーク情報も提供されます。 ただし、BOOTP には、静的なネットワーク構成用に設計されているという欠点があります。 すばやい、または自動のアドレス割り当ては許可されません。

これが、動的ホスト構成プロトコル (DHCP) が非常に便利である理由です。 DHCP は、BOOTP の基本的な機能を拡張するように設計されており、完全に自動化された IP サーバーの割り当てと、指定した期間にわたって IP アドレスをクライアントに "リース" することによる完全に動的な IP アドレスの割り当ての機能が含まれています。 DHCP は、BOOTP のように静的な方法で IP アドレスを割り当てるように構成することもできます。

## <a name="dhcp-messages"></a>DHCP のメッセージ

DHCP では BOOTP の機能が大幅に拡張されていますが、BOOTP と同じメッセージ形式が使用され、BOOTP と同じベンダー オプションがサポートされます。 この機能を実行するために、DHCP では次の 7 つの新しい DHCP 固有のオプションが導入されています。

| オプション     | 値 | 出発地                |
| ---------- | ----- | --------------------- |
| DISCOVER   | (1)   | (DHCP クライアントによって送信されます) |
| OFFER      | (2)   | (DHCP サーバーによって送信されます) |
| 要求    | (3)   | (DHCP クライアントによって送信されます) |
| DECLINE    | (4)   | (DHCP クライアントによって送信されます) |
| ACK        | (5)   | (DHCP サーバーによって送信されます) |
| NACK       | (6)   | (DHCP サーバーによって送信されます) |
| RELEASE    | (7)   | (DHCP クライアントによって送信されます) |
| INFORM     | (8)   | (DHCP クライアントによって送信されます) |
| FORCERENEW | (9)   | (DHCP クライアントによって送信されます) |

## <a name="dhcp-communication"></a>DHCP の通信

DHCP サーバーにより、UDP プロトコルを利用して DHCP クライアント要求の受信と応答の送信が行われます。 IP アドレスが提供される前に、DHCP 情報を運ぶ UDP メッセージが、IP ブロードキャスト アドレス 255.255.255.255 を利用して送受信されます。 ただし、クライアントによって DHCP サーバーのアドレスが認識されている場合は、ユニキャスト メッセージを使用して DHCP メッセージを送信することができます。

## <a name="dhcp-server-state-machine"></a>DHCP サーバーのステート マシン

DHCP サーバーは、*nx_dhcp_server_create* の処理中に作成される内部 DHCP スレッドによって処理される 2 ステップのステート マシンとして実装されます。 DHCP サーバーの主な状態は、1) DHCP クライアントからの DISCOVER メッセージの受信と 2) REQUEST メッセージの受信です。

対応する DHCP クライアントの状態を次に示します。

- **NX_DHCP_STATE_BOOT**: 以前の IP アドレスから開始します
- **NX_DHCP_STATE_INIT**: 以前の IP アドレス値を使用せずに開始します
- **NX_DHCP_STATE_SELECTING**: 任意の DHCP サーバーからの応答を待機しています
- **NX_DHCP_STATE_REQUESTING**: DHCP サーバーが特定され、IP アドレス要求が送信されました
- **NX_DHCP_STATE_BOUND**: DHCP による IP アドレスのリースが確立されました
- **NX_DHCP_STATE_RENEWING**: DHCP による IP アドレスのリースの更新の時間が経過し、更新が要求されました
- **NX_DHCP_STATE_REBINDING**: DHCP による IP アドレスのリースの再バインドの時間が経過し、更新が要求されました
- **NX_DHCP_STATE_FORCERENEW**: DHCP による IP アドレスのリースが確立され、サーバーまたはアプリケーションによる更新が強制されます
- **NX_DHCP_STATE_FAILED**: サーバーが見つからなかったか、サーバーからの応答がありませんでした

## <a name="dhcp-additional-parameters"></a>DHCP の追加パラメーター

NetX DHCP サーバーには、オプション パラメーターの既定の一覧があります。これは、*nx_dhcp_server.h* 内の構成可能オプション NX_DHCP_DEFAULT_SERVER_OPTION_LIST で設定され、DHCP クライアントに共通/重要なネットワーク構成パラメーター (ルーターまたはゲートウェイのアドレスや DNS クライアントの DNS サーバーなど) を提供します。

## <a name="dhcp-rfcs"></a>DHCP RFC

NetX DHCP サーバーは、RFC2132、RFC2131、および関連する RFC に準拠しています。
