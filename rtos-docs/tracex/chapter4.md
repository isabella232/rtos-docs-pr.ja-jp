---
title: 第 4 章 - Azure RTOS TraceX のパフォーマンス分析
description: この章では、Azure RTOS TraceX のパフォーマンス分析ツールについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812353"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a><span data-ttu-id="63a83-103">第 4 章 - Azure RTOS TraceX のパフォーマンス分析</span><span class="sxs-lookup"><span data-stu-id="63a83-103">Chapter 4 - Azure RTOS TraceX performance analysis</span></span>

<span data-ttu-id="63a83-104">この章では、Azure RTOS TraceX のパフォーマンス分析ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="63a83-104">This chapter describes the Azure RTOS TraceX performance analysis tool:</span></span>

## <a name="performance-analysis"></a><span data-ttu-id="63a83-105">パフォーマンス分析</span><span class="sxs-lookup"><span data-stu-id="63a83-105">Performance Analysis</span></span>

<span data-ttu-id="63a83-106">TraceX には、トレース ファイルのパフォーマンス分析機能が組み込みで用意されています。</span><span class="sxs-lookup"><span data-stu-id="63a83-106">TraceX provides built-in performance analysis of trace files.</span></span> <span data-ttu-id="63a83-107">*実行プロファイル*、*人気のあるサービス*、*スレッド スタックの使用状況*、および各種 *パフォーマンス統計* (FileX および NetX の統計を含む) などの情報を、簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="63a83-107">Information such as the *execution profile*, *popular services*, *thread stack usage*, and various *performance statistics,* including FileX and NetX statistics *,* are readily available.</span></span> <span data-ttu-id="63a83-108">これらの情報は、***[表示]*** メニュー項目から確認できます。</span><span class="sxs-lookup"><span data-stu-id="63a83-108">This information is available via the ***View*** menu item.</span></span> 


## <a name="execution-profile"></a><span data-ttu-id="63a83-109">実行プロファイル</span><span class="sxs-lookup"><span data-stu-id="63a83-109">Execution Profile</span></span>

<span data-ttu-id="63a83-110">***[実行プロファイルの生成]** _ ボタンまたは _*_[表示] - [実行プロファイル]_\*_ を選択すると、現在読み込まれているトレース ファイルの TraceX 実行プロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-110">Selecting the ***Generate Execution Profile** _ button or _*_View -Execution Profile_\*_ presents the TraceX execution profile for the currently loaded trace file.</span></span> <span data-ttu-id="63a83-111">_*図 19*\* に示すのは、サンプルの ThreadX デモ トレースに関連付けられた実行プロファイルです。</span><span class="sxs-lookup"><span data-stu-id="63a83-111">The execution profile associated with the sample ThreadX demonstration trace is shown in _\*Figure 19\*\*.</span></span>

![サンプルの ThreadX デモ トレースに関連付けられた実行プロファイルのスクリーンショット。](./media/user-guide/execution_profile.png)

<span data-ttu-id="63a83-113">**図 19**</span><span class="sxs-lookup"><span data-stu-id="63a83-113">**FIGURE 19**</span></span>

<span data-ttu-id="63a83-114">**図 19** の例では、処理時間の約 45% が "**_スレッド 2_*_" 内にあり、処理時間の約 51% が "_*_スレッド 1_**" 内にあります。トレースの大部分ではこれらのスレッドによってメッセージが送受信されているので、これは理にかなった値と言えます。</span><span class="sxs-lookup"><span data-stu-id="63a83-114">The example shown in **Figure 19** indicates that nearly 45% of the processing time is inside of **_thread 2_*_ and nearly 51% of the processing time is inside of _*_thread 1_** This is logical since the bulk of the trace shows these threads sending and receiving messages.</span></span> <span data-ttu-id="63a83-115">この例では、残りの実行コンテキストでの実行時間はごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="63a83-115">The remaining execution contexts have only a small amount of execution time in this example.</span></span>

## <a name="popular-services"></a><span data-ttu-id="63a83-116">人気のあるサービス</span><span class="sxs-lookup"><span data-stu-id="63a83-116">Popular Services</span></span>

<span data-ttu-id="63a83-117">\***[表示] -> [人気のあるサービス]** _ を選択すると、現在読み込まれているトレース ファイル内の人気のあるサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-117">Selecting \***View ->Popular Services** _ presents the popular services in the currently loaded trace file.</span></span> <span data-ttu-id="63a83-118">既定では、この情報はシステム全体を対象に表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-118">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="63a83-119">ただし、特定のスレッドを対象にして人気のサービスを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="63a83-119">However, the popular services for specific threads are also available.</span></span> <span data-ttu-id="63a83-120">*図 20*\* に示すのは、サンプルの ThreadX デモ トレースの人気サービスです。</span><span class="sxs-lookup"><span data-stu-id="63a83-120">The popular services in the sample ThreadX demonstration trace are shown in _\*Figure 20\*\*.</span></span>

![サンプルの ThreadX デモ トレースの人気サービスのスクリーンショット。](./media/user-guide/popular_services.png)

<span data-ttu-id="63a83-122">**図 20**</span><span class="sxs-lookup"><span data-stu-id="63a83-122">**FIGURE 20**</span></span>

<span data-ttu-id="63a83-123">**図 20** の例では、**_tx_queue_send_*_ と _*_tx_queue_receive_** が、このトレースで最もよく使用されている 2 つのサービスであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="63a83-123">The example shown in **Figure 20** indicates that **_tx_queue_send_*_ and _*_tx_queue_receive_** are the two most popular services in this trace.</span></span> <span data-ttu-id="63a83-124">これは、このトレースのキャプチャ元である標準の ThreadX デモの動作と一致しています。</span><span class="sxs-lookup"><span data-stu-id="63a83-124">This is consistent with the behavior of the standard ThreadX demonstration from which this trace was captured.</span></span>

<span data-ttu-id="63a83-125">このウィンドウの上部にあるドロップダウン リストを使用すると、特定のスレッドを選択してこの分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="63a83-125">Specific threads can be selected for this analysis by using the drop down selection list at the top of this window.</span></span> <span data-ttu-id="63a83-126">**図 21** は、"**_スレッド 3_**" を対象にしてこの分析を行った場合の結果です。</span><span class="sxs-lookup"><span data-stu-id="63a83-126">**Figure 21** shows this analysis for **_thread 3_**.</span></span>

![TraceX の人気サービス分析のスクリーンショット。](./media/user-guide/popular_services_thread3.png)

<span data-ttu-id="63a83-128">**図 21**</span><span class="sxs-lookup"><span data-stu-id="63a83-128">**FIGURE 21**</span></span>

## <a name="thread-stack-usage-analysis-for-thread-3"></a><span data-ttu-id="63a83-129">スレッド スタックの使用状況</span><span class="sxs-lookup"><span data-stu-id="63a83-129">Thread Stack Usage</span></span> ![スレッド 3 の分析。](./media/user-guide/screen_shot_17.png)

<span data-ttu-id="63a83-131">***[スレッド スタック使用状況の生成]** _ ボタンまたは _*_[表示] -> [スレッド スタックの使用状況]_\*_ を選択すると、トレース ファイル内の各スレッドのスタック使用状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-131">Selecting the ***Generate Thread Stack Usage** _ button or _*_View -> Thread Stack Usage_\*_ presents the stack usage for each thread in the trace file.</span></span> <span data-ttu-id="63a83-132">これは、ファイル内のトレース エントリの多くに現在のスレッド スタック ポインターを含んでいる ThreadX によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-132">This is accomplished by ThreadX including the current thread stack pointer in many of the trace entries in the file.</span></span> <span data-ttu-id="63a83-133">スタックの使用率が100% の場合、それはスタックがオーバーフローした状態であり、アプリケーションで修正する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="63a83-133">A stack usage of 100% indicates the stack has overflowed and must be corrected in the application.</span></span> <span data-ttu-id="63a83-134">そのトレース ファイル内でスレッドの実行がない場合、そのスレッドのスタック使用率は 0% と表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-134">If there is no thread execution within this trace file, the stack usage for that thread is shown at 0%.</span></span> <span data-ttu-id="63a83-135">_\* 図 22\*\* に示すのは、サンプルの ThreadX デモ トレースのスレッド スタック使用状況です。</span><span class="sxs-lookup"><span data-stu-id="63a83-135">The thread stack usage in the sample ThreadX demonstration trace is shown in _\*Figure 22\*\*.</span></span>

![TraceX のスレッド スタック使用状況のスクリーンショット。](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="63a83-137">**図 22**</span><span class="sxs-lookup"><span data-stu-id="63a83-137">**FIGURE 22**</span></span>

<span data-ttu-id="63a83-138">**図 22** の例では、このトレースのほとんどのスレッドのスタック使用率が、9% から 12% であると示されています。</span><span class="sxs-lookup"><span data-stu-id="63a83-138">The example shown in **Figure 22** indicates that most threads in this trace have between 9% and 12% stack usage.</span></span>

## <a name="performance-statistics"></a><span data-ttu-id="63a83-139">パフォーマンス統計</span><span class="sxs-lookup"><span data-stu-id="63a83-139">Performance Statistics</span></span>

<span data-ttu-id="63a83-140">***[パフォーマンス統計の生成]** _ ボタンまたは _ *_[表示] -> [パフォーマンス統計]_** を選択すると、現在読み込まれているトレース ファイルのパフォーマンス統計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-140">Selecting the ***Generate Performance Statistics** _ button or _ *_View -> Performance Statistics_** presents the performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="63a83-141">既定では、この情報はシステム全体を対象に表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-141">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="63a83-142">ただし、特定のスレッドを対象にパフォーマンス統計を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="63a83-142">However, the performance statistics are also available for each specific thread.</span></span>

<span data-ttu-id="63a83-143">**図 23** に示すのは、サンプルの ThreadX デモ トレースのパフォーマンス統計です。</span><span class="sxs-lookup"><span data-stu-id="63a83-143">The performance statistics of the sample ThreadX demonstration trace are shown in **Figure 23**.</span></span>

![TraceX のパフォーマンス統計のスクリーンショット。](./media/user-guide/performance_statistics.png)

<span data-ttu-id="63a83-145">**図 23**</span><span class="sxs-lookup"><span data-stu-id="63a83-145">**FIGURE 23**</span></span>

<span data-ttu-id="63a83-146">**図 23** の例の場合、このトレース ファイルには、18 件のコンテキスト切り替え、5 件のスレッド プリエンプション、16 件のスレッド保留、19 件のスレッド再開、および 3 件の割り込みがあると表示されています。</span><span class="sxs-lookup"><span data-stu-id="63a83-146">The example shown in **Figure 23** indicates that there were 18 context switches in this trace file, as well as five thread preemptions, 16 thread suspensions, 19 thread resumptions, and three interrupts.</span></span> <span data-ttu-id="63a83-147">このトレース ファイルに優先度逆転は見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="63a83-147">There were no priority inversions found in this trace file.</span></span> <span data-ttu-id="63a83-148">優先度逆転には、"*決定論的*" と "*非決定論的*" の 2 つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="63a83-148">Notice there are two categories of priority inversions, namely, *deterministic* and *nondeterministic*.</span></span> <span data-ttu-id="63a83-149">決定論的な優先度逆転とは、優先度の低いスレッドによって所有されているミューテックスでスレッドがブロックされる優先度逆転のことです。</span><span class="sxs-lookup"><span data-stu-id="63a83-149">Deterministic priority inversions are priority inversion in which a thread is blocked on a mutex owned by a lower priority thread.</span></span> <span data-ttu-id="63a83-150">非決定論的な優先度逆転とは、決定論的な優先度逆転の最中に、別の優先度の低いスレッドが実行される状況のことです。</span><span class="sxs-lookup"><span data-stu-id="63a83-150">An nondeterministic priority inversion is where a different lower priority thread runs during a deterministic priority inversion.</span></span> <span data-ttu-id="63a83-151">後者の場合、アプリケーションで予期しないタイミング動作が発生する可能性があるため、注意深く調査する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63a83-151">The later can cause unforeseen timing behavior in the application and should be studied carefully.</span></span>

## <a name="filex-statistics"></a><span data-ttu-id="63a83-152">FileX 統計</span><span class="sxs-lookup"><span data-stu-id="63a83-152">FileX Statistics</span></span>

<span data-ttu-id="63a83-153">\***[表示] -> [FileX 統計]** _ を選択すると、現在読み込まれているトレース ファイルの FileX パフォーマンス統計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-153">Selecting \***View -> FileX Statistics** _ presents the FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="63a83-154">この情報は、システム全体 (開いているすべてのメディア オブジェクト) を対象に表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-154">This information is displayed for the entire system, on all opened ../media objects.</span></span> <span data-ttu-id="63a83-155">_*図 24*\* に示すのは、サンプルの FileX デモ トレースのパフォーマンス統計です。</span><span class="sxs-lookup"><span data-stu-id="63a83-155">The performance statistics of the sample FileX demonstration trace are shown in _\*Figure 24\*\*.</span></span>

![FileX 統計のスクリーンショット。](./media/user-guide/filex_statistics.png)

<span data-ttu-id="63a83-157">**図 24**</span><span class="sxs-lookup"><span data-stu-id="63a83-157">**FIGURE 24**</span></span>

<span data-ttu-id="63a83-158">**図 27** の例では、19 件のメディア オープン、19 件のメディア クローズ、19 件のメディア フラッシュ、18 件のディレクトリ読み取り、19 件のディレクトリ書き込み、および 18 件のディレクトリ キャッシュ ミスがあったと表示されています。</span><span class="sxs-lookup"><span data-stu-id="63a83-158">The example shown in **Figure 27** indicates there were 19 ../media opens, 19 ../media closes, 19 ../media flushes, 18 directory reads, 19 directory writes, and 18 directory cache misses.</span></span> <span data-ttu-id="63a83-159">統計ウィンドウで下にスクロールすると、その他の情報も確認できます。</span><span class="sxs-lookup"><span data-stu-id="63a83-159">Additonal information can be viewed by scrolling down in the statistics window.</span></span>

## <a name="netx-statistics"></a><span data-ttu-id="63a83-160">NetX 統計</span><span class="sxs-lookup"><span data-stu-id="63a83-160">NetX Statistics</span></span>

<span data-ttu-id="63a83-161">\***[表示] - [NetX 統計]** _ を選択すると、現在読み込まれているトレース ファイルの NetX パフォーマンス統計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-161">Selecting \***View -NetX Statistics** _ presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="63a83-162">この情報は、システム全体を対象に表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-162">This information is displayed for the entire system.</span></span> <span data-ttu-id="63a83-163">_*図 25*\* に示すのは、サンプルの NetX デモ トレースのパフォーマンス統計です。</span><span class="sxs-lookup"><span data-stu-id="63a83-163">The performance statistics of the sample NetX demonstration trace are shown in _\*Figure 25\*\*.</span></span>

![NetX 統計のスクリーンショット。](./media/user-guide/netx_statistics.png)

<span data-ttu-id="63a83-165">**図 25**</span><span class="sxs-lookup"><span data-stu-id="63a83-165">**FIGURE 25**</span></span>

<span data-ttu-id="63a83-166">**図 25** の例では、ARP、Ping、および UDP イベントはなく、30 件の IP パケット送信、1368 件の IP バイト送信、30 件の IP パケット受信、および 1360 件の IP バイト受信があったと表示されています。</span><span class="sxs-lookup"><span data-stu-id="63a83-166">The example shown in **Figure 25** indicates there were no ARP, Ping, or UDP events, but there were 30 IP packets sent, 1,368 IP bytes sent, 30 IP packets received, and 1,360 IP bytes received.</span></span>

## <a name="trace-file-information"></a><span data-ttu-id="63a83-167">トレース ファイル情報</span><span class="sxs-lookup"><span data-stu-id="63a83-167">Trace File Information</span></span>

<span data-ttu-id="63a83-168">\***[表示] -> [トレース ファイル情報]** _ を選択すると、開いているトレース ファイルに関する、いくつかの基本的な情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-168">Selecting \***View -> Trace File Information** _ presents some basic information about the opened trace file.</span></span> <span data-ttu-id="63a83-169">この情報には、ファイルのバイト順、タイム ソースのサイズ、各オブジェクト名の最大バイト数、およびすべてのトレース ファイル ポインターのベース アドレスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="63a83-169">This information includes the byte order of the file, size of the time source, maximum number of bytes for each object name, and the base address of all trace file pointers.</span></span> <span data-ttu-id="63a83-170">_ *図 26*\* に示すのは、標準の **_demo_threadx.trx_** トレース ファイルのトレース ファイル情報です。</span><span class="sxs-lookup"><span data-stu-id="63a83-170">_ *Figure 26*\* shows the trace file information for the standard **_demo_threadx.trx_** trace file.</span></span>

![TraceX のファイル情報のスクリーンショット。](./media/user-guide/trace_file_info.png)

<span data-ttu-id="63a83-172">**図 26**</span><span class="sxs-lookup"><span data-stu-id="63a83-172">**FIGURE 26**</span></span>

## <a name="raw-trace-dump"></a><span data-ttu-id="63a83-173">生のトレース ダンプ</span><span class="sxs-lookup"><span data-stu-id="63a83-173">Raw Trace Dump</span></span>

<span data-ttu-id="63a83-174">\***[表示] -> [生のトレース ダンプ]** _ を選択すると、生のトレース ダンプを含んだファイルを指定するダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-174">Selecting \***View -> Raw Trace Dump** _ presents a dialog to name the file containing the raw trace dump.</span></span> <span data-ttu-id="63a83-175">ファイル名とパスを入力すると、TraceX によって生のトレース ファイルがテキスト形式で作成され、_*_notepad.exe_*_ が起動してファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63a83-175">After the file name and path are entered, TraceX builds the raw trace file in text format and launches _*_notepad.exe_*_ to display it.</span></span> <span data-ttu-id="63a83-176">_ *図 27*\* に示すのは、標準の **_demo_threadx.trx_** トレース ファイルの生のトレース ファイル ダンプです。</span><span class="sxs-lookup"><span data-stu-id="63a83-176">_ *Figure 27*\* shows the raw trace file dump for the standard **_demo_threadx.trx_** trace file.</span></span>

![生のトレース ダンプのスクリーンショット。](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="63a83-178">**図 27**</span><span class="sxs-lookup"><span data-stu-id="63a83-178">**FIGURE 27**</span></span>
