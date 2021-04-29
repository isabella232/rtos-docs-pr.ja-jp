---
title: Azure RTOS ThreadX を理解する
description: Azure ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812161"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="b5189-103">Azure RTOS ThreadX の概要</span><span class="sxs-lookup"><span data-stu-id="b5189-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="b5189-104">Azure RTOS ThreadX は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用リアルタイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="b5189-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="b5189-105">Azure RTOS ThreadX では、高度なスケジューリング、通信、同期、タイマー、メモリ管理、および割り込み管理機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b5189-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="b5189-106">さらに、Azure RTOS ThreadX には、picokernel™ アーキテクチャ、プリエンプションしきい値™ スケジューリング、イベントチェーン™、実行プロファイル、パフォーマンス メトリック、システム イベント トレースなど、優れた機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="b5189-107">使いやすさの面でも非常に優れているため、Azure RTOS ThreadX は、最も要件の厳しい埋め込みアプリケーションに最適な選択肢と言えます。</span><span class="sxs-lookup"><span data-stu-id="b5189-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="b5189-108">2017 年時点で、Azure RTOS ThreadX は、コンシューマー デバイス、医療エレクトロニクス、工業用制御機器など、62 億点以上の幅広い製品に展開されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="b5189-109">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="b5189-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-api"></a><span data-ttu-id="b5189-110">Azure RTOS ThreadX API</span><span class="sxs-lookup"><span data-stu-id="b5189-110">Azure RTOS ThreadX API</span></span>

* <span data-ttu-id="b5189-111">直感的で一貫性のある API</span><span class="sxs-lookup"><span data-stu-id="b5189-111">Intuitive and consistent API</span></span>
* <span data-ttu-id="b5189-112">名詞 - 動詞の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="b5189-112">Noun-verb naming convention</span></span>
* <span data-ttu-id="b5189-113">すべての API の先頭を *tx_* にして、Azure RTOS ThreadX として簡単に識別</span><span class="sxs-lookup"><span data-stu-id="b5189-113">All APIs have leading *tx_* to easily identify as Azure RTOS ThreadX</span></span>
* <span data-ttu-id="b5189-114">ブロックしている API にオプションのスレッド タイムアウトがある</span><span class="sxs-lookup"><span data-stu-id="b5189-114">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="b5189-115">多数の API をアプリケーション ISR から直接利用可能</span><span class="sxs-lookup"><span data-stu-id="b5189-115">Many APIs are directly available from application ISRs</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="b5189-116">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="b5189-116">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="b5189-117">動的スレッド作成</span><span class="sxs-lookup"><span data-stu-id="b5189-117">Dynamic thread creation</span></span>
* <span data-ttu-id="b5189-118">スレッド数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-118">No limits on the number of threads</span></span>
* <span data-ttu-id="b5189-119">主なスレッド API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-119">Main thread APIs include:</span></span>
  * <span data-ttu-id="b5189-120">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="b5189-120">tx_thread_create</span></span>
  * <span data-ttu-id="b5189-121">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-121">tx_thread_delete</span></span>
  * <span data-ttu-id="b5189-122">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="b5189-122">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="b5189-123">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="b5189-123">tx_thread_priority_change</span></span>
  * <span data-ttu-id="b5189-124">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="b5189-124">tx_thread_relinquish</span></span>
  * <span data-ttu-id="b5189-125">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="b5189-125">tx_thread_reset</span></span>
  * <span data-ttu-id="b5189-126">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="b5189-126">tx_thread_resume</span></span>
  * <span data-ttu-id="b5189-127">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="b5189-127">tx_thread_sleep</span></span>
  * <span data-ttu-id="b5189-128">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="b5189-128">tx_thread_suspend</span></span>
  * <span data-ttu-id="b5189-129">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="b5189-129">tx_thread_terminate</span></span>
  * <span data-ttu-id="b5189-130">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="b5189-130">tx_thread_wait_abort</span></span>
* <span data-ttu-id="b5189-131">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-131">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="b5189-132">メッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="b5189-132">Message Queues</span></span>

* <span data-ttu-id="b5189-133">動的キュー作成</span><span class="sxs-lookup"><span data-stu-id="b5189-133">Dynamic queue creation</span></span>
* <span data-ttu-id="b5189-134">キューの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-134">No limits on the number of queues</span></span>
* <span data-ttu-id="b5189-135">値 (またはポインターによる参照) によってコピーされるメッセージ</span><span class="sxs-lookup"><span data-stu-id="b5189-135">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="b5189-136">メッセージ サイズは 32 ビットの単語で 1 - 16 個</span><span class="sxs-lookup"><span data-stu-id="b5189-136">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="b5189-137">空および満杯時におけるオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-137">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="b5189-138">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-138">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5189-139">主なメッセージ キュー API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-139">Main message queue APIs include:</span></span>
  * <span data-ttu-id="b5189-140">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="b5189-140">tx_queue_create</span></span>
  * <span data-ttu-id="b5189-141">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-141">tx_queue_delete</span></span>
  * <span data-ttu-id="b5189-142">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="b5189-142">tx_queue_flush</span></span>
  * <span data-ttu-id="b5189-143">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="b5189-143">tx_queue_front_send</span></span>
  * <span data-ttu-id="b5189-144">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="b5189-144">tx_queue_receive</span></span>
  * <span data-ttu-id="b5189-145">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="b5189-145">tx_queue_send_notify</span></span>
* <span data-ttu-id="b5189-146">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-146">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="b5189-147">カウント セマフォ</span><span class="sxs-lookup"><span data-stu-id="b5189-147">Counting Semaphores</span></span>

* <span data-ttu-id="b5189-148">動的セマフォ作成</span><span class="sxs-lookup"><span data-stu-id="b5189-148">Dynamic semaphore creation</span></span>
* <span data-ttu-id="b5189-149">セマフォの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-149">No limits on the number of semaphores</span></span>
* <span data-ttu-id="b5189-150">32 ビット カウント セマフォ (0 から 4,294,967,295)</span><span class="sxs-lookup"><span data-stu-id="b5189-150">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="b5189-151">コンシューマー プロデューサーまたはリソース保護のサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-151">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="b5189-152">セマフォが使用できない場合の、オプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-152">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="b5189-153">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-153">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5189-154">主なセマフォ API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-154">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="b5189-155">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="b5189-155">tx_semaphore_create</span></span>
  * <span data-ttu-id="b5189-156">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-156">tx_semaphore_delete</span></span>
  * <span data-ttu-id="b5189-157">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="b5189-157">tx_semaphore_get</span></span>
  * <span data-ttu-id="b5189-158">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="b5189-158">tx_semaphore_put</span></span>
  * <span data-ttu-id="b5189-159">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="b5189-159">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="b5189-160">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-160">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="b5189-161">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="b5189-161">Mutexes</span></span>

* <span data-ttu-id="b5189-162">動的ミューテックス作成</span><span class="sxs-lookup"><span data-stu-id="b5189-162">Dynamic mutex creation</span></span>
* <span data-ttu-id="b5189-163">ミューテックスの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-163">No limits on the number of mutexes</span></span>
* <span data-ttu-id="b5189-164">入れ子になったリソース保護のサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-164">Nested resource protection supported</span></span>
* <span data-ttu-id="b5189-165">オプションの優先度継承のサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-165">Optional priority inheritance supported</span></span>
* <span data-ttu-id="b5189-166">ミューテックスが使用できない場合の、オプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-166">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="b5189-167">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-167">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5189-168">主なミューテックス API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-168">Main mutex APIs include:</span></span>
  * <span data-ttu-id="b5189-169">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="b5189-169">tx_mutex_create</span></span>
  * <span data-ttu-id="b5189-170">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-170">tx_mutex_delete</span></span>
  * <span data-ttu-id="b5189-171">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="b5189-171">tx_mutex_get</span></span>
  * <span data-ttu-id="b5189-172">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="b5189-172">tx_mutex_put</span></span>
* <span data-ttu-id="b5189-173">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-173">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="b5189-174">イベント フラグ</span><span class="sxs-lookup"><span data-stu-id="b5189-174">Event Flags</span></span>

* <span data-ttu-id="b5189-175">動的イベント フラグ グループ作成</span><span class="sxs-lookup"><span data-stu-id="b5189-175">Dynamic event flag group creation</span></span>
* <span data-ttu-id="b5189-176">イベント フラグ グループの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-176">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="b5189-177">1 つまたは複数のスレッドの同期</span><span class="sxs-lookup"><span data-stu-id="b5189-177">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="b5189-178">アトミックの取得とクリアのサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-178">Atomic get and clear supported</span></span>
* <span data-ttu-id="b5189-179">AND/OR のイベント セットに対する、オプションでのマルチスレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-179">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="b5189-180">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5189-181">主なイベント フラグ API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-181">Main event flag APIs include:</span></span>
  * <span data-ttu-id="b5189-182">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="b5189-182">tx_event_flags_create</span></span>
  * <span data-ttu-id="b5189-183">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-183">tx_event_flags_delete</span></span>
  * <span data-ttu-id="b5189-184">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="b5189-184">tx_event_flags_get</span></span>
  * <span data-ttu-id="b5189-185">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="b5189-185">tx_event_flags_set</span></span>
  * <span data-ttu-id="b5189-186">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="b5189-186">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="b5189-187">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-187">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="b5189-188">ブロック メモリ プール</span><span class="sxs-lookup"><span data-stu-id="b5189-188">Block Memory Pools</span></span>

* <span data-ttu-id="b5189-189">動的ブロック プール作成</span><span class="sxs-lookup"><span data-stu-id="b5189-189">Dynamic block pool creation</span></span>
* <span data-ttu-id="b5189-190">ブロック プールの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-190">No limits on the number of block pools</span></span>
* <span data-ttu-id="b5189-191">固定サイズ ブロックのサイズ、またはプールのサイズに制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-191">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="b5189-192">きわめて高速なメモリ割り当て/処理配置</span><span class="sxs-lookup"><span data-stu-id="b5189-192">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="b5189-193">空のプールに対するオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-193">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="b5189-194">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-194">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5189-195">主なブロック プール API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-195">Main block pool APIs include:</span></span>
  * <span data-ttu-id="b5189-196">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="b5189-196">tx_block_pool_create</span></span>
  * <span data-ttu-id="b5189-197">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-197">tx_block_pool_delete</span></span>
  * <span data-ttu-id="b5189-198">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="b5189-198">tx_block_allocate</span></span>
  * <span data-ttu-id="b5189-199">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="b5189-199">tx_block_release</span></span>
* <span data-ttu-id="b5189-200">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-200">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="b5189-201">バイト メモリ プール</span><span class="sxs-lookup"><span data-stu-id="b5189-201">Byte Memory Pools</span></span>

* <span data-ttu-id="b5189-202">動的バイト プール作成</span><span class="sxs-lookup"><span data-stu-id="b5189-202">Dynamic byte pool creation</span></span>
* <span data-ttu-id="b5189-203">バイト プールの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-203">No limits on the number of byte pools</span></span>
* <span data-ttu-id="b5189-204">バイト プールのサイズに制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-204">No limits on size of byte pool</span></span>
* <span data-ttu-id="b5189-205">きわめて柔軟な可変長メモリ割り当て/割り当て解除</span><span class="sxs-lookup"><span data-stu-id="b5189-205">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="b5189-206">割り当てサイズのローカリティのサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-206">Allocation size locality supported</span></span>
* <span data-ttu-id="b5189-207">空のプールに対するオプションでのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-207">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="b5189-208">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-208">Optional timeout on all suspension</span></span>
* <span data-ttu-id="b5189-209">主なバイト プール API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-209">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="b5189-210">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="b5189-210">tx_byte_pool_create</span></span>
  * <span data-ttu-id="b5189-211">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-211">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="b5189-212">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="b5189-212">tx_byte_allocate</span></span>
  * <span data-ttu-id="b5189-213">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="b5189-213">tx_byte_release</span></span>
* <span data-ttu-id="b5189-214">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-214">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="b5189-215">アプリケーション タイマー</span><span class="sxs-lookup"><span data-stu-id="b5189-215">Application Timers</span></span>

* <span data-ttu-id="b5189-216">動的タイマーの作成</span><span class="sxs-lookup"><span data-stu-id="b5189-216">Dynamic timer creation</span></span>
* <span data-ttu-id="b5189-217">タイマーの数に制限なし</span><span class="sxs-lookup"><span data-stu-id="b5189-217">No limits on the number of timers</span></span>
* <span data-ttu-id="b5189-218">定期的またはワンショット タイマーのサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-218">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="b5189-219">定期的タイマーの初期有効期限に異なる値を設定可能</span><span class="sxs-lookup"><span data-stu-id="b5189-219">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="b5189-220">タイマーのアクティブ化または非アクティブ化に対する検索なし</span><span class="sxs-lookup"><span data-stu-id="b5189-220">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="b5189-221">すべてのタイマーは 1 つのハードウェア タイマー割り込みから派生</span><span class="sxs-lookup"><span data-stu-id="b5189-221">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="b5189-222">主なタイマー API としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-222">Main timer APIs include:</span></span>
  * <span data-ttu-id="b5189-223">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="b5189-223">tx_timer_create</span></span>
  * <span data-ttu-id="b5189-224">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="b5189-224">tx_timer_delete</span></span>
  * <span data-ttu-id="b5189-225">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="b5189-225">tx_timer_activate</span></span>
  * <span data-ttu-id="b5189-226">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="b5189-226">tx_timer_change</span></span>
  * <span data-ttu-id="b5189-227">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="b5189-227">tx_timer_deactivate</span></span>
* <span data-ttu-id="b5189-228">追加情報とパフォーマンス API</span><span class="sxs-lookup"><span data-stu-id="b5189-228">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="b5189-229">Azure RTOS ThreadX コア スケジューラ</span><span class="sxs-lookup"><span data-stu-id="b5189-229">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="b5189-230">最小限のフットプリント (フラッシュは 2 KB、RAM は 1 KB)</span><span class="sxs-lookup"><span data-stu-id="b5189-230">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="b5189-231">サブマイクロ秒の高速なコンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="b5189-231">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="b5189-232">スレッド数に関係なく、完全に決定論的</span><span class="sxs-lookup"><span data-stu-id="b5189-232">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="b5189-233">優先度に基づく完全なプリエンプティブ スケジューリング</span><span class="sxs-lookup"><span data-stu-id="b5189-233">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="b5189-234">32 の既定優先度レベル (オプションで最大 1024 レベル)</span><span class="sxs-lookup"><span data-stu-id="b5189-234">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="b5189-235">優先度レベル内での協調スケジューリング (FIFO)</span><span class="sxs-lookup"><span data-stu-id="b5189-235">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="b5189-236">プリエンプションしきい値テクノロジ</span><span class="sxs-lookup"><span data-stu-id="b5189-236">Preemption-threshold technology</span></span>
* <span data-ttu-id="b5189-237">オプションのタイマー サービス:</span><span class="sxs-lookup"><span data-stu-id="b5189-237">Optional timer services, including:</span></span>
  * <span data-ttu-id="b5189-238">スレッド単位での、オプションのタイム スライス</span><span class="sxs-lookup"><span data-stu-id="b5189-238">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="b5189-239">すべてのブロックに対するオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="b5189-239">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="b5189-240">API でハードウェア タイマー割り込みを要求</span><span class="sxs-lookup"><span data-stu-id="b5189-240">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="b5189-241">実行プロファイル</span><span class="sxs-lookup"><span data-stu-id="b5189-241">Execution profiling</span></span>
* <span data-ttu-id="b5189-242">システムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b5189-242">System-level Trace</span></span>
* <span data-ttu-id="b5189-243">多くの標準に対して認定された安全性</span><span class="sxs-lookup"><span data-stu-id="b5189-243">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="b5189-244">最も多く展開されている RTOS</span><span class="sxs-lookup"><span data-stu-id="b5189-244">Most deployed RTOS</span></span>

<span data-ttu-id="b5189-245">大手 M2M 市場インテリジェンス企業である VDC Research によると、Azure RTOS ThreadX は全世界で 62 億件以上展開されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-245">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="b5189-246">Azure RTOS ThreadX の人気は、その信頼性、品質、サイズ、パフォーマンス、先進的機能、使いやすさ、および全体的な市場投入時間が高く評価されていることの証明と言えます。</span><span class="sxs-lookup"><span data-stu-id="b5189-246">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="b5189-247">*「私たちは、会社の設立以来、ワイヤレスおよび IoT 市場における THREADX の成長の軌跡を見てきましたが、THREADX が幅広い業界で導入されていることに、改めて感心しています。」*</span><span class="sxs-lookup"><span data-stu-id="b5189-247">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="b5189-248">– VDC Research 取締役副社長 Chris Rommel 氏</span><span class="sxs-lookup"><span data-stu-id="b5189-248">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="b5189-249">小さなフットプリント</span><span class="sxs-lookup"><span data-stu-id="b5189-249">Small footprint</span></span>

<span data-ttu-id="b5189-250">Azure RTOS ThreadX では、必要な命令領域が 2 KB、RAM が 1 KB と非常に小さいため、フットプリントを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="b5189-250">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="b5189-251">これは主に、非階層型の picokernel™ アーキテクチャと自動スケーリングによって実現されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-251">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="b5189-252">自動スケーリングとは、アプリケーションで使用されるサービス (およびサポート インフラストラクチャ) だけが、リンク時の最終イメージに含めるられることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b5189-252">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="b5189-253">Azure RTOS ThreadX の典型的なサイズ特性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b5189-253">Here are some typical Azure RTOS ThreadX size characteristics:</span></span>

|<span data-ttu-id="b5189-254">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="b5189-254">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="b5189-255">典型的なサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="b5189-255">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="b5189-256">コア サービス (必須)</span><span class="sxs-lookup"><span data-stu-id="b5189-256">Core Services (Require)</span></span> |<span data-ttu-id="b5189-257">2,000</span><span class="sxs-lookup"><span data-stu-id="b5189-257">2,000</span></span>  |
|<span data-ttu-id="b5189-258">キュー サービス</span><span class="sxs-lookup"><span data-stu-id="b5189-258">Queue Services</span></span>  |<span data-ttu-id="b5189-259">900</span><span class="sxs-lookup"><span data-stu-id="b5189-259">900</span></span>  |
|<span data-ttu-id="b5189-260">イベント フラグ サービス</span><span class="sxs-lookup"><span data-stu-id="b5189-260">Event Flag Services</span></span>  |<span data-ttu-id="b5189-261">900</span><span class="sxs-lookup"><span data-stu-id="b5189-261">900</span></span>  |
|<span data-ttu-id="b5189-262">セマフォ サービス</span><span class="sxs-lookup"><span data-stu-id="b5189-262">Semaphore Services</span></span>  |<span data-ttu-id="b5189-263">450</span><span class="sxs-lookup"><span data-stu-id="b5189-263">450</span></span>  |
|<span data-ttu-id="b5189-264">ミューテックス サービス</span><span class="sxs-lookup"><span data-stu-id="b5189-264">Mutex Services</span></span>  |<span data-ttu-id="b5189-265">1,200</span><span class="sxs-lookup"><span data-stu-id="b5189-265">1,200</span></span>  |
|<span data-ttu-id="b5189-266">ブロック メモリ サービス</span><span class="sxs-lookup"><span data-stu-id="b5189-266">Block Memory Services</span></span>  |<span data-ttu-id="b5189-267">550</span><span class="sxs-lookup"><span data-stu-id="b5189-267">550</span></span>  |
|<span data-ttu-id="b5189-268">バイト メモリ サービス</span><span class="sxs-lookup"><span data-stu-id="b5189-268">Byte Memory Services</span></span>  |<span data-ttu-id="b5189-269">900</span><span class="sxs-lookup"><span data-stu-id="b5189-269">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="b5189-270">高速実行</span><span class="sxs-lookup"><span data-stu-id="b5189-270">Fast execution</span></span>

<span data-ttu-id="b5189-271">Azure RTOS ThreadX は、ほとんどの一般的なプロセッサでサブマイクロ秒のコンテキスト切り替えを実現しており、他の商用 RTOS よりも全体的にかなり高速です。</span><span class="sxs-lookup"><span data-stu-id="b5189-271">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="b5189-272">高速なだけでなく、Azure RTOS ThreadX は高度に決定論的です。</span><span class="sxs-lookup"><span data-stu-id="b5189-272">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="b5189-273">200 スレッドが待機している場合でも、1 スレッドだけの場合でも、同様に高速なパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="b5189-273">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="b5189-274">Azure RTOS ThreadX の典型的なパフォーマンス特性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b5189-274">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="b5189-275">高速ブート: Azure RTOS ThreadX は、120 サイクル未満で起動します。</span><span class="sxs-lookup"><span data-stu-id="b5189-275">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="b5189-276">基本的なエラー チェックの省略 (オプション): Azure RTOS ThreadX の基本的なエラー チェックは、コンパイル時にスキップできます。</span><span class="sxs-lookup"><span data-stu-id="b5189-276">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="b5189-277">これは、アプリケーション コードが検証されていて、各パラメーターに対するエラー チェックがそれ以上必要ない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b5189-277">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="b5189-278">これは、システム全体ではなく、コンパイル単位で実行できる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b5189-278">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="b5189-279">picokernel™ 設計: サービスは相互に階層化されていないため、不要な関数呼び出しによるオーバーヘッドが発生しません。</span><span class="sxs-lookup"><span data-stu-id="b5189-279">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="b5189-280">\*最適化された割り込み処理: プリエンプションが必要でない限り、ISR の開始/終了によって保存/復元されるのは、スクラッチ レジスタだけです。</span><span class="sxs-lookup"><span data-stu-id="b5189-280">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="b5189-281">最適化された API 処理:</span><span class="sxs-lookup"><span data-stu-id="b5189-281">Optimized API Processing:</span></span>

    |<span data-ttu-id="b5189-282">Azure RTOS ThreadX のサービス</span><span class="sxs-lookup"><span data-stu-id="b5189-282">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="b5189-283">サービス時間 (マイクロ秒単位)\*</span><span class="sxs-lookup"><span data-stu-id="b5189-283">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="b5189-284">スレッド中断</span><span class="sxs-lookup"><span data-stu-id="b5189-284">Thread Suspend</span></span>  |<span data-ttu-id="b5189-285">0.6</span><span class="sxs-lookup"><span data-stu-id="b5189-285">0.6</span></span>  |
    |<span data-ttu-id="b5189-286">スレッド再開</span><span class="sxs-lookup"><span data-stu-id="b5189-286">Thread Resume</span></span>  |<span data-ttu-id="b5189-287">0.6</span><span class="sxs-lookup"><span data-stu-id="b5189-287">0.6</span></span>  |
    |<span data-ttu-id="b5189-288">キュー送信</span><span class="sxs-lookup"><span data-stu-id="b5189-288">Queue Send</span></span>  |<span data-ttu-id="b5189-289">0.3</span><span class="sxs-lookup"><span data-stu-id="b5189-289">0.3</span></span>  |
    |<span data-ttu-id="b5189-290">キュー受信</span><span class="sxs-lookup"><span data-stu-id="b5189-290">Queue Receive</span></span>  |<span data-ttu-id="b5189-291">0.3</span><span class="sxs-lookup"><span data-stu-id="b5189-291">0.3</span></span>  |
    |<span data-ttu-id="b5189-292">セマフォの取得</span><span class="sxs-lookup"><span data-stu-id="b5189-292">Get Semaphore</span></span>  |<span data-ttu-id="b5189-293">0.2</span><span class="sxs-lookup"><span data-stu-id="b5189-293">0.2</span></span>  |
    |<span data-ttu-id="b5189-294">セマフォの配置</span><span class="sxs-lookup"><span data-stu-id="b5189-294">Put Semaphore</span></span>  |<span data-ttu-id="b5189-295">0.2</span><span class="sxs-lookup"><span data-stu-id="b5189-295">0.2</span></span>  |
    |<span data-ttu-id="b5189-296">コンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="b5189-296">Context Switch</span></span>  |<span data-ttu-id="b5189-297">0.4</span><span class="sxs-lookup"><span data-stu-id="b5189-297">0.4</span></span>  |
    |<span data-ttu-id="b5189-298">割り込み応答</span><span class="sxs-lookup"><span data-stu-id="b5189-298">Interrupt Response</span></span>  |<span data-ttu-id="b5189-299">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="b5189-299">0.0 – 0.6</span></span>  |

    <span data-ttu-id="b5189-300">\**パフォーマンスの数値は、200MHz で実行されている典型的なプロセッサに基づいたものです*。</span><span class="sxs-lookup"><span data-stu-id="b5189-300">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="b5189-301">TUV と UL による多くの安全性標準による事前認定</span><span class="sxs-lookup"><span data-stu-id="b5189-301">Pre-certified by TUV and UL to many safety standards</span></span>

<span data-ttu-id="b5189-302">Azure RTOS ThreadX と Azure RTOS ThreadX SMP は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-302">Azure RTOS ThreadX and Azure RTOS ThreadX SMP have been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="b5189-303">この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS ThreadX と Azure RTOS ThreadX SMP を使用できることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="b5189-303">The certification confirms that Azure RTOS ThreadX and Azure RTOS ThreadX SMP can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="b5189-304">ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。</span><span class="sxs-lookup"><span data-stu-id="b5189-304">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="b5189-305">工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療機器、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5189-305">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to ensure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="SGS TUV SAAR 認定":::

<span data-ttu-id="b5189-307">Azure RTOS ThreadX と Azure RTOS ThreadX SMP は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-307">Azure RTOS ThreadX and Azure RTOS ThreadX SMP have been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="b5189-308">UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。</span><span class="sxs-lookup"><span data-stu-id="b5189-308">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="UL 認定":::

<span data-ttu-id="b5189-310">TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-310">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="b5189-311">EAL4+ コモン クライテリア セキュリティ認定</span><span class="sxs-lookup"><span data-stu-id="b5189-311">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="b5189-312">Azure RTOS は、EAL4+ のコモン クライテリア セキュリティ認定を達成しました。</span><span class="sxs-lookup"><span data-stu-id="b5189-312">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="b5189-313">評価対象 (TOE) は、Azure RTOS ThreadX、Azure RTOS NetX-Duo、Azure RTOS NetX Secure TLS、および Azure RTOS NetX MQTT です。</span><span class="sxs-lookup"><span data-stu-id="b5189-313">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX-Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="b5189-314">これは、深い埋め込み型センサー、デバイス、エッジ ルーター、およびゲートウェイに必要な最も一般的な IoT プロトコルを表します。</span><span class="sxs-lookup"><span data-stu-id="b5189-314">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="EAL 認定":::

<span data-ttu-id="b5189-316">Azure RTOS セキュリティ認定に使用される IT セキュリティ評価機関は Brightsight BV で、証明機関は SERTIT です。</span><span class="sxs-lookup"><span data-stu-id="b5189-316">The IT Security Evaluation Facility used for the Azure RTOS security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="b5189-317">シンプルで優れた操作性</span><span class="sxs-lookup"><span data-stu-id="b5189-317">Simple, easy to use</span></span>

<span data-ttu-id="b5189-318">Azure RTOS ThreadX は、非常に簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5189-318">Azure RTOS ThreadX is very simple to use.</span></span> <span data-ttu-id="b5189-319">Azure RTOS ThreadX API は直感的で高機能です。</span><span class="sxs-lookup"><span data-stu-id="b5189-319">The Azure RTOS ThreadX API is both intuitive and highly functional.</span></span> <span data-ttu-id="b5189-320">API 名は、略語や、他の RTOS 製品で一般的な大幅に省略された名前ではなく、実際の言葉で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-320">The API names are made of real words and not the alphabet soup of highly abbreviated names that are so common in other RTOS products.</span></span> <span data-ttu-id="b5189-321">すべての Azure RTOS ThreadX API は、先頭に `tx_` が付き、名詞 - 動詞の名前付け規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="b5189-321">All Azure RTOS ThreadX APIs have a leading `tx_` and follow a noun-verb naming convention.</span></span> <span data-ttu-id="b5189-322">さらに、API 全体で機能に一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="b5189-322">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="b5189-323">たとえば、中断を実行するすべての API には、API 用の同様に機能するオプションのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-323">For example, all APIs that suspend have an optional timeout that functions in an identical manner for APIs.</span></span>

<span data-ttu-id="b5189-324">Azure RTOS ThreadX アプリケーションの構築は簡単です。</span><span class="sxs-lookup"><span data-stu-id="b5189-324">Building an Azure RTOS ThreadX application is easy.</span></span> <span data-ttu-id="b5189-325">アプリケーションで必要なことは、*tx_api.h* を含め、main から `tx_kernel_enter` を呼び出し、`tx_application_define` 関数を定義して 1 つのスレッドを作成し、スレッド エントリ ポイント関数を定義し、Azure RTOS ThreadX ライブラリ (通常は *tx.a*) にリンクするということです。</span><span class="sxs-lookup"><span data-stu-id="b5189-325">The application needs to include *tx_api.h*, call `tx_kernel_enter` from main, define the `tx_application_define` function and create one thread, define the thread entry point function, and link against the Azure RTOS ThreadX library (typically *tx.a*).</span></span>

<span data-ttu-id="b5189-326">Azure RTOS ThreadX では、非常に充実した内容のドキュメントが提供されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-326">Azure RTOS ThreadX also boasts the highest caliber of documentation available.</span></span> 

## <a name="advanced-technology"></a><span data-ttu-id="b5189-327">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="b5189-327">Advanced technology</span></span>

<span data-ttu-id="b5189-328">Azure RTOS ThreadX は高度なテクノロジであり、その最も注目すべき機能は、プリエンプションしきい値によるスケジューリングです。</span><span class="sxs-lookup"><span data-stu-id="b5189-328">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="b5189-329">この機能は Azure RTOS ThreadX に固有のものであり、広範な学術研究の対象となってきたものです。</span><span class="sxs-lookup"><span data-stu-id="b5189-329">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="b5189-330">例については、「[How to localize reference titles.docx (プリエンプションしきい値を使った固定優先度タスクのスケジューリング)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)」(コンコーディア大学 Yun Wang、ピッツバーグ大学 Manas Saksena 共著) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5189-330">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="b5189-331">以下に示すのは、Azure RTOS ThreadX の機能です。</span><span class="sxs-lookup"><span data-stu-id="b5189-331">Consider the capabilities of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="b5189-332">完全かつ包括的なマルチタスキング機能</span><span class="sxs-lookup"><span data-stu-id="b5189-332">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="b5189-333">スレッド、アプリケーション タイマー、メッセージ キュー、カウント セマフォ、ミューテックス、イベント フラグ、ブロックおよびバイト メモリ プール</span><span class="sxs-lookup"><span data-stu-id="b5189-333">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="b5189-334">優先度に基づくプリエンプティブ スケジューリング</span><span class="sxs-lookup"><span data-stu-id="b5189-334">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="b5189-335">優先度の柔軟性 – 最大 1024 段階の優先度レベル</span><span class="sxs-lookup"><span data-stu-id="b5189-335">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="b5189-336">協調スケジューリング</span><span class="sxs-lookup"><span data-stu-id="b5189-336">Cooperative Scheduling</span></span>
* <span data-ttu-id="b5189-337">プリエンプションしきい値™ – Azure RTOS ThreadX に固有の機能。コンテキスト切り替えを減らし、柔軟なスケジューリングを保証するのに役立ちます (学術研究に基づく)</span><span class="sxs-lookup"><span data-stu-id="b5189-337">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="b5189-338">Azure RTOS ThreadX モジュールによるメモリ保護</span><span class="sxs-lookup"><span data-stu-id="b5189-338">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="b5189-339">完全に決定論的</span><span class="sxs-lookup"><span data-stu-id="b5189-339">Fully Deterministic</span></span>
* <span data-ttu-id="b5189-340">イベント トレース – 直近の *n* 個のシステム/アプリケーション イベントをキャプチャ</span><span class="sxs-lookup"><span data-stu-id="b5189-340">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="b5189-341">イベント チェーン™ – Azure RTOS ThreadX の各通信または同期オブジェクトに対して、アプリケーション固有の "通知" コールバック関数を登録</span><span class="sxs-lookup"><span data-stu-id="b5189-341">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="b5189-342">メモリ保護のオプションを備えた、Azure RTOS ThreadX モジュール</span><span class="sxs-lookup"><span data-stu-id="b5189-342">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="b5189-343">実行時パフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="b5189-343">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="b5189-344">スレッド再開の数</span><span class="sxs-lookup"><span data-stu-id="b5189-344">Number of thread resumptions</span></span>
  * <span data-ttu-id="b5189-345">スレッド中断の数</span><span class="sxs-lookup"><span data-stu-id="b5189-345">Number of thread suspensions</span></span>
  * <span data-ttu-id="b5189-346">要請されたスレッド プリエンプションの数</span><span class="sxs-lookup"><span data-stu-id="b5189-346">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="b5189-347">非同期スレッド割り込みプリエンプションの数</span><span class="sxs-lookup"><span data-stu-id="b5189-347">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="b5189-348">スレッド優先度逆転の数</span><span class="sxs-lookup"><span data-stu-id="b5189-348">Number of thread priority inversions</span></span>
  * <span data-ttu-id="b5189-349">スレッド放棄の数</span><span class="sxs-lookup"><span data-stu-id="b5189-349">Number of thread relinquishes</span></span>
* <span data-ttu-id="b5189-350">実行プロファイル キット (EPK)</span><span class="sxs-lookup"><span data-stu-id="b5189-350">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="b5189-351">個別の割り込みスタック</span><span class="sxs-lookup"><span data-stu-id="b5189-351">Separate Interrupt Stack</span></span>
* <span data-ttu-id="b5189-352">実行時スタック分析</span><span class="sxs-lookup"><span data-stu-id="b5189-352">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="b5189-353">最適化されたタイマー割り込み処理</span><span class="sxs-lookup"><span data-stu-id="b5189-353">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="b5189-354">マルチコア サポート (AMP と SMP)</span><span class="sxs-lookup"><span data-stu-id="b5189-354">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="b5189-355">標準の Azure RTOS ThreadX は、多くの場合、非対称マルチプロセッシング (AMP) 方式で使用されます。この方式では、Azure RTOS ThreadX とアプリケーション (または Linux) の個別のコピーが各コアで実行され、共有メモリまたは OpenAMP などのプロセッサ間通信メカニズム (Azure RTOS ThreadX では OpenAMP がサポートされています) を介して、相互の通信が行われます。</span><span class="sxs-lookup"><span data-stu-id="b5189-355">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="b5189-356">これは、Azure RTOS ThreadX を使った最も典型的なマルチコア構成であり、アプリケーションがプロセッサを効果的に読み込むことができる場合に、最も効率的に機能します。</span><span class="sxs-lookup"><span data-stu-id="b5189-356">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="b5189-357">プロセッサの読み込みが高度に動的な環境では、次のプロセッサ ファミリで Azure RTOS ThreadX Symetric Multiprocessing (SMP) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5189-357">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="b5189-358">ARM Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="b5189-358">ARM Cortex-Ax</span></span>
* <span data-ttu-id="b5189-359">ARM Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="b5189-359">ARM Cortex-Rx</span></span>
* <span data-ttu-id="b5189-360">ARM Cortex-A5x 64 ビット</span><span class="sxs-lookup"><span data-stu-id="b5189-360">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="b5189-361">MIPS 34K、1004K、interAptiv</span><span class="sxs-lookup"><span data-stu-id="b5189-361">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="b5189-362">PowerPC</span><span class="sxs-lookup"><span data-stu-id="b5189-362">PowerPC</span></span>
* <span data-ttu-id="b5189-363">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="b5189-363">Synopsys ARC HS</span></span>
* <span data-ttu-id="b5189-364">x86</span><span class="sxs-lookup"><span data-stu-id="b5189-364">x86</span></span>

<span data-ttu-id="b5189-365">Azure RTOS ThreadX SMP では、*n* 個のプロセッサ間で動的な負荷分散が実行されるため、すべての Azure RTOS ThreadX リソース (キュー、セマフォ、イベント フラグ、メモリ プールなど) は、コア上の任意のスレッドからアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5189-365">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="b5189-366">Azure RTOS ThreadX SMP では、すべてのコアで完全な Azure RTOS ThreadX API が有効になり、SMP の操作に対して、次の新しい API が導入されます。</span><span class="sxs-lookup"><span data-stu-id="b5189-366">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="b5189-367">Azure RTOS ThreadX モジュールによるメモリ保護</span><span class="sxs-lookup"><span data-stu-id="b5189-367">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="b5189-368">Azure RTOS ThreadX モジュールと呼ばれるアドオン製品を使用すると、1 つ以上のアプリケーション スレッドを "モジュール" にバンドルし、それをターゲットで動的に読み込んで実行 (またはインプレース実行) することができます。</span><span class="sxs-lookup"><span data-stu-id="b5189-368">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="b5189-369">モジュールを使用して、フィールドのアップグレード、バグの修正、およびプログラムのパーティション分割を行えば、大規模なアプリケーションでのメモリ使用を、アクティブなスレッドに必要な分だけに抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="b5189-369">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="b5189-370">モジュールには、Azure RTOS ThreadX 自体から完全に分離されたアドレス空間もあります。</span><span class="sxs-lookup"><span data-stu-id="b5189-370">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="b5189-371">これにより、Azure RTOS ThreadX ではモジュールの周囲にメモリ保護 (MPU または MMU を使用) を配置できるようになっているので、モジュールの外部からの偶発的なアクセスによって、他のソフトウェア コンポーネントが破損するのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="b5189-371">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="b5189-372">市場投入までの時間を最短化</span><span class="sxs-lookup"><span data-stu-id="b5189-372">Fastest time-to-market</span></span>

<span data-ttu-id="b5189-373">Azure RTOS ThreadX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。</span><span class="sxs-lookup"><span data-stu-id="b5189-373">Azure RTOS ThreadX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="b5189-374">その結果、Azure RTOS ThreadX は過去 7 年間、市場投入時間の短縮性において、RTOS 業界をリードしています (Embedded Market Forecasters (EMF) の調査に基づく)。</span><span class="sxs-lookup"><span data-stu-id="b5189-374">As a result, Azure RTOS ThreadX has been the leading time-to-market RTOS for the last seven consecutive years, per the Embedded Market Forecasters (EMF) surveys.</span></span> <span data-ttu-id="b5189-375">この調査によると、Azure RTOS ThreadX を使って設計された製品の 70% が、スケジュールどおりに市場に投入されています。これは、他のどの RTOS よりも優れた結果です。</span><span class="sxs-lookup"><span data-stu-id="b5189-375">The surveys consistently show that 70% of designs using Azure RTOS ThreadX get to market on time – surpassing all other RTOSes.</span></span>

<span data-ttu-id="b5189-376">一貫した市場投入まで時間が利点となる理由は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b5189-376">The following are reasons for our consistent time-to-market advantage:</span></span>

* <span data-ttu-id="b5189-377">高品質のドキュメント</span><span class="sxs-lookup"><span data-stu-id="b5189-377">Quality Documentation</span></span>
* <span data-ttu-id="b5189-378">完全なソース コードを提供</span><span class="sxs-lookup"><span data-stu-id="b5189-378">Complete Source Code Availability</span></span>
* <span data-ttu-id="b5189-379">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="b5189-379">Easy-to-Use API</span></span>
* <span data-ttu-id="b5189-380">包括的かつ高度な機能セット</span><span class="sxs-lookup"><span data-stu-id="b5189-380">Comprehensive and Advanced Feature Set</span></span>
* <span data-ttu-id="b5189-381">広範なサードパーティ製ツールの統合 – 特に IAR の Embedded Workbench™</span><span class="sxs-lookup"><span data-stu-id="b5189-381">Broad 3rd Party Tools Integration – Especially IAR’s Embedded Workbench™</span></span>

## <a name="royalty-free"></a><span data-ttu-id="b5189-382">ロイヤリティ フリー</span><span class="sxs-lookup"><span data-stu-id="b5189-382">Royalty free</span></span>

<span data-ttu-id="b5189-383">ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスのコストもかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="b5189-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="b5189-384">最高品質の完全なソース コード</span><span class="sxs-lookup"><span data-stu-id="b5189-384">Full, highest-quality source code</span></span>

<span data-ttu-id="b5189-385">Azure RTOS ThreadX は開発当初から、完全な C ソースコードで配布される、産業用の RTOS として設計されました。</span><span class="sxs-lookup"><span data-stu-id="b5189-385">From the very beginning, Azure RTOS ThreadX was designed to be an Industrial Grade RTOS, distributed with full C source code.</span></span> <span data-ttu-id="b5189-386">Azure RTOS ThreadX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="b5189-386">Azure RTOS ThreadX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="b5189-387">また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。</span><span class="sxs-lookup"><span data-stu-id="b5189-387">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

<span data-ttu-id="b5189-388">Azure RTOS ThreadX は厳密なコーディング規則に準拠しており、C コードのすべての行に意味のわかるコメントを記述するという要件も設けられていいます。</span><span class="sxs-lookup"><span data-stu-id="b5189-388">Azure RTOS ThreadX conforms to strict coding conventions, including the requirement that every line of C code has a meaningful comment.</span></span> <span data-ttu-id="b5189-389">さらに、Azure RTOS ThreadX のソースは最高クラスの標準で認定を受けています。</span><span class="sxs-lookup"><span data-stu-id="b5189-389">In addition, the Azure RTOS ThreadX source has been certified to the highest standards.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="b5189-390">MISRA 準拠</span><span class="sxs-lookup"><span data-stu-id="b5189-390">MISRA compliant</span></span>

<span data-ttu-id="b5189-391">Azure RTOS ThreadX と Azure RTOS ThreadX SMP のソース コードは、MISRA-C:2004 と MISRA C:2012 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="b5189-391">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="b5189-392">MISRA C は、C プログラミング言語を使用した重要なシステム用の一連のプログラミング ガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="b5189-392">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="b5189-393">元の MISRA C ガイドラインは主に自動車アプリケーションを対象としていましたが、今では MISRA C は安全性が重要な任意のアプリケーションに適用可能なものとして広く認識されています。</span><span class="sxs-lookup"><span data-stu-id="b5189-393">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="b5189-394">Azure RTOS ThreadX は、MISRA-C:2004 と MISRA C:2012 のすべての必要規則と必須規則に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="b5189-394">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 認定":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="b5189-396">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-396">Supports most popular architectures</span></span>

<span data-ttu-id="b5189-397">Azure RTOS ThreadX は、すぐに利用可能で完全なテストとサポートが実現されている、次のような最も一般的な 32/64 ビットのマイクロプロセッサで動作します。</span><span class="sxs-lookup"><span data-stu-id="b5189-397">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="b5189-398">Analog Devices: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="b5189-398">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="b5189-399">Andes Core: RISC-V</span><span class="sxs-lookup"><span data-stu-id="b5189-399">Andes Core: RISC-V</span></span>
* <span data-ttu-id="b5189-400">Ambiqmicro: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="b5189-400">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="b5189-401">ARM: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="b5189-401">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="b5189-402">Cadence: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="b5189-402">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="b5189-403">CEVA: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="b5189-403">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="b5189-404">Cypress: RISC-V</span><span class="sxs-lookup"><span data-stu-id="b5189-404">Cypress: RISC-V</span></span>
* <span data-ttu-id="b5189-405">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="b5189-405">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="b5189-406">Infineon: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="b5189-406">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="b5189-407">Intel および Intel FPGA: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="b5189-407">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="b5189-408">Microchip: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="b5189-408">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="b5189-409">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="b5189-409">Microsemi: RISC-V</span></span>
* <span data-ttu-id="b5189-410">NXP: LPC、ARM7、ARM9、PowerPC、68K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="b5189-410">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="b5189-411">Renesas: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="b5189-411">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="b5189-412">Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="b5189-412">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="b5189-413">Synopsys: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="b5189-413">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="b5189-414">ST: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="b5189-414">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="b5189-415">Tl: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="b5189-415">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="b5189-416">Wave Computing: MIPS32 4K、24K、34K、1004K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="b5189-416">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="b5189-417">Xilinx: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="b5189-417">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="b5189-418">最も一般的なツールをサポート</span><span class="sxs-lookup"><span data-stu-id="b5189-418">Supports most popular tools</span></span>

<span data-ttu-id="b5189-419">Azure RTOS ThreadX では、一般的な埋め込み開発ツールがサポートされています。これには、最も包括的な Azure RTOS ThreadX カーネル認識が利用できる、IAR のEmbedded Workbench™ も含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5189-419">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="b5189-420">その他のツール統合としては、GNU (GCC)、ARM DS-5/uVision®、Green Hills MULTI®、Wind River Workbench™、Imagination Codescape、Renesas e2studio、Metaware SeeCode™、NXP CodeWarrior、Lauterbach TRACE32®、TI Code-Composer Studio、CrossCore などがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b5189-420">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>
