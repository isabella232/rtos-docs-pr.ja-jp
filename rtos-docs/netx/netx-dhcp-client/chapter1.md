---
title: 第 1 章 - Azure RTOS NetX DHCP クライアントの概要
description: NetX では、アプリケーションの IP アドレスは、nx_ip_create サービス呼び出しに対して指定されるパラメーターの 1 つです。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 44eb764c84a15a1bc96cf94bcbc8f81be7b41eef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811621"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a>第 1 章 - Azure RTOS NetX DHCP クライアントの概要

NetX では、アプリケーションの IP アドレスは、*nx_ip_create* サービス呼び出しに対して指定されるパラメーターの 1 つです。 アプリケーションで IP アドレスが静的に、またはユーザーの構成によって認識されている場合、IP アドレスを指定しても問題はありません。 ただし、アプリケーションで IP アドレスを認識していない場合、または関知しない場合もあります。 そのような場合は、*nx_ip_create* 関数にゼロの IP アドレスを指定し、Azure RTOS DHCP クライアント プロトコルを使用して IP アドレスを動的に取得する必要があります。

## <a name="dynamic-ip-address-assignment"></a>動的な IP アドレスの割り当て

ネットワークから動的な IP アドレスを取得するために使用される基本サービスは、逆アドレス解決プロトコル (RARP) です。 このプロトコルは ARP に似ていますが、別のネットワーク ノードの MAC アドレスを見つけるのではなく、自身の IP アドレスを取得するように設計されています。 低レベルの RARP メッセージはローカル ネットワークでブロードキャストされます。ネットワーク上のサーバーが、RARP 応答 (動的に割り当てられた IP アドレスを含む) に応答する役割を担います。

RARP では IP アドレスを動的に割り当てるためのサービスが提供されますが、いくつかの短所があります。 最も明白な欠点は、RARP では IP アドレスの動的割り当てのみが提供されることです。 ほとんどの場合、デバイスがネットワークに適切に参加するためには、さらに情報が必要となります。 IP アドレスに加えて、ほとんどのデバイスではネットワーク マスクとゲートウェイ IP アドレスが必要です。 DNS サーバーの IP アドレスとその他のネットワーク情報が必要な場合もあります。 RARP には、この情報を提供する機能がありません。

## <a name="rarp-alternatives"></a>RARP の代替

RARP の欠点を克服するために、研究者によって、ブートストラップ プロトコル (BOOTP) と呼ばれるより包括的な IP アドレス割り当てメカニズムが開発されました。 このプロトコルでは、IP アドレスを動的に割り当てることができ、追加の重要なネットワーク情報も提供されます。 ただし、BOOTP には、静的なネットワーク構成用に設計されているという欠点があります。 素早いアドレス割り当てや自動アドレス割り当ては許可されません。

これが動的ホスト構成プロトコル (DHCP) が非常に便利である点です。 DHCP は、BOOTP の基本的な機能を拡張するように設計されており、完全に自動化された IP サーバーの割り当てと、指定した期間にわたって IP アドレスをクライアントに "リース" することによる完全に動的な IP アドレスの割り当てが含まれています。 DHCP は、BOOTP のように静的な方法で IP アドレスを割り当てるように構成することもできます。

## <a name="dhcp-messages"></a>DHCP のメッセージ

DHCP では BOOTP の機能が大幅に拡張されていますが、BOOTP と同じメッセージ形式が使用され、BOOTP と同じベンダー オプションがサポートされます。 この機能を実行するために、DHCP では次の 7 つの新しい DHCP 固有のオプションが導入されています。

- DISCOVER (1) (DHCP クライアントによって送信されます)

- OFFER (2) (DHCP サーバーによって送信されます)

- REQUEST (3) (DHCP クライアントによって送信されます)

- DECLINE (4) (DHCP クライアントによって送信されます)

- ACK (5) (DHCP サーバーによって送信されます)

- NACK (6) (DHCP サーバーによって送信されます)

- RELEASE (7) (DHCP クライアントによって送信されます)

- INFORM (8) (DHCP クライアントによって送信されます)

- FORCERENEW (9) (DHCP クライアントによって送信されます)

## <a name="dhcp-communication"></a>DHCP による通信

DHCP では UDP プロトコルを利用して、要求とフィールドの応答が送信されます。 IP アドレスが提供される前に、DHCP 情報を運ぶ UDP メッセージが、IP ブロードキャスト アドレス 255.255.255.255 を利用して送受信されます。

## <a name="dhcp-client-state-machine"></a>DHCP クライアントのステート マシン

DHCP クライアントは、ステート マシンとして実装されます。 このステート マシンは、*nx_dhcp_create* の処理中に作成される内部 DHCP スレッドによって処理されます。 DHCP クライアントの主な状態は次のとおりです。


- **NX_DHCP_STATE_BOOT** 以前の IP アドレスから開始します

- **NX_DHCP_STATE_INIT** 以前の IP アドレス値を使用せずに開始します

- **NX_DHCP_STATE_SELECTING** 任意の DHCP サーバーからの応答を待機しています

- **NX_DHCP_STATE_REQUESTING** DHCP サーバーが特定され、IP アドレス要求を送信しました

- **NX_DHCP_STATE_BOUND** DHCP による IP アドレスのリースが確立されました

- **NX_DHCP_STATE_RENEWING** DHCP による IP アドレスのリースの更新時間が経過し、更新を要求されました

- **NX_DHCP_STATE_REBINDING** DHCP による IP アドレスのリースの再バインドの時間が経過し、更新を要求されました

- **NX_DHCP_STATE_FORCERENEW** DHCP による IP アドレスのリースが確立されました。サーバー (現在はサポートされていません) またはアプリケーションによって nx_dhcp_force_renew が呼び出されることによって更新が強制されます

- **NX_DHCP_STATE_ADDRESS_PROBING** DHCP による IP アドレスのプローブ。IP アドレスの競合を検出するために、ARP プローブが送信されます。

## <a name="dhcp-client-multiple-interface-support"></a>DHCP クライアントでの複数インターフェイスのサポート

DHCP クライアントは、1 つのネットワーク インターフェイスでのみ実行するように以前は実装されていました。 既定の動作では、DHCP クライアントはプライマリ インターフェイスで実行されていました (現在でも)。 *nx_dhcp_set_interface_index* を呼び出すことによって、アプリケーションでプライマリ インターフェイスではなく、セカンダリ ネットワーク インターフェイスで DHCP を実行することができました (現在でも)。

DHCP を複数のインターフェイスで並列的に実行することがサポートされるようになりました。 複数の物理インターフェイスで DHCP クライアントを同時に実行する方法の詳細については、第 2 章の **複数のインターフェイスに同時に存在する DHCP クライアント** に関するページを参照してください。

## <a name="dhcp-user-request"></a>DHCP でのユーザー要求

DHCP サーバーによって IP アドレスが付与されたら、DHCP クライアントの処理では、*nx_dhcp_user_option_request* サービスを使用して、追加のパラメーターを要求できます (一度に 1 つずつ)。

## <a name="dhcp-client-socket-queue"></a>DHCP クライアントのソケット キュー 

DHCP クライアントでは、サーバーが応答するのを待機している間、他の DHCP クライアントに向けた DHCP サーバーからのブロードキャスト パケットがそのソケット受信キューから自動的にクリアされます。 ビジー状態のネットワークでは、そうしないと、そのクライアントに向けられたパケットが破棄される可能性があります。

## <a name="dhcp-rfcs"></a>DHCP の RFC

NetX DHCP は、RFC2132、RFC2131、関連する RFC に準拠しています。

