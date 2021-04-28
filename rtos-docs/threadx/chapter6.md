---
title: 第 6 章 - Azure RTOS ThreadX のデモンストレーション システム
description: この章では、すべての Azure RTOS ThreadX プロセッサ サポート パッケージに付属するデモンストレーション システムについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810268"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="c1c13-103">第 6 章 - Azure RTOS ThreadX のデモンストレーション システム</span><span class="sxs-lookup"><span data-stu-id="c1c13-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="c1c13-104">この章では、すべての Azure RTOS ThreadX プロセッサ サポート パッケージに付属するデモンストレーション システムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="c1c13-105">概要</span><span class="sxs-lookup"><span data-stu-id="c1c13-105">Overview</span></span>

<span data-ttu-id="c1c13-106">各 ThreadX 製品ディストリビューションには、サポートされているすべてのマイクロプロセッサで動作するデモンストレーション システムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1c13-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="c1c13-107">このサンプル システムは、ディストリビューション ファイル ***demo_threadx.c*** で定義されており、組み込みのマルチスレッド環境で ThreadX がどのように使用されるかを示すように設計されています。</span><span class="sxs-lookup"><span data-stu-id="c1c13-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="c1c13-108">このデモンストレーションは、初期化、8 つのスレッド、1 つのバイト プール、1 つのブロック プール、1 つのキュー、1 つのセマフォ、1 つのミューテックス、および 1 つのイベント フラグ グループで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="c1c13-109">"*スレッドのスタック サイズを除いて、このデモンストレーション アプリケーションは、ThreadX でサポートされるすべてのプロセッサで同じです。* "</span><span class="sxs-lookup"><span data-stu-id="c1c13-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="c1c13-110">この章の残りの部分で参照されている行番号を含む、***demo_threadx.c*** の完全な記述。</span><span class="sxs-lookup"><span data-stu-id="c1c13-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="c1c13-111">アプリケーションの定義</span><span class="sxs-lookup"><span data-stu-id="c1c13-111">Application Define</span></span>

<span data-ttu-id="c1c13-112">***tx_application_define*** 関数は、基本的な ThreadX の初期化が完了した後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="c1c13-113">これは、スレッド、キュー、セマフォ、ミューテックス、イベント フラグ、メモリ プールなど、最初のシステム リソースすべてを設定する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="c1c13-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="c1c13-114">デモンストレーション システムの ***tx_application_define** _ ("_行番号 60 から 164*") では、デモンストレーション オブジェクトが次の順序で作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="c1c13-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-115">byte_pool_0</span></span>
- <span data-ttu-id="c1c13-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-116">thread_0</span></span>
- <span data-ttu-id="c1c13-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="c1c13-117">thread_1</span></span>
- <span data-ttu-id="c1c13-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="c1c13-118">thread_2</span></span>
- <span data-ttu-id="c1c13-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="c1c13-119">thread_3</span></span>
- <span data-ttu-id="c1c13-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="c1c13-120">thread_4</span></span>
- <span data-ttu-id="c1c13-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="c1c13-121">thread_5</span></span>
- <span data-ttu-id="c1c13-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="c1c13-122">thread_6</span></span>
- <span data-ttu-id="c1c13-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="c1c13-123">thread_7</span></span>
- <span data-ttu-id="c1c13-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-124">queue_0</span></span>
- <span data-ttu-id="c1c13-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-125">semaphore_0</span></span>
- <span data-ttu-id="c1c13-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-126">event_flags_0</span></span>
- <span data-ttu-id="c1c13-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-127">mutex_0</span></span>
- <span data-ttu-id="c1c13-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="c1c13-128">block_pool_0</span></span>

<span data-ttu-id="c1c13-129">このデモンストレーション システムでは、その他の ThreadX オブジェクトは作成されません。</span><span class="sxs-lookup"><span data-stu-id="c1c13-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="c1c13-130">ただし、実際のアプリケーションでは、実行時に実行中のスレッド内でシステム オブジェクトが作成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c1c13-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="c1c13-131">最初の実行</span><span class="sxs-lookup"><span data-stu-id="c1c13-131">Initial Execution</span></span>

<span data-ttu-id="c1c13-132">すべてのスレッドは、**TX_AUTO_START** オプションを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="c1c13-133">これにより、最初の実行の準備が整います。</span><span class="sxs-lookup"><span data-stu-id="c1c13-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="c1c13-134">***tx_application_define*** が完了すると、制御がスレッド スケジューラに移動し、そこから個々のスレッドに移動します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="c1c13-135">スレッドが実行される順序は、その優先順位と作成された順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c1c13-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="c1c13-136">デモンストレーション システムでは、***thread_0*** の優先順位が最も高いため ("*優先順位 1 で作成*")、これが最初に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="c1c13-137">***thread_0*** が中断されると、***thread_5*** が実行され、その後に ***thread_3** _、_*_thread_4_*_、_*_thread_6_*_、 _*_thread_7_**、\*\*\*thread_1**_ の実行が続き、最後に _*_thread_2_*\* が実行されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="c1c13-138">"***thread_3** と **thread_4** の優先順位は同じですが (両方とも優先順位 8 で作成)、\*\*thread_3*\* が最初に実行されます。これは、**thread_4** より前に **thread_3** が作成され、準備ができたためです。同じ優先順位のスレッドは FIFO 方式で実行されます。\* "</span><span class="sxs-lookup"><span data-stu-id="c1c13-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="c1c13-139">スレッド 0</span><span class="sxs-lookup"><span data-stu-id="c1c13-139">Thread 0</span></span>

<span data-ttu-id="c1c13-140">関数 ***thread_0_entry*** により、スレッドのエントリ ポイントがマークされます ("*167 から 190 行目*")。</span><span class="sxs-lookup"><span data-stu-id="c1c13-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="c1c13-141">***Thread_0*** は、デモンストレーション システムで最初に実行されるスレッドです。</span><span class="sxs-lookup"><span data-stu-id="c1c13-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="c1c13-142">その処理は単純です。そのカウンターをインクリメントし、10 タイマー ティックの間スリープ状態になり、***thread_5*** をウェイクアップするイベント フラグを設定した後、そのシーケンスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="c1c13-143">***Thread_0*** は、システムで最も優先順位の高いスレッドです。</span><span class="sxs-lookup"><span data-stu-id="c1c13-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="c1c13-144">要求されたスリープは、期限切れになると、デモンストレーションで実行中の他のスレッドを横取りします。</span><span class="sxs-lookup"><span data-stu-id="c1c13-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="c1c13-145">スレッド 1</span><span class="sxs-lookup"><span data-stu-id="c1c13-145">Thread 1</span></span>

<span data-ttu-id="c1c13-146">関数 ***thread_1_entry** _ により、スレッドのエントリ ポイントがマークされます ("_193 から 216 行目 *")。\*\*\*Thread_1**\* は、デモンストレーション システムで最後から 2 番目に実行されるスレッドです。その処理は、カウンターのインクリメント、***thread_2*** へのメッセージの送信 ("\*\**queue_0\*\*\*\* 経由*")、そのシーケンスの繰り返しで構成されます。_*_queue_0_*_ がいっぱいになるたびに \***thread_1**_ が中断されることに注意してください ("_207 行目\*")。</span><span class="sxs-lookup"><span data-stu-id="c1c13-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="c1c13-147">スレッド 2</span><span class="sxs-lookup"><span data-stu-id="c1c13-147">Thread 2</span></span>

<span data-ttu-id="c1c13-148">関数 ***thread_2_entry*** により、スレッドのエントリ ポイントがマークされます ("*219 から 243 行目*")。</span><span class="sxs-lookup"><span data-stu-id="c1c13-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="c1c13-149">***Thread_2*** は、デモンストレーション システムで最後に実行されるスレッドです。</span><span class="sxs-lookup"><span data-stu-id="c1c13-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="c1c13-150">その処理は、カウンターのインクリメント、***thread_1*** からのメッセージの取得 (***queue_0*** 経由)、そのシーケンスの繰り返しで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="c1c13-151">***thread_2** _ は _*_queue_0_*_ が空になるたびに中断されることに注意してください ("_233 行目*")。</span><span class="sxs-lookup"><span data-stu-id="c1c13-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="c1c13-152">***thread_1** _ と _ *_thread_2_** は、デモンストレーション システムで最も低い優先順位 ("\* 優先順位 16*") を共有していますが、これら "*スレッド 3 および 4\*"</span><span class="sxs-lookup"><span data-stu-id="c1c13-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="c1c13-153">は、ほとんどの場合実行の準備ができている限られた数のスレッドでもあります。</span><span class="sxs-lookup"><span data-stu-id="c1c13-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="c1c13-154">これらは、タイムスライシングを使用して作成される限られた数のスレッドでもあります ("*87 および 93 行目*")。</span><span class="sxs-lookup"><span data-stu-id="c1c13-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="c1c13-155">各スレッドは、他のスレッドが実行される前に最大 4 タイマー ティックの間実行できます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="c1c13-156">スレッド 3 と 4</span><span class="sxs-lookup"><span data-stu-id="c1c13-156">Threads 3 and 4</span></span>

<span data-ttu-id="c1c13-157">関数 ***thread_3_and_4_entry*** により、***thread_3** _ と _ *_thread_4_** の両方のエントリ ポイントがマークされます (246 から 280 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="c1c13-158">どちらのスレッドも優先順位は 8 です。そのため、デモンストレーション システムで 3 番目と 4 番目に実行されるスレッドになります。</span><span class="sxs-lookup"><span data-stu-id="c1c13-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="c1c13-159">各スレッドの処理は同じです。カウンターをインクリメントし、***semaphore_0*** を取得して、2 タイマー ティックの間スリープ状態になり、***semaphore_0*** を解放した後、そのシーケンスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="c1c13-160">***semaphore_0*** が使用できなくなると必ず各スレッドが中断されることに注意してください (264 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="c1c13-161">また、どちらのスレッドでもメイン処理に同じ関数が使用されています。</span><span class="sxs-lookup"><span data-stu-id="c1c13-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="c1c13-162">両方にそれぞれ独自のスタックがあり、C は本来再入可能であるため、これは問題になりません。</span><span class="sxs-lookup"><span data-stu-id="c1c13-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="c1c13-163">各スレッドでは、スレッド入力パラメーターの調査によってどちらであるかが判明します (258 行目)。このパラメーターは、スレッドの作成時に設定されます (102 および 109 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="c1c13-164">"*スレッドの実行中に現在のスレッド ポイントを取得し、それを制御ブロックのアドレスと比較してスレッド ID を判定することも理にかなっています。* "</span><span class="sxs-lookup"><span data-stu-id="c1c13-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="c1c13-165">スレッド 5</span><span class="sxs-lookup"><span data-stu-id="c1c13-165">Thread 5</span></span>

<span data-ttu-id="c1c13-166">関数 ***thread_5_entry*** により、スレッドのエントリ ポイントがマークされます (283 から 305 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="c1c13-167">***Thread_5*** は、デモンストレーション システムで 2 番目に実行されるスレッドです。</span><span class="sxs-lookup"><span data-stu-id="c1c13-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="c1c13-168">その処理は、カウンターのインクリメント、***thread_0*** からのイベント フラグの取得 (***event_flags_0*** 経由)、そのシーケンスの繰り返しで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="c1c13-169">***event_flags_0*** のイベント フラグが使用できなくなると必ず ***thread_5*** が中断されることに注意してください (298 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="c1c13-170">スレッド 6 と 7</span><span class="sxs-lookup"><span data-stu-id="c1c13-170">Threads 6 and 7</span></span>

<span data-ttu-id="c1c13-171">関数 ***thread_6_and_7_entry*** により、***thread_6** _ と _ *_thread_7_** 両方のエントリ ポイントがマークされます (307 から 358 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="c1c13-172">どちらのスレッドも優先順位は 8 です。そのため、デモンストレーション システムで 5 番目と 6 番目に実行されるスレッドになります。</span><span class="sxs-lookup"><span data-stu-id="c1c13-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="c1c13-173">各スレッドの処理は同じです。カウンターをインクリメントし、***mutex_0*** を取得して、2 タイマー ティックの間スリープ状態になり、***mutex_0*** を解放した後、そのシーケンスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="c1c13-174">***mutex_0*** が使用できなくなると必ず各スレッドが中断されることに注意してください (325 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="c1c13-175">また、どちらのスレッドでもメイン処理に同じ関数が使用されています。</span><span class="sxs-lookup"><span data-stu-id="c1c13-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="c1c13-176">両方にそれぞれ独自のスタックがあり、C は本来再入可能であるため、これは問題になりません。</span><span class="sxs-lookup"><span data-stu-id="c1c13-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="c1c13-177">各スレッドでは、スレッド入力パラメーターの調査によってどちらであるかが判明します (319 行目)。このパラメーターは、スレッドの作成時に設定されます (126 および 133 行目)。</span><span class="sxs-lookup"><span data-stu-id="c1c13-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="c1c13-178">デモンストレーションの観察</span><span class="sxs-lookup"><span data-stu-id="c1c13-178">Observing the Demonstration</span></span>

<span data-ttu-id="c1c13-179">デモンストレーションのスレッドは、それぞれ独自の一意のカウンターをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="c1c13-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="c1c13-180">デモの動作を確認するために、次のカウンターを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="c1c13-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="c1c13-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-181">thread_0_counter</span></span>
- <span data-ttu-id="c1c13-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-182">thread_1_counter</span></span>
- <span data-ttu-id="c1c13-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-183">thread_2_counter</span></span>
- <span data-ttu-id="c1c13-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-184">thread_3_counter</span></span>
- <span data-ttu-id="c1c13-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-185">thread_4_counter</span></span>
- <span data-ttu-id="c1c13-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-186">thread_5_counter</span></span>
- <span data-ttu-id="c1c13-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-187">thread_6_counter</span></span>
- <span data-ttu-id="c1c13-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="c1c13-188">thread_7_counter</span></span>

<span data-ttu-id="c1c13-189">これらの各カウンターは、デモンストレーションの実行に応じて増加し続けます。そのうち、***thread_1_counter** _ と _ *_thread_2_counter_** は最も速い速度で増加します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="c1c13-190">ディストリビューション ファイル: demo_threadx.c</span><span class="sxs-lookup"><span data-stu-id="c1c13-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="c1c13-191">このセクションでは、この章全体で参照されている行番号を含む、***demo_threadx.c*** の完全な記述を示します。</span><span class="sxs-lookup"><span data-stu-id="c1c13-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
void thread_0_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {

        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}


void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}


void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;


    /* This function is executed from thread 3 and thread 4. As the loop
    below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;


    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
            &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
        below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
