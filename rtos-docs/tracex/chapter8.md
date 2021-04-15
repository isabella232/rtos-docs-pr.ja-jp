---
title: 第 8 章 - Azure RTOS NetX トレース イベント
description: この章では、Azure RTOS NetX イベントについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813169"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="26a46-103">第 8 章 - Azure RTOS NetX トレース イベント</span><span class="sxs-lookup"><span data-stu-id="26a46-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="26a46-104">この章では、Azure RTOS NetX イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="26a46-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="26a46-105">イベントとアイコンの一覧</span><span class="sxs-lookup"><span data-stu-id="26a46-105">List of Events and Icons</span></span>

<span data-ttu-id="26a46-106">次に、TraceX によって表示される NetX イベントの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="26a46-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="26a46-107">アイコン</span><span class="sxs-lookup"><span data-stu-id="26a46-107">Icon</span></span>                                           | <span data-ttu-id="26a46-108">意味</span><span class="sxs-lookup"><span data-stu-id="26a46-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![内部 A R P 要求の受信アイコン](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="26a46-110">内部 ARP 要求の受信</span><span class="sxs-lookup"><span data-stu-id="26a46-110">Internal ARP Request Receive</span></span> |
| ![内部 A R P 要求の送信アイコン](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="26a46-112">内部 ARP 要求の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-112">Internal ARP Request Send</span></span> |
| ![内部 A R P 応答の受信アイコン](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="26a46-114">内部 ARP 応答の受信</span><span class="sxs-lookup"><span data-stu-id="26a46-114">Internal ARP Response Receive</span></span> |
| ![内部 A R P 応答の送信アイコン](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="26a46-116">内部 ARP 応答の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-116">Internal ARP Response Send</span></span> |
| ![内部 I C M P 受信アイコン](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="26a46-118">内部 ICMP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-118">Internal ICMP Receive</span></span> |
| ![内部 I C M P 送信アイコン](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="26a46-120">内部 ICMP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-120">Internal ICMP Send</span></span> |
| ![内部 NetX I G M P 受信アイコン](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="26a46-122">内部 NetX IGMP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-122">Internal NetX IGMP Receive</span></span> |
| ![内部 I P 受信アイコン](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="26a46-124">内部 IP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-124">Internal IP Receive</span></span> |
| ![内部 I P 送信アイコン](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="26a46-126">内部 IP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-126">Internal IP Send</span></span> |
| ![内部 T C P データ受信アイコン](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="26a46-128">内部 TCP データ受信</span><span class="sxs-lookup"><span data-stu-id="26a46-128">Internal TCP Data Receive</span></span> |
| ![内部 T C P データ送信アイコン](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="26a46-130">内部 TCP データ送信</span><span class="sxs-lookup"><span data-stu-id="26a46-130">Internal TCP Data Send</span></span> |
| ![内部 T C P FIN 受信アイコン](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="26a46-132">内部 TCP FIN 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-132">Internal TCP FIN Receive</span></span> |
| ![内部 T C P F I N 送信アイコン](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="26a46-134">内部 TCP FIN 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-134">Internal TCP FIN Send</span></span> |
| ![内部 T C P R S T 受信アイコン](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="26a46-136">内部 TCP RST 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-136">Internal TCP RST Receive</span></span> |
| ![内部 T C P R S T 送信アイコン](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="26a46-138">内部 TCP RST 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-138">Internal TCP RST Send</span></span> |
| ![内部 T C P S Y N 受信アイコン](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="26a46-140">内部 TCP SYN 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-140">Internal TCP SYN Receive</span></span> |
| ![内部 T C P S Y N 送信アイコン](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="26a46-142">内部 TCP SYN 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-142">Internal TCP SYN Send</span></span> |
| ![内部 U D P 受信アイコン](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="26a46-144">内部 UDP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-144">Internal UDP Receive</span></span> |
| ![内部 U D P 送信アイコン](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="26a46-146">内部 UDP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-146">Internal UDP Send</span></span> |
| ![内部 R A R P 受信アイコン](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="26a46-148">内部 RARP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-148">Internal RARP Receive</span></span> |
| ![内部 R A R P 送信アイコン](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="26a46-150">内部 RARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-150">Internal RARP Send</span></span> |
| ![内部 T C P 再試行アイコン](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="26a46-152">内部 TCP 再試行</span><span class="sxs-lookup"><span data-stu-id="26a46-152">Internal TCP Retry</span></span> |
| ![内部 T C P 状態の変更アイコン](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="26a46-154">内部 TCP 状態の変更</span><span class="sxs-lookup"><span data-stu-id="26a46-154">Internal TCP State Change</span></span> |
| ![内部 I / O ドライバーのパケット送信アイコン](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="26a46-156">内部 I/O ドライバーのパケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-156">Internal I/O Driver Packet Send</span></span> |
| ![icon](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="26a46-158">内部 I/O ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="26a46-158">Internal I/O Driver Initialize</span></span> |
| ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="26a46-160">内部 I/O ドライバー リンクの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-160">Internal I/O Driver Link Enable</span></span> |
| ![内部 I / O ドライバー リンクの無効化アイコン](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="26a46-162">内部 I/O ドライバー リンクの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-162">Internal I/O Driver Link Disable</span></span> |
| ![内部 I / O ドライバーのパケット ブロードキャスト アイコン](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="26a46-164">内部 I/O ドライバーのパケット ブロードキャスト</span><span class="sxs-lookup"><span data-stu-id="26a46-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![内部 I / O ドライバーの ARP 送信アイコン](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="26a46-166">内部 I/O ドライバーの ARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-166">Internal I/O Driver ARP Send</span></span> |
| ![内部 I / O ドライバーの ARP 応答の送信アイコン](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="26a46-168">内部 I/O ドライバーの ARP 応答の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-168">Internal I/O Driver ARP Response Send</span></span> |
| ![内部 I / O ドライバーの RARP 送信アイコン](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="26a46-170">内部 I/O ドライバーの RARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-170">Internal I/O Driver RARP Send</span></span> |
| ![内部 I / O ドライバーのマルチキャスト参加アイコン](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="26a46-172">内部 I/O ドライバーのマルチキャスト参加</span><span class="sxs-lookup"><span data-stu-id="26a46-172">Internal I/O Driver Multicast Join</span></span> |
| ![内部 I / O ドライバーのマルチキャスト離脱アイコン](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="26a46-174">内部 I/O ドライバーのマルチキャスト離脱</span><span class="sxs-lookup"><span data-stu-id="26a46-174">Internal I/O Driver Multicast Leave</span></span> |
| ![内部 I / O ドライバーの状態取得アイコン](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="26a46-176">内部 I/O ドライバーの状態取得</span><span class="sxs-lookup"><span data-stu-id="26a46-176">Internal I/O Driver Get Status</span></span> |
| ![内部 I / O ドライバーの速度取得アイコン](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="26a46-178">内部 I/O ドライバーの速度取得</span><span class="sxs-lookup"><span data-stu-id="26a46-178">Internal I/O Driver Get Speed</span></span> |
| ![内部 I / O ドライバーの二重タイプ取得アイコン](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="26a46-180">内部 I/O ドライバーの二重タイプ取得</span><span class="sxs-lookup"><span data-stu-id="26a46-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![内部 I / O ドライバーのエラー数取得アイコン](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="26a46-182">内部 I/O ドライバーのエラー数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-182">Internal I/O Driver Get Error Count</span></span> |
| ![内部 I / O ドライバーの RX 数取得アイコン](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="26a46-184">内部 I/O ドライバーの RX 数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-184">Internal I/O Driver Get RX Count</span></span> |
| ![内部 I / O ドライバーの TX 数取得アイコン](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="26a46-186">内部 I/O ドライバーの TX 数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-186">Internal I/O Driver Get TX Count</span></span> |
| ![内部 I / O ドライバーの割り当てエラー数の取得アイコン](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="26a46-188">内部 I/O ドライバーの割り当てエラー数の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="26a46-190">内部 I/O ドライバーの初期化解除</span><span class="sxs-lookup"><span data-stu-id="26a46-190">Internal I/O Driver Un-initialize</span></span> |
| ![内部 I / O ドライバーの遅延処理アイコン](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="26a46-192">内部 I/O ドライバーの遅延処理</span><span class="sxs-lookup"><span data-stu-id="26a46-192">Internal I/O Driver Deferred Processing</span></span> |
| ![A R P 動的エントリの無効化アイコン](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="26a46-194">**ARP 動的エントリの無効化** (*nx_arp_dynamic_entries_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="26a46-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![A R P 動的エントリの設定アイコン](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="26a46-196">**ARP 動的エントリの設定** (*nx_arp_dynamic_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![A R P 有効化アイコン](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="26a46-198">**ARP 有効化** (*nx_arp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![A R P Gratuitous 送信アイコン](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="26a46-200">**ARP Gratuitous 送信** (*nx_arp_gratuitous_send*)</span><span class="sxs-lookup"><span data-stu-id="26a46-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![A R P ハードウェア アドレス検索アイコン](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="26a46-202">**ARP ハードウェア アドレス検索** (*nx_arp_hardware_address_find*)</span><span class="sxs-lookup"><span data-stu-id="26a46-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![A R P 情報の取得アイコン](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="26a46-204">**ARP 情報の取得** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![A R P IP アドレス検索アイコン](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="26a46-206">**ARP IP アドレス検索** (*nx_arp_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="26a46-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![A R P 静的エントリの作成アイコン](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="26a46-208">**ARP 静的エントリの作成** (*nx_arp_static_entry_create*)</span><span class="sxs-lookup"><span data-stu-id="26a46-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="26a46-210">**ARP 静的エントリの削除** (*nx_arp_static_entries_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="26a46-212">**ARP 静的エントリの削除** (*nx_arp_static_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Duo キャッシュ エントリの削除アイコン](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="26a46-214">**Duo キャッシュ エントリの削除** (*nxd_nd_cache_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Duo キャッシュ エントリの設定アイコン](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="26a46-216">**Duo キャッシュ エントリの設定** (*nxd_nd_cache_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Duo キャッシュの無効化アイコン](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="26a46-218">**Duo キャッシュの無効化** (*nxd_nd_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="26a46-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Duo キャッシュ I P アドレス検索アイコン](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="26a46-220">**Duo キャッシュ IP アドレス検索** (*nxd_nd_cache_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="26a46-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![Duo I C M P の有効化アイコン](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="26a46-222">**Duo ICMP の有効化** (*nxd_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![Duo I C M P I P v 6 ping アイコン](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="26a46-224">**Duo ICMP IPv6 ping** (*nxd_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="26a46-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Duo I P ペイロードの最大サイズの検索アイコン](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="26a46-226">**Duo IP ペイロードの最大サイズの検索** (*nx_max_payload_size_find*)</span><span class="sxs-lookup"><span data-stu-id="26a46-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Duo I P 生パケット送信アイコン](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="26a46-228">**Duo IP 生パケット送信** (*nxd_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="26a46-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Duo I P v 6 既定ルーターの追加アイコン](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="26a46-230">**Duo IPv6 既定ルーターの追加** (*nxd_ipv6_default_router_add*)</span><span class="sxs-lookup"><span data-stu-id="26a46-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Duo I P v 6 既定ルーターの削除アイコン](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="26a46-232">**Duo IPv6 既定ルーターの削除** (*nxd_ipv6_default_router_delete)*</span><span class="sxs-lookup"><span data-stu-id="26a46-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Duo I P v 6 の有効化アイコン](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="26a46-234">**Duo IPv6 の有効化** (*nxd_ipv6_enable)*</span><span class="sxs-lookup"><span data-stu-id="26a46-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Duo I P v 6 グローバル アドレスの取得アイコン](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="26a46-236">**Duo IPv6 グローバル アドレスの取得** (*nxd_ipv6_global_address_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Duo I P v 6 グローバル アドレスの設定アイコン](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="26a46-238">**Duo IPv6 グローバル アドレスの設定** (*nxd_ipv6_global_address_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Duo I P v 6 DAD プロセスの開始アイコン](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="26a46-240">**Duo IPv6 DAD プロセスの開始** (*nxd_ipv6_initiate_dad_process*)</span><span class="sxs-lookup"><span data-stu-id="26a46-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Duo I P v 6 インターフェイス アドレスの取得アイコン](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="26a46-242">**Duo IPv6 インターフェイス アドレスの取得** (*nxd_ipv6_interface_address_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Duo I P v 6 インターフェイス アドレスの設定アイコン](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="26a46-244">**Duo IPv6 インターフェイス アドレスの設定** (*nxd_ipv6_interface_address_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Duo I P v 6 リンク ローカル アドレスの取得アイコン](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="26a46-246">**Duo IPv6 リンク ローカル アドレスの取得** (*nxd_ipv6_linklocal_address_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Duo I P v 6 リンク ローカル アドレスの設定アイコン](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="26a46-248">**Duo IPv6 リンク ローカル アドレスの設定** (*nxd_ipv6_linklocal_address_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Duo I P v 6 生パケットの送信アイコン](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="26a46-250">**Duo IPv6 生パケットの送信** (*nxd_ipv6_raw_packet_send)*</span><span class="sxs-lookup"><span data-stu-id="26a46-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![Duo T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="26a46-252">**Duo TCP ソケット ピア情報の取得** (*nxd_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Duo T C P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="26a46-254">**Duo TCP ソケットの設定インターフェイス** (*nxd_tcp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="26a46-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Duo U D P ソケット送信アイコン](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="26a46-256">**Duo UDP ソケット送信** (*nxd_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="26a46-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Duo U D P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="26a46-258">**Duo UDP ソケットの設定インターフェイス** (*nxd_udp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="26a46-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Duo U D P ソース抽出アイコン](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="26a46-260">**Duo UDP ソース抽出** (*nxd_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="26a46-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![I C M P の有効化アイコン](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="26a46-262">**ICMP の有効化** (*nx_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![I C M P 情報の取得アイコン](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="26a46-264">**ICMP 情報の取得** (*nx_icmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![I C M P ping アイコン](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="26a46-266">**ICMP ping** (*nx_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="26a46-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![I G M P の有効化アイコン](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="26a46-268">**IGMP の有効化** (*nx_igmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![I G M P 情報の取得アイコン](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="26a46-270">**IGMP 情報の取得** (*nx_igmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![I G M P ループバックの無効化アイコン](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="26a46-272">**IGMP ループバックの無効化** (*nx_igmp_loopback_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![I G M P ループバックの有効化アイコン](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="26a46-274">**IGMP ループバックの有効化** (*nx_igmp_loopback_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![I G M P マルチキャスト参加アイコン](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="26a46-276">**IGMP マルチキャスト参加** (*nx_igmp_multicast_join*)</span><span class="sxs-lookup"><span data-stu-id="26a46-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![I G M P マルチキャスト離脱アイコン](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="26a46-278">**IGMP マルチキャスト離脱** (*nx_igmp_multicast_leave*)</span><span class="sxs-lookup"><span data-stu-id="26a46-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![I P アドレス変更通知アイコン](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="26a46-280">**IP アドレス変更通知** (*nx_ip_address_change_notify*)</span><span class="sxs-lookup"><span data-stu-id="26a46-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![I P アドレス取得アイコン](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="26a46-282">**IP アドレスの取得** (*nx_ip_address_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![I P アドレスの設定アイコン](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="26a46-284">**IP アドレスの設定** (*nx_ip_address_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![I P の作成アイコン](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="26a46-286">**IP の作成** (*nx_ip_create*)</span><span class="sxs-lookup"><span data-stu-id="26a46-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![I P の削除アイコン](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="26a46-288">**IP の削除** (*nx_ip_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![I P ドライバーのダイレクト コマンド アイコン](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="26a46-290">**IP ドライバーのダイレクト コマンド** (*nx_ip_driver_direct_command*)</span><span class="sxs-lookup"><span data-stu-id="26a46-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![I P 転送の無効化アイコン](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="26a46-292">**IP 転送の無効化** (*nx_ip_forwarding_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![I P 転送の有効化アイコン](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="26a46-294">**IP 転送の有効化** (*nx_ip_forwarding_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![I P フラグメントの無効化アイコン](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="26a46-296">**IP フラグメントの無効化** (*nx_ip_fragment_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![I P フラグメントの有効化アイコン](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="26a46-298">**IP フラグメントの有効化** (*nx_ip_fragment_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![I P ゲートウェイ アドレスの設定アイコン](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="26a46-300">**IP ゲートウェイ アドレスの設定** (*nx_ip_gateway_address_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![I P 情報の取得アイコン](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="26a46-302">**IP 情報の取得** (*nx_ip_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![I P インターフェイスのアタッチ アイコン](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="26a46-304">**IP インターフェイスのアタッチ** (*nx_ip_interface_attach*)</span><span class="sxs-lookup"><span data-stu-id="26a46-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![I P インターフェイス情報の取得アイコン](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="26a46-306">**IP インターフェイス情報の取得** (*nx_ip_interface_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![I P 生パケットの無効化アイコン](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="26a46-308">**IP 生パケットの無効化** (*nx_ip_raw_packet_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![I P 生パケットの有効化アイコン](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="26a46-310">**IP 生パケットの有効化** (*nx_ip_raw_packet_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![I P 生パケットの受信アイコン](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="26a46-312">**IP 生パケットの受信** (*nx_ip_raw_packet_receive*)</span><span class="sxs-lookup"><span data-stu-id="26a46-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![I P 生パケットの送信アイコン](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="26a46-314">**IP 生パケットの送信** (*nx_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="26a46-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![I P 静的ルートの追加アイコン](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="26a46-316">**IP 静的ルートの追加** (*nx_ip_static_route_add*)</span><span class="sxs-lookup"><span data-stu-id="26a46-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![I P 静的ルートの削除アイコン](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="26a46-318">**IP 静的ルートの削除** (*nx_ip_static_route_delete)*</span><span class="sxs-lookup"><span data-stu-id="26a46-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![I P 状態チェック アイコン](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="26a46-320">**IP 状態チェック** (*nx_ip_status_check*)</span><span class="sxs-lookup"><span data-stu-id="26a46-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![I P S E C の有効化アイコン](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="26a46-322">**IPSEC の有効化** (*nx_ipsec_enable)*</span><span class="sxs-lookup"><span data-stu-id="26a46-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![パケットの割り当てアイコン](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="26a46-324">**パケットの割り当て** (*nx_packet_allocate*)</span><span class="sxs-lookup"><span data-stu-id="26a46-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![パケット コピー アイコン](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="26a46-326">**パケット コピー** (*nx_packet_copy*)</span><span class="sxs-lookup"><span data-stu-id="26a46-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![パケット データの追加アイコン](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="26a46-328">**パケット データの追加** (*nx_packet_data_append*)</span><span class="sxs-lookup"><span data-stu-id="26a46-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![パケット データ抽出オフセット アイコン](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="26a46-330">**パケット データ抽出オフセット** (*nx_packet_data_extract_offset*)</span><span class="sxs-lookup"><span data-stu-id="26a46-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![パケット データ取得アイコン](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="26a46-332">**パケット データ取得** (*nx_packet_data_retrieve*)</span><span class="sxs-lookup"><span data-stu-id="26a46-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![パケット長の取得アイコン](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="26a46-334">**パケット長の取得** (*nx_packet_length_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![パケット プールの作成アイコン](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="26a46-336">**パケット プールの作成** (*nx_packet_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="26a46-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![パケット プールの削除アイコン](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="26a46-338">**パケット プールの削除** (*nx_packet_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![パケット プール情報の取得アイコン](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="26a46-340">**パケット プール情報の取得** (*nx_packet_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![パケット解放アイコン](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="26a46-342">**パケット解放** (*nx_packet_release*)</span><span class="sxs-lookup"><span data-stu-id="26a46-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![パケット送信解放アイコン](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="26a46-344">**パケット送信解放** (*nx_packet_transmit_release*)</span><span class="sxs-lookup"><span data-stu-id="26a46-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![R A R P の無効化アイコン](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="26a46-346">**RARP の無効化** (*nx_rarp_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![R A R P の有効化アイコン](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="26a46-348">**RARP の有効化** (*nx_rarp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![R A R P 情報の取得アイコン](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="26a46-350">**RARP 情報の取得** (*nx_rarp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![システム初期化アイコン](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="26a46-352">**システム初期化** (*nx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="26a46-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![T C P クライアント ソケット バインド アイコン](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="26a46-354">**TCP クライアント ソケット バインド** (*nx_tcp_client_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="26a46-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![T C P クライアント ソケット接続アイコン](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="26a46-356">**TCP クライアント ソケット接続** (*nx_tcp_client_socket_connect*)</span><span class="sxs-lookup"><span data-stu-id="26a46-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![T C P クライアント ソケット ポートの取得アイコン](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="26a46-358">**TCP クライアント ソケット ポートの取得** (*nx_tcp_client_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![T C P クライアント ソケットのバインド解除アイコン](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="26a46-360">**TCP クライアント ソケットのバインド解除** (*nx_tcp_client_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="26a46-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![T C P の有効化アイコン](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="26a46-362">**TCP の有効化** (*nx_tcp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![T C P 空きポートの検索アイコン](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="26a46-364">**TCP 空きポートの検索** (*nx_tcp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="26a46-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![T C P 情報の取得アイコン](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="26a46-366">**TCP 情報の取得** (*nx_tcp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![T C P サーバー ソケットの受け入れアイコン](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="26a46-368">**TCP サーバー ソケットの受け入れ** (*nx_tcp_server_socket_accept*)</span><span class="sxs-lookup"><span data-stu-id="26a46-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![T C P サーバー ソケットのリッスン アイコン](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="26a46-370">**TCP サーバー ソケットのリッスン** (*nx_tcp_server_socket_listen*)</span><span class="sxs-lookup"><span data-stu-id="26a46-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![T C P サーバー ソケットの再リッスン アイコン](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="26a46-372">**TCP サーバー ソケットの再リッスン** (*nx_tcp_server_socket_relisten*)</span><span class="sxs-lookup"><span data-stu-id="26a46-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![T C P サーバー ソケットの受け入れ解除アイコン](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="26a46-374">**TCP サーバー ソケットの受け入れ解除** (*nx_tcp_server_socket_unaccept*)</span><span class="sxs-lookup"><span data-stu-id="26a46-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![T C P サーバー ソケットのリッスン解除アイコン](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="26a46-376">**TCP サーバー ソケットのリッスン解除** (*nx_tcp_server_socket_unlisten*)</span><span class="sxs-lookup"><span data-stu-id="26a46-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![使用可能な T C P ソケット バイト数アイコン](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="26a46-378">**使用可能な TCP ソケット バイト数** (*nx_tcp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="26a46-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![T C P ソケットの作成アイコン](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="26a46-380">**TCP ソケットの作成** (*nx_tcp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="26a46-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![T C P ソケットの削除アイコン](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="26a46-382">**TCP ソケットの削除** (*nx_tcp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![T C P ソケットの切断アイコン](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="26a46-384">**TCP ソケットの切断** (*nx_tcp_socket_disconnect*)</span><span class="sxs-lookup"><span data-stu-id="26a46-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![T C P ソケット情報の取得アイコン](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="26a46-386">**TCP ソケット情報の取得** (*nx_tcp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![T C P ソケット MSS の取得アイコン](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="26a46-388">**TCP ソケット MSS の取得** (*nx_tcp_socket_mss_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![T C P ソケット MSS ピアの取得アイコン](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="26a46-390">**TCP ソケット MSS ピアの取得** (*nx_tcp_socket_mss_peer_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![T C P ソケット MSS の設定アイコン](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="26a46-392">**TCP ソケット MSS の設定** (*nx_tcp_socket_mss_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="26a46-394">**TCP ソケット ピア情報の取得** (*nx_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![T C P ソケット受信アイコン](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="26a46-396">**TCP ソケット受信** (*nx_tcp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="26a46-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![T C P ソケット受信通知アイコン](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="26a46-398">**TCP ソケット受信通知** (*nx_tcp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="26a46-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![T C P ソケット送信アイコン](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="26a46-400">**TCP ソケット送信** (*nx_tcp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="26a46-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![T C P ソケット状態待機アイコン](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="26a46-402">**TCP ソケット状態待機** (*nx_tcp_socket_state_wait*)</span><span class="sxs-lookup"><span data-stu-id="26a46-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![T C P ソケット送信の構成アイコン](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="26a46-404">**TCP ソケット送信の構成** (*nx_tcp_socket_transmit_configure*)</span><span class="sxs-lookup"><span data-stu-id="26a46-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![T C P ソケット ウィンドウ更新通知の設定アイコン](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="26a46-406">**TCP ソケット ウィンドウ更新通知の設定** (*nx_tcp_socket_window_update_notify_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![U D P の有効化アイコン](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="26a46-408">**UDP の有効化** (*nx_udp_enable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![U D P 空きポートの検索アイコン](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="26a46-410">**UDP 空きポートの検索** (*nx_udp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="26a46-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![U D P 情報の取得アイコン](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="26a46-412">**UDP 情報の取得** (*nx_udp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![U D P ソケット バインド アイコン](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="26a46-414">**UDP ソケット バインド** (*nx_udp_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="26a46-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![使用可能な U D P ソケット バイト数アイコン](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="26a46-416">**使用可能な UDP ソケット バイト数** (*nx_udp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="26a46-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![U D P ソケット チェックサムの無効化アイコン](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="26a46-418">**UDP ソケット チェックサムの無効化** (*nx_udp_socket_checksum_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![U D P ソケット チェックサムの有効化アイコン](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="26a46-420">**UDP ソケット チェックサムの有効化** (*nx_udp_socket_checksum_disable*)</span><span class="sxs-lookup"><span data-stu-id="26a46-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![U D P ソケットの作成アイコン](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="26a46-422">**UDP ソケットの作成** (*nx_udp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="26a46-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![U D P ソケットの削除アイコン](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="26a46-424">**UDP ソケットの削除** (*nx_udp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="26a46-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![U D ソケット情報の取得アイコン](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="26a46-426">**UDP ソケット情報の取得** (*nx_udp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![U D P ソケット インターフェイスの設定アイコン](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="26a46-428">**UDP ソケット インターフェイスの設定** (*nx_udp_socket_interface_set*)</span><span class="sxs-lookup"><span data-stu-id="26a46-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![U D P ソケット ポートの取得アイコン](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="26a46-430">**UDP ソケット ポートの取得** (*nx_udp_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="26a46-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![U D P ソケット受信アイコン](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="26a46-432">**UDP ソケット受信** (*nx_udp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="26a46-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![U D P ソケット受信通知アイコン](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="26a46-434">**UDP ソケット受信通知** (*nx_udp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="26a46-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![U D P ソケット送信アイコン](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="26a46-436">**UDP ソケット送信** (*nx_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="26a46-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![U D P ソケットのバインド解除アイコン](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="26a46-438">**UDP ソケットのバインド解除** (*nx_udp_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="26a46-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![U D P ソース抽出アイコン](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="26a46-440">**UDP ソース抽出** (*nx_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="26a46-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="26a46-441">イベントの説明</span><span class="sxs-lookup"><span data-stu-id="26a46-441">Event Descriptions</span></span>

<span data-ttu-id="26a46-442">次のページでは、NetX トレース イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="26a46-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="26a46-443">内部 ARP 要求の受信</span><span class="sxs-lookup"><span data-stu-id="26a46-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="26a46-444">内部 ARP 要求の受信</span><span class="sxs-lookup"><span data-stu-id="26a46-444">Internal ARP request receive</span></span>

<span data-ttu-id="26a46-445">**アイコン** ![内部 ARP 要求の受信アイコン](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="26a46-446">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-446">**Description**</span></span>

<span data-ttu-id="26a46-447">このイベントは、内部 NetX ARP 要求の受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="26a46-448">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-448">**Information Fields**</span></span>

- <span data-ttu-id="26a46-449">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-450">情報フィールド 2: 送信元 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="26a46-451">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-452">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="26a46-453">内部 ARP 要求の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="26a46-454">内部 ARP 要求の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-454">Internal ARP request send</span></span>

<span data-ttu-id="26a46-455">**アイコン** ![内部 ARP 要求の送信アイコン](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="26a46-456">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-456">**Description**</span></span>

<span data-ttu-id="26a46-457">このイベントは、内部 NetX ARP 要求の送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="26a46-458">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-458">**Information Fields**</span></span>

- <span data-ttu-id="26a46-459">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-460">情報フィールド 2: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="26a46-461">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-462">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="26a46-463">内部 ARP 応答の受信</span><span class="sxs-lookup"><span data-stu-id="26a46-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="26a46-464">内部 ARP 要求の受信</span><span class="sxs-lookup"><span data-stu-id="26a46-464">Internal ARP request receive</span></span>

<span data-ttu-id="26a46-465">**アイコン** ![内部 ARP 要求の受信アイコン](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="26a46-466">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-466">**Description**</span></span>

<span data-ttu-id="26a46-467">このイベントは、内部 NetX ARP 応答の受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="26a46-468">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-468">**Information Fields**</span></span>

- <span data-ttu-id="26a46-469">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-470">情報フィールド 2: 送信元 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="26a46-471">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-472">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="26a46-473">内部 ARP 応答の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="26a46-474">内部 ARP 要求の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-474">Internal ARP request send</span></span>

<span data-ttu-id="26a46-475">**アイコン** ![内部 ARP 要求の送信アイコン](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="26a46-476">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-476">**Description**</span></span>

<span data-ttu-id="26a46-477">このイベントは、内部 NetX 応答の送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="26a46-478">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-478">**Information Fields**</span></span>

- <span data-ttu-id="26a46-479">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-480">情報フィールド 2: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="26a46-481">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-482">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="26a46-483">内部 ICMP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="26a46-484">内部 ICMP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-484">Internal ICMP receive</span></span>

<span data-ttu-id="26a46-485">**アイコン** ![内部 I C M P 受信アイコン](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="26a46-486">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-486">**Description**</span></span>

<span data-ttu-id="26a46-487">このイベントは、内部 NetX ICMP 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="26a46-488">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-488">**Information Fields**</span></span>

- <span data-ttu-id="26a46-489">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-490">情報フィールド 2: 送信元 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="26a46-491">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-492">情報フィールド 4: ICMP ヘッダーのワード 0</span><span class="sxs-lookup"><span data-stu-id="26a46-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="26a46-493">内部 ICMP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="26a46-494">内部 ICMP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-494">Internal ICMP send</span></span>

<span data-ttu-id="26a46-495">**アイコン** ![内部 I C M P 送信アイコン](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="26a46-496">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-496">**Description**</span></span>

<span data-ttu-id="26a46-497">このイベントは、内部 NetX ICMP 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="26a46-498">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-498">**Information Fields**</span></span>

- <span data-ttu-id="26a46-499">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-500">情報フィールド 2: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="26a46-501">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-502">情報フィールド 4: ICMP ヘッダーのワード 0</span><span class="sxs-lookup"><span data-stu-id="26a46-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="26a46-503">内部 IGMP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="26a46-504">内部 IGMP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-504">Internal IGMP receive</span></span>

<span data-ttu-id="26a46-505">**アイコン** ![内部 I G M P 受信アイコン](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="26a46-506">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-506">**Description**</span></span>

<span data-ttu-id="26a46-507">このイベントは、内部 NetX IGMP 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="26a46-508">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-508">**Information Fields**</span></span>

- <span data-ttu-id="26a46-509">情報フィールド 1: IP ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="26a46-510">情報フィールド 2: 送信元 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="26a46-511">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-512">情報フィールド 4: IGMP ヘッダーのワード 0</span><span class="sxs-lookup"><span data-stu-id="26a46-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="26a46-513">内部 IP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="26a46-514">内部 IP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-514">Internal IP receive</span></span>

<span data-ttu-id="26a46-515">**アイコン** ![内部 I P 受信アイコン](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="26a46-516">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-516">**Description**</span></span>

<span data-ttu-id="26a46-517">このイベントは、内部 NetX の IP 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="26a46-518">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-518">**Information Fields**</span></span>

- <span data-ttu-id="26a46-519">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-520">情報フィールド 2: 送信元 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="26a46-521">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-522">情報フィールド 4: パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="26a46-523">内部 IP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="26a46-524">内部 IP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-524">Internal IP send</span></span>

<span data-ttu-id="26a46-525">**アイコン** ![内部 I P 送信アイコン](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="26a46-526">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-526">**Description**</span></span>

<span data-ttu-id="26a46-527">このイベントは、内部 NetX IP 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="26a46-528">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-528">**Information Fields**</span></span>

- <span data-ttu-id="26a46-529">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-530">情報フィールド 2: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="26a46-531">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-532">情報フィールド 4: パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="26a46-533">内部 TCP データ受信</span><span class="sxs-lookup"><span data-stu-id="26a46-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="26a46-534">内部 TCP データ受信</span><span class="sxs-lookup"><span data-stu-id="26a46-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="26a46-535">**アイコン** ![内部 T C P データ受信アイコン](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="26a46-536">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-536">**Description**</span></span>

<span data-ttu-id="26a46-537">このイベントは、内部 NetX TCP データ受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="26a46-538">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-538">**Information Fields**</span></span>

- <span data-ttu-id="26a46-539">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-540">情報フィールド 2: 送信元 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="26a46-541">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-542">情報フィールド 4: 受信シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="26a46-543">内部 TCP データ送信</span><span class="sxs-lookup"><span data-stu-id="26a46-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="26a46-544">内部 TCP データ送信</span><span class="sxs-lookup"><span data-stu-id="26a46-544">Internal TCP Data Send</span></span>

<span data-ttu-id="26a46-545">**アイコン** ![内部 T C P データ送信アイコン](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="26a46-546">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-546">**Description**</span></span>

<span data-ttu-id="26a46-547">このイベントは、内部 NetX TCP データ送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="26a46-548">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-548">**Information Fields**</span></span>

- <span data-ttu-id="26a46-549">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-550">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-551">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-552">情報フィールド 4: 転送シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="26a46-553">内部 TCP FIN 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="26a46-554">内部 TCP FIN 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-554">Internal TCP fin receive</span></span>

<span data-ttu-id="26a46-555">**アイコン** ![内部 T C P F I N 受信アイコン](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="26a46-556">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-556">**Description**</span></span>

<span data-ttu-id="26a46-557">このイベントは、内部 NetX TCP FIN 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="26a46-558">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-558">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-559">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-560">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-561">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-562">情報フィールド 4: 受信シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="26a46-563">内部 TCP FIN 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="26a46-564">内部 TCP FIN 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-564">Internal TCP fin send</span></span>

<span data-ttu-id="26a46-565">**アイコン** ![内部 T C P F I N 送信アイコン](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="26a46-566">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-566">**Description**</span></span>

<span data-ttu-id="26a46-567">このイベントは、内部 NetX TCP FIN 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="26a46-568">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-568">**Information Fields**</span></span>

- <span data-ttu-id="26a46-569">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-570">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-571">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-572">情報フィールド 4: 転送シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="26a46-573">内部 TCP RST 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="26a46-574">内部 TCP RST 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-574">Internal TCP RST receive</span></span>

<span data-ttu-id="26a46-575">**アイコン** ![内部 T C P R S T 受信アイコン](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="26a46-576">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-576">**Description**</span></span>

<span data-ttu-id="26a46-577">このイベントは、内部 NetX TCP リセット受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="26a46-578">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-578">**Information Fields**</span></span>

- <span data-ttu-id="26a46-579">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="26a46-580">情報フィールド 2: ソケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="26a46-581">情報フィールド 3: パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="26a46-582">情報フィールド 4: 受信シーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="26a46-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="26a46-583">内部 TCP RST 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="26a46-584">内部 TCP RST 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-584">Internal TCP RST send</span></span>

<span data-ttu-id="26a46-585">**アイコン** ![内部 T C P R S T 送信アイコン](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="26a46-586">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-586">**Description**</span></span>

<span data-ttu-id="26a46-587">このイベントは、内部 NetX TCP リセット送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="26a46-588">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-588">**Information Fields**</span></span>

- <span data-ttu-id="26a46-589">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-590">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-591">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-592">情報フィールド 4: 転送シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="26a46-593">内部 TCP SYN 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="26a46-594">内部 TCP SYN 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="26a46-595">**アイコン** ![内部 T C P S Y N 受信アイコン](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="26a46-596">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-596">**Description**</span></span>

<span data-ttu-id="26a46-597">このイベントは、内部 NetX TCP SYN 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="26a46-598">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-598">**Information Fields**</span></span>

- <span data-ttu-id="26a46-599">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-600">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-601">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-602">情報フィールド 4: 受信シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="26a46-603">内部 TCP SYN 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="26a46-604">内部 TCP SYN 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-604">Internal TCP SYN send</span></span>

<span data-ttu-id="26a46-605">**アイコン** ![内部 T C P S Y N 送信アイコン](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="26a46-606">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-606">**Description**</span></span>

<span data-ttu-id="26a46-607">このイベントは、内部 NetX TCP SYN 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="26a46-608">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="26a46-608">Information Fields</span></span> 

- <span data-ttu-id="26a46-609">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-610">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-611">情報フィールド 3: パケットへのポインター - 情報フィールド 4: 転送シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="26a46-612">内部 UDP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="26a46-613">内部 UDP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-613">Internal UDP receive</span></span>

<span data-ttu-id="26a46-614">**アイコン** ![内部 U D P 受信アイコン](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="26a46-615">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-615">**Description**</span></span>

<span data-ttu-id="26a46-616">このイベントは、内部 NetX UDP 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="26a46-617">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-617">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-618">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-619">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-620">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-621">情報フィールド 4: UDP ヘッダーのワード 0</span><span class="sxs-lookup"><span data-stu-id="26a46-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="26a46-622">内部 UDP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="26a46-623">内部 UDP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-623">Internal UDP send</span></span>

<span data-ttu-id="26a46-624">**アイコン** ![内部 U D P 送信アイコン](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="26a46-625">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-625">**Description**</span></span>

<span data-ttu-id="26a46-626">このイベントは、内部 NetX UDP 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="26a46-627">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-627">**Information Fields**</span></span>

- <span data-ttu-id="26a46-628">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-629">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-630">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-631">情報フィールド 4: UDP ヘッダーのワード 0</span><span class="sxs-lookup"><span data-stu-id="26a46-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="26a46-632">内部 RARP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="26a46-633">内部 RARP 受信</span><span class="sxs-lookup"><span data-stu-id="26a46-633">Internal RARP receive</span></span> 

<span data-ttu-id="26a46-634">**アイコン** ![内部 R A R P 受信アイコン](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="26a46-635">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-635">**Description**</span></span>

<span data-ttu-id="26a46-636">このイベントは、内部 NetX RARP 受信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="26a46-637">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-637">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-638">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-639">情報フィールド 2: ターゲット IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="26a46-640">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-641">情報フィールド 4: RARP ヘッダーのワード 1</span><span class="sxs-lookup"><span data-stu-id="26a46-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="26a46-642">内部 RARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="26a46-643">内部 RARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-643">Internal RARP send</span></span> 

<span data-ttu-id="26a46-644">**アイコン** ![内部 R A R P 送信アイコン](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="26a46-645">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-645">**Description**</span></span>

<span data-ttu-id="26a46-646">このイベントは、内部 NetX RARP 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="26a46-647">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-647">**Information Fields**</span></span>

- <span data-ttu-id="26a46-648">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-649">情報フィールド 2: ターゲット IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="26a46-650">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-651">情報フィールド 4: RARP ヘッダーのワード 1</span><span class="sxs-lookup"><span data-stu-id="26a46-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="26a46-652">内部 TCP 再試行</span><span class="sxs-lookup"><span data-stu-id="26a46-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="26a46-653">内部 TCP 再試行</span><span class="sxs-lookup"><span data-stu-id="26a46-653">Internal TCP retry</span></span> 

<span data-ttu-id="26a46-654">**アイコン** ![内部 T C P 再試行アイコン](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="26a46-655">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-655">**Description**</span></span>

<span data-ttu-id="26a46-656">このイベントは、内部 NetX TCP 再試行イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="26a46-657">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-657">**Information Fields**</span></span>
- <span data-ttu-id="26a46-658">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-659">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-660">情報フィールド 3: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="26a46-661">情報フィールド 4: 再試行回数</span><span class="sxs-lookup"><span data-stu-id="26a46-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="26a46-662">内部 TCP 状態の変更</span><span class="sxs-lookup"><span data-stu-id="26a46-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="26a46-663">内部 TCP 状態の変更</span><span class="sxs-lookup"><span data-stu-id="26a46-663">Internal TCP state change</span></span> 

<span data-ttu-id="26a46-664">**アイコン** ![内部 T C P 状態の変更アイコン](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="26a46-665">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-665">**Description**</span></span>

<span data-ttu-id="26a46-666">このイベントは、内部 NetX TCP ソケットの状態変更イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="26a46-667">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-667">**Information Fields**</span></span>

- <span data-ttu-id="26a46-668">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-669">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-670">情報フィールド 3: 以前の状態</span><span class="sxs-lookup"><span data-stu-id="26a46-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="26a46-671">情報フィールド 4: 新しい状態</span><span class="sxs-lookup"><span data-stu-id="26a46-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="26a46-672">内部 I/O ドライバーのパケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="26a46-673">内部 I/O ドライバーのパケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="26a46-674">**アイコン** ![内部 I / O ドライバーのパケット送信アイコン](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="26a46-675">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-675">**Description**</span></span>

<span data-ttu-id="26a46-676">このイベントは、内部 NetX I/O ドライバーのパケット送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="26a46-677">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-677">**Information Fields**</span></span>

- <span data-ttu-id="26a46-678">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-679">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-680">情報フィールド 3: パケット サイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="26a46-681">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="26a46-682">内部 I/O ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="26a46-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="26a46-683">内部 I/O ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="26a46-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="26a46-684">**アイコン** ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="26a46-685">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-685">**Description**</span></span>

<span data-ttu-id="26a46-686">このイベントは、内部 NetX I/O ドライバーの初期化イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="26a46-687">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-687">**Information Fields**</span></span>

- <span data-ttu-id="26a46-688">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="26a46-689">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26a46-690">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26a46-691">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="26a46-692">内部 I/O ドライバー リンクの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="26a46-693">内部 I/O ドライバー リンクの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="26a46-694">**アイコン** ![内部 I / O ドライバー リンクの有効化アイコン](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="26a46-695">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-695">**Description**</span></span>

<span data-ttu-id="26a46-696">このイベントは、内部 NetX I/O ドライバー リンクの有効化イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="26a46-697">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-697">**Information Fields**</span></span>

- <span data-ttu-id="26a46-698">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="26a46-699">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26a46-700">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26a46-701">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="26a46-702">内部 I/O ドライバー リンクの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="26a46-703">内部 I/O ドライバー リンクの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="26a46-704">**アイコン** ![内部 I / O ドライバー リンクの無効化アイコン](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="26a46-705">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-705">**Description**</span></span>

<span data-ttu-id="26a46-706">このイベントは、内部 NetX I/O ドライバー リンクの無効化イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="26a46-707">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-707">**Information Fields**</span></span>

- <span data-ttu-id="26a46-708">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-709">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-710">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-711">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="26a46-712">内部 I/O ドライバーのパケット ブロードキャスト</span><span class="sxs-lookup"><span data-stu-id="26a46-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="26a46-713">内部 I/O ドライバーのパケット ブロードキャスト</span><span class="sxs-lookup"><span data-stu-id="26a46-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="26a46-714">**アイコン** ![内部 I / O ドライバーのパケット ブロードキャスト アイコン](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="26a46-715">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-715">**Description**</span></span>

<span data-ttu-id="26a46-716">このイベントは、内部 NetX I/O ドライバーのパケット ブロードキャスト イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="26a46-717">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-717">**Information Fields**</span></span>

- <span data-ttu-id="26a46-718">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-719">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-720">情報フィールド 3: パケット サイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="26a46-721">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="26a46-722">内部 I/O ドライバーの ARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="26a46-723">内部 I/O ドライバーの ARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="26a46-724">**アイコン** ![内部 I / O ドライバーの ARP 送信アイコン](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="26a46-725">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-725">**Description**</span></span>

<span data-ttu-id="26a46-726">このイベントは、内部 NetX I/O ドライバーの ARP 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="26a46-727">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-727">**Information Fields**</span></span>

- <span data-ttu-id="26a46-728">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-729">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-730">情報フィールド 3: パケット サイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="26a46-731">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="26a46-732">内部 I/O ドライバーの ARP 応答の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="26a46-733">内部 I/O ドライバーの ARP 応答の送信</span><span class="sxs-lookup"><span data-stu-id="26a46-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="26a46-734">**アイコン** ![内部 I / O ドライバーの ARP 応答の送信アイコン](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="26a46-735">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-735">**Description**</span></span>

<span data-ttu-id="26a46-736">このイベントは、内部 NetX I/O ドライバーの ARP 応答送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="26a46-737">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-737">**Information Fields**</span></span>

- <span data-ttu-id="26a46-738">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-739">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-740">情報フィールド 3: パケット サイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="26a46-741">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="26a46-742">内部 I/O ドライバーの RARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="26a46-743">内部 I/O ドライバーの RARP 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="26a46-744">**アイコン** ![内部 I / O ドライバーの RARP 送信アイコン](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="26a46-745">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-745">**Description**</span></span>

<span data-ttu-id="26a46-746">このイベントは、内部 NetX I/O ドライバーの RARP 送信イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="26a46-747">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-747">**Information Fields**</span></span>

- <span data-ttu-id="26a46-748">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-749">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-750">情報フィールド 3: パケット サイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="26a46-751">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="26a46-752">内部 I/O ドライバーのマルチキャスト参加</span><span class="sxs-lookup"><span data-stu-id="26a46-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="26a46-753">内部 I/O ドライバーのマルチキャスト参加</span><span class="sxs-lookup"><span data-stu-id="26a46-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="26a46-754">**アイコン** ![内部 I / O ドライバーのマルチキャスト参加アイコン](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="26a46-755">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-755">**Description**</span></span>

<span data-ttu-id="26a46-756">このイベントは、内部 NetX I/O ドライバーのマルチキャスト参加イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="26a46-757">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-757">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-758">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-759">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-760">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-761">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="26a46-762">内部 I/O ドライバーのマルチキャスト離脱</span><span class="sxs-lookup"><span data-stu-id="26a46-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="26a46-763">内部 I/O ドライバーのマルチキャスト離脱</span><span class="sxs-lookup"><span data-stu-id="26a46-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="26a46-764">**アイコン** ![内部 I / O ドライバーのマルチキャスト離脱アイコン](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="26a46-765">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-765">**Description**</span></span>

<span data-ttu-id="26a46-766">このイベントは、内部 NetX I/O ドライバーのマルチキャスト離脱イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="26a46-767">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-767">**Information Fields**</span></span>

- <span data-ttu-id="26a46-768">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-769">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-770">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-771">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="26a46-772">内部 I/O ドライバーの状態取得</span><span class="sxs-lookup"><span data-stu-id="26a46-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="26a46-773">内部 I/O ドライバーの状態取得</span><span class="sxs-lookup"><span data-stu-id="26a46-773">Internal I/O driver get status</span></span>

<span data-ttu-id="26a46-774">**アイコン** ![内部 I / O ドライバーの状態取得アイコン](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="26a46-775">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-775">**Description**</span></span>

<span data-ttu-id="26a46-776">このイベントは、内部 NetX I/O ドライバーの状態取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="26a46-777">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-777">**Information Fields**</span></span>

- <span data-ttu-id="26a46-778">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-779">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-780">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-781">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="26a46-782">内部 I/O ドライバーの速度取得</span><span class="sxs-lookup"><span data-stu-id="26a46-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="26a46-783">内部 I/O ドライバーの速度取得</span><span class="sxs-lookup"><span data-stu-id="26a46-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="26a46-784">**アイコン** ![内部 I / O ドライバーの速度取得アイコン](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="26a46-785">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-785">**Description**</span></span>

<span data-ttu-id="26a46-786">このイベントは、内部 NetX I/O ドライバーの速度取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="26a46-787">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-787">**Information Fields**</span></span>

- <span data-ttu-id="26a46-788">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-789">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-790">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-791">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="26a46-792">内部 I/O ドライバーの二重タイプ取得</span><span class="sxs-lookup"><span data-stu-id="26a46-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="26a46-793">内部 I/O ドライバーの二重タイプ取得</span><span class="sxs-lookup"><span data-stu-id="26a46-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="26a46-794">**アイコン** ![内部 I / O ドライバーの二重タイプ取得アイコン](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="26a46-795">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-795">**Description**</span></span>

<span data-ttu-id="26a46-796">このイベントは、内部 NetX I/O ドライバーの二重タイプ取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="26a46-797">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-797">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-798">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-799">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-800">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-801">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="26a46-802">内部 I/O ドライバーのエラー数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="26a46-803">内部 I/O ドライバーのエラー数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="26a46-804">**アイコン** ![内部 I / O ドライバーのエラー数取得アイコン](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="26a46-805">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-805">**Description**</span></span>

<span data-ttu-id="26a46-806">このイベントは、内部 NetX I/O ドライバーのエラー数取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="26a46-807">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-807">**Information Fields**</span></span>

- <span data-ttu-id="26a46-808">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-809">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-810">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-811">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="26a46-812">内部 I/O ドライバーの RX 数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="26a46-813">内部 I/O ドライバーの RX 数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="26a46-814">**アイコン** ![内部 I / O ドライバーの RX 数取得アイコン](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="26a46-815">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-815">**Description**</span></span>

<span data-ttu-id="26a46-816">このイベントは、内部 NetX I/O ドライバーの RX 数取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="26a46-817">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-817">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-818">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-819">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-820">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-821">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="26a46-822">内部 I/O ドライバーの TX 数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="26a46-823">内部 I/O ドライバーの TX 数取得</span><span class="sxs-lookup"><span data-stu-id="26a46-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="26a46-824">**アイコン** ![内部 I / O ドライバーの T X 数取得アイコン](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="26a46-825">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-825">**Description**</span></span>

<span data-ttu-id="26a46-826">このイベントは、内部 NetX I/O ドライバーの TX 数取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="26a46-827">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-827">**Information Fields**</span></span>

- <span data-ttu-id="26a46-828">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-829">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-830">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-831">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="26a46-832">内部 I/O ドライバーの割り当てエラー数の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="26a46-833">内部 I/O ドライバーの割り当てエラー数の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="26a46-834">**アイコン** ![内部 I / O ドライバーの割り当てエラー数の取得アイコン](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="26a46-835">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-835">**Description**</span></span>

<span data-ttu-id="26a46-836">このイベントは、内部 NetX I/O ドライバーの割り当てエラー数の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="26a46-837">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-837">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-838">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-839">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-840">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-841">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="26a46-842">内部 I/O ドライバーの初期化解除</span><span class="sxs-lookup"><span data-stu-id="26a46-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="26a46-843">内部 I/O ドライバーの初期化解除</span><span class="sxs-lookup"><span data-stu-id="26a46-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="26a46-844">**アイコン** ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="26a46-845">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-845">**Description**</span></span>

<span data-ttu-id="26a46-846">このイベントは、内部 NetX I/O ドライバーの初期化解除イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="26a46-847">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-847">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-848">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-849">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-850">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-851">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="26a46-852">内部 I/O ドライバーの遅延処理</span><span class="sxs-lookup"><span data-stu-id="26a46-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="26a46-853">内部 I/O ドライバーの遅延処理</span><span class="sxs-lookup"><span data-stu-id="26a46-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="26a46-854">**アイコン** ![内部 I / O ドライバーの遅延処理アイコン](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="26a46-855">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-855">**Description**</span></span>

<span data-ttu-id="26a46-856">このイベントは、内部 NetX I/O ドライバーの遅延処理イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="26a46-857">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-857">**Information Fields**</span></span>

- <span data-ttu-id="26a46-858">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-859">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-860">情報フィールド 3: パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="26a46-861">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="26a46-862">ARP 動的エントリの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="26a46-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="26a46-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="26a46-864">**アイコン** ![A R P 動的エントリの無効化アイコン](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="26a46-865">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-865">**Description**</span></span>

<span data-ttu-id="26a46-866">このイベントは、nx_arp_dynamic_entries_invalidate を使用したすべての動的 ARP エントリの無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="26a46-867">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-867">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-868">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-869">情報フィールド 2: 無効化されたエントリ</span><span class="sxs-lookup"><span data-stu-id="26a46-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="26a46-870">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-871">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="26a46-872">ARP 動的エントリの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="26a46-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="26a46-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="26a46-874">**アイコン** ![A R P 動的エントリの設定アイコン](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="26a46-875">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-875">**Description**</span></span>

<span data-ttu-id="26a46-876">このイベントは、nx_arp_dynamic_entry_set を使用した動的 ARP エントリの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="26a46-877">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-877">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-878">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-879">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-880">情報フィールド 3: 物理アドレス (MSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="26a46-881">情報フィールド 4: 物理アドレス (LSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="26a46-882">ARP 有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="26a46-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-883">nx_arp_enable</span></span>

<span data-ttu-id="26a46-884">**アイコン** ![A R P 有効化アイコン](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="26a46-885">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-885">**Description**</span></span>

<span data-ttu-id="26a46-886">このイベントは、nx_arp_enable を使用した ARP の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="26a46-887">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-887">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-888">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-889">情報フィールド 2: ARP キャッシュ メモリ ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="26a46-890">情報フィールド 3: ARP キャッシュ メモリ サイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="26a46-891">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="26a46-892">ARP Gratuitous 送信</span><span class="sxs-lookup"><span data-stu-id="26a46-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="26a46-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="26a46-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="26a46-894">**アイコン** ![A R P Gratuitous 送信アイコン](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="26a46-895">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-895">**Description**</span></span>

<span data-ttu-id="26a46-896">このイベントは、nx_arp_gratuitous_send を使用した ARP Gratuitous 送信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="26a46-897">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-897">**Information Fields**</span></span>

- <span data-ttu-id="26a46-898">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-899">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-900">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-901">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="26a46-902">ARP ハードウェア アドレス検索</span><span class="sxs-lookup"><span data-stu-id="26a46-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="26a46-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="26a46-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="26a46-904">**アイコン** ![A R P ハードウェア アドレス検索アイコン](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="26a46-905">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-905">**Description**</span></span>

<span data-ttu-id="26a46-906">このイベントは、nx_arp_hardware_address_find を使用した物理アドレスの検索を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="26a46-907">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-907">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-908">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-909">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-910">情報フィールド 3: 物理アドレス (MSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="26a46-911">情報フィールド 4: 物理アドレス (LSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="26a46-912">ARP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="26a46-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-913">nx_arp_info_get</span></span>

<span data-ttu-id="26a46-914">**アイコン** ![A R P 情報の取得アイコン](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="26a46-915">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-915">**Description**</span></span>

<span data-ttu-id="26a46-916">このイベントは、nx_arp_info_get を使用した情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="26a46-917">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-917">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-918">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-919">情報フィールド 2: 送信済み ARP</span><span class="sxs-lookup"><span data-stu-id="26a46-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="26a46-920">情報フィールド 3: ARP 応答</span><span class="sxs-lookup"><span data-stu-id="26a46-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="26a46-921">情報フィールド 4: 受信済み ARP</span><span class="sxs-lookup"><span data-stu-id="26a46-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="26a46-922">ARP IP アドレス検索</span><span class="sxs-lookup"><span data-stu-id="26a46-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="26a46-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="26a46-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="26a46-924">**アイコン** ![A R P I P アドレス検索アイコン](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="26a46-925">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-925">**Description**</span></span>

<span data-ttu-id="26a46-926">このイベントは、指定された物理アドレスに関連付けられた IP アドレスの、nx_arp_ip_address_find を使用した検索を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="26a46-927">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-927">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-928">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-929">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-930">情報フィールド 3: 物理アドレス (MSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="26a46-931">情報フィールド 4: 物理アドレス (LSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="26a46-932">ARP 静的エントリの作成</span><span class="sxs-lookup"><span data-stu-id="26a46-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="26a46-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="26a46-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="26a46-934">**アイコン** ![A R P 静的エントリの作成アイコン](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="26a46-935">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-935">**Description**</span></span>

<span data-ttu-id="26a46-936">このイベントは、nx_arp_static_entry_create を使用した静的 ARP エントリの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="26a46-937">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-937">**Information Fields**</span></span>

- <span data-ttu-id="26a46-938">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-939">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-940">情報フィールド 3: 物理アドレス (MSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="26a46-941">情報フィールド 4: 物理アドレス (LSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="26a46-942">ARP 静的エントリの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="26a46-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="26a46-944">**アイコン** ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="26a46-945">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-945">**Description**</span></span>

<span data-ttu-id="26a46-946">このイベントは、nx_arp_static_entries_delete を使用したすべての ARP 静的エントリの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="26a46-947">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-947">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-948">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-949">情報フィールド 2: 削除されたエントリ</span><span class="sxs-lookup"><span data-stu-id="26a46-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="26a46-950">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-951">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="26a46-952">ARP 静的エントリの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="26a46-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="26a46-954">**アイコン** ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="26a46-955">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-955">**Description**</span></span>

<span data-ttu-id="26a46-956">このイベントは、nx_arp_static_entry_delete を使用した静的 ARP エントリの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="26a46-957">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-957">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-958">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-959">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-960">情報フィールド 3: 物理アドレス (MSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="26a46-961">情報フィールド 4: 物理アドレス (LSW)</span><span class="sxs-lookup"><span data-stu-id="26a46-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="26a46-962">Duo キャッシュ エントリの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="26a46-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="26a46-964">**アイコン** ![Duo キャッシュ エントリの削除アイコン](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="26a46-965">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-965">**Description**</span></span>

<span data-ttu-id="26a46-966">このイベントは、nx_udp_socket_create を使用した近隣キャッシュ テーブルに含まれるエントリの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="26a46-967">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-967">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-968">情報フィールド 1: 削除する IPv6 リンク ローカル アドレスの 4 番目 (最下位) のワード</span><span class="sxs-lookup"><span data-stu-id="26a46-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="26a46-969">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-970">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-971">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="26a46-972">Duo キャッシュ エントリの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="26a46-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="26a46-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="26a46-974">**アイコン** ![Duo キャッシュ エントリの設定アイコン](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="26a46-975">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-975">**Description**</span></span>

<span data-ttu-id="26a46-976">このイベントは、nxd_nd_cache_entry_set を使用した、キャッシュ エントリの作成と近隣キャッシュ テーブルの追加を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="26a46-977">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-977">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-978">情報フィールド 1: 追加する IPv6 アドレスの 4 番目 (最下位) のワード</span><span class="sxs-lookup"><span data-stu-id="26a46-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="26a46-979">情報フィールド 2: 物理アドレスの MSB</span><span class="sxs-lookup"><span data-stu-id="26a46-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="26a46-980">情報フィールド 3: 物理アドレスの LSB</span><span class="sxs-lookup"><span data-stu-id="26a46-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="26a46-981">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="26a46-982">Duo キャッシュの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="26a46-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="26a46-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="26a46-984">**アイコン** ![Duo キャッシュの無効化アイコン](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="26a46-985">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-985">**Description**</span></span>

<span data-ttu-id="26a46-986">このイベントは、nxd_nd_cache_invalidate を使用した、近隣ノード キャッシュ テーブル全体の無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="26a46-987">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-987">**Information Fields**</span></span>

- <span data-ttu-id="26a46-988">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-989">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-990">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-991">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="26a46-992">Duo キャッシュ IP アドレス検索</span><span class="sxs-lookup"><span data-stu-id="26a46-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="26a46-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="26a46-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="26a46-994">**アイコン** ![Duo キャッシュ I P アドレス検索アイコン](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="26a46-995">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-995">**Description**</span></span>

<span data-ttu-id="26a46-996">このイベントは、nxd_nd_cache_ip_address_find を使用して、指定された物理アドレスと一致する IP アドレスをキャッシュ テーブルから取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="26a46-997">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-997">**Information Fields**</span></span>

- <span data-ttu-id="26a46-998">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-999">情報フィールド 2: IPv6 アドレスの 4 番目 (最下位) のワード</span><span class="sxs-lookup"><span data-stu-id="26a46-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="26a46-1000">情報フィールド 3: 物理アドレスの MSB</span><span class="sxs-lookup"><span data-stu-id="26a46-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="26a46-1001">情報フィールド 4: 物理アドレスの LSB</span><span class="sxs-lookup"><span data-stu-id="26a46-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="26a46-1002">Duo ICMP の有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="26a46-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="26a46-1004">**アイコン** ![Duo I C M P の有効化アイコン](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="26a46-1005">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1005">**Description**</span></span>

<span data-ttu-id="26a46-1006">このイベントは、nxd_icmp_enable を使用して、指定された IP インスタンスで有効になっている ICMPv4 および ICMPv6 サービスを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="26a46-1007">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1007">**Information Fields**</span></span>
- <span data-ttu-id="26a46-1008">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1009">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1010">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1011">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="26a46-1012">Duo ICMP ping</span><span class="sxs-lookup"><span data-stu-id="26a46-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="26a46-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="26a46-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="26a46-1014">**アイコン** ![Duo I C M P ping アイコン](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="26a46-1015">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1015">**Description**</span></span>

<span data-ttu-id="26a46-1016">このイベントは、nxd_icmp_ping を使用した IPv6 ホストへの ping (エコー要求) の送信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="26a46-1017">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1017">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1018">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1019">情報フィールド 2: IPv6 アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="26a46-1020">情報フィールド 3: エコー データへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="26a46-1021">情報フィールド 4: エコー データのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="26a46-1022">Duo IP ペイロードの最大サイズの検索</span><span class="sxs-lookup"><span data-stu-id="26a46-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="26a46-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="26a46-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="26a46-1024">**アイコン** ![Duo I P ペイロードの最大サイズの検索アイコン](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="26a46-1025">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1025">**Description**</span></span>

<span data-ttu-id="26a46-1026">このイベントは、指定されたパケットに断片化せずに含められる最大ペイロードを計算します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="26a46-1027">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1027">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1028">情報フィールド 1: ソケット ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="26a46-1029">情報フィールド 2: ピア IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="26a46-1030">情報フィールド 3: ピア ポート 情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="26a46-1031">Duo IP 生パケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="26a46-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="26a46-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="26a46-1033">**アイコン** ![Duo I P 生パケット送信アイコン](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="26a46-1034">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1034">**Description**</span></span>

<span data-ttu-id="26a46-1035">このイベントは、nxd_ip_raw_packet_send を使用した、指定されたネットワーク インターフェイスから指定された IP 宛先アドレスへの生 IP パケットの送信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="26a46-1036">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1036">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1037">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1038">情報フィールド 2: 送信するパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="26a46-1039">情報フィールド 3: 宛先アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="26a46-1040">情報フィールド 4: パケット プロトコル</span><span class="sxs-lookup"><span data-stu-id="26a46-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="26a46-1041">Duo IPv6 既定ルーターの追加</span><span class="sxs-lookup"><span data-stu-id="26a46-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="26a46-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="26a46-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="26a46-1043">**アイコン** ![Duo I P v 6 既定ルーターの追加アイコン](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="26a46-1044">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1044">**Description**</span></span>

<span data-ttu-id="26a46-1045">このイベントは、nxd_ipv6_default_router_add を使用して、IP インスタンスの IPv6 ルーティング テーブルに既定のルーターを追加することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="26a46-1046">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1046">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1047">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="26a46-1048">情報フィールド 2: 宛先ネットワーク アドレス。</span><span class="sxs-lookup"><span data-stu-id="26a46-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="26a46-1049">情報フィールド 3: 有効期間情報。</span><span class="sxs-lookup"><span data-stu-id="26a46-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="26a46-1050">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="26a46-1051">Duo IPv6 既定ルーターの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="26a46-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="26a46-1053">**アイコン** ![Duo I P v 6 既定ルーターの削除アイコン](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="26a46-1054">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1054">**Description**</span></span>

<span data-ttu-id="26a46-1055">このイベントは、nxd_ipv6_default_router_delete を使用して、IP インスタンスの IPv6 ルーティング テーブルから既定のルーターを削除することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="26a46-1056">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1056">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1057">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="26a46-1058">情報フィールド 2: 既定ルーターの IPv6 アドレスで 4 番目のワード (最下位)。</span><span class="sxs-lookup"><span data-stu-id="26a46-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="26a46-1059">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26a46-1060">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="26a46-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="26a46-1061">Duo IPv6 の有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="26a46-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="26a46-1063">**アイコン** ![Duo I P v 6 の有効化アイコン](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="26a46-1064">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1064">**Description**</span></span>

<span data-ttu-id="26a46-1065">このイベントは、nxd_ipv6_enable を使用して、指定された IP インスタンスの IPv6 サービスを有効化することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="26a46-1066">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1066">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1067">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1068">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1069">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1070">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="26a46-1071">Duo IPv6 グローバル アドレス取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="26a46-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="26a46-1073">**アイコン** ![Duo I P v 6 グローバル アドレス取得アイコン](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="26a46-1074">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1074">**Description**</span></span>

<span data-ttu-id="26a46-1075">このイベントは、nxd_ipv6_global_address_get を使用して、IP インスタンス インターフェイス テーブルのインデックス 1 にある IP インスタンスのグローバル (プライマリ) IP アドレスを取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="26a46-1076">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1076">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1077">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a46-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="26a46-1078">情報フィールド 2: グローバル アドレスの 4 番目のワード (最下位)</span><span class="sxs-lookup"><span data-stu-id="26a46-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="26a46-1079">情報フィールド 3: IPv6 アドレス プレフィックス長。</span><span class="sxs-lookup"><span data-stu-id="26a46-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="26a46-1080">情報フィールド 4: IP インターフェイス テーブル (1) へのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a46-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="26a46-1081">Duo IPv6 グローバル アドレスの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="26a46-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="26a46-1083">**アイコン** ![Duo I P v 6 グローバル アドレスの設定アイコン](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="26a46-1084">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1084">**Description**</span></span>

<span data-ttu-id="26a46-1085">このイベントは、nxd_ipv6_global_address_set を使用して、IP インスタンス インターフェイス テーブルのインデックス 1 にある IP インスタンスのグローバル (プライマリ) IP アドレスを設定することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="26a46-1086">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1086">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1087">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1088">情報フィールド 2: グローバル アドレスの 4 番目のワード (最下位)</span><span class="sxs-lookup"><span data-stu-id="26a46-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="26a46-1089">情報フィールド 3: IPv6 アドレス プレフィックス長</span><span class="sxs-lookup"><span data-stu-id="26a46-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="26a46-1090">情報フィールド 4: IP インターフェイス テーブル (1) へのインデックス</span><span class="sxs-lookup"><span data-stu-id="26a46-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="26a46-1091">Duo IPv6 DAD プロセスの開始</span><span class="sxs-lookup"><span data-stu-id="26a46-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="26a46-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="26a46-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="26a46-1093">**アイコン** ![Duo I P v 6 DAD プロセスの開始アイコン](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="26a46-1094">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1094">**Description**</span></span>

<span data-ttu-id="26a46-1095">このイベントは、IP インスタンスにリンク ローカルまたは IP インターフェイス アドレスが割り当てられている場合に、nxd_ipv6_initiate_dad_process を使用して、重複アドレス検出 (DAD) プロセスが開始されることを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="26a46-1096">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1096">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1097">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1098">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1099">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1100">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="26a46-1101">Duo IPv6 インターフェイス アドレスの取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="26a46-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="26a46-1103">**アイコン** ![Duo I P v 6 インターフェイス アドレスの取得アイコン](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="26a46-1104">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1104">**Description**</span></span>

<span data-ttu-id="26a46-1105">このイベントは、nxd_ipv6_interface_address_get を使用して、指定されたインデックス位置にある IP アドレスとプレフィックスを IP インスタンス インターフェイス アドレス テーブルに取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="26a46-1106">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1106">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1107">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1108">情報フィールド 2: 返す IPv6 アドレスの 4 番目のワード (最下位)</span><span class="sxs-lookup"><span data-stu-id="26a46-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="26a46-1109">情報フィールド 4: IP インスタンス インターフェイス テーブルへのインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="26a46-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="26a46-1110">Duo IPv6 インターフェイス アドレスの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="26a46-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="26a46-1112">**アイコン** ![Duo I P v 6 インターフェイス アドレスの設定アイコン](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="26a46-1113">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1113">**Description**</span></span>

<span data-ttu-id="26a46-1114">このイベントは、指定されたインデックスにある IP アドレスとプレフィックスを IP インスタンス インターフェイス アドレス テーブルに設定することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="26a46-1115">nxd_ipv6_interface_address_set を使用した場合、インデックス ゼロ (リンク ローカル アドレス) では許可されません。</span><span class="sxs-lookup"><span data-stu-id="26a46-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="26a46-1116">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1116">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1117">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1118">情報フィールド 2: 返す IPv6 アドレスの 4 番目のワード (最下位)</span><span class="sxs-lookup"><span data-stu-id="26a46-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="26a46-1119">情報フィールド 3: プレフィックス長</span><span class="sxs-lookup"><span data-stu-id="26a46-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="26a46-1120">情報フィールド 4: IP インスタンス インターフェイス テーブルへのインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="26a46-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="26a46-1121">Duo IPv6 リンク ローカル アドレスの取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="26a46-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="26a46-1123">**アイコン** ![Duo I P v 6 リンク ローカル アドレスの取得アイコン](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="26a46-1124">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1124">**Description**</span></span>

<span data-ttu-id="26a46-1125">このイベントは、指定された IP インスタンスのリンク ローカル アドレスを nxd_ipv6_linklocal_address_get を使用して取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="26a46-1126">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1126">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1127">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1128">情報フィールド 2: IPv6 リンク ローカル アドレスの 4 番目のワード (最下位)</span><span class="sxs-lookup"><span data-stu-id="26a46-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="26a46-1129">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1130">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="26a46-1131">Duo IPv6 リンク ローカル アドレスの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="26a46-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="26a46-1133">**アイコン** ![Duo I P v 6 リンク ローカル アドレスの設定アイコン](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="26a46-1134">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1134">**Description**</span></span>

<span data-ttu-id="26a46-1135">このイベントは、nxd_ipv6_linklocal_address_set を使用した、IP インスタンスのリンク ローカル アドレスの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="26a46-1136">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1136">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1137">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1138">情報フィールド 2: IPv6 リンク ローカル アドレスの 4 番目 (最下位) のワード</span><span class="sxs-lookup"><span data-stu-id="26a46-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="26a46-1139">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1140">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="26a46-1141">Duo IPv6 生パケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="26a46-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="26a46-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="26a46-1143">**アイコン** ![Duo I P v 6 生パケット送信アイコン](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="26a46-1144">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1144">**Description**</span></span>

<span data-ttu-id="26a46-1145">このイベントは、nxd_ip_raw_packet_send を使用して、指定された宛先にプライマリ IP インターフェイスを介して生 IP パケットを送信することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="26a46-1146">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1146">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1147">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1148">情報フィールド 2: 送信するパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="26a46-1149">情報フィールド 3: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="26a46-1150">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="26a46-1151">Duo TCP ソケット ピア情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="26a46-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="26a46-1153">**アイコン** ![Duo T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="26a46-1154">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1154">**Description**</span></span>

<span data-ttu-id="26a46-1155">このイベントでは、指定されたソケットで受信した TCP パケットから送信者データが抽出されます。</span><span class="sxs-lookup"><span data-stu-id="26a46-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="26a46-1156">送信元の IP アドレスとポートが返されます。</span><span class="sxs-lookup"><span data-stu-id="26a46-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="26a46-1157">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1157">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1158">情報フィールド 1: ソケット ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="26a46-1159">情報フィールド 2: ピア IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="26a46-1160">情報フィールド 3: ピア ポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="26a46-1161">情報フィールド 4: IP アドレスの最下位の 32 ビット</span><span class="sxs-lookup"><span data-stu-id="26a46-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="26a46-1162">Duo TCP ソケットの設定インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26a46-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="26a46-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="26a46-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="26a46-1164">**アイコン** ![Duo T C P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="26a46-1165">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1165">**Description**</span></span>

<span data-ttu-id="26a46-1166">このイベントは、クライアントが指定されたサーバー IP アドレスの TCP サーバーに接続した後で、nxd_tcp_client_socket_connect を使用して発信ソケット インターフェイスを設定することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="26a46-1167">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1167">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1168">情報フィールド 1: TCP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="26a46-1169">情報フィールド 2: インターフェイス ID</span><span class="sxs-lookup"><span data-stu-id="26a46-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="26a46-1170">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1171">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="26a46-1172">Duo UDP ソケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="26a46-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="26a46-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="26a46-1174">**アイコン** ![Duo U D P ソケットの送信アイコン](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="26a46-1175">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1175">**Description**</span></span>

<span data-ttu-id="26a46-1176">このイベントは、nxd_udp_socket_send 経由で入力 IP アドレスとポートを使用して、指定されたソケットを介して UDP パケットを送信することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="26a46-1177">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1177">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1178">情報フィールド 1: ポインター UDP ソケット</span><span class="sxs-lookup"><span data-stu-id="26a46-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="26a46-1179">情報フィールド 2: UDP パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="26a46-1180">情報フィールド 3: パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="26a46-1181">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="26a46-1182">Duo UDP ソケットの設定インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26a46-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="26a46-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="26a46-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="26a46-1184">**アイコン** ![Duo U D P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="26a46-1185">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1185">**Description**</span></span>

<span data-ttu-id="26a46-1186">このイベントは、nxd_udp_socket_set_interface を使用して、指定された UDP ソケット送信インターフェイスを入力インターフェイス ID に対応するインターフェイスに設定することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="26a46-1187">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1187">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1188">情報フィールド 1: UDP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="26a46-1189">情報フィールド 2: インターフェイス ID</span><span class="sxs-lookup"><span data-stu-id="26a46-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="26a46-1190">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1191">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="26a46-1192">Duo UDP ソース抽出</span><span class="sxs-lookup"><span data-stu-id="26a46-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="26a46-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="26a46-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="26a46-1194">**アイコン** ![Duo U D P ソース抽出アイコン](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="26a46-1195">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1195">**Description**</span></span>

<span data-ttu-id="26a46-1196">このイベントは、受信したパケットの IP アドレスと送信元ポートの抽出を表します (IPv4 または IPv6)。</span><span class="sxs-lookup"><span data-stu-id="26a46-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="26a46-1197">IPv6 の場合、IP アドレスの 4 番目のワード (最下位) が nxd_udp_source_extract によって返されます。</span><span class="sxs-lookup"><span data-stu-id="26a46-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="26a46-1198">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1198">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1199">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="26a46-1200">情報フィールド 2: IP バージョン</span><span class="sxs-lookup"><span data-stu-id="26a46-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="26a46-1201">情報フィールド 3: 送信元 IP アドレス (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="26a46-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="26a46-1202">情報フィールド 4: 送信元ポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="26a46-1203">ICMP の有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="26a46-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1204">nx_icmp_enable</span></span>

<span data-ttu-id="26a46-1205">**アイコン** ![I C M P の有効化アイコン](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="26a46-1206">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1206">**Description**</span></span>

<span data-ttu-id="26a46-1207">このイベントは、nx_icmp_enable を使用した ICMP の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="26a46-1208">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1208">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1209">情報フィールド 1: IP インスタンス l へのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="26a46-1210">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1211">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1212">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="26a46-1213">ICMP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="26a46-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="26a46-1215">**アイコン** ![I C M P 情報の取得アイコン](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="26a46-1216">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1216">**Description**</span></span>

<span data-ttu-id="26a46-1217">このイベントは、nx_icmp_info_get を使用した情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="26a46-1218">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1218">**Information Fields**</span></span>
- <span data-ttu-id="26a46-1219">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1220">情報フィールド 2: 送信された ping</span><span class="sxs-lookup"><span data-stu-id="26a46-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="26a46-1221">情報フィールド 3: ping 応答</span><span class="sxs-lookup"><span data-stu-id="26a46-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="26a46-1222">情報フィールド 4: 受信した ping</span><span class="sxs-lookup"><span data-stu-id="26a46-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="26a46-1223">ICMP Ping</span><span class="sxs-lookup"><span data-stu-id="26a46-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="26a46-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="26a46-1224">nx_icmp_ping</span></span>

<span data-ttu-id="26a46-1225">**アイコン** ![I C M P ping アイコン](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="26a46-1226">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1226">**Description**</span></span>

<span data-ttu-id="26a46-1227">このイベントは、nx_icmp_ping を使用したターゲット IP アドレスの ping を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="26a46-1228">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1228">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1229">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1230">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-1231">情報フィールド 3: データへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="26a46-1232">情報フィールド 4: データのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="26a46-1233">IGMP の有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="26a46-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1234">nx_icmp_enable</span></span>

<span data-ttu-id="26a46-1235">**アイコン** ![I G M P の有効化アイコン](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="26a46-1236">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1236">**Description**</span></span>

<span data-ttu-id="26a46-1237">このイベントは、nx_igmp_enable を使用した IGMP の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="26a46-1238">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1238">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1239">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1240">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1241">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1242">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="26a46-1243">IGMP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="26a46-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="26a46-1245">**アイコン** ![I G M P 情報の取得アイコン](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="26a46-1246">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1246">**Description**</span></span>

<span data-ttu-id="26a46-1247">このイベントは、nx_igmp_info_get 経由での情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="26a46-1248">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1248">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1249">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1250">情報フィールド 2: 送信されたレポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="26a46-1251">情報フィールド 3: 受信したクエリ</span><span class="sxs-lookup"><span data-stu-id="26a46-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="26a46-1252">情報フィールド 4: 参加しているグループ</span><span class="sxs-lookup"><span data-stu-id="26a46-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="26a46-1253">IGMP ループバックの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="26a46-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="26a46-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="26a46-1255">**アイコン** ![I G M P ループバックの無効化アイコン](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="26a46-1256">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1256">**Description**</span></span>

<span data-ttu-id="26a46-1257">このイベントは、nx_igmp_loopback_disable を使用した IGMP ループバックの無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="26a46-1258">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1258">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1259">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1260">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1261">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1262">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="26a46-1263">IGMP ループバックの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="26a46-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="26a46-1265">**アイコン** ![I G M P ループバックの有効化アイコン](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="26a46-1266">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1266">**Description**</span></span>

<span data-ttu-id="26a46-1267">このイベントは、nx_igmp_loopback_enable を使用した IGMP ループバックの有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="26a46-1268">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1268">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1269">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1270">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1271">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1272">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="26a46-1273">IGMP マルチキャスト参加</span><span class="sxs-lookup"><span data-stu-id="26a46-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="26a46-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="26a46-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="26a46-1275">**アイコン** ![I G M P マルチキャスト参加アイコン](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="26a46-1276">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1276">**Description**</span></span>

<span data-ttu-id="26a46-1277">このイベントは、nx_igmp_multicast_join を使用したマルチキャスト グループの参加を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="26a46-1278">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1278">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1279">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1280">情報フィールド 2: グループ IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="26a46-1281">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1282">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="26a46-1283">IGMP マルチキャスト離脱</span><span class="sxs-lookup"><span data-stu-id="26a46-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="26a46-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="26a46-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="26a46-1285">**アイコン** ![I G M P マルチキャスト離脱アイコン](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="26a46-1286">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1286">**Description**</span></span>

<span data-ttu-id="26a46-1287">このイベントは、nx_igmp_multicast_leave を使用した、マルチキャスト グループの離脱を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="26a46-1288">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1288">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1289">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1290">情報フィールド 2: グループ IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="26a46-1291">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1292">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="26a46-1293">IP アドレス変更通知</span><span class="sxs-lookup"><span data-stu-id="26a46-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="26a46-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="26a46-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="26a46-1295">**アイコン** ![I P アドレス変更通知アイコン](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="26a46-1296">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1296">**Description**</span></span>

<span data-ttu-id="26a46-1297">このイベントは、nx_ip_address_change_notify を使用した IP 変更通知の登録を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="26a46-1298">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1298">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1299">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1300">情報フィールド 2: コールバック関数ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="26a46-1301">情報フィールド 3: 追加情報ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="26a46-1302">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="26a46-1303">IP アドレスの取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="26a46-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1304">nx_ip_address_get</span></span>

<span data-ttu-id="26a46-1305">**アイコン** ![I P アドレスの取得アイコン](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="26a46-1306">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1306">**Description**</span></span>

<span data-ttu-id="26a46-1307">このイベントは、nx_ip_address_get を使用した IP アドレスの取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="26a46-1308">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1308">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1309">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1310">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-1311">情報フィールド 3: ネットワーク マスク</span><span class="sxs-lookup"><span data-stu-id="26a46-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="26a46-1312">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="26a46-1313">IP アドレスの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="26a46-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1314">nx_ip_address_set</span></span>

<span data-ttu-id="26a46-1315">**アイコン** ![I P アドレスの設定アイコン](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="26a46-1316">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1316">**Description**</span></span>

<span data-ttu-id="26a46-1317">このイベントは nx_ip_address_set を使用した IP アドレスの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="26a46-1318">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1318">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1319">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1320">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-1321">情報フィールド 3: ネットワーク マスク</span><span class="sxs-lookup"><span data-stu-id="26a46-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="26a46-1322">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="26a46-1323">IP の作成</span><span class="sxs-lookup"><span data-stu-id="26a46-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="26a46-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="26a46-1324">nx_ip_create</span></span>

<span data-ttu-id="26a46-1325">**アイコン** ![I P の作成アイコン](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="26a46-1326">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1326">**Description**</span></span>

<span data-ttu-id="26a46-1327">このイベントは、nx_ip_create を使用した IP インスタンスの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="26a46-1328">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1328">**Information Fields**</span></span> 
- <span data-ttu-id="26a46-1329">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1330">情報フィールド 2: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="26a46-1331">情報フィールド 3: ネットワーク マスク</span><span class="sxs-lookup"><span data-stu-id="26a46-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="26a46-1332">情報フィールド 4: 既定のパケット プール ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="26a46-1333">IP の削除</span><span class="sxs-lookup"><span data-stu-id="26a46-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="26a46-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-1334">nx_ip_delete</span></span>

<span data-ttu-id="26a46-1335">**アイコン** ![I P の削除アイコン](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="26a46-1336">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1336">**Description**</span></span>

<span data-ttu-id="26a46-1337">このイベントは、nx_ip_delete を使用した IP インスタンスの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="26a46-1338">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1338">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1339">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1340">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1341">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1342">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="26a46-1343">IP ドライバーのダイレクト コマンド</span><span class="sxs-lookup"><span data-stu-id="26a46-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="26a46-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="26a46-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="26a46-1345">**アイコン** ![I P ドライバーのダイレクト コマンド アイコン](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="26a46-1346">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1346">**Description**</span></span>

<span data-ttu-id="26a46-1347">このイベントは、nx_ip_driver_direct_command を使用したダイレクト I/O ドライバー コマンドを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="26a46-1348">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1348">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1349">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1350">情報フィールド 2: ドライバー コマンド</span><span class="sxs-lookup"><span data-stu-id="26a46-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="26a46-1351">情報フィールド 3: 戻り値</span><span class="sxs-lookup"><span data-stu-id="26a46-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="26a46-1352">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="26a46-1353">IP 転送の無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="26a46-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="26a46-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="26a46-1355">**アイコン** ![I P 転送の無効化アイコン](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="26a46-1356">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1356">**Description**</span></span>

<span data-ttu-id="26a46-1357">このイベントは、nx_ip_forwarding_disable を使用した、IP 転送の無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="26a46-1358">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1358">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1359">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1360">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1361">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1362">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="26a46-1363">IP 転送の有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="26a46-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="26a46-1365">**アイコン** ![I P 転送の有効化アイコン](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="26a46-1366">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1366">**Description**</span></span>

<span data-ttu-id="26a46-1367">このイベントは、nx_ip_forwarding_enable を使用した IP 転送の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="26a46-1368">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1368">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1369">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1370">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1371">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1372">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="26a46-1373">IP フラグメントの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="26a46-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="26a46-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="26a46-1375">**アイコン** ![I P フラグメントの無効化アイコン](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="26a46-1376">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1376">**Description**</span></span>

<span data-ttu-id="26a46-1377">このイベントは、nx_ip_fragment_disable を使用した、IP フラグメントの無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="26a46-1378">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1378">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1379">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1380">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1381">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1382">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="26a46-1383">IP フラグメントの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="26a46-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="26a46-1385">**アイコン** ![I P フラグメントの有効化アイコン](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="26a46-1386">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1386">**Description**</span></span>

<span data-ttu-id="26a46-1387">このイベントは、nx_ip_fragment_enable を使用した IP フラグメントの有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="26a46-1388">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1388">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1389">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1390">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1391">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1392">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="26a46-1393">IP ゲートウェイ アドレスの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="26a46-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="26a46-1395">**アイコン** ![I P ゲートウェイ アドレスの設定アイコン](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="26a46-1396">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1396">**Description**</span></span>

<span data-ttu-id="26a46-1397">このイベントは、nx_ip_gateway_address_set を使用したゲートウェイ IP アドレスの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="26a46-1398">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1398">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1399">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1400">情報フィールド 2: ゲートウェイ IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="26a46-1401">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1402">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="26a46-1403">IP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="26a46-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1404">nx_ip_info_get</span></span>

<span data-ttu-id="26a46-1405">**アイコン** ![I P 情報の取得アイコン](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="26a46-1406">**説明** このイベントは、nx_ip_info_get を使用した IP 情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="26a46-1407">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1407">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1408">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1409">情報フィールド 2: 送信された IP バイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="26a46-1410">情報フィールド 3: 受信した IP バイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="26a46-1411">情報フィールド 4: ドロップされた IP パケット数</span><span class="sxs-lookup"><span data-stu-id="26a46-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="26a46-1412">IP インターフェイスのアタッチ</span><span class="sxs-lookup"><span data-stu-id="26a46-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="26a46-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="26a46-1413">nx_interface_attach</span></span>

<span data-ttu-id="26a46-1414">**アイコン** ![I P インターフェイスのアタッチ アイコン](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="26a46-1415">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1415">**Description**</span></span>

<span data-ttu-id="26a46-1416">このイベントは、nx_ip_interface_attach を使用して、IP インスタンスに接続されているセカンダリ ネットワーク インターフェイスを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="26a46-1417">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1417">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1418">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1419">情報フィールド 2: インターフェイスの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="26a46-1420">情報フィールド 3: IP インターフェイス テーブルへのインデックス</span><span class="sxs-lookup"><span data-stu-id="26a46-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="26a46-1421">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="26a46-1422">IP インターフェイス情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="26a46-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="26a46-1424">**アイコン** ![ IP インターフェイス情報の取得アイコン](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="26a46-1425">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1425">**Description**</span></span>

<span data-ttu-id="26a46-1426">このイベントは、nx_ip_interface_info_get を使用して、指定されたネットワーク インターフェイスから取得した情報を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="26a46-1427">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1427">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1428">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1429">情報フィールド 2: インターフェイスの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="26a46-1430">情報フィールド 3: インターフェイスの MAC アドレスの MSB</span><span class="sxs-lookup"><span data-stu-id="26a46-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="26a46-1431">情報フィールド 4: インターフェイスの MAC アドレスの LSB</span><span class="sxs-lookup"><span data-stu-id="26a46-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="26a46-1432">IP 生パケットの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="26a46-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="26a46-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="26a46-1434">**アイコン** ![I P 生パケットの無効化アイコン](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="26a46-1435">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1435">**Description**</span></span>

<span data-ttu-id="26a46-1436">このイベントは、nx_ip_raw_packet_disable を使用した生 IP パケット通信の無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="26a46-1437">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1437">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1438">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1439">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1440">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1441">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="26a46-1442">IP 生パケットの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="26a46-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="26a46-1444">**アイコン** ![I P 生パケットの有効化アイコン](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="26a46-1445">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1445">**Description**</span></span>

<span data-ttu-id="26a46-1446">このイベントは、nx_ip_raw_packet_enable を使用した生 IP パケット通信の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="26a46-1447">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1447">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1448">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1449">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1450">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1451">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="26a46-1452">IP 生パケットの受信</span><span class="sxs-lookup"><span data-stu-id="26a46-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="26a46-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="26a46-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="26a46-1454">**アイコン** ![I P 生パケットの受信アイコン](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="26a46-1455">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1455">**Description**</span></span>

<span data-ttu-id="26a46-1456">このイベントは、nx_ip_raw_packet_receive を使用した生 IP パケットの受信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="26a46-1457">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1457">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1458">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1459">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-1460">情報フィールド 3: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="26a46-1461">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="26a46-1462">IP 生パケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="26a46-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="26a46-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="26a46-1464">**アイコン** ![I P 生パケット送信アイコン](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="26a46-1465">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1465">**Description**</span></span>

<span data-ttu-id="26a46-1466">このイベントは、nx_ip_raw_packet_send を使用した生 IP パケットの送信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="26a46-1467">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1467">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1468">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1469">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-1470">情報フィールド 3: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="26a46-1471">情報フィールド 4: サービスの種類</span><span class="sxs-lookup"><span data-stu-id="26a46-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="26a46-1472">IP 静的ルートの追加</span><span class="sxs-lookup"><span data-stu-id="26a46-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="26a46-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="26a46-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="26a46-1474">**アイコン** ![I P 静的ルートの追加アイコン](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="26a46-1475">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1475">**Description**</span></span>

<span data-ttu-id="26a46-1476">このイベントは、nx_ip_static_route_add を使用して、IP インスタンスのルーティング テーブルに追加される静的ルートを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="26a46-1477">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1477">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1478">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1479">情報フィールド 2: ネットワーク アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="26a46-1480">情報フィールド 3: ネットワーク マスク</span><span class="sxs-lookup"><span data-stu-id="26a46-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="26a46-1481">情報フィールド 4: ネクスト ホップ</span><span class="sxs-lookup"><span data-stu-id="26a46-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="26a46-1482">IP 静的ルートの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="26a46-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="26a46-1484">**アイコン** ![I P 静的ルートの削除アイコン](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="26a46-1485">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1485">**Description**</span></span>

<span data-ttu-id="26a46-1486">このイベントは、nx_ip_static_route_delete を使用して、IP インスタンス ルーティング テーブルから削除される静的ルートを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="26a46-1487">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1487">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1488">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1489">情報フィールド 2: ネットワーク アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="26a46-1490">情報フィールド 3: ネットワーク マスク</span><span class="sxs-lookup"><span data-stu-id="26a46-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="26a46-1491">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="26a46-1492">IP 状態チェック</span><span class="sxs-lookup"><span data-stu-id="26a46-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="26a46-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="26a46-1493">nx_ip_status_check</span></span>

<span data-ttu-id="26a46-1494">**アイコン** ![I P 状態チェック アイコン](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="26a46-1495">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1495">**Description**</span></span>

<span data-ttu-id="26a46-1496">このイベントは、nx_ip_status_check を使用した IP 状態の確認を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="26a46-1497">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="26a46-1497">Information Fields</span></span> 

- <span data-ttu-id="26a46-1498">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="26a46-1499">情報フィールド 2: 要求された状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="26a46-1500">情報フィールド 3: 実際の状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="26a46-1501">情報フィールド 4: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="26a46-1502">IPSEC の有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="26a46-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="26a46-1504">**アイコン** ![I P S E C の有効化アイコン](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="26a46-1505">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1505">**Description**</span></span>

<span data-ttu-id="26a46-1506">このイベントは、nx_ipsec_enable を使用して、指定された IP インスタンスの IPSec サービスを有効化することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="26a46-1507">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1507">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1508">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1509">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1510">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1511">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="26a46-1512">パケットの割り当て</span><span class="sxs-lookup"><span data-stu-id="26a46-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="26a46-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="26a46-1513">nx_packet_allocate</span></span>

<span data-ttu-id="26a46-1514">**アイコン** ![パケットの割り当てアイコン](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="26a46-1515">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1515">**Description**</span></span>

<span data-ttu-id="26a46-1516">このイベントは、nx_packet_allocate を使用したパケットの割り当てを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="26a46-1517">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1517">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1518">情報フィールド 1: パケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="26a46-1519">情報フィールド 2: 割り当てられたパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="26a46-1520">情報フィールド 3: パケットの種類</span><span class="sxs-lookup"><span data-stu-id="26a46-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="26a46-1521">情報フィールド 4: 使用可能なパケット</span><span class="sxs-lookup"><span data-stu-id="26a46-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="26a46-1522">パケット コピー</span><span class="sxs-lookup"><span data-stu-id="26a46-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="26a46-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="26a46-1523">nx_packet_copy</span></span>

<span data-ttu-id="26a46-1524">**アイコン** ![パケット コピー アイコン](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="26a46-1525">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1525">**Description**</span></span>

<span data-ttu-id="26a46-1526">このイベントは、nx_packet_copy を使用したパケットのコピーを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="26a46-1527">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1527">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1528">情報フィールド 2: 新しいパケット ポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="26a46-1529">情報フィールド 3: パケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="26a46-1530">情報フィールド 4: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="26a46-1531">パケット データの追加</span><span class="sxs-lookup"><span data-stu-id="26a46-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="26a46-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="26a46-1532">nx_packet_data_append</span></span>

<span data-ttu-id="26a46-1533">**アイコン** ![パケット データの追加アイコン](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="26a46-1534">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1534">**Description**</span></span>

<span data-ttu-id="26a46-1535">このイベントは、nx_packet_data_append を使用したパケットへのデータの追加を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="26a46-1536">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1536">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1537">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="26a46-1538">情報フィールド 2: データへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="26a46-1539">情報フィールド 3: データのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="26a46-1540">情報フィールド 4: パケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="26a46-1541">パケット データ抽出オフセット</span><span class="sxs-lookup"><span data-stu-id="26a46-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="26a46-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="26a46-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="26a46-1543">**アイコン** ![パケット データ抽出オフセット アイコン](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="26a46-1544">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1544">**Description**</span></span>

<span data-ttu-id="26a46-1545">このイベントは、nx_udp_source_extract_offset を使用してパケットから指定されたバッファーに抽出されるパケット データを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="26a46-1546">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1546">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1547">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="26a46-1548">情報フィールド 2: 指定されたバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="26a46-1549">情報フィールド 3: コピーされたバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="26a46-1550">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="26a46-1551">パケット データ取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="26a46-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="26a46-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="26a46-1553">**アイコン** ![パケット データ取得アイコン](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="26a46-1554">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1554">**Description**</span></span>

<span data-ttu-id="26a46-1555">このイベントは、nx_packet_data_retrieve を使用したパケットからのデータ取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="26a46-1556">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1556">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1557">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="26a46-1558">情報フィールド 2: バッファーの先頭へのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="26a46-1559">情報フィールド 3: コピーされたバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="26a46-1560">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="26a46-1561">パケット長の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="26a46-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1562">nx_packet_length_get</span></span>

<span data-ttu-id="26a46-1563">**アイコン** ![パケット長の取得アイコン](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="26a46-1564">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1564">**Description**</span></span>

<span data-ttu-id="26a46-1565">このイベントは、nx_packet_length_get を使用したパケット長の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="26a46-1566">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1566">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1567">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="26a46-1568">情報フィールド 2: パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="26a46-1569">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1570">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="26a46-1571">パケット プールの作成</span><span class="sxs-lookup"><span data-stu-id="26a46-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="26a46-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="26a46-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="26a46-1573">**アイコン** ![パケット プールの作成アイコン](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="26a46-1574">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1574">**Description**</span></span>

<span data-ttu-id="26a46-1575">このイベントは、nx_packet_pool_create を使用したパケット プールの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="26a46-1576">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1576">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1577">情報フィールド 1: パケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="26a46-1578">情報フィールド 2: パケット ペイロードのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="26a46-1579">情報フィールド 3: プール メモリ領域へのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="26a46-1580">情報フィールド 4: プール メモリ領域のサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="26a46-1581">パケット プールの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="26a46-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="26a46-1583">**アイコン** ![パケット プールの削除アイコン](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="26a46-1584">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1584">**Description**</span></span>

<span data-ttu-id="26a46-1585">このイベントは、nx_packet_pool_delete を使用したパケット プールの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="26a46-1586">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1586">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1587">情報フィールド 1: パケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="26a46-1588">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1589">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1590">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="26a46-1591">パケット プール情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="26a46-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="26a46-1593">**アイコン** ![パケット プール情報の取得アイコン](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="26a46-1594">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1594">**Description**</span></span>

<span data-ttu-id="26a46-1595">このイベントは、nx_packet_pool_info_get を使用したパケット プール情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="26a46-1596">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1596">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1597">情報フィールド 1: パケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="26a46-1598">情報フィールド 2: 合計パケット数</span><span class="sxs-lookup"><span data-stu-id="26a46-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="26a46-1599">情報フィールド 3: 使用可能なパケット数</span><span class="sxs-lookup"><span data-stu-id="26a46-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="26a46-1600">情報フィールド 4: 空の要求</span><span class="sxs-lookup"><span data-stu-id="26a46-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="26a46-1601">パケット解放</span><span class="sxs-lookup"><span data-stu-id="26a46-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="26a46-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="26a46-1602">nx_packet_data_release</span></span>

<span data-ttu-id="26a46-1603">**アイコン** ![パケット解放アイコン](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="26a46-1604">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1604">**Description**</span></span>

<span data-ttu-id="26a46-1605">このイベントは、nx_packet_release を使用したパケット解放を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="26a46-1606">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1606">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1607">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="26a46-1608">情報フィールド 2: パケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="26a46-1609">情報フィールド 3: 使用可能なパケット数</span><span class="sxs-lookup"><span data-stu-id="26a46-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="26a46-1610">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="26a46-1611">パケット送信解放</span><span class="sxs-lookup"><span data-stu-id="26a46-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="26a46-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="26a46-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="26a46-1613">**アイコン** ![パケット送信解放アイコン](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="26a46-1614">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1614">**Description**</span></span>

<span data-ttu-id="26a46-1615">このイベントは、nx_packet_transmit_release を使用した送信パケットの解放を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="26a46-1616">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1616">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1617">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="26a46-1618">情報フィールド 2: パケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="26a46-1619">情報フィールド 3: 使用可能なパケット数</span><span class="sxs-lookup"><span data-stu-id="26a46-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="26a46-1620">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="26a46-1621">RARP の無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="26a46-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="26a46-1622">nx_rarp_disable</span></span>

<span data-ttu-id="26a46-1623">**アイコン** ![R A R P の無効化アイコン](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="26a46-1624">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1624">**Description**</span></span>

<span data-ttu-id="26a46-1625">このイベントは、nx_rarp_disable を使用した RARP の無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="26a46-1626">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1626">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1627">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1628">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1629">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1630">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="26a46-1631">RARP 有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="26a46-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1632">nx_rarp_enable</span></span>

<span data-ttu-id="26a46-1633">**アイコン** ![R A R P 有効化アイコン](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="26a46-1634">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1634">**Description**</span></span>

<span data-ttu-id="26a46-1635">このイベントは、nx_rarp_enable を使用した RARP の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="26a46-1636">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1636">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1637">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1638">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1639">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1640">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="26a46-1641">RARP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="26a46-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="26a46-1643">**アイコン** ![R A R P 情報の取得アイコン](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="26a46-1644">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1644">**Description**</span></span>

<span data-ttu-id="26a46-1645">このイベントは、nx_rarp_info_get を使用した RARP 情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="26a46-1646">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1646">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1647">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1648">情報フィールド 2: 送信された要求</span><span class="sxs-lookup"><span data-stu-id="26a46-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="26a46-1649">情報フィールド 3: 受信した応答</span><span class="sxs-lookup"><span data-stu-id="26a46-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="26a46-1650">情報フィールド 4: 無効な応答</span><span class="sxs-lookup"><span data-stu-id="26a46-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="26a46-1651">システム初期化</span><span class="sxs-lookup"><span data-stu-id="26a46-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="26a46-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="26a46-1652">nx_system_initialize</span></span>

<span data-ttu-id="26a46-1653">**アイコン** ![システム初期化アイコン](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="26a46-1654">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1654">**Description**</span></span>

<span data-ttu-id="26a46-1655">このイベントは、nx_system_initialize を使用した NetX の初期化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="26a46-1656">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1656">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1657">情報フィールド 1: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="26a46-1658">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1659">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1660">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="26a46-1661">TCP クライアント ソケット バインド</span><span class="sxs-lookup"><span data-stu-id="26a46-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="26a46-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="26a46-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="26a46-1663">**アイコン** ![T P クライアント ソケット バインド アイコン](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="26a46-1664">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1664">**Description**</span></span>

<span data-ttu-id="26a46-1665">このイベントは、nx_tcp_client_socket_bind を介してクライアント ソケットをポートにバインドすることを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="26a46-1666">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1666">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1667">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1668">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1669">情報フィールド 3: 要求されたポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="26a46-1670">情報フィールド 4: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="26a46-1671">TCP クライアント ソケット接続</span><span class="sxs-lookup"><span data-stu-id="26a46-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="26a46-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="26a46-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="26a46-1673">**アイコン** ![T C P クライアント ソケット接続アイコン](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="26a46-1674">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1674">**Description**</span></span>

<span data-ttu-id="26a46-1675">このイベントは、nx_tcp_client_socket_connect を使用したクライアント ソケット接続の確立を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="26a46-1676">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1676">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1677">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1678">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1679">情報フィールド 3: サーバーの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="26a46-1680">情報フィールド 4: 要求されたサーバー ポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="26a46-1681">TCP クライアント ソケット ポートの取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="26a46-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="26a46-1683">**アイコン** ![T C P クライアント ソケット ポートの取得アイコン](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="26a46-1684">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1684">**Description**</span></span>

<span data-ttu-id="26a46-1685">このイベントは、nx_tcp_client_socket_port_get を使用したクライアント ソケット ポート番号の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="26a46-1686">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1686">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1687">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1688">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1689">情報フィールド 3: ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="26a46-1690">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="26a46-1691">TCP クライアント ソケットのバインド解除</span><span class="sxs-lookup"><span data-stu-id="26a46-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="26a46-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="26a46-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="26a46-1693">**アイコン** ![T C P クライアント ソケットのバインド解除アイコン](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="26a46-1694">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1694">**Description**</span></span>

<span data-ttu-id="26a46-1695">このイベントは、nx_tcp_client_socket_unbind を使用した、ソケットに関連付けられているポートのバインド解除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="26a46-1696">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1696">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1697">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1698">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1699">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1700">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="26a46-1701">TCP 有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="26a46-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1702">nx_tcp_enable</span></span>

<span data-ttu-id="26a46-1703">**アイコン** ![T C P 有効化アイコン](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="26a46-1704">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1704">**Description**</span></span>

<span data-ttu-id="26a46-1705">このイベントは、nx_tcp_enable を使用した TCP の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="26a46-1706">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1706">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1707">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1708">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1709">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1710">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="26a46-1711">TCP 空きポート検索 TCP 空きポート検索</span><span class="sxs-lookup"><span data-stu-id="26a46-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="26a46-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="26a46-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="26a46-1713">**アイコン** ![T CP 空きポート検索アイコン](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="26a46-1714">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1714">**Description**</span></span>

<span data-ttu-id="26a46-1715">このイベントは、nx_tcp_free_port_find を使用した、TCP 空きポートの検索を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="26a46-1716">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1716">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1717">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1718">情報フィールド 2: ポート番号検索の開始</span><span class="sxs-lookup"><span data-stu-id="26a46-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="26a46-1719">情報フィールド 3: 空きポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="26a46-1720">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="26a46-1721">TCP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="26a46-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="26a46-1723">**アイコン** ![T C P 情報の取得アイコン](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="26a46-1724">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1724">**Description**</span></span>

<span data-ttu-id="26a46-1725">このイベントは、nx_tcp_info_get を使用して、指定された IP インスタンスの TCP 情報を取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="26a46-1726">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1726">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1727">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1728">情報フィールド 2: 送信されたバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="26a46-1729">情報フィールド 3: 受信したバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="26a46-1730">情報フィールド 4: 無効なパケット数</span><span class="sxs-lookup"><span data-stu-id="26a46-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="26a46-1731">TCP サーバー ソケットの受け入れ</span><span class="sxs-lookup"><span data-stu-id="26a46-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="26a46-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="26a46-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="26a46-1733">**アイコン** ![T C P サーバー ソケットの受け入れアイコン](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="26a46-1734">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1734">**Description**</span></span>

<span data-ttu-id="26a46-1735">このイベントは、nx_tcp_server_socket_accept を使用して、アクティブな接続要求を受信した後のサーバー ソケットの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="26a46-1736">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1736">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1737">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1738">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1739">情報フィールド 3: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="26a46-1740">情報フィールド 4: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="26a46-1741">TCP サーバー ソケットのリッスン</span><span class="sxs-lookup"><span data-stu-id="26a46-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="26a46-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="26a46-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="26a46-1743">**アイコン** ![T C P サーバー ソケットのリッスン アイコン](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="26a46-1744">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1744">**Description**</span></span>

<span data-ttu-id="26a46-1745">このイベントは、nx_tcp_server_socket_listen を使用して、指定された TCP ポートに対するリッスン要求とサーバー ソケットの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="26a46-1746">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1746">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1747">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1748">情報フィールド 2: TCP ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="26a46-1749">情報フィールド 3: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1750">情報フィールド 4: キューに入れることができる接続の最大数</span><span class="sxs-lookup"><span data-stu-id="26a46-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="26a46-1751">TCP サーバー ソケットの再リッスン</span><span class="sxs-lookup"><span data-stu-id="26a46-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="26a46-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="26a46-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="26a46-1753">**アイコン** ![T C P サーバー ソケットの再リッスン アイコン](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="26a46-1754">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1754">**Description**</span></span>

<span data-ttu-id="26a46-1755">このイベントは、nx_tcp_server_socket_relisten を使用して、指定された TCP ポート上の既存のリッスン要求に対して別のサーバー ソケットを登録することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="26a46-1756">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1756">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1757">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1758">情報フィールド 2: TCP ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="26a46-1759">情報フィールド 3: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1760">情報フィールド 4: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="26a46-1761">TCP サーバー ソケットの受け入れ解除</span><span class="sxs-lookup"><span data-stu-id="26a46-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="26a46-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="26a46-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="26a46-1763">**アイコン** ![T C P サーバー ソケットの受け入れ解除アイコン](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="26a46-1764">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1764">**Description**</span></span>

<span data-ttu-id="26a46-1765">このイベントは、nx_tcp_server_socket_unaccept を使用して、以前のパッシブ接続を受信するポートとの関連付けからサーバー ソケットを削除することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="26a46-1766">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1766">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1767">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1768">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1769">情報フィールド 3: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="26a46-1770">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="26a46-1771">TCP サーバー ソケットのリッスン解除 TCP サーバー ソケットのリッスン解除</span><span class="sxs-lookup"><span data-stu-id="26a46-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="26a46-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="26a46-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="26a46-1773">**アイコン** ![T C P サーバー ソケットのリッスン解除アイコン](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="26a46-1774">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1774">**Description**</span></span>

<span data-ttu-id="26a46-1775">このイベントは、nx_tcp_server_socket_unlisten を使用して、指定された TCP ポートに対する前のリッスン要求を削除することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="26a46-1776">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1776">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1777">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1778">情報フィールド 2: TCP ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="26a46-1779">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1780">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="26a46-1781">使用可能な TCP ソケット バイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="26a46-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="26a46-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="26a46-1783">**アイコン** ![使用可能な T C P ソケット バイト数アイコン](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="26a46-1784">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1784">**Description**</span></span>

<span data-ttu-id="26a46-1785">このイベントは、nx_tcp_socket_bytes_available を使用して、指定された TCP 受信ソケットで現在使用できるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="26a46-1786">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1786">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1787">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1788">情報フィールド 2: TCP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="26a46-1789">情報フィールド 3: ソケットで受信したバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="26a46-1790">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="26a46-1791">TCP ソケットの作成</span><span class="sxs-lookup"><span data-stu-id="26a46-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="26a46-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="26a46-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="26a46-1793">**アイコン** ![T C P ソケットの作成アイコン](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="26a46-1794">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1794">**Description**</span></span>

<span data-ttu-id="26a46-1795">このイベントは、nx_tcp_socket_create を使用した TCP ソケットの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="26a46-1796">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1796">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1797">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1798">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1799">情報フィールド 3: サービスの種類</span><span class="sxs-lookup"><span data-stu-id="26a46-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="26a46-1800">情報フィールド 4: 受信ウィンドウのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="26a46-1801">TCP ソケットの削除</span><span class="sxs-lookup"><span data-stu-id="26a46-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="26a46-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="26a46-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="26a46-1803">**アイコン** ![T C P ソケットの削除アイコン](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="26a46-1804">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1804">**Description**</span></span>

<span data-ttu-id="26a46-1805">このイベントは、nx_tcp_socket_delete を使用したソケットの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="26a46-1806">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1806">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1807">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1808">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1809">情報フィールド 3: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="26a46-1810">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="26a46-1811">TCP ソケットの切断</span><span class="sxs-lookup"><span data-stu-id="26a46-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="26a46-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="26a46-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="26a46-1813">**アイコン** ![T C P ソケットの切断アイコン](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="26a46-1814">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1814">**Description**</span></span>

<span data-ttu-id="26a46-1815">このイベントは、nx_tcp_socket_disconnect を使用したソケットの切断を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="26a46-1816">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1816">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1817">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1818">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1819">情報フィールド 3: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="26a46-1820">情報フィールド 4: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="26a46-1821">TCP ソケット情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="26a46-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="26a46-1823">**アイコン** ![T C P ソケット情報の取得アイコン](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="26a46-1824">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1824">**Description**</span></span>

<span data-ttu-id="26a46-1825">このイベントは、nx_tcp_socket_info_get を使用したソケットに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="26a46-1826">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1826">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1827">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1828">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1829">情報フィールド 3: このソケット経由で送信されたバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="26a46-1830">情報フィールド 4: このソケット経由で受信したバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="26a46-1831">TCP ソケット MSS の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="26a46-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="26a46-1833">**アイコン** ![T C P ソケット M S S の取得アイコン](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="26a46-1834">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1834">**Description**</span></span>

<span data-ttu-id="26a46-1835">このイベントは、nx_tcp_socket_mss_get を使用したソケットの MSS 取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="26a46-1836">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1836">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1837">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1838">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1839">情報フィールド 3: 最大セグメント サイズ (MSS)</span><span class="sxs-lookup"><span data-stu-id="26a46-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="26a46-1840">情報フィールド 4: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="26a46-1841">TCP ソケット MSS ピアの取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="26a46-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="26a46-1843">**アイコン** ![T C P ソケット M S S ピアの取得アイコン](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="26a46-1844">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1844">**Description**</span></span>

<span data-ttu-id="26a46-1845">このイベントは、nx_tcp_socket_mss_peer_get を使用して、ソケットのピアの MSS 値を取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="26a46-1846">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1846">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1847">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1848">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1849">情報フィールド 3: ピアの MSS</span><span class="sxs-lookup"><span data-stu-id="26a46-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="26a46-1850">情報フィールド 4: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="26a46-1851">TCP ソケット MSS の設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="26a46-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="26a46-1853">**アイコン** ![T C P ソケット M S S の設定アイコン](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="26a46-1854">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1854">**Description**</span></span>

<span data-ttu-id="26a46-1855">このイベントは、nx_tcp_socket_mss_set を使用したソケットの MSS 設定を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="26a46-1856">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1856">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1857">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1858">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1859">情報フィールド 3: MSS</span><span class="sxs-lookup"><span data-stu-id="26a46-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="26a46-1860">情報フィールド 4: ソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="26a46-1861">TCP ソケット ピア情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="26a46-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="26a46-1863">**アイコン** ![T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="26a46-1864">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1864">**Description**</span></span>

<span data-ttu-id="26a46-1865">このイベントは、nx_tcp_socket_peer_info_get を使用して、ピア (接続ホストなど) の IP アドレスとポートについて TCP ソケットから取得された情報を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="26a46-1866">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1866">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1867">情報フィールド 1: TCP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="26a46-1868">情報フィールド 2: ピア IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="26a46-1869">情報フィールド 3: ピア ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="26a46-1870">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="26a46-1871">TCP ソケット受信</span><span class="sxs-lookup"><span data-stu-id="26a46-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="26a46-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="26a46-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="26a46-1873">**アイコン** ![T C P ソケット受信アイコン](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="26a46-1874">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1874">**Description**</span></span>

<span data-ttu-id="26a46-1875">このイベントは、nx_tcp_socket_receive を使用したソケットからのデータ受信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="26a46-1876">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1876">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1877">情報フィールド 1: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1878">情報フィールド 2: 受信したパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="26a46-1879">情報フィールド 3: 受信パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="26a46-1880">情報フィールド 4: 受信シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="26a46-1881">TCP ソケット受信通知</span><span class="sxs-lookup"><span data-stu-id="26a46-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="26a46-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="26a46-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="26a46-1883">**アイコン** ![T C P ソケット受信通知アイコン](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="26a46-1884">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1884">**Description**</span></span>

<span data-ttu-id="26a46-1885">このイベントは、nx_tcp_socket_receive_notify を使用した、ソケットの受信通知コールバックの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="26a46-1886">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1886">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1887">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1888">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1889">情報フィールド 3: 受信通知コールバックへのポインター 情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="26a46-1890">TCP ソケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="26a46-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="26a46-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="26a46-1892">**アイコン** ![T C P ソケット送信アイコン](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="26a46-1893">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1893">**Description**</span></span>

<span data-ttu-id="26a46-1894">このイベントは、nx_tcp_socket_send を使用したソケット上のデータの送信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="26a46-1895">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1895">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1896">情報フィールド 1: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1897">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-1898">情報フィールド 3: パケットの長さ</span><span class="sxs-lookup"><span data-stu-id="26a46-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="26a46-1899">情報フィールド 4: 転送シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="26a46-1900">TCP ソケット状態待機</span><span class="sxs-lookup"><span data-stu-id="26a46-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="26a46-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="26a46-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="26a46-1902">**アイコン** ![T C P ソケット状態待機アイコン](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="26a46-1903">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1903">**Description**</span></span>

<span data-ttu-id="26a46-1904">このイベントは、nx_tcp_socket_state_wait を使用して、ソケットが特定の状態になるのを待機していることを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="26a46-1905">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1905">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1906">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1907">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1908">情報フィールド 3: 期待されるソケット状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="26a46-1909">情報フィールド 4: 前のソケットの状態</span><span class="sxs-lookup"><span data-stu-id="26a46-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="26a46-1910">TCP ソケット送信の構成</span><span class="sxs-lookup"><span data-stu-id="26a46-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="26a46-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="26a46-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="26a46-1912">**アイコン** ![T C P ソケット送信の構成アイコン](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="26a46-1913">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1913">**Description**</span></span>

<span data-ttu-id="26a46-1914">このイベントは、nx_tcp_socket_transmit_configure を使用したソケットの送信オプションの構成を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="26a46-1915">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1915">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1916">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1917">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1918">情報フィールド 3: 送信キューの深さ</span><span class="sxs-lookup"><span data-stu-id="26a46-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="26a46-1919">情報フィールド 4: タイムアウト値</span><span class="sxs-lookup"><span data-stu-id="26a46-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="26a46-1920">TCP ソケット ウィンドウ更新通知の設定</span><span class="sxs-lookup"><span data-stu-id="26a46-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="26a46-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="26a46-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="26a46-1922">**アイコン** ![T C P ソケット ウィンドウ更新通知の設定アイコン](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="26a46-1923">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1923">**Description**</span></span>

<span data-ttu-id="26a46-1924">このイベントは、nx_tcp_window_update_notify_set を使用して、リモート ホストの受信ウィンドウが増加したことの通知を受信する TCP ソケットを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="26a46-1925">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1925">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1926">情報フィールド 1: TCP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="26a46-1927">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1928">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1929">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="26a46-1930">UDP 有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="26a46-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1931">nx_udp_enable</span></span>

<span data-ttu-id="26a46-1932">**アイコン** ![U D P 有効化アイコン](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="26a46-1933">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1933">**Description**</span></span>

<span data-ttu-id="26a46-1934">このイベントは、nx_udp_enable を使用した UDP の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="26a46-1935">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1935">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1936">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1937">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="26a46-1938">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1939">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="26a46-1940">UDP 空きポートの検索</span><span class="sxs-lookup"><span data-stu-id="26a46-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="26a46-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="26a46-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="26a46-1942">**アイコン** ![U D P 空きポートの検索アイコン](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="26a46-1943">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1943">**Description**</span></span>

<span data-ttu-id="26a46-1944">このイベントは、nx_udp_free_port_find を使用した、空き UDP ポートの検索を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="26a46-1945">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1945">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1946">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1947">情報フィールド 2: 検索の開始ポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="26a46-1948">情報フィールド 3: 空きポート</span><span class="sxs-lookup"><span data-stu-id="26a46-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="26a46-1949">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="26a46-1950">UDP 情報の取得</span><span class="sxs-lookup"><span data-stu-id="26a46-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="26a46-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="26a46-1951">nx_udp_info_get</span></span>

<span data-ttu-id="26a46-1952">**アイコン** ![U D P 情報の取得アイコン](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="26a46-1953">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1953">**Description**</span></span>

<span data-ttu-id="26a46-1954">このイベントは、nx_udp_info_get を使用した情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="26a46-1955">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1955">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1956">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1957">情報フィールド 2: 送信された UDP バイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="26a46-1958">情報フィールド 3: 受信した UDP バイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="26a46-1959">情報フィールド 4: 無効なパケット</span><span class="sxs-lookup"><span data-stu-id="26a46-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="26a46-1960">UDP ソケット バインド</span><span class="sxs-lookup"><span data-stu-id="26a46-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="26a46-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="26a46-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="26a46-1962">**アイコン** ![U D P ソケット バインド アイコン](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="26a46-1963">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1963">**Description**</span></span>

<span data-ttu-id="26a46-1964">このイベントは、nx_udp_socket_bind を使用したポートへの UDP ソケットのバインドを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="26a46-1965">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1965">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1966">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1967">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1968">情報フィールド 3: ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="26a46-1969">情報フィールド 4: 待機オプション</span><span class="sxs-lookup"><span data-stu-id="26a46-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="26a46-1970">使用可能な UDP ソケット バイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="26a46-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="26a46-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="26a46-1972">**アイコン** ![使用可能な U D P ソケット バイト数アイコン](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="26a46-1973">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1973">**Description**</span></span>

<span data-ttu-id="26a46-1974">このイベントは、nx_udp_socket_bytes_available を使用して UDP ソケットで受信した現在のバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="26a46-1975">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1975">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1976">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1977">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1978">情報フィールド 3: ソケットで受信したバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="26a46-1979">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="26a46-1980">UDP ソケット チェックサムの無効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="26a46-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="26a46-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="26a46-1982">**アイコン** ![U D P ソケット チェックサムの無効化アイコン](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="26a46-1983">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1983">**Description**</span></span>

<span data-ttu-id="26a46-1984">このイベントは、nx_udp_socket_checksum_disable を使用した UDP ソケット上のデータのチェックサムの無効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="26a46-1985">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1985">**Information Fields**</span></span> 

- <span data-ttu-id="26a46-1986">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1987">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1988">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1989">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="26a46-1990">UDP ソケット チェックサムの有効化</span><span class="sxs-lookup"><span data-stu-id="26a46-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="26a46-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="26a46-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="26a46-1992">**アイコン** ![U D P ソケット チェックサムの有効化アイコン](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="26a46-1993">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-1993">**Description**</span></span>

<span data-ttu-id="26a46-1994">このイベントは、nx_udp_socket_checksum_enable を使用したソケットでのチェックサム処理の有効化を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="26a46-1995">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-1995">**Information Fields**</span></span>

- <span data-ttu-id="26a46-1996">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-1997">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-1998">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-1999">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="26a46-2000">UDP ソケットの作成</span><span class="sxs-lookup"><span data-stu-id="26a46-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="26a46-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="26a46-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="26a46-2002">**アイコン** ![U D P ソケット作成アイコン](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="26a46-2003">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2003">**Description**</span></span>

<span data-ttu-id="26a46-2004">このイベントは、nx_udp_socket_create を使用した UDP ソケットの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="26a46-2005">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2005">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2006">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2007">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-2008">情報フィールド 3: サービスの種類</span><span class="sxs-lookup"><span data-stu-id="26a46-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="26a46-2009">情報フィールド 4: 最大受信キュー</span><span class="sxs-lookup"><span data-stu-id="26a46-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="26a46-2010">UDP ソケット削除イベント</span><span class="sxs-lookup"><span data-stu-id="26a46-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="26a46-2011">nx_udp_socket_delete イベント</span><span class="sxs-lookup"><span data-stu-id="26a46-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="26a46-2012">**アイコン** ![U D P ソケット削除イベント アイコン](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="26a46-2013">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2013">**Description**</span></span>

<span data-ttu-id="26a46-2014">このイベントは、nx_udp_socket_delete を使用した UDP ソケットの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="26a46-2015">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2015">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2016">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2017">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-2018">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-2019">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="26a46-2020">UDP ソケット情報の取得イベント</span><span class="sxs-lookup"><span data-stu-id="26a46-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="26a46-2021">nx_udp_socket_info_get イベント</span><span class="sxs-lookup"><span data-stu-id="26a46-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="26a46-2022">**アイコン** ![U D P ソケット情報の取得イベント アイコン](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="26a46-2023">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2023">**Description**</span></span>

<span data-ttu-id="26a46-2024">このイベントは、nx_udp_socket_info_get を使用して UDP ソケットに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="26a46-2025">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2025">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2026">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2027">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-2028">情報フィールド 3: ソケット経由で送信されたバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="26a46-2029">情報フィールド 4: ソケット経由で受信したバイト数</span><span class="sxs-lookup"><span data-stu-id="26a46-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="26a46-2030">UDP ソケット インターフェイスの設定</span><span class="sxs-lookup"><span data-stu-id="26a46-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="26a46-2031">nx_udp_socket_interface_set イベント</span><span class="sxs-lookup"><span data-stu-id="26a46-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="26a46-2032">**アイコン** ![U D P ソケット インターフェイスの設定アイコン](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="26a46-2033">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2033">**Description**</span></span>

<span data-ttu-id="26a46-2034">このイベントは、nx_udp_socket_interface_set を使用して、指定された UDP ソケットの発信インターフェイスを、指定されたインターフェイスで設定することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="26a46-2035">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2035">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2036">情報フィールド 1: UDP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="26a46-2037">情報フィールド 2: ソケットのインターフェイスに対応するインデックス</span><span class="sxs-lookup"><span data-stu-id="26a46-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="26a46-2038">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="26a46-2039">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="26a46-2040">UDP ソケット ポートの取得</span><span class="sxs-lookup"><span data-stu-id="26a46-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="26a46-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="26a46-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="26a46-2042">**アイコン** ![U D P ソケット ポートの取得アイコン](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="26a46-2043">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2043">**Description**</span></span>

<span data-ttu-id="26a46-2044">このイベントは、nx_udp_socket_port_get を使用して、指定された UDP ソケットがバインドされている UDP ポートを取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="26a46-2045">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2045">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2046">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2047">情報フィールド 2: UDP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="26a46-2048">情報フィールド 3: ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="26a46-2049">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="26a46-2050">UDP ソケット受信</span><span class="sxs-lookup"><span data-stu-id="26a46-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="26a46-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="26a46-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="26a46-2052">**アイコン** ![U D P ソケット受信アイコン](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="26a46-2053">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2053">**Description**</span></span>

<span data-ttu-id="26a46-2054">このイベントは、nx_udp_socket_receive を使用して、指定された UDP ソケットの受信データを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="26a46-2055">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2055">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2056">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2057">情報フィールド 2: UDP ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="26a46-2058">情報フィールド 3: 受信したパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="26a46-2059">情報フィールド 4: 受信したパケットのサイズ</span><span class="sxs-lookup"><span data-stu-id="26a46-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="26a46-2060">UDP ソケットの受信通知</span><span class="sxs-lookup"><span data-stu-id="26a46-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="26a46-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="26a46-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="26a46-2062">**アイコン** ![U D P ソケットの受信通知アイコン](./media/user-guide/netx-events/image163.png) **説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="26a46-2063">このイベントは、nx_udp_socket_receive_notify を使用した受信通知コールバックの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="26a46-2064">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2064">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2065">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2066">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-2067">情報フィールド 3: 通知関数を受信するポインター 情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="26a46-2068">UDP ソケット送信</span><span class="sxs-lookup"><span data-stu-id="26a46-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="26a46-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="26a46-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="26a46-2070">**アイコン** ![U D P ソケット送信アイコン](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="26a46-2071">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2071">**Description**</span></span>

<span data-ttu-id="26a46-2072">このイベントは、nx_udp_socket_send を使用した、UDP ソケット経由のデータ送信を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="26a46-2073">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2073">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2074">情報フィールド 1: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="26a46-2075">情報フィールド 2: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="26a46-2076">情報フィールド 3: パケット長</span><span class="sxs-lookup"><span data-stu-id="26a46-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="26a46-2077">情報フィールド 4: 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="26a46-2078">UDP ソケットのバインド解除</span><span class="sxs-lookup"><span data-stu-id="26a46-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="26a46-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="26a46-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="26a46-2080">**アイコン** ![U D P ソケットのバインド解除アイコン](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="26a46-2081">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2081">**Description**</span></span>

<span data-ttu-id="26a46-2082">このイベントは、nx_udp_socket_unbind を使用した UDP ポートのソケットとのバインド解除を表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="26a46-2083">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2083">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2084">情報フィールド 1: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="26a46-2085">情報フィールド 2: ソケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="26a46-2086">情報フィールド 3: ポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="26a46-2087">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="26a46-2088">UDP ソース抽出</span><span class="sxs-lookup"><span data-stu-id="26a46-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="26a46-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="26a46-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="26a46-2090">**アイコン** ![U D P ソース抽出アイコン](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="26a46-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="26a46-2091">**説明**</span><span class="sxs-lookup"><span data-stu-id="26a46-2091">**Description**</span></span>

<span data-ttu-id="26a46-2092">このイベントは、nx_udp_source_extract を使用して、受信した UDP パケットの IP アドレスとポート番号を取得することを表します。</span><span class="sxs-lookup"><span data-stu-id="26a46-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="26a46-2093">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26a46-2093">**Information Fields**</span></span>

- <span data-ttu-id="26a46-2094">情報フィールド 1: パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="26a46-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="26a46-2095">情報フィールド 2: 送信者の IP アドレス</span><span class="sxs-lookup"><span data-stu-id="26a46-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="26a46-2096">情報フィールド 3: 送信者のポート番号</span><span class="sxs-lookup"><span data-stu-id="26a46-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="26a46-2097">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="26a46-2097">Info Field 4: Not used</span></span>