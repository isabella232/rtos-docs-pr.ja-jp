---
title: 第 3 章 - Azure RTOS NetX Duo DHCPv6 の構成オプション
description: Azure RTOS NetX Duo DHCPv6 を構築するための構成オプションがいくつかあります。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 129d1421215452448b1de4626fdeda530a5466bd63ed0c758676c3ad60f9d6fb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782423"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>第 3 章 - Azure RTOS NetX Duo DHCPv6 の構成オプション

Azure RTOS NetX Duo DHCPv6 を構築するための構成オプションがいくつかあります。 次の一覧で、それぞれについて詳しく説明します。  
  
  
- **NX_DHCPV6_THREAD_PRIORITY**: クライアント スレッドの優先順位。 既定では、この値は、クライアント スレッドを優先度 2 で実行することを指定します。

- **NX_DHCPV6_MUTEX_WAIT**: DHCPv6 クライアント ミューテックスの排他ロックを取得するためのタイムアウト オプション。 既定値は TX_WAIT_FOREVER です。

- **NX_DHCPV6_TICKS_PER_SECOND**: 秒に対するティックの比率。 これはプロセッサに依存します。 既定値は 100 です。

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**: 現在の IP アドレスがクライアントに割り当てられた時間の長さを IP 有効期間タイマーが更新する時間間隔 (秒単位)。 既定では、この値は 1 です。

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**: セッション中にクライアントがサーバーと通信している時間の長さをセッション タイマーが更新する時間間隔 (秒単位)。 既定では、この値は 1 です。

- **NX_DHCPV6_MAX_IA_ADDRESS**: クライアント レコードに追加できる IA アドレスの最大数。 既定値は 1 です。 

- **NX_DHCPV6_NUM_DNS_SERVERS**: クライアント レコードに格納する DNS サーバーの数。 既定値は 2 です。

- **NX_DHCPV6_NUM_TIME_SERVERS**: クライアント レコードに格納するタイム サーバーの数。 既定値は 1 です。

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**: クライアントのネットワーク ドメイン名を保持するための、クライアント レコード内のバッファーのサイズ。 既定値は 30 です。

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**: クライアントのタイム ゾーン名を保持するための、クライアント レコード内のバッファーのサイズ。 既定値は 10 です。

- **NX_DHCPV6_MAX_MESSAGE_SIZE**: サーバーの応答でオプションの状態メッセージを保持するための、クライアント レコード内のバッファーのサイズ。 既定値は 100 バイトです。

- **NX_DHCPV6_PACKET_TIME_OUT**: クライアント パケット プールからパケットを割り当てられるまでのタイムアウト (秒単位)。 既定値は 3 秒です。

- **NX_DHCPV6_TYPE_OF_SERVICE**: これは、DHCPv6 クライアント ソケットからの UDP パケット転送用のサービスの種類を定義します。 既定値は、**NX_IP_NORMAL** です。

- **NX_DHCPV6_TIME_TO_LIVE**: パケットが破棄される前に、クライアント パケットがネットワーク ルーターによって転送される回数。 既定値は 0x80 です。

- **NX_DHCPV6_QUEUE_DEPTH**: NetX Duo でパケットが破棄される前に、クライアントの UDP ソケット受信キューに保持されるパケットの数を指定します。 既定値は 5 です。

## <a name="dhcpv6-message-transmission"></a>DHCPv6 メッセージの送信

DHCPv6 メッセージ転送でパラメーターを設定するための DHCPv6 クライアント オプションのセットがあります。 次のとおりです。 

  - 初期タイムアウト

  - 最初の転送の最大遅延

  - 最大再送信タイムアウト 

  - 再送信の最大数 

  - サーバー応答を待機する最大期間

これらのパラメーターは、各 DHCPv6 クライアント メッセージに適用されます。

- SOLICIT

- REQUEST

- RENEW

- REBIND

- RELEASE

- DECLINE

- CONFIRM

- INFORM

これらの構成可能なオプションとその既定値の完全な一覧を次に示します。 

values:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

再送信タイムアウトが制限されないようにするには、メッセージの再送信回数を 0 に設定します。 DHCPv6 クライアント メッセージが再送信される回数 (再試行) に制限がない場合は、メッセージの再送信回数を 0 に設定します。

> [!NOTE]
> タイムアウトまたは再試行の回数に関係なく、IPv6 アドレスは有効期間が終了すると IP アドレス テーブルから削除され、クライアントによる使用はできなくなります。 NetX Duo DHCPv6 クライアントでは、新しい IPv6 アドレスを要求する SOLICIT メッセージの送信が自動的に開始されます。