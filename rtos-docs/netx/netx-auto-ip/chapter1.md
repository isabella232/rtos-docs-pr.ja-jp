---
title: 第 1 章 - Azure RTOS NetX AutoIP の概要
description: Azure RTOS NetX AutoIP プロトコルは、ローカル ネットワーク上で IPv4 アドレスを動的に構成するために設計されたプロトコルです。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c26b4112814bb586e056246d68c2597d56df6085
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811666"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a>第 1 章 - Azure RTOS NetX AutoIP の概要
  
Azure RTOS NetX AutoIP プロトコルは、ローカル ネットワーク上で IPv4 アドレスを動的に構成するために設計されたプロトコルです。 AutoIP は、その IP アドレス自動割り当て機能を実行するために ARP 機能を利用する単純なプロトコルです。 AutoIP では、169.254.1.0 ～ 169.254.254.255 の範囲のアドレスを割り当てます。

## <a name="autoip-requirements"></a>AutoIP の要件

NetX AutoIP パッケージが正しく機能するには、NetX IP インスタンスが既に作成されている必要があります。 さらに、その同じ IP インスタンス上で ARP が有効になっている必要があります。 NetX AutoIP パッケージには、それ以上の要件はありません。

## <a name="autoip-constraints"></a>AutoIP の制約 

NetX AutoIP プロトコルでは、RFC3927 標準の要件を実装しています。 ただし、次の制約があります。

1. NetX DHCP が使用される場合は、DHCP スレッドを、NetX IP インスタンス スレッドと AutoIP スレッドの両方より高い優先度で作成する必要があります。
1. NetX AutoIP には、古い IP アドレスを引き続き使用するためのメカニズムは用意されていません。
1. IP アドレスが変更された場合、既存の TCP 接続をすべて切断し、それらを新しい IP アドレス上で再確立する処理はアプリケーションが担当します。

## <a name="autoip-protocol-implementation"></a>AutoIP プロトコルの実装

NetX AutoIP プロトコルでは、最初に 169.254.1.0 ～ 169.254.254.255 の AutoIP IPv4 アドレス範囲内のランダムなアドレスを選択します。 あるいは、***nx_auto_ip_start*** 関数に指定することにより、アプリケーションで開始 IP アドレスを強制することもできます。 これは、以前の実行である AutoIP アドレスが正常に使用されていた状況で役立ちます。

AutoIP アドレスが選択されると、NetX AutoIP では、その選択されたアドレスの一連の ARP プローブを送出します。 ARP プローブは、送信者アドレスが 0.0.0.0 に設定され、ターゲット アドレスが目的の AutoIP アドレスに設定されている ARP 要求メッセージで構成されます。 これらの一連の ARP プローブが送信されます (実際の数は、定義 NX_AUTO_IP_PROBE_NUM によって決定されます)。 別のネットワーク ノードがこのプローブに応答するか、または同じアドレスの同一のプローブを送信した場合は、新しい AutoIP アドレスが AutoIP IPv4 アドレス範囲内でランダムに選択され、プローブ処理が繰り返されます。

NX_AUTO_IP_PROBE_NUM 個のプローブが送信されても応答がなかった場合、NetX AutoIP では、選択されたアドレスの一連の ARP アナウンスを発行します。 ARP アナウンスは、ARP メッセージ内の送信者アドレスとターゲット アドレスの両方が選択された AutoIP アドレスに設定されている ARP 要求メッセージで構成されます。 定義 NX_AUTO_IP_ANNOUNCE_NUM に対応する一連の ARP アナウンス メッセージが送信されます。 別のネットワーク ノードがアナウンス メッセージに応答するか、または同じアドレスの同一のアナウンスを送信した場合は、新しい AutoIP アドレスが AutoIP IPv4 アドレス範囲内でランダムに選択され、プローブ処理が始めからやり直されます。

競合がまったく検出されずにプローブとアナウンスが完了すると、選択された AutoIP アドレスは有効と見なされ、関連付けられた IP インスタンスがこのアドレスに設定されます。

## <a name="autoip-address-change"></a>AutoIP アドレスの変更

先に説明したように、NetX AutoIP では、プローブ処理とアナウンス処理が成功した後に IP インスタンス アドレスを変更します。 このケースの監視はそれほど重要ではありません。 ただし、将来 AutoIP アドレスが変更される可能性があります。 潜在的な原因には、将来の AutoIP アドレスの競合や DHCP アドレス解決が含まれます。 これらの潜在的な状況を適切に処理するために、アプリケーションでは、次の NetX API を使用して IP アドレスのすべての変更を自身に通知する必要があります。

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

指定されている *ip_address_change_notify* 関数の処理では、NetX AutoIP プロセッサを再起動するか、またはその後 DHCP でその IP アドレスが解決された場合はそれを無効にする必要があります。 処理の例については、「*小規模システムの例*」セクションを参照してください。

## <a name="autoip-rfcs"></a>AutoIP RFC

NetX AutoIP は、RFC3927 および関連する RFC に準拠しています。