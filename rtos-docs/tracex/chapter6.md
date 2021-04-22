---
title: 第 6 章 - Azure RTOS ThreadX トレース イベント
description: この章では、Azure RTOS ThreadX イベントについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812371"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="55005-103">第 6 章 - Azure RTOS ThreadX トレース イベント</span><span class="sxs-lookup"><span data-stu-id="55005-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="55005-104">この章では、Azure RTOS ThreadX イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55005-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="55005-105">イベントとアイコンの一覧</span><span class="sxs-lookup"><span data-stu-id="55005-105">List of Events and Icons</span></span>

<span data-ttu-id="55005-106">次に、TraceX によって表示される ThreadX イベントの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="55005-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="55005-107">**アイコン**</span><span class="sxs-lookup"><span data-stu-id="55005-107">**Icon**</span></span>                         | <span data-ttu-id="55005-108">**意味**</span><span class="sxs-lookup"><span data-stu-id="55005-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![内部スレッド再開アイコン](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="55005-110">内部スレッド再開</span><span class="sxs-lookup"><span data-stu-id="55005-110">Internal thread resume</span></span>  |
| ![内部スレッド中断アイコン](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="55005-112">内部スレッド中断</span><span class="sxs-lookup"><span data-stu-id="55005-112">Internal thread suspend</span></span> |
| ![割り込みサービス ルーチン開始アイコン](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="55005-114">割り込みサービス ルーチン (ISR) 開始</span><span class="sxs-lookup"><span data-stu-id="55005-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![割り込みサービス ルーチン終了アイコン](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="55005-116">割り込みサービス ルーチン (ISR) 終了</span><span class="sxs-lookup"><span data-stu-id="55005-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![内部タイム スライス アイコン](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="55005-118">内部タイム スライス</span><span class="sxs-lookup"><span data-stu-id="55005-118">Internal time-slice</span></span> |
| ![実行中アイコン](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="55005-120">実行中</span><span class="sxs-lookup"><span data-stu-id="55005-120">Running</span></span> |
| ![ブロック プール割り当てアイコン](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="55005-122">**ブロック プール割り当て** (*tx_block_allocate*)</span><span class="sxs-lookup"><span data-stu-id="55005-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![ブロック プール作成アイコン](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="55005-124">**ブロック プール作成** (*tx_block_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![ブロック プール削除アイコン](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="55005-126">**ブロック プール削除** (*tx_block_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![ブロック プール情報取得アイコン](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="55005-128">**ブロック プール情報取得** (*tx_block_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![ブロック プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="55005-130">**ブロック プール パフォーマンス情報取得** (*tx_block_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![ブロック プール システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="55005-132">**ブロック プール システム パフォーマンス情報取得** (*tx_block_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![ブロック プール優先度付けアイコン](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="55005-134">**ブロック プール優先度付け** (*tx_block_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="55005-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![プールへのブロック解放アイコン](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="55005-136">**プールへのブロック解放** (*tx_block_release*)</span><span class="sxs-lookup"><span data-stu-id="55005-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![バイト プール メモリ割り当てアイコン](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="55005-138">**バイト プール メモリ割り当て** (*tx_byte_allocate*)</span><span class="sxs-lookup"><span data-stu-id="55005-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![バイト プール作成アイコン](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="55005-140">**バイト プール作成** (*tx_byte_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![バイト プール削除アイコン](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="55005-142">**バイト プール削除** (*tx_byte_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![バイト プール情報取得アイコン](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="55005-144">**バイト プール情報取得** (*tx_byte_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![バイト プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="55005-146">**バイト プール パフォーマンス情報取得** (*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![バイト プール システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="55005-148">**バイト プール システム パフォーマンス情報取得** (*tx_byte_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![\*バイト プール優先度付けアイコン](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="55005-150">**バイト プール優先度付け** (*tx_byte_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="55005-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![プールへのバイト メモリ解放アイコン](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="55005-152">**プールへのバイト メモリ解放** (*tx_byte_release*)</span><span class="sxs-lookup"><span data-stu-id="55005-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![イベント フラグ作成アイコン](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="55005-154">**イベント フラグ作成** (*tx_event_flags_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![イベント フラグ削除アイコン](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="55005-156">**イベント フラグ削除** (*tx_event_flags_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![イベント フラグ取得アイコン](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="55005-158">**イベント フラグ取得** (*tx_event_flags_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![イベント フラグ情報取得アイコン](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="55005-160">**イベント フラグ情報取得** (*tx_event_flags_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![イベント フラグ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="55005-162">**イベント フラグ パフォーマンス情報取得** (*tx_event_flags_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![イベント フラグ システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="55005-164">**イベント フラグ システム パフォーマンス情報取得** (*tx_event_flags_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![イベント フラグ設定アイコン](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="55005-166">**イベント フラグ設定** (*tx_event_flags_set*)</span><span class="sxs-lookup"><span data-stu-id="55005-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![イベント フラグ設定通知アイコン](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="55005-168">**イベント フラグ設定通知** (*tx_event_flags_set_notify*)</span><span class="sxs-lookup"><span data-stu-id="55005-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![割り込み有効化/無効化アイコン](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="55005-170">**割り込み有効化/無効化** (*tx_interrupt_control*)</span><span class="sxs-lookup"><span data-stu-id="55005-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![ミューテックス作成アイコン](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="55005-172">**ミューテックス作成** (*tx_mutex_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![ミューテックス削除アイコン](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="55005-174">**ミューテックス削除** (*tx_mutex_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![ミューテックス取得アイコン](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="55005-176">**ミューテックス取得** (*tx_mutex_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![ミューテックス情報取得アイコン](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="55005-178">**ミューテックス情報取得** (*tx_mutex_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![ミューテックス パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="55005-180">**ミューテックス パフォーマンス情報取得** (*tx_mutex_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![ミューテックス システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="55005-182">**ミューテックス システム パフォーマンス情報取得** (*tx_mutex_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![ミューテックス優先度付けアイコン](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="55005-184">**ミューテックス優先度付け** (*tx_mutex_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="55005-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![ミューテックス配置アイコン](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="55005-186">**ミューテックス配置** (*tx_mutex_put*)</span><span class="sxs-lookup"><span data-stu-id="55005-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![キュー作成アイコン](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="55005-188">**キュー作成** (*tx_queue_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![キュー削除アイコン](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="55005-190">**キュー削除** (*tx_queue_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![キュー フラッシュ アイコン](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="55005-192">**キュー フラッシュ** (*tx_queue_flush*)</span><span class="sxs-lookup"><span data-stu-id="55005-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![キュー先頭送信アイコン](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="55005-194">**キュー先頭送信** (*tx_queue_front_send*)</span><span class="sxs-lookup"><span data-stu-id="55005-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![キュー情報取得アイコン](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="55005-196">**キュー情報取得** (*tx_queue_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![キュー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="55005-198">**キュー パフォーマンス情報取得** (*tx_queue_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![キュー システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="55005-200">**キュー システム パフォーマンス情報取得** (*tx_queue_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![キュー優先度付けアイコン](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="55005-202">**キュー優先度付け** (*tx_queue_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="55005-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![キュー受信メッセージ アイコン](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="55005-204">**キュー受信メッセージ** (*tx_queue_receive*)</span><span class="sxs-lookup"><span data-stu-id="55005-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![キュー送信メッセージ アイコン](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="55005-206">**キュー送信メッセージ** (*tx_queue_send*)</span><span class="sxs-lookup"><span data-stu-id="55005-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![キュー送信通知アイコン](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="55005-208">**キュー送信通知** (*tx_queue_send_notify*)</span><span class="sxs-lookup"><span data-stu-id="55005-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![セマフォ シーリング配置アイコン](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="55005-210">**セマフォ シーリング配置** (*tx_semaphore_ceiling_put*)</span><span class="sxs-lookup"><span data-stu-id="55005-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![セマフォ作成アイコン](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="55005-212">**セマフォ作成** (*tx_semaphore_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![セマフォ削除アイコン](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="55005-214">**セマフォ削除** (*tx_semaphore_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![セマフォ取得アイコン](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="55005-216">**セマフォ取得** (*tx_semaphore_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![セマフォ情報取得アイコン](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="55005-218">**セマフォ情報取得** (*tx_semaphore_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![セマフォ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="55005-220">**セマフォ パフォーマンス情報取得** (*tx_semaphroe_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![セマフォ システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="55005-222">**セマフォ システム パフォーマンス情報取得** (*tx_semaphore_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![セマフォ優先度付けアイコン](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="55005-224">**セマフォ優先度付け** (*tx_semaphore_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="55005-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![セマフォ配置アイコン](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="55005-226">**セマフォ配置** (*tx_semaphore_put*)</span><span class="sxs-lookup"><span data-stu-id="55005-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![セマフォ配置通知アイコン](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="55005-228">**セマフォ配置通知** (*tx_semaphore_put_notify*)</span><span class="sxs-lookup"><span data-stu-id="55005-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![スレッド作成アイコン](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="55005-230">**スレッド作成** (*tx_thread_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![スレッド削除アイコン](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="55005-232">**スレッド削除** (*tx_thread_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![スレッド終了/開始通知アイコン](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="55005-234">**スレッド終了/開始通知** (*tx_thread_entry_exit_notify*)</span><span class="sxs-lookup"><span data-stu-id="55005-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![スレッド識別アイコン](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="55005-236">**スレッド識別** (*tx_thread_identify*)</span><span class="sxs-lookup"><span data-stu-id="55005-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![スレッド情報取得アイコン](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="55005-238">**スレッド情報取得** (*tx_thread_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![スレッド パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="55005-240">**スレッド パフォーマンス情報取得** (*tx_thread_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![スレッド パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="55005-242">**スレッド パフォーマンス システム情報取得** (*tx_thread_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![スレッド プリエンプション変更アイコン](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="55005-244">**スレッド プリエンプション変更** (*tx_thread_preemption_change*)</span><span class="sxs-lookup"><span data-stu-id="55005-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![スレッド優先度変更アイコン](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="55005-246">**スレッド優先度変更** (*tx_thread_priority_change*)</span><span class="sxs-lookup"><span data-stu-id="55005-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![スレッド放棄アイコン](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="55005-248">**スレッド放棄** (*tx_thread_relinquish*)</span><span class="sxs-lookup"><span data-stu-id="55005-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![スレッド リセット アイコン](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="55005-250">**スレッド リセット** (*tx_thread_reset*)</span><span class="sxs-lookup"><span data-stu-id="55005-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\*スレッド再開アイコン](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="55005-252">**スレッド再開** (\**tx_thread_resume*)</span><span class="sxs-lookup"><span data-stu-id="55005-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![スレッド スリープ アイコン](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="55005-254">**スレッド スリープ** (*tx_thread_sleep*)\*</span><span class="sxs-lookup"><span data-stu-id="55005-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![スレッド スタック エラー通知アイコン](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="55005-256">**スレッド スタック エラー通知** (*tx_thread_stack_error_notify*)</span><span class="sxs-lookup"><span data-stu-id="55005-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![スレッド中断アイコン](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="55005-258">**スレッド中断** (*tx_thread_suspend*)</span><span class="sxs-lookup"><span data-stu-id="55005-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![スレッド終了アイコン](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="55005-260">**スレッド終了** (*tx_thread_terminate*)</span><span class="sxs-lookup"><span data-stu-id="55005-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![スレッド タイム スライス変更アイコン](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="55005-262">**スレッド タイム スライス変更** (*tx_thread_time_slice_change*)</span><span class="sxs-lookup"><span data-stu-id="55005-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![スレッド待機中止アイコン](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="55005-264">**スレッド待機中止** (*tx_thread_wait_abort*)</span><span class="sxs-lookup"><span data-stu-id="55005-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![時間取得アイコン](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="55005-266">**時間取得** (*tx_time_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-266">**Time get** (*tx_time_get*)</span></span> |
| ![時間設定アイコン](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="55005-268">**時間設定** (*tx_time_set*)</span><span class="sxs-lookup"><span data-stu-id="55005-268">**Time set** (*tx_time_set*)</span></span> |
| ![\*タイマー アクティブ化アイコン](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="55005-270">**タイマー アクティブ化** (*tx_timer_activate*)</span><span class="sxs-lookup"><span data-stu-id="55005-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![タイマー変更アイコン](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="55005-272">**タイマー変更** (*tx_timer_change*)</span><span class="sxs-lookup"><span data-stu-id="55005-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![タイマー作成アイコン](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="55005-274">**タイマー作成** (*tx_timer_create*)</span><span class="sxs-lookup"><span data-stu-id="55005-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![タイマー非アクティブ化アイコン](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="55005-276">**タイマー非アクティブ化** (*tx_timer_deactivate*)</span><span class="sxs-lookup"><span data-stu-id="55005-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![タイマー削除アイコン](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="55005-278">**タイマー削除** (*tx_timer_delete*)</span><span class="sxs-lookup"><span data-stu-id="55005-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![タイマー情報取得アイコン](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="55005-280">**タイマー情報取得** (*tx_timer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![タイマー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="55005-282">**タイマー パフォーマンス情報取得** (*tx_timer_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\*タイマー パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="55005-284">**タイマー パフォーマンス システム情報取得** (*tx_timer_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="55005-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![ユーザー定義イベント アイコン](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="55005-286">**ユーザー定義イベント** (第 10 章を参照)</span><span class="sxs-lookup"><span data-stu-id="55005-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="55005-287">イベントの説明</span><span class="sxs-lookup"><span data-stu-id="55005-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="55005-288">内部スレッド再開</span><span class="sxs-lookup"><span data-stu-id="55005-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="55005-289">内部スレッド再開</span><span class="sxs-lookup"><span data-stu-id="55005-289">Internal thread resume</span></span>

<span data-ttu-id="55005-290">**アイコン** ![内部スレッド再開アイコン](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="55005-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="55005-291">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-291">**Description**</span></span>

<span data-ttu-id="55005-292">このイベントは、スレッドの実行を再開する ThreadX の内部処理を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="55005-293">指定されたスレッドの優先順位が最も高く、プリエンプションしきい値によって実行がブロックされていない場合、システムではこの新しく準備されたスレッドの実行が開始されます。</span><span class="sxs-lookup"><span data-stu-id="55005-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="55005-294">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-294">**Information Fields**</span></span>

- <span data-ttu-id="55005-295">情報フィールド 1: 再開するスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="55005-296">情報フィールド 2: 再開するスレッドの以前の状態。状態は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55005-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="55005-297">スレッドの状態</span><span class="sxs-lookup"><span data-stu-id="55005-297">Thread state</span></span>                     | <span data-ttu-id="55005-298">値</span><span class="sxs-lookup"><span data-stu-id="55005-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="55005-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="55005-299">TX_READY</span></span>                         | <span data-ttu-id="55005-300">0</span><span class="sxs-lookup"><span data-stu-id="55005-300">0</span></span>       |
  |  <span data-ttu-id="55005-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="55005-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="55005-302">1</span><span class="sxs-lookup"><span data-stu-id="55005-302">1</span></span>       |
  |  <span data-ttu-id="55005-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="55005-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="55005-304">2</span><span class="sxs-lookup"><span data-stu-id="55005-304">2</span></span>       |
  |  <span data-ttu-id="55005-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="55005-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="55005-306">3</span><span class="sxs-lookup"><span data-stu-id="55005-306">3</span></span>       |
  |  <span data-ttu-id="55005-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="55005-307">TX_SLEEP</span></span>                         | <span data-ttu-id="55005-308">4</span><span class="sxs-lookup"><span data-stu-id="55005-308">4</span></span>       |
  |  <span data-ttu-id="55005-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="55005-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="55005-310">5</span><span class="sxs-lookup"><span data-stu-id="55005-310">5</span></span>       |
  |  <span data-ttu-id="55005-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="55005-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="55005-312">6</span><span class="sxs-lookup"><span data-stu-id="55005-312">6</span></span>       |
  |  <span data-ttu-id="55005-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="55005-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="55005-314">7</span><span class="sxs-lookup"><span data-stu-id="55005-314">7</span></span>       |
  |  <span data-ttu-id="55005-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="55005-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="55005-316">8</span><span class="sxs-lookup"><span data-stu-id="55005-316">8</span></span>       |
  |  <span data-ttu-id="55005-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="55005-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="55005-318">9</span><span class="sxs-lookup"><span data-stu-id="55005-318">9</span></span>       |
  |  <span data-ttu-id="55005-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="55005-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="55005-320">12</span><span class="sxs-lookup"><span data-stu-id="55005-320">12</span></span>      |
  |  <span data-ttu-id="55005-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="55005-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="55005-322">13</span><span class="sxs-lookup"><span data-stu-id="55005-322">13</span></span>      |

- <span data-ttu-id="55005-323">情報フィールド 3: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="55005-324">情報フィールド 4: 次に実行優先順位の高いスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="55005-325">内部スレッド中断</span><span class="sxs-lookup"><span data-stu-id="55005-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="55005-326">内部スレッド中断</span><span class="sxs-lookup"><span data-stu-id="55005-326">Internal thread suspend</span></span>

<span data-ttu-id="55005-327">**アイコン** ![内部スレッド中断アイコン](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="55005-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="55005-328">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-328">**Description**</span></span>

<span data-ttu-id="55005-329">このイベントは、スレッドの実行を中断する ThreadX の内部処理を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="55005-330">実行の準備ができ、次に優先順位の高いスレッドが 4 番目の情報フィールドに配置されます。</span><span class="sxs-lookup"><span data-stu-id="55005-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="55005-331">この値が NULL の場合、実行の準備が整っているスレッドが他になく、システムはアイドル状態になります。</span><span class="sxs-lookup"><span data-stu-id="55005-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="55005-332">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-332">**Information Fields**</span></span>

- <span data-ttu-id="55005-333">情報フィールド 1: 中断するスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="55005-334">情報フィールド 2: 中断するスレッドの新しい状態。状態は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55005-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="55005-335">スレッドの状態</span><span class="sxs-lookup"><span data-stu-id="55005-335">Thread state</span></span>                     | <span data-ttu-id="55005-336">値</span><span class="sxs-lookup"><span data-stu-id="55005-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="55005-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="55005-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="55005-338">1</span><span class="sxs-lookup"><span data-stu-id="55005-338">1</span></span>       |
  |  <span data-ttu-id="55005-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="55005-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="55005-340">2</span><span class="sxs-lookup"><span data-stu-id="55005-340">2</span></span>       |
  |  <span data-ttu-id="55005-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="55005-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="55005-342">3</span><span class="sxs-lookup"><span data-stu-id="55005-342">3</span></span>       |
  |  <span data-ttu-id="55005-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="55005-343">TX_SLEEP</span></span>                         | <span data-ttu-id="55005-344">4</span><span class="sxs-lookup"><span data-stu-id="55005-344">4</span></span>       |
  |  <span data-ttu-id="55005-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="55005-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="55005-346">5</span><span class="sxs-lookup"><span data-stu-id="55005-346">5</span></span>       |
  |  <span data-ttu-id="55005-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="55005-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="55005-348">6</span><span class="sxs-lookup"><span data-stu-id="55005-348">6</span></span>       |
  |  <span data-ttu-id="55005-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="55005-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="55005-350">7</span><span class="sxs-lookup"><span data-stu-id="55005-350">7</span></span>       |
  |  <span data-ttu-id="55005-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="55005-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="55005-352">8</span><span class="sxs-lookup"><span data-stu-id="55005-352">8</span></span>       |
  |  <span data-ttu-id="55005-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="55005-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="55005-354">9</span><span class="sxs-lookup"><span data-stu-id="55005-354">9</span></span>       |
  |  <span data-ttu-id="55005-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="55005-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="55005-356">12</span><span class="sxs-lookup"><span data-stu-id="55005-356">12</span></span>      |
  |  <span data-ttu-id="55005-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="55005-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="55005-358">13</span><span class="sxs-lookup"><span data-stu-id="55005-358">13</span></span>      |

- <span data-ttu-id="55005-359">情報フィールド 3: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="55005-360">情報フィールド 4: 次に実行優先順位の高いスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="55005-361">NULL の場合、システムはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="55005-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="55005-362">割り込みサービス ルーチン (ISR) 開始</span><span class="sxs-lookup"><span data-stu-id="55005-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="55005-363">ISR 開始</span><span class="sxs-lookup"><span data-stu-id="55005-363">Enter ISR</span></span> 

<span data-ttu-id="55005-364">**アイコン** ![ISR 開始アイコン](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="55005-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="55005-365">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-365">**Description**</span></span>

<span data-ttu-id="55005-366">このイベントは、アプリケーションでの割り込みサービス ルーチン (ISR) の開始を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="55005-367">割り込みサービス ルーチンの実行は、ISR 終了イベントが発生するまで続行されます。</span><span class="sxs-lookup"><span data-stu-id="55005-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="55005-368">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-368">**Information Fields**</span></span>

- <span data-ttu-id="55005-369">情報フィールド 1: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="55005-370">情報フィールド 2: アプリケーション定義の ISR 番号 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="55005-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="55005-371">情報フィールド 3: 入れ子になった割り込みカウント。</span><span class="sxs-lookup"><span data-stu-id="55005-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="55005-372">情報フィールド 4: 内部プリエンプション無効フラグ。</span><span class="sxs-lookup"><span data-stu-id="55005-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="55005-373">割り込みサービス ルーチン (ISR) 終了</span><span class="sxs-lookup"><span data-stu-id="55005-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="55005-374">ISR 終了</span><span class="sxs-lookup"><span data-stu-id="55005-374">Exit ISR</span></span>

<span data-ttu-id="55005-375">**アイコン** ![ISR 終了アイコン](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="55005-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="55005-376">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-376">**Description**</span></span>

<span data-ttu-id="55005-377">このイベントは、アプリケーションでの割り込みサービス ルーチン (ISR) の終了を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="55005-378">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-378">**Information Fields**</span></span>

- <span data-ttu-id="55005-379">情報フィールド 1: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="55005-380">情報フィールド 2: アプリケーション定義の ISR 番号 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="55005-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="55005-381">情報フィールド 3: 入れ子になった割り込みカウント。</span><span class="sxs-lookup"><span data-stu-id="55005-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="55005-382">情報フィールド 4: 内部プリエンプション無効フラグ。</span><span class="sxs-lookup"><span data-stu-id="55005-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="55005-383">内部タイム スライス</span><span class="sxs-lookup"><span data-stu-id="55005-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="55005-384">内部タイム スライス</span><span class="sxs-lookup"><span data-stu-id="55005-384">Internal time-slice</span></span>

<span data-ttu-id="55005-385">**アイコン** ![内部タイム スライス アイコン](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="55005-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="55005-386">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-386">**Description**</span></span>

<span data-ttu-id="55005-387">このイベントは、タイム スライス操作を実行する ThreadX の内部処理を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="55005-388">最初の情報フィールドには、同じ優先順位の次のスレッドが配置されます。</span><span class="sxs-lookup"><span data-stu-id="55005-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="55005-389">この値が現在のスレッドと同じ場合、タイム スライスは実行されませんでした。</span><span class="sxs-lookup"><span data-stu-id="55005-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="55005-390">情報フィールド 1: 次に実行するスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="55005-391">情報フィールド 2: 入れ子になった割り込みカウント。</span><span class="sxs-lookup"><span data-stu-id="55005-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="55005-392">情報フィールド 3: 内部プリエンプション無効フラグ。</span><span class="sxs-lookup"><span data-stu-id="55005-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="55005-393">情報フィールド 4: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="55005-394">実行中</span><span class="sxs-lookup"><span data-stu-id="55005-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="55005-395">コンテキストで実行中</span><span class="sxs-lookup"><span data-stu-id="55005-395">Running in context</span></span>

<span data-ttu-id="55005-396">**アイコン** ![実行中アイコン](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="55005-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="55005-397">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-397">**Description**</span></span>

<span data-ttu-id="55005-398">このイベントは、スレッド コンテキストまたはアイドル システム内で実行されていることを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="55005-399">これは、割り込みの結果としてコンテキストでの後続の変更を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="55005-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="55005-400">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-400">**Information Fields**</span></span>
- <span data-ttu-id="55005-401">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-402">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-403">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-404">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="55005-405">ブロック割り当て</span><span class="sxs-lookup"><span data-stu-id="55005-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="55005-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="55005-406">tx_block_allocate</span></span>

<span data-ttu-id="55005-407">**アイコン** ![ブロック割り当てアイコン](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="55005-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="55005-408">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-408">**Description**</span></span>

<span data-ttu-id="55005-409">このイベントは、tx_block_allocate を使用したメモリ ブロックの割り当てを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="55005-410">成功した場合は、割り当てられたブロックのアドレスが 2 番目の情報フィールドに返されます。</span><span class="sxs-lookup"><span data-stu-id="55005-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="55005-411">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-411">**Information Fields**</span></span>
- <span data-ttu-id="55005-412">情報フィールド 1: 対応するブロック プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="55005-413">情報フィールド 2: 返されるメモリ ブロックへのポインター (成功した場合)。</span><span class="sxs-lookup"><span data-stu-id="55005-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="55005-414">情報フィールド 3: tx_block_allocate 呼び出しに指定する待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="55005-415">情報フィールド 4: この割り当て後にプール内で使用可能な残りのブロック数。</span><span class="sxs-lookup"><span data-stu-id="55005-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="55005-416">ブロック プール作成</span><span class="sxs-lookup"><span data-stu-id="55005-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="55005-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="55005-417">tx_block_pool_create</span></span>

<span data-ttu-id="55005-418">**アイコン** ![ブロック プール作成アイコン](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="55005-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="55005-419">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-419">**Description**</span></span>

<span data-ttu-id="55005-420">このイベントは、tx_block_pool_create を使用したメモリ ブロック プールの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="55005-421">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-421">**Information Fields**</span></span>

- <span data-ttu-id="55005-422">情報フィールド 1: 対応するブロック プール制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="55005-423">情報フィールド 2: プールの開始メモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="55005-424">情報フィールド 3: プール内のブロックの数。</span><span class="sxs-lookup"><span data-stu-id="55005-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="55005-425">情報フィールド 4: プール内の各ブロックのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="55005-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="55005-426">ブロック プール削除</span><span class="sxs-lookup"><span data-stu-id="55005-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="55005-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="55005-427">tx_block_pool_delete</span></span>

<span data-ttu-id="55005-428">**アイコン** ![ブロック プール削除アイコン](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="55005-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="55005-429">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-429">**Description**</span></span>

<span data-ttu-id="55005-430">このイベントは、tx_block_pool_delete を使用したメモリ ブロック プールの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="55005-431">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-431">**Information Fields**</span></span>

- <span data-ttu-id="55005-432">情報フィールド 1: ブロック プール制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="55005-433">情報フィールド 2: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="55005-434">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-435">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="55005-436">ブロック プール情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="55005-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="55005-438">**アイコン** ![ブロック プール情報取得アイコン](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="55005-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="55005-439">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-439">**Description**</span></span>

<span data-ttu-id="55005-440">このイベントは、tx_block_pool_info_get を使用したメモリ ブロック プールに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="55005-441">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-441">**Information Fields**</span></span>

- <span data-ttu-id="55005-442">情報フィールド 1: ブロック プール制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="55005-443">情報フィールド 2: 呼び出し中のスタック ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="55005-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="55005-444">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-445">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="55005-446">ブロック プール パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="55005-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="55005-448">**アイコン** ![ブロック プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="55005-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="55005-449">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-449">**Description**</span></span>

<span data-ttu-id="55005-450">このイベントは、tx_block_pool_performance_info_get を使用したメモリ ブロック プールに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="55005-451">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-451">**Information Fields**</span></span>

- <span data-ttu-id="55005-452">情報フィールド 1: ブロック プール制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="55005-453">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-454">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-455">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="55005-456">ブロック プール パフォーマンス システム情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="55005-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="55005-458">**アイコン** ![ブロック プール パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="55005-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="55005-459">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-459">**Description**</span></span>

<span data-ttu-id="55005-460">このイベントは、tx_block_pool_performance_system_info_get を使用したすべてのメモリ ブロック プールに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="55005-461">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-461">**Information Fields**</span></span>
- <span data-ttu-id="55005-462">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-463">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-464">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-465">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="55005-466">ブロック プール優先度付け</span><span class="sxs-lookup"><span data-stu-id="55005-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="55005-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="55005-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="55005-468">**アイコン** ![ブロック プール優先度付けアイコン](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="55005-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="55005-469">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-469">**Description**</span></span>

<span data-ttu-id="55005-470">このイベントは、ブロック プールの中断リストの先頭に優先順位が最も高い中断されたスレッドを配置することを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="55005-471">tx_block_release を呼び出す前にこの処理が行われた場合、優先順位が最も高い中断されたスレッドが解放されたブロックを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="55005-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="55005-472">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-472">**Information Fields**</span></span>
- <span data-ttu-id="55005-473">情報フィールド 1: メモリ ブロック プールのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="55005-474">情報フィールド 2: このブロック プールで中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="55005-475">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="55005-476">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="55005-477">ブロック解放</span><span class="sxs-lookup"><span data-stu-id="55005-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="55005-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="55005-478">tx_block_release</span></span>

<span data-ttu-id="55005-479">**アイコン** ![ブロック解放アイコン](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="55005-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="55005-480">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-480">**Description**</span></span>

<span data-ttu-id="55005-481">このイベントは、以前に割り当てられたブロックを解放してブロック プールに戻すことを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="55005-482">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-482">**Information Fields**</span></span>

- <span data-ttu-id="55005-483">情報フィールド 1: メモリ ブロック プールのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="55005-484">情報フィールド 2: 解放するブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="55005-485">情報フィールド 3: このブロック プールで中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="55005-486">情報フィールド 4: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="55005-487">バイト割り当て</span><span class="sxs-lookup"><span data-stu-id="55005-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="55005-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="55005-488">tx_byte_allocate</span></span>

<span data-ttu-id="55005-489">**アイコン** ![バイト割り当てアイコン](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="55005-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="55005-490">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-490">**Description**</span></span>

<span data-ttu-id="55005-491">このイベントは、tx_byte_allocate を使用したメモリの割り当てを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="55005-492">成功した場合は、割り当てられたメモリのアドレスが 2 番目の情報フィールドに返されます。</span><span class="sxs-lookup"><span data-stu-id="55005-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="55005-493">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-493">**Information Fields**</span></span>
- <span data-ttu-id="55005-494">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="55005-495">情報フィールド 2: 返されるメモリへのポインター (成功した場合)。</span><span class="sxs-lookup"><span data-stu-id="55005-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="55005-496">情報フィールド 3: 要求したバイト数。</span><span class="sxs-lookup"><span data-stu-id="55005-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="55005-497">情報フィールド 4: tx_byte_allocate 呼び出しに指定する待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="55005-498">バイト プール作成</span><span class="sxs-lookup"><span data-stu-id="55005-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="55005-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="55005-499">tx_byte_pool_create</span></span>

<span data-ttu-id="55005-500">**アイコン** ![バイト プール作成アイコン](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="55005-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="55005-501">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-501">**Description**</span></span>

<span data-ttu-id="55005-502">このイベントは、tx_byte_pool_create を使用したバイト プールの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="55005-503">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-503">**Information Fields**</span></span>

- <span data-ttu-id="55005-504">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="55005-505">情報フィールド 2: メモリ領域の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="55005-506">情報フィールド 3: バイト プール内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="55005-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="55005-507">情報フィールド 4: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="55005-508">バイト プール削除</span><span class="sxs-lookup"><span data-stu-id="55005-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="55005-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="55005-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="55005-510">**アイコン** ![バイト プール削除アイコン](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="55005-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="55005-511">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-511">**Description**</span></span>

<span data-ttu-id="55005-512">このイベントは、tx_byte_pool_delete を使用したバイト プールの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="55005-513">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-513">**Information Fields**</span></span>

- <span data-ttu-id="55005-514">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="55005-515">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="55005-516">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-517">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="55005-518">バイト プール情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="55005-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="55005-520">**アイコン** ![バイト プール情報取得アイコン](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="55005-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="55005-521">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-521">**Description**</span></span>

<span data-ttu-id="55005-522">このイベントは、tx_byte_pool_info_get を使用したバイト プール情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="55005-523">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-523">**Information Fields**</span></span>

- <span data-ttu-id="55005-524">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="55005-525">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-526">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-527">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="55005-528">バイト プール パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="55005-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="55005-530">**アイコン** ![バイト プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="55005-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="55005-531">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-531">**Description**</span></span>

<span data-ttu-id="55005-532">このイベントは、tx_byte_pool_performance_info_get を使用したバイト プール パフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="55005-533">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-533">**Information Fields**</span></span>

- <span data-ttu-id="55005-534">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="55005-535">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-536">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-537">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="55005-538">バイト プール パフォーマンス システム情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="55005-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="55005-540">**アイコン** ![バイト プール パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="55005-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="55005-541">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-541">**Description**</span></span>

<span data-ttu-id="55005-542">このイベントは、tx_byte_pool_performance_system_info_get を使用したバイト プール パフォーマンス システム情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="55005-543">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-543">**Information Fields**</span></span>

- <span data-ttu-id="55005-544">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-545">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-546">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-547">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="55005-548">バイト プール優先度付け</span><span class="sxs-lookup"><span data-stu-id="55005-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="55005-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="55005-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="55005-550">**アイコン** ![バイト プール優先度付けアイコン](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="55005-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="55005-551">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-551">**Description**</span></span>

<span data-ttu-id="55005-552">このイベントは、tx_byte_pool_prioritize を使用したバイト プールの中断リストの優先順位付けを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="55005-553">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-553">**Information Fields**</span></span>

- <span data-ttu-id="55005-554">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="55005-555">情報フィールド 2: バイト プールで現在中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="55005-556">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-557">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="55005-558">バイト解放</span><span class="sxs-lookup"><span data-stu-id="55005-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="55005-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="55005-559">tx_byte_release</span></span>

<span data-ttu-id="55005-560">**アイコン** ![バイト解放アイコン](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="55005-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="55005-561">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-561">**Description**</span></span>

<span data-ttu-id="55005-562">このイベントは、tx_byte_release を使用したバイト プールから割り当てられたメモリ ブロックの解放を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="55005-563">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-563">**Information Fields**</span></span>

- <span data-ttu-id="55005-564">情報フィールド 1: 対応するバイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="55005-565">情報フィールド 2: 以前に割り当てられたバイト プール メモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="55005-566">情報フィールド 3: このバイト プールで中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="55005-567">情報フィールド 4: 使用可能なメモリのバイト数。</span><span class="sxs-lookup"><span data-stu-id="55005-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="55005-568">イベント フラグ作成</span><span class="sxs-lookup"><span data-stu-id="55005-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="55005-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="55005-569">tx_event_flags_create</span></span>

<span data-ttu-id="55005-570">**アイコン** ![イベント フラグ作成アイコン](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="55005-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="55005-571">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-571">**Description**</span></span>

<span data-ttu-id="55005-572">このイベントは、tx_event_flags_create を使用した新しいイベント フラグ グループの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="55005-573">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-573">**Information Fields**</span></span> 
- <span data-ttu-id="55005-574">情報フィールド 1: イベント フラグ グループ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="55005-575">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-576">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-577">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="55005-578">イベント フラグ削除</span><span class="sxs-lookup"><span data-stu-id="55005-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="55005-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="55005-579">tx_event_flags_delete</span></span>

<span data-ttu-id="55005-580">**アイコン** ![イベント フラグ削除アイコン](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="55005-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="55005-581">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-581">**Description**</span></span>

<span data-ttu-id="55005-582">このイベントは、tx_event_flags_delete を使用したイベント フラグ グループの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="55005-583">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-583">**Information Fields**</span></span> 

- <span data-ttu-id="55005-584">情報フィールド 1: イベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="55005-585">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-586">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-587">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="55005-588">イベント フラグ取得</span><span class="sxs-lookup"><span data-stu-id="55005-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="55005-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="55005-589">tx_event_flags_get</span></span>

<span data-ttu-id="55005-590">**アイコン** ![イベント フラグ取得アイコン](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="55005-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="55005-591">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-591">**Description**</span></span>

<span data-ttu-id="55005-592">このイベントは、tx_event_flags_get を使用した既存のイベント フラグ グループからのイベント フラグの取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="55005-593">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-593">**Information Fields**</span></span>

- <span data-ttu-id="55005-594">情報フィールド 1: イベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="55005-595">情報フィールド 2: 要求されたイベント フラグ。</span><span class="sxs-lookup"><span data-stu-id="55005-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="55005-596">情報フィールド 3: グループに現在設定されているイベント フラグ。</span><span class="sxs-lookup"><span data-stu-id="55005-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="55005-597">情報フィールド 4: イベント フラグ取得時に要求されたオプション。</span><span class="sxs-lookup"><span data-stu-id="55005-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="55005-598">イベント フラグ情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="55005-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="55005-600">**アイコン** ![イベント フラグ情報取得アイコン](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="55005-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="55005-601">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-601">**Description**</span></span>

<span data-ttu-id="55005-602">このイベントは、tx_event_flags_info_get を使用した既存のイベント フラグ グループに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="55005-603">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-603">**Information Fields**</span></span>

- <span data-ttu-id="55005-604">情報フィールド 1: イベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="55005-605">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-606">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-607">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="55005-608">イベント フラグ パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="55005-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="55005-610">**アイコン** ![イベント フラグ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="55005-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="55005-611">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-611">**Description**</span></span>

<span data-ttu-id="55005-612">このイベントは、tx_event_flags_performance_info_get を使用した既存のイベント フラグ グループに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="55005-613">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-613">**Information Fields**</span></span> 
- <span data-ttu-id="55005-614">情報フィールド 1: イベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="55005-615">情報フィールド 2: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="55005-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="55005-616">情報フィールド 3: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="55005-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="55005-617">情報フィールド 4: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="55005-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="55005-618">イベント フラグ パフォーマンス システム情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="55005-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="55005-620">**アイコン** ![イベント フラグ パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="55005-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="55005-621">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-621">**Description**</span></span>

<span data-ttu-id="55005-622">このイベントは、tx_event_flags_performance_system_info_get を使用した既存のイベント フラグ グループに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="55005-623">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-623">**Information Fields**</span></span>
- <span data-ttu-id="55005-624">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-625">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-626">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-627">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="55005-628">イベント フラグ設定</span><span class="sxs-lookup"><span data-stu-id="55005-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="55005-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="55005-629">tx_event_flags_set</span></span>

<span data-ttu-id="55005-630">**アイコン** ![イベント フラグ設定アイコン](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="55005-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="55005-631">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-631">**Description**</span></span>

<span data-ttu-id="55005-632">このイベントは、tx_event_flags_set を使用した既存のイベント フラグ グループのイベント フラグの設定 (または消去) を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="55005-633">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-633">**Information Fields**</span></span>

- <span data-ttu-id="55005-634">情報フィールド 1: イベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="55005-635">情報フィールド 2: 設定 (または消去) するイベント フラグ。</span><span class="sxs-lookup"><span data-stu-id="55005-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="55005-636">情報フィールド 3: AND または OR のイベント フラグ オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="55005-637">情報フィールド 4: イベント フラグ グループで中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="55005-638">イベント フラグ設定通知</span><span class="sxs-lookup"><span data-stu-id="55005-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="55005-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="55005-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="55005-640">**アイコン** ![イベント フラグ設定通知アイコン](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="55005-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="55005-641">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-641">**Description**</span></span>

<span data-ttu-id="55005-642">このイベントは、tx_event_flags_set_notify を使用した既存のイベント フラグ グループのイベント フラグ設定操作に対する通知コールバックの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="55005-643">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-643">**Information Fields**</span></span>

- <span data-ttu-id="55005-644">情報フィールド 1: イベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="55005-645">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-646">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-647">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="55005-648">割り込み制御</span><span class="sxs-lookup"><span data-stu-id="55005-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="55005-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="55005-649">tx_interrupt_control</span></span>

<span data-ttu-id="55005-650">**アイコン** ![割り込み制御アイコン](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="55005-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="55005-651">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-651">**Description**</span></span>

<span data-ttu-id="55005-652">このイベントは、tx_interrupt_control を使用したプロセッサの割り込みロックアウト状態の変化を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="55005-653">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-653">**Information Fields**</span></span>

- <span data-ttu-id="55005-654">情報フィールド 1: 新しい割り込み状態。</span><span class="sxs-lookup"><span data-stu-id="55005-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="55005-655">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-656">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-657">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="55005-658">ミューテックス作成</span><span class="sxs-lookup"><span data-stu-id="55005-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="55005-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="55005-659">tx_mutex_create</span></span>

<span data-ttu-id="55005-660">**アイコン** ![ミューテックス作成アイコン](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="55005-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="55005-661">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-661">**Description**</span></span>

<span data-ttu-id="55005-662">このイベントは、tx_mutex_create を使用したミューテックスの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="55005-663">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-663">**Information Fields**</span></span>

- <span data-ttu-id="55005-664">情報フィールド 1: ミューテックス制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="55005-665">情報フィールド 2: 優先度の継承オプション</span><span class="sxs-lookup"><span data-stu-id="55005-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="55005-666">(TX_INHERIT または TX_NO_INHERIT)。</span><span class="sxs-lookup"><span data-stu-id="55005-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="55005-667">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-668">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="55005-669">ミューテックス削除</span><span class="sxs-lookup"><span data-stu-id="55005-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="55005-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="55005-670">tx_mutex_delete</span></span>

<span data-ttu-id="55005-671">**アイコン** ![ミューテックス削除アイコン](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="55005-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="55005-672">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-672">**Description**</span></span>

<span data-ttu-id="55005-673">このイベントは、tx_mutex_delete を使用したミューテックスの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="55005-674">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-674">**Information Fields**</span></span> 

- <span data-ttu-id="55005-675">情報フィールド 1: ミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="55005-676">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-677">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-678">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="55005-679">ミューテックス取得</span><span class="sxs-lookup"><span data-stu-id="55005-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="55005-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="55005-680">tx_mutex_get</span></span>

<span data-ttu-id="55005-681">**アイコン** ![ミューテックス取得アイコン](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="55005-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="55005-682">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-682">**Description**</span></span>

<span data-ttu-id="55005-683">このイベントは、tx_mutex_get を使用したミューテックスの取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="55005-684">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-684">**Information Fields**</span></span>

- <span data-ttu-id="55005-685">情報フィールド 1: ミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="55005-686">情報フィールド 2: tx_mutex_get 呼び出しに指定する待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="55005-687">情報フィールド 3: ミューテックスを所有するスレッドへのポインター (NULL はミューテックスが所有されていないことを意味します)。</span><span class="sxs-lookup"><span data-stu-id="55005-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="55005-688">情報フィールド 4: 所有スレッドが tx_mutex_get を呼び出した回数。</span><span class="sxs-lookup"><span data-stu-id="55005-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="55005-689">ミューテックス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="55005-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-690">tx_mutex_info_get</span></span>

<span data-ttu-id="55005-691">**アイコン** ![ミューテックス情報取得アイコン](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="55005-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="55005-692">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-692">**Description**</span></span>

<span data-ttu-id="55005-693">このイベントは、tx_mutex_info_get を使用したミューテックス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="55005-694">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-694">**Information Fields**</span></span>

- <span data-ttu-id="55005-695">情報フィールド 1: ミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="55005-696">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-697">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-698">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="55005-699">ミューテックス パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="55005-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="55005-701">**アイコン** ![ミューテックス パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="55005-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="55005-702">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-702">**Description**</span></span>

<span data-ttu-id="55005-703">このイベントは、tx_mutex_performance_info_get を使用したミューテックス パフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="55005-704">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-704">**Information Fields**</span></span>

- <span data-ttu-id="55005-705">情報フィールド 1: ミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="55005-706">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-707">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-708">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="55005-709">ミューテックス パフォーマンス システム情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="55005-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="55005-711">**アイコン** ![ミューテックス パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="55005-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="55005-712">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-712">**Description**</span></span>

<span data-ttu-id="55005-713">このイベントは、tx_mutex_performance_system_info_get を使用したミューテックス システム パフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="55005-714">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-714">**Information Fields**</span></span>

- <span data-ttu-id="55005-715">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-716">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-717">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-718">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="55005-719">ミューテックス優先度付け</span><span class="sxs-lookup"><span data-stu-id="55005-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="55005-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="55005-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="55005-721">**アイコン** ![ミューテックス優先度付けアイコン](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="55005-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="55005-722">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-722">**Description**</span></span>

<span data-ttu-id="55005-723">このイベントは、tx_mutex_prioritize を使用したミューテックスの中断リストの優先順位付けを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="55005-724">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-724">**Information Fields**</span></span>

- <span data-ttu-id="55005-725">情報フィールド 1: 対応するミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="55005-726">情報フィールド 2: ミューテックスで現在中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="55005-727">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-728">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="55005-729">ミューテックス配置</span><span class="sxs-lookup"><span data-stu-id="55005-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="55005-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="55005-730">tx_mutex_put</span></span>

<span data-ttu-id="55005-731">**アイコン** ![ミューテックス配置アイコン](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="55005-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="55005-732">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-732">**Description**</span></span>

<span data-ttu-id="55005-733">このイベントは、tx_mutex_put を使用した以前に所有されたミューテックスの解放を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="55005-734">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-734">**Information Fields**</span></span>

- <span data-ttu-id="55005-735">情報フィールド 1: 対応するミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="55005-736">情報フィールド 2: ミューテックスを所有しているスレッドのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="55005-737">情報フィールド 3: 未処理のミューテックス取得要求の数。</span><span class="sxs-lookup"><span data-stu-id="55005-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="55005-738">情報フィールド 4: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="55005-739">キュー作成</span><span class="sxs-lookup"><span data-stu-id="55005-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="55005-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="55005-740">tx_queue_create</span></span>

<span data-ttu-id="55005-741">**アイコン** ![キュー作成アイコン](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="55005-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="55005-742">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-742">**Description**</span></span>

<span data-ttu-id="55005-743">このイベントは、tx_queue_create を使用したメッセージ キューの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="55005-744">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-744">**Information Fields**</span></span>

- <span data-ttu-id="55005-745">情報フィールド 1: キュー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="55005-746">情報フィールド 2: 32 ビット ワードで見たメッセージのサイズ。</span><span class="sxs-lookup"><span data-stu-id="55005-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="55005-747">情報フィールド 3: キュー メモリ領域の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="55005-748">情報フィールド 4: キュー メモリ領域内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="55005-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="55005-749">キュー削除</span><span class="sxs-lookup"><span data-stu-id="55005-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="55005-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="55005-750">tx_queue_delete</span></span>

<span data-ttu-id="55005-751">**アイコン** ![キュー削除アイコン](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="55005-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="55005-752">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-752">**Description**</span></span>

<span data-ttu-id="55005-753">このイベントは、tx_queue_delete を使用したキューの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="55005-754">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-754">**Information Fields**</span></span>

- <span data-ttu-id="55005-755">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-756">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-757">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-758">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="55005-759">キュー フラッシュ</span><span class="sxs-lookup"><span data-stu-id="55005-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="55005-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="55005-760">tx_queue_flush</span></span>

<span data-ttu-id="55005-761">**アイコン** ![キュー フラッシュ アイコン](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="55005-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="55005-762">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-762">**Description**</span></span>

<span data-ttu-id="55005-763">このイベントは、tx_queue_flush を使用したキューのフラッシュ (すべてのキューの内容のクリア) を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="55005-764">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-764">**Information Fields**</span></span>

- <span data-ttu-id="55005-765">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-766">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-767">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-768">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="55005-769">キュー先頭送信</span><span class="sxs-lookup"><span data-stu-id="55005-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="55005-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="55005-770">tx_queue_front_send</span></span>

<span data-ttu-id="55005-771">**アイコン** ![キュー先頭送信アイコン](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="55005-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="55005-772">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-772">**Description**</span></span>

<span data-ttu-id="55005-773">このイベントは、tx_queue_front_send を使用したキューの先頭へのメッセージの送信を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="55005-774">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-774">**Information Fields**</span></span>

- <span data-ttu-id="55005-775">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-776">情報フィールド 2: メッセージの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="55005-777">情報フィールド 3:</span><span class="sxs-lookup"><span data-stu-id="55005-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="55005-778">tx_queue_front_send 呼び出しに指定された待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="55005-779">情報フィールド 4: 既にキューに登録されているメッセージの数。</span><span class="sxs-lookup"><span data-stu-id="55005-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="55005-780">キュー情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="55005-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-781">tx_queue_info_get</span></span>

<span data-ttu-id="55005-782">**アイコン** ![キュー情報取得アイコン](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="55005-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="55005-783">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-783">**Description**</span></span>

<span data-ttu-id="55005-784">このイベントは、tx_queue_info_get を使用したキューに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="55005-785">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-785">**Information Fields**</span></span> 
- <span data-ttu-id="55005-786">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-787">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-788">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-789">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="55005-790">キュー パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="55005-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="55005-792">**アイコン** ![キュー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="55005-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="55005-793">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-793">**Description**</span></span>

<span data-ttu-id="55005-794">このイベントは、tx_queue_performance_info_get を使用したキューに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="55005-795">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-795">**Information Fields**</span></span> 

- <span data-ttu-id="55005-796">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-797">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-798">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-799">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="55005-800">キュー パフォーマンス システム情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="55005-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="55005-802">**アイコン** ![キュー パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="55005-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="55005-803">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-803">**Description**</span></span>

<span data-ttu-id="55005-804">このイベントは、システム内のすべてのキューに関するシステム パフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="55005-805">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-805">**Information Fields**</span></span>

- <span data-ttu-id="55005-806">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-807">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-808">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-809">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="55005-810">キュー優先度付け</span><span class="sxs-lookup"><span data-stu-id="55005-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="55005-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="55005-811">tx_queue_prioritize</span></span>

<span data-ttu-id="55005-812">**アイコン** ![キュー優先度付けアイコン](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="55005-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="55005-813">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-813">**Description**</span></span>

<span data-ttu-id="55005-814">このイベントは、tx_queue_prioritize を使用したキューの中断リストの優先順位付けを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="55005-815">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-815">**Information Fields**</span></span> 

- <span data-ttu-id="55005-816">情報フィールド 1: 対応するキューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="55005-817">情報フィールド 2: キューで現在中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="55005-818">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-819">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="55005-820">キュー受信</span><span class="sxs-lookup"><span data-stu-id="55005-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="55005-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="55005-821">tx_queue_receive</span></span>

<span data-ttu-id="55005-822">**アイコン** ![キュー受信アイコン](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="55005-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="55005-823">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-823">**Description**</span></span>

<span data-ttu-id="55005-824">このイベントは、tx_queue_receive を使用したキューからのメッセージの受信を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="55005-825">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-825">**Information Fields**</span></span> 

- <span data-ttu-id="55005-826">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-827">情報フィールド 2: メッセージの宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="55005-828">情報フィールド 3: 呼び出しに指定された待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="55005-829">情報フィールド 4: 現在キューに置かれているメッセージの数。</span><span class="sxs-lookup"><span data-stu-id="55005-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="55005-830">キュー送信</span><span class="sxs-lookup"><span data-stu-id="55005-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="55005-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="55005-831">tx_queue_send</span></span>

<span data-ttu-id="55005-832">**アイコン** ![キュー送信アイコン](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="55005-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="55005-833">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-833">**Description**</span></span>

<span data-ttu-id="55005-834">このイベントは、tx_queue_send を使用したキューへのメッセージの送信を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="55005-835">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-835">**Information Fields**</span></span> 

- <span data-ttu-id="55005-836">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-837">情報フィールド 2: メッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="55005-838">情報フィールド 3: 呼び出しに指定された待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="55005-839">情報フィールド 4: 現在キューに置かれているメッセージの数。</span><span class="sxs-lookup"><span data-stu-id="55005-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="55005-840">キュー送信通知</span><span class="sxs-lookup"><span data-stu-id="55005-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="55005-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="55005-841">tx_queue_send_notify</span></span>

<span data-ttu-id="55005-842">**アイコン** ![キュー送信通知アイコン](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="55005-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="55005-843">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-843">**Description**</span></span>

<p><span data-ttu-id="55005-844">このイベントは、メッセージがキューに送信されるたびに呼び出される tx_queue_send_notify を使用したコールバックの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="55005-845">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-845">**Information Fields**</span></span> 

- <span data-ttu-id="55005-846">情報フィールド 1: キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="55005-847">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-848">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-849">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="55005-850">セマフォ シーリング配置</span><span class="sxs-lookup"><span data-stu-id="55005-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="55005-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="55005-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="55005-852">**アイコン** ![セマフォ シーリング配置アイコン](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="55005-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="55005-853">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-853">**Description**</span></span>

<span data-ttu-id="55005-854">このイベントは、tx_semaphore_ceiling_put を使用したセマフォへの配置を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="55005-855">これは、put 操作で最大値またはシーリングを超えることができないようにセマフォの最大値が検査されるという点で tx_semaphore_put とは異なります。</span><span class="sxs-lookup"><span data-stu-id="55005-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="55005-856">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-856">**Information Fields**</span></span>

- <span data-ttu-id="55005-857">情報フィールド 1: セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="55005-858">情報フィールド 2: 現在のセマフォ数。</span><span class="sxs-lookup"><span data-stu-id="55005-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="55005-859">情報フィールド 3: セマフォで中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="55005-860">情報フィールド 4: 呼び出しに指定されたシーリング制限。</span><span class="sxs-lookup"><span data-stu-id="55005-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="55005-861">セマフォ作成</span><span class="sxs-lookup"><span data-stu-id="55005-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="55005-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="55005-862">tx_semaphore_create</span></span>

<span data-ttu-id="55005-863">**アイコン** ![セマフォ作成アイコン](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="55005-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="55005-864">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-864">**Description**</span></span>

<span data-ttu-id="55005-865">このイベントは、tx_semaphore_create を使用したセマフォの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="55005-866">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-866">**Information Fields**</span></span>

- <span data-ttu-id="55005-867">情報フィールド 1: セマフォ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="55005-868">情報フィールド 2: 初期のセマフォ数。</span><span class="sxs-lookup"><span data-stu-id="55005-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="55005-869">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-870">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="55005-871">セマフォ削除</span><span class="sxs-lookup"><span data-stu-id="55005-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="55005-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="55005-872">tx_semaphore_delete</span></span>

<span data-ttu-id="55005-873">**アイコン** ![セマフォ削除アイコン](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="55005-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="55005-874">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-874">**Description**</span></span>

<span data-ttu-id="55005-875">このイベントは、tx_semaphore_delete を使用したセマフォの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="55005-876">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-876">**Information Fields**</span></span>

- <span data-ttu-id="55005-877">情報フィールド 1: セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="55005-878">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-879">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-880">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="55005-881">セマフォ取得</span><span class="sxs-lookup"><span data-stu-id="55005-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="55005-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="55005-882">tx_semaphore_get</span></span>

<span data-ttu-id="55005-883">**アイコン** ![セマフォ取得アイコン](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="55005-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="55005-884">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-884">**Description**</span></span>

<span data-ttu-id="55005-885">このイベントは、tx_semaphore_get を使用したセマフォの取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="55005-886">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-886">**Information Fields**</span></span>

- <span data-ttu-id="55005-887">情報フィールド 1: セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="55005-888">情報フィールド 2: 呼び出しに指定された待機オプション。</span><span class="sxs-lookup"><span data-stu-id="55005-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="55005-889">情報フィールド 3: 現在のセマフォ数。</span><span class="sxs-lookup"><span data-stu-id="55005-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="55005-890">情報フィールド 4: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="55005-891">セマフォ情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="55005-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="55005-893">**アイコン** ![セマフォ情報取得アイコン](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="55005-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="55005-894">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-894">**Description**</span></span>

<span data-ttu-id="55005-895">このイベントは、tx_semaphore_info_get を使用したセマフォに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="55005-896">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-896">**Information Fields**</span></span>

- <span data-ttu-id="55005-897">情報フィールド 1: セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="55005-898">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-899">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-900">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="55005-901">セマフォ パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="55005-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="55005-903">**アイコン** ![セマフォ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="55005-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="55005-904">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-904">**Description**</span></span>

<span data-ttu-id="55005-905">このイベントは、tx_semaphore_performance_info_get を使用したセマフォに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="55005-906">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-906">**Information Fields**</span></span>

- <span data-ttu-id="55005-907">情報フィールド 1: セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="55005-908">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-909">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-910">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="55005-911">セマフォ パフォーマンス システム情報</span><span class="sxs-lookup"><span data-stu-id="55005-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="55005-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="55005-913">**アイコン** ![セマフォ パフォーマンス システム情報アイコン](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="55005-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="55005-914">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-914">**Description**</span></span>

<span data-ttu-id="55005-915">このイベントは、tx_semaphore_performance_system_info_get を使用したシステム内のすべてのセマフォに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="55005-916">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-916">**Information Fields**</span></span> 

- <span data-ttu-id="55005-917">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-918">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-919">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-920">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="55005-921">セマフォ優先度付け</span><span class="sxs-lookup"><span data-stu-id="55005-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="55005-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="55005-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="55005-923">**アイコン** ![セマフォ優先度付けアイコン](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="55005-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="55005-924">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-924">**Description**</span></span>

<span data-ttu-id="55005-925">このイベントは、tx_semaphore_prioritize を使用したセマフォの中断リストの優先順位付けを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="55005-926">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-926">**Information Fields**</span></span>

- <span data-ttu-id="55005-927">情報フィールド 1: 対応するセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="55005-928">情報フィールド 2: セマフォで現在中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="55005-929">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-930">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="55005-931">セマフォ配置</span><span class="sxs-lookup"><span data-stu-id="55005-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="55005-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="55005-932">tx_semaphore_put</span></span>

<span data-ttu-id="55005-933">**アイコン** ![セマフォ配置アイコン](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="55005-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="55005-934">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-934">**Description**</span></span>

<span data-ttu-id="55005-935">このイベントは、tx_semaphore_put を使用したセマフォ インスタンスの解放を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="55005-936">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-936">**Information Fields**</span></span> 

- <span data-ttu-id="55005-937">情報フィールド 1: 対応するセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="55005-938">情報フィールド 2: 現在のセマフォ数。</span><span class="sxs-lookup"><span data-stu-id="55005-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="55005-939">情報フィールド 3: セマフォで中断されているスレッドの数。</span><span class="sxs-lookup"><span data-stu-id="55005-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="55005-940">情報フィールド 4: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="55005-941">セマフォ配置通知</span><span class="sxs-lookup"><span data-stu-id="55005-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="55005-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="55005-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="55005-943">**アイコン** ![セマフォ配置通知アイコン](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="55005-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="55005-944">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-944">**Description**</span></span>

<span data-ttu-id="55005-945">このイベントは、セマフォ インスタンスが配置されるたびに呼び出される tx_semaphore_put_notify を使用したコールバックの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="55005-946">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-946">**Information Fields**</span></span> 

- <span data-ttu-id="55005-947">情報フィールド 1: セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="55005-948">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-949">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-950">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="55005-951">スレッド作成</span><span class="sxs-lookup"><span data-stu-id="55005-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="55005-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="55005-952">tx_thread_create</span></span>

<span data-ttu-id="55005-953">**アイコン** ![スレッド作成アイコン](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="55005-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="55005-954">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-954">**Description**</span></span>

<span data-ttu-id="55005-955">このイベントは、tx_thread_create を使用したスレッドの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="55005-956">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-956">**Information Fields**</span></span>

- <span data-ttu-id="55005-957">情報フィールド 1: スレッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="55005-958">情報フィールド 2: スレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="55005-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="55005-959">情報フィールド 3: スレッドのスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="55005-960">情報フィールド 4: スタックのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="55005-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="55005-961">スレッド削除</span><span class="sxs-lookup"><span data-stu-id="55005-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="55005-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="55005-962">tx_thread_delete</span></span>

<span data-ttu-id="55005-963">**アイコン** ![スレッド削除アイコン](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="55005-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="55005-964">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-964">**Description**</span></span>

<span data-ttu-id="55005-965">このイベントは、tx_thread_delete を使用したスレッドの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="55005-966">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-966">**Information Fields**</span></span> 

- <span data-ttu-id="55005-967">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-968">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-969">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-970">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="55005-971">スレッド開始/終了通知</span><span class="sxs-lookup"><span data-stu-id="55005-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="55005-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="55005-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="55005-973">**アイコン** ![スレッド開始/終了通知アイコン](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="55005-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="55005-974">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-974">**Description**</span></span>

<span data-ttu-id="55005-975">このイベントは、スレッドが開始または終了するたびに呼び出される tx_thread_entry_exit_notify を使用したコールバックの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="55005-976">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-976">**Information Fields**</span></span> 

- <span data-ttu-id="55005-977">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-978">情報フィールド 2: 登録時のスレッド状態。</span><span class="sxs-lookup"><span data-stu-id="55005-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="55005-979">情報フィールド 3: 呼び出し時のスタックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="55005-980">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="55005-981">スレッド識別</span><span class="sxs-lookup"><span data-stu-id="55005-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="55005-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="55005-982">tx_thread_identify</span></span>

<span data-ttu-id="55005-983">**アイコン** ![スレッド識別アイコン](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="55005-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="55005-984">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-984">**Description**</span></span>

<span data-ttu-id="55005-985">このイベントは、tx_thread_identify を使用した現在のスレッド ポインターの取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="55005-986">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-986">**Information Fields**</span></span>

- <span data-ttu-id="55005-987">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-988">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-989">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-990">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="55005-991">スレッド情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="55005-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-992">tx_thread_info_get</span></span>

<span data-ttu-id="55005-993">**アイコン** ![スレッド情報取得アイコン](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="55005-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="55005-994">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-994">**Description**</span></span>

<span data-ttu-id="55005-995">このイベントは、tx_thread_info_get を使用した指定されたスレッドに関する情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="55005-996">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-996">**Information Fields**</span></span>

- <span data-ttu-id="55005-997">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-998">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="55005-999">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1000">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="55005-1001">スレッド パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="55005-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="55005-1003">**アイコン** ![スレッド パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="55005-1004">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1004">**Description**</span></span>

<span data-ttu-id="55005-1005">このイベントは、tx_thread_performance_info_get を使用した指定されたスレッドに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="55005-1006">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1006">**Information Fields**</span></span>

- <span data-ttu-id="55005-1007">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1008">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="55005-1009">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1010">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="55005-1011">スレッド パフォーマンス システム情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="55005-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="55005-1013">**アイコン** ![スレッド パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="55005-1014">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1014">**Description**</span></span>

<span data-ttu-id="55005-1015">このイベントは、tx_thread_performance_system_info_get を使用したすべてのスレッドに関するパフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="55005-1016">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1016">**Information Fields**</span></span> 

- <span data-ttu-id="55005-1017">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-1018">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1019">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1020">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="55005-1021">スレッド プリエンプション変更</span><span class="sxs-lookup"><span data-stu-id="55005-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="55005-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="55005-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="55005-1023">**アイコン** ![スレッド プリエンプション変更アイコン](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="55005-1024">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1024">**Description**</span></span>

<span data-ttu-id="55005-1025">このイベントは、tx_thread_preemption_change を使用したスレッドのプリエンプションしきい値の変更を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="55005-1026">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1026">**Information Fields**</span></span> 

- <span data-ttu-id="55005-1027">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1028">情報フィールド 2: 新しいプリエンプションしきい値。</span><span class="sxs-lookup"><span data-stu-id="55005-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="55005-1029">情報フィールド 3: 以前のプリエンプションしきい値。</span><span class="sxs-lookup"><span data-stu-id="55005-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="55005-1030">情報フィールド 4: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="55005-1031">スレッド優先度変更</span><span class="sxs-lookup"><span data-stu-id="55005-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="55005-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="55005-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="55005-1033">**アイコン** ![スレッド優先度変更アイコン](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="55005-1034">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1034">**Description**</span></span>

<span data-ttu-id="55005-1035">このイベントは、tx_thread_priority_change を使用したスレッドの優先順位の変更を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="55005-1036">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="55005-1036">Information Fields</span></span> 
- <span data-ttu-id="55005-1037">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1038">情報フィールド 2: 新しい優先順位。</span><span class="sxs-lookup"><span data-stu-id="55005-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="55005-1039">情報フィールド 3: 以前の優先順位。</span><span class="sxs-lookup"><span data-stu-id="55005-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="55005-1040">情報フィールド 4: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="55005-1041">スレッド放棄</span><span class="sxs-lookup"><span data-stu-id="55005-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="55005-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="55005-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="55005-1043">**アイコン** ![スレッド放棄アイコン](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="55005-1044">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1044">**Description**</span></span>

<span data-ttu-id="55005-1045">このイベントは、tx_thread_relinquish を使用したスレッドからのプロセッサの解放を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="55005-1046">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1046">**Information Fields**</span></span>

- <span data-ttu-id="55005-1047">情報フィールド 1: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1048">情報フィールド 2: 次に実行するスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="55005-1049">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1050">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="55005-1051">スレッド リセット</span><span class="sxs-lookup"><span data-stu-id="55005-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="55005-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="55005-1052">tx_thread_reset</span></span>

<span data-ttu-id="55005-1053">**アイコン** ![スレッド リセット アイコン](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="55005-1054">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1054">**Description**</span></span>

<span data-ttu-id="55005-1055">このイベントは、tx_thread_reset を使用した完了または終了したスレッドのリセットを表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="55005-1056">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1056">**Information Fields**</span></span>

- <span data-ttu-id="55005-1057">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1058">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="55005-1059">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1060">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="55005-1061">スレッド再開</span><span class="sxs-lookup"><span data-stu-id="55005-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="55005-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="55005-1062">tx_thread_resume</span></span>

<span data-ttu-id="55005-1063">**アイコン** ![スレッド再開アイコン](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="55005-1064">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1064">**Description**</span></span>

<span data-ttu-id="55005-1065">このイベントは、tx_thread_resume を使用した中断されたスレッドの再開を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="55005-1066">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1066">**Information Fields**</span></span>

- <span data-ttu-id="55005-1067">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1068">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="55005-1069">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1070">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="55005-1071">スレッド スリープ</span><span class="sxs-lookup"><span data-stu-id="55005-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="55005-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="55005-1072">tx_thread_sleep</span></span>

<span data-ttu-id="55005-1073">**アイコン** ![スレッド スリープ アイコン](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="55005-1074">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1074">**Description**</span></span>

<span data-ttu-id="55005-1075">このイベントは、tx_thread_sleep を使用した指定されたタイマー ティック数の現在のスレッドの中断を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="55005-1076">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1076">**Information Fields**</span></span>

- <span data-ttu-id="55005-1077">情報フィールド 1: 中断するティック数。</span><span class="sxs-lookup"><span data-stu-id="55005-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="55005-1078">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="55005-1079">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1080">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="55005-1081">スレッド スタック エラー通知</span><span class="sxs-lookup"><span data-stu-id="55005-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="55005-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="55005-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="55005-1083">**アイコン** ![スレッド スタック エラー通知アイコン](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="55005-1084">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1084">**Description**</span></span>

<span data-ttu-id="55005-1085">このイベントは、tx_thread_stack_error_notify_event を使用したスレッド スタック エラー通知ルーチンの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="55005-1086">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1086">**Information Fields**</span></span> 

- <span data-ttu-id="55005-1087">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-1088">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1089">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1090">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="55005-1091">スレッド中断</span><span class="sxs-lookup"><span data-stu-id="55005-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="55005-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="55005-1092">tx_thread_suspend</span></span>

<span data-ttu-id="55005-1093">**アイコン** ![スレッド中断アイコン](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="55005-1094">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1094">**Description**</span></span>

<span data-ttu-id="55005-1095">このイベントは、tx_thread_suspend を使用したスレッドの中断を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="55005-1096">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1096">**Information Fields**</span></span> 

- <span data-ttu-id="55005-1097">情報フィールド 1: 中断するスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="55005-1098">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="55005-1099">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1100">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="55005-1101">スレッド終了</span><span class="sxs-lookup"><span data-stu-id="55005-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="55005-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="55005-1102">tx_thread_terminate</span></span>

<span data-ttu-id="55005-1103">**アイコン** ![スレッド終了アイコン](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="55005-1104">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1104">**Description**</span></span>

<span data-ttu-id="55005-1105">このイベントは、tx_thread_terminate を使用したスレッドの終了を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="55005-1106">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1106">**Information Fields**</span></span> 

- <span data-ttu-id="55005-1107">情報フィールド 1: 終了するスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="55005-1108">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="55005-1109">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1110">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="55005-1111">スレッド タイム スライス変更</span><span class="sxs-lookup"><span data-stu-id="55005-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="55005-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="55005-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="55005-1113">**アイコン** ![スレッド タイム スライス変更アイコン](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="55005-1114">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1114">**Description**</span></span>

<span data-ttu-id="55005-1115">このイベントは、tx_thread_time_slice_change を使用したスレッドのタイム スライスの変更を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="55005-1116">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1116">**Information Fields**</span></span>

- <span data-ttu-id="55005-1117">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1118">情報フィールド 2: 新しいタイム スライス。</span><span class="sxs-lookup"><span data-stu-id="55005-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="55005-1119">情報フィールド 3: 以前のタイム スライス。</span><span class="sxs-lookup"><span data-stu-id="55005-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="55005-1120">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="55005-1121">スレッド待機中止</span><span class="sxs-lookup"><span data-stu-id="55005-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="55005-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="55005-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="55005-1123">**アイコン** ![スレッド待機中止アイコン](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="55005-1124">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1124">**Description**</span></span>

<span data-ttu-id="55005-1125">このイベントは、tx_thread_wait_abort を使用したスレッドの中断の中止を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="55005-1126">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1126">**Information Fields**</span></span>

- <span data-ttu-id="55005-1127">情報フィールド 1: スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="55005-1128">情報フィールド 2: 呼び出し時のスレッドの状態。</span><span class="sxs-lookup"><span data-stu-id="55005-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="55005-1129">情報フィールド 3: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1130">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="55005-1131">時間取得</span><span class="sxs-lookup"><span data-stu-id="55005-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="55005-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="55005-1132">tx_time_get</span></span>

<span data-ttu-id="55005-1133">**アイコン** ![時間取得アイコン](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="55005-1134">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1134">**Description**</span></span>

<span data-ttu-id="55005-1135">このイベントは、tx_time_get を使用した現在のタイマー ティック数の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="55005-1136">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1136">**Information Fields**</span></span>

- <span data-ttu-id="55005-1137">情報フィールド 1: 現在のタイマー ティック数。</span><span class="sxs-lookup"><span data-stu-id="55005-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="55005-1138">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1139">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1140">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="55005-1141">時間設定</span><span class="sxs-lookup"><span data-stu-id="55005-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="55005-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="55005-1142">tx_time_set</span></span>

<span data-ttu-id="55005-1143">**アイコン** ![時間設定アイコン](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="55005-1144">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1144">**Description**</span></span>

<span data-ttu-id="55005-1145">このイベントは、tx_time_set を使用した現在のタイマー ティック数の設定を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="55005-1146">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1146">**Information Fields**</span></span>

- <span data-ttu-id="55005-1147">情報フィールド 1: 新しいタイマー ティック数。</span><span class="sxs-lookup"><span data-stu-id="55005-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="55005-1148">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1149">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1150">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="55005-1151">タイマー アクティブ化</span><span class="sxs-lookup"><span data-stu-id="55005-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="55005-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="55005-1152">tx_timer_activate</span></span>

<span data-ttu-id="55005-1153">**アイコン** ![タイマー アクティブ化アイコン](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="55005-1154">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1154">**Description**</span></span>

<span data-ttu-id="55005-1155">このイベントは、tx_timer_activate を使用した指定されたタイマーのアクティブ化を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="55005-1156">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1156">**Information Fields**</span></span>

- <span data-ttu-id="55005-1157">情報フィールド 1: タイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="55005-1158">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1159">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1160">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="55005-1161">タイマー変更</span><span class="sxs-lookup"><span data-stu-id="55005-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="55005-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="55005-1162">tx_timer_change</span></span>

<span data-ttu-id="55005-1163">**アイコン** ![タイマー変更アイコン](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="55005-1164">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1164">**Description**</span></span>

<span data-ttu-id="55005-1165">このイベントは、tx_timer_change を使用した指定されたタイマーの変更を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="55005-1166">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1166">**Information Fields**</span></span>

- <span data-ttu-id="55005-1167">情報フィールド 1: タイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="55005-1168">情報フィールド 2: 初期の有効期限のティック。</span><span class="sxs-lookup"><span data-stu-id="55005-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="55005-1169">情報フィールド 3: 有効期限のティックの再スケジュール。</span><span class="sxs-lookup"><span data-stu-id="55005-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="55005-1170">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="55005-1171">タイマー作成</span><span class="sxs-lookup"><span data-stu-id="55005-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="55005-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="55005-1172">tx_timer_create</span></span>

<span data-ttu-id="55005-1173">**アイコン** ![タイマー作成アイコン](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="55005-1174">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1174">**Description**</span></span>

<span data-ttu-id="55005-1175">このイベントは、tx_timer_create を使用したタイマーの作成を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="55005-1176">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1176">**Information Fields**</span></span>

- <span data-ttu-id="55005-1177">情報フィールド 1: タイマー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="55005-1178">情報フィールド 2: 初期の有効期限のティック。</span><span class="sxs-lookup"><span data-stu-id="55005-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="55005-1179">情報フィールド 3: 有効期限のティックの再スケジュール。</span><span class="sxs-lookup"><span data-stu-id="55005-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="55005-1180">情報フィールド 4: 自動有効化値。TX_AUTO_ACTIVATE (1) または TX_NO_ACTIVATE (0) のいずれか。</span><span class="sxs-lookup"><span data-stu-id="55005-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="55005-1181">タイマー非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="55005-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="55005-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="55005-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="55005-1183">**アイコン** ![タイマー非アクティブ化アイコン](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="55005-1184">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1184">**Description**</span></span>

<span data-ttu-id="55005-1185">このイベントは、tx_timer_deactivate を使用したタイマーの非アクティブ化を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="55005-1186">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1186">**Information Fields**</span></span>

- <span data-ttu-id="55005-1187">情報フィールド 1: タイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="55005-1188">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1189">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1190">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="55005-1191">タイマー削除</span><span class="sxs-lookup"><span data-stu-id="55005-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="55005-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="55005-1192">tx_timer_delete</span></span>

<span data-ttu-id="55005-1193">**アイコン** ![タイマー削除アイコン](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="55005-1194">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1194">**Description**</span></span>

<span data-ttu-id="55005-1195">このイベントは、tx_timer_delete を使用したタイマーの削除を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="55005-1196">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1196">**Information Fields**</span></span> 

- <span data-ttu-id="55005-1197">情報フィールド 1: タイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="55005-1198">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1199">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1200">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="55005-1201">タイマー情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="55005-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-1202">tx_timer_info_get</span></span>

<span data-ttu-id="55005-1203">**アイコン** ![タイマー取得情報アイコン](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="55005-1204">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1204">**Description**</span></span>

<span data-ttu-id="55005-1205">このイベントは、tx_timer_info_get を使用したタイマー情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="55005-1206">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1206">**Information Fields**</span></span>

- <span data-ttu-id="55005-1207">情報フィールド 1: タイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="55005-1208">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1209">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1210">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="55005-1211">タイマー パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="55005-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="55005-1213">**アイコン** ![タイマー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="55005-1214">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1214">**Description**</span></span> 

<span data-ttu-id="55005-1215">このイベントは、tx_timer_performance_info_get を使用したタイマー パフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="55005-1216">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1216">**Information Fields**</span></span>

- <span data-ttu-id="55005-1217">情報フィールド 1: タイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="55005-1218">情報フィールド 2: 呼び出し時のスタック ポインター。</span><span class="sxs-lookup"><span data-stu-id="55005-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="55005-1219">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1220">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="55005-1221">タイマー システム パフォーマンス情報取得</span><span class="sxs-lookup"><span data-stu-id="55005-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="55005-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="55005-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="55005-1223">**アイコン** ![タイマー システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="55005-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="55005-1224">**説明**</span><span class="sxs-lookup"><span data-stu-id="55005-1224">**Description**</span></span> 

<span data-ttu-id="55005-1225">このイベントは、tx_timer_performance_system_info_get を使用したすべてのタイマー パフォーマンス情報の取得を表します。</span><span class="sxs-lookup"><span data-stu-id="55005-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="55005-1226">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="55005-1226">**Information Fields**</span></span>

- <span data-ttu-id="55005-1227">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="55005-1228">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="55005-1229">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="55005-1230">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="55005-1230">Info Field 4: Not used.</span></span>