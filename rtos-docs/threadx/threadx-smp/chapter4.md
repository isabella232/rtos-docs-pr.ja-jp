---
title: 第 4 章 - Azure RTOS ThreadX SMP サービスの説明
description: この章は、すべての Azure RTOS ThreadX SMP サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812839"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="220d0-103">第 4 章 - Azure RTOS ThreadX SMP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="220d0-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="220d0-104">この章は、すべての Azure RTOS ThreadX SMP サービスの説明をアルファベット順にまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="220d0-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="220d0-105">これらの名前は、類似するすべてのサービスがグループ化されるよう命名されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="220d0-106">次の説明の「戻り値」セクション内の **太字** で記載されている値は、API エラー チェックを無効にする際に使用される **TX_DISABLE_ERROR_CHECKING** 定義の影響を受けません。一方、太字以外の値は完全に無効になっています。</span><span class="sxs-lookup"><span data-stu-id="220d0-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="220d0-107">さらに、"**プリエンプション可能**" というの見出しの下に "**はい**" と表示されているものは、そのサービスを呼び出すと優先順位の高いスレッドが再開され、呼び出し元のスレッドが割り込まれます。</span><span class="sxs-lookup"><span data-stu-id="220d0-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="220d0-108">**tx_block_allocate**: *固定サイズのメモリ ブロックの割り当て*</span><span class="sxs-lookup"><span data-stu-id="220d0-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="220d0-109">**tx_block_pool_create**: *固定サイズのメモリ ブロック プールの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="220d0-110">**tx_block_pool_delete**: *メモリ ブロック プールの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="220d0-111">**tx_block_pool_info_get**: *ブロック プールに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="220d0-112">**tx_block_pool_performance_info_get**: *ブロック プールのパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="220d0-113">**tx_block_pool_performance_system_info_get**: *ブロック プール システムのパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="220d0-114">**tx_block_pool_prioritize**: *ブロック プールの中断リストの優先順位の設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="220d0-115">**tx_block_release**: *固定サイズのメモリ ブロックの解放*</span><span class="sxs-lookup"><span data-stu-id="220d0-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="220d0-116">**tx_byte_allocate**: *メモリのバイト数の割り当て*</span><span class="sxs-lookup"><span data-stu-id="220d0-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="220d0-117">**tx_byte_pool_create**: *メモリ バイト プールの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="220d0-118">**tx_byte_pool_delete**: *メモリ バイト プールの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="220d0-119">**tx_byte_pool_info_get**: *バイト プールに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="220d0-120">**tx_byte_pool_performance_info_get**: *バイト プールのパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="220d0-121">**tx_byte_pool_performance_system_info_get**: *バイト プール システムのパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="220d0-122">**tx_byte_pool_prioritize**: *バイト プールの中断リストの優先順位の設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="220d0-123">**tx_byte_release**: *メモリ プールへバイトを解放*</span><span class="sxs-lookup"><span data-stu-id="220d0-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="220d0-124">**tx_event_flags_create**: *イベント フラグ グループの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="220d0-125">**tx_event_flags_delete**: *イベント フラグ グループの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="220d0-126">**tx_event_flags_get**: *イベント フラグ グループからのイベント フラグの取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="220d0-127">**tx_event_flags_info_get**: *イベント フラグ グループに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="220d0-128">**tx_event_flags_performance_info_get**: *イベント フラグ グループのパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="220d0-129">**tx_event_flags_performance_system_info_get**: *パフォーマンス システム情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="220d0-130">**tx_event_flags_set**: *イベント フラグ グループでのイベント フラグの設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="220d0-131">**tx_event_flags_set_notify**: *イベント フラグの設定時にアプリケーションに通知*</span><span class="sxs-lookup"><span data-stu-id="220d0-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="220d0-132">**tx_interrupt_control**: *割り込みの有効化と無効化*</span><span class="sxs-lookup"><span data-stu-id="220d0-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="220d0-133">**tx_mutex_create**: *相互排他ミューテックスの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="220d0-134">**tx_mutex_delete**: *相互排他ミューテックスの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="220d0-135">**tx_mutex_get**: *ミューテックスの所有権の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="220d0-136">**tx_mutex_info_get**: *ミューテックスに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="220d0-137">**tx_mutex_performance_info_get**: *ミューテックスのパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="220d0-138">**tx_mutex_performance_system_info_get**: *ミューテックスのシステム パフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="220d0-139">**tx_mutex_prioritize**: *ミューテックスの中断リストの優先順位の設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="220d0-140">**tx_mutex_put**: *ミューテックスの所有権の解放*</span><span class="sxs-lookup"><span data-stu-id="220d0-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="220d0-141">**tx_queue_create**: *メッセージ キューの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="220d0-142">**tx_queue_delete**: *メッセージ キューの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="220d0-143">**tx_queue_flush**: *メッセージ キューのメッセージを空にする*</span><span class="sxs-lookup"><span data-stu-id="220d0-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="220d0-144">**tx_queue_front_send**: *メッセージをキューの先頭に送る*</span><span class="sxs-lookup"><span data-stu-id="220d0-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="220d0-145">**tx_queue_info_get**: *キューに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="220d0-146">**tx_queue_performance_info_get**: *キューに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="220d0-147">**tx_queue_performance_system_info_get**: *キュー システムに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="220d0-148">**tx_queue_prioritize**: *キューの中断リストの優先順位の設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="220d0-149">**tx_queue_receive**: *メッセージ キューからのメッセージの取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="220d0-150">**tx_queue_send**: *メッセージ キューへのメッセージの送信*</span><span class="sxs-lookup"><span data-stu-id="220d0-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="220d0-151">**tx_queue_send_notify**: *メッセージをキューに送信するときにアプリケーションに通知*</span><span class="sxs-lookup"><span data-stu-id="220d0-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="220d0-152">**tx_semaphore_ceiling_put**: *上限が設定されたカウント セマフォへのインスタンスの配置*</span><span class="sxs-lookup"><span data-stu-id="220d0-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="220d0-153">**tx_semaphore_create**: *カウント セマフォの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="220d0-154">**tx_semaphore_delete**: *カウント セマフォの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="220d0-155">**tx_semaphore_get**: *カウント セマフォからのインスタンスの取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="220d0-156">**tx_semaphore_info_get**: *セマフォに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="220d0-157">**tx_semaphore_performance_info_get**: *セマフォに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="220d0-158">**tx_semaphore_performance_system_info_get**: *セマフォ システムに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="220d0-159">**tx_semaphore_prioritize**: *セマフォの中断リストの優先順位の設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="220d0-160">**tx_semaphore_put**: *カウント セマフォへのインスタンスの配置*</span><span class="sxs-lookup"><span data-stu-id="220d0-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="220d0-161">**tx_semaphore_put_notify**: *セマフォの配置時にアプリケーションに通知*</span><span class="sxs-lookup"><span data-stu-id="220d0-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="220d0-162">**tx_thread_create**: *アプリケーション スレッドの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="220d0-163">**tx_thread_delete**: *アプリケーション スレッドの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="220d0-164">**tx_thread_entry_exit_notify**: *スレッドの開始または終了時にアプリケーションに通知*</span><span class="sxs-lookup"><span data-stu-id="220d0-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="220d0-165">**tx_thread_identify**: *現在実行中のスレッドを指すポインターを取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="220d0-166">**tx_thread_info_get**: *スレッドに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="220d0-167">**tx_thread_performance_info_get**: *スレッドに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="220d0-168">**tx_thread_performance_system_info_get**: *スレッド システムに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="220d0-169">**tx_thread_preemption_change**: *アプリケーション スレッドの プリエンプションしきい値 の変更*</span><span class="sxs-lookup"><span data-stu-id="220d0-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="220d0-170">**tx_thread_priority_change**: *アプリケーション スレッドの優先順位の変更*</span><span class="sxs-lookup"><span data-stu-id="220d0-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="220d0-171">**tx_thread_relinquish**: *制御を他のアプリケーション スレッドに放棄*</span><span class="sxs-lookup"><span data-stu-id="220d0-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="220d0-172">**tx_thread_reset**: *スレッドのリセット*</span><span class="sxs-lookup"><span data-stu-id="220d0-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="220d0-173">**tx_thread_resume**: *中断したアプリケーション スレッドの再開*</span><span class="sxs-lookup"><span data-stu-id="220d0-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="220d0-174">**tx_thread_sleep**: *現在のスレッドを指定された時間だけ中断*</span><span class="sxs-lookup"><span data-stu-id="220d0-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="220d0-175">**tx_thread_smp_core_exclude**: *一連のコアでスレッドの実行を除外*</span><span class="sxs-lookup"><span data-stu-id="220d0-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="220d0-176">**tx_thread_smp_core_exclude_get**: *スレッドで現在除外されているコアを取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="220d0-177">**tx_thread_smp_core_get**: *現在実行中の呼び出し元のコアの取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="220d0-178">**tx_thread_stack_error_notify**: *スレッド スタック エラー通知コールバックの登録*</span><span class="sxs-lookup"><span data-stu-id="220d0-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="220d0-179">**tx_thread_suspend**: *アプリケーション スレッドの中断*</span><span class="sxs-lookup"><span data-stu-id="220d0-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="220d0-180">**tx_thread_terminate**: *アプリケーション スレッドを終了*</span><span class="sxs-lookup"><span data-stu-id="220d0-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="220d0-181">**tx_thread_time_slice_change**: *アプリケーション スレッドのタイムスライスの変更*</span><span class="sxs-lookup"><span data-stu-id="220d0-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="220d0-182">**tx_thread_wait_abort**: *指定したスレッドの中断の中止*</span><span class="sxs-lookup"><span data-stu-id="220d0-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="220d0-183">**tx_time_get**: *現在の時刻の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="220d0-184">**tx_time_set**: *現在の時刻の設定*</span><span class="sxs-lookup"><span data-stu-id="220d0-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="220d0-185">**tx_timer_activate**: *アプリケーション タイマーのアクティブ化*</span><span class="sxs-lookup"><span data-stu-id="220d0-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="220d0-186">**tx_timer_change**: *アプリケーション タイマーの変更*</span><span class="sxs-lookup"><span data-stu-id="220d0-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="220d0-187">**tx_timer_create**: *アプリケーション タイマーの作成*</span><span class="sxs-lookup"><span data-stu-id="220d0-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="220d0-188">**tx_timer_deactivate**: *アプリケーション タイマーの非アクティブ化*</span><span class="sxs-lookup"><span data-stu-id="220d0-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="220d0-189">**tx_timer_delete**: *アプリケーション タイマーの削除*</span><span class="sxs-lookup"><span data-stu-id="220d0-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="220d0-190">**tx_timer_info_get**: *アプリケーション タイマーに関する情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="220d0-191">**tx_timer_performance_info_get**: *タイマーに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="220d0-192">**tx_timer_performance_system_info_get**: *タイマー システムに関するパフォーマンス情報の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="220d0-193">**tx_timer_smp_core_exclude**: *一連のコアでタイマー実行を除外*</span><span class="sxs-lookup"><span data-stu-id="220d0-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="220d0-194">**tx_timer_smp_core_exclude_get**: *タイマーの現在のコアの除外の取得*</span><span class="sxs-lookup"><span data-stu-id="220d0-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="220d0-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-195">tx_block_allocate</span></span>
<span data-ttu-id="220d0-196">固定サイズのメモリ ブロックを割り当てます</span><span class="sxs-lookup"><span data-stu-id="220d0-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-197">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-198">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-198">Description</span></span>

<span data-ttu-id="220d0-199">このサービスを使用すると、指定したメモリ プールから固定サイズのメモリ ブロックが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="220d0-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="220d0-200">メモリ ブロックの実際のサイズは、メモリ プールの作成時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="220d0-201">アプリケーション コードによって、割り当てられたメモリ ブロックの外部に書き込まれないようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="220d0-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="220d0-202">これが発生すると、隣接する (通常は後続の) メモリ ブロックが破損します。</span><span class="sxs-lookup"><span data-stu-id="220d0-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="220d0-203">結果は予測不可能で、多くの場合、致命的です。</span><span class="sxs-lookup"><span data-stu-id="220d0-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-204">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-204">Parameters</span></span>

- <span data-ttu-id="220d0-205">**pool_ptr**: 以前に作成されたメモリ ブロック プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="220d0-206">**block_ptr**: 宛先ブロック ポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="220d0-207">割り当てが正常に行われると、割り当てられたメモリ ブロックのアドレスが、このパラメーターが指す位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="220d0-208">**wait_option**: 使用可能なメモリ ブロックがない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="220d0-209">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-210">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-212">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="220d0-213">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスから直ちに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="220d0-214">これは、サービスが非スレッド (たとえば、初期化、タイマー、ISR など) から呼び出された場合にのみ有効なオプションです。</span><span class="sxs-lookup"><span data-stu-id="220d0-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="220d0-215">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、メモリ ブロックが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="220d0-216">数値 (1-0xFFFFFFFE) を選択すると、中断してメモリ ブロックを待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-217">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-217">Return Values</span></span>

- <span data-ttu-id="220d0-218">**TX_SUCCESS**: (0x00) メモリ ブロックの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="220d0-219">**TX_DELETED**: (0x01) スレッドが中断されている間にメモリ ブロック プールが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-220">**TX_NO_MEMORY**: (0x10) 指定された待機時間内にメモリ ブロックを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="220d0-221">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="220d0-222">TX_POOL_ERROR: (0x02) メモリ ブロック プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="220d0-223">TX_PTR_ERROR: (0x03) 宛先ポインターを指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="220d0-224">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-225">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-225">Allowed From</span></span>

<span data-ttu-id="220d0-226">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-227">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-227">Preemption Possible</span></span>

<span data-ttu-id="220d0-228">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-229">例</span><span class="sxs-lookup"><span data-stu-id="220d0-229">Example</span></span>

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="220d0-230">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-230">See Also</span></span>

- <span data-ttu-id="220d0-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-231">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="220d0-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="220d0-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-238">tx_block_pool_create</span></span>
<span data-ttu-id="220d0-239">固定サイズのメモリ ブロック プールの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-240">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="220d0-241">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-241">Description</span></span>

<span data-ttu-id="220d0-242">このサービスを使用すると、固定サイズのメモリ ブロック プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="220d0-243">指定したメモリ領域は、次の式を使用して、可能な限り多くの固定サイズのメモリ ブロックに分割されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="220d0-244">**合計ブロック** = (**合計バイト**) / (**ブロック サイズ** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="220d0-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-245">各メモリ ブロックには、ユーザーには見えない、前の数式の "sizeof (void \*)" で表されるオーバー ヘッドのポインターが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="220d0-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-246">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-246">Parameters</span></span>

- <span data-ttu-id="220d0-247">**pool_ptr**: メモリ ブロック プールの制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="220d0-248">**name_ptr**: メモリ ブロック プールの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="220d0-249">**block_size**: 各メモリ ブロック内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="220d0-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="220d0-250">**pool_start**: メモリ ブロック プールの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="220d0-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="220d0-251">開始アドレスは、ULONG データ型のサイズに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="220d0-252">**pool_size**: メモリ ブロック プールで使用可能な合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="220d0-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-253">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-253">Return Values</span></span>

- <span data-ttu-id="220d0-254">**TX_SUCCESS**: (0x00) メモリ ブロック プールの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="220d0-255">TX_POOL_ERROR: (0x02) メモリ ブロック プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="220d0-256">ポインターが NULL であるか、プールが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="220d0-257">TX_PTR_ERROR: (0x03) プールの開始アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="220d0-258">TX_SIZE_ERROR: (0x05) プールのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="220d0-259">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-260">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-260">Allowed From</span></span>

<span data-ttu-id="220d0-261">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-262">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-262">Preemption Possible</span></span>

<span data-ttu-id="220d0-263">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-263">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-264">例</span><span class="sxs-lookup"><span data-stu-id="220d0-264">Example</span></span>

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-265">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-265">See Also</span></span>

- <span data-ttu-id="220d0-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-266">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="220d0-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="220d0-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-273">tx_block_pool_delete</span></span>

<span data-ttu-id="220d0-274">メモリ ブロック プールの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-275">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-276">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-276">Description</span></span>

<span data-ttu-id="220d0-277">このサービスを使用すると、指定したブロック メモリ プールが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="220d0-278">このプールからのメモリ ブロックを待機しているすべての中断されたスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-279">プールに関連付けられているメモリ領域の管理はアプリケーションの役割です。これは、サービスの完了後に利用できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="220d0-280">また、このアプリケーションでは、削除されたプールまたはその前のメモリ ブロックが使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-281">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-281">Parameters</span></span>

- <span data-ttu-id="220d0-282">**pool_ptr**: 以前に作成されたメモリ ブロック プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-283">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-283">Return Values</span></span>

- <span data-ttu-id="220d0-284">**TX_SUCCESS**: (0x00) メモリ ブロック プールの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="220d0-285">TX_POOL_ERROR: (0x02) メモリ ブロック プールポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="220d0-286">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-287">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-287">Allowed From</span></span>

<span data-ttu-id="220d0-288">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-289">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-289">Preemption Possible</span></span>

<span data-ttu-id="220d0-290">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-291">例</span><span class="sxs-lookup"><span data-stu-id="220d0-291">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-292">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-292">See Also</span></span>

- <span data-ttu-id="220d0-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-293">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-294">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="220d0-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="220d0-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="220d0-301">ブロック プールに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-302">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="220d0-303">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-303">Description</span></span>

<span data-ttu-id="220d0-304">このサービスを使用すると、指定したブロック メモリ プールに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-305">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-305">Parameters</span></span>

- <span data-ttu-id="220d0-306">**pool_ptr**: 以前に作成されたメモリ ブロック プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="220d0-307">**name**: ブロック プールの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="220d0-308">**available**: ブロック プール内の使用可能なブロック数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="220d0-309">**total_blocks**: ブロック プール内のブロックの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="220d0-310">**first_suspended**: このブロック プールの中断リストの最初にあるスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="220d0-311">**suspended_count**: このブロック プールで現在中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="220d0-312">**next_pool**: 次に作成されたブロック プールのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-313">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-314">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-314">Return Values</span></span>

- <span data-ttu-id="220d0-315">**TX_SUCCESS**: (0x00) ブロック プールの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="220d0-316">TX_POOL_ERROR: (0x02) メモリ ブロック プールポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-317">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-317">Allowed From</span></span>

<span data-ttu-id="220d0-318">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-319">例</span><span class="sxs-lookup"><span data-stu-id="220d0-319">Example</span></span>

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-320">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-320">See Also</span></span>

- <span data-ttu-id="220d0-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-321">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-322">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="220d0-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="220d0-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="220d0-330">ブロック プールのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-331">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="220d0-332">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-332">Description</span></span>

<span data-ttu-id="220d0-333">このサービスを使用すると、指定したメモリ ブロック プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-334">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-335">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-335">Parameters</span></span>

- <span data-ttu-id="220d0-336">**pool_ptr**: 以前に作成されたメモリ ブロック プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="220d0-337">**allocates**: このプールで実行された割り当て要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="220d0-338">**releases**: このプールで実行された解放要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="220d0-339">**suspensions**: このプールのスレッド割り当て保留の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="220d0-340">**timeouts**: このプールの割り当て保留タイムアウト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-341">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-342">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-342">Return Values</span></span>

- <span data-ttu-id="220d0-343">**TX_SUCCESS**: (0x00) ブロック プールのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="220d0-344">**TX_PTR_ERROR**: (0x03) ブロック プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="220d0-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-346">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-346">Allowed From</span></span>

<span data-ttu-id="220d0-347">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-348">例</span><span class="sxs-lookup"><span data-stu-id="220d0-348">Example</span></span>

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-349">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-349">See Also</span></span>

- <span data-ttu-id="220d0-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-350">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-351">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="220d0-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="220d0-358">ブロック プール システムのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-359">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-360">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-360">Description</span></span>

<span data-ttu-id="220d0-361">このサービスを使用すると、アプリケーション内のすべてのメモリ ブロック プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-362">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-363">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-363">Parameters</span></span>

- <span data-ttu-id="220d0-364">**allocates**: すべてのブロック プールで実行された割り当て要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="220d0-365">**releases**: すべてのブロック プールで実行されたリリース要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="220d0-366">**suspensions**: すべてのブロック プールのスレッド割り当て保留の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="220d0-367">**timeouts**: すべてのブロック プールで実行される割り当て保留タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-368">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-369">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-369">Return Values</span></span>

- <span data-ttu-id="220d0-370">**TX_SUCCESS**: (0x00) ブロック プール システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="220d0-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-372">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-372">Allowed From</span></span>

<span data-ttu-id="220d0-373">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-374">例</span><span class="sxs-lookup"><span data-stu-id="220d0-374">Example</span></span>

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-375">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-375">See Also</span></span>

- <span data-ttu-id="220d0-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-376">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-377">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="220d0-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="220d0-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="220d0-384">ブロック プールの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="220d0-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-385">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-386">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-386">Description</span></span>

<span data-ttu-id="220d0-387">このサービスを使用すると、このプール上のメモリ ブロックで中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="220d0-388">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-389">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-389">Parameters</span></span> 

- <span data-ttu-id="220d0-390">**pool_ptr**: メモリ ブロック プールの制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-391">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-391">Return Values</span></span>

- <span data-ttu-id="220d0-392">**TX_SUCCESS**: (0x00) ブロック プールの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="220d0-393">TX_POOL_ERROR: (0x02) メモリ ブロック プールポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-394">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-394">Allowed From</span></span>

<span data-ttu-id="220d0-395">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-396">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-396">Preemption Possible</span></span>

<span data-ttu-id="220d0-397">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-397">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-398">例</span><span class="sxs-lookup"><span data-stu-id="220d0-398">Example</span></span>

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-399">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-399">See Also</span></span>

- <span data-ttu-id="220d0-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-400">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-401">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="220d0-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="220d0-407">tx_block_release</span></span>

<span data-ttu-id="220d0-408">固定サイズのメモリ ブロックの解放</span><span class="sxs-lookup"><span data-stu-id="220d0-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-409">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-410">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-410">Description</span></span>

<span data-ttu-id="220d0-411">このサービスを使用すると、以前に割り当てられたブロックが、関連付けられているメモリ プールに解放されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="220d0-412">このプールからのメモリ ブロックを待機している中断中のスレッドが 1 つ以上ある場合、中断された最初のスレッドにこのメモリ ブロックが割り当てられ、再開されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-413">アプリケーションでは、プールに解放された後にメモリ ブロック領域が使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-414">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-414">Parameters</span></span>

- <span data-ttu-id="220d0-415">**block_ptr**: 以前に割り当てられていたメモリ ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-416">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-416">Return Values</span></span>

- <span data-ttu-id="220d0-417">**TX_SUCCESS**: (0x00) メモリ ブロックの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="220d0-418">TX_PTR_ERROR: (0x03) メモリ ブロックを指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-419">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-419">Allowed From</span></span>

<span data-ttu-id="220d0-420">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-421">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-421">Preemption Possible</span></span>

<span data-ttu-id="220d0-422">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-423">例</span><span class="sxs-lookup"><span data-stu-id="220d0-423">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-424">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-424">See Also</span></span>

- <span data-ttu-id="220d0-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-425">tx_block_allocate</span></span>
- <span data-ttu-id="220d0-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-426">tx_block_pool_create</span></span>
- <span data-ttu-id="220d0-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="220d0-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="220d0-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="220d0-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-432">tx_byte_allocate</span></span>

<span data-ttu-id="220d0-433">メモリのバイト数の割り当て</span><span class="sxs-lookup"><span data-stu-id="220d0-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-434">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-435">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-435">Description</span></span>

<span data-ttu-id="220d0-436">このサービスを使用すると、指定したバイト数が、指定したメモリ バイト プールから割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="220d0-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="220d0-437">アプリケーション コードによって、割り当てられたメモリ ブロックの外部に書き込まれないようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="220d0-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="220d0-438">これが発生すると、隣接する (通常は後続の) メモリ ブロックが破損します。</span><span class="sxs-lookup"><span data-stu-id="220d0-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="220d0-439">結果は予測不可能で、多くの場合、致命的です。</span><span class="sxs-lookup"><span data-stu-id="220d0-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-440">このサービスのパフォーマンスは、ブロック サイズとプール内の断片化の量によって機能します。</span><span class="sxs-lookup"><span data-stu-id="220d0-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="220d0-441">このため、このサービスは、実行のタイムクリティカルなスレッドでは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="220d0-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-442">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-442">Parameters</span></span>

- <span data-ttu-id="220d0-443">**pool_ptr**: 以前に作成されたメモリ プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="220d0-444">**memory_ptr**: 宛先メモリ ポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="220d0-445">割り当てが正常に行われると、割り当てられたメモリ領域のアドレスが、このパラメーターが指す場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="220d0-446">**memory_size**: 要求されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="220d0-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="220d0-447">**wait_option**: 使用可能なメモリが不足している場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="220d0-448">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-449">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-451">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-452">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-453">*これは、サービスが初期化から呼び出された場合にのみ有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="220d0-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="220d0-454">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、十分なメモリが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="220d0-455">数値 (1-0xFFFFFFFE) を選択すると、中断してメモリを待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-456">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-456">Return Values</span></span>

- <span data-ttu-id="220d0-457">**TX_SUCCESS**: (0x00) メモリの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="220d0-458">**TX_DELETED**: (0x01) スレッドが中断されている間にメモリ プールが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-459">**TX_NO_MEMORY**: (0x10) 指定された待機時間内にメモリを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="220d0-460">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-461">TX_POOL_ERROR: (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="220d0-462">TX_PTR_ERROR: (0x03) 宛先ポインターを指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="220d0-463">TX_SIZE_ERROR: (0X05) 要求されたサイズが 0 である、またはプールより大きい値です。</span><span class="sxs-lookup"><span data-stu-id="220d0-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="220d0-464">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="220d0-465">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-466">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-466">Allowed From</span></span>

<span data-ttu-id="220d0-467">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-468">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-468">Preemption Possible</span></span>

<span data-ttu-id="220d0-469">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-470">例</span><span class="sxs-lookup"><span data-stu-id="220d0-470">Example</span></span>

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-471">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-471">See Also</span></span>

- <span data-ttu-id="220d0-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="220d0-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="220d0-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-479">tx_byte_pool_create</span></span>

<span data-ttu-id="220d0-480">メモリ バイト プールの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-481">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="220d0-482">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-482">Description</span></span>

<span data-ttu-id="220d0-483">このサービスを使用すると、指定した領域にメモリ バイト プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="220d0-484">最初のプールは、基本的に 1 つの非常に大きな空きブロックで構成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="220d0-485">ただし、割り当てが行われると、プールは小さいブロックに分割されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-486">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-486">Parameters</span></span>

- <span data-ttu-id="220d0-487">**pool_ptr**: メモリ プールの制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="220d0-488">**name_ptr**: メモリ プールの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="220d0-489">**pool_start**: メモリ プールの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="220d0-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="220d0-490">開始アドレスは、ULONG データ型のサイズに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="220d0-491">**pool_size**: メモリ プールで使用可能な合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="220d0-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-492">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-492">Return Values</span></span>

- <span data-ttu-id="220d0-493">**TX_SUCCESS**: (0x00) メモリ プールの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="220d0-494">TX_POOL_ERROR: (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="220d0-495">ポインターが NULL であるか、プールが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="220d0-496">TX_PTR_ERROR: (0x03) プールの開始アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="220d0-497">TX_SIZE_ERROR: (0x05) プールのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="220d0-498">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-499">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-499">Allowed From</span></span>

<span data-ttu-id="220d0-500">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-501">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-501">Preemption Possible</span></span>

<span data-ttu-id="220d0-502">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-502">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-503">例</span><span class="sxs-lookup"><span data-stu-id="220d0-503">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-504">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-504">See Also</span></span>

- <span data-ttu-id="220d0-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-505">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="220d0-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="220d0-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="220d0-513">メモリ バイト プールの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-514">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-515">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-515">Description</span></span>

<span data-ttu-id="220d0-516">このサービスを使用すると、指定したメモリ バイト プールが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="220d0-517">このプールからのメモリを待機しているすべての中断されたスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-518">プールに関連付けられているメモリ領域の管理はアプリケーションの役割です。これは、サービスの完了後に利用できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="220d0-519">また、アプリケーションでは、削除されたプールまたは以前に割り当てられたメモリが使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-520">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-520">Parameters</span></span> 

- <span data-ttu-id="220d0-521">**pool_ptr**: 以前に作成されたメモリ プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-522">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-522">Return Values</span></span>

- <span data-ttu-id="220d0-523">**TX_SUCCESS**: (0x00) メモリ プールの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="220d0-524">TX_POOL_ERROR: (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="220d0-525">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-526">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-526">Allowed From</span></span>

<span data-ttu-id="220d0-527">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-528">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-528">Preemption Possible</span></span>

<span data-ttu-id="220d0-529">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-530">例</span><span class="sxs-lookup"><span data-stu-id="220d0-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-531">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-531">See Also</span></span>

- <span data-ttu-id="220d0-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-532">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="220d0-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="220d0-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="220d0-540">バイト プールに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-541">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="220d0-542">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-542">Description</span></span>

<span data-ttu-id="220d0-543">このサービスを使用すると、指定したメモリ バイト プールに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-544">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-544">Parameters</span></span>

- <span data-ttu-id="220d0-545">**pool_ptr**: 以前に作成されたメモリ プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="220d0-546">**name**: バイト プールの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="220d0-547">**available**: プール内で使用可能なバイト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="220d0-548">**fragments**: バイト プール内のメモリ フラグメントの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="220d0-549">**first_suspended**: このバイト プールの中断リストの最初にあるスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="220d0-550">**suspended_count**: このバイト プールで現在中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="220d0-551">**next_pool**: 次に作成されたバイト プールのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-552">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-553">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-553">Return Values</span></span>

- <span data-ttu-id="220d0-554">**TX_SUCCESS**: (0x00) プールの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="220d0-555">TX_POOL_ERROR: (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-556">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-556">Allowed From</span></span>

<span data-ttu-id="220d0-557">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-558">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-558">Preemption Possible</span></span>

<span data-ttu-id="220d0-559">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-559">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-560">例</span><span class="sxs-lookup"><span data-stu-id="220d0-560">Example</span></span>

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-561">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-561">See Also</span></span>

- <span data-ttu-id="220d0-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-562">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="220d0-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="220d0-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="220d0-570">バイト プールのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-571">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-572">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-572">Description</span></span>

<span data-ttu-id="220d0-573">このサービスを使用すると、指定したメモリ バイト プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-574">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-575">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-575">Parameters</span></span>

- <span data-ttu-id="220d0-576">**pool_ptr**: 以前に作成されたメモリ バイト プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="220d0-577">**allocates**: このプールで実行された割り当て要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="220d0-578">**releases**: このプールで実行された解放要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="220d0-579">**fragments_searched**: このプールでの割り当て要求中に検索された内部メモリ フラグメントの数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="220d0-580">**merges**: このプールでの割り当て要求中に統合された内部メモリ ブロック数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="220d0-581">**splits**: このプールで割り当て要求中に作成された内部メモリ ブロックの分割 (フラグメント) 数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="220d0-582">**suspensions**: このプールのスレッド割り当て保留の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="220d0-583">**timeouts**: このプールの割り当て保留タイムアウト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-584">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-585">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-585">Return Values</span></span>

- <span data-ttu-id="220d0-586">TX_SUCCESS: (0x00) バイト プールのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="220d0-587">**TX_PTR_ERROR**: (0x03) バイト プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="220d0-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-589">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-589">Allowed From</span></span>

<span data-ttu-id="220d0-590">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-591">例</span><span class="sxs-lookup"><span data-stu-id="220d0-591">Example</span></span>

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-592">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-592">See Also</span></span>

- <span data-ttu-id="220d0-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-593">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="220d0-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="220d0-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="220d0-601">バイト プール システムのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-602">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="220d0-603">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-603">Description</span></span>

<span data-ttu-id="220d0-604">このサービスを使用すると、システム内のすべてのメモリ バイト プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-605">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-606">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-606">Parameters</span></span>

- <span data-ttu-id="220d0-607">**allocates**: このプールで実行された割り当て要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="220d0-608">**releases**: このプールで実行された解放要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="220d0-609">**fragments_searched**: すべてのバイト プールで割り当て要求中に検索された内部メモリ フラグメントの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="220d0-610">**merges**: すべてのバイト プールで割り当て要求中に統合された内部メモリ ブロックの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="220d0-611">**splits**: すべてのバイト プールで割り当て要求中に作成された内部メモリ ブロックの分割 (フラグメント) の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="220d0-612">**suspensions**: すべてのバイト プールのスレッド割り当て保留の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="220d0-613">**timeouts**: すべてのバイト プールの割り当て保留タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-614">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-615">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-615">Return Values</span></span>

- <span data-ttu-id="220d0-616">**TX_SUCCESS**: (0x00) バイト プールのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="220d0-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-618">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-618">Allowed From</span></span>

<span data-ttu-id="220d0-619">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-620">例</span><span class="sxs-lookup"><span data-stu-id="220d0-620">Example</span></span>

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-621">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-621">See Also</span></span>

- <span data-ttu-id="220d0-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-622">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="220d0-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="220d0-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="220d0-630">バイト プールの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="220d0-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-631">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-632">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-632">Description</span></span>

<span data-ttu-id="220d0-633">このサービスを使用すると、このプール上のメモリで中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="220d0-634">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-635">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-635">Parameters</span></span> 

- <span data-ttu-id="220d0-636">**pool_ptr**: メモリ プールの制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-637">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-637">Return Values</span></span>

- <span data-ttu-id="220d0-638">**TX_SUCCESS**: (0x00) メモリ プールの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="220d0-639">TX_POOL_ERROR: (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-640">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-640">Allowed From</span></span>

<span data-ttu-id="220d0-641">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-642">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-642">Preemption Possible</span></span>

<span data-ttu-id="220d0-643">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-643">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-644">例</span><span class="sxs-lookup"><span data-stu-id="220d0-644">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-645">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-645">See Also</span></span>

- <span data-ttu-id="220d0-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-646">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="220d0-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="220d0-653">tx_byte_release</span></span>

<span data-ttu-id="220d0-654">メモリ プールへバイトを解放</span><span class="sxs-lookup"><span data-stu-id="220d0-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-655">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-656">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-656">Description</span></span>

<span data-ttu-id="220d0-657">このサービスを使用すると、以前に割り当てられたメモリ領域が、関連付けられているプールに解放されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="220d0-658">このプールからのメモリを待機しているスレッドが 1 つ以上ある場合、中断された各スレッドにはメモリが割り当てられ、メモリが使い果たされるか、中断されたスレッドがなくなるまで再開されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="220d0-659">中断されたスレッドにメモリを割り当てるこのプロセスは、常に中断された最初のスレッドから開始されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-660">アプリケーションでは、解放された後にメモリ領域が使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-661">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-661">Parameters</span></span>

- <span data-ttu-id="220d0-662">**memory_ptr**: 以前に割り当てられていたメモリ領域を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-663">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-663">Return Values</span></span>

- <span data-ttu-id="220d0-664">**TX_SUCCESS**: (0x00) メモリの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="220d0-665">TX_PTR_ERROR: (0x03) メモリ領域ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="220d0-666">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-667">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-667">Allowed From</span></span>

<span data-ttu-id="220d0-668">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-669">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-669">Preemption Possible</span></span>

<span data-ttu-id="220d0-670">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-671">例</span><span class="sxs-lookup"><span data-stu-id="220d0-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-672">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-672">See Also</span></span>

- <span data-ttu-id="220d0-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="220d0-673">tx_byte_allocate</span></span>
- <span data-ttu-id="220d0-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="220d0-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="220d0-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="220d0-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="220d0-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="220d0-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="220d0-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-680">tx_event_flags_create</span></span>

<span data-ttu-id="220d0-681">イベント フラグ グループの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-682">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-683">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-683">Description</span></span>

<span data-ttu-id="220d0-684">このサービスを使用すると、32 イベント フラグのグループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="220d0-685">グループ内の 32 イベント フラグすべてが 0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="220d0-686">各イベント フラグは、1 つのビットで表されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-687">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-687">Parameters</span></span>

- <span data-ttu-id="220d0-688">**group_ptr**: イベント フラグ グループ制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="220d0-689">**name_ptr**: イベント フラグ グループの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-690">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-690">Return Values</span></span>

- <span data-ttu-id="220d0-691">**TX_SUCCESS**: (0x00) イベント グループの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="220d0-692">TX_GROUP_ERROR: (0x06) イベント グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="220d0-693">ポインターが NULL であるか、イベント グループが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="220d0-694">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-695">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-695">Allowed From</span></span>

<span data-ttu-id="220d0-696">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-697">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-697">Preemption Possible</span></span>

<span data-ttu-id="220d0-698">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-698">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-699">例</span><span class="sxs-lookup"><span data-stu-id="220d0-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-700">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-700">See Also</span></span>

- <span data-ttu-id="220d0-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-702">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-706">tx_event_flags_set</span></span>
- <span data-ttu-id="220d0-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="220d0-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-708">tx_event_flags_delete</span></span>

<span data-ttu-id="220d0-709">イベント フラグ グループの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-710">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-711">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-711">Description</span></span>

<span data-ttu-id="220d0-712">このサービスを使用すると、指定したイベント フラグ グループが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="220d0-713">このグループからのイベントを待機しているすべての中断されたスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-714">アプリケーションでは、イベント フラグ グループを削除する前に、このイベント フラグ グループの通知コールバックの設定が完了している (または無効になっている) ことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="220d0-715">また、アプリケーションでは、すべての削除されたイベント フラグ グループが今後使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-716">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-716">Parameters</span></span> 

- <span data-ttu-id="220d0-717">**group_ptr**: 以前に作成されたイベント フラグ グループを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-718">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-718">Return Values</span></span>

- <span data-ttu-id="220d0-719">**TX_SUCCESS**: (0x00) イベント フラグ グループの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="220d0-720">TX_GROUP_ERROR: (0x06) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="220d0-721">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-722">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-722">Allowed From</span></span>

<span data-ttu-id="220d0-723">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-724">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-724">Preemption Possible</span></span>

<span data-ttu-id="220d0-725">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-726">例</span><span class="sxs-lookup"><span data-stu-id="220d0-726">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-727">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-727">See Also</span></span>

- <span data-ttu-id="220d0-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-728">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-729">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-733">tx_event_flags_set</span></span>
- <span data-ttu-id="220d0-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="220d0-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-735">tx_event_flags_get</span></span>

<span data-ttu-id="220d0-736">イベント フラグ グループからのイベント フラグの取得</span><span class="sxs-lookup"><span data-stu-id="220d0-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-737">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-738">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-738">Description</span></span>

<span data-ttu-id="220d0-739">このサービスを使用すると、指定したイベント フラグ グループからイベント フラグが取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="220d0-740">各イベント フラグ グループには 32 イベント フラグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="220d0-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="220d0-741">各フラグは、1 つのビットで表されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="220d0-742">このサービスを使用すると、入力パラメーターで選択されているように、さまざまなイベント フラグの組み合わせが取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-743">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-743">Parameters</span></span>

- <span data-ttu-id="220d0-744">**group_ptr**: 以前に作成されたイベント フラグ グループを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="220d0-745">**requested_flags**: 32 ビットの符号なし変数。要求されたイベント フラグを表します。</span><span class="sxs-lookup"><span data-stu-id="220d0-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="220d0-746">**get_option**: 要求されたイベント フラグのすべてが必要か、あるいはいずれかが必要かを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="220d0-747">有効なオプションは以下のとおりです:</span><span class="sxs-lookup"><span data-stu-id="220d0-747">The following are valid selections:</span></span>
    - <span data-ttu-id="220d0-748">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="220d0-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="220d0-749">**TX_AND_CLEAR**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="220d0-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="220d0-750">**TX_OR**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="220d0-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="220d0-751">**TX_OR_CLEAR**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="220d0-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="220d0-752">TX_AND または TX_AND_CLEAR を選択すると、すべてのイベント フラグがグループ内に存在しなければならないことが指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="220d0-753">TX_OR または TX_OR_CLEAR を選択すると、あらゆるイベント フラグが指定可能であることが指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="220d0-754">TX_AND_CLEAR または TX_OR_CLEAR が指定されている場合は、要求を満たすイベント フラグがクリアされます (0 に設定されます)。</span><span class="sxs-lookup"><span data-stu-id="220d0-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="220d0-755">**actual_flags_ptr**: 取得したイベント フラグが置かれる場所である宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="220d0-756">取得した実際のフラグには、要求されなかったフラグが含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="220d0-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="220d0-757">**wait_option**: 選択したイベント フラグが設定されていない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="220d0-758">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-759">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-761">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-762">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-763">これは、サービスが非スレッド (たとえば、初期化、タイマー、ISR など) から呼び出された場合にのみ有効なオプションです。</span><span class="sxs-lookup"><span data-stu-id="220d0-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="220d0-764">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、イベント フラグが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="220d0-765">数値 (1-0xFFFFFFFE) を選択すると、中断してイベント フラグを待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-766">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-766">Return Values</span></span>

- <span data-ttu-id="220d0-767">**TX_SUCCESS**: (0x00) イベント フラグの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="220d0-768">**TX_DELETED**: (0x01) スレッドが中断されている間にイベント フラグ グループが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-769">**TX_NO_EVENTS**: (0x07) 指定されたイベントを指定された待機時間内に取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="220d0-770">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-771">TX_GROUP_ERROR: (0x06) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="220d0-772">TX_PTR_ERROR: (0x03) 実際のイベント フラグのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="220d0-773">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="220d0-774">TX_OPTION_ERROR: (0x08) 無効な取得オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-775">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-775">Allowed From</span></span>

<span data-ttu-id="220d0-776">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-777">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-777">Preemption Possible</span></span>

<span data-ttu-id="220d0-778">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-779">例</span><span class="sxs-lookup"><span data-stu-id="220d0-779">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-780">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-780">See Also</span></span>

- <span data-ttu-id="220d0-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-781">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-786">tx_event_flags_set</span></span>
- <span data-ttu-id="220d0-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="220d0-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="220d0-789">イベント フラグ グループに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-790">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="220d0-791">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-791">Description</span></span>

<span data-ttu-id="220d0-792">このサービスを使用すると、指定したイベント フラグ グループに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-793">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-793">Parameters</span></span>

- <span data-ttu-id="220d0-794">**group_ptr**: イベント フラグ グループ制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="220d0-795">**name**: イベント フラグ グループの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="220d0-796">**current_flags**: イベント フラグ グループ内の現在の設定フラグの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="220d0-797">**first_suspended**: このイベント フラグ グループの中断リストの最初にあるスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="220d0-798">**suspended_count**: このイベント フラグ グループで現在中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="220d0-799">**next_group**: 次に作成されたイベント フラグ グループのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-800">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-801">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-801">Return Values</span></span>

- <span data-ttu-id="220d0-802">**TX_SUCCESS**: (0x00) イベント グループの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="220d0-803">TX_GROUP_ERROR: (0x06) イベント グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-804">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-804">Allowed From</span></span>

<span data-ttu-id="220d0-805">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-806">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-806">Preemption Possible</span></span>

<span data-ttu-id="220d0-807">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-807">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-808">例</span><span class="sxs-lookup"><span data-stu-id="220d0-808">Example</span></span>

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-809">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-809">See Also</span></span>

- <span data-ttu-id="220d0-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-810">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-812">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-815">tx_event_flags_set</span></span>
- <span data-ttu-id="220d0-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="220d0-817">tx_event_flags_performance info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="220d0-818">イベント フラグ グループのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-819">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-820">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-820">Description</span></span>

<span data-ttu-id="220d0-821">このサービスを使用すると、指定したイベント フラグ グループに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-822">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-823">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-823">Parameters</span></span>

- <span data-ttu-id="220d0-824">**group_ptr**: 以前に作成されたイベント フラグ グループを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="220d0-825">**sets**: このグループで実行されたイベント フラグ設定要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="220d0-826">**gets**: このグループで実行されたイベント フラグの取得要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="220d0-827">**suspensions**: このグループのスレッド イベント フラグ取得中断数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="220d0-828">**timeouts**: このグループのイベント フラグ取得中断タイムアウト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-829">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-830">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-830">Return Values</span></span>

- <span data-ttu-id="220d0-831">**TX_SUCCESS**: (0x00) イベント フラグ グループのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="220d0-832">**TX_PTR_ERROR**: (0x03) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="220d0-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-834">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-834">Allowed From</span></span>

<span data-ttu-id="220d0-835">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-836">例</span><span class="sxs-lookup"><span data-stu-id="220d0-836">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-837">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-837">See Also</span></span>

- <span data-ttu-id="220d0-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-838">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-840">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-843">tx_event_flags_set</span></span>
- <span data-ttu-id="220d0-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="220d0-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="220d0-846">パフォーマンス システム情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-847">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-848">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-848">Description</span></span>

<span data-ttu-id="220d0-849">このサービスを使用すると、システム内のすべてのイベント フラグ グループに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-850">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-851">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-851">Parameters</span></span>

- <span data-ttu-id="220d0-852">**sets**: すべてのグループで実行されたイベント フラグ設定要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="220d0-853">**gets**: すべてのグループで実行されたイベント フラグの取得要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="220d0-854">**suspensions**: すべてのグループのスレッド イベント フラグ取得中断の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="220d0-855">**timeouts**: すべてのグループのイベント フラグ取得中断タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-856">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-857">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-857">Return Values</span></span>

- <span data-ttu-id="220d0-858">**TX_SUCCESS**: (0x00) イベント フラグ システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="220d0-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-860">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-860">Allowed From</span></span>

<span data-ttu-id="220d0-861">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-862">例</span><span class="sxs-lookup"><span data-stu-id="220d0-862">Example</span></span>

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-863">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-863">See Also</span></span>

- <span data-ttu-id="220d0-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-864">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-866">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-869">tx_event_flags_set</span></span>
- <span data-ttu-id="220d0-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="220d0-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-871">tx_event_flags_set</span></span>

<span data-ttu-id="220d0-872">イベント フラグ グループでのイベント フラグの設定</span><span class="sxs-lookup"><span data-stu-id="220d0-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-873">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="220d0-874">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-874">Description</span></span>

<span data-ttu-id="220d0-875">このサービスを使用すると、指定したセット オプションに応じて、イベント フラグ グループ内のイベント フラグが設定またはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="220d0-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="220d0-876">イベント フラグ要求が満たされている、中断されたスレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-877">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-877">Parameters</span></span>

- <span data-ttu-id="220d0-878">**group_ptr**: 以前に作成されたイベント フラグ グループ制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="220d0-879">**flags_to_set**: 選択した設定オプションに基づいて設定またはクリアするイベント フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="220d0-880">**set_option**: 指定されたイベント フラグをグループの現在のイベント フラグへ AND 演算するか OR 演算するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="220d0-881">有効なオプションは以下のとおりです:</span><span class="sxs-lookup"><span data-stu-id="220d0-881">The following are valid selections:</span></span>
    - <span data-ttu-id="220d0-882">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="220d0-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="220d0-883">**TX_OR**: (0x00) TX_AND を選択すると、指定されたイベント フラグがグループの現在のイベント フラグへ **AND** 演算することが指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="220d0-884">このオプションは、グループ内のイベント フラグをクリアするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="220d0-885">あるいは、TX_OR が指定されている場合、指定されたイベント フラグは、グループ内の現在のイベントで **OR** 演算されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-886">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-886">Return Values</span></span>

- <span data-ttu-id="220d0-887">**TX_SUCCESS**: (0x00) イベント フラグの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="220d0-888">TX_GROUP_ERROR: (0x06) イベント フラグ グループを指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="220d0-889">TX_OPTION_ERROR: (0x08) 無効なセット オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-890">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-890">Allowed From</span></span>

<span data-ttu-id="220d0-891">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-892">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-892">Preemption Possible</span></span>

<span data-ttu-id="220d0-893">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-894">例</span><span class="sxs-lookup"><span data-stu-id="220d0-894">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-895">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-895">See Also</span></span>

- <span data-ttu-id="220d0-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-896">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-898">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="220d0-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="220d0-904">イベント フラグの設定時にアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="220d0-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-905">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="220d0-906">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-906">Description</span></span>

<span data-ttu-id="220d0-907">このサービスを使用すると、指定したイベント フラグ グループで 1 つ以上のイベント フラグが設定されるたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="220d0-908">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-909">アプリケーションのイベント フラグ設定通知コールバックによって、中断オプションによる ThreadX SMP API の呼び出しを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="220d0-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-910">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-910">Parameters</span></span> 
- <span data-ttu-id="220d0-911">**group_ptr**: 以前に作成されたイベント フラグ グループを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="220d0-912">**events_set_notify**: アプリケーションのイベント フラグ設定通知関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="220d0-913">この値が TX_NULL の場合、通知が無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-914">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-914">Return Values</span></span>

- <span data-ttu-id="220d0-915">**TX_SUCCESS**: (0x00) イベント フラグ設定通知の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="220d0-916">TX_GROUP_ERROR: (0x06) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="220d0-917">TX_FEATURE_NOT_ENABLED: (0xFF) システムは、通知機能を無効にしてコンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="220d0-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-918">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-918">Allowed From</span></span>

<span data-ttu-id="220d0-919">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-920">例</span><span class="sxs-lookup"><span data-stu-id="220d0-920">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a><span data-ttu-id="220d0-921">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-921">See Also</span></span>

- <span data-ttu-id="220d0-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="220d0-922">tx_event_flags_create</span></span>
- <span data-ttu-id="220d0-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="220d0-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="220d0-924">tx_event_flags_get</span></span>
- <span data-ttu-id="220d0-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="220d0-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="220d0-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="220d0-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="220d0-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="220d0-929">tx_interrupt_control</span></span>

<span data-ttu-id="220d0-930">割り込みの有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="220d0-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-931">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="220d0-932">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-932">Description</span></span>

<span data-ttu-id="220d0-933">このサービスを使用すると、入力パラメーター **new_posture** によって指定された割り込みが有効または無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-934">このサービスがアプリケーション スレッドから呼び出された場合、割り込みの状態はそのスレッドのコンテキストの一部として残ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="220d0-935">たとえば、スレッドによってこのルーチンが呼び出されて割り込みが無効になった後に中断された場合、再開されたときに割り込みが再び無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="220d0-936">このサービスを使用して、初期化中に割り込みを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="220d0-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="220d0-937">これを行うと、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-938">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-938">Parameters</span></span>

- <span data-ttu-id="220d0-939">**new_posture**: このパラメーターは、割り込みを無効にするか有効にするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="220d0-940">有効な値は、**TX_INT_DISABLE と TX_INT_ENABLE** です。</span><span class="sxs-lookup"><span data-stu-id="220d0-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="220d0-941">これらのパラメーターの実際の値はポートに固有です。</span><span class="sxs-lookup"><span data-stu-id="220d0-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="220d0-942">さらに、一部の処理アーキテクチャで追加の割り込み無効状態がサポートされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="220d0-943">詳細については、ディストリビューション ディスクで提供されている **_readme_threadx.txt_** の情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="220d0-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-944">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-944">Return Values</span></span>

- <span data-ttu-id="220d0-945">前の状態: このサービスから、前の割り込み状態が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="220d0-946">これにより、サービスのユーザーが、割り込みが無効になった後に前の状態を復元できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-947">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-947">Allowed From</span></span>

<span data-ttu-id="220d0-948">スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-949">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-949">Preemption Possible</span></span>

<span data-ttu-id="220d0-950">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-950">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-951">例</span><span class="sxs-lookup"><span data-stu-id="220d0-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="220d0-952">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-952">See Also</span></span>

<span data-ttu-id="220d0-953">None</span><span class="sxs-lookup"><span data-stu-id="220d0-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="220d0-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-954">tx_mutex_create</span></span>

<span data-ttu-id="220d0-955">相互排他ミューテックスの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-956">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="220d0-957">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-957">Description</span></span>
    
<span data-ttu-id="220d0-958">このサービスを使用すると、リソース保護のためにスレッド間の相互排他を行うミューテックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-959">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-959">Parameters</span></span>

- <span data-ttu-id="220d0-960">**mutex_ptr**: ミューテックス制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="220d0-961">**name_ptr**: ミューテックスの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="220d0-962">**priority_inherit**: このミューテックスで優先度の継承をサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="220d0-963">この値が TX_INHERIT の場合、優先度の継承がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="220d0-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="220d0-964">ただし、TX_NO_INHERIT が指定されている場合、優先度の継承はこのミューテックスではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="220d0-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-965">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-965">Return Values</span></span>

- <span data-ttu-id="220d0-966">**TX_SUCCESS**: (0x00) ミューテックスの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="220d0-967">TX_MUTEX_ERROR: (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="220d0-968">ポインターが NULL であるか、ミューテックスが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="220d0-969">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="220d0-970">TX_INHERIT_ERROR: (0x1F) 優先度継承パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-971">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-971">Allowed From</span></span>

<span data-ttu-id="220d0-972">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-973">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-973">Preemption Possible</span></span>

<span data-ttu-id="220d0-974">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-974">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-975">例</span><span class="sxs-lookup"><span data-stu-id="220d0-975">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-976">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-976">See Also</span></span>

- <span data-ttu-id="220d0-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-977">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-978">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="220d0-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="220d0-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-984">tx_mutex_delete</span></span>

<span data-ttu-id="220d0-985">相互排他ミューテックスの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-986">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-987">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-987">Description</span></span>

<span data-ttu-id="220d0-988">このサービスを使用すると、指定したミューテックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="220d0-989">ミューテックスを待機しているすべての中断されたスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-990">削除されたミューテックスを使用できないようにするのは、アプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="220d0-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-991">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-991">Parameters</span></span>

- <span data-ttu-id="220d0-992">**mutex_ptr**: 以前に作成されたミューテックスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-993">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-993">Return Values</span></span>

- <span data-ttu-id="220d0-994">**TX_SUCCESS**: (0x00) ミューテックスの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="220d0-995">TX_MUTEX_ERROR: (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="220d0-996">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-997">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-997">Allowed From</span></span>

<span data-ttu-id="220d0-998">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-999">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-999">Preemption Possible</span></span>

<span data-ttu-id="220d0-1000">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1001">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1002">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1002">See Also</span></span>

- <span data-ttu-id="220d0-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1003">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1004">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="220d0-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="220d0-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1010">tx_mutex_get</span></span>

<span data-ttu-id="220d0-1011">ミューテックスの所有権の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1012">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-1013">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1013">Description</span></span>

<span data-ttu-id="220d0-1014">このサービスを使用すると、指定したミューテックスの排他的所有権の取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="220d0-1015">呼び出し元のスレッドによって既にミューテックスが所有されている場合は、内部カウンターがインクリメントされ、正常な状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="220d0-1016">ミューテックスが別のスレッドによって所有されており、このスレッドの優先順位が高く、優先度の継承がミューテックス作成時に指定されている場合、優先度の低いスレッドの優先順位は一時的に呼び出し元スレッドの優先順位まで上昇します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1017">優先順位が継承されたミューテックスを所有する優先度の低いスレッドの優先順位は、ミューテックス所有権の間に外部スレッドによって変更されてはなりません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1018">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1018">Parameters</span></span>

- <span data-ttu-id="220d0-1019">**mutex_ptr**: 以前に作成されたミューテックスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="220d0-1020">**wait_option**: ミューテックスが既に別のスレッドによって所有されている場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="220d0-1021">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-1022">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-1024">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-1025">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-1026">*これは、サービスが初期化から呼び出された場合にのみ有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="220d0-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="220d0-1027">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、ミューテックスが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="220d0-1028">数値 (1-0xFFFFFFFE) を選択すると、中断してミューテックスを待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1029">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1029">Return Values</span></span>

- <span data-ttu-id="220d0-1030">**TX_SUCCESS**: (0x00) ミューテックスの取得操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="220d0-1031">**TX_DELETED**: (0x01) スレッドが中断されている間にミューテックスが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-1032">**TX_NOT_AVAILABLE**: (0x1D) 指定された待機時間内にミューテックスの所有権を取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="220d0-1033">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-1034">TX_MUTEX_ERROR: (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="220d0-1035">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="220d0-1036">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1037">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1037">Allowed From</span></span>

<span data-ttu-id="220d0-1038">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1039">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1039">Preemption Possible</span></span>

<span data-ttu-id="220d0-1040">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1041">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="220d0-1042">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1042">See Also</span></span>

- <span data-ttu-id="220d0-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1043">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="220d0-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="220d0-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="220d0-1051">ミューテックスに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1052">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="220d0-1053">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1053">Description</span></span>

<span data-ttu-id="220d0-1054">このサービスを使用すると、指定したミューテックスから情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1055">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1055">Parameters</span></span>

- <span data-ttu-id="220d0-1056">**mutex_ptr**: ミューテックス制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="220d0-1057">**name**: ミューテックスの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="220d0-1058">**count**: ミューテックスの所有権カウントの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="220d0-1059">**owner**: 所有スレッドのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="220d0-1060">**first_suspended**: このミューテックスの中断リストの最初にあるスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="220d0-1061">**suspended_count**: このミューテックスで現在中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="220d0-1062">**next_mutex**: 次に作成されるミューテックスのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1063">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1064">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1064">Return Values</span></span>

- <span data-ttu-id="220d0-1065">**TX_SUCCESS**: (0x00) ミューテックスの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="220d0-1066">TX_MUTEX_ERROR: (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1067">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1067">Allowed From</span></span>

<span data-ttu-id="220d0-1068">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1069">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1069">Preemption Possible</span></span>

<span data-ttu-id="220d0-1070">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1071">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1071">Example</span></span>

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1072">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1072">See Also</span></span>

- <span data-ttu-id="220d0-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1073">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1075">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="220d0-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="220d0-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="220d0-1081">ミューテックスのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1082">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="220d0-1083">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1083">Description</span></span>

<span data-ttu-id="220d0-1084">このサービスを使用すると、指定したミューテックスに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1085">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_MUTEX_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1086">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1086">Parameters</span></span>

- <span data-ttu-id="220d0-1087">**mutex_ptr**: 以前に作成されたミューテックスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="220d0-1088">**puts**: このミューテックスで実行された配置要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="220d0-1089">**gets**: このミューテックスで実行された取得要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="220d0-1090">**suspensions**: このミューテックスのスレッド ミューテックス取得中断数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="220d0-1091">**timeouts**: このミューテックスのミューテックス取得中断タイムアウト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="220d0-1092">**inversions**: このミューテックスのスレッド優先度逆転数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="220d0-1093">**inheritances**: このミューテックスのスレッド優先度の継承操作の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1094">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1095">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1095">Return Values</span></span>

- <span data-ttu-id="220d0-1096">**TX_SUCCESS**: (0x00) ミューテックスのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="220d0-1097">**TX_PTR_ERROR**: (0x03) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="220d0-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1099">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1099">Allowed From</span></span>

<span data-ttu-id="220d0-1100">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1101">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1101">Example</span></span>

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1102">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1102">See Also</span></span>

- <span data-ttu-id="220d0-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1103">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1105">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="220d0-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="220d0-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="220d0-1111">ミューテックスのシステム パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1112">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="220d0-1113">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1113">Description</span></span>

<span data-ttu-id="220d0-1114">このサービスを使用すると、システム内のすべてのミューテックスに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1115">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_MUTEX_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1116">Parameters</span></span>

- <span data-ttu-id="220d0-1117">**puts**: すべてのミューテックスで実行された配置要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="220d0-1118">**gets**: すべてのミューテックスで実行された取得要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="220d0-1119">**suspensions**: すべてのミューテックスのスレッド ミューテックス取得中断の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="220d0-1120">**timeouts**: すべてのミューテックスのミューテックス取得中断タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="220d0-1121">**inversions**: すべてのミューテックスのスレッド優先度逆転の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="220d0-1122">**inheritances**: すべてのミューテックスのスレッド優先度の継承操作の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1123">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1124">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1124">Return Values</span></span>

- <span data-ttu-id="220d0-1125">**TX_SUCCESS**: (0x00) ミューテックス システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="220d0-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1127">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1127">Allowed From</span></span>

<span data-ttu-id="220d0-1128">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1129">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1129">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1130">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1130">See Also</span></span>

- <span data-ttu-id="220d0-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1131">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1133">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="220d0-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="220d0-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="220d0-1139">ミューテックスの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="220d0-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1140">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1141">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1141">Description</span></span>

<span data-ttu-id="220d0-1142">このサービスを使用すると、このミューテックスの所有権をめぐって中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="220d0-1143">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1144">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1144">Parameters</span></span> 

- <span data-ttu-id="220d0-1145">**mutex_ptr**: 以前に作成されたミューテックスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1146">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1146">Return Values</span></span>

- <span data-ttu-id="220d0-1147">**TX_SUCCESS**: (0x00) ミューテックスの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="220d0-1148">TX_MUTEX_ERROR: (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1149">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1149">Allowed From</span></span>

<span data-ttu-id="220d0-1150">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1151">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1151">Preemption Possible</span></span>

<span data-ttu-id="220d0-1152">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1153">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1153">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1154">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1154">See Also</span></span>

- <span data-ttu-id="220d0-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1155">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1157">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="220d0-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1162">tx_mutex_put</span></span>

<span data-ttu-id="220d0-1163">ミューテックスの所有権の解放</span><span class="sxs-lookup"><span data-stu-id="220d0-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1164">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1165">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1165">Description</span></span>

<span data-ttu-id="220d0-1166">このサービスを使用すると、指定したミューテックスの所有権カウントが減ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="220d0-1167">所有権カウントがゼロの場合は、ミューテックスが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1168">ミューテックスの作成時に優先度の継承が選択された場合、解放するスレッドの優先度は、最初にミューテックスの所有権を取得したときの優先度に復元されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="220d0-1169">解放するスレッドがミューテックスを所有している間に行われた他の優先順位の変更は元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1170">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1170">Parameters</span></span>

- <span data-ttu-id="220d0-1171">**mutex_ptr**: 以前に作成されたミューテックスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1172">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1172">Return Values</span></span>

- <span data-ttu-id="220d0-1173">**TX_SUCCESS**: (0x00) ミューテックスの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="220d0-1174">**TX_NOT_OWNED**: (0x1E) ミューテックスは、呼び出し元によって所有されていません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="220d0-1175">TX_MUTEX_ERROR: (0x1C) ミューテックスを指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="220d0-1176">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1177">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1177">Allowed From</span></span>

<span data-ttu-id="220d0-1178">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1179">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1179">Preemption Possible</span></span>

<span data-ttu-id="220d0-1180">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1181">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1182">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1182">See Also</span></span>

- <span data-ttu-id="220d0-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1183">tx_mutex_create</span></span>
- <span data-ttu-id="220d0-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="220d0-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1185">tx_mutex_get</span></span>
- <span data-ttu-id="220d0-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="220d0-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="220d0-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="220d0-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1190">tx_queue_create</span></span>

<span data-ttu-id="220d0-1191">メッセージ キューの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="220d0-1193">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1193">Description</span></span>

<span data-ttu-id="220d0-1194">このサービスを使用すると、主にスレッド間通信に使用される、メッセージ キューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="220d0-1195">メッセージの合計数は、指定したメッセージ サイズと、キュー内の合計バイト数から計算されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1196">キューのメモリ領域で指定された合計バイト数が、指定したメッセージ サイズで均等に割り切れない場合、メモリ領域の残りのバイトは使用されません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1197">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1197">Parameters</span></span>

- <span data-ttu-id="220d0-1198">**queue_ptr**: メッセージ キュー コントロール ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="220d0-1199">**name_ptr**: メッセージ キューの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="220d0-1200">**message_size**: キュー内の各メッセージのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="220d0-1201">メッセージのサイズは、32 ビットの 1 ワードから 32 ビットの 16 ワードまでの範囲です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="220d0-1202">有効なメッセージ サイズのオプションは、1 から 16 の数値です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="220d0-1203">**queue_start**: メッセージ キューの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="220d0-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="220d0-1204">開始アドレスは、ULONG データ型のサイズに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="220d0-1205">**queue_size**: メッセージ キューで使用可能な合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="220d0-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1206">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1206">Return Values</span></span>

- <span data-ttu-id="220d0-1207">**TX_SUCCESS**: (0x00) メッセージ キューの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="220d0-1208">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="220d0-1209">ポインターが NULL であるか、キューが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="220d0-1210">TX_PTR_ERROR: (0x03) メッセージ キューの開始アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="220d0-1211">TX_SIZE_ERROR: (0x05) メッセージ キューのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="220d0-1212">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1213">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1213">Allowed From</span></span>

<span data-ttu-id="220d0-1214">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1215">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1215">Preemption Possible</span></span>

<span data-ttu-id="220d0-1216">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1217">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1217">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1218">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1218">See Also</span></span>

- <span data-ttu-id="220d0-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1219">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1220">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1226">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1227">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="220d0-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1229">tx_queue_delete</span></span>

<span data-ttu-id="220d0-1230">メッセージ キューの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1231">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1232">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1232">Description</span></span>

<span data-ttu-id="220d0-1233">このサービスを使用すると、指定したメッセージ キューが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="220d0-1234">このキューからのメッセージを待機しているすべての中断されたスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1235">アプリケーションでは、キューを削除する前に、このキューに対する送信通知コールバックが完了している (または無効になっている) ことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="220d0-1236">また、アプリケーションでは、削除されたキューが今後使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="220d0-1237">*キューに関連付けられているメモリ領域を管理するのもアプリケーションの役割です。これは、サービスの完了後に利用できます。*</span><span class="sxs-lookup"><span data-stu-id="220d0-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1238">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1238">Parameters</span></span> 

- <span data-ttu-id="220d0-1239">**queue_ptr**: 以前に作成されたメッセージ キューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1240">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1240">Return Values</span></span>

- <span data-ttu-id="220d0-1241">**TX_SUCCESS**: (0x00) メッセージ キューの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="220d0-1242">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="220d0-1243">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1244">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1244">Allowed From</span></span>

<span data-ttu-id="220d0-1245">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1246">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1246">Preemption Possible</span></span>

<span data-ttu-id="220d0-1247">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1248">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1248">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1249">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1249">See Also</span></span>

- <span data-ttu-id="220d0-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1250">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1251">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1257">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1258">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="220d0-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1260">tx_queue_flush</span></span>

<span data-ttu-id="220d0-1261">メッセージ キューのメッセージを空にする</span><span class="sxs-lookup"><span data-stu-id="220d0-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1262">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1263">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1263">Description</span></span>

<span data-ttu-id="220d0-1264">このサービスを使用すると、指定したメッセージ キューに格納されているすべてのメッセージが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="220d0-1265">キューがいっぱいの場合、中断されたすべてのスレッドのメッセージが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="220d0-1266">中断された各スレッドが、メッセージ送信が成功したことを示す戻りステータスで再開されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="220d0-1267">キューが空の場合、このサービスは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1268">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1268">Parameters</span></span> 

- <span data-ttu-id="220d0-1269">**queue_ptr**: 以前に作成されたメッセージ キューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1270">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1270">Return Values</span></span>

- <span data-ttu-id="220d0-1271">**TX_SUCCESS**: (0x00) メッセージ キューのフラッシュに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="220d0-1272">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1273">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1273">Allowed From</span></span>

<span data-ttu-id="220d0-1274">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1275">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1275">Preemption Possible</span></span>

<span data-ttu-id="220d0-1276">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1277">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1277">Example</span></span>

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1278">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1278">See Also</span></span>

- <span data-ttu-id="220d0-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1279">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1280">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1286">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1287">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="220d0-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1289">tx_queue_front_send</span></span>

<span data-ttu-id="220d0-1290">メッセージをキューの先頭に送る</span><span class="sxs-lookup"><span data-stu-id="220d0-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1291">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-1292">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1292">Description</span></span>

<span data-ttu-id="220d0-1293">このサービスを使用すると、指定したメッセージ キューの前の場所にメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="220d0-1294">メッセージは、ソース ポインターによって指定されたメモリ領域からキューの先頭に **コピー** されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1295">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1295">Parameters</span></span>

- <span data-ttu-id="220d0-1296">**queue_ptr**: メッセージ キュー コントロール ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="220d0-1297">**source_ptr**: メッセージを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="220d0-1298">**wait_option**: メッセージ キューがいっぱいになった場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="220d0-1299">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-1300">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-1302">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-1303">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-1304">*これは、サービスが非スレッド (たとえば、初期化、タイマー、ISR など) から呼び出された場合にのみ有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="220d0-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="220d0-1305">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、キューに空きができるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="220d0-1306">数値 (1-0xFFFFFFFE) を選択すると、中断してキューに空きができるまで待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1307">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1307">Return Values</span></span>

- <span data-ttu-id="220d0-1308">**TX_SUCCESS**: (0x00) メッセージの送信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="220d0-1309">**TX_DELETED**: (0x01) スレッドが中断されている間にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-1310">**TX_QUEUE_FULL**: (0x0B) 指定された待機時間の間キューがいっぱいだったため、メッセージを送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="220d0-1311">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-1312">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="220d0-1313">TX_PTR_ERROR: (0x03) メッセージのソース ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="220d0-1314">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1315">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1315">Allowed From</span></span>

<span data-ttu-id="220d0-1316">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1317">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1317">Preemption Possible</span></span>

<span data-ttu-id="220d0-1318">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1319">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1319">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1320">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1320">See Also</span></span>

- <span data-ttu-id="220d0-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1321">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1322">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1323">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1328">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1329">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="220d0-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1331">tx_queue_info_get</span></span>

<span data-ttu-id="220d0-1332">キューに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1333">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="220d0-1334">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1334">Description</span></span>

<span data-ttu-id="220d0-1335">このサービスを使用すると、指定したメッセージ キューに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1336">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1336">Parameters</span></span>

- <span data-ttu-id="220d0-1337">**queue_ptr**: 以前に作成されたメッセージ キューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="220d0-1338">**name**: キューの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="220d0-1339">**enqueued**: 現在キューに入っているメッセージの数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="220d0-1340">**available_storage**: キューに現在余裕があるメッセージ数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="220d0-1341">**first_suspended**: このキューの中断リストの最初にあるスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="220d0-1342">**suspended_count**: このキューで現在中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="220d0-1343">**next_queue**: 次に作成されたキューのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1344">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1345">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1345">Return Values</span></span>

- <span data-ttu-id="220d0-1346">**TX_SUCCESS**: (0x00) キューの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="220d0-1347">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1348">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1348">Allowed From</span></span>

<span data-ttu-id="220d0-1349">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1350">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1350">Preemption Possible</span></span>

<span data-ttu-id="220d0-1351">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1352">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1352">Example</span></span>

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1353">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1353">See Also</span></span>

- <span data-ttu-id="220d0-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1354">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1355">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1356">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1361">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1362">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="220d0-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="220d0-1365">キューに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1366">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-1367">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1367">Description</span></span>

<span data-ttu-id="220d0-1368">このサービスを使用すると、指定したキューに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1369">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_QUEUE_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1370">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1370">Parameters</span></span>

- <span data-ttu-id="220d0-1371">**queue_ptr**: 以前に作成されたキューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="220d0-1372">**messages_sent**: このキューで実行された送信要求の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="220d0-1373">**messages_received**: このキューで実行された受信要求の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="220d0-1374">**empty_suspensions**: このキューでキューが空になった中断数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="220d0-1375">**empty_suspensions**: このキューでキューが満杯になった中断数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="220d0-1376">**full_errors**: このキューでキューが満杯になったエラー数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="220d0-1377">**timeouts**: このキューのスレッド中断タイムアウトの数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1378">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1379">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1379">Return Values</span></span>

- <span data-ttu-id="220d0-1380">**TX_SUCCESS**: (0x00) キューのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="220d0-1381">**TX_PTR_ERROR**: (0x03) キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="220d0-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1383">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1383">Allowed From</span></span>

<span data-ttu-id="220d0-1384">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1385">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1385">Example</span></span>

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1386">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1386">See Also</span></span>

- <span data-ttu-id="220d0-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1387">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1388">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1389">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1394">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1395">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="220d0-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="220d0-1398">キュー システムに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1399">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-1400">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1400">Description</span></span>

<span data-ttu-id="220d0-1401">このサービスを使用すると、システム内のすべてのキューに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1402">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_QUEUE_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1403">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1403">Parameters</span></span>

- <span data-ttu-id="220d0-1404">**messages_sent**: すべてのキューで実行された送信要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="220d0-1405">**messages_received**: すべてのキューで実行された受信要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="220d0-1406">**empty_suspensions**: すべてのキューでキューが空になった中断の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="220d0-1407">**full_suspensions**: すべてのキューでキューが満杯になった中断の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="220d0-1408">**full_errors**: すべてのキューでキューが満杯になったエラーの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="220d0-1409">**timeouts**: すべてのキューのスレッド中断タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1410">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1411">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1411">Return Values</span></span>

- <span data-ttu-id="220d0-1412">**TX_SUCCESS**: (0x00) キュー システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="220d0-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1414">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1414">Allowed From</span></span>

<span data-ttu-id="220d0-1415">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1416">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1416">Example</span></span>

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1417">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1417">See Also</span></span>

- <span data-ttu-id="220d0-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1418">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1419">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1420">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1425">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1426">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="220d0-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="220d0-1429">キューの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="220d0-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1430">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="220d0-1431">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1431">Description</span></span>

<span data-ttu-id="220d0-1432">このサービスを使用すると、このキューにメッセージを入れるために (またはメッセージを配置するために) 中断された最優先のスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="220d0-1433">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1434">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1434">Parameters</span></span> 

- <span data-ttu-id="220d0-1435">**queue_ptr**: 以前に作成されたメッセージ キューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1436">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1436">Return Values</span></span>

- <span data-ttu-id="220d0-1437">**TX_SUCCESS**: (0x00) キューの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="220d0-1438">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1439">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1439">Allowed From</span></span>

<span data-ttu-id="220d0-1440">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1441">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1441">Preemption Possible</span></span>

<span data-ttu-id="220d0-1442">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1443">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1443">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1444">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1444">See Also</span></span>

- <span data-ttu-id="220d0-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1445">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1446">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1447">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1452">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1453">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="220d0-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1455">tx_queue_receive</span></span>

<span data-ttu-id="220d0-1456">メッセージ キューからのメッセージの取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1457">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-1458">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1458">Description</span></span>

<span data-ttu-id="220d0-1459">このサービスを使用すると、指定したメッセージ キューからメッセージが取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="220d0-1460">取得されたメッセージは、キューから、宛先ポインターによって指定されたメモリ領域に **コピー** されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="220d0-1461">そのメッセージは、その後キューから削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="220d0-1462">指定された宛先メモリ領域は、メッセージを保持できるだけの大きさでなければなりません。つまり、**destination_ptr** によってポイントされるメッセージの送信先は、少なくともこのキューのメッセージ サイズと同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="220d0-1463">それ以外の場合、宛先の容量が十分でないと、メモリ破損が次のメモリ領域で発生します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1464">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1464">Parameters</span></span>

- <span data-ttu-id="220d0-1465">**queue_ptr**: 以前に作成されたメッセージ キューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="220d0-1466">**destination_ptr**: メッセージのコピー先の場所。</span><span class="sxs-lookup"><span data-stu-id="220d0-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="220d0-1467">**wait_option**: メッセージ キューが空になった場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="220d0-1468">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-1469">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="220d0-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="220d0-1471">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-1472">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-1473">これは、サービスが非スレッド (たとえば、初期化、タイマー、ISR など) から呼び出された場合にのみ有効なオプションです。</span><span class="sxs-lookup"><span data-stu-id="220d0-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="220d0-1474">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、メッセージが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="220d0-1475">数値 (1-0xFFFFFFFE) を選択すると、中断してメッセージを待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1476">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1476">Return Values</span></span>

- <span data-ttu-id="220d0-1477">**TX_SUCCESS**: (0x00) メッセージの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="220d0-1478">**TX_DELETED**: (0x01) スレッドが中断されている間にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-1479">**TX_QUEUE_EMPTY**: (0x0A) 指定された待機時間の間キューが空だったため、メッセージを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="220d0-1480">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-1481">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="220d0-1482">TX_PTR_ERROR (0x03): メッセージの宛先ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="220d0-1483">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1484">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1484">Allowed From</span></span>

<span data-ttu-id="220d0-1485">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1486">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1486">Preemption Possible</span></span>

<span data-ttu-id="220d0-1487">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1488">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1488">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1489">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1489">See Also</span></span>

- <span data-ttu-id="220d0-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1490">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1491">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1492">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1498">tx_queue_send</span></span>
- <span data-ttu-id="220d0-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="220d0-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1500">tx_queue_send</span></span>

<span data-ttu-id="220d0-1501">メッセージ キューへのメッセージの送信</span><span class="sxs-lookup"><span data-stu-id="220d0-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1502">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="220d0-1503">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1503">Description</span></span>

<span data-ttu-id="220d0-1504">このサービスを使用すると、指定したメッセージ キューにメッセージが送られます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="220d0-1505">送信されたメッセージは、ソース ポインターによって指定されたメモリ領域からキューに **コピー** されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1506">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1506">Parameters</span></span>

- <span data-ttu-id="220d0-1507">**queue_ptr**: 以前に作成されたメッセージ キューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="220d0-1508">**source_ptr**: メッセージを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="220d0-1509">**wait_option**: メッセージ キューがいっぱいになった場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="220d0-1510">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-1511">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-1513">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-1514">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-1515">*これは、サービスが非スレッド (たとえば、初期化、タイマー、ISR など) から呼び出された場合にのみ有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="220d0-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="220d0-1516">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、キューに空きができるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="220d0-1517">数値 (1-0xFFFFFFFE) を選択すると、中断してキューに空きができるまで待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1518">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1518">Return Values</span></span>

- <span data-ttu-id="220d0-1519">**TX_SUCCESS**: (0x00) メッセージの送信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="220d0-1520">**TX_DELETED**: (0x01) スレッドが中断されている間にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-1521">**TX_QUEUE_FULL**: (0x0B) 指定された待機時間の間キューがいっぱいだったため、メッセージを送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="220d0-1522">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-1523">TX_QUEUE_ERROR: (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="220d0-1524">TX_PTR_ERROR: (0x03) メッセージのソース ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="220d0-1525">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1526">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1526">Allowed From</span></span>

<span data-ttu-id="220d0-1527">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1528">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1528">Preemption Possible</span></span>

<span data-ttu-id="220d0-1529">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1530">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1530">Example</span></span>

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1531">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1531">See Also</span></span>

- <span data-ttu-id="220d0-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1532">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1533">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1534">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1540">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="220d0-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="220d0-1543">メッセージをキューに送信するときにアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="220d0-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1544">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="220d0-1545">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1545">Description</span></span>

<span data-ttu-id="220d0-1546">このサービスを使用すると、指定されたキューにメッセージが送信されるたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="220d0-1547">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-1548">アプリケーションのキュー送信通知コールバックによって、中断オプションによる ThreadX SMP API の呼び出しを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1549">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1549">Parameters</span></span> 

- <span data-ttu-id="220d0-1550">**queue_ptr**: 以前に作成されたキューを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="220d0-1551">**queue_send_notify**: アプリケーションのキュー送信通知関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="220d0-1552">この値が TX_NULL の場合、通知が無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1553">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1553">Return Values</span></span>

- <span data-ttu-id="220d0-1554">**TX_SUCCESS**: (0x00) キューの送信通知の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="220d0-1555">TX_QUEUE_ERROR: (0x09) キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="220d0-1556">TX_FEATURE_NOT_ENABLED: (0xFF) システムは、通知機能を無効にしてコンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1557">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1557">Allowed From</span></span>

<span data-ttu-id="220d0-1558">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1559">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1559">Example</span></span>

```C
TX_QUEUE         my_queue;

/* Register the "my_queue_send_notify" function for monitoring
   messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
   successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
/* A message was just sent to this queue! */
}
```
### <a name="see-also"></a><span data-ttu-id="220d0-1560">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1560">See Also</span></span>

- <span data-ttu-id="220d0-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1561">tx_queue_create</span></span>
- <span data-ttu-id="220d0-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1562">tx_queue_delete</span></span>
- <span data-ttu-id="220d0-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="220d0-1563">tx_queue_flush</span></span>
- <span data-ttu-id="220d0-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="220d0-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="220d0-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="220d0-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="220d0-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="220d0-1569">tx_queue_receive</span></span>
- <span data-ttu-id="220d0-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="220d0-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="220d0-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="220d0-1572">上限が設定されたカウント セマフォへのインスタンスの配置</span><span class="sxs-lookup"><span data-stu-id="220d0-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1573">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="220d0-1574">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1574">Description</span></span>

<span data-ttu-id="220d0-1575">このサービスを使用すると、指定されたカウント セマフォにインスタンスが 1 つ入れられます。つまり、カウント セマフォが 1 つインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="220d0-1576">カウント セマフォの現在の値が指定された上限以上の場合、インスタンスは配置されず、TX_CEILING_EXCEEDED エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1577">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1577">Parameters</span></span> 

- <span data-ttu-id="220d0-1578">**semaphore_ptr**: 以前に作成されたセマフォを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="220d0-1579">**ceiling**: セマフォで許可される最大限度 (有効な値の範囲は 1 から 0xFFFFFFFF)。</span><span class="sxs-lookup"><span data-stu-id="220d0-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1580">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1580">Return Values</span></span>

- <span data-ttu-id="220d0-1581">**TX_SUCCESS**: (0x00) セマフォの上限の配置に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="220d0-1582">**TX_CEILING_EXCEEDED**: (0x21) 配置要求が上限を超えています。</span><span class="sxs-lookup"><span data-stu-id="220d0-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="220d0-1583">TX_INVALID_CEILING: (0x22) 上限に無効な値である 0 が指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="220d0-1584">TX_SEMAPHORE_ERROR: (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1585">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1585">Allowed From</span></span>

<span data-ttu-id="220d0-1586">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1587">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="220d0-1588">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1588">See Also</span></span>

- <span data-ttu-id="220d0-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="220d0-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1598">tx_semaphore_create</span></span>

<span data-ttu-id="220d0-1599">カウント セマフォの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1600">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="220d0-1601">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1601">Description</span></span>

<span data-ttu-id="220d0-1602">このサービスを使用すると、スレッド間同期のカウント セマフォが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="220d0-1603">初期のセマフォ数は、入力パラメーターとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1604">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1604">Parameters</span></span> 

- <span data-ttu-id="220d0-1605">**semaphore_ptr**: セマフォ制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="220d0-1606">**name_ptr**: セマフォの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="220d0-1607">**initial_count**: このセマフォの最初の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="220d0-1608">有効な値の範囲は 0x00000000 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1609">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1609">Return Values</span></span>

- <span data-ttu-id="220d0-1610">**TX_SUCCESS**: (0x00) セマフォの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="220d0-1611">TX_SEMAPHORE_ERROR: (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="220d0-1612">ポインターが NULL であるか、セマフォが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="220d0-1613">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1614">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1614">Allowed From</span></span>

<span data-ttu-id="220d0-1615">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1616">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1616">Preemption Possible</span></span>

<span data-ttu-id="220d0-1617">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1618">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1618">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1619">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1619">See Also</span></span>

- <span data-ttu-id="220d0-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="220d0-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="220d0-1630">カウント セマフォの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1631">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1632">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1632">Description</span></span>

<span data-ttu-id="220d0-1633">このサービスを使用すると、指定されたカウント セマフォが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="220d0-1634">中断されセマフォ インスタンスを待機しているすべての中断されたスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1635">アプリケーションでは、セマフォを削除する前に、このセマフォに対する配置通知コールバックが完了している (または無効になっている) ことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="220d0-1636">また、アプリケーションでは、削除されたセマフォが今後使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1637">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1637">Parameters</span></span> 

- <span data-ttu-id="220d0-1638">**semaphore_ptr**: 以前に作成されたセマフォを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1639">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1639">Return Values</span></span>

- <span data-ttu-id="220d0-1640">**TX_SUCCESS**: (0x00) カウント セマフォの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="220d0-1641">TX_SEMAPHORE_ERROR: (0x0C) カウント セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="220d0-1642">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1643">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1643">Allowed From</span></span>

<span data-ttu-id="220d0-1644">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1645">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1645">Preemption Possible</span></span>

<span data-ttu-id="220d0-1646">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1647">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1648">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1648">See Also</span></span>

- <span data-ttu-id="220d0-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="220d0-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1658">tx_semaphore_get</span></span>

<span data-ttu-id="220d0-1659">カウント セマフォからのインスタンスの取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1660">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="220d0-1661">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1661">Description</span></span>

<span data-ttu-id="220d0-1662">このサービスを使用すると、指定されたカウント セマフォからインスタンスが (ひとつだけ) 取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="220d0-1663">その結果、指定されたセマフォの数が 1 つ減少します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1664">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1664">Parameters</span></span>

- <span data-ttu-id="220d0-1665">**semaphore_ptr**: 以前に作成されたカウント セマフォを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="220d0-1666">**wait_option**: 使用可能なセマフォのインスタンスがない場合、つまり、セマフォ数が 0 の場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="220d0-1667">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="220d0-1668">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="220d0-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="220d0-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="220d0-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="220d0-1670">タイムアウト値: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="220d0-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="220d0-1671">TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="220d0-1672">*これは、サービスが非スレッド (たとえば、初期化、タイマー、ISR など) から呼び出された場合にのみ有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="220d0-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="220d0-1673">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、セマフォ インスタンスが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="220d0-1674">数値 (1-0xFFFFFFFE) を選択すると、中断してセマフォ インスタンスを待機し続ける時間 (タイマーティックの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1675">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1675">Return Values</span></span>

- <span data-ttu-id="220d0-1676">**TX_SUCCESS**: (0x00) セマフォ インスタンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="220d0-1677">**TX_DELETED**: (0x01) スレッドが中断されている間にカウント セマフォが削除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="220d0-1678">**TX_NO_INSTANCE**: (0x0D) カウント セマフォのインスタンスを取得できませんでした (指定された待機時間内のセマフォ数は 0 です)。</span><span class="sxs-lookup"><span data-stu-id="220d0-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="220d0-1679">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-1680">TX_SEMAPHORE_ERROR: (0x0C) カウント セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="220d0-1681">TX_WAIT_ERROR: (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1682">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1682">Allowed From</span></span>

<span data-ttu-id="220d0-1683">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1684">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1684">Preemption Possible</span></span>

<span data-ttu-id="220d0-1685">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1686">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1686">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1687">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1687">See Also</span></span>

- <span data-ttu-id="220d0-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="220d0-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="220d0-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="220d0-1697">セマフォに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1698">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="220d0-1699">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1699">Description</span></span>

<span data-ttu-id="220d0-1700">このサービスを使用すると、指定したセマフォに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1701">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1701">Parameters</span></span>

- <span data-ttu-id="220d0-1702">**semaphore_ptr**: セマフォ制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="220d0-1703">**name**: セマフォの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="220d0-1704">**current_value**: 現在のセマフォ数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="220d0-1705">**first_suspended**: このセマフォの中断リストの最初にあるスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="220d0-1706">**suspended_count**: このセマフォで現在中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="220d0-1707">**next_semaphore**: 次に作成されたセマフォのポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1708">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1709">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1709">Return Values</span></span>

- <span data-ttu-id="220d0-1710">**TX_SUCCESS**: (0x00) セマフォの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="220d0-1711">TX_SEMAPHORE_ERROR: (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1712">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1712">Allowed From</span></span>

<span data-ttu-id="220d0-1713">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1714">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1714">Preemption Possible</span></span>

<span data-ttu-id="220d0-1715">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1716">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1716">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1717">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1717">See Also</span></span>

- <span data-ttu-id="220d0-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="220d0-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="220d0-1728">セマフォに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1729">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-1730">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1730">Description</span></span>

<span data-ttu-id="220d0-1731">このサービスを使用すると、指定したセマフォに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-1732">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1733">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1733">Parameters</span></span>

- <span data-ttu-id="220d0-1734">**semaphore_ptr**: 以前に作成されたセマフォを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="220d0-1735">**puts**: このセマフォで実行された配置要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="220d0-1736">**gets**: このセマフォで実行された取得要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="220d0-1737">**suspensions**: このセマフォで中断されているスレッド数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="220d0-1738">**timeouts**: このセマフォのスレッド中断タイムアウトの数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1739">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1740">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1740">Return Values</span></span>

- <span data-ttu-id="220d0-1741">**TX_SUCCESS**: (0x00) セマフォのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="220d0-1742">**TX_PTR_ERROR**: (0x03) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="220d0-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1744">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1744">Allowed From</span></span>

<span data-ttu-id="220d0-1745">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1746">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1746">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1747">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1747">See Also</span></span>

- <span data-ttu-id="220d0-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="220d0-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="220d0-1758">セマフォ システムに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1759">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="220d0-1760">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1760">Description</span></span>

<span data-ttu-id="220d0-1761">このサービスを使用すると、システム内のすべてのセマフォに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1762">ThreadX SMP ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1763">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1763">Parameters</span></span>

- <span data-ttu-id="220d0-1764">**puts**: すべてのセマフォで実行された配置要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="220d0-1765">**gets**: すべてのセマフォで実行された取得要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="220d0-1766">**suspensions**: すべてのセマフォのスレッド中断の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="220d0-1767">**suspensions**: すべてのセマフォのスレッド中断タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1768">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1769">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1769">Return Values</span></span>

- <span data-ttu-id="220d0-1770">TX_SUCCESS: (0x00) セマフォ システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="220d0-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1772">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1772">Allowed From</span></span>

<span data-ttu-id="220d0-1773">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1774">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1774">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1775">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1775">See Also</span></span>

- <span data-ttu-id="220d0-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="220d0-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="220d0-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="220d0-1786">セマフォの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="220d0-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1787">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1788">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1788">Description</span></span>

<span data-ttu-id="220d0-1789">このサービスを使用すると、セマフォのインスタンスをめぐって中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="220d0-1790">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1791">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1791">Parameters</span></span> 

- <span data-ttu-id="220d0-1792">**semaphore_ptr**: 以前に作成されたセマフォを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1793">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1793">Return Values</span></span>

- <span data-ttu-id="220d0-1794">**TX_SUCCESS**: (0x00) セマフォの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="220d0-1795">TX_SEMAPHORE_ERROR: (0x0C) カウント セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1796">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1796">Allowed From</span></span>

<span data-ttu-id="220d0-1797">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1798">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1798">Preemption Possible</span></span>

<span data-ttu-id="220d0-1799">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1800">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1800">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1801">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1801">See Also</span></span>

- <span data-ttu-id="220d0-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="220d0-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1807">tx_semaphore_put</span></span>

<span data-ttu-id="220d0-1808">カウント セマフォへのインスタンスの配置</span><span class="sxs-lookup"><span data-stu-id="220d0-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1809">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1810">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1810">Description</span></span>

<span data-ttu-id="220d0-1811">このサービスを使用すると、指定されたカウント セマフォにインスタンスが 1 つ入れられます。つまり、カウント セマフォが 1 つインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1812">セマフォがすべて 1 のとき (OxFFFFFFFF) のときにこのサービスが呼び出されると、新しい配置操作によってセマフォはゼロにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1813">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1813">Parameters</span></span>

- <span data-ttu-id="220d0-1814">**semaphore_ptr**: 以前に作成されたカウント セマフォ制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1815">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1815">Return Values</span></span>

- <span data-ttu-id="220d0-1816">**TX_SUCCESS**: (0x00) セマフォの配置に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="220d0-1817">TX_SEMAPHORE_ERROR: (0x0C) カウント セマフォを指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1818">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1818">Allowed From</span></span>

<span data-ttu-id="220d0-1819">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1820">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1820">Preemption Possible</span></span>

<span data-ttu-id="220d0-1821">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1822">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1823">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1823">See Also</span></span>

- <span data-ttu-id="220d0-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="220d0-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="220d0-1834">セマフォの配置時にアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="220d0-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1835">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="220d0-1836">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1836">Description</span></span>

<span data-ttu-id="220d0-1837">このサービスを使用すると、指定されたセマフォが配置されるたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="220d0-1838">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-1839">アプリケーションのセマフォ通知コールバックによって、中断オプションによる ThreadX SMP API の呼び出しを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1840">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1840">Parameters</span></span> 

- <span data-ttu-id="220d0-1841">**semaphore_ptr**: 以前に作成されたセマフォを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="220d0-1842">**semaphore_put_notify**: アプリケーションのセマフォ配置通知関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="220d0-1843">この値が TX_NULL の場合、通知が無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1844">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1844">Return Values</span></span>

- <span data-ttu-id="220d0-1845">**TX_SUCCESS**: (0x00) セマフォ配置通知の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="220d0-1846">TX_SEMAPHORE_ERROR: (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="220d0-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、通知機能を無効にしてコンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1848">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1848">Allowed From</span></span>

<span data-ttu-id="220d0-1849">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1850">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1850">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a><span data-ttu-id="220d0-1851">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1851">See Also</span></span>

- <span data-ttu-id="220d0-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="220d0-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="220d0-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="220d0-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="220d0-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="220d0-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="220d0-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="220d0-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="220d0-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="220d0-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="220d0-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1861">tx_thread_create</span></span>

<span data-ttu-id="220d0-1862">アプリケーション スレッドの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1863">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="220d0-1864">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1864">Description</span></span>

<span data-ttu-id="220d0-1865">このサービスを使用すると、指定されたタスク エントリ関数で実行が開始されるアプリケーション スレッドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="220d0-1866">スタック、優先度、プリエンプションしきい値、およびタイムスライスは、入力パラメーターによって指定される属性の中にあります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="220d0-1867">さらに、スレッドの初期実行状態も指定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1868">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1868">Parameters</span></span>

- <span data-ttu-id="220d0-1869">**thread_ptr**: スレッド制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="220d0-1870">**name_ptr**: スレッドの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="220d0-1871">**entry_function**: スレッド実行の初期 C 関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="220d0-1872">このエントリ関数から戻されたスレッドは完了状態になり、無期限に保留されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="220d0-1873">**entry_input**: 最初の実行時にスレッドのエントリ関数に渡される 32 ビット値。</span><span class="sxs-lookup"><span data-stu-id="220d0-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="220d0-1874">この入力が使用されるかどうかは、アプリケーションによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="220d0-1875">**stack_start**: スタックのメモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="220d0-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="220d0-1876">**stack_size**: スタック メモリ領域内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="220d0-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="220d0-1877">スレッドのスタック領域は、最悪の場合の関数呼び出し入れ子やローカル変数の使用に対処できるだけの大きさでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="220d0-1878">**priority**: スレッドの数値優先度。</span><span class="sxs-lookup"><span data-stu-id="220d0-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="220d0-1879">有効な値の範囲は 0 から (TX_MAX_PRIORITES-1) です。0 は優先度が最も高いことを表します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="220d0-1880">**preempt_threshold**: 無効なプリエンプションの最高優先度レベル (0 ～ (TX_MAX_PRIORITIES-1))。</span><span class="sxs-lookup"><span data-stu-id="220d0-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="220d0-1881">このレベルより優先度が高い場合のみ、このスレッドがプリエンプション可能になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="220d0-1882">この値は、指定された優先度以下でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="220d0-1883">値がスレッド優先度と等しいと、プリエンプションしきい値が無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="220d0-1884">**time_slice**: このスレッドの実行が、同じ優先度の他の準備完了スレッドを実行できるより前に許可されるタイマーティック数。</span><span class="sxs-lookup"><span data-stu-id="220d0-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="220d0-1885">プリエンプションしきい値を使用すると、タイムスライスが無効になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="220d0-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="220d0-1886">有効なタイムスライス値の範囲は、1 から 0xFFFFFFFF までです。</span><span class="sxs-lookup"><span data-stu-id="220d0-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="220d0-1887">値が **TX_NO_TIME_SLICE** (0 の値) の場合、このスレッドのタイムスライスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="220d0-1888">タイムスライシングを使用すると、わずかなシステム オーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="220d0-1889">タイムスライシングは、複数のスレッドが同じ優先度を共有している場合にしか役立たないため、一意の優先度を持つスレッドにはタイム スライスを割り当てないでください。</span><span class="sxs-lookup"><span data-stu-id="220d0-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="220d0-1890">**auto_start**: スレッドをすぐに開始するか保留状態にするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="220d0-1891">有効なオプションは **TX_AUTO_START** (0x01) と **TX_DONT_START** (0x00) です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="220d0-1892">TX_DONT_START が指定されている場合、スレッドを実行するためにアプリケーションは後で tx_thread_resume を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1893">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1893">Return Values</span></span>

- <span data-ttu-id="220d0-1894">**TX_SUCCESS**: (0x00) スレッドの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="220d0-1895">TX_THREAD_ERROR: (0x0E) スレッド制御ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="220d0-1896">ポインターが NULL であるか、スレッドは既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="220d0-1897">TX_PTR_ERROR: (0x03) エントリ ポイントの開始アドレスが無効であるか、スタック領域が無効 (通常は NULL) です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="220d0-1898">TX_SIZE_ERROR: (0x05) スタック領域のサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="220d0-1899">スレッドを実行するには、少なくとも **TX_MINIMUM_STACK** バイト必要です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="220d0-1900">TX_PRIORITY_ERROR: (0x0F) スレッド優先度の値が (0 から (TX_MAX_PRIORITIES-1)) の範囲外であるため、無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="220d0-1901">TX_THRESH_ERROR: (0x18) 無効なプリエンプションしきい値が指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="220d0-1902">この値は、スレッドの初期優先度以下の有効な優先度でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="220d0-1903">TX_START_ERROR: (0x10) 自動開始の選択が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="220d0-1904">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1905">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1905">Allowed From</span></span>

<span data-ttu-id="220d0-1906">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1907">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1907">Preemption Possible</span></span>

<span data-ttu-id="220d0-1908">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1909">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1909">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
                my_thread_entry, 0x1234,
                (VOID *) 0x400000, 1000,
                15, 15, TX_NO_TIME_SLICE,
                TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
   for execution! */
...

/* Thread’s entry function. When "my_thread" actually
   begins execution, control is transferred to this
   function. */
VOID my_thread_entry (ULONG initial_input)
{

    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */

    /* The real work of the thread, including calls to
    other function should be called from here! */

    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```
### <a name="see-also"></a><span data-ttu-id="220d0-1910">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1910">See Also</span></span>

- <span data-ttu-id="220d0-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1911">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-1913">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-1920">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-1921">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="220d0-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1928">tx_thread_delete</span></span>

<span data-ttu-id="220d0-1929">アプリケーション スレッドの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1930">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-1931">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1931">Description</span></span>

<span data-ttu-id="220d0-1932">このサービスを使用すると、指定したアプリケーション スレッドが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="220d0-1933">指定されたスレッドは終了または完了した状態でなければならないため、そのスレッド自体を削除しようとしているスレッドからこのサービスを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-1934">スレッドのスタックに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、サービスの完了後に利用できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="220d0-1935">また、アプリケーションでは、削除されたスレッドが使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1936">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1936">Parameters</span></span>

- <span data-ttu-id="220d0-1937">**thread_ptr**: 以前に作成されたアプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1938">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1938">Return Values</span></span>

- <span data-ttu-id="220d0-1939">**TX_SUCCESS**: (0x00) スレッドの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="220d0-1940">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-1941">**TX_DELETE_ERROR**: (0x11) 指定されたスレッドが終了または完了した状態でありません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="220d0-1942">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1943">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1943">Allowed From</span></span>

<span data-ttu-id="220d0-1944">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-1945">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-1945">Preemption Possible</span></span>

<span data-ttu-id="220d0-1946">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1947">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1947">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-1948">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1948">See Also</span></span>

- <span data-ttu-id="220d0-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1949">tx_thread_create</span></span>
- <span data-ttu-id="220d0-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-1951">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-1958">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-1959">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="220d0-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="220d0-1967">スレッドの開始または終了時にアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="220d0-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-1968">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="220d0-1969">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-1969">Description</span></span>

<span data-ttu-id="220d0-1970">このサービスを使用すると、指定されたスレッドが開始または終了するたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="220d0-1971">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-1972">アプリケーションのスレッド開始/終了通知コールバックによって、中断オプションによる ThreadX SMP API の呼び出しを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="220d0-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-1973">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-1973">Parameters</span></span>

- <span data-ttu-id="220d0-1974">**thread_ptr**: 以前に作成されたスレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="220d0-1975">**entry_exit_notify**: アプリケーションのスレッド開始/終了通知関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="220d0-1976">開始/終了通知関数の 2 番目のパラメーターで、開始または終了が存在するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="220d0-1977">値 TX_THREAD_ENTRY (0x00) は、スレッドが開始されたことを示します。値 TX_THREAD_EXIT (0x01) は、スレッドが終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="220d0-1978">この値が TX_NULL の場合、通知が無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-1979">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-1979">Return Values</span></span>

- <span data-ttu-id="220d0-1980">**TX_SUCCESS**: (0x00) スレッド開始/終了通知関数の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="220d0-1981">TX_THREAD_ERROR: (0x0E) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="220d0-1982">**TX_FEATURE_NOT_ENABLED (0xFF)** システムは、通知機能を無効にしてコンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="220d0-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-1983">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-1983">Allowed From</span></span>

<span data-ttu-id="220d0-1984">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-1985">例</span><span class="sxs-lookup"><span data-stu-id="220d0-1985">Example</span></span>

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
                my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
   successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{

    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
                 /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
         /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="220d0-1986">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-1986">See Also</span></span>

- <span data-ttu-id="220d0-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-1987">tx_thread_create</span></span>
- <span data-ttu-id="220d0-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-1988">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-1990">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-1997">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-1998">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="220d0-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2005">tx_thread_identify</span></span>

<span data-ttu-id="220d0-2006">現在実行中のスレッドを指すポインターを取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2007">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="220d0-2008">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2008">Description</span></span>

<span data-ttu-id="220d0-2009">このサービスを使用すると、現在実行中のスレッドを指すポインターが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="220d0-2010">実行中のスレッドがない場合、null ポインターが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2011">このサービスが ISR から呼び出された場合、戻り値は、実行中の割り込みハンドラーの前に実行されているスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2012">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2012">Parameters</span></span>

<span data-ttu-id="220d0-2013">None</span><span class="sxs-lookup"><span data-stu-id="220d0-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2014">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2014">Return Values</span></span>

- <span data-ttu-id="220d0-2015">thread pointer: 現在実行中のスレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="220d0-2016">実行中のスレッドがない場合、戻り値は TX_NULL です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2017">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2017">Allowed From</span></span>

<span data-ttu-id="220d0-2018">スレッドと ISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2019">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2019">Preemption Possible</span></span>

<span data-ttu-id="220d0-2020">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2021">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2021">Example</span></span>

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2022">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2022">See Also</span></span>

- <span data-ttu-id="220d0-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2023">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2024">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2032">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2033">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="220d0-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2040">tx_thread_info_get</span></span>

<span data-ttu-id="220d0-2041">スレッドに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2042">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="220d0-2043">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2043">Description</span></span>

<span data-ttu-id="220d0-2044">このサービスを使用すると、指定したスレッドに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2045">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2045">Parameters</span></span> 

- <span data-ttu-id="220d0-2046">**thread_ptr**: スレッド制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="220d0-2047">**name**: スレッドの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="220d0-2048">**state**: スレッドの現在の実行状態の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="220d0-2049">使用できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="220d0-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="220d0-2050">**TX_READY**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="220d0-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="220d0-2051">**TX_COMPLETED**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="220d0-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="220d0-2052">**TX_TERMINATED**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="220d0-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="220d0-2053">**TX_SUSPENDED**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="220d0-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="220d0-2054">**TX_SLEEP**: (0x04)</span><span class="sxs-lookup"><span data-stu-id="220d0-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="220d0-2055">**TX_QUEUE_SUSP**: (0x05)</span><span class="sxs-lookup"><span data-stu-id="220d0-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="220d0-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span><span class="sxs-lookup"><span data-stu-id="220d0-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="220d0-2057">**TX_EVENT_FLAG**: (0x07)</span><span class="sxs-lookup"><span data-stu-id="220d0-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="220d0-2058">**TX_BLOCK_MEMORY**: (0x08)</span><span class="sxs-lookup"><span data-stu-id="220d0-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="220d0-2059">**TX_BYTE_MEMORY**: (0x09)</span><span class="sxs-lookup"><span data-stu-id="220d0-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="220d0-2060">**TX_MUTEX_SUSP**: (0x0D)</span><span class="sxs-lookup"><span data-stu-id="220d0-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="220d0-2061">**run_count**: スレッドの実行数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="220d0-2062">**priority**: スレッドの優先度の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="220d0-2063">**preemption_threshold**: スレッドのプリエンプションしきい値の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="220d0-2064">**time_slice**: スレッドのタイムスライスの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="220d0-2065">**next_thread**: 次に作成されるスレッド ポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="220d0-2066">**suspended_thread**: 中断リスト内の次のスレッドを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2067">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2068">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2068">Return Values</span></span>

- <span data-ttu-id="220d0-2069">**TX_SUCCESS**: (0x00) スレッドの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="220d0-2070">TX_THREAD_ERROR: (0x0E) スレッド制御ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2071">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2071">Allowed From</span></span>

<span data-ttu-id="220d0-2072">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2073">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2073">Preemption Possible</span></span>

<span data-ttu-id="220d0-2074">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2075">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2075">Example</span></span>

```C
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
   thread "my_thread." */
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2076">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2076">See Also</span></span>

- <span data-ttu-id="220d0-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2077">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2078">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2080">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2086">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2087">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="220d0-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="220d0-2095">スレッドに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2096">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="220d0-2097">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2097">Description</span></span>

<span data-ttu-id="220d0-2098">このサービスを使用すると、指定したスレッドに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2099">ThreadX SMP ライブラリとアプリケーションからパフォーマンス情報が返されるようにするには、このサービス用に定義された **TX_THREAD_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2100">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2100">Parameters</span></span> 

- <span data-ttu-id="220d0-2101">**thread_ptr**: 以前に作成されたスレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="220d0-2102">**resumptions**: このスレッドの再開数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="220d0-2103">**suspensions**: このスレッドの再開数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="220d0-2104">**solicited_preemptions**: このスレッドにより行われた ThreadX API サービス呼び出しによるプリエンプション数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="220d0-2105">**interrupt_preemptions**: 割り込み処理の結果であるこのスレッドのプリエンプション数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="220d0-2106">**priority_inversions**: このスレッドの優先度逆転数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="220d0-2107">**time_slices**: このスレッドのタイムスライス数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="220d0-2108">**relinquishes**: このスレッドにより実行されるスレッド放棄の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="220d0-2109">**timeouts**: このスレッドでの中断タイムアウトの数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="220d0-2110">**wait_aborts**: このスレッドで実行された待機中止の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="220d0-2111">**last_preempted_by**: このスレッドを最後にプリエンプションしたスレッド ポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2112">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2113">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2113">Return Values</span></span>

- <span data-ttu-id="220d0-2114">**TX_SUCCESS**: (0x00) スレッド パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="220d0-2115">**TX_PTR_ERROR**: (0x03) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="220d0-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2117">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2117">Allowed From</span></span>

<span data-ttu-id="220d0-2118">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2119">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2119">Example</span></span>

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

/* Retrieve performance information on the previously created
   thread. */
status = tx_thread_performance_info_get(&my_thread, &resumptions,
               &suspensions,
               &solicited_preemptions, &interrupt_preemptions,
               &priority_inversions, &time_slices,
               &relinquishes, &timeouts,
               &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2120">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2120">See Also</span></span>

- <span data-ttu-id="220d0-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2121">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2122">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2124">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2130">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2131">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="220d0-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="220d0-2139">スレッド システムに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2140">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="220d0-2141">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2141">Description</span></span>

<span data-ttu-id="220d0-2142">このサービスを使用すると、システム内のすべてのスレッドに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2143">ThreadX SMP ライブラリとアプリケーションからパフォーマンス情報が返されるようにするには、このサービス用に定義された **TX_THREAD_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2144">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2144">Parameters</span></span>

- <span data-ttu-id="220d0-2145">**resumptions**: スレッド再開の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="220d0-2146">**suspensions**: スレッド保留の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="220d0-2147">**solicited_preemptions**: スレッドで ThreadX API サービスが呼び出された結果としてのスレッド プリエンプションの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="220d0-2148">**interrupt_preemptions**: 割り込み処理の結果としてのスレッド プリエンプションの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="220d0-2149">**priority_inversions**: スレッド優先度逆転の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="220d0-2150">**time_slices**: スレッド タイムスライスの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="220d0-2151">**relinquishes**: スレッド放棄の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="220d0-2152">**timeouts**: スレッド中断タイムアウトの総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="220d0-2153">**wait_aborts**: スレッド待機中止の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="220d0-2154">**non_idle_returns**: 別のスレッドの実行準備が整ったときにスレッドがシステムに戻る回数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="220d0-2155">**idle_returns**: 実行する準備ができているスレッドが他にない場合 (アイドル状態のシステム) にスレッドがシステムに戻る回数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2156">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2157">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2157">Return Values</span></span>

- <span data-ttu-id="220d0-2158">**TX_SUCCESS**: (0x00) スレッド システム パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="220d0-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2160">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2160">Allowed From</span></span>

<span data-ttu-id="220d0-2161">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2162">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2162">Example</span></span>

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

/* Retrieve performance information on all previously created
   thread. */
status = tx_thread_performance_system_info_get(&resumptions,
                &suspensions,
                &solicited_preemptions, &interrupt_preemptions,
                &priority_inversions, &time_slices, &relinquishes,
                &timeouts, &wait_aborts, &non_idle_returns,
                &idle_returns);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2163">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2163">See Also</span></span>

- <span data-ttu-id="220d0-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2164">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2165">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2167">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2173">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2174">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="220d0-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="220d0-2182">アプリケーション スレッドのプリエンプションしきい値の変更</span><span class="sxs-lookup"><span data-stu-id="220d0-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2183">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="220d0-2184">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2184">Description</span></span>

<span data-ttu-id="220d0-2185">このサービスを使用すると、指定したスレッドのプリエンプションしきい値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="220d0-2186">プリエンプションしきい値によって、指定されたスレッドよりプリエンプションしきい値以下のスレッドが優先されることがなくなります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2187">プリエンプションしきい値を使用すると、指定されたスレッドのタイム スライシングが無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2188">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2188">Parameters</span></span>

- <span data-ttu-id="220d0-2189">**thread_ptr**: 以前に作成されたアプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="220d0-2190">**new_threshold**: 新しいプリエンプションしきい値の優先度レベル (0 ～ (TX_MAX_PRIORITIES-1))。</span><span class="sxs-lookup"><span data-stu-id="220d0-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="220d0-2191">**old_threshold**: 前のプリエンプションしきい値を返す場所を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2192">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2192">Return Values</span></span>

- <span data-ttu-id="220d0-2193">**TX_SUCCESS**: (0x00) プリエンプションしきい値の変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="220d0-2194">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2195">**TX_THRESH_ERROR**: (0x18) 指定された新しいプリエンプションしきい値が、有効なスレッド優先度でない (0 ～ (TX_MAX_PRIORITIES-1) 以外の値) か、現在のスレッド優先度より大きい (優先度が低い) です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="220d0-2196">TX_PTR_ERROR: (0x03) 前のプリエンプションしきい値の保存場所を指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="220d0-2197">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2198">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2198">Allowed From</span></span>

<span data-ttu-id="220d0-2199">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2200">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2200">Preemption Possible</span></span>

<span data-ttu-id="220d0-2201">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2202">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2202">Example</span></span>

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

/* Disable all preemption of the specified thread. The
   current preemption-threshold is returned in
   "my_old_threshold". Assume that "my_thread" has
   already been created. */
status = tx_thread_preemption_change(&my_thread,
                             0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
   non-preemptable by another thread. Note that ISRs are
   not prevented by preemption disabling. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2203">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2203">See Also</span></span>

- <span data-ttu-id="220d0-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2204">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2205">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2207">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2213">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2214">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="220d0-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="220d0-2222">アプリケーション スレッドの優先度の変更</span><span class="sxs-lookup"><span data-stu-id="220d0-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2223">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="220d0-2224">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2224">Description</span></span>

<span data-ttu-id="220d0-2225">このサービスを使用すると、指定されたスレッドの優先度が変更されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="220d0-2226">有効な優先順位の範囲は 0 から (TX_MAX_PRIORITES-1) です。0 は最高の優先度レベルを表します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2227">指定されたスレッドのプリエンプションしきい値は、自動的に新しい優先度に設定されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="220d0-2228">新しいしきい値が必要な場合は、**tx_thread_preemption_change** サービスをこの呼び出しの後に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2229">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2229">Parameters</span></span>

- <span data-ttu-id="220d0-2230">**thread_ptr**: 以前に作成されたアプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="220d0-2231">**new_priority**: 新しいスレッド優先度レベル (0 ～ (TX_MAX_PRIORITIES-1))。</span><span class="sxs-lookup"><span data-stu-id="220d0-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="220d0-2232">**old_priority**: スレッドの前の優先度を返す場所を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2233">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2233">Return Values</span></span>

- <span data-ttu-id="220d0-2234">**TX_SUCCESS**: (0x00) 優先度付けの変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="220d0-2235">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2236">TX_PRIORITY_ERROR: (0x0F) 指定された新しい優先度が無効 (0 ～ (TX_MAX_PRIORITIES-1) 以外の値) です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="220d0-2237">TX_PTR_ERROR: (0x03) 前の優先度の保存場所を指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="220d0-2238">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2239">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2239">Allowed From</span></span>

<span data-ttu-id="220d0-2240">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2241">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2241">Preemption Possible</span></span>

<span data-ttu-id="220d0-2242">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2243">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2243">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2244">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2244">See Also</span></span>

- <span data-ttu-id="220d0-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2245">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2246">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2248">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2254">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2255">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="220d0-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="220d0-2263">制御を他のアプリケーション スレッドに放棄</span><span class="sxs-lookup"><span data-stu-id="220d0-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2264">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="220d0-2265">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2265">Description</span></span>

<span data-ttu-id="220d0-2266">このサービスを使用すると、同じまたはそれ以上の優先順位で実行可能な他のスレッドに対してプロセッサ制御が放棄されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2267">このサービスは、同じ優先順位のスレッドに対する制御を放棄するだけでなく、現在のスレッドのプリエンプションしきい値の設定によって実行できない優先順位の高いスレッドに対する制御も放棄します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2268">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2268">Parameters</span></span>

<span data-ttu-id="220d0-2269">None</span><span class="sxs-lookup"><span data-stu-id="220d0-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2270">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2270">Return Values</span></span>

<span data-ttu-id="220d0-2271">None</span><span class="sxs-lookup"><span data-stu-id="220d0-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2272">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2272">Allowed From</span></span>

<span data-ttu-id="220d0-2273">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2274">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2274">Preemption Possible</span></span>

<span data-ttu-id="220d0-2275">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2276">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2276">Example</span></span>

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {

        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```
### <a name="see-also"></a><span data-ttu-id="220d0-2277">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2277">See Also</span></span>

- <span data-ttu-id="220d0-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2278">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2279">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2281">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2287">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2288">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="220d0-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2295">tx_thread_reset</span></span>

<span data-ttu-id="220d0-2296">スレッドのリセット</span><span class="sxs-lookup"><span data-stu-id="220d0-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2297">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2298">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2298">Description</span></span>

<span data-ttu-id="220d0-2299">このサービスを使用すると、スレッドの作成時に定義されたエントリ ポイントで実行するよう指定されたスレッドがリセットされます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="220d0-2300">リセットできるスレッドは、**TX_COMPLETED** または **TX_TERMINATED** の状態にあるものに限られます</span><span class="sxs-lookup"><span data-stu-id="220d0-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2301">スレッドを再実行するためには、再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2302">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2302">Parameters</span></span> 

- <span data-ttu-id="220d0-2303">**thread_ptr**: 以前に作成されたスレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2304">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2304">Return Values</span></span>

- <span data-ttu-id="220d0-2305">**TX_SUCCESS**: (0x00) スレッドのリセットに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="220d0-2306">**TX_NOT_DONE**: (0x20) 指定されたスレッドが TX_COMPLETED や TX_TERMINATED の状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="220d0-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="220d0-2307">TX_THREAD_ERROR: (0x0E) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="220d0-2308">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2309">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2309">Allowed From</span></span>

<span data-ttu-id="220d0-2310">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2311">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2312">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2312">See Also</span></span>

- <span data-ttu-id="220d0-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2313">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2314">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2316">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2323">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="220d0-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2330">tx_thread_resume</span></span>

<span data-ttu-id="220d0-2331">中断したアプリケーション スレッドの再開</span><span class="sxs-lookup"><span data-stu-id="220d0-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2333">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2333">Description</span></span>

<span data-ttu-id="220d0-2334">このサービスを使用すると、***tx_thread_suspend*** 呼び出しによって以前に中断されたスレッドの実行が再開または準備されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="220d0-2335">また、このサービスを使用すると、自動開始なしで作成されたスレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2336">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2336">Parameters</span></span>

- <span data-ttu-id="220d0-2337">**thread_ptr**: 中断されたアプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2338">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2338">Return Values</span></span>

- <span data-ttu-id="220d0-2339">**TX_SUCCESS**: (0x00) スレッドの再開に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="220d0-2340">**TX_SUSPEND_LIFTED**: (0x19) 以前に設定された遅延中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="220d0-2341">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2342">**TX_RESUME_ERROR**: (0x12) 指定されたスレッドは中断されていないか、以前に **_tx_thread_suspend_** 以外のサービスによって中断されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2343">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2343">Allowed From</span></span>

<span data-ttu-id="220d0-2344">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2345">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2345">Preemption Possible</span></span>

<span data-ttu-id="220d0-2346">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2347">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2348">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2348">See Also</span></span>

- <span data-ttu-id="220d0-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2349">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2350">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2352">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2359">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="220d0-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2366">tx_thread_sleep</span></span>

<span data-ttu-id="220d0-2367">現在のスレッドを指定された時間だけ中断</span><span class="sxs-lookup"><span data-stu-id="220d0-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2368">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="220d0-2369">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2369">Description</span></span>

<span data-ttu-id="220d0-2370">このサービスによって、呼び出し元のスレッドは、指定したタイマー ティック数だけ中断されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="220d0-2371">タイマー刻みに関連付けられている物理時間の量は、アプリケーション固有です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="220d0-2372">このサービスは、アプリケーション スレッドからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2373">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2373">Parameters</span></span>

- <span data-ttu-id="220d0-2374">**timer_ticks**: 呼び出し元のアプリケーション スレッドを中断するタイマー ティック数 (0 から 0xFFFFFFFF まで)。</span><span class="sxs-lookup"><span data-stu-id="220d0-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="220d0-2375">0 を指定した場合、サービスはすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2376">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2376">Return Values</span></span>

- <span data-ttu-id="220d0-2377">**TX_SUCCESS**: (0x00) スレッドのスリープに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="220d0-2378">**TX_WAIT_ABORTED**: (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="220d0-2379">**TX_CALLER_ERROR**: (0x13) サービスが非スレッドから呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2380">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2380">Allowed From</span></span>

<span data-ttu-id="220d0-2381">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2382">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2382">Preemption Possible</span></span>

<span data-ttu-id="220d0-2383">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2384">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2385">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2385">See Also</span></span>

- <span data-ttu-id="220d0-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2386">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2387">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2389">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2396">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2397">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="220d0-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="220d0-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="220d0-2404">一連のコアでスレッドの実行を除外</span><span class="sxs-lookup"><span data-stu-id="220d0-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2405">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="220d0-2406">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2406">Description</span></span>

<span data-ttu-id="220d0-2407">この関数を使用すると、"*exclusion_map*" というビット マップで指定されているコアの実行から、指定したスレッドが除外されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="220d0-2408">"*Exclusion_map*" の各ビットはコア (ビット 0 はコア 0 を表す) を表します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="220d0-2409">ビットが設定されている場合、対応するコアが指定したスレッドの実行から除外されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2410">プロセッサの除外を使用すると、最適な一致を見つけるために、スレッドとコアのマッピング ロジックに追加の処理が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="220d0-2411">この処理は、準備が整ったスレッドの数によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2412">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2412">Parameters</span></span> 

- <span data-ttu-id="220d0-2413">**thread_ptr**: コアの除外を変更するためのスレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="220d0-2414">**exclusion_map**: ビットが設定されたコアが除外されることを示すビット マップ。</span><span class="sxs-lookup"><span data-stu-id="220d0-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="220d0-2415">値に 0 を指定すると、スレッドが任意のコア (既定値) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2416">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2416">Return Values</span></span>

- <span data-ttu-id="220d0-2417">TX_SUCCESS: (0x00) コアの除外に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="220d0-2418">TX_THREAD_ERROR: (0x0E) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2419">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2419">Allowed From</span></span>

<span data-ttu-id="220d0-2420">初期化、ISR、スレッド、およびタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2421">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="220d0-2422">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2422">See Also</span></span>

- <span data-ttu-id="220d0-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="220d0-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="220d0-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="220d0-2426">スレッドで現在除外されているコアを取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2427">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2428">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2428">Description</span></span>

<span data-ttu-id="220d0-2429">この関数を使用すると、現在のコアの除外リストが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2430">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2430">Parameters</span></span>

- <span data-ttu-id="220d0-2431">**thread_ptr**: コアの除外を取得するスレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="220d0-2432">**exclusion_map_ptr**: 現在のコア除外ビット マップの宛先。</span><span class="sxs-lookup"><span data-stu-id="220d0-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2433">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2433">Return Values</span></span>

- <span data-ttu-id="220d0-2434">TX_SUCCESS: (0x00) スレッドのコアの除外の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="220d0-2435">TX_THREAD_ERROR: (0x0E) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="220d0-2436">TX_PTR_ERROR: (0x03) 例外の宛先ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2437">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2437">Allowed From</span></span>

<span data-ttu-id="220d0-2438">初期化、ISR、スレッド、およびタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2439">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="220d0-2440">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2440">See Also</span></span>

- <span data-ttu-id="220d0-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="220d0-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="220d0-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="220d0-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="220d0-2444">現在実行中の呼び出し元のコアの取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2445">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="220d0-2446">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2446">Description</span></span>

<span data-ttu-id="220d0-2447">この関数を使用すると、このサービスを実行しているコアのコア ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2448">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2448">Parameters</span></span>

<span data-ttu-id="220d0-2449">None</span><span class="sxs-lookup"><span data-stu-id="220d0-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2450">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2450">Return Values</span></span>

- <span data-ttu-id="220d0-2451">core_id: 現在実行中のコアの ID (0 から TX_THREAD_SMP_MAX_CORES-1)</span><span class="sxs-lookup"><span data-stu-id="220d0-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2452">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2452">Allowed From</span></span>

<span data-ttu-id="220d0-2453">初期化、ISR、スレッド、およびタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2454">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2455">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2455">See Also</span></span>

- <span data-ttu-id="220d0-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="220d0-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="220d0-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="220d0-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="220d0-2459">スレッド スタック エラー通知コールバックの登録</span><span class="sxs-lookup"><span data-stu-id="220d0-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2460">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="220d0-2461">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2461">Description</span></span>

<span data-ttu-id="220d0-2462">このサービスを使用すると、スレッド スタック エラーを処理するための通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="220d0-2463">実行中に ThreadX SMP でスレッド スタック エラーが検出されると、この通知関数が呼び出されてエラーが処理されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="220d0-2464">エラーの処理は、アプリケーションによって完全に定義されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="220d0-2465">違反したスレッドの停止からシステム全体のリセットまで、あらゆることを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2466">ThreadX SMP ライブラリは、このサービスからパフォーマンス情報を返すために定義された **TX_ENABLE_STACK_CHECKING** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2467">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2467">Parameters</span></span>

- <span data-ttu-id="220d0-2468">**error_handler**: アプリケーションのスタック エラー処理関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="220d0-2469">この値が TX_NULL の場合、通知が無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2470">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2470">Return Values</span></span>

- <span data-ttu-id="220d0-2471">**TX_SUCCESS**: (0x00) スレッドのリセットに成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="220d0-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2473">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2473">Allowed From</span></span>

<span data-ttu-id="220d0-2474">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2475">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="220d0-2476">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2476">See Also</span></span>

- <span data-ttu-id="220d0-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2477">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2478">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2480">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2487">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2488">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="220d0-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2494">tx_thread_suspend</span></span>

<span data-ttu-id="220d0-2495">アプリケーション スレッドの中断</span><span class="sxs-lookup"><span data-stu-id="220d0-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2496">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2497">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2497">Description</span></span>

<span data-ttu-id="220d0-2498">このサービスを使用すると、指定したアプリケーション スレッドが中断されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="220d0-2499">スレッドがこのサービスを呼び出して自身を中断する場合があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2500">指定したスレッドが既に別の理由で中断されている場合、この中断は、前の中断が解除されるまで内部的に保持されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="220d0-2501">この場合、指定したスレッドが無条件で中断されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="220d0-2502">後続の無条件中断要求は無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="220d0-2503">中断された後、スレッドを ***tx_thread_resume*** によって再開して再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="220d0-2504">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2504">Parameters</span></span>

- <span data-ttu-id="220d0-2505">**thread_ptr**: アプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2506">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2506">Return Values</span></span>

- <span data-ttu-id="220d0-2507">**TX_SUCCESS**: (0x00) スレッドの中断に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="220d0-2508">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2509">**TX_SUSPEND_ERROR**: (0x14) 指定されたスレッドは終了または完了の状態です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="220d0-2510">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2511">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2511">Allowed From</span></span>

<span data-ttu-id="220d0-2512">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2513">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2513">Preemption Possible</span></span>

<span data-ttu-id="220d0-2514">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2515">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2516">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2516">See Also</span></span>

- <span data-ttu-id="220d0-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2517">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2518">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2520">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2527">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2528">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="220d0-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2534">tx_thread_terminate</span></span>

<span data-ttu-id="220d0-2535">アプリケーション スレッドを終了</span><span class="sxs-lookup"><span data-stu-id="220d0-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2536">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2537">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2537">Description</span></span>

<span data-ttu-id="220d0-2538">このサービスを使用すると、指定したアプリケーション スレッドが、スレッドが中断されているかどうかに関係なく終了します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="220d0-2539">スレッドがこのサービスを呼び出して自身を終了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2540">終了した後、スレッドを再実行するためにはリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="220d0-2541">スレッドが終了に適した状態であることを確認するのは、アプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="220d0-2542">例えば、アプリケーションの重要な処理中や、他のミドルウェア コンポーネントの内部でスレッドを終了させたりしないようにしてください。こうすると、処理が不明な状態なままになります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2543">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2543">Parameters</span></span>

- <span data-ttu-id="220d0-2544">**thread_ptr**: アプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2545">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2545">Return Values</span></span>

- <span data-ttu-id="220d0-2546">**TX_SUCCESS**: (0x00) スレッドの停止に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="220d0-2547">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2548">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2549">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2549">Allowed From</span></span>

<span data-ttu-id="220d0-2550">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2551">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2551">Preemption Possible</span></span>

<span data-ttu-id="220d0-2552">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2553">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2554">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2554">See Also</span></span>

- <span data-ttu-id="220d0-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2555">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2556">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2558">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2565">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2566">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="220d0-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="220d0-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="220d0-2573">アプリケーション スレッドのタイムスライスの変更</span><span class="sxs-lookup"><span data-stu-id="220d0-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2574">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="220d0-2575">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2575">Description</span></span>

<span data-ttu-id="220d0-2576">このサービスを使用すると、指定したアプリケーション スレッドのタイムスライスが変更されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="220d0-2577">スレッドのタイムスライスを選択すると、同じまたはそれより高い優先順位の他のスレッドが実行できるようになるまで、指定したタイマー ティック数を超えて実行されることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2578">プリエンプションしきい値を使用すると、指定されたスレッドのタイム スライシングが無効になります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2579">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2579">Parameters</span></span>

- <span data-ttu-id="220d0-2580">**thread_ptr**: アプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="220d0-2581">**new_time_slice**: 新しいタイム スライス値。</span><span class="sxs-lookup"><span data-stu-id="220d0-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="220d0-2582">有効な値は TX_NO_TIME_SLICE と 1 から 0xFFFFFFFF までの数値です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="220d0-2583">**old_time_slice**: 指定したスレッドの前のタイムスライス値を格納する場所を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2584">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2584">Return Values</span></span>

- <span data-ttu-id="220d0-2585">**TX_SUCCESS**: (0x00) タイムスライスの変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="220d0-2586">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2587">TX_PTR_ERROR: (0x03) 前のタイムスライス保存場所を指すポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="220d0-2588">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2589">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2589">Allowed From</span></span>

<span data-ttu-id="220d0-2590">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2591">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2591">Preemption Possible</span></span>

<span data-ttu-id="220d0-2592">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2593">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2593">Example</span></span>

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

/* Change the time-slice of the thread associated with
   "my_thread" to 20. This will mean that "my_thread"
   can only run for 20 timer-ticks consecutively before
   other threads of equal or higher priority get a chance
   to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
                             &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
   has been changed to 20 and the previous time-slice is
   in "my_old_time_slice." */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2594">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2594">See Also</span></span>

- <span data-ttu-id="220d0-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2595">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2596">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2598">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2605">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2606">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="220d0-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="220d0-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="220d0-2613">指定したスレッドの中断の停止</span><span class="sxs-lookup"><span data-stu-id="220d0-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2614">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="220d0-2615">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2615">Description</span></span>

<span data-ttu-id="220d0-2616">このサービスを使用すると、指定したスレッドのスリープやその他のオブジェクトの中断が中止されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="220d0-2617">待機が中止されると、スレッドが待機していたサービスから TX_WAIT_ABORTED 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2618">このサービスでは、tx_thread_suspend サービスによって行われた明示的な中断は解放されません。</span><span class="sxs-lookup"><span data-stu-id="220d0-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2619">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2619">Parameters</span></span>

- <span data-ttu-id="220d0-2620">**thread_ptr**: 以前に作成されたアプリケーション スレッドを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2621">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2621">Return Values</span></span>

- <span data-ttu-id="220d0-2622">**TX_SUCCESS**: (0x00) スレッド待機中止に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="220d0-2623">TX_THREAD_ERROR: (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="220d0-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) 指定されたスレッドが待機中状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="220d0-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2625">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2625">Allowed From</span></span>

<span data-ttu-id="220d0-2626">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2627">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2627">Preemption Possible</span></span>

<span data-ttu-id="220d0-2628">はい</span><span class="sxs-lookup"><span data-stu-id="220d0-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2629">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2630">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2630">See Also</span></span>

- <span data-ttu-id="220d0-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2631">tx_thread_create</span></span>
- <span data-ttu-id="220d0-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2632">tx_thread_delete</span></span>
- <span data-ttu-id="220d0-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="220d0-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="220d0-2634">tx_thread_identify</span></span>
- <span data-ttu-id="220d0-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="220d0-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="220d0-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="220d0-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="220d0-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="220d0-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="220d0-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="220d0-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="220d0-2641">tx_thread_reset</span></span>
- <span data-ttu-id="220d0-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="220d0-2642">tx_thread_resume</span></span>
- <span data-ttu-id="220d0-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="220d0-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="220d0-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="220d0-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="220d0-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="220d0-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="220d0-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="220d0-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="220d0-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="220d0-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2648">tx_time_get</span></span>

<span data-ttu-id="220d0-2649">現在の時刻の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2650">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="220d0-2651">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2651">Description</span></span>

<span data-ttu-id="220d0-2652">このサービスを使用すると、内部システム クロックの内容が返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="220d0-2653">タイマー刻みごとに内部システム クロックが 1 つ増えます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="220d0-2654">システム クロックは初期化時に 0 に設定されますが、サービス ***tx_time_set*** を使用することで特定の値に変更できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2655">各タイマー刻みが表す実際の時間は、アプリケーションに固有です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2656">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2656">Parameters</span></span>

<span data-ttu-id="220d0-2657">None</span><span class="sxs-lookup"><span data-stu-id="220d0-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2658">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2658">Return Values</span></span>

- <span data-ttu-id="220d0-2659">system clock ticks: 自走の内部システム クロックの値。</span><span class="sxs-lookup"><span data-stu-id="220d0-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2660">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2660">Allowed From</span></span>

<span data-ttu-id="220d0-2661">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2662">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2662">Preemption Possible</span></span>

<span data-ttu-id="220d0-2663">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2664">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2665">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2665">See Also</span></span>

- <span data-ttu-id="220d0-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="220d0-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="220d0-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="220d0-2667">tx_time_set</span></span>

<span data-ttu-id="220d0-2668">現在の時刻の設定</span><span class="sxs-lookup"><span data-stu-id="220d0-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2669">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="220d0-2670">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2670">Description</span></span>

<span data-ttu-id="220d0-2671">このサービスを使用すると、内部システム クロックを指定した値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="220d0-2672">タイマー刻みごとに内部システム クロックが 1 つ増えます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2673">各タイマー刻みが表す実際の時間は、アプリケーションに固有です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2674">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2674">Parameters</span></span>

- <span data-ttu-id="220d0-2675">**new_time**: システム クロックに挿入する新しい時間。有効な値の範囲は 0 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2676">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2676">Return Values</span></span>

<span data-ttu-id="220d0-2677">None</span><span class="sxs-lookup"><span data-stu-id="220d0-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2678">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2678">Allowed From</span></span>

<span data-ttu-id="220d0-2679">スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2680">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2680">Preemption Possible</span></span>

<span data-ttu-id="220d0-2681">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2682">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2683">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2683">See Also</span></span>

- <span data-ttu-id="220d0-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="220d0-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2685">tx_timer_activate</span></span>

<span data-ttu-id="220d0-2686">アプリケーション タイマーのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="220d0-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2687">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2688">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2688">Description</span></span>

<span data-ttu-id="220d0-2689">このサービスを使用すると、指定したアプリケーション タイマーがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="220d0-2690">同じ時刻に期限が切れるタイマーの期限切れルーチンは、アクティブになった順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-2691">期限切れになったワンショット タイマーを再びアクティブにするには、まず **tx_timer_change** を使用してリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2692">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2692">Parameters</span></span>

- <span data-ttu-id="220d0-2693">**timer_ptr**: 以前に作成されたアプリケーション タイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2694">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2694">Return Values</span></span>

- <span data-ttu-id="220d0-2695">**TX_SUCCESS**: (0x00) アプリケーション タイマーのアクティブ化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="220d0-2696">**TX_TIMER_ERROR**: (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="220d0-2697">**TX_ACTIVATE_ERROR**: (0x17) タイマーは既にアクティブであるか、あるいは既に期限が切れているワンショット タイマーです。</span><span class="sxs-lookup"><span data-stu-id="220d0-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2698">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2698">Allowed From</span></span>

<span data-ttu-id="220d0-2699">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2700">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2700">Preemption Possible</span></span>

<span data-ttu-id="220d0-2701">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2702">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2703">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2703">See Also</span></span>

- <span data-ttu-id="220d0-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2704">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2705">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2707">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="220d0-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="220d0-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2711">tx_timer_change</span></span>

<span data-ttu-id="220d0-2712">アプリケーション タイマーの変更</span><span class="sxs-lookup"><span data-stu-id="220d0-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2713">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="220d0-2714">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2714">Description</span></span>

<span data-ttu-id="220d0-2715">このサービスを使用すると、指定したアプリケーション タイマーの有効期限特性が変更されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="220d0-2716">このサービスを呼び出す前に、タイマーを非アクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2717">タイマーを再び開始するには、このサービスの後に **tx_timer_activate** サービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2718">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2718">Parameters</span></span>

- <span data-ttu-id="220d0-2719">**timer_ptr**: タイマー制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="220d0-2720">**initial_ticks**: タイマー有効期限の最初のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="220d0-2721">有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="220d0-2722">**reschedule_ticks**: すべてのタイマー有効期限の、最初の後のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="220d0-2723">このパラメーターにゼロを指定すると、タイマーはワンショット タイマーになります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="220d0-2724">それ以外の場合、定期的なタイマーの有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="220d0-2725">期限切れになったワンショット タイマーを再びアクティブにするには、まず **tx_timer_change** を使用してリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2726">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2726">Return Values</span></span>

- <span data-ttu-id="220d0-2727">**TX_SUCCESS**: (0x00) アプリケーション タイマーの変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="220d0-2728">TX_TIMER_ERROR: (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="220d0-2729">TX_TICK_ERROR: (0x16) 最初のティックとして無効な値 (0) が指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="220d0-2730">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2731">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2731">Allowed From</span></span>

<span data-ttu-id="220d0-2732">スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2733">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2733">Preemption Possible</span></span>

<span data-ttu-id="220d0-2734">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2735">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2735">Example</span></span>

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a><span data-ttu-id="220d0-2736">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2736">See Also</span></span>

- <span data-ttu-id="220d0-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2737">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2738">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2740">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="220d0-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="220d0-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2744">tx_timer_create</span></span>

<span data-ttu-id="220d0-2745">アプリケーション タイマーの作成</span><span class="sxs-lookup"><span data-stu-id="220d0-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2746">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="220d0-2747">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2747">Description</span></span>

<span data-ttu-id="220d0-2748">このサービスを使用すると、指定した有効期限関数と期間でアプリケーション タイマーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2749">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2749">Parameters</span></span>

- <span data-ttu-id="220d0-2750">**timer_ptr**: タイマー制御ブロックを指すポインター</span><span class="sxs-lookup"><span data-stu-id="220d0-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="220d0-2751">**name_ptr**: タイマーの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="220d0-2752">**expiration_function**: タイマーの期限が切れたときに呼び出すアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="220d0-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="220d0-2753">**expiration_input**: タイマーの期限が切れたときに有効期限関数に渡す入力。</span><span class="sxs-lookup"><span data-stu-id="220d0-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="220d0-2754">**initial_ticks**: タイマー有効期限の最初のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="220d0-2755">有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="220d0-2756">**reschedule_ticks**: すべてのタイマー有効期限の、最初の後のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="220d0-2757">このパラメーターにゼロを指定すると、タイマーはワンショット タイマーになります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="220d0-2758">それ以外の場合、定期的なタイマーの有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="220d0-2759">ワンショット タイマーの期限が切れた後に再びアクティブにするには、tx_timer_change を使用してリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="220d0-2760">**auto_activate**: タイマーの作成時に自動的にアクティブにするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="220d0-2761">この値が **TX_AUTO_ACTIVATE** (0x01) の場合、タイマーはアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="220d0-2762">それ以外の場合、値 **TX_NO_ACTIVATE** (0x00) を選択すると、タイマーは非アクティブ状態で作成されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="220d0-2763">この場合、その後にタイマーを実際に開始するには、**_tx_timer_activate_** サービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2764">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2764">Return Values</span></span>

- <span data-ttu-id="220d0-2765">**TX_SUCCESS**: (0x00) アプリケーション タイマーの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="220d0-2766">TX_TIMER_ERROR: (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="220d0-2767">ポインターが NULL であるか、タイマーが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="220d0-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="220d0-2768">TX_TICK_ERROR: (0x16) 最初のティックとして無効な値 (0) が指定されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="220d0-2769">TX_ACTIVATE_ERROR: (0x17) 無効なアクティブ化が選択されました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="220d0-2770">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2771">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2771">Allowed From</span></span>

<span data-ttu-id="220d0-2772">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="220d0-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2773">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2773">Preemption Possible</span></span>

<span data-ttu-id="220d0-2774">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2775">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2775">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2776">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2776">See Also</span></span>

- <span data-ttu-id="220d0-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2777">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2778">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2780">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="220d0-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="220d0-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="220d0-2785">アプリケーション タイマーの非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="220d0-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2786">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="220d0-2787">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2787">Description</span></span>

<span data-ttu-id="220d0-2788">このサービスを使用すると、指定したアプリケーション タイマーが非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="220d0-2789">タイマーが既に非アクティブ化されている場合、このサービスによる影響はありません。</span><span class="sxs-lookup"><span data-stu-id="220d0-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2790">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2790">Parameters</span></span> 

- <span data-ttu-id="220d0-2791">**timer_ptr**: 以前に作成されたアプリケーション タイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2792">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2792">Return Values</span></span>

- <span data-ttu-id="220d0-2793">**TX_SUCCESS**: (0x00) アプリケーション タイマーの非アクティブ化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="220d0-2794">TX_TIMER_ERROR: (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2795">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2795">Allowed From</span></span>

<span data-ttu-id="220d0-2796">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2797">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2797">Preemption Possible</span></span>

<span data-ttu-id="220d0-2798">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2799">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2800">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2800">See Also</span></span>

- <span data-ttu-id="220d0-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2801">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2802">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2803">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2804">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="220d0-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="220d0-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2808">tx_timer_delete</span></span>

<span data-ttu-id="220d0-2809">アプリケーション タイマーの削除</span><span class="sxs-lookup"><span data-stu-id="220d0-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2810">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2811">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2811">Description</span></span>

<span data-ttu-id="220d0-2812">このサービスを使用すると、指定されたアプリケーション タイマーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2813">削除されたタイマーを使用できないようにするのは、アプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2814">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2814">Parameters</span></span> 

- <span data-ttu-id="220d0-2815">**timer_ptr**: 以前に作成されたアプリケーション タイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2816">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2816">Return Values</span></span>

- <span data-ttu-id="220d0-2817">**TX_SUCCESS**: (0x00) アプリケーション タイマーの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="220d0-2818">TX_TIMER_ERROR: (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="220d0-2819">TX_CALLER_ERROR: (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2820">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2820">Allowed From</span></span>

<span data-ttu-id="220d0-2821">Threads</span><span class="sxs-lookup"><span data-stu-id="220d0-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2822">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2822">Preemption Possible</span></span>

<span data-ttu-id="220d0-2823">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2824">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2825">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2825">See Also</span></span>

- <span data-ttu-id="220d0-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2826">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2827">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2828">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="220d0-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="220d0-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2833">tx_timer_info_get</span></span>

<span data-ttu-id="220d0-2834">アプリケーション タイマーに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2835">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="220d0-2836">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2836">Description</span></span>

<span data-ttu-id="220d0-2837">このサービスを使用すると、指定されたアプリケーション タイマーに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2838">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2838">Parameters</span></span>

- <span data-ttu-id="220d0-2839">**timer_ptr**: 以前に作成されたアプリケーション タイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="220d0-2840">**name**: タイマーの名前を指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="220d0-2841">**active**: タイマーのアクティブ表示の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="220d0-2842">タイマーがアクティブでない場合やこのサービスがタイマー自体から呼び出された場合は、TX_FALSE 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="220d0-2843">それ以外の場合、タイマーがアクティブな場合は、TX_TRUE 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="220d0-2844">**remaining_ticks**: タイマーが期限切れになるまでのタイマーティック数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="220d0-2845">**reschedule_ticks**: このタイマーを自動的に再スケジュールするために使用されるタイマーティック数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="220d0-2846">値がゼロの場合、タイマーはワンショットであり、再スケジュールされません。</span><span class="sxs-lookup"><span data-stu-id="220d0-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="220d0-2847">**next_timer**: 次に作成されるアプリケーション タイマーを指すポインターの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="220d0-2848">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2849">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2849">Return Values</span></span>

- <span data-ttu-id="220d0-2850">**TX_SUCCESS**: (0x00) タイマーの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="220d0-2851">TX_TIMER_ERROR: (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2852">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2852">Allowed From</span></span>

<span data-ttu-id="220d0-2853">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="220d0-2854">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="220d0-2854">Preemption Possible</span></span>

<span data-ttu-id="220d0-2855">いいえ</span><span class="sxs-lookup"><span data-stu-id="220d0-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2856">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2856">Example</span></span>

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2857">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2857">See Also</span></span>

- <span data-ttu-id="220d0-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2858">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2859">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2860">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2862">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="220d0-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="220d0-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="220d0-2867">タイマーに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2868">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="220d0-2869">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2869">Description</span></span>

<span data-ttu-id="220d0-2870">このサービスを使用すると、指定されたアプリケーション タイマーに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2871">ThreadX SMP ライブラリとアプリケーションからパフォーマンス情報が返されるようにするには、このサービス用に定義された **TX_TIMER_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2872">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2872">Parameters</span></span> 

- <span data-ttu-id="220d0-2873">**timer_ptr**: 以前に作成されたタイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="220d0-2874">**activates**: このタイマーで実行されたアクティブ化要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="220d0-2875">**reactivates**: この周期的なタイマーに従って実行された自動再起動の回数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="220d0-2876">**deactivates**: このタイマーで実行された非アクティブ化要求数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="220d0-2877">**expirations**: このタイマーの有効期限の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="220d0-2878">**expiration_adjusts**: このタイマーで実行された内部有効期限調整の数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="220d0-2879">これらの調整は、既定のタイマー一覧サイズ (既定では有効期限が 32 ティックを超えるタイマー) より大きいタイマーのタイマー割り込み処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2880">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2881">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2881">Return Values</span></span>

- <span data-ttu-id="220d0-2882">**TX_SUCCESS**: (0x00) タイマー パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="220d0-2883">**TX_PTR_ERROR**: (0x03) タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="220d0-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2885">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2885">Allowed From</span></span>

<span data-ttu-id="220d0-2886">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2887">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2887">Example</span></span>

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2888">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2888">See Also</span></span>

- <span data-ttu-id="220d0-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2889">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2890">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2891">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2893">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="220d0-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="220d0-2897">タイマー システムに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2898">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="220d0-2899">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2899">Description</span></span>

<span data-ttu-id="220d0-2900">このサービスを使用すると、システム内のすべてのアプリケーション タイマーに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2901">ThreadX SMP ライブラリとアプリケーションからパフォーマンス情報が返されるようにするには、このサービス用に定義された **TX_TIMER_ENABLE_PERFORMANCE_INFO** を使用して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2902">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2902">Parameters</span></span>

- <span data-ttu-id="220d0-2903">**activates**: すべてのタイマーで実行されたアクティブ化要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="220d0-2904">**reactivates**: すべての周期的なタイマーに従って実行された自動再起動の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="220d0-2905">**deactivates**: すべてのタイマーで実行された非アクティブ化要求の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="220d0-2906">**expirations**: すべてのタイマーの有効期限の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="220d0-2907">**expiration_adjusts**: すべてのタイマーで実行された内部有効期限調整の総数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="220d0-2908">これらの調整は、既定のタイマー一覧サイズ (既定では有効期限が 32 ティックを超えるタイマー) より大きいタイマーのタイマー割り込み処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2909">パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2910">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2910">Return Values</span></span>

- <span data-ttu-id="220d0-2911">**TX_SUCCESS**: (0x00) タイマー システム パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="220d0-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) システムは、パフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="220d0-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2913">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2913">Allowed From</span></span>

<span data-ttu-id="220d0-2914">初期化、スレッド、タイマー、およびISR</span><span class="sxs-lookup"><span data-stu-id="220d0-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2915">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2915">Example</span></span>

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="220d0-2916">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2916">See Also</span></span>

- <span data-ttu-id="220d0-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="220d0-2917">tx_timer_activate</span></span>
- <span data-ttu-id="220d0-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="220d0-2918">tx_timer_change</span></span>
- <span data-ttu-id="220d0-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="220d0-2919">tx_timer_create</span></span>
- <span data-ttu-id="220d0-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="220d0-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="220d0-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="220d0-2921">tx_timer_delete</span></span>
- <span data-ttu-id="220d0-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="220d0-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="220d0-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="220d0-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="220d0-2925">一連のコアでタイマー実行を除外</span><span class="sxs-lookup"><span data-stu-id="220d0-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2926">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="220d0-2927">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2927">Description</span></span>

<span data-ttu-id="220d0-2928">この関数を使用すると、"*exclusion_map*" というビット マップで指定されているコアの実行から、指定したタイマーが除外されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="220d0-2929">"*Exclusion_map*" の各ビットはコア (ビット 0 はコア 0 を表す) を表します。</span><span class="sxs-lookup"><span data-stu-id="220d0-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="220d0-2930">ビットが設定されている場合、対応するコアが指定したタイマーの実行から除外されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="220d0-2931">プロセッサの除外を使用すると、最適な一致を見つけるために、スレッドとコアのマッピング ロジックに追加の処理が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="220d0-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="220d0-2932">この処理は、準備が整ったスレッドの数によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2933">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2933">Parameters</span></span>

- <span data-ttu-id="220d0-2934">**timer_ptr**: コアの除外を変更するタイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="220d0-2935">**exclusion_map**: ビットが設定されたコアが除外されることを示すビット マップ。</span><span class="sxs-lookup"><span data-stu-id="220d0-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="220d0-2936">値に 0 を指定すると、タイマーが任意のコア (既定値) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2937">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2937">Return Values</span></span>

- <span data-ttu-id="220d0-2938">**TX_SUCCESS**: (0x00) コアの除外に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="220d0-2939">**TX_TIMER_ERROR** (0x0E) タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2940">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2940">Allowed From</span></span>

<span data-ttu-id="220d0-2941">初期化、ISR、スレッド、およびタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2942">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="220d0-2943">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2943">See Also</span></span>

- <span data-ttu-id="220d0-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="220d0-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="220d0-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="220d0-2946">タイマーの現在のコアの除外の取得</span><span class="sxs-lookup"><span data-stu-id="220d0-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="220d0-2947">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="220d0-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="220d0-2948">説明</span><span class="sxs-lookup"><span data-stu-id="220d0-2948">Description</span></span>

<span data-ttu-id="220d0-2949">この関数を使用すると、現在のコアの除外リストが返されます。</span><span class="sxs-lookup"><span data-stu-id="220d0-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="220d0-2950">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220d0-2950">Parameters</span></span>

- <span data-ttu-id="220d0-2951">**timer_ptr**: コアの除外を取得するタイマーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="220d0-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="220d0-2952">**exclusion_map_ptr**: 現在のコア除外ビット マップの宛先。</span><span class="sxs-lookup"><span data-stu-id="220d0-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="220d0-2953">戻り値</span><span class="sxs-lookup"><span data-stu-id="220d0-2953">Return Values</span></span>

- <span data-ttu-id="220d0-2954">TX_SUCCESS: (0x00) タイマーのコアの除外の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="220d0-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="220d0-2955">TX_TIMER_ERROR: (0x0E) タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="220d0-2956">TX_PTR_ERROR: (0x03) 例外の宛先ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="220d0-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="220d0-2957">許可元</span><span class="sxs-lookup"><span data-stu-id="220d0-2957">Allowed From</span></span>

<span data-ttu-id="220d0-2958">初期化、ISR、スレッド、およびタイマー</span><span class="sxs-lookup"><span data-stu-id="220d0-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="220d0-2959">例</span><span class="sxs-lookup"><span data-stu-id="220d0-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="220d0-2960">参照</span><span class="sxs-lookup"><span data-stu-id="220d0-2960">See Also</span></span>

- <span data-ttu-id="220d0-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="220d0-2961">tx_timer_smp_core_exclude</span></span>