---
title: Azure RTOS ThreadX を理解する
description: Azure ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 938619170ef51d354fa970134328c17407ae846a
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754864"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="060c3-103">Azure RTOS ThreadX の概要</span><span class="sxs-lookup"><span data-stu-id="060c3-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="060c3-104">Azure RTOS ThreadX は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用リアルタイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="060c3-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="060c3-105">Azure RTOS ThreadX では、高度なスケジューリング、通信、同期、タイマー、メモリ管理、および割り込み管理機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="060c3-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="060c3-106">さらに、Azure RTOS ThreadX には、picokernel™ アーキテクチャ、プリエンプションしきい値™ スケジューリング、イベントチェーン™、実行プロファイル、パフォーマンス メトリック、システム イベント トレースなど、優れた機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="060c3-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="060c3-107">使いやすさの面でも非常に優れているため、Azure RTOS ThreadX は、最も要件の厳しい埋め込みアプリケーションに最適な選択肢と言えます。</span><span class="sxs-lookup"><span data-stu-id="060c3-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="060c3-108">2017 年時点で、Azure RTOS ThreadX は、コンシューマー デバイス、医療エレクトロニクス、工業用制御機器など、62 億点以上の幅広い製品に展開されています。</span><span class="sxs-lookup"><span data-stu-id="060c3-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="060c3-109">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="060c3-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="060c3-110">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="060c3-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="060c3-111">動的スレッド作成</span><span class="sxs-lookup"><span data-stu-id="060c3-111">Dynamic thread creation</span></span>
* <span data-ttu-id="060c3-112">スレッド数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-112">No limits on the number of threads</span></span>
* <span data-ttu-id="060c3-113">主なスレッド API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="060c3-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="060c3-114">tx_thread_create</span></span>
  * <span data-ttu-id="060c3-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-115">tx_thread_delete</span></span>
  * <span data-ttu-id="060c3-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="060c3-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="060c3-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="060c3-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="060c3-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="060c3-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="060c3-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="060c3-119">tx_thread_reset</span></span>
  * <span data-ttu-id="060c3-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="060c3-120">tx_thread_resume</span></span>
  * <span data-ttu-id="060c3-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="060c3-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="060c3-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="060c3-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="060c3-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="060c3-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="060c3-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="060c3-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="060c3-125">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="060c3-126">メッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="060c3-126">Message Queues</span></span>

* <span data-ttu-id="060c3-127">動的キュー作成</span><span class="sxs-lookup"><span data-stu-id="060c3-127">Dynamic queue creation</span></span>
* <span data-ttu-id="060c3-128">キューの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-128">No limits on the number of queues</span></span>
* <span data-ttu-id="060c3-129">値 (またはポインターによる参照) によってコピーされるメッセージ</span><span class="sxs-lookup"><span data-stu-id="060c3-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="060c3-130">メッセージ サイズは 32 ビットの単語で 1 - 16 個</span><span class="sxs-lookup"><span data-stu-id="060c3-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="060c3-131">空および満杯時におけるオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="060c3-132">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="060c3-133">主なメッセージ キュー API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="060c3-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="060c3-134">tx_queue_create</span></span>
  * <span data-ttu-id="060c3-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-135">tx_queue_delete</span></span>
  * <span data-ttu-id="060c3-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="060c3-136">tx_queue_flush</span></span>
  * <span data-ttu-id="060c3-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="060c3-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="060c3-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="060c3-138">tx_queue_receive</span></span>
  * <span data-ttu-id="060c3-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="060c3-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="060c3-140">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="060c3-141">カウント セマフォ</span><span class="sxs-lookup"><span data-stu-id="060c3-141">Counting Semaphores</span></span>

* <span data-ttu-id="060c3-142">動的セマフォ作成</span><span class="sxs-lookup"><span data-stu-id="060c3-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="060c3-143">セマフォの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="060c3-144">32 ビット カウント セマフォ (0 から 4,294,967,295)</span><span class="sxs-lookup"><span data-stu-id="060c3-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="060c3-145">コンシューマー プロデューサーまたはリソース保護のサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="060c3-146">セマフォが使用できない場合の、オプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="060c3-147">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="060c3-148">主なセマフォ API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="060c3-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="060c3-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="060c3-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="060c3-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="060c3-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="060c3-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="060c3-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="060c3-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="060c3-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="060c3-154">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="060c3-155">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="060c3-155">Mutexes</span></span>

* <span data-ttu-id="060c3-156">動的ミューテックス作成</span><span class="sxs-lookup"><span data-stu-id="060c3-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="060c3-157">ミューテックスの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="060c3-158">入れ子になったリソース保護のサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-158">Nested resource protection supported</span></span>
* <span data-ttu-id="060c3-159">オプションの優先度継承のサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="060c3-160">ミューテックスが使用できない場合の、オプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="060c3-161">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="060c3-162">主なミューテックス API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="060c3-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="060c3-163">tx_mutex_create</span></span>
  * <span data-ttu-id="060c3-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="060c3-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="060c3-165">tx_mutex_get</span></span>
  * <span data-ttu-id="060c3-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="060c3-166">tx_mutex_put</span></span>
* <span data-ttu-id="060c3-167">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="060c3-168">イベント フラグ</span><span class="sxs-lookup"><span data-stu-id="060c3-168">Event Flags</span></span>

* <span data-ttu-id="060c3-169">動的イベント フラグ グループ作成</span><span class="sxs-lookup"><span data-stu-id="060c3-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="060c3-170">イベント フラグ グループの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="060c3-171">1 つまたは複数のスレッドの同期</span><span class="sxs-lookup"><span data-stu-id="060c3-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="060c3-172">アトミックの取得とクリアのサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="060c3-173">AND/OR のイベント セットに対する、オプションでのマルチスレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="060c3-174">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="060c3-175">主なイベント フラグ API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="060c3-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="060c3-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="060c3-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="060c3-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="060c3-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="060c3-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="060c3-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="060c3-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="060c3-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="060c3-181">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="060c3-182">ブロック メモリ プール</span><span class="sxs-lookup"><span data-stu-id="060c3-182">Block Memory Pools</span></span>

* <span data-ttu-id="060c3-183">動的ブロック プール作成</span><span class="sxs-lookup"><span data-stu-id="060c3-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="060c3-184">ブロック プールの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="060c3-185">固定サイズ ブロックのサイズ、またはプールのサイズに制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="060c3-186">きわめて高速なメモリ割り当て/処理配置</span><span class="sxs-lookup"><span data-stu-id="060c3-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="060c3-187">空のプールに対するオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="060c3-188">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="060c3-189">主なブロック プール API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="060c3-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="060c3-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="060c3-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="060c3-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="060c3-192">tx_block_allocate</span></span>
  * <span data-ttu-id="060c3-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="060c3-193">tx_block_release</span></span>
* <span data-ttu-id="060c3-194">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="060c3-195">バイト メモリ プール</span><span class="sxs-lookup"><span data-stu-id="060c3-195">Byte Memory Pools</span></span>

* <span data-ttu-id="060c3-196">動的バイト プール作成</span><span class="sxs-lookup"><span data-stu-id="060c3-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="060c3-197">バイト プールの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="060c3-198">バイト プールのサイズに制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="060c3-199">きわめて柔軟な可変長メモリ割り当て/割り当て解除</span><span class="sxs-lookup"><span data-stu-id="060c3-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="060c3-200">割り当てサイズのローカリティのサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-200">Allocation size locality supported</span></span>
* <span data-ttu-id="060c3-201">空のプールに対するオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="060c3-202">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="060c3-203">主なバイト プール API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="060c3-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="060c3-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="060c3-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="060c3-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="060c3-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="060c3-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="060c3-207">tx_byte_release</span></span>
* <span data-ttu-id="060c3-208">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="060c3-209">アプリケーション タイマー</span><span class="sxs-lookup"><span data-stu-id="060c3-209">Application Timers</span></span>

* <span data-ttu-id="060c3-210">動的タイマーの作成</span><span class="sxs-lookup"><span data-stu-id="060c3-210">Dynamic timer creation</span></span>
* <span data-ttu-id="060c3-211">タイマーの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="060c3-211">No limits on the number of timers</span></span>
* <span data-ttu-id="060c3-212">定期的またはワンショット タイマーのサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="060c3-213">定期的タイマーの初期有効期限に異なる値を設定可能</span><span class="sxs-lookup"><span data-stu-id="060c3-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="060c3-214">タイマーのアクティブ化または非アクティブ化に対する検索なし</span><span class="sxs-lookup"><span data-stu-id="060c3-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="060c3-215">すべてのタイマーは 1 つのハードウェア タイマー割り込みから派生</span><span class="sxs-lookup"><span data-stu-id="060c3-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="060c3-216">主なタイマー API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="060c3-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="060c3-217">tx_timer_create</span></span>
  * <span data-ttu-id="060c3-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="060c3-218">tx_timer_delete</span></span>
  * <span data-ttu-id="060c3-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="060c3-219">tx_timer_activate</span></span>
  * <span data-ttu-id="060c3-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="060c3-220">tx_timer_change</span></span>
  * <span data-ttu-id="060c3-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="060c3-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="060c3-222">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="060c3-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="060c3-223">Azure RTOS ThreadX コア スケジューラ</span><span class="sxs-lookup"><span data-stu-id="060c3-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="060c3-224">最小限のフットプリント (フラッシュは 2 KB、RAM は 1 KB)</span><span class="sxs-lookup"><span data-stu-id="060c3-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="060c3-225">サブマイクロ秒の高速なコンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="060c3-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="060c3-226">スレッド数に関係なく、完全に決定論的</span><span class="sxs-lookup"><span data-stu-id="060c3-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="060c3-227">優先度に基づく完全なプリエンプティブ スケジューリング</span><span class="sxs-lookup"><span data-stu-id="060c3-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="060c3-228">32 の既定優先度レベル (オプションで最大 1024 レベル)</span><span class="sxs-lookup"><span data-stu-id="060c3-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="060c3-229">優先度レベル内での協調スケジューリング (FIFO)</span><span class="sxs-lookup"><span data-stu-id="060c3-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="060c3-230">プリエンプションしきい値テクノロジ</span><span class="sxs-lookup"><span data-stu-id="060c3-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="060c3-231">オプションのタイマー サービス:</span><span class="sxs-lookup"><span data-stu-id="060c3-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="060c3-232">スレッド単位での、オプションのタイム スライス</span><span class="sxs-lookup"><span data-stu-id="060c3-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="060c3-233">すべてのブロックに対するオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="060c3-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="060c3-234">API でハードウェア タイマー割り込みを要求</span><span class="sxs-lookup"><span data-stu-id="060c3-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="060c3-235">実行プロファイル</span><span class="sxs-lookup"><span data-stu-id="060c3-235">Execution profiling</span></span>
* <span data-ttu-id="060c3-236">システムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="060c3-236">System-level Trace</span></span>
* <span data-ttu-id="060c3-237">多くの標準に対して認定された安全性</span><span class="sxs-lookup"><span data-stu-id="060c3-237">Safety certified to many standards</span></span>

## <a name="threadx-footprint"></a><span data-ttu-id="060c3-238">ThreadX メモリ占有領域</span><span class="sxs-lookup"><span data-stu-id="060c3-238">ThreadX footprint</span></span>

<span data-ttu-id="060c3-239">Azure RTOS ThreadX では、必要な命令領域が 2 KB、RAM が 1 KB と非常に小さいため、フットプリントを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="060c3-239">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="060c3-240">これは主に、非階層型の picokernel™ アーキテクチャと自動スケーリングによって実現されています。</span><span class="sxs-lookup"><span data-stu-id="060c3-240">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="060c3-241">自動スケーリングとは、アプリケーションで使用されるサービス (およびサポート インフラストラクチャ) だけが、リンク時の最終イメージに含めるられることを意味します。</span><span class="sxs-lookup"><span data-stu-id="060c3-241">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="060c3-242">Azure RTOS ThreadX の典型的なサイズ特性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="060c3-242">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="060c3-243">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="060c3-243">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="060c3-244">典型的なサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="060c3-244">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="060c3-245">コア サービス (必須)</span><span class="sxs-lookup"><span data-stu-id="060c3-245">Core Services (Require)</span></span> |<span data-ttu-id="060c3-246">2,000</span><span class="sxs-lookup"><span data-stu-id="060c3-246">2,000</span></span>  |
|<span data-ttu-id="060c3-247">キュー サービス</span><span class="sxs-lookup"><span data-stu-id="060c3-247">Queue Services</span></span>  |<span data-ttu-id="060c3-248">900</span><span class="sxs-lookup"><span data-stu-id="060c3-248">900</span></span>  |
|<span data-ttu-id="060c3-249">イベント フラグ サービス</span><span class="sxs-lookup"><span data-stu-id="060c3-249">Event Flag Services</span></span>  |<span data-ttu-id="060c3-250">900</span><span class="sxs-lookup"><span data-stu-id="060c3-250">900</span></span>  |
|<span data-ttu-id="060c3-251">セマフォ サービス</span><span class="sxs-lookup"><span data-stu-id="060c3-251">Semaphore Services</span></span>  |<span data-ttu-id="060c3-252">450</span><span class="sxs-lookup"><span data-stu-id="060c3-252">450</span></span>  |
|<span data-ttu-id="060c3-253">ミューテックス サービス</span><span class="sxs-lookup"><span data-stu-id="060c3-253">Mutex Services</span></span>  |<span data-ttu-id="060c3-254">1,200</span><span class="sxs-lookup"><span data-stu-id="060c3-254">1,200</span></span>  |
|<span data-ttu-id="060c3-255">ブロック メモリ サービス</span><span class="sxs-lookup"><span data-stu-id="060c3-255">Block Memory Services</span></span>  |<span data-ttu-id="060c3-256">550</span><span class="sxs-lookup"><span data-stu-id="060c3-256">550</span></span>  |
|<span data-ttu-id="060c3-257">バイト メモリ サービス</span><span class="sxs-lookup"><span data-stu-id="060c3-257">Byte Memory Services</span></span>  |<span data-ttu-id="060c3-258">900</span><span class="sxs-lookup"><span data-stu-id="060c3-258">900</span></span>  |

## <a name="threadx-execution-speed"></a><span data-ttu-id="060c3-259">ThreadX 実行速度</span><span class="sxs-lookup"><span data-stu-id="060c3-259">ThreadX execution speed</span></span>

<span data-ttu-id="060c3-260">Azure RTOS ThreadX は、ほとんどの一般的なプロセッサでサブマイクロ秒のコンテキスト切り替えを実現しており、他の商用 RTOS よりも全体的にかなり高速です。</span><span class="sxs-lookup"><span data-stu-id="060c3-260">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="060c3-261">高速なだけでなく、Azure RTOS ThreadX は高度に決定論的です。</span><span class="sxs-lookup"><span data-stu-id="060c3-261">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="060c3-262">200 スレッドが待機している場合でも、1 スレッドだけの場合でも、同様に高速なパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="060c3-262">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="060c3-263">Azure RTOS ThreadX の典型的なパフォーマンス特性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="060c3-263">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="060c3-264">高速ブート: Azure RTOS ThreadX は、120 サイクル未満で起動します。</span><span class="sxs-lookup"><span data-stu-id="060c3-264">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="060c3-265">基本的なエラー チェックの省略 (オプション): Azure RTOS ThreadX の基本的なエラー チェックは、コンパイル時にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="060c3-265">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="060c3-266">これは、アプリケーション コードが検証されていて、各パラメーターに対するエラー チェックがそれ以上必要ない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="060c3-266">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="060c3-267">これは、システム全体ではなく、コンパイル単位で実行できる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="060c3-267">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="060c3-268">picokernel™ 設計: サービスは相互に階層化されていないため、不要な関数呼び出しによるオーバーヘッドが発生しません。</span><span class="sxs-lookup"><span data-stu-id="060c3-268">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="060c3-269">\*最適化された割り込み処理: プリエンプションが必要でない限り、ISR の開始/終了によって保存/復元されるのは、スクラッチ レジスタだけです。</span><span class="sxs-lookup"><span data-stu-id="060c3-269">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="060c3-270">最適化された API 処理:</span><span class="sxs-lookup"><span data-stu-id="060c3-270">Optimized API Processing:</span></span>

    |<span data-ttu-id="060c3-271">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="060c3-271">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="060c3-272">サービス時間 (マイクロ秒単位)\*</span><span class="sxs-lookup"><span data-stu-id="060c3-272">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="060c3-273">スレッド中断</span><span class="sxs-lookup"><span data-stu-id="060c3-273">Thread Suspend</span></span>  |<span data-ttu-id="060c3-274">0.6</span><span class="sxs-lookup"><span data-stu-id="060c3-274">0.6</span></span>  |
    |<span data-ttu-id="060c3-275">スレッド再開</span><span class="sxs-lookup"><span data-stu-id="060c3-275">Thread Resume</span></span>  |<span data-ttu-id="060c3-276">0.6</span><span class="sxs-lookup"><span data-stu-id="060c3-276">0.6</span></span>  |
    |<span data-ttu-id="060c3-277">キュー送信</span><span class="sxs-lookup"><span data-stu-id="060c3-277">Queue Send</span></span>  |<span data-ttu-id="060c3-278">0.3</span><span class="sxs-lookup"><span data-stu-id="060c3-278">0.3</span></span>  |
    |<span data-ttu-id="060c3-279">キュー受信</span><span class="sxs-lookup"><span data-stu-id="060c3-279">Queue Receive</span></span>  |<span data-ttu-id="060c3-280">0.3</span><span class="sxs-lookup"><span data-stu-id="060c3-280">0.3</span></span>  |
    |<span data-ttu-id="060c3-281">セマフォの取得</span><span class="sxs-lookup"><span data-stu-id="060c3-281">Get Semaphore</span></span>  |<span data-ttu-id="060c3-282">0.2</span><span class="sxs-lookup"><span data-stu-id="060c3-282">0.2</span></span>  |
    |<span data-ttu-id="060c3-283">セマフォの配置</span><span class="sxs-lookup"><span data-stu-id="060c3-283">Put Semaphore</span></span>  |<span data-ttu-id="060c3-284">0.2</span><span class="sxs-lookup"><span data-stu-id="060c3-284">0.2</span></span>  |
    |<span data-ttu-id="060c3-285">コンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="060c3-285">Context Switch</span></span>  |<span data-ttu-id="060c3-286">0.4</span><span class="sxs-lookup"><span data-stu-id="060c3-286">0.4</span></span>  |
    |<span data-ttu-id="060c3-287">割り込み応答</span><span class="sxs-lookup"><span data-stu-id="060c3-287">Interrupt Response</span></span>  |<span data-ttu-id="060c3-288">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="060c3-288">0.0 – 0.6</span></span>  |

    <span data-ttu-id="060c3-289">\**パフォーマンスの数値は、200MHz で実行されている典型的なプロセッサに基づいたものです*。</span><span class="sxs-lookup"><span data-stu-id="060c3-289">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="060c3-290">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="060c3-290">Advanced technology</span></span>

<span data-ttu-id="060c3-291">Azure RTOS ThreadX は高度なテクノロジであり、その最も注目すべき機能は、プリエンプションしきい値によるスケジューリングです。</span><span class="sxs-lookup"><span data-stu-id="060c3-291">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="060c3-292">この機能は Azure RTOS ThreadX に固有のものであり、広範な学術研究の対象となってきたものです。</span><span class="sxs-lookup"><span data-stu-id="060c3-292">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="060c3-293">例については、「[How to localize reference titles.docx (プリエンプションしきい値を使った固定優先度タスクのスケジューリング)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)」(コンコーディア大学 Yun Wang、ピッツバーグ大学 Manas Saksena 共著) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="060c3-293">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="060c3-294">以下に示すのは、Azure RTOS ThreadX の機能です。</span><span class="sxs-lookup"><span data-stu-id="060c3-294">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="060c3-295">完全かつ包括的なマルチタスキング機能</span><span class="sxs-lookup"><span data-stu-id="060c3-295">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="060c3-296">スレッド、アプリケーション タイマー、メッセージ キュー、カウント セマフォ、ミューテックス、イベント フラグ、ブロックおよびバイト メモリ プール</span><span class="sxs-lookup"><span data-stu-id="060c3-296">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="060c3-297">優先度に基づくプリエンプティブ スケジューリング</span><span class="sxs-lookup"><span data-stu-id="060c3-297">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="060c3-298">優先度の柔軟性 – 最大 1024 段階の優先度レベル</span><span class="sxs-lookup"><span data-stu-id="060c3-298">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="060c3-299">協調スケジューリング</span><span class="sxs-lookup"><span data-stu-id="060c3-299">Cooperative Scheduling</span></span>
* <span data-ttu-id="060c3-300">プリエンプションしきい値™ – Azure RTOS ThreadX に固有の機能。コンテキスト切り替えを減らし、柔軟なスケジューリングを保証するのに役立ちます (学術研究に基づく)</span><span class="sxs-lookup"><span data-stu-id="060c3-300">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="060c3-301">Azure RTOS ThreadX モジュールによるメモリ保護</span><span class="sxs-lookup"><span data-stu-id="060c3-301">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="060c3-302">完全に決定論的</span><span class="sxs-lookup"><span data-stu-id="060c3-302">Fully Deterministic</span></span>
* <span data-ttu-id="060c3-303">イベント トレース – 直近の *n* 個のシステム/アプリケーション イベントをキャプチャ</span><span class="sxs-lookup"><span data-stu-id="060c3-303">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="060c3-304">イベント チェーン™ – Azure RTOS ThreadX の各通信または同期オブジェクトに対して、アプリケーション固有の "通知" コールバック関数を登録</span><span class="sxs-lookup"><span data-stu-id="060c3-304">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="060c3-305">メモリ保護のオプションを備えた、Azure RTOS ThreadX モジュール</span><span class="sxs-lookup"><span data-stu-id="060c3-305">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="060c3-306">実行時パフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="060c3-306">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="060c3-307">スレッド再開の数</span><span class="sxs-lookup"><span data-stu-id="060c3-307">Number of thread resumptions</span></span>
  * <span data-ttu-id="060c3-308">スレッド中断の数</span><span class="sxs-lookup"><span data-stu-id="060c3-308">Number of thread suspensions</span></span>
  * <span data-ttu-id="060c3-309">要請されたスレッド プリエンプションの数</span><span class="sxs-lookup"><span data-stu-id="060c3-309">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="060c3-310">非同期スレッド割り込みプリエンプションの数</span><span class="sxs-lookup"><span data-stu-id="060c3-310">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="060c3-311">スレッド優先度逆転の数</span><span class="sxs-lookup"><span data-stu-id="060c3-311">Number of thread priority inversions</span></span>
  * <span data-ttu-id="060c3-312">スレッド放棄の数</span><span class="sxs-lookup"><span data-stu-id="060c3-312">Number of thread relinquishes</span></span>
* <span data-ttu-id="060c3-313">実行プロファイル キット (EPK)</span><span class="sxs-lookup"><span data-stu-id="060c3-313">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="060c3-314">個別の割り込みスタック</span><span class="sxs-lookup"><span data-stu-id="060c3-314">Separate Interrupt Stack</span></span>
* <span data-ttu-id="060c3-315">実行時スタック分析</span><span class="sxs-lookup"><span data-stu-id="060c3-315">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="060c3-316">最適化されたタイマー割り込み処理</span><span class="sxs-lookup"><span data-stu-id="060c3-316">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="060c3-317">マルチコア サポート (AMP と SMP)</span><span class="sxs-lookup"><span data-stu-id="060c3-317">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="060c3-318">標準の Azure RTOS ThreadX は、多くの場合、非対称マルチプロセッシング (AMP) 方式で使用されます。この方式では、Azure RTOS ThreadX とアプリケーション (または Linux) の個別のコピーが各コアで実行され、共有メモリまたは OpenAMP などのプロセッサ間通信メカニズム (Azure RTOS ThreadX では OpenAMP がサポートされています) を介して、相互の通信が行われます。</span><span class="sxs-lookup"><span data-stu-id="060c3-318">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="060c3-319">これは、Azure RTOS ThreadX を使った最も典型的なマルチコア構成であり、アプリケーションがプロセッサを効果的に読み込むことができる場合に、最も効率的に機能します。</span><span class="sxs-lookup"><span data-stu-id="060c3-319">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="060c3-320">プロセッサの読み込みが高度に動的な環境では、次のプロセッサ ファミリで Azure RTOS ThreadX Symetric Multiprocessing (SMP) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="060c3-320">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="060c3-321">ARM Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="060c3-321">ARM Cortex-Ax</span></span>
* <span data-ttu-id="060c3-322">ARM Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="060c3-322">ARM Cortex-Rx</span></span>
* <span data-ttu-id="060c3-323">ARM Cortex-A5x 64 ビット</span><span class="sxs-lookup"><span data-stu-id="060c3-323">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="060c3-324">MIPS 34K、1004K、interAptiv</span><span class="sxs-lookup"><span data-stu-id="060c3-324">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="060c3-325">PowerPC</span><span class="sxs-lookup"><span data-stu-id="060c3-325">PowerPC</span></span>
* <span data-ttu-id="060c3-326">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="060c3-326">Synopsys ARC HS</span></span>
* <span data-ttu-id="060c3-327">x86</span><span class="sxs-lookup"><span data-stu-id="060c3-327">x86</span></span>

<span data-ttu-id="060c3-328">Azure RTOS ThreadX SMP では、*n* 個のプロセッサ間で動的な負荷分散が実行されるため、すべての Azure RTOS ThreadX リソース (キュー、セマフォ、イベント フラグ、メモリ プールなど) は、コア上の任意のスレッドからアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="060c3-328">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="060c3-329">Azure RTOS ThreadX SMP では、すべてのコアで完全な Azure RTOS ThreadX API が有効になり、SMP の操作に対して、次の新しい API が導入されます。</span><span class="sxs-lookup"><span data-stu-id="060c3-329">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="060c3-330">Azure RTOS ThreadX モジュールによるメモリ保護</span><span class="sxs-lookup"><span data-stu-id="060c3-330">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="060c3-331">Azure RTOS ThreadX モジュールと呼ばれるアドオン製品を使用すると、1 つ以上のアプリケーション スレッドを "モジュール" にバンドルし、それをターゲットで動的に読み込んで実行 (またはインプレース実行) することができます。</span><span class="sxs-lookup"><span data-stu-id="060c3-331">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="060c3-332">モジュールを使用して、フィールドのアップグレード、バグの修正、およびプログラムのパーティション分割を行えば、大規模なアプリケーションでのメモリ使用を、アクティブなスレッドに必要な分だけに抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="060c3-332">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="060c3-333">モジュールには、Azure RTOS ThreadX 自体から完全に分離されたアドレス空間もあります。</span><span class="sxs-lookup"><span data-stu-id="060c3-333">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="060c3-334">これにより、Azure RTOS ThreadX ではモジュールの周囲にメモリ保護 (MPU または MMU を使用) を配置できるようになっているので、モジュールの外部からの偶発的なアクセスによって、他のソフトウェア コンポーネントが破損するのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="060c3-334">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="060c3-335">MISRA 準拠</span><span class="sxs-lookup"><span data-stu-id="060c3-335">MISRA compliant</span></span>

<span data-ttu-id="060c3-336">Azure RTOS ThreadX と Azure RTOS ThreadX SMP のソース コードは、MISRA-C:2004 と MISRA C:2012 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="060c3-336">Azure RTOS ThreadX and Azure RTOS ThreadX SMP source code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="060c3-337">MISRA C は、C プログラミング言語を使用した重要なシステム用の一連のプログラミング ガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="060c3-337">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="060c3-338">元の MISRA C ガイドラインは主に自動車アプリケーションを対象としていましたが、今では MISRA C は安全性が重要な任意のアプリケーションに適用可能なものとして広く認識されています。</span><span class="sxs-lookup"><span data-stu-id="060c3-338">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="060c3-339">Azure RTOS ThreadX は、MISRA-C:2004 と MISRA C:2012 のすべての必要規則と必須規則に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="060c3-339">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 認定":::

## <a name="supports-most-popular-tools"></a><span data-ttu-id="060c3-341">最も一般的なツールをサポート</span><span class="sxs-lookup"><span data-stu-id="060c3-341">Supports most popular tools</span></span>

<span data-ttu-id="060c3-342">Azure RTOS ThreadX では、一般的な埋め込み開発ツールがサポートされています。これには、最も包括的な Azure RTOS ThreadX カーネル認識が利用できる、IAR のEmbedded Workbench™ も含まれています。</span><span class="sxs-lookup"><span data-stu-id="060c3-342">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="060c3-343">その他のツール統合としては、GNU (GCC)、ARM DS-5/uVision®、Green Hills MULTI®、Wind River Workbench™、Imagination Codescape、Renesas e2studio、Metaware SeeCode™、NXP CodeWarrior、Lauterbach TRACE32®、TI Code-Composer Studio、CrossCore などがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="060c3-343">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="060c3-344">ThreadX の適合レイヤー</span><span class="sxs-lookup"><span data-stu-id="060c3-344">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="060c3-345">Azure RTOS ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="060c3-345">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="060c3-346">Azure RTOS にアプリケーションを簡単に移行できるようにするために、ThreadX は、さまざまなレガシ RTO API (FreeRTOS、POSIX、OSEK など) のための[適合レイヤー](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)を提供しています。</span><span class="sxs-lookup"><span data-stu-id="060c3-346">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
