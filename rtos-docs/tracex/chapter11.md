---
title: 第 11 章 - イベント トレース バッファーの形式
description: ThreadX には、すべての Azure RTOS ThreadX サービス、スレッド状態の変更、およびユーザー定義イベントに対する組み込みのイベント トレース サポートが用意されています。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812392"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="8a81a-103">第 11 章 - イベント トレース バッファーの形式</span><span class="sxs-lookup"><span data-stu-id="8a81a-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="8a81a-104">Azure RTOS ThreadX には、すべての ThreadX サービス、スレッド状態の変更、およびユーザー定義イベントに対する組み込みのイベント トレース サポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8a81a-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="8a81a-105">イベント トレースを使用するには、**TX_ENABLE_EVENT_TRACE** が定義された ThreadX、NetX、および FileX ライブラリをビルドし、**_tx_trace_enable_** 関数を呼び出してトレースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8a81a-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="8a81a-106">この章では、そのプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="8a81a-107">イベント トレース形式</span><span class="sxs-lookup"><span data-stu-id="8a81a-107">Event Trace Format</span></span>

<span data-ttu-id="8a81a-108">ThreadX イベント トレース バッファーの形式は、コントロール ヘッダー、オブジェクト レジストリ、およびトレース エントリの 3 つのセクションに分かれています。</span><span class="sxs-lookup"><span data-stu-id="8a81a-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="8a81a-109">以下に示すのは、ThreadX イベント トレース バッファーの一般的なレイアウトです。</span><span class="sxs-lookup"><span data-stu-id="8a81a-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="8a81a-110">**コントロール ヘッダー**</span><span class="sxs-lookup"><span data-stu-id="8a81a-110">**Control Header**</span></span>

<span data-ttu-id="8a81a-111">**オブジェクト レジストリ エントリ 0**</span><span class="sxs-lookup"><span data-stu-id="8a81a-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="8a81a-112">**…**</span><span class="sxs-lookup"><span data-stu-id="8a81a-112">**…**</span></span>

<span data-ttu-id="8a81a-113">**オブジェクト レジストリ エントリ "n"**</span><span class="sxs-lookup"><span data-stu-id="8a81a-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="8a81a-114">**イベント トレース エントリ 0**</span><span class="sxs-lookup"><span data-stu-id="8a81a-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="8a81a-115">**…**</span><span class="sxs-lookup"><span data-stu-id="8a81a-115">**…**</span></span>

<span data-ttu-id="8a81a-116">**イベント トレース エントリ "n"**</span><span class="sxs-lookup"><span data-stu-id="8a81a-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="8a81a-117">イベント トレース コントロール ヘッダー</span><span class="sxs-lookup"><span data-stu-id="8a81a-117">Event Trace Control Header</span></span>

<span data-ttu-id="8a81a-118">コントロール ヘッダーでは、イベント トレース バッファーの厳密なレイアウトが定義されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="8a81a-119">これには、登録できる ThreadX オブジェクトの数や、記録できるイベントの数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="8a81a-120">さらに、コントロール ヘッダーでは、トレース バッファーの各要素が存在する場所も定義されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="8a81a-121">次のデータ構造は、コントロール ヘッダーを定義したものです。</span><span class="sxs-lookup"><span data-stu-id="8a81a-121">The following data structure defines the control header:</span></span>

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a><span data-ttu-id="8a81a-122">コントロール ヘッダー ID</span><span class="sxs-lookup"><span data-stu-id="8a81a-122">Control Header ID</span></span>

<span data-ttu-id="8a81a-123">コントロール ヘッダー ID は、32 ビットの 16 進数値 (0x54585442) で構成されます。これは、ASCII 文字 ***TXTB*** に対応します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="8a81a-124">この値は、32 ビットの符号なし変数として書き込まれるため、イベント トレース バッファーのエンディアンを検出するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="8a81a-125">たとえば、メモリの最初の 4 つのバイトの値が 0x54、0x58、0x54、0x42 の場合、イベント トレース バッファーはビッグ エンディアン形式で書き込まれています。</span><span class="sxs-lookup"><span data-stu-id="8a81a-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="8a81a-126">それ以外の場合、イベント トレース バッファーはリトル エンディアン形式で書き込まれています。</span><span class="sxs-lookup"><span data-stu-id="8a81a-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="8a81a-127">タイマー有効マスク</span><span class="sxs-lookup"><span data-stu-id="8a81a-127">Timer Valid Mask</span></span>

<span data-ttu-id="8a81a-128">タイマー有効マスクでは、実際のイベント トレース エントリ内での、有効なタイムスタンプのビット数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="8a81a-129">たとえば、タイムスタンプ ソースに 16 ビットが含まれている場合、このフィールドの値は 0xFFFF とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="8a81a-130">32 ビットのタイムスタン プソースの場合、値は 0xFFFFFFFF になります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="8a81a-131">この値は、_*_tx_port h_*\* 内の \***TX_TRACE_TIME_MASK** _ 定数によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="8a81a-132">トレース ベース アドレス</span><span class="sxs-lookup"><span data-stu-id="8a81a-132">Trace Base Address</span></span>

<span data-ttu-id="8a81a-133">トレース バッファー ベース アドレスは、***tx_trace_enable*** 呼び出しでのトレース バッファーの開始点として、アプリケーションによって指定されたアドレスです。</span><span class="sxs-lookup"><span data-stu-id="8a81a-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="8a81a-134">このアドレスは、バッファー内のさまざまな要素に対するバッファー相対オフセットを分析ツールで取得する目的専用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="8a81a-135">たとえば、トレース バッファー内の現在のイベントのバッファー相対オフセットは、現在のイベント アドレスからベース アドレスを単純に減算することで計算されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="8a81a-136">レジストリの開始ポインターと終了ポインター</span><span class="sxs-lookup"><span data-stu-id="8a81a-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="8a81a-137">レジストリ開始ポインターは、最初のオブジェクト レジストリ エントリのアドレスを指し、レジストリ終了ポインターは、最後のレジスタ エントリの直後のアドレスを指します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="8a81a-138">これらの値は *tx_trace_enable* の処理中に設定され、トレース中は変更されません。</span><span class="sxs-lookup"><span data-stu-id="8a81a-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="8a81a-139">レジストリ名サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-139">Registry Name Size</span></span>

<span data-ttu-id="8a81a-140">レジストリ名サイズでは、レジストリ エントリ内の各オブジェクト名の最大サイズがバイト単位で定義されます。これは、シンボル \***TX_TRACE_OBJECT_REGISTRY_NAME** _ によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="8a81a-141">既定値は 32 であり、_*_tx_trace.h_*_ で定義されています。</span><span class="sxs-lookup"><span data-stu-id="8a81a-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="8a81a-142">オブジェクト名は、オブジェクトの作成時にアプリケーションによって指定された名前に対応します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="8a81a-143">たとえば、スレッドのオブジェクト レジストリ名は、_*_tx_thread_create_*\* の呼び出しに対してアプリケーションによって指定された名前です。</span><span class="sxs-lookup"><span data-stu-id="8a81a-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="8a81a-144">バッファーの開始ポインターと終了ポインター</span><span class="sxs-lookup"><span data-stu-id="8a81a-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="8a81a-145">イベント トレース バッファーの開始ポインターは、最初のトレース エントリのアドレスを指し、レジストリ終了ポインターは、最後のトレース エントリの直後のアドレスを指します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="8a81a-146">これらの値は ***tx_trace_enable*** の処理中に設定され、トレース中は変更されません。</span><span class="sxs-lookup"><span data-stu-id="8a81a-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="8a81a-147">現在のバッファー ポインター</span><span class="sxs-lookup"><span data-stu-id="8a81a-147">Current Buffer Pointer</span></span>

<span data-ttu-id="8a81a-148">イベント トレース バッファーの現在のポインターは、最も古いトレース エントリのアドレスを指します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="8a81a-149">トレース エントリは循環リストで保持されるため、現在のバッファー ポインターは次に書き込まれるトレース エントリも表します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="8a81a-150">イベント トレース オブジェクト レジストリ</span><span class="sxs-lookup"><span data-stu-id="8a81a-150">Event Trace Object Registry</span></span>

<span data-ttu-id="8a81a-151">イベント トレース オブジェクト レジストリには、アプリケーションによって作成されたオブジェクトに対応する、\***n** _ 個のオブジェクト レジストリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="8a81a-152">オブジェクト レジストリの主な目的は、外部分析ツールで実際のオブジェクト名をトレース バッファー エントリのオブジェクト アドレスと関連付けできるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="8a81a-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="8a81a-153">レジストリ エントリの数は、_ *_tx_trace_enable_*\* 呼び出しでアプリケーションによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="8a81a-154">各オブジェクト レジスタ エントリには、アプリケーションによって以前に作成された特定の ThreadX オブジェクトに関する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="8a81a-155">次のデータ構造は、各オブジェクトのレジストリ エントリを定義したものです。</span><span class="sxs-lookup"><span data-stu-id="8a81a-155">The following data structure defines each object registry entry:</span></span>

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a><span data-ttu-id="8a81a-156">オブジェクト使用可能フラグ</span><span class="sxs-lookup"><span data-stu-id="8a81a-156">Object Available Flag</span></span>

<span data-ttu-id="8a81a-157">オブジェクト レジストリ エントリが使用可能な場合は、オブジェクト使用可能フラグが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="8a81a-158">それ以外の場合 (値が 1 ではない場合)、オブジェクト レジストリ エントリは使用できません。</span><span class="sxs-lookup"><span data-stu-id="8a81a-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="8a81a-159">なお、使用可能な場合でも、エントリに有効な情報が含まれている可能性はあるという点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="8a81a-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="8a81a-160">オブジェクト エントリの種類</span><span class="sxs-lookup"><span data-stu-id="8a81a-160">Object Entry Type</span></span>

<span data-ttu-id="8a81a-161">オブジェクト エントリの種類では、そのエントリ内のオブジェクトの種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="8a81a-162">次に示すのは、有効なオブジェクトの種類の一覧です。</span><span class="sxs-lookup"><span data-stu-id="8a81a-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="8a81a-163">**Value**</span><span class="sxs-lookup"><span data-stu-id="8a81a-163">**Value**</span></span> | <span data-ttu-id="8a81a-164">**オブジェクトの種類**</span><span class="sxs-lookup"><span data-stu-id="8a81a-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="8a81a-165">0</span><span class="sxs-lookup"><span data-stu-id="8a81a-165">0</span></span>         | <span data-ttu-id="8a81a-166">無効</span><span class="sxs-lookup"><span data-stu-id="8a81a-166">Not Valid</span></span>       |
| <span data-ttu-id="8a81a-167">1</span><span class="sxs-lookup"><span data-stu-id="8a81a-167">1</span></span>         | <span data-ttu-id="8a81a-168">スレッド</span><span class="sxs-lookup"><span data-stu-id="8a81a-168">Thread</span></span>          |
| <span data-ttu-id="8a81a-169">2</span><span class="sxs-lookup"><span data-stu-id="8a81a-169">2</span></span>         | <span data-ttu-id="8a81a-170">Timer</span><span class="sxs-lookup"><span data-stu-id="8a81a-170">Timer</span></span> |
| <span data-ttu-id="8a81a-171">3</span><span class="sxs-lookup"><span data-stu-id="8a81a-171">3</span></span>         | <span data-ttu-id="8a81a-172">キュー</span><span class="sxs-lookup"><span data-stu-id="8a81a-172">Queue</span></span> |
| <span data-ttu-id="8a81a-173">4</span><span class="sxs-lookup"><span data-stu-id="8a81a-173">4</span></span>         | <span data-ttu-id="8a81a-174">Semaphore</span><span class="sxs-lookup"><span data-stu-id="8a81a-174">Semaphore</span></span> |
| <span data-ttu-id="8a81a-175">5</span><span class="sxs-lookup"><span data-stu-id="8a81a-175">5</span></span>         | <span data-ttu-id="8a81a-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="8a81a-176">Mutex</span></span> |
| <span data-ttu-id="8a81a-177">6</span><span class="sxs-lookup"><span data-stu-id="8a81a-177">6</span></span>         | <span data-ttu-id="8a81a-178">イベント フラグ グループ</span><span class="sxs-lookup"><span data-stu-id="8a81a-178">Event Flags Group</span></span> |
| <span data-ttu-id="8a81a-179">7</span><span class="sxs-lookup"><span data-stu-id="8a81a-179">7</span></span>         | <span data-ttu-id="8a81a-180">ブロック プール</span><span class="sxs-lookup"><span data-stu-id="8a81a-180">Block Pool</span></span> |
| <span data-ttu-id="8a81a-181">8</span><span class="sxs-lookup"><span data-stu-id="8a81a-181">8</span></span>         | <span data-ttu-id="8a81a-182">バイト プール</span><span class="sxs-lookup"><span data-stu-id="8a81a-182">Byte Pool</span></span> |
| <span data-ttu-id="8a81a-183">9</span><span class="sxs-lookup"><span data-stu-id="8a81a-183">9</span></span>         | <span data-ttu-id="8a81a-184">メディア</span><span class="sxs-lookup"><span data-stu-id="8a81a-184">../media</span></span> |
| <span data-ttu-id="8a81a-185">10</span><span class="sxs-lookup"><span data-stu-id="8a81a-185">10</span></span>        | <span data-ttu-id="8a81a-186">ファイル</span><span class="sxs-lookup"><span data-stu-id="8a81a-186">File</span></span> |
| <span data-ttu-id="8a81a-187">11</span><span class="sxs-lookup"><span data-stu-id="8a81a-187">11</span></span>        | <span data-ttu-id="8a81a-188">IP</span><span class="sxs-lookup"><span data-stu-id="8a81a-188">IP</span></span> |
| <span data-ttu-id="8a81a-189">12</span><span class="sxs-lookup"><span data-stu-id="8a81a-189">12</span></span>        | <span data-ttu-id="8a81a-190">パケット プール</span><span class="sxs-lookup"><span data-stu-id="8a81a-190">Packet Pool</span></span> |
| <span data-ttu-id="8a81a-191">13</span><span class="sxs-lookup"><span data-stu-id="8a81a-191">13</span></span>        | <span data-ttu-id="8a81a-192">TCP ソケット</span><span class="sxs-lookup"><span data-stu-id="8a81a-192">TCP Socket</span></span> |
| <span data-ttu-id="8a81a-193">14</span><span class="sxs-lookup"><span data-stu-id="8a81a-193">14</span></span>        | <span data-ttu-id="8a81a-194">UDP ソケット</span><span class="sxs-lookup"><span data-stu-id="8a81a-194">UDP Socket</span></span> |
| <span data-ttu-id="8a81a-195">15-20</span><span class="sxs-lookup"><span data-stu-id="8a81a-195">15-20</span></span>     | <span data-ttu-id="8a81a-196">予約済み</span><span class="sxs-lookup"><span data-stu-id="8a81a-196">Reserved</span></span> |  
| <span data-ttu-id="8a81a-197">21</span><span class="sxs-lookup"><span data-stu-id="8a81a-197">21</span></span>        | <span data-ttu-id="8a81a-198">USB ホスト スタック デバイス</span><span class="sxs-lookup"><span data-stu-id="8a81a-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="8a81a-199">22</span><span class="sxs-lookup"><span data-stu-id="8a81a-199">22</span></span>        | <span data-ttu-id="8a81a-200">USB ホスト スタック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a81a-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="8a81a-201">23</span><span class="sxs-lookup"><span data-stu-id="8a81a-201">23</span></span>        | <span data-ttu-id="8a81a-202">USB ホスト エンドポイント</span><span class="sxs-lookup"><span data-stu-id="8a81a-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="8a81a-203">24</span><span class="sxs-lookup"><span data-stu-id="8a81a-203">24</span></span>        | <span data-ttu-id="8a81a-204">USB ホスト クラス</span><span class="sxs-lookup"><span data-stu-id="8a81a-204">USB Host Class</span></span> |
| <span data-ttu-id="8a81a-205">25</span><span class="sxs-lookup"><span data-stu-id="8a81a-205">25</span></span>        | <span data-ttu-id="8a81a-206">USB デバイス</span><span class="sxs-lookup"><span data-stu-id="8a81a-206">USB Device</span></span> |
| <span data-ttu-id="8a81a-207">26</span><span class="sxs-lookup"><span data-stu-id="8a81a-207">26</span></span>        | <span data-ttu-id="8a81a-208">USB デバイス インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a81a-208">USB Device Interface</span></span> |
| <span data-ttu-id="8a81a-209">27</span><span class="sxs-lookup"><span data-stu-id="8a81a-209">27</span></span>        | <span data-ttu-id="8a81a-210">USB デバイス エンドポイント</span><span class="sxs-lookup"><span data-stu-id="8a81a-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="8a81a-211">28</span><span class="sxs-lookup"><span data-stu-id="8a81a-211">28</span></span>        | <span data-ttu-id="8a81a-212">USB デバイス クラス</span><span class="sxs-lookup"><span data-stu-id="8a81a-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="8a81a-213">オブジェクト ポインター</span><span class="sxs-lookup"><span data-stu-id="8a81a-213">Object Pointer</span></span>

<span data-ttu-id="8a81a-214">オブジェクト ポインターでは、ThreadX API を使用してオブジェクトにアクセスするために使用されるオブジェクト アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="8a81a-215">オブジェクト予約済みフィールド</span><span class="sxs-lookup"><span data-stu-id="8a81a-215">Object Reserved Fields</span></span>

<span data-ttu-id="8a81a-216">スレッド以外のすべてのオブジェクトについては、これらの予約済みフィールドは 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="8a81a-217">スレッドの場合は、レジストリに入力された時点でのスレッドの優先度が、この 2 つの予約済みフィールドに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="8a81a-218">オブジェクト パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a81a-218">Object Parameters</span></span>

<span data-ttu-id="8a81a-219">オブジェクト パラメーターには、オブジェクトに関する補足情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="8a81a-220">次に示すのは、各 ThreadX オブジェクトの補足情報に関する説明です。</span><span class="sxs-lookup"><span data-stu-id="8a81a-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="8a81a-221">**オブジェクトの種類**</span><span class="sxs-lookup"><span data-stu-id="8a81a-221">**Object Type**</span></span>        | <span data-ttu-id="8a81a-222">**パラメーター 1**</span><span class="sxs-lookup"><span data-stu-id="8a81a-222">**Parameter 1**</span></span>  | <span data-ttu-id="8a81a-223">**パラメーター 2**</span><span class="sxs-lookup"><span data-stu-id="8a81a-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="8a81a-224">スレッド</span><span class="sxs-lookup"><span data-stu-id="8a81a-224">Thread</span></span>                 | <span data-ttu-id="8a81a-225">スタックの開始</span><span class="sxs-lookup"><span data-stu-id="8a81a-225">Stack Start</span></span>      | <span data-ttu-id="8a81a-226">スタック サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-226">Stack Size</span></span> |
| <span data-ttu-id="8a81a-227">Timer</span><span class="sxs-lookup"><span data-stu-id="8a81a-227">Timer</span></span>                  | <span data-ttu-id="8a81a-228">初期ティック</span><span class="sxs-lookup"><span data-stu-id="8a81a-228">Initial Ticks</span></span> | <span data-ttu-id="8a81a-229">ティックの再スケジュール</span><span class="sxs-lookup"><span data-stu-id="8a81a-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="8a81a-230">キュー</span><span class="sxs-lookup"><span data-stu-id="8a81a-230">Queue</span></span>                  | <span data-ttu-id="8a81a-231">キュー サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-231">Queue Size</span></span> | <span data-ttu-id="8a81a-232">メッセージ サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-232">Message Size</span></span> |
| <span data-ttu-id="8a81a-233">Semaphore</span><span class="sxs-lookup"><span data-stu-id="8a81a-233">Semaphore</span></span>              | <span data-ttu-id="8a81a-234">初期インスタンス</span><span class="sxs-lookup"><span data-stu-id="8a81a-234">Initial Instances</span></span> | - |
| <span data-ttu-id="8a81a-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="8a81a-235">Mutex</span></span>                  | <span data-ttu-id="8a81a-236">継承フラグ</span><span class="sxs-lookup"><span data-stu-id="8a81a-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="8a81a-237">イベント フラグ グループ</span><span class="sxs-lookup"><span data-stu-id="8a81a-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="8a81a-238">ブロック プール</span><span class="sxs-lookup"><span data-stu-id="8a81a-238">Block Pool</span></span>             | <span data-ttu-id="8a81a-239">合計ブロック数</span><span class="sxs-lookup"><span data-stu-id="8a81a-239">Total Blocks</span></span> | <span data-ttu-id="8a81a-240">ブロック サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-240">Block Size</span></span> |
| <span data-ttu-id="8a81a-241">バイト プール</span><span class="sxs-lookup"><span data-stu-id="8a81a-241">Byte Pool</span></span>              | <span data-ttu-id="8a81a-242">Total Bytes</span><span class="sxs-lookup"><span data-stu-id="8a81a-242">Total Bytes</span></span> | - |
| <span data-ttu-id="8a81a-243">メディア</span><span class="sxs-lookup"><span data-stu-id="8a81a-243">../media</span></span>                  | <span data-ttu-id="8a81a-244">FAT キャッシュ サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-244">Fat Cache Size</span></span> | <span data-ttu-id="8a81a-245">セクター キャッシュ サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-245">Sector Cache Size</span></span> |
| <span data-ttu-id="8a81a-246">ファイル</span><span class="sxs-lookup"><span data-stu-id="8a81a-246">File</span></span>                   | - | - |
| <span data-ttu-id="8a81a-247">IP</span><span class="sxs-lookup"><span data-stu-id="8a81a-247">IP</span></span>                     | <span data-ttu-id="8a81a-248">スタックの開始</span><span class="sxs-lookup"><span data-stu-id="8a81a-248">Stack Start</span></span> | <span data-ttu-id="8a81a-249">スタック サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-249">Stack Size</span></span> |
| <span data-ttu-id="8a81a-250">パケット プール</span><span class="sxs-lookup"><span data-stu-id="8a81a-250">Packet Pool</span></span>            | <span data-ttu-id="8a81a-251">Packet Size</span><span class="sxs-lookup"><span data-stu-id="8a81a-251">Packet Size</span></span> | <span data-ttu-id="8a81a-252">パケット数</span><span class="sxs-lookup"><span data-stu-id="8a81a-252">Number of Packets</span></span> |
| <span data-ttu-id="8a81a-253">TCP ソケット</span><span class="sxs-lookup"><span data-stu-id="8a81a-253">TCP Socket</span></span>             | <span data-ttu-id="8a81a-254">IP アドレス</span><span class="sxs-lookup"><span data-stu-id="8a81a-254">IP address</span></span> | <span data-ttu-id="8a81a-255">ウィンドウ サイズ</span><span class="sxs-lookup"><span data-stu-id="8a81a-255">Window Size</span></span> |
| <span data-ttu-id="8a81a-256">UDP ソケット</span><span class="sxs-lookup"><span data-stu-id="8a81a-256">UDP Socket</span></span>             | <span data-ttu-id="8a81a-257">IP アドレス</span><span class="sxs-lookup"><span data-stu-id="8a81a-257">IP address</span></span> | <span data-ttu-id="8a81a-258">RX キューの最大数</span><span class="sxs-lookup"><span data-stu-id="8a81a-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="8a81a-259">オブジェクト名</span><span class="sxs-lookup"><span data-stu-id="8a81a-259">Object Name</span></span>

<span data-ttu-id="8a81a-260">オブジェクト名には、ThreadX オブジェクトの名前が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="8a81a-261">この名前は、オブジェクトの作成時に ThreadX に対して指定された名前です。</span><span class="sxs-lookup"><span data-stu-id="8a81a-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="8a81a-262">既定では、オブジェクト名の最大文字数は 32 文字です。</span><span class="sxs-lookup"><span data-stu-id="8a81a-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="8a81a-263">実際の名前が 32 文字を超える場合は、名前が切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="8a81a-264">イベント トレース エントリ</span><span class="sxs-lookup"><span data-stu-id="8a81a-264">Event Trace Entries</span></span>

<span data-ttu-id="8a81a-265">イベント トレース エントリは、イベント トレース バッファーの下部にあります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="8a81a-266">エントリは循環リストに保持され、現在のエントリ ポインターは最も古いエントリを指します。</span><span class="sxs-lookup"><span data-stu-id="8a81a-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="8a81a-267">リスト内のエントリの数は、***tx_trace_enable*** の呼び出しによって計算されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="8a81a-268">各オブジェクト レジスタ エントリには、特定の ThreadX トレース イベントに関する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="8a81a-269">次のデータ構造は、各トレース イベント エントリを定義したものです。</span><span class="sxs-lookup"><span data-stu-id="8a81a-269">The following data structure defines each trace event entry:</span></span>

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a><span data-ttu-id="8a81a-270">スレッド ポインター</span><span class="sxs-lookup"><span data-stu-id="8a81a-270">Thread Pointer</span></span>

<span data-ttu-id="8a81a-271">スレッド ポインターには、このイベントの発生時に実行されているスレッドのアドレスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="8a81a-272">初期化中にイベントが発生した場合 (スレッドが実行されていない場合)、このポインターの値は 0xF0F0F0F0 になります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="8a81a-273">割り込みサービス ルーチン (ISR) の実行中にイベントが発生した場合、このポインターの値は 0xFFFFFFFF になります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="8a81a-274">エントリがまだ使用されていない場合、このポインターの値は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="8a81a-275">スレッド優先度</span><span class="sxs-lookup"><span data-stu-id="8a81a-275">Thread Priority</span></span>

<span data-ttu-id="8a81a-276">スレッド優先度フィールドには、そのイベントの発生時に実行されていたスレッドの優先度とプリエンプションしきい値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="8a81a-277">割り込みコンテキストが存在する場合 (スレッド ポインターが 0xFFFFFFFF の場合)、このフィールドの値は優先度ではなく、イベント時点での ***_tx_thread_current_ptr*** の値になります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="8a81a-278">その他の場合、このフィールドの値は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="8a81a-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="8a81a-279">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8a81a-279">Event ID</span></span>

<span data-ttu-id="8a81a-280">イベント ID では、発生したイベントが指定されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="8a81a-281">有効な ThreadX トレース イベント ID の範囲は、1 - 1024 です。</span><span class="sxs-lookup"><span data-stu-id="8a81a-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="8a81a-282">1025 以降で始まる値は、ユーザー固有のイベント用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="8a81a-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="8a81a-283">ThreadX イベント ID の完全な定義については、***tx_trace.h*** ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a81a-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="8a81a-284">情報フィールド (1-4)</span><span class="sxs-lookup"><span data-stu-id="8a81a-284">Information Fields (1-4)</span></span>

<span data-ttu-id="8a81a-285">情報フィールドには、特定のイベントに関する追加情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a81a-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="8a81a-286">定義されている各 ThreadX イベント ID の情報フィールドの完全な説明については、***tx_trace.h*** ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a81a-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>