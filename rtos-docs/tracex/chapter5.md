---
title: 第 5 章 - トレース バッファーの生成
description: この章では、Azure RTOS TraceX イベント バッファーを構築する方法について説明します。また、基になるバッファーの形式についても説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812338"
---
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="d231b-103">第 5 章 - トレース バッファーの生成</span><span class="sxs-lookup"><span data-stu-id="d231b-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="d231b-104">この章では、Azure RTOS TraceX イベント バッファーを構築する方法について説明します。また、基になるバッファーの形式についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d231b-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="d231b-105">ThreadX イベント トレースのサポート</span><span class="sxs-lookup"><span data-stu-id="d231b-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="d231b-106">ThreadX には、すべての ThreadX サービス、スレッド状態の変更、およびユーザー定義イベントに対する組み込みのイベント トレース サポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="d231b-107">ThreadX イベント トレース機能は、主に、アプリケーションの最後の "n" 件のアクティビティを分析する事後分析ツールとして設計されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="d231b-108">この情報から、開発者は、問題や最適化の対象となる可能性のあるターゲットを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d231b-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="d231b-109">TraceX では、ThreadX によって作成されたイベント トレース バッファーをグラフィカルに表示します。</span><span class="sxs-lookup"><span data-stu-id="d231b-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="d231b-110">次に、バッファーの作成方法と、基になるバッファーの形式について説明します。</span><span class="sxs-lookup"><span data-stu-id="d231b-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="d231b-111">イベント トレースの有効化</span><span class="sxs-lookup"><span data-stu-id="d231b-111">Enabling Event Trace</span></span>

<span data-ttu-id="d231b-112">イベント トレースを有効にするには、タイムスタンプ定数を定義し、**TX_ENABLE_EVENT_TRACE** が定義された ThreadX ライブラリをビルドし、**tx_trace_enable** 関数を呼び出してトレースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d231b-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="d231b-113">タイムスタンプ定数の定義</span><span class="sxs-lookup"><span data-stu-id="d231b-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="d231b-114">タイムスタンプ定数は、イベント トレース エントリで使用されるタイムスタンプを開発者が制御できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="d231b-115">2 つのタイムスタンプ定数とその既定値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d231b-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="d231b-116">上記の定数は **tx_port.h** で定義され、各イベントで 1 つずつ増加する "偽の" タイムスタンプを作成します。</span><span class="sxs-lookup"><span data-stu-id="d231b-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="d231b-117">実際のタイムスタンプ定義の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d231b-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="d231b-118">上記の定数は、アドレス 0x13000004 を読み取ることによって取得される 32 ビット タイマーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d231b-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="d231b-119">ほとんどのアプリケーション固有のタイムスタンプは、同様の方法でセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="d231b-120">トレース バッファーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="d231b-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="d231b-121">TraceX では、ホスト上でバイナリ、Intel HEX、または Motorola S-Record ファイル形式のトレース バッファーが必要です。</span><span class="sxs-lookup"><span data-stu-id="d231b-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="d231b-122">これを実現する最も簡単な方法は、ターゲットを停止し、***tx_trace_enable*** 関数に指定したメモリ領域をホスト上のファイルにダンプするようにデバッガーに指示することです。</span><span class="sxs-lookup"><span data-stu-id="d231b-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="d231b-123">***トレース収集コード自体でターゲットを停止しないように注意してください。これにより、無効なトレース情報が生成される可能性があります。プログラムが ThreadX 内で停止した場合、トレース バッファーをダンプする前に、トレース挿入マクロをステップ オーバーすることをお勧めします。***</span><span class="sxs-lookup"><span data-stu-id="d231b-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-124">*付録 D では、さまざまな開発ツール内からトレース バッファーをダンプする方法を示します。*</span><span class="sxs-lookup"><span data-stu-id="d231b-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="d231b-125">拡張イベント トレース API</span><span class="sxs-lookup"><span data-stu-id="d231b-125">Extended Event Trace API</span></span>

<span data-ttu-id="d231b-126">**TX_ENABLE_EVENT_TRACE** が定義された状態で ThreadX をビルドすると、アプリケーションで次の新しいイベント トレース API を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d231b-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="d231b-127">tx_trace_enable: *イベントのトレースを有効にする*</span><span class="sxs-lookup"><span data-stu-id="d231b-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="d231b-128">tx_trace_event_filter: *指定されたイベントをフィルター処理する*</span><span class="sxs-lookup"><span data-stu-id="d231b-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="d231b-129">tx_trace_event_unfilter: *指定されたイベントをフィルター解除する*</span><span class="sxs-lookup"><span data-stu-id="d231b-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="d231b-130">tx_trace_disable: *イベントのトレースを無効にする*</span><span class="sxs-lookup"><span data-stu-id="d231b-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="d231b-131">tx_trace_isr_enter_insert: *ISR トレース開始イベントを挿入する*</span><span class="sxs-lookup"><span data-stu-id="d231b-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="d231b-132">tx_trace_isr_exit_insert: *ISR トレース終了イベントを挿入する*</span><span class="sxs-lookup"><span data-stu-id="d231b-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="d231b-133">tx_trace_buffer_full_notify: *トレース バッファーの完全なアプリケーション コールバックを登録する*</span><span class="sxs-lookup"><span data-stu-id="d231b-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="d231b-134">tx_trace_user_event_insert: *ユーザー イベントを挿入する*</span><span class="sxs-lookup"><span data-stu-id="d231b-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="d231b-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="d231b-135">tx_trace_enable</span></span>

<span data-ttu-id="d231b-136">イベントのトレースを有効にする</span><span class="sxs-lookup"><span data-stu-id="d231b-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-137">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="d231b-138">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-138">Description</span></span>
<span data-ttu-id="d231b-139">このサービスにより、ThreadX 内のイベント トレースが有効になります。</span><span class="sxs-lookup"><span data-stu-id="d231b-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="d231b-140">アプリケーションでは、トレース バッファーと ThreadX オブジェクトの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d231b-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-141">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-142">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-142">Input Parameters</span></span>

- <span data-ttu-id="d231b-143">**trace_buffer_start**: ユーザーが指定したトレース バッファーの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d231b-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="d231b-144">**trace_buffer_size**: トレース バッファーのメモリ内の合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="d231b-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="d231b-145">トレース バッファーが大きいほど、格納できるエントリが増えます。</span><span class="sxs-lookup"><span data-stu-id="d231b-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="d231b-146">**registry_entries**: トレース レジストリに保持するアプリケーション ThreadX オブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="d231b-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="d231b-147">レジストリは、オブジェクトのアドレスとオブジェクト名を関連付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d231b-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="d231b-148">これは、GUI トレース分析ツールで非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="d231b-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="d231b-149">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-149">Return Values</span></span>

- <span data-ttu-id="d231b-150">**TX_SUCCESS** (0x00) イベント トレースの有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d231b-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="d231b-151">**TX_SIZE_ERROR** (0x05) 指定されたトレース バッファー サイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="d231b-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="d231b-152">トレース ヘッダー、オブジェクト レジストリ、および少なくとも 1 つのトレース エントリに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="d231b-153">**TX_NOT_DONE** (0x20) イベント トレースは既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d231b-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="d231b-154">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="d231b-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-155">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-155">Allowed From</span></span>

<span data-ttu-id="d231b-156">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d231b-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-157">例</span><span class="sxs-lookup"><span data-stu-id="d231b-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-158">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-158">See Also</span></span>

<span data-ttu-id="d231b-159">tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="d231b-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="d231b-160">tx_trace_event_filter</span></span>

<span data-ttu-id="d231b-161">指定されたイベントをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="d231b-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-162">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="d231b-163">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-163">Description</span></span>

<span data-ttu-id="d231b-164">このサービスでは、指定されたイベントをフィルター処理して、アクティブなトレース バッファーに挿入されないようにします。</span><span class="sxs-lookup"><span data-stu-id="d231b-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="d231b-165">既定では、*tx_trace_enable* が呼び出された後にはイベントはフィルター処理されません。</span><span class="sxs-lookup"><span data-stu-id="d231b-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-166">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-167">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-167">Input Parameters</span></span>

- <span data-ttu-id="d231b-168">**event_filter_bits**: フィルター処理するイベントに対応するビット。</span><span class="sxs-lookup"><span data-stu-id="d231b-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="d231b-169">複数のイベントをフィルター処理するには、適切な定数の論理和を指定します。</span><span class="sxs-lookup"><span data-stu-id="d231b-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="d231b-170">この変数の有効な定数は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-170">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="d231b-171">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-171">Return Values</span></span>

- <span data-ttu-id="d231b-172">**TX_SUCCESS** (0x00) イベントのフィルター処理に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d231b-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="d231b-173">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="d231b-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-174">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-174">Allowed From</span></span>

<span data-ttu-id="d231b-175">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d231b-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-176">例</span><span class="sxs-lookup"><span data-stu-id="d231b-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-177">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-177">See Also</span></span>

<span data-ttu-id="d231b-178">tx_trace_enable、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="d231b-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="d231b-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="d231b-180">指定されたイベントをフィルター解除する</span><span class="sxs-lookup"><span data-stu-id="d231b-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-181">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="d231b-182">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-182">Description</span></span>

<span data-ttu-id="d231b-183">このサービスでは、指定されたイベントをフィルター解除して、アクティブなトレース バッファーに挿入されるようにします。</span><span class="sxs-lookup"><span data-stu-id="d231b-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-184">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-185">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-185">Input Parameters</span></span>

- <span data-ttu-id="d231b-186">**event_unfilter_bits**: フィルター解除するイベントに対応するビット。</span><span class="sxs-lookup"><span data-stu-id="d231b-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="d231b-187">複数のイベントをフィルター解除するには、適切な定数の論理和を指定します。</span><span class="sxs-lookup"><span data-stu-id="d231b-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="d231b-188">この変数の有効な定数は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-188">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="d231b-189">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-189">Return Values</span></span>

- <span data-ttu-id="d231b-190">**TX_SUCCESS** (0x00) イベントのフィルター解除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d231b-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="d231b-191">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="d231b-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-192">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-192">Allowed From</span></span>

<span data-ttu-id="d231b-193">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d231b-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-194">例</span><span class="sxs-lookup"><span data-stu-id="d231b-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-195">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-195">See Also</span></span>

<span data-ttu-id="d231b-196">tx_trace_enable、tx_trace_event_filter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="d231b-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="d231b-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="d231b-198">イベントのトレースを無効にする</span><span class="sxs-lookup"><span data-stu-id="d231b-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-199">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="d231b-200">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-200">Description</span></span>

<span data-ttu-id="d231b-201">このサービスにより、ThreadX 内のイベント トレースが無効になります。</span><span class="sxs-lookup"><span data-stu-id="d231b-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="d231b-202">これは、アプリケーションで現在のイベント トレース バッファーをフリーズし、場合によっては実行時に外部に転送する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d231b-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="d231b-203">無効にした後は、**tx_trace_enable** を呼び出して、トレースを再度開始できます。</span><span class="sxs-lookup"><span data-stu-id="d231b-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-204">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-205">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-205">Input Parameters</span></span>

<span data-ttu-id="d231b-206">[なし] :</span><span class="sxs-lookup"><span data-stu-id="d231b-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="d231b-207">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-207">Return Values</span></span>

- <span data-ttu-id="d231b-208">**TX_SUCCESS** (0x00) イベント トレースの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d231b-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="d231b-209">**TX_NOT_DONE** (0x20) イベント トレースは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d231b-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="d231b-210">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="d231b-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-211">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-211">Allowed From</span></span>

<span data-ttu-id="d231b-212">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d231b-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-213">例</span><span class="sxs-lookup"><span data-stu-id="d231b-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-214">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-214">See Also</span></span>

<span data-ttu-id="d231b-215">tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="d231b-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="d231b-217">ISR 開始イベントを挿入する</span><span class="sxs-lookup"><span data-stu-id="d231b-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-218">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="d231b-219">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-219">Description</span></span>

<span data-ttu-id="d231b-220">このサービスでは、ISR 開始イベントをイベント トレース バッファーに挿入します。</span><span class="sxs-lookup"><span data-stu-id="d231b-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="d231b-221">これは、ISR 処理の開始時にアプリケーションによって呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="d231b-222">指定されたパラメーターは、アプリケーションに対して特定の ISR を識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-223">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-224">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-224">Input Parameters</span></span> 
- <span data-ttu-id="d231b-225">**isr_id**: ISR を識別するためのアプリケーション固有の値。</span><span class="sxs-lookup"><span data-stu-id="d231b-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="d231b-226">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-226">Return Values</span></span>

<span data-ttu-id="d231b-227">**なし**</span><span class="sxs-lookup"><span data-stu-id="d231b-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-228">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-228">Allowed From</span></span> 

<span data-ttu-id="d231b-229">ISR</span><span class="sxs-lookup"><span data-stu-id="d231b-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-230">例</span><span class="sxs-lookup"><span data-stu-id="d231b-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-231">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-231">See Also</span></span>

<span data-ttu-id="d231b-232">tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="d231b-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="d231b-234">ISR 終了イベントを挿入する</span><span class="sxs-lookup"><span data-stu-id="d231b-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-235">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="d231b-236">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-236">Description</span></span>

<span data-ttu-id="d231b-237">このサービスでは、ISR 開始イベントをイベント トレース バッファーに挿入します。</span><span class="sxs-lookup"><span data-stu-id="d231b-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="d231b-238">これは、ISR 処理の開始時にアプリケーションによって呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="d231b-239">指定されたパラメーターは、アプリケーションに対して ISR を識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-240">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-241">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-241">Input Parameters</span></span> 

- <span data-ttu-id="d231b-242">**isr_id**: ISR を識別するためのアプリケーション固有の値。</span><span class="sxs-lookup"><span data-stu-id="d231b-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="d231b-243">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-243">Return Values</span></span>

<span data-ttu-id="d231b-244">**なし**</span><span class="sxs-lookup"><span data-stu-id="d231b-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-245">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-245">Allowed From</span></span>

<span data-ttu-id="d231b-246">ISR</span><span class="sxs-lookup"><span data-stu-id="d231b-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-247">例</span><span class="sxs-lookup"><span data-stu-id="d231b-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-248">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-248">See Also</span></span>

<span data-ttu-id="d231b-249">tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="d231b-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="d231b-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="d231b-251">トレース バッファーの完全なアプリケーション コールバックを登録する</span><span class="sxs-lookup"><span data-stu-id="d231b-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-252">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="d231b-253">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-253">Description</span></span>

<span data-ttu-id="d231b-254">このサービスでは、トレース バッファーがいっぱいになったときに ThreadX によって呼び出されるアプリケーション コールバック関数を登録します。</span><span class="sxs-lookup"><span data-stu-id="d231b-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="d231b-255">その後、アプリケーションでトレースを無効にしたり、場合によっては新しいトレース バッファーを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="d231b-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-256">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-257">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-257">Input Parameters</span></span>

- <span data-ttu-id="d231b-258">**full_buffer_callback**: トレース バッファーがいっぱいになったときに呼び出すアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="d231b-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="d231b-259">値が NULL の場合、通知コールバックは無効になります。</span><span class="sxs-lookup"><span data-stu-id="d231b-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="d231b-260">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-260">Return Values</span></span>

<span data-ttu-id="d231b-261">**なし**</span><span class="sxs-lookup"><span data-stu-id="d231b-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-262">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-262">Allowed From</span></span>

<span data-ttu-id="d231b-263">ISR</span><span class="sxs-lookup"><span data-stu-id="d231b-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-264">例</span><span class="sxs-lookup"><span data-stu-id="d231b-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-265">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-265">See Also</span></span>

<span data-ttu-id="d231b-266">tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="d231b-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="d231b-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="d231b-268">ユーザー イベントを挿入する</span><span class="sxs-lookup"><span data-stu-id="d231b-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="d231b-269">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d231b-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="d231b-270">説明</span><span class="sxs-lookup"><span data-stu-id="d231b-270">Description</span></span>

<span data-ttu-id="d231b-271">このサービスでは、ユーザー イベントをトレース バッファーに挿入します。</span><span class="sxs-lookup"><span data-stu-id="d231b-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="d231b-272">ユーザー イベント ID は、定数 **TX_TRACE_USER_EVENT_START** よりも大きくする必要があります。これは 4096 に定義されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="d231b-273">最大ユーザー イベントは、定数 **TX_TRACE_USER_EVENT_END** によって定義されます。これは 65535 に定義されています。</span><span class="sxs-lookup"><span data-stu-id="d231b-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="d231b-274">この範囲内のすべてのイベントがアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d231b-274">All events within this range are available to the application.</span></span> <span data-ttu-id="d231b-275">情報フィールドはアプリケーション固有です。</span><span class="sxs-lookup"><span data-stu-id="d231b-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d231b-276">ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="d231b-277">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d231b-277">Input Parameters</span></span>

- <span data-ttu-id="d231b-278">**event_id**: アプリケーション固有のイベント ID で、**TX_TRACE_USER_EVENT_START** より大きく、**TX_TRACE_USER_EVENT_END** 以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d231b-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="d231b-279">**info_field_1**: アプリケーション固有の情報フィールド。</span><span class="sxs-lookup"><span data-stu-id="d231b-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="d231b-280">**info_field_2**: アプリケーション固有の情報フィールド。</span><span class="sxs-lookup"><span data-stu-id="d231b-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="d231b-281">**info_field_3**: アプリケーション固有の情報フィールド。</span><span class="sxs-lookup"><span data-stu-id="d231b-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="d231b-282">**info_field_4**: アプリケーション固有の情報フィールド。</span><span class="sxs-lookup"><span data-stu-id="d231b-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="d231b-283">戻り値</span><span class="sxs-lookup"><span data-stu-id="d231b-283">Return Values</span></span>
- <span data-ttu-id="d231b-284">**TX_SUCCESS** (0x00) ユーザー イベントの挿入に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d231b-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="d231b-285">**TX_NOT_DONE** (0x20) イベント トレースは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d231b-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="d231b-286">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="d231b-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="d231b-287">許可元</span><span class="sxs-lookup"><span data-stu-id="d231b-287">Allowed From</span></span>

<span data-ttu-id="d231b-288">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d231b-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="d231b-289">例</span><span class="sxs-lookup"><span data-stu-id="d231b-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="d231b-290">参照</span><span class="sxs-lookup"><span data-stu-id="d231b-290">See Also</span></span>

<span data-ttu-id="d231b-291">tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="d231b-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>