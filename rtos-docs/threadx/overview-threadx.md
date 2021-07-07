---
title: Azure RTOS ThreadX を理解する
description: Azure ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0fb861c2291046c2ac6edf1d03014996daa09a8e
ms.sourcegitcommit: c1b00341e0c5ab71372f3d9cc4ee3bdd3702b805
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2021
ms.locfileid: "111988364"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="7f8a1-103">Azure RTOS ThreadX の概要</span><span class="sxs-lookup"><span data-stu-id="7f8a1-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="7f8a1-104">Azure RTOS ThreadX は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用リアルタイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="7f8a1-105">Azure RTOS ThreadX では、高度なスケジューリング、通信、同期、タイマー、メモリ管理、および割り込み管理機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="7f8a1-106">さらに、Azure RTOS ThreadX には、picokernel™ アーキテクチャ、プリエンプションしきい値™ スケジューリング、イベントチェーン™、実行プロファイル、パフォーマンス メトリック、システム イベント トレースなど、優れた機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="7f8a1-107">使いやすさの面でも非常に優れているため、Azure RTOS ThreadX は、最も要件の厳しい埋め込みアプリケーションに最適な選択肢と言えます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="7f8a1-108">2017 年時点で、Azure RTOS ThreadX は、コンシューマー デバイス、医療エレクトロニクス、工業用制御機器など、62 億点以上の幅広い製品に展開されています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="7f8a1-109">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="7f8a1-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="7f8a1-110">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="7f8a1-111">動的スレッド作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-111">Dynamic thread creation</span></span>
* <span data-ttu-id="7f8a1-112">スレッド数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-112">No limits on the number of threads</span></span>
* <span data-ttu-id="7f8a1-113">主なスレッド API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="7f8a1-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-114">tx_thread_create</span></span>
  * <span data-ttu-id="7f8a1-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-115">tx_thread_delete</span></span>
  * <span data-ttu-id="7f8a1-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="7f8a1-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="7f8a1-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="7f8a1-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="7f8a1-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="7f8a1-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="7f8a1-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="7f8a1-119">tx_thread_reset</span></span>
  * <span data-ttu-id="7f8a1-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="7f8a1-120">tx_thread_resume</span></span>
  * <span data-ttu-id="7f8a1-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="7f8a1-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="7f8a1-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="7f8a1-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="7f8a1-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="7f8a1-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="7f8a1-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="7f8a1-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="7f8a1-125">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="7f8a1-126">メッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="7f8a1-126">Message Queues</span></span>

* <span data-ttu-id="7f8a1-127">動的キュー作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-127">Dynamic queue creation</span></span>
* <span data-ttu-id="7f8a1-128">キューの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-128">No limits on the number of queues</span></span>
* <span data-ttu-id="7f8a1-129">値 (またはポインターによる参照) によってコピーされるメッセージ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="7f8a1-130">メッセージ サイズは 32 ビットの単語で 1 - 16 個</span><span class="sxs-lookup"><span data-stu-id="7f8a1-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="7f8a1-131">空および満杯時におけるオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="7f8a1-132">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7f8a1-133">主なメッセージ キュー API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="7f8a1-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-134">tx_queue_create</span></span>
  * <span data-ttu-id="7f8a1-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-135">tx_queue_delete</span></span>
  * <span data-ttu-id="7f8a1-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="7f8a1-136">tx_queue_flush</span></span>
  * <span data-ttu-id="7f8a1-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="7f8a1-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="7f8a1-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="7f8a1-138">tx_queue_receive</span></span>
  * <span data-ttu-id="7f8a1-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="7f8a1-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="7f8a1-140">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="7f8a1-141">カウント セマフォ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-141">Counting Semaphores</span></span>

* <span data-ttu-id="7f8a1-142">動的セマフォ作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="7f8a1-143">セマフォの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="7f8a1-144">32 ビット カウント セマフォ (0 から 4,294,967,295)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="7f8a1-145">コンシューマー プロデューサーまたはリソース保護のサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="7f8a1-146">セマフォが使用できない場合の、オプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="7f8a1-147">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7f8a1-148">主なセマフォ API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="7f8a1-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="7f8a1-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="7f8a1-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="7f8a1-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="7f8a1-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="7f8a1-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="7f8a1-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="7f8a1-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="7f8a1-154">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="7f8a1-155">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-155">Mutexes</span></span>

* <span data-ttu-id="7f8a1-156">動的ミューテックス作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="7f8a1-157">ミューテックスの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="7f8a1-158">入れ子になったリソース保護のサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-158">Nested resource protection supported</span></span>
* <span data-ttu-id="7f8a1-159">オプションの優先度継承のサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="7f8a1-160">ミューテックスが使用できない場合の、オプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="7f8a1-161">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7f8a1-162">主なミューテックス API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="7f8a1-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-163">tx_mutex_create</span></span>
  * <span data-ttu-id="7f8a1-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="7f8a1-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="7f8a1-165">tx_mutex_get</span></span>
  * <span data-ttu-id="7f8a1-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="7f8a1-166">tx_mutex_put</span></span>
* <span data-ttu-id="7f8a1-167">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="7f8a1-168">イベント フラグ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-168">Event Flags</span></span>

* <span data-ttu-id="7f8a1-169">動的イベント フラグ グループ作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="7f8a1-170">イベント フラグ グループの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="7f8a1-171">1 つまたは複数のスレッドの同期</span><span class="sxs-lookup"><span data-stu-id="7f8a1-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="7f8a1-172">アトミックの取得とクリアのサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="7f8a1-173">AND/OR のイベント セットに対する、オプションでのマルチスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="7f8a1-174">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7f8a1-175">主なイベント フラグ API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="7f8a1-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="7f8a1-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="7f8a1-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="7f8a1-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="7f8a1-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="7f8a1-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="7f8a1-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="7f8a1-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="7f8a1-181">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="7f8a1-182">ブロック メモリ プール</span><span class="sxs-lookup"><span data-stu-id="7f8a1-182">Block Memory Pools</span></span>

* <span data-ttu-id="7f8a1-183">動的ブロック プール作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="7f8a1-184">ブロック プールの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="7f8a1-185">固定サイズ ブロックのサイズ、またはプールのサイズに制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="7f8a1-186">きわめて高速なメモリ割り当て/処理配置</span><span class="sxs-lookup"><span data-stu-id="7f8a1-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="7f8a1-187">空のプールに対するオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="7f8a1-188">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7f8a1-189">主なブロック プール API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="7f8a1-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="7f8a1-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="7f8a1-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="7f8a1-192">tx_block_allocate</span></span>
  * <span data-ttu-id="7f8a1-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="7f8a1-193">tx_block_release</span></span>
* <span data-ttu-id="7f8a1-194">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="7f8a1-195">バイト メモリ プール</span><span class="sxs-lookup"><span data-stu-id="7f8a1-195">Byte Memory Pools</span></span>

* <span data-ttu-id="7f8a1-196">動的バイト プール作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="7f8a1-197">バイト プールの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="7f8a1-198">バイト プールのサイズに制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="7f8a1-199">きわめて柔軟な可変長メモリ割り当て/割り当て解除</span><span class="sxs-lookup"><span data-stu-id="7f8a1-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="7f8a1-200">割り当てサイズのローカリティのサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-200">Allocation size locality supported</span></span>
* <span data-ttu-id="7f8a1-201">空のプールに対するオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="7f8a1-202">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7f8a1-203">主なバイト プール API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="7f8a1-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="7f8a1-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="7f8a1-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="7f8a1-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="7f8a1-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="7f8a1-207">tx_byte_release</span></span>
* <span data-ttu-id="7f8a1-208">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="7f8a1-209">アプリケーション タイマー</span><span class="sxs-lookup"><span data-stu-id="7f8a1-209">Application Timers</span></span>

* <span data-ttu-id="7f8a1-210">動的タイマーの作成</span><span class="sxs-lookup"><span data-stu-id="7f8a1-210">Dynamic timer creation</span></span>
* <span data-ttu-id="7f8a1-211">タイマーの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-211">No limits on the number of timers</span></span>
* <span data-ttu-id="7f8a1-212">定期的またはワンショット タイマーのサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="7f8a1-213">定期的タイマーの初期有効期限に異なる値を設定可能</span><span class="sxs-lookup"><span data-stu-id="7f8a1-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="7f8a1-214">タイマーのアクティブ化または非アクティブ化に対する検索なし</span><span class="sxs-lookup"><span data-stu-id="7f8a1-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="7f8a1-215">すべてのタイマーは 1 つのハードウェア タイマー割り込みから派生</span><span class="sxs-lookup"><span data-stu-id="7f8a1-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="7f8a1-216">主なタイマー API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="7f8a1-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="7f8a1-217">tx_timer_create</span></span>
  * <span data-ttu-id="7f8a1-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="7f8a1-218">tx_timer_delete</span></span>
  * <span data-ttu-id="7f8a1-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="7f8a1-219">tx_timer_activate</span></span>
  * <span data-ttu-id="7f8a1-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="7f8a1-220">tx_timer_change</span></span>
  * <span data-ttu-id="7f8a1-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="7f8a1-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="7f8a1-222">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="7f8a1-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="7f8a1-223">Azure RTOS ThreadX コア スケジューラ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="7f8a1-224">最小限のフットプリント (フラッシュは 2 KB、RAM は 1 KB)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="7f8a1-225">サブマイクロ秒の高速なコンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="7f8a1-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="7f8a1-226">スレッド数に関係なく、完全に決定論的</span><span class="sxs-lookup"><span data-stu-id="7f8a1-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="7f8a1-227">優先度に基づく完全なプリエンプティブ スケジューリング</span><span class="sxs-lookup"><span data-stu-id="7f8a1-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="7f8a1-228">32 の既定優先度レベル (オプションで最大 1024 レベル)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="7f8a1-229">優先度レベル内での協調スケジューリング (FIFO)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="7f8a1-230">プリエンプションしきい値テクノロジ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="7f8a1-231">オプションのタイマー サービス:</span><span class="sxs-lookup"><span data-stu-id="7f8a1-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="7f8a1-232">スレッド単位での、オプションのタイム スライス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="7f8a1-233">すべてのブロックに対するオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7f8a1-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="7f8a1-234">API でハードウェア タイマー割り込みを要求</span><span class="sxs-lookup"><span data-stu-id="7f8a1-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="7f8a1-235">実行プロファイル</span><span class="sxs-lookup"><span data-stu-id="7f8a1-235">Execution profiling</span></span>
* <span data-ttu-id="7f8a1-236">システムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="7f8a1-236">System-level Trace</span></span>
* <span data-ttu-id="7f8a1-237">多くの標準に対して認定された安全性</span><span class="sxs-lookup"><span data-stu-id="7f8a1-237">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="7f8a1-238">最も多く展開されている RTOS</span><span class="sxs-lookup"><span data-stu-id="7f8a1-238">Most deployed RTOS</span></span>

<span data-ttu-id="7f8a1-239">大手 M2M 市場インテリジェンス企業である VDC Research によると、Azure RTOS ThreadX は全世界で 62 億件以上展開されています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-239">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="7f8a1-240">Azure RTOS ThreadX の人気は、その信頼性、品質、サイズ、パフォーマンス、先進的機能、使いやすさ、および全体的な市場投入時間が高く評価されていることの証明と言えます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-240">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="7f8a1-241">*「私たちは、会社の設立以来、ワイヤレスおよび IoT 市場における THREADX の成長の軌跡を見てきましたが、THREADX が幅広い業界で導入されていることに、改めて感心しています。」*</span><span class="sxs-lookup"><span data-stu-id="7f8a1-241">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="7f8a1-242">– VDC Research 取締役副社長 Chris Rommel 氏</span><span class="sxs-lookup"><span data-stu-id="7f8a1-242">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="7f8a1-243">小さなフットプリント</span><span class="sxs-lookup"><span data-stu-id="7f8a1-243">Small footprint</span></span>

<span data-ttu-id="7f8a1-244">Azure RTOS ThreadX では、必要な命令領域が 2 KB、RAM が 1 KB と非常に小さいため、フットプリントを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-244">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="7f8a1-245">これは主に、非階層型の picokernel™ アーキテクチャと自動スケーリングによって実現されています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-245">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="7f8a1-246">自動スケーリングとは、アプリケーションで使用されるサービス (およびサポート インフラストラクチャ) だけが、リンク時の最終イメージに含めるられることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-246">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="7f8a1-247">Azure RTOS ThreadX の典型的なサイズ特性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-247">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="7f8a1-248">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-248">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="7f8a1-249">典型的なサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-249">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="7f8a1-250">コア サービス (必須)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-250">Core Services (Require)</span></span> |<span data-ttu-id="7f8a1-251">2,000</span><span class="sxs-lookup"><span data-stu-id="7f8a1-251">2,000</span></span>  |
|<span data-ttu-id="7f8a1-252">キュー サービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-252">Queue Services</span></span>  |<span data-ttu-id="7f8a1-253">900</span><span class="sxs-lookup"><span data-stu-id="7f8a1-253">900</span></span>  |
|<span data-ttu-id="7f8a1-254">イベント フラグ サービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-254">Event Flag Services</span></span>  |<span data-ttu-id="7f8a1-255">900</span><span class="sxs-lookup"><span data-stu-id="7f8a1-255">900</span></span>  |
|<span data-ttu-id="7f8a1-256">セマフォ サービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-256">Semaphore Services</span></span>  |<span data-ttu-id="7f8a1-257">450</span><span class="sxs-lookup"><span data-stu-id="7f8a1-257">450</span></span>  |
|<span data-ttu-id="7f8a1-258">ミューテックス サービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-258">Mutex Services</span></span>  |<span data-ttu-id="7f8a1-259">1,200</span><span class="sxs-lookup"><span data-stu-id="7f8a1-259">1,200</span></span>  |
|<span data-ttu-id="7f8a1-260">ブロック メモリ サービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-260">Block Memory Services</span></span>  |<span data-ttu-id="7f8a1-261">550</span><span class="sxs-lookup"><span data-stu-id="7f8a1-261">550</span></span>  |
|<span data-ttu-id="7f8a1-262">バイト メモリ サービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-262">Byte Memory Services</span></span>  |<span data-ttu-id="7f8a1-263">900</span><span class="sxs-lookup"><span data-stu-id="7f8a1-263">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="7f8a1-264">高速実行</span><span class="sxs-lookup"><span data-stu-id="7f8a1-264">Fast execution</span></span>

<span data-ttu-id="7f8a1-265">Azure RTOS ThreadX は、ほとんどの一般的なプロセッサでサブマイクロ秒のコンテキスト切り替えを実現しており、他の商用 RTOS よりも全体的にかなり高速です。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-265">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="7f8a1-266">高速なだけでなく、Azure RTOS ThreadX は高度に決定論的です。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-266">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="7f8a1-267">200 スレッドが待機している場合でも、1 スレッドだけの場合でも、同様に高速なパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-267">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="7f8a1-268">Azure RTOS ThreadX の典型的なパフォーマンス特性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-268">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="7f8a1-269">高速ブート: Azure RTOS ThreadX は、120 サイクル未満で起動します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-269">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="7f8a1-270">基本的なエラー チェックの省略 (オプション): Azure RTOS ThreadX の基本的なエラー チェックは、コンパイル時にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-270">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="7f8a1-271">これは、アプリケーション コードが検証されていて、各パラメーターに対するエラー チェックがそれ以上必要ない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-271">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="7f8a1-272">これは、システム全体ではなく、コンパイル単位で実行できる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-272">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="7f8a1-273">picokernel™ 設計: サービスは相互に階層化されていないため、不要な関数呼び出しによるオーバーヘッドが発生しません。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-273">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="7f8a1-274">\*最適化された割り込み処理: プリエンプションが必要でない限り、ISR の開始/終了によって保存/復元されるのは、スクラッチ レジスタだけです。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-274">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="7f8a1-275">最適化された API 処理:</span><span class="sxs-lookup"><span data-stu-id="7f8a1-275">Optimized API Processing:</span></span>

    |<span data-ttu-id="7f8a1-276">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="7f8a1-276">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="7f8a1-277">サービス時間 (マイクロ秒単位)\*</span><span class="sxs-lookup"><span data-stu-id="7f8a1-277">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="7f8a1-278">スレッド中断</span><span class="sxs-lookup"><span data-stu-id="7f8a1-278">Thread Suspend</span></span>  |<span data-ttu-id="7f8a1-279">0.6</span><span class="sxs-lookup"><span data-stu-id="7f8a1-279">0.6</span></span>  |
    |<span data-ttu-id="7f8a1-280">スレッド再開</span><span class="sxs-lookup"><span data-stu-id="7f8a1-280">Thread Resume</span></span>  |<span data-ttu-id="7f8a1-281">0.6</span><span class="sxs-lookup"><span data-stu-id="7f8a1-281">0.6</span></span>  |
    |<span data-ttu-id="7f8a1-282">キュー送信</span><span class="sxs-lookup"><span data-stu-id="7f8a1-282">Queue Send</span></span>  |<span data-ttu-id="7f8a1-283">0.3</span><span class="sxs-lookup"><span data-stu-id="7f8a1-283">0.3</span></span>  |
    |<span data-ttu-id="7f8a1-284">キュー受信</span><span class="sxs-lookup"><span data-stu-id="7f8a1-284">Queue Receive</span></span>  |<span data-ttu-id="7f8a1-285">0.3</span><span class="sxs-lookup"><span data-stu-id="7f8a1-285">0.3</span></span>  |
    |<span data-ttu-id="7f8a1-286">セマフォの取得</span><span class="sxs-lookup"><span data-stu-id="7f8a1-286">Get Semaphore</span></span>  |<span data-ttu-id="7f8a1-287">0.2</span><span class="sxs-lookup"><span data-stu-id="7f8a1-287">0.2</span></span>  |
    |<span data-ttu-id="7f8a1-288">セマフォの配置</span><span class="sxs-lookup"><span data-stu-id="7f8a1-288">Put Semaphore</span></span>  |<span data-ttu-id="7f8a1-289">0.2</span><span class="sxs-lookup"><span data-stu-id="7f8a1-289">0.2</span></span>  |
    |<span data-ttu-id="7f8a1-290">コンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="7f8a1-290">Context Switch</span></span>  |<span data-ttu-id="7f8a1-291">0.4</span><span class="sxs-lookup"><span data-stu-id="7f8a1-291">0.4</span></span>  |
    |<span data-ttu-id="7f8a1-292">割り込み応答</span><span class="sxs-lookup"><span data-stu-id="7f8a1-292">Interrupt Response</span></span>  |<span data-ttu-id="7f8a1-293">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="7f8a1-293">0.0 – 0.6</span></span>  |

    <span data-ttu-id="7f8a1-294">\**パフォーマンスの数値は、200MHz で実行されている典型的なプロセッサに基づいたものです*。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-294">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="7f8a1-295">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-295">Advanced technology</span></span>

<span data-ttu-id="7f8a1-296">Azure RTOS ThreadX は高度なテクノロジであり、その最も注目すべき機能は、プリエンプションしきい値によるスケジューリングです。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-296">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="7f8a1-297">この機能は Azure RTOS ThreadX に固有のものであり、広範な学術研究の対象となってきたものです。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-297">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="7f8a1-298">例については、「[How to localize reference titles.docx (プリエンプションしきい値を使った固定優先度タスクのスケジューリング)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)」(コンコーディア大学 Yun Wang、ピッツバーグ大学 Manas Saksena 共著) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-298">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="7f8a1-299">以下に示すのは、Azure RTOS ThreadX の機能です。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-299">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="7f8a1-300">完全かつ包括的なマルチタスキング機能</span><span class="sxs-lookup"><span data-stu-id="7f8a1-300">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="7f8a1-301">スレッド、アプリケーション タイマー、メッセージ キュー、カウント セマフォ、ミューテックス、イベント フラグ、ブロックおよびバイト メモリ プール</span><span class="sxs-lookup"><span data-stu-id="7f8a1-301">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="7f8a1-302">優先度に基づくプリエンプティブ スケジューリング</span><span class="sxs-lookup"><span data-stu-id="7f8a1-302">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="7f8a1-303">優先度の柔軟性 – 最大 1024 段階の優先度レベル</span><span class="sxs-lookup"><span data-stu-id="7f8a1-303">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="7f8a1-304">協調スケジューリング</span><span class="sxs-lookup"><span data-stu-id="7f8a1-304">Cooperative Scheduling</span></span>
* <span data-ttu-id="7f8a1-305">プリエンプションしきい値™ – Azure RTOS ThreadX に固有の機能。コンテキスト切り替えを減らし、柔軟なスケジューリングを保証するのに役立ちます (学術研究に基づく)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-305">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="7f8a1-306">Azure RTOS ThreadX モジュールによるメモリ保護</span><span class="sxs-lookup"><span data-stu-id="7f8a1-306">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="7f8a1-307">完全に決定論的</span><span class="sxs-lookup"><span data-stu-id="7f8a1-307">Fully Deterministic</span></span>
* <span data-ttu-id="7f8a1-308">イベント トレース – 直近の *n* 個のシステム/アプリケーション イベントをキャプチャ</span><span class="sxs-lookup"><span data-stu-id="7f8a1-308">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="7f8a1-309">イベント チェーン™ – Azure RTOS ThreadX の各通信または同期オブジェクトに対して、アプリケーション固有の "通知" コールバック関数を登録</span><span class="sxs-lookup"><span data-stu-id="7f8a1-309">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="7f8a1-310">メモリ保護のオプションを備えた、Azure RTOS ThreadX モジュール</span><span class="sxs-lookup"><span data-stu-id="7f8a1-310">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="7f8a1-311">実行時パフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="7f8a1-311">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="7f8a1-312">スレッド再開の数</span><span class="sxs-lookup"><span data-stu-id="7f8a1-312">Number of thread resumptions</span></span>
  * <span data-ttu-id="7f8a1-313">スレッド中断の数</span><span class="sxs-lookup"><span data-stu-id="7f8a1-313">Number of thread suspensions</span></span>
  * <span data-ttu-id="7f8a1-314">要請されたスレッド プリエンプションの数</span><span class="sxs-lookup"><span data-stu-id="7f8a1-314">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="7f8a1-315">非同期スレッド割り込みプリエンプションの数</span><span class="sxs-lookup"><span data-stu-id="7f8a1-315">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="7f8a1-316">スレッド優先度逆転の数</span><span class="sxs-lookup"><span data-stu-id="7f8a1-316">Number of thread priority inversions</span></span>
  * <span data-ttu-id="7f8a1-317">スレッド放棄の数</span><span class="sxs-lookup"><span data-stu-id="7f8a1-317">Number of thread relinquishes</span></span>
* <span data-ttu-id="7f8a1-318">実行プロファイル キット (EPK)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-318">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="7f8a1-319">個別の割り込みスタック</span><span class="sxs-lookup"><span data-stu-id="7f8a1-319">Separate Interrupt Stack</span></span>
* <span data-ttu-id="7f8a1-320">実行時スタック分析</span><span class="sxs-lookup"><span data-stu-id="7f8a1-320">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="7f8a1-321">最適化されたタイマー割り込み処理</span><span class="sxs-lookup"><span data-stu-id="7f8a1-321">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="7f8a1-322">マルチコア サポート (AMP と SMP)</span><span class="sxs-lookup"><span data-stu-id="7f8a1-322">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="7f8a1-323">標準の Azure RTOS ThreadX は、多くの場合、非対称マルチプロセッシング (AMP) 方式で使用されます。この方式では、Azure RTOS ThreadX とアプリケーション (または Linux) の個別のコピーが各コアで実行され、共有メモリまたは OpenAMP などのプロセッサ間通信メカニズム (Azure RTOS ThreadX では OpenAMP がサポートされています) を介して、相互の通信が行われます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-323">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="7f8a1-324">これは、Azure RTOS ThreadX を使った最も典型的なマルチコア構成であり、アプリケーションがプロセッサを効果的に読み込むことができる場合に、最も効率的に機能します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-324">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="7f8a1-325">プロセッサの読み込みが高度に動的な環境では、次のプロセッサ ファミリで Azure RTOS ThreadX Symetric Multiprocessing (SMP) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-325">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="7f8a1-326">ARM Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="7f8a1-326">ARM Cortex-Ax</span></span>
* <span data-ttu-id="7f8a1-327">ARM Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="7f8a1-327">ARM Cortex-Rx</span></span>
* <span data-ttu-id="7f8a1-328">ARM Cortex-A5x 64 ビット</span><span class="sxs-lookup"><span data-stu-id="7f8a1-328">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="7f8a1-329">MIPS 34K、1004K、interAptiv</span><span class="sxs-lookup"><span data-stu-id="7f8a1-329">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="7f8a1-330">PowerPC</span><span class="sxs-lookup"><span data-stu-id="7f8a1-330">PowerPC</span></span>
* <span data-ttu-id="7f8a1-331">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="7f8a1-331">Synopsys ARC HS</span></span>
* <span data-ttu-id="7f8a1-332">x86</span><span class="sxs-lookup"><span data-stu-id="7f8a1-332">x86</span></span>

<span data-ttu-id="7f8a1-333">Azure RTOS ThreadX SMP では、*n* 個のプロセッサ間で動的な負荷分散が実行されるため、すべての Azure RTOS ThreadX リソース (キュー、セマフォ、イベント フラグ、メモリ プールなど) は、コア上の任意のスレッドからアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-333">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="7f8a1-334">Azure RTOS ThreadX SMP では、すべてのコアで完全な Azure RTOS ThreadX API が有効になり、SMP の操作に対して、次の新しい API が導入されます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-334">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="7f8a1-335">Azure RTOS ThreadX モジュールによるメモリ保護</span><span class="sxs-lookup"><span data-stu-id="7f8a1-335">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="7f8a1-336">Azure RTOS ThreadX モジュールと呼ばれるアドオン製品を使用すると、1 つ以上のアプリケーション スレッドを "モジュール" にバンドルし、それをターゲットで動的に読み込んで実行 (またはインプレース実行) することができます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-336">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="7f8a1-337">モジュールを使用して、フィールドのアップグレード、バグの修正、およびプログラムのパーティション分割を行えば、大規模なアプリケーションでのメモリ使用を、アクティブなスレッドに必要な分だけに抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-337">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="7f8a1-338">モジュールには、Azure RTOS ThreadX 自体から完全に分離されたアドレス空間もあります。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-338">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="7f8a1-339">これにより、Azure RTOS ThreadX ではモジュールの周囲にメモリ保護 (MPU または MMU を使用) を配置できるようになっているので、モジュールの外部からの偶発的なアクセスによって、他のソフトウェア コンポーネントが破損するのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-339">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="7f8a1-340">MISRA 準拠</span><span class="sxs-lookup"><span data-stu-id="7f8a1-340">MISRA compliant</span></span>

<span data-ttu-id="7f8a1-341">Azure RTOS ThreadX と Azure RTOS ThreadX SMP のソース コードは、MISRA-C:2004 と MISRA C:2012 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-341">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="7f8a1-342">MISRA C は、C プログラミング言語を使用した重要なシステム用の一連のプログラミング ガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-342">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="7f8a1-343">元の MISRA C ガイドラインは主に自動車アプリケーションを対象としていましたが、今では MISRA C は安全性が重要な任意のアプリケーションに適用可能なものとして広く認識されています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-343">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="7f8a1-344">Azure RTOS ThreadX は、MISRA-C:2004 と MISRA C:2012 のすべての必要規則と必須規則に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-344">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 認定":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="7f8a1-346">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-346">Supports most popular architectures</span></span>

<span data-ttu-id="7f8a1-347">Azure RTOS ThreadX は、すぐに利用可能で完全なテストとサポートが実現されている、次のような最も一般的な 32/64 ビットのマイクロプロセッサで動作します。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-347">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="7f8a1-348">Analog Devices: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="7f8a1-348">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="7f8a1-349">Andes Core: RISC-V</span><span class="sxs-lookup"><span data-stu-id="7f8a1-349">Andes Core: RISC-V</span></span>
* <span data-ttu-id="7f8a1-350">Ambiqmicro: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="7f8a1-350">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="7f8a1-351">ARM: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="7f8a1-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="7f8a1-352">Cadence: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="7f8a1-352">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="7f8a1-353">CEVA: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="7f8a1-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="7f8a1-354">Cypress: RISC-V</span><span class="sxs-lookup"><span data-stu-id="7f8a1-354">Cypress: RISC-V</span></span>
* <span data-ttu-id="7f8a1-355">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="7f8a1-355">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="7f8a1-356">Infineon: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="7f8a1-356">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="7f8a1-357">Intel および Intel FPGA: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="7f8a1-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="7f8a1-358">Microchip: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="7f8a1-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="7f8a1-359">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="7f8a1-359">Microsemi: RISC-V</span></span>
* <span data-ttu-id="7f8a1-360">NXP: LPC、ARM7、ARM9、PowerPC、68K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="7f8a1-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="7f8a1-361">Renesas: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="7f8a1-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="7f8a1-362">Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="7f8a1-362">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="7f8a1-363">Synopsys: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="7f8a1-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="7f8a1-364">ST: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="7f8a1-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="7f8a1-365">Tl: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="7f8a1-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="7f8a1-366">Wave Computing: MIPS32 4K、24K、34K、1004K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="7f8a1-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="7f8a1-367">Xilinx: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="7f8a1-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="7f8a1-368">最も一般的なツールをサポート</span><span class="sxs-lookup"><span data-stu-id="7f8a1-368">Supports most popular tools</span></span>

<span data-ttu-id="7f8a1-369">Azure RTOS ThreadX では、一般的な埋め込み開発ツールがサポートされています。これには、最も包括的な Azure RTOS ThreadX カーネル認識が利用できる、IAR のEmbedded Workbench™ も含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-369">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="7f8a1-370">その他のツール統合としては、GNU (GCC)、ARM DS-5/uVision®、Green Hills MULTI®、Wind River Workbench™、Imagination Codescape、Renesas e2studio、Metaware SeeCode™、NXP CodeWarrior、Lauterbach TRACE32®、TI Code-Composer Studio、CrossCore などがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-370">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="7f8a1-371">ThreadX の適合レイヤー</span><span class="sxs-lookup"><span data-stu-id="7f8a1-371">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="7f8a1-372">Azure RTOS ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-372">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="7f8a1-373">Azure RTOS にアプリケーションを簡単に移行できるようにするために、ThreadX は、さまざまなレガシ RTO API (FreeRTOS、POSIX、OSEK など) のための[適合レイヤー](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)を提供しています。</span><span class="sxs-lookup"><span data-stu-id="7f8a1-373">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
