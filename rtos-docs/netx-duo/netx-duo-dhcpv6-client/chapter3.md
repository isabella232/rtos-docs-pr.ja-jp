---
title: 第 3 章 - Azure RTOS NetX Duo DHCPv6 の構成オプション
description: Azure RTOS NetX Duo DHCPv6 を構築するための構成オプションがいくつかあります。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810904"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="d584d-103">第 3 章 - Azure RTOS NetX Duo DHCPv6 の構成オプション</span><span class="sxs-lookup"><span data-stu-id="d584d-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="d584d-104">Azure RTOS NetX Duo DHCPv6 を構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d584d-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="d584d-105">次の一覧で、それぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="d584d-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="d584d-106">**NX_DHCPV6_THREAD_PRIORITY**: クライアント スレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="d584d-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="d584d-107">既定では、この値は、クライアント スレッドを優先度 2 で実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d584d-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="d584d-108">**NX_DHCPV6_MUTEX_WAIT**: DHCPv6 クライアント ミューテックスの排他ロックを取得するためのタイムアウト オプション。</span><span class="sxs-lookup"><span data-stu-id="d584d-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="d584d-109">既定値は TX_WAIT_FOREVER です。</span><span class="sxs-lookup"><span data-stu-id="d584d-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="d584d-110">**NX_DHCPV6_TICKS_PER_SECOND**: 秒に対するティックの比率。</span><span class="sxs-lookup"><span data-stu-id="d584d-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="d584d-111">これはプロセッサに依存します。</span><span class="sxs-lookup"><span data-stu-id="d584d-111">This is processor dependent.</span></span> <span data-ttu-id="d584d-112">既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-112">The default value is 100.</span></span>

- <span data-ttu-id="d584d-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**: 現在の IP アドレスがクライアントに割り当てられた時間の長さを IP 有効期間タイマーが更新する時間間隔 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="d584d-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="d584d-114">既定では、この値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-114">By default, this value is 1.</span></span>

- <span data-ttu-id="d584d-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**: セッション中にクライアントがサーバーと通信している時間の長さをセッション タイマーが更新する時間間隔 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="d584d-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="d584d-116">既定では、この値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-116">By default, this value is 1.</span></span>

- <span data-ttu-id="d584d-117">**NX_DHCPV6_MAX_IA_ADDRESS**: クライアント レコードに追加できる IA アドレスの最大数。</span><span class="sxs-lookup"><span data-stu-id="d584d-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="d584d-118">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-118">The default value is 1.</span></span> 

- <span data-ttu-id="d584d-119">**NX_DHCPV6_NUM_DNS_SERVERS**: クライアント レコードに格納する DNS サーバーの数。</span><span class="sxs-lookup"><span data-stu-id="d584d-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="d584d-120">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-120">The default value is 2.</span></span>

- <span data-ttu-id="d584d-121">**NX_DHCPV6_NUM_TIME_SERVERS**: クライアント レコードに格納するタイム サーバーの数。</span><span class="sxs-lookup"><span data-stu-id="d584d-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="d584d-122">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-122">The default value is 1.</span></span>

- <span data-ttu-id="d584d-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**: クライアントのネットワーク ドメイン名を保持するための、クライアント レコード内のバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="d584d-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="d584d-124">既定値は 30 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-124">The default value is 30.</span></span>

- <span data-ttu-id="d584d-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**: クライアントのタイム ゾーン名を保持するための、クライアント レコード内のバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="d584d-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="d584d-126">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-126">The default value is 10.</span></span>

- <span data-ttu-id="d584d-127">**NX_DHCPV6_MAX_MESSAGE_SIZE**: サーバーの応答でオプションの状態メッセージを保持するための、クライアント レコード内のバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="d584d-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="d584d-128">既定値は 100 バイトです。</span><span class="sxs-lookup"><span data-stu-id="d584d-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="d584d-129">**NX_DHCPV6_PACKET_TIME_OUT**: クライアント パケット プールからパケットを割り当てられるまでのタイムアウト (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="d584d-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="d584d-130">既定値は 3 秒です。</span><span class="sxs-lookup"><span data-stu-id="d584d-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="d584d-131">**NX_DHCPV6_TYPE_OF_SERVICE**: これは、DHCPv6 クライアント ソケットからの UDP パケット転送用のサービスの種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="d584d-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="d584d-132">既定値は、**NX_IP_NORMAL** です。</span><span class="sxs-lookup"><span data-stu-id="d584d-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="d584d-133">**NX_DHCPV6_TIME_TO_LIVE**: パケットが破棄される前に、クライアント パケットがネットワーク ルーターによって転送される回数。</span><span class="sxs-lookup"><span data-stu-id="d584d-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="d584d-134">既定値は 0x80 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-134">The default value is 0x80.</span></span>

- <span data-ttu-id="d584d-135">**NX_DHCPV6_QUEUE_DEPTH**: NetX Duo でパケットが破棄される前に、クライアントの UDP ソケット受信キューに保持されるパケットの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d584d-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="d584d-136">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="d584d-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="d584d-137">DHCPv6 メッセージの送信</span><span class="sxs-lookup"><span data-stu-id="d584d-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="d584d-138">DHCPv6 メッセージ転送でパラメーターを設定するための DHCPv6 クライアント オプションのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="d584d-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="d584d-139">次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d584d-139">These are:</span></span> 

  - <span data-ttu-id="d584d-140">初期タイムアウト</span><span class="sxs-lookup"><span data-stu-id="d584d-140">initial timeout</span></span>

  - <span data-ttu-id="d584d-141">最初の転送の最大遅延</span><span class="sxs-lookup"><span data-stu-id="d584d-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="d584d-142">最大再送信タイムアウト</span><span class="sxs-lookup"><span data-stu-id="d584d-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="d584d-143">再送信の最大数</span><span class="sxs-lookup"><span data-stu-id="d584d-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="d584d-144">サーバー応答を待機する最大期間</span><span class="sxs-lookup"><span data-stu-id="d584d-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="d584d-145">これらのパラメーターは、各 DHCPv6 クライアント メッセージに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d584d-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="d584d-146">SOLICIT</span><span class="sxs-lookup"><span data-stu-id="d584d-146">SOLICIT</span></span>

- <span data-ttu-id="d584d-147">REQUEST</span><span class="sxs-lookup"><span data-stu-id="d584d-147">REQUEST</span></span>

- <span data-ttu-id="d584d-148">RENEW</span><span class="sxs-lookup"><span data-stu-id="d584d-148">RENEW</span></span>

- <span data-ttu-id="d584d-149">REBIND</span><span class="sxs-lookup"><span data-stu-id="d584d-149">REBIND</span></span>

- <span data-ttu-id="d584d-150">RELEASE</span><span class="sxs-lookup"><span data-stu-id="d584d-150">RELEASE</span></span>

- <span data-ttu-id="d584d-151">DECLINE</span><span class="sxs-lookup"><span data-stu-id="d584d-151">DECLINE</span></span>

- <span data-ttu-id="d584d-152">CONFIRM</span><span class="sxs-lookup"><span data-stu-id="d584d-152">CONFIRM</span></span>

- <span data-ttu-id="d584d-153">INFORM</span><span class="sxs-lookup"><span data-stu-id="d584d-153">INFORM</span></span>

<span data-ttu-id="d584d-154">これらの構成可能なオプションとその既定値の完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d584d-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="d584d-155">values:</span><span class="sxs-lookup"><span data-stu-id="d584d-155">values:</span></span>

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

<span data-ttu-id="d584d-156">再送信タイムアウトが制限されないようにするには、メッセージの再送信回数を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d584d-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="d584d-157">DHCPv6 クライアント メッセージが再送信される回数 (再試行) に制限がない場合は、メッセージの再送信回数を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d584d-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="d584d-158">タイムアウトまたは再試行の回数に関係なく、IPv6 アドレスは有効期間が終了すると IP アドレス テーブルから削除され、クライアントによる使用はできなくなります。</span><span class="sxs-lookup"><span data-stu-id="d584d-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="d584d-159">NetX Duo DHCPv6 クライアントでは、新しい IPv6 アドレスを要求する SOLICIT メッセージの送信が自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="d584d-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>