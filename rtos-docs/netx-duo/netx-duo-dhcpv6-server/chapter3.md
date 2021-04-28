---
title: 第 3 章 - Azure RTOS NetX Duo DHCPv6 サーバーの構成オプション
description: この章では、Azure RTOS NetX Duo DHCPv6 サーバーの構成オプションについて説明します。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30f6e1c657eb62ebec48d6bb8caafac320727146
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811819"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>第 3 章 - Azure RTOS NetX Duo DHCPv6 サーバーの構成オプション

NetX Duo DHCPv6 サーバー アプリケーションを作成するためのいくつかの構成オプションがあります。 次の一覧は、それぞれの詳細を示しています。
  
- **NX_DISABLE_ERROR_CHECKING** このオプションを使用すると、DHCPv6 エラー チェックが削除されます。 通常はアプリケーションがデバッグされたときに有効にします。  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** DHCPv6 スレッド スタックのサイズを定義します。 既定では、サイズは 4096 バイトであり、ほとんどの NetX Duo アプリケーションで十分な値です。

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** DHCPv6Server スレッドの優先順位を定義します。 これは、DHCPv6 サーバーの IP スレッド タスクの優先順位よりも低くする必要があります。 既定値は 2 です。

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** リース タイマー エントリ関数が ThreadX スケジューラによって呼び出されたときのタイマー間隔 (秒単位)。 エントリ関数では、すべてのクライアントのリース時間をタイマー間隔で増分するように、DHCPv6 サーバーのフラグが設定されます。 既定では、この値は 60 です。

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** セッション タイマー エントリ関数が ThreadX スケジューラによって呼び出されたときのタイマー間隔 (秒単位)。 エントリ関数では、すべてのアクティブなクライアント セッションの時間をタイマー間隔で増分するように、DHCPv6 サーバーのフラグを設定します。 既定では、この値は 3 です。

次の定義は、状態オプションのメッセージの種類とユーザーが構成可能なメッセージに適用されます。 状態オプションは、クライアント要求の結果を示します。

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"IA オプションが許可されています"*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"IA オプションが許可されていません - 使用可能なアドレスがありません"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"IA オプションが許可されていません - 無効なクライアント要求"*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"IA オプションが許可されていません - クライアントはリンクに存在しません"*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"IA オプションが許可されていません - クライアントではマルチキャストを使用する必要があります"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** "*IA オプションが許可されていません - 使用可能なアドレスがありません*"

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** ベンダーが割り当てた ID でサーバー DUID を作成します。 DUID の種類を NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED に設定する必要があります。

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** ベンダーが割り当てた ID の上限を設定します。 既定値は 48 です。

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** DUID のエンタープライズの種類をプライベート ベンダーの種類に設定します。

- **NX_DHCPV6_PACKET_WAIT_OPTION** サーバーの *nx_udp_socket_receive* 呼び出しの待機オプションを定義します。 これは、DHCPv6 サーバーが受信関数を呼び出したときに、パケットが既にエンキューされているように、NetX Duo からソケットに受信通知コールバックがあるので形式的なものです。 既定値は 1 秒 (1 * NX_IP_PERIODIC_RATE) です。

- **NX_DHCPV6_SERVER_DUID_TYPE** サーバーによってクライアントへのすべてのメッセージに含められるサーバー DUID の種類を定義します。 既定値はリンク レイヤー + 時間 (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME) です。

- **NX_DHCPV6_SERVER_HW_TYPE** DUID のリンク レイヤーおよびリンク レイヤー + 時間のオプションのハードウェアの種類を定義します。 既定値は NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET です。

- **NX_DHCPV6_PREFERENCE_VALUE** 0 - 255 の優先オプション値を定義します。この値が高いほど、同じ名前の DHCPv6 オプションで優先度が高くなります。 これにより、IP アドレスの割り当てに複数の DHCPv6 サーバーが使用可能な場合に、このサーバーの提示に対する優先度がクライアントに通知されます。 値が 255 の場合は、このサーバーを選択するようにクライアントに指示されます。 値が 0 の場合は、クライアントが自由に選択できることを示します。 既定値はゼロです。

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** クライアント レコードに保存できるクライアント要求のオプション要求の最大数を定義します。 既定値は 6 です。

- **NX_DHCPV6_DEFAULT_T1_TIME** クライアントで IP アドレスの更新を開始する必要があるときに、サーバーによってクライアントへのアドレスのリースに割り当てられる時間 (秒単位)。 既定値は 2000 秒です。

- **NX_DHCPV6_DEFAULT_T2_TIME** 更新が失敗したと推定され、クライアントで IP アドレスの再バインドを開始する必要があるときに、サーバーによってクライアントへのアドレスのリースに割り当てられる時間 (秒単位)。 既定値は 3000 秒です。

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** サーバーによって割り当てられる、割り当てられたクライアント IP アドレスのリースが非推奨になるまでの時間 (秒単位) を定義します。 既定値は 2 NX_DHCPV6_DEFAULT_T1_TIME です。

- **NX_DHCPV6_DEFAULT_VALID_TIME** サーバーによって割り当てられる、割り当てられたクライアント IP アドレスのリースが期限切れになるまでの時間 (秒単位) を定義します。 この時間が経過すると、クライアントの IP アドレスは無効になります。 既定値は 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME です。

- **NX_DHCPV6_STATUS_MESSAGE_MAX** 状態オプション メッセージ フィールドのサーバー メッセージの最大サイズを定義します。 既定値は 100 バイトです。

- **NX_DHCPV6_MAX_LEASES** サーバーの IP リース テーブルのサイズを定義します (たとえば、リースに使用できる IPv6 アドレスを格納できる最大数)。 既定では、この値は 100 です。

- **NX_DHCPV6_MAX_CLIENTS** サーバーのクライアント レコード テーブルのサイズを定義します (たとえば、格納できるクライアントの最大数)。この値は、NX_DHCPV6_MAX_LEASES 値以下である必要があります。 既定では、この値は 120 です。

- **NX_DHCPV6_PACKET_TIME_OUT** DHCPv6 サーバーでパケット割り当てを待機するときの待機オプションをタイマー刻みで定義します。 既定値は 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND です。

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** サーバー パケット プールに対するパケット割り当て呼び出しの待機オプションを定義します。 既定値は (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) または 3 秒です。

- **NX_DHCPV6_PACKET_SIZE** サーバー パケット プールのパケットのパケット ペイロードを定義します。 既定値は 500 バイトです。

- **NX_DHCPV6_PACKET_POOL_SIZE** サーバーで DHCPv6 メッセージを送信するために割り当てるパケットのサーバー パケット プールのサイズを定義します。既定値は (10 * NX_DHCPV6_PACKET_SIZE) です。

- **NX_DHCPV6_TYPE_OF_SERVICE** UDP パケット転送用のサービスの種類を定義します。 既定では、この値は NX_IP_NORMAL です。

- **NX_DHCPV6_FRAGMENT_OPTION** サーバー ソケットの断片化オプションを定義します。 既定値は NX_DON’T_FRAGMENT です

- **NX_DHCPV6_TIME_TO_LIVE** パケットが破棄される前に、サーバーからの DHCPv6 パケットが通過できるルーターの数を指定します。 既定値は 0x80 に設定されます。

- **NX_DHCPV6_QUEUE_DEPTH** NetX Duo でパケットが破棄される前に、サーバーの UDP ソケット受信キューに保持されるパケットの数を指定します。