---
title: 第 4 章 - Azure RTOS ThreadX サービスの説明
description: この章は、すべての Azure RTO ThreadX サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810274"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="ac9b0-103">第 4 章 - Azure RTOS ThreadX サービスの説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="ac9b0-104">この章は、すべての Azure RTO ThreadX サービスの説明をアルファベット順にまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="ac9b0-105">これらの名前は、類似するすべてのサービスがグループ化されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="ac9b0-106">次の説明の「戻り値」セクション内の **太字** で記載されている値は、API エラー チェックを無効にする際に使用される **TX_DISABLE_ERROR_CHECKING** 定義の影響を受けません。一方、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="ac9b0-107">さらに、「**割り込み可能**」というの見出しの下に「**はい**」と表示されているものは、そのサービスを呼び出すと優先順位の高いスレッドが再開され、呼び出し元のスレッドが割り込まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="ac9b0-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-108">tx_block_allocate</span></span>

<span data-ttu-id="ac9b0-109">固定サイズのメモリ ブロックの割り当て</span><span class="sxs-lookup"><span data-stu-id="ac9b0-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-110">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-111">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-111">Description</span></span>

<span data-ttu-id="ac9b0-112">このサービスを使用すると、指定したメモリ プールから固定サイズのメモリ ブロックが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="ac9b0-113">メモリ ブロックの実際のサイズは、メモリ プールの作成時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-114">*アプリケーション コードで、割り当てられたメモリ ブロックの外部に書き込まないようにすることが重要です。これが発生すると、隣接する (通常は後続の) メモリ ブロックで破損が発生します。結果は予測不可能で、多くの場合、致命的です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-115">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-115">Parameters</span></span>

- <span data-ttu-id="ac9b0-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-116">**pool_ptr**</span></span> <br><span data-ttu-id="ac9b0-117">以前に作成されたメモリ ブロック プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="ac9b0-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-118">**block_ptr**</span></span> <br><span data-ttu-id="ac9b0-119">目標ブロック ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="ac9b0-120">割り当てが正常に行われると、割り当てられたメモリ ブロックのアドレスが、このパラメーターが指す位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="ac9b0-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-121">**wait_option**</span></span> <br><span data-ttu-id="ac9b0-122">使用可能なメモリ ブロックがない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="ac9b0-123">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-124">**TX_NO_WAIT** (0x00000000) - **TX_NO_WAIT** を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="ac9b0-125">*これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです*。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="ac9b0-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - **TX_WAIT_FOREVER** を選択すると、呼び出し元のスレッドは、メモリ ブロックが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="ac9b0-127">"*タイムアウト値*" (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、メモリ ブロックを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-128">Return Values</span></span>

- <span data-ttu-id="ac9b0-129">**TX_SUCCESS** (0x00) メモリ ブロックの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="ac9b0-130">**TX_DELETED** (0x01) スレッドが中断されている間にメモリ ブロック プールが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-131">**TX_NO_MEMORY** (0x10) サービスは指定した待機時間内に固定サイズのメモリ ブロックを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-132">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="ac9b0-133">**TX_POOL_ERROR** (0x02) メモリ ブロック プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="ac9b0-134">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="ac9b0-135">**TX_PTR_ERROR** (0x03) 目標ポインターへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-136">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-136">Allowed From</span></span>

<span data-ttu-id="ac9b0-137">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-138">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-138">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-139">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-140">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-140">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-141">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-141">See Also</span></span>

- <span data-ttu-id="ac9b0-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-142">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="ac9b0-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-149">tx_block_pool_create</span></span>

<span data-ttu-id="ac9b0-150">固定サイズのメモリ ブロック プールの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-151">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="ac9b0-152">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-152">Description</span></span>

<span data-ttu-id="ac9b0-153">このサービスを使用すると、固定サイズのメモリ ブロック プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="ac9b0-154">指定したメモリ領域は、次の式を使用して、可能な限り多くの固定サイズのメモリ ブロックに分割されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="ac9b0-155">**合計ブロック** = (**合計バイト数**) / (**ブロック サイズ** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="ac9b0-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="ac9b0-156">\*各メモリ ブロックには、ユーザーには見えない、前の数式の "sizeof(void *)" で表されるオーバー ヘッドのポインターが 1 つ含まれています。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-157">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-157">Parameters</span></span>

- <span data-ttu-id="ac9b0-158">**pool_ptr** メモリ ブロック プールの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="ac9b0-159">**name_ptr** メモリ ブロック プールの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="ac9b0-160">**block_size** 各メモリ ブロック内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="ac9b0-161">**pool_start** メモリ ブロック プールの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="ac9b0-162">開始アドレスは、ULONG データ型のサイズに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="ac9b0-163">**pool_size** メモリ ブロック プールで使用可能な合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-164">Return Values</span></span>

- <span data-ttu-id="ac9b0-165">**TX_SUCCESS** (0x00) メモリ ブロック プールの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="ac9b0-166">**TX_POOL_ERROR** (0x02) メモリ ブロック プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="ac9b0-167">ポインターが NULL であるか、プールが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="ac9b0-168">**TX_PTR_ERROR** (0x03) プールの開始アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="ac9b0-169">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="ac9b0-170">**TX_SIZE_ERROR** (0x05) プールのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-171">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-171">Allowed From</span></span>

<span data-ttu-id="ac9b0-172">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-173">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-173">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-174">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-174">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-175">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-175">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-176">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-176">See Also</span></span>

- <span data-ttu-id="ac9b0-177">tx_block_allocate、tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-178">tx_block_pool_info_get、tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-180">tx_block_pool_prioritize、tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="ac9b0-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-181">tx_block_pool_delete</span></span>

<span data-ttu-id="ac9b0-182">メモリ ブロック プールの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-183">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-184">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-184">Description</span></span>

<span data-ttu-id="ac9b0-185">このサービスを使用すると、指定したブロック メモリ プールが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="ac9b0-186">このプールからのメモリ ブロックを待機しているすべてのスレッドが再開され、**TX_DELETED** 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-187">*プールに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、サービスの完了後に利用できます。また、このアプリケーションでは削除されたプールまたはその前のメモリ ブロックの使用を防ぐ必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-188">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-188">Parameters</span></span>

- <span data-ttu-id="ac9b0-189">**pool_ptr** 以前に作成されたメモリ ブロック プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-190">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-190">Return Values</span></span>

- <span data-ttu-id="ac9b0-191">**TX_SUCCESS** (0x00) メモリ ブロック プールの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="ac9b0-192">**TX_POOL_ERROR** (0x02) メモリ ブロック プールのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="ac9b0-193">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-194">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-194">Allowed From</span></span>

<span data-ttu-id="ac9b0-195">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-196">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-196">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-197">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-198">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-199">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-199">See Also</span></span>

- <span data-ttu-id="ac9b0-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-200">tx_block_allocate</span></span>
- <span data-ttu-id="ac9b0-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-201">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-202">tx_block_pool_info_get、tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-204">tx_block_pool_prioritize、tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="ac9b0-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="ac9b0-206">ブロック プールに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-207">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-207">Prototype</span></span>

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="ac9b0-208">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-208">Description</span></span>

<span data-ttu-id="ac9b0-209">このサービスを使用すると、指定したブロック メモリ プールに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-210">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-210">Parameters</span></span>

- <span data-ttu-id="ac9b0-211">**pool_ptr** 以前に作成されたメモリ ブロック プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="ac9b0-212">**name** ブロック プールの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="ac9b0-213">**available** ブロック プール内の使用可能なブロック数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="ac9b0-214">**total_blocks** ブロック プール内の合計ブロック数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="ac9b0-215">**first_suspended** このブロック プールの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="ac9b0-216">**suspended_count** このブロック プールで現在中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="ac9b0-217">**next_pool** 次に作成されたブロック プールのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-218">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-219">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-219">Return Values</span></span>

- <span data-ttu-id="ac9b0-220">**TX_SUCCESS** (0x00) ブロック プールの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="ac9b0-221">**TX_POOL_ERROR** (0x02) メモリ ブロック プールのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-222">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-222">Allowed From</span></span>

<span data-ttu-id="ac9b0-223">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-224">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-224">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-225">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-225">See Also</span></span>

- <span data-ttu-id="ac9b0-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-226">tx_block_allocate</span></span>
- <span data-ttu-id="ac9b0-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-227">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-229">tx_block_pool_info_get、tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-231">tx_block_pool_prioritize、tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="ac9b0-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="ac9b0-233">ブロック プールのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-234">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="ac9b0-235">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-235">Description</span></span>

<span data-ttu-id="ac9b0-236">このサービスを使用すると、指定したメモリ ブロック プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-237">"*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*" **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** " *を使用して構築する必要があります。* "</span><span class="sxs-lookup"><span data-stu-id="ac9b0-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-238">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-238">Parameters</span></span>

- <span data-ttu-id="ac9b0-239">**pool_ptr** 以前に作成されたメモリ ブロック プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="ac9b0-240">**allocates** このプールで実行される割り当て要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="ac9b0-241">**releases** このプールで実行されるリリース要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="ac9b0-242">**suspensions** このプールのスレッド割り当て保留の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="ac9b0-243">**timeouts** このプールの割り当て保留タイムアウト数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="ac9b0-244">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-245">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-245">Return Values</span></span>

- <span data-ttu-id="ac9b0-246">**TX_SUCCESS** (0x00) ブロック プールのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="ac9b0-247">**TX_PTR_ERROR** (0x03) ブロック プールポ インターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="ac9b0-248">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-249">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-249">Allowed From</span></span>

<span data-ttu-id="ac9b0-250">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-251">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-251">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-252">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-252">See Also</span></span>

- <span data-ttu-id="ac9b0-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-253">tx_block_allocate</span></span>
- <span data-ttu-id="ac9b0-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-254">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="ac9b0-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-261">ブロック プール システムのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-262">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-263">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-263">Description</span></span>

<span data-ttu-id="ac9b0-264">このサービスを使用すると、アプリケーション内のすべてのメモリ ブロック プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-265">"*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*" **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** " *を使用して構築する必要があります。* "</span><span class="sxs-lookup"><span data-stu-id="ac9b0-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-266">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-266">Parameters</span></span>

- <span data-ttu-id="ac9b0-267">**allocates** すべてのブロック プールで実行される割り当て要求数の合計の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="ac9b0-268">**releases** すべてのブロック プールで実行されるリリース要求数の合計の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="ac9b0-269">**suspensions** すべてのブロック プールのスレッド割り当て保留の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="ac9b0-270">**timeouts** すべてのブロック プールで実行される割り当て保留タイムアウトの合計の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-271">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-272">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-272">Return Values</span></span>

- <span data-ttu-id="ac9b0-273">**TX_SUCCESS** (0x00) ブロック プール システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="ac9b0-274">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-275">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-275">Allowed From</span></span>

<span data-ttu-id="ac9b0-276">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-277">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-277">Example</span></span>

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-278">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-278">See Also</span></span>

- <span data-ttu-id="ac9b0-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-279">tx_block_allocate</span></span>
- <span data-ttu-id="ac9b0-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-280">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="ac9b0-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="ac9b0-287">ブロック プールの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="ac9b0-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-288">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-289">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-289">Description</span></span>

<span data-ttu-id="ac9b0-290">このサービスを使用すると、このプール上のメモリ ブロックで中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="ac9b0-291">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-292">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-292">Parameters</span></span>

- <span data-ttu-id="ac9b0-293">**pool_ptr** メモリ ブロック プールの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-294">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-294">Return Values</span></span>

- <span data-ttu-id="ac9b0-295">**TX_SUCCESS** (0x00) ブロック プールの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="ac9b0-296">**TX_POOL_ERROR** (0x02) メモリ ブロック プールのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-297">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-297">Allowed From</span></span>

<span data-ttu-id="ac9b0-298">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-299">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-299">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-300">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-300">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-301">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-301">Example</span></span>
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-302">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-302">See Also</span></span>

- <span data-ttu-id="ac9b0-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-303">tx_block_allocate</span></span>
- <span data-ttu-id="ac9b0-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-304">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="ac9b0-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-310">tx_block_release</span></span>

<span data-ttu-id="ac9b0-311">固定サイズのメモリ ブロックの解放</span><span class="sxs-lookup"><span data-stu-id="ac9b0-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-312">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="ac9b0-313">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-313">Description</span></span>

<span data-ttu-id="ac9b0-314">このサービスを使用すると、以前に割り当てられたブロックを、関連付けられているメモリ プールに解放します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="ac9b0-315">このプールからのメモリ ブロックを待機している中断中のスレッドが 1 つ以上ある場合、中断された最初のスレッドにこのメモリ ブロックが割り当てられ、再開されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ac9b0-316">*アプリケーションは、プールに解放された後にメモリ ブロック領域使用しないようにする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-317">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-317">Parameters</span></span>

- <span data-ttu-id="ac9b0-318">**block_ptr** 以前に割り当てられていたメモリ ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-319">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-319">Return Values</span></span>

- <span data-ttu-id="ac9b0-320">**TX_SUCCESS** (0x00) メモリ ブロックの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="ac9b0-321">**TX_PTR_ERROR** (0x03) メモリ ブロックへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-322">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-322">Allowed From</span></span>

<span data-ttu-id="ac9b0-323">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-324">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-324">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-325">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-326">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-326">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-327">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-327">See Also</span></span>

- <span data-ttu-id="ac9b0-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-328">tx_block_allocate</span></span>
- <span data-ttu-id="ac9b0-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-329">tx_block_pool_create</span></span>
- <span data-ttu-id="ac9b0-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="ac9b0-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="ac9b0-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-335">tx_byte_allocate</span></span>

<span data-ttu-id="ac9b0-336">メモリのバイト数の割り当て</span><span class="sxs-lookup"><span data-stu-id="ac9b0-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-337">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-338">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-338">Description</span></span>

<span data-ttu-id="ac9b0-339">このサービスを使用すると、指定したバイト数が、指定したメモリ バイト プールから割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-340">*アプリケーション コードで、割り当てられたメモリ ブロックの外部に書き込まないようにすることが重要です。これが発生すると、隣接する (通常は後続の) メモリ ブロックで破損が発生します。結果は予測不可能で、多くの場合、致命的です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-341">*このサービスのパフォーマンスは、ブロック サイズとプール内の断片化の量によって機能します。このため、このサービスは、実行のタイムクリティカルなスレッドでは使用しないでください。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-342">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-342">Parameters</span></span>

- <span data-ttu-id="ac9b0-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-343">**pool_ptr**</span></span> <br><span data-ttu-id="ac9b0-344">以前に作成されたメモリ ブロック プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="ac9b0-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-345">**memory_ptr**</span></span> <br><span data-ttu-id="ac9b0-346">目標メモリ ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="ac9b0-347">割り当てが正常に行われると、割り当てられたメモリ領域のアドレスが、このパラメーターが指す場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="ac9b0-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-348">**memory_size**</span></span> <br><span data-ttu-id="ac9b0-349">要求されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-349">Number of bytes requested.</span></span>
- <span data-ttu-id="ac9b0-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-350">**wait_option**</span></span> <br><span data-ttu-id="ac9b0-351">使用可能なメモリが不足している場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="ac9b0-352">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-353">**TX_NO_WAIT** (0x00000000) - **TX_NO_WAIT** を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-354">*これは、サービスが初期化から呼び出された場合に唯一有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="ac9b0-355">**TX_WAIT_FOREVER** (0xFFFFFFFF) - **TX_WAIT_FOREVER** を選択すると、呼び出し元のスレッドは、十分なメモリが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="ac9b0-356">*タイムアウト値* (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、メモリを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-357">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-357">Return Values</span></span>

- <span data-ttu-id="ac9b0-358">**TX_SUCCESS** (0x00) メモリの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="ac9b0-359">**TX_DELETED** (0x01) スレッドが中断されている間にメモリ プールが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-360">**TX_NO_MEMORY** (0x10) サービスは指定した待機時間内にメモリを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-361">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-362">**TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="ac9b0-363">**TX_PTR_ERROR** (0x03) 目標ポインターへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="ac9b0-364">**TX_SIZE_ERROR** (0X05) 要求されたサイズが 0 である、またはプールより大きい値です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="ac9b0-365">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="ac9b0-366">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-367">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-367">Allowed From</span></span>

<span data-ttu-id="ac9b0-368">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-369">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-369">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-370">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-371">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-371">Example</span></span>
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-372">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-372">See Also</span></span>

- <span data-ttu-id="ac9b0-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="ac9b0-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-380">tx_byte_pool_create</span></span>

<span data-ttu-id="ac9b0-381">メモリ バイト プールの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-382">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="ac9b0-383">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-383">Description</span></span>

<span data-ttu-id="ac9b0-384">このサービスを使用すると、指定した領域にメモリ バイト プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="ac9b0-385">プールは最初、基本的に 1 つの非常に大きな空きブロックで構成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="ac9b0-386">ただし、割り当てが行われると、プールは小さいブロックに分割されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-387">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-387">Parameters</span></span>

- <span data-ttu-id="ac9b0-388">**pool_ptr** メモリ プールの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="ac9b0-389">**name_ptr** メモリ プールの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="ac9b0-390">**pool_start** メモリ プールの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="ac9b0-391">開始アドレスは、ULONG データ型のサイズに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="ac9b0-392">**pool_size** メモリ プールで使用可能な合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-393">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-393">Return Values</span></span>

- <span data-ttu-id="ac9b0-394">**TX_SUCCESS** (0x00) メモリ プールの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="ac9b0-395">**TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="ac9b0-396">ポインターが NULL であるか、プールが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="ac9b0-397">**TX_PTR_ERROR** (0x03) プールの開始アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="ac9b0-398">**TX_SIZE_ERROR** (0x05) プールのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="ac9b0-399">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-400">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-400">Allowed From</span></span>

<span data-ttu-id="ac9b0-401">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-402">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-402">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-403">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-403">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-404">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-404">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-405">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-405">See Also</span></span>

- <span data-ttu-id="ac9b0-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-406">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="ac9b0-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="ac9b0-414">メモリ バイト プールの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-415">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-416">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-416">Description</span></span>

<span data-ttu-id="ac9b0-417">このサービスを使用すると、指定したメモリ バイト プールが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="ac9b0-418">このプールからのメモリを待機しているすべてのスレッドが再開され、**TX_DELETED** 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-419">*プールに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、サービスの完了後に利用できます。また、このアプリケーションでは削除されたプール、あるいは以前にそこから割り当てられたメモリの使用を防ぐ必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-420">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-420">Parameters</span></span>

- <span data-ttu-id="ac9b0-421">**pool_ptr** 以前に作成されたメモリ プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-422">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-422">Return Values</span></span>

- <span data-ttu-id="ac9b0-423">**TX_SUCCESS** (0x00) メモリ プールの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="ac9b0-424">**TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="ac9b0-425">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-426">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-426">Allowed From</span></span>

<span data-ttu-id="ac9b0-427">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-428">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-428">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-429">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-430">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-431">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-431">See Also</span></span>

- <span data-ttu-id="ac9b0-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-432">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="ac9b0-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="ac9b0-440">バイト プールに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-441">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-441">Prototype</span></span>

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="ac9b0-442">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-442">Description</span></span>

<span data-ttu-id="ac9b0-443">このサービスを使用すると、指定したメモリ バイト プールに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-444">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-444">Parameters</span></span>

- <span data-ttu-id="ac9b0-445">**pool_ptr** 以前に作成されたメモリ プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="ac9b0-446">**name** バイト プールの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="ac9b0-447">**available** プール内で使用可能なバイト数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="ac9b0-448">**fragments** バイト プール内のメモリ フラグメントの合計数の保存先のポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="ac9b0-449">**first_suspended** このバイト プールの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="ac9b0-450">**suspended_count** このバイト プールで現在中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="ac9b0-451">**next_pool** 次に作成されるバイト プールのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-452">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-453">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-453">Return Values</span></span>

- <span data-ttu-id="ac9b0-454">**TX_SUCCESS** (0x00) プールの情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="ac9b0-455">**TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-456">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-456">Allowed From</span></span>

<span data-ttu-id="ac9b0-457">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-458">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-458">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-459">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-459">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-460">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-460">Example</span></span>

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-461">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-461">See Also</span></span>

- <span data-ttu-id="ac9b0-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-462">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="ac9b0-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="ac9b0-470">バイト プールのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-471">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-471">Prototype</span></span>

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-472">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-472">Description</span></span>

<span data-ttu-id="ac9b0-473">このサービスを使用すると、指定したメモリ バイト プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-474">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-475">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-475">Parameters</span></span>

- <span data-ttu-id="ac9b0-476">**pool_ptr** 以前に作成されたメモリ バイト プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="ac9b0-477">**allocates** このプールで実行された割り当て要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="ac9b0-478">**releases** このプールで実行された解放要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="ac9b0-479">**fragments_searched** このプールで割り当て要求中に検索された内部メモリ フラグメントの数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="ac9b0-480">**merges** このプールで割り当て要求中に統合された内部メモリ ブロック数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="ac9b0-481">**splits** このプールで割り当て要求中に作成された内部メモリ ブロックの分割 (フラグメント) 数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="ac9b0-482">**suspensions** このプールのスレッド割り当て保留の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="ac9b0-483">**timeouts** このプールの割り当て保留タイムアウト数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-484">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-485">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-485">Return Values</span></span>

- <span data-ttu-id="ac9b0-486">**TX_SUCCESS** (0x00) バイト プールのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="ac9b0-487">**TX_PTR_ERROR** (0x03) バイト プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="ac9b0-488">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-489">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-489">Allowed From</span></span>

<span data-ttu-id="ac9b0-490">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-491">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-491">Example</span></span>

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="ac9b0-492">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-492">See Also</span></span>

- <span data-ttu-id="ac9b0-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-493">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="ac9b0-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-501">バイト プール システムのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-502">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-502">Prototype</span></span>

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="ac9b0-503">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-503">Description</span></span>

<span data-ttu-id="ac9b0-504">このサービスを使用すると、システム内のすべてのメモリ バイト プールに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-505">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-506">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-506">Parameters</span></span>

- <span data-ttu-id="ac9b0-507">**allocates** このプールで実行された割り当て要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="ac9b0-508">**releases** このプールで実行された解放要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="ac9b0-509">**fragments_searched** すべてのバイト プールで割り当て要求中に検索された内部メモリ フラグメントの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="ac9b0-510">**merges** すべてのバイト プールで割り当て要求中に統合された内部メモリ ブロックの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="ac9b0-511">**splits** すべてのバイト プールで割り当て要求中に作成された内部メモリ ブロックの分割 (フラグメント) の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="ac9b0-512">**suspensions** すべてのバイト プールのスレッド割り当て保留の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="ac9b0-513">**timeouts** すべてのバイト プールでの割り当て保留タイムアウトの合計の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-514">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-515">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-515">Return Values</span></span>

- <span data-ttu-id="ac9b0-516">**TX_SUCCESS** (0x00) バイト プールのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="ac9b0-517">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-518">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-518">Allowed From</span></span>

 <span data-ttu-id="ac9b0-519">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-520">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-520">Example</span></span>

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-521">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-521">See Also</span></span>

- <span data-ttu-id="ac9b0-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-522">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="ac9b0-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="ac9b0-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="ac9b0-530">バイト プールの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="ac9b0-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-531">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="ac9b0-532">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-532">Description</span></span>

<span data-ttu-id="ac9b0-533">このサービスを使用すると、このプール上のメモリで中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="ac9b0-534">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-535">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-535">Parameters</span></span>

- <span data-ttu-id="ac9b0-536">**pool_ptr** メモリ プールの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-537">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-537">Return Values</span></span>

- <span data-ttu-id="ac9b0-538">**TX_SUCCESS** (0x00) メモリ プールの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="ac9b0-539">**TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-540">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-540">Allowed From</span></span>

<span data-ttu-id="ac9b0-541">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-542">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-542">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-543">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-543">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-544">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-544">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-545">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-545">See Also</span></span>

- <span data-ttu-id="ac9b0-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-546">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="ac9b0-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="ac9b0-553">tx_byte_release</span></span>

<span data-ttu-id="ac9b0-554">メモリ プールへバイトを解放</span><span class="sxs-lookup"><span data-stu-id="ac9b0-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-555">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-556">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-556">Description</span></span>

<span data-ttu-id="ac9b0-557">このサービスを使用すると、以前に割り当てられたメモリ領域を、関連付けられているプールに解放します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="ac9b0-558">このプールからのメモリを待機しているスレッドが 1 つ以上ある場合、メモリが使い果たされるか、中断されたスレッドがなくなるまで、中断された各スレッドにメモリが割り当てられて再開されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="ac9b0-559">中断されたスレッドにメモリを割り当てるこのプロセスは、常に中断された最初のスレッドから開始されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-560">*アプリケーションは、解放された後にメモリ領域を使用しないようにする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-561">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-561">Parameters</span></span>

- <span data-ttu-id="ac9b0-562">**memory_ptr** 以前に割り当てられていたメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-563">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-563">Return Values</span></span>

- <span data-ttu-id="ac9b0-564">**TX_SUCCESS** (0x00) メモリの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="ac9b0-565">**TX_PTR_ERROR** (0x03) メモリ領域ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="ac9b0-566">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-567">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-567">Allowed From</span></span>

<span data-ttu-id="ac9b0-568">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-569">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-569">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-570">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-571">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-572">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-572">See Also</span></span>

- <span data-ttu-id="ac9b0-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-573">tx_byte_allocate</span></span>
- <span data-ttu-id="ac9b0-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="ac9b0-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="ac9b0-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="ac9b0-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="ac9b0-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-580">tx_event_flags_create</span></span>

<span data-ttu-id="ac9b0-581">イベント フラグ グループの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-582">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-583">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-583">Description</span></span>

<span data-ttu-id="ac9b0-584">このサービスを使用すると、32 個のイベント フラグのグループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="ac9b0-585">グループ内の 32 個すべてのイベント フラグが 0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="ac9b0-586">各イベント フラグは、1 つのビットで表されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-587">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-587">Parameters</span></span>

- <span data-ttu-id="ac9b0-588">**group_ptr** イベント フラグ グループ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="ac9b0-589">**name_ptr** イベント フラグ グループの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-590">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-590">Return Values</span></span>

- <span data-ttu-id="ac9b0-591">**TX_SUCCESS** (0x00) イベント グループの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="ac9b0-592">**TX_GROUP_ERROR** (0x06) イベント グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="ac9b0-593">ポインターが **NULL** であるか、イベント グループが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="ac9b0-594">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-595">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-595">Allowed From</span></span>

<span data-ttu-id="ac9b0-596">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-597">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-597">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-598">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-598">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-599">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-600">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-600">See Also</span></span>

- <span data-ttu-id="ac9b0-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-602">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-606">tx_event_flags_set</span></span>
- <span data-ttu-id="ac9b0-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="ac9b0-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-608">tx_event_flags_delete</span></span>

<span data-ttu-id="ac9b0-609">イベント フラグ グループの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-610">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-611">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-611">Description</span></span>

<span data-ttu-id="ac9b0-612">このサービスを使用すると、指定したイベント フラグ グループが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="ac9b0-613">このグループからのイベントを待機しているすべての中断スレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ac9b0-614">*アプリケーションは、このイベント フラグ グループを削除する前に、イベント フラグ グループに設定された通知コールバックが完了する (または無効になる) ようにしなければなりません。さらに、アプリケーションは、削除されたイベント フラグ グループがすべて今後使用されないようにしなければなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-615">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-615">Parameters</span></span>

- <span data-ttu-id="ac9b0-616">**group_ptr** 以前に作成されたイベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-617">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-617">Return Values</span></span>

- <span data-ttu-id="ac9b0-618">**TX_SUCCESS** (0x00) イベント フラグ グループの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="ac9b0-619">**TX_GROUP_ERROR** (0x06) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="ac9b0-620">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-621">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-621">Allowed From</span></span>

<span data-ttu-id="ac9b0-622">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-623">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-623">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-624">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-625">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-625">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-626">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-626">See Also</span></span>

- <span data-ttu-id="ac9b0-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-627">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-628">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-632">tx_event_flags_set</span></span>
- <span data-ttu-id="ac9b0-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="ac9b0-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-634">tx_event_flags_get</span></span>

<span data-ttu-id="ac9b0-635">イベント フラグ グループからのイベント フラグの取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-636">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-637">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-637">Description</span></span>

<span data-ttu-id="ac9b0-638">このサービスを使用すると、指定したイベント フラグ グループからイベント フラグが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="ac9b0-639">各イベント フラグ グループに 32 個のイベント フラグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="ac9b0-640">各フラグは、1 つのビットで表されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="ac9b0-641">このサービスを使用すると、入力パラメーターでの選択に従って、さまざまなイベント フラグの組み合わせを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-642">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-642">Parameters</span></span>

- <span data-ttu-id="ac9b0-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-643">**group_ptr**</span></span> <br><span data-ttu-id="ac9b0-644">以前に作成されたイベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="ac9b0-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-645">**requested_flags**</span></span> <br><span data-ttu-id="ac9b0-646">32 ビットの符号なし変数。要求されたイベントフラグを表します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="ac9b0-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-647">**get_option**</span></span> <br><span data-ttu-id="ac9b0-648">要求されるイベント フラグのすべてが必要か、あるいはいずれかが必要かを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="ac9b0-649">有効な選択を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-649">The following are valid selections:</span></span>

  - <span data-ttu-id="ac9b0-650">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="ac9b0-651">**TX_AND_CLEAR** (0x03)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="ac9b0-652">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="ac9b0-653">**TX_OR_CLEAR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="ac9b0-654">TX_AND または TX_AND_CLEAR を選択すると、すべてのイベント フラグがグループ内に存在しなければならないことが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="ac9b0-655">TX_OR または TX_OR_CLEAR を選択すると、任意のイベント フラグで十分であることが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="ac9b0-656">TX_AND_CLEAR または TX_OR_CLEAR が指定されている場合は、要求を満たすイベント フラグがクリアされます (ゼロに設定されます)。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="ac9b0-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="ac9b0-658">取得したイベント フラグが配置されている場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="ac9b0-659">取得した実際のフラグには、要求されなかったフラグが含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="ac9b0-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-660">**wait_option**</span></span>  <br><span data-ttu-id="ac9b0-661">選択したイベント フラグが設定されていない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="ac9b0-662">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-663">**TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-664">これは、初期化、タイマー、ISR など、サービスが非スレッドから呼び出された場合には唯一有効なオプションです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="ac9b0-665">**TX_WAIT_FOREVER** タイムアウト値 (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、イベントフラグが使用可能になるまで、呼び出し元のスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="ac9b0-666">タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、イベント フラグを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-667">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-667">Return Values</span></span>

- <span data-ttu-id="ac9b0-668">**TX_SUCCESS** (0x00) イベント フラグの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="ac9b0-669">**TX_DELETED** (0X01) スレッドが中断されている間にイベント フラグ グループが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-670">**TX_NO_EVENTS** (0x07) サービスで、指定されたイベントを指定された待機時間内に取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-671">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-672">**TX_GROUP_ERROR** (0x06) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="ac9b0-673">**TX_PTR_ERROR** (0x03) 実際のイベント フラグのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="ac9b0-674">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="ac9b0-675">**TX_OPTION_ERROR** (0x08) 無効な get オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-676">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-676">Allowed From</span></span>

<span data-ttu-id="ac9b0-677">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-678">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-678">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-679">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-680">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-680">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

<span data-ttu-id="ac9b0-681">**参照**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-681">**See Also**</span></span>

- <span data-ttu-id="ac9b0-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-682">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-687">tx_event_flags_set</span></span>
- <span data-ttu-id="ac9b0-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="ac9b0-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="ac9b0-690">イベント フラグ グループに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="ac9b0-691">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="ac9b0-692">**説明**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-692">**Description**</span></span>

<span data-ttu-id="ac9b0-693">このサービスを使用すると、指定したイベント フラグ グループに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="ac9b0-694">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-694">**Parameters**</span></span>

- <span data-ttu-id="ac9b0-695">**group_ptr** イベント フラグ グループ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="ac9b0-696">**name** イベント フラグ グループの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="ac9b0-697">**current_flags** イベント フラグ グループ内の現在の設定フラグの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="ac9b0-698">**first_suspended** このイベント フラグ グループの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="ac9b0-699">**suspended_count** このイベント フラグ グループで現在中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="ac9b0-700">**next_group** 次に作成されるイベント フラグ グループのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-701">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-702">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-702">Return Values</span></span>

- <span data-ttu-id="ac9b0-703">**TX_SUCCESS** (0x00) イベント グループ情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="ac9b0-704">**TX_GROUP_ERROR** (0x06) イベント グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-705">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-705">Allowed From</span></span>

<span data-ttu-id="ac9b0-706">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-707">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-707">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-708">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-708">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-709">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-709">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
<span data-ttu-id="ac9b0-710">**参照**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-710">**See Also**</span></span>

- <span data-ttu-id="ac9b0-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-711">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-713">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-716">tx_event_flags_set</span></span>
- <span data-ttu-id="ac9b0-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="ac9b0-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="ac9b0-719">イベント フラグ グループのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-720">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-721">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-721">Description</span></span>

<span data-ttu-id="ac9b0-722">このサービスを使用すると、指定したイベント フラグ グループに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-723">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-724">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-724">Parameters</span></span>

- <span data-ttu-id="ac9b0-725">**group_ptr** 以前に作成されたイベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="ac9b0-726">**sets** このグループで実行されたイベント フラグ設定要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="ac9b0-727">**gets** このグループで実行されたイベント フラグ取得要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="ac9b0-728">**suspensions** このグループのスレッド イベント フラグ取得中断数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="ac9b0-729">**timeouts** このグループのイベント フラグ取得中断タイムアウト数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-730">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-731">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-731">Return Values</span></span>

- <span data-ttu-id="ac9b0-732">**TX_SUCCESS** (0x00) イベント フラグ グループのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="ac9b0-733">**TX_PTR_ERROR** (0x03) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="ac9b0-734">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-735">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-735">Allowed From</span></span>

<span data-ttu-id="ac9b0-736">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-737">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-737">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-738">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-738">See Also</span></span>

- <span data-ttu-id="ac9b0-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-739">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-741">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-744">tx_event_flags_set</span></span>
- <span data-ttu-id="ac9b0-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="ac9b0-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-747">パフォーマンス システム情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-748">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-749">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-749">Description</span></span>

<span data-ttu-id="ac9b0-750">このサービスを使用すると、システム内のすべてのイベント フラグ グループに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-751">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-752">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-752">Parameters</span></span>

- <span data-ttu-id="ac9b0-753">**sets** すべてのグループで実行されたイベント フラグ設定要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="ac9b0-754">**gets** すべてのグループで実行されたイベント フラグ取得要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="ac9b0-755">**suspensions** すべてのグループのスレッド イベント フラグ取得中断の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="ac9b0-756">**timeouts** すべてのグループのイベント フラグ取得中断タイムアウトの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-757">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-758">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-758">Return Values</span></span>

- <span data-ttu-id="ac9b0-759">**TX_SUCCESS** (0x00) イベント フラグ システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="ac9b0-760">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-761">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-761">Example</span></span>

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-762">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-762">See Also</span></span>

- <span data-ttu-id="ac9b0-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-763">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-765">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-768">tx_event_flags_set</span></span>
- <span data-ttu-id="ac9b0-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="ac9b0-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-770">tx_event_flags_set</span></span>

<span data-ttu-id="ac9b0-771">イベント フラグ グループのイベント フラグの設定</span><span class="sxs-lookup"><span data-stu-id="ac9b0-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-772">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-773">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-773">Description</span></span>

<span data-ttu-id="ac9b0-774">このサービスを使用すると、指定した set オプションに応じて、イベント フラグ グループ内のイベント フラグが設定またはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="ac9b0-775">イベント フラグ要求が現在満たされているすべての中断スレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-776">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-776">Parameters</span></span>

- <span data-ttu-id="ac9b0-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-777">**group_ptr**</span></span> <br><span data-ttu-id="ac9b0-778">以前に作成されたイベント フラグ グループ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="ac9b0-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-779">**flags_to_set**</span></span> <br><span data-ttu-id="ac9b0-780">選択した set オプションに基づいて設定またはクリアするイベント フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="ac9b0-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-781">**set_option**</span></span> <br><span data-ttu-id="ac9b0-782">指定されたイベント フラグをグループの現在のイベント フラグへ AND演算するか OR 演算するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="ac9b0-783">有効な選択を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-783">The following are valid selections:</span></span>
  - <span data-ttu-id="ac9b0-784">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="ac9b0-785">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="ac9b0-786">TX_AND を選択すると、指定されたイベント フラグがグループの現在のイベント フラグへ **AND** 演算することが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="ac9b0-787">このオプションは、グループ内のイベント フラグをクリアするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="ac9b0-788">あるいは、TX_OR が指定されている場合、指定されたイベント フラグは、グループ内の現在のイベントへ **OR** 演算されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-789">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-789">Return Values</span></span>
- <span data-ttu-id="ac9b0-790">**TX_SUCCESS** (0x00) イベント フラグの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="ac9b0-791">**TX_GROUP_ERROR** (0x06) イベント フラグ グループへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="ac9b0-792">**TX_OPTION_ERROR** (0x08) 無効な set オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-793">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-793">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-794">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-795">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-795">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-796">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-796">See Also</span></span>

- <span data-ttu-id="ac9b0-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-797">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-799">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="ac9b0-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="ac9b0-805">イベント フラグの設定時にアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="ac9b0-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-806">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="ac9b0-807">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-807">Description</span></span>

<span data-ttu-id="ac9b0-808">このサービスを使用すると、指定したイベント フラグ グループで 1 つ以上のイベント フラグが設定されるたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="ac9b0-809">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-810">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-810">Parameters</span></span>
- <span data-ttu-id="ac9b0-811">**group_ptr** 以前に作成されたイベント フラグ グループへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="ac9b0-812">**events_set_notify** アプリケーションのイベント フラグ設定通知関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="ac9b0-813">この値が TX_NULL の場合は、通知が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-814">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-814">Return Values</span></span>

- <span data-ttu-id="ac9b0-815">**TX_SUCCESS** (0x00) イベント フラグ設定通知の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="ac9b0-816">**TX_GROUP_ERROR** (0x06) イベント フラグ グループ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="ac9b0-817">**TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-818">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-818">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-819">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-819">See Also</span></span>

- <span data-ttu-id="ac9b0-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-820">tx_event_flags_create</span></span>
- <span data-ttu-id="ac9b0-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="ac9b0-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-822">tx_event_flags_get</span></span>
- <span data-ttu-id="ac9b0-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="ac9b0-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="ac9b0-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="ac9b0-827">tx_interrupt_control</span></span>

<span data-ttu-id="ac9b0-828">割り込みを有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="ac9b0-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-829">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="ac9b0-830">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-830">Description</span></span>

<span data-ttu-id="ac9b0-831">このサービスを使用すると、入力パラメーター *new_posture* の指定に従って割り込みが有効または無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-832">*このサービスがアプリケーション スレッドから呼び出された場合、割り込み状態はそのスレッドのコンテキストの一部のままになります。たとえば、スレッドがこのルーチンを呼び出して割り込みを無効にしてから中断した場合、再開されたとき、割り込みが再び無効になります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="ac9b0-833">*このサービスを使用して、初期化中に割り込みを有効にしないでください。予期しない結果が起きる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-834">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-834">Parameters</span></span>

- <span data-ttu-id="ac9b0-835">**new_posture** このパラメーターは、割り込みを無効にするか有効にするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="ac9b0-836">有効な値は、**TX_INT_DISABLE** と **TX_INT_ENABLE** です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="ac9b0-837">これらのパラメーターの実際の値はポートに固有です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="ac9b0-838">さらに、一部の処理アーキテクチャで追加の割り込み無効状態がサポートされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-839">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-839">Return Values</span></span>
- <span data-ttu-id="ac9b0-840">**前の状態** このサービスは、前の割り込み状態を呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="ac9b0-841">これにより、サービスのユーザーが、割り込みが無効になった後に前の状態を復元できます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-842">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-842">Allowed From</span></span>

<span data-ttu-id="ac9b0-843">スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-844">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-844">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-845">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-845">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-846">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-847">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-847">See Also</span></span>

<span data-ttu-id="ac9b0-848">None</span><span class="sxs-lookup"><span data-stu-id="ac9b0-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="ac9b0-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-849">tx_mutex_create</span></span>

<span data-ttu-id="ac9b0-850">相互排他ミューテックスの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-851">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="ac9b0-852">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-852">Description</span></span>

<span data-ttu-id="ac9b0-853">このサービスを使用すると、リソース保護のためにスレッド間の相互排他を行うミューテックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-854">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-854">Parameters</span></span>

- <span data-ttu-id="ac9b0-855">**mutex_ptr** ミューテックス制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="ac9b0-856">**name_ptr** ミューテックスの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="ac9b0-857">**priority_inherit** このミューテックスが優先度の継承をサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="ac9b0-858">この値が TX_INHERIT の場合、優先度の継承がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="ac9b0-859">ただし、TX_NO_INHERIT が指定された場合、このミューテックスでは優先度の継承がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-860">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-860">Return Values</span></span>

- <span data-ttu-id="ac9b0-861">**TX_SUCCESS** (0x00) ミューテックスの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="ac9b0-862">**TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="ac9b0-863">ポインターが NULL であるか、ミューテックスが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="ac9b0-864">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="ac9b0-865">**TX_INHERIT_ERROR** (0x1F) 優先度継承パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-866">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-866">Allowed From</span></span>

<span data-ttu-id="ac9b0-867">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-868">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-868">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-869">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-869">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-870">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-870">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-871">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-871">See Also</span></span>

- <span data-ttu-id="ac9b0-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-872">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-873">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="ac9b0-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="ac9b0-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-879">tx_mutex_delete</span></span>

<span data-ttu-id="ac9b0-880">相互排他ミューテックスの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-881">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-882">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-882">Description</span></span>

<span data-ttu-id="ac9b0-883">このサービスを使用すると、指定したミューテックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="ac9b0-884">ミューテックスを待機しているすべてのスレッドが再開され、**TX_DELETED** 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-885">*削除されたミューテックスを使用できないようにするのは、アプリケーションの役割です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-886">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-886">Parameters</span></span>

- <span data-ttu-id="ac9b0-887">**mutex_ptr** 以前作成されたミューテックスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-888">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-888">Return Values</span></span>

- <span data-ttu-id="ac9b0-889">**TX_SUCCESS** (0x00) ミューテックスの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="ac9b0-890">**TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="ac9b0-891">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-892">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-892">Allowed From</span></span>

<span data-ttu-id="ac9b0-893">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-894">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-894">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-895">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-896">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-897">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-897">See Also</span></span>

- <span data-ttu-id="ac9b0-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-898">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-899">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="ac9b0-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="ac9b0-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-905">tx_mutex_get</span></span>

<span data-ttu-id="ac9b0-906">ミューテックスの所有権の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-907">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-908">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-908">Description</span></span>

<span data-ttu-id="ac9b0-909">このサービスは、指定したミューテックスの排他的所有権の取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="ac9b0-910">呼び出し元のスレッドによって既にミューテックスが所有されている場合は、内部カウンターがインクリメントされ、成功ステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="ac9b0-911">ミューテックスが別のスレッドによって所有されており、このスレッドの優先度が高く、優先度の継承がミューテックス作成時に指定されている場合、低優先度スレッドの優先度は一時的に呼び出し元スレッドの優先度まで上昇します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-912">*優先度の継承が指定されたミューテックスを所有する低優先度スレッドの優先度を、ミューテックス所有権を有している間に外部スレッドによって変更しないでください。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-913">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-913">Parameters</span></span>

- <span data-ttu-id="ac9b0-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="ac9b0-915">以前に作成されたミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="ac9b0-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-916">**wait_option**</span></span> <br><span data-ttu-id="ac9b0-917">ミューテックスが既に別のスレッドによって所有されている場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="ac9b0-918">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-919">**TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-920">*これは、サービスが初期化から呼び出された場合に唯一有効なオプションです。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="ac9b0-921">**TX_WAIT_FOREVER** タイムアウト (0xFFFFFFFF) - **TX_WAIT_FOREVER** を選択すると、ミューテックスが使用可能になるまで、呼び出し元のスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="ac9b0-922">タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、ミューテックスを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-923">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-923">Return Values</span></span>

- <span data-ttu-id="ac9b0-924">**TX_SUCCESS** (0x00) ミューテックスの取得操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="ac9b0-925">**TX_DELETED** (0x01) スレッドが中断されている間にミューテックスが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-926">**TX_NOT_AVAILABLE** (0x1D) 指定された待機時間内にサービスでミューテックスの所有権を取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-927">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-928">**TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="ac9b0-929">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="ac9b0-930">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-931">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-931">Allowed From</span></span>

<span data-ttu-id="ac9b0-932">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-933">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-933">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-934">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-935">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-936">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-936">See Also</span></span>

- <span data-ttu-id="ac9b0-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-937">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-938">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="ac9b0-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="ac9b0-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-944">tx_mutex_info_get</span></span>

<span data-ttu-id="ac9b0-945">ミューテックスに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-946">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-946">Prototype</span></span>

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a><span data-ttu-id="ac9b0-947">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-947">Description</span></span>

<span data-ttu-id="ac9b0-948">このサービスを使用すると、指定したミューテックスから情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-949">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-949">Parameters</span></span>

- <span data-ttu-id="ac9b0-950">**mutex_ptr** ミューテックス制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="ac9b0-951">**name** ミューテックスの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="ac9b0-952">**count** ミューテックスの所有権数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="ac9b0-953">**owner** 所有スレッドのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="ac9b0-954">**first_suspended** このミューテックスの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="ac9b0-955">**suspended_count** このミューテックスで現在中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="ac9b0-956">**next_mutex** 次に作成されるミューテックスへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-957">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-958">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-958">Return Values</span></span>

- <span data-ttu-id="ac9b0-959">**TX_SUCCESS** (0x00) ミューテックス情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="ac9b0-960">**TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-961">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-961">Allowed From</span></span>

<span data-ttu-id="ac9b0-962">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-963">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-963">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-964">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-964">No</span></span>

<span data-ttu-id="ac9b0-965">**例**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-965">**Example**</span></span>

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-966">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-966">See Also</span></span>

- <span data-ttu-id="ac9b0-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-967">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-968">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-969">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="ac9b0-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="ac9b0-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="ac9b0-975">ミューテックス パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-976">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-976">Prototype</span></span>

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="ac9b0-977">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-977">Description</span></span>

<span data-ttu-id="ac9b0-978">このサービスを使用すると、指定したミューテックスに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-979">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-980">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-980">Parameters</span></span>

- <span data-ttu-id="ac9b0-981">**mutex_ptr** 以前作成されたミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="ac9b0-982">**puts** このミューテックスで実行された put 要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="ac9b0-983">**gets** このミューテックスで実行された取得要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="ac9b0-984">**suspensions** このミューテックスのスレッド ミューテックス取得中断数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="ac9b0-985">**timeouts** このミューテックスのミューテックス取得中断タイムアウト数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="ac9b0-986">**inversions** このミューテックスのスレッド優先度逆転数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="ac9b0-987">**inheritances** このミューテックスのスレッド優先度継承操作の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-988">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-989">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-989">Return Values</span></span>

- <span data-ttu-id="ac9b0-990">**TX_SUCCESS** (0x00) ミューテックスのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="ac9b0-991">**TX_PTR_ERROR** (0x03) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="ac9b0-992">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-993">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-993">Allowed From</span></span>

<span data-ttu-id="ac9b0-994">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-995">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-995">Example</span></span>

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-996">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-996">See Also</span></span>

- <span data-ttu-id="ac9b0-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-997">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-998">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-999">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="ac9b0-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="ac9b0-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-1005">ミューテックスのシステム パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1006">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1007">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1007">Description</span></span>

<span data-ttu-id="ac9b0-1008">このサービスを使用すると、システム内のすべてのミューテックスに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1009">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1010">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1010">Parameters</span></span>

- <span data-ttu-id="ac9b0-1011">**puts** すべてのミューテックスで実行された配置要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="ac9b0-1012">**gets** すべてのミューテックスで実行された取得要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="ac9b0-1013">**suspensions** すべてのミューテックスのスレッド ミューテックス取得中断の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="ac9b0-1014">**timeouts** すべてのミューテックスのミューテックス取得中断タイムアウトの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="ac9b0-1015">**inversions** すべてのミューテックスのスレッド優先度逆転の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="ac9b0-1016">**inheritances** すべてのミューテックスのスレッド優先度の継承操作の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1017">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1018">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1018">Return Values</span></span>

- <span data-ttu-id="ac9b0-1019">**TX_SUCCESS** (0x00) ミューテックスのシステム パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="ac9b0-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1021">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1021">Allowed From</span></span>

<span data-ttu-id="ac9b0-1022">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1023">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1023">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1024">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1024">See Also</span></span>

- <span data-ttu-id="ac9b0-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1025">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1027">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="ac9b0-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="ac9b0-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="ac9b0-1033">ミューテックスの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1034">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1035">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1035">Description</span></span>

<span data-ttu-id="ac9b0-1036">このサービスを使用すると、このミューテックスの所有権に対して中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="ac9b0-1037">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1038">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1038">Parameters</span></span>

- <span data-ttu-id="ac9b0-1039">**mutex_ptr** 以前に作成されたミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1040">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1040">Return Values</span></span>

- <span data-ttu-id="ac9b0-1041">**TX_SUCCESS** (0x00) ミューテックスの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="ac9b0-1042">**TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1043">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1043">Allowed From</span></span>

<span data-ttu-id="ac9b0-1044">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1045">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1045">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1046">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1047">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1047">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1048">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1048">See Also</span></span>

- <span data-ttu-id="ac9b0-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1049">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1051">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="ac9b0-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1056">tx_mutex_put</span></span>

<span data-ttu-id="ac9b0-1057">ミューテックスの所有権を解放</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1058">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1059">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1059">Description</span></span>

<span data-ttu-id="ac9b0-1060">このサービスを使用すると、指定したミューテックスの所有権カウントが減ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="ac9b0-1061">所有権カウントがゼロの場合は、ミューテックスが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1062">*ミューテックスの作成時に優先度の継承が選択された場合、解放するスレッドの優先度は、最初にミューテックスの所有権を取得したときの優先度に復元されます。解放するスレッドがミューテックスを所有している間に行われた他の優先度の変更は元に戻されます。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1063">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1063">Parameters</span></span>
- <span data-ttu-id="ac9b0-1064">mutex_ptr 以前に作成されたミューテックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1065">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1065">Return Values</span></span>
- <span data-ttu-id="ac9b0-1066">**TX_SUCCESS** (0x00) ミューテックスの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="ac9b0-1067">**TX_NOT_OWNED** (0x1E) ミューテックスが呼び出し元によって所有されていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="ac9b0-1068">**TX_MUTEX_ERROR** (0x1C) ミューテックスへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="ac9b0-1069">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1070">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1070">Allowed From</span></span>

<span data-ttu-id="ac9b0-1071">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1072">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1072">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1073">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1074">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1075">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1075">See Also</span></span>

- <span data-ttu-id="ac9b0-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1076">tx_mutex_create</span></span>
- <span data-ttu-id="ac9b0-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="ac9b0-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1078">tx_mutex_get</span></span>
- <span data-ttu-id="ac9b0-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="ac9b0-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="ac9b0-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1083">tx_queue_create</span></span>

<span data-ttu-id="ac9b0-1084">メッセージ キューの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1085">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1086">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1086">Description</span></span>

<span data-ttu-id="ac9b0-1087">このサービスを使用すると、主にスレッド間通信に使用される、メッセージ キューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="ac9b0-1088">メッセージの合計数は、指定したメッセージ サイズと、キュー内の合計バイト数から計算されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1089">*キューのメモリ領域で指定された合計バイト数が、指定したメッセージ サイズで均等に割り切れない場合、メモリ領域の残りのバイトは使用されません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1090">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1090">Parameters</span></span>

- <span data-ttu-id="ac9b0-1091">**queue_ptr** メッセージ キュー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="ac9b0-1092">**name_ptr** メッセージ キューの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="ac9b0-1093">**message_size** キュー内の各メッセージのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="ac9b0-1094">メッセージのサイズは、32 ビットの 1 ワードから 32 ビットの 16 ワードまでの範囲です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="ac9b0-1095">有効なメッセージ サイズのオプションは、1 から 16 の数値です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="ac9b0-1096">**queue_start** メッセージ キューの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="ac9b0-1097">開始アドレスは、ULONG データ型のサイズに合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="ac9b0-1098">**queue_size** メッセージ キューで使用可能な合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1099">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1099">Return Values</span></span>

- <span data-ttu-id="ac9b0-1100">**TX_SUCCESS** (0x00) メッセージ キューの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="ac9b0-1101">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="ac9b0-1102">ポインターが NULL であるか、キューが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="ac9b0-1103">**TX_PTR_ERROR** (0x03) メッセージ キューの開始アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="ac9b0-1104">**TX_SIZE_ERROR** (0x05) メッセージ キューのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="ac9b0-1105">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1106">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1106">Allowed From</span></span>

<span data-ttu-id="ac9b0-1107">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1108">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1108">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1109">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1110">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1110">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1111">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1111">See Also</span></span>

- <span data-ttu-id="ac9b0-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1112">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1113">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1119">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1120">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="ac9b0-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1122">tx_queue_delete</span></span>

<span data-ttu-id="ac9b0-1123">メッセージ キューの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1124">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1125">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1125">Description</span></span>

<span data-ttu-id="ac9b0-1126">このサービスを使用すると、指定したメッセージ キューが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="ac9b0-1127">このキューからのメッセージを待機しているすべてのスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ac9b0-1128">*アプリケーションは、このキューの送信通知コールバックが、キューを削除する前に完了する (または無効になる) ようにしなければなりません。さらに、アプリケーションは、削除されたキューが今後使用されないようにしなければなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="ac9b0-1129">*キューに関連付けられているメモリ領域を管理するのもアプリケーションの役割です。これは、サービスの完了後にも利用できます。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1130">Parameters</span></span>

- <span data-ttu-id="ac9b0-1131">**queue_ptr** 以前に作成されたメッセージ キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1132">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1132">Return Values</span></span>

- <span data-ttu-id="ac9b0-1133">**TX_SUCCESS** (0x00) 正常にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="ac9b0-1134">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="ac9b0-1135">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1136">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1136">Allowed From</span></span>

<span data-ttu-id="ac9b0-1137">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1138">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1138">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1139">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1140">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1140">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1141">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1141">See Also</span></span>

- <span data-ttu-id="ac9b0-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1142">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1143">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1149">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1150">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="ac9b0-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1152">tx_queue_flush</span></span>

<span data-ttu-id="ac9b0-1153">メッセージ キューのメッセージを空にする</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1155">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1155">Description</span></span>

<span data-ttu-id="ac9b0-1156">このサービスを使用すると、指定したメッセージ キューに格納されているすべてのメッセージが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="ac9b0-1157">キューがいっぱいの場合、中断されたすべてのスレッドのメッセージが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="ac9b0-1158">中断された各スレッドが、メッセージ送信が成功したことを示す戻りステータスで再開されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="ac9b0-1159">キューが空の場合、このサービスは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1160">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1160">Parameters</span></span>

- <span data-ttu-id="ac9b0-1161">**queue_ptr** 以前に作成されたメッセージ キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1162">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1162">Return Values</span></span>

- <span data-ttu-id="ac9b0-1163">**TX_SUCCESS** (0x00) メッセージ キューのフラッシュが成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="ac9b0-1164">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1165">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1165">Allowed From</span></span>

<span data-ttu-id="ac9b0-1166">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1167">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1167">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1168">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1169">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1169">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1170">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1170">See Also</span></span>

- <span data-ttu-id="ac9b0-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1171">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1172">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1178">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1179">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="ac9b0-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1181">tx_queue_front_send</span></span>

<span data-ttu-id="ac9b0-1182">メッセージをキューの先頭に送る</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1183">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1184">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1184">Description</span></span>

<span data-ttu-id="ac9b0-1185">このサービスを使用すると、メッセージが指定したメッセージ キューの先頭の場所に送られます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="ac9b0-1186">メッセージは、ソース ポインターによって指定されたメモリ領域からキューの先頭に **コピー** されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1187">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1187">Parameters</span></span>

- <span data-ttu-id="ac9b0-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1188">**queue_ptr**</span></span> <br><span data-ttu-id="ac9b0-1189">メッセージ キュー コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="ac9b0-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1190">**source_ptr**</span></span> <br><span data-ttu-id="ac9b0-1191">メッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1191">Pointer to the message.</span></span>
- <span data-ttu-id="ac9b0-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1192">**wait_option**</span></span>  <br><span data-ttu-id="ac9b0-1193">メッセージ キューがいっぱいの場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="ac9b0-1194">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-1195">**TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-1196">*これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="ac9b0-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、キューに空きができるまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="ac9b0-1198">タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、キューに空きができるのを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1199">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1199">Return Values</span></span>

- <span data-ttu-id="ac9b0-1200">**TX_SUCCESS** (0x00) メッセージの送信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="ac9b0-1201">**TX_DELETED** (0x01) スレッドが中断されている間にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-1202">**TX_QUEUE_FULL** (0x0B) 指定された待機時間の間キューがいっぱいだったため、サービスがメッセージを送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-1203">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-1204">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="ac9b0-1205">**TX_PTR_ERROR** (0x03) メッセージのソース ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="ac9b0-1206">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1207">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1207">Allowed From</span></span>

<span data-ttu-id="ac9b0-1208">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1209">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1209">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1210">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1211">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1211">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1212">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1212">See Also</span></span>

- <span data-ttu-id="ac9b0-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1213">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1214">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1215">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1220">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1221">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="ac9b0-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1223">tx_queue_info_get</span></span>

<span data-ttu-id="ac9b0-1224">キューに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1225">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1225">Prototype</span></span>

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1226">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1226">Description</span></span>

<span data-ttu-id="ac9b0-1227">このサービスを使用すると、指定したメッセージ キューに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1228">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1228">Parameters</span></span>

- <span data-ttu-id="ac9b0-1229">**queue_ptr** 以前に作成されたメッセージ キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="ac9b0-1230">**name** キューの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="ac9b0-1231">**enqueued** 現在キューに入っているメッセージ数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="ac9b0-1232">**available_storage** キューに現在余裕があるメッセージ数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="ac9b0-1233">**first_suspended** このキューの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="ac9b0-1234">**suspended_count** このキューで現在中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="ac9b0-1235">**next_queue** 次に作成されるキューのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1236">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1237">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1237">Return Values</span></span>

- <span data-ttu-id="ac9b0-1238">**TX_SUCCESS** (0x00) キュー情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="ac9b0-1239">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1240">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1240">Allowed From</span></span>

<span data-ttu-id="ac9b0-1241">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1242">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1242">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1243">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1244">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1244">Example</span></span>

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1245">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1245">See Also</span></span>

- <span data-ttu-id="ac9b0-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1246">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1247">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1248">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1253">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1254">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="ac9b0-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="ac9b0-1257">キュー パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1258">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1258">Prototype</span></span>

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1259">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1259">Description</span></span>

<span data-ttu-id="ac9b0-1260">このサービスを使用すると、指定したキューに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1261">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ "_を使用してビルドする必要があります。*"</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1262">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1262">Parameters</span></span>

- <span data-ttu-id="ac9b0-1263">**queue_ptr** 以前に作成されたキューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="ac9b0-1264">**messages_sent** このキューで実行される送信要求の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="ac9b0-1265">**messages_received** このキューで実行される受信要求の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="ac9b0-1266">**empty_suspensions** このキューでキューが空になった中断数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="ac9b0-1267">**empty_suspensions** このキューでキューが満杯になった中断数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="ac9b0-1268">**full_errors** このキューでキューが満杯になったエラー数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="ac9b0-1269">**timeouts** このキューのスレッド中断タイムアウトの数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1270">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1271">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1271">Return Values</span></span>

- <span data-ttu-id="ac9b0-1272">**TX_SUCCESS** (0x00) キューのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="ac9b0-1273">**TX_PTR_ERROR** (0x03) キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="ac9b0-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1275">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1275">Allowed From</span></span>

<span data-ttu-id="ac9b0-1276">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1277">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1277">Example</span></span>

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1278">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1278">See Also</span></span>

- <span data-ttu-id="ac9b0-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1279">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1280">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1281">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1286">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1287">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="ac9b0-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-1290">キュー システム パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1291">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1292">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1292">Description</span></span>

<span data-ttu-id="ac9b0-1293">このサービスを使用すると、システム内のすべてのキューに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1294">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ "_を使用してビルドする必要があります。*"</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1295">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1295">Parameters</span></span>

- <span data-ttu-id="ac9b0-1296">**messages_sent** すべてのキューで実行される送信要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="ac9b0-1297">**messages_received** すべてのキューで実行される受信要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="ac9b0-1298">**empty_suspensions** すべてのキューでキューが空になった中断の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="ac9b0-1299">ほ **full_suspensions** すべてのキューでキューが満杯になった中断の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="ac9b0-1300">**full_errors** すべてのキューでキューが満杯になったエラーの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="ac9b0-1301">**timeouts** すべてのキューのスレッド保留タイムアウトの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1302">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="ac9b0-1303">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1303">**Return Values**</span></span>

- <span data-ttu-id="ac9b0-1304">**TX_SUCCESS** (0x00) キュー システムのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="ac9b0-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1306">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1306">Allowed From</span></span>

<span data-ttu-id="ac9b0-1307">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1308">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1308">Example</span></span>

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1309">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1309">See Also</span></span>

- <span data-ttu-id="ac9b0-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1310">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1311">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1312">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1317">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1318">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="ac9b0-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="ac9b0-1321">キューの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1322">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1323">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1323">Description</span></span>

<span data-ttu-id="ac9b0-1324">このサービスを使用すると、メッセージで中断された (またはメッセージを配置する) 最も優先度の高いスレッドがこのキューで中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="ac9b0-1325">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1326">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1326">Parameters</span></span>

- <span data-ttu-id="ac9b0-1327">**queue_ptr** 以前に作成されたメッセージ キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1328">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1328">Return Values</span></span>

- <span data-ttu-id="ac9b0-1329">**TX_SUCCESS** (0x00) キューの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="ac9b0-1330">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1331">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1331">Allowed From</span></span>

<span data-ttu-id="ac9b0-1332">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1333">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1333">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1334">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1335">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1335">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1336">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1336">See Also</span></span>

- <span data-ttu-id="ac9b0-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1337">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1338">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1339">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1344">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1345">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="ac9b0-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1347">tx_queue_receive</span></span>

<span data-ttu-id="ac9b0-1348">メッセージ キューからのメッセージの取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1349">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1350">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1350">Description</span></span>

<span data-ttu-id="ac9b0-1351">このサービスは、指定されたメッセージ キューからメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="ac9b0-1352">取得されたメッセージは、キューから目標ポインターによって指定されたメモリ領域に **コピー** されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="ac9b0-1353">そのメッセージは、その後キューから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1354">*指定された目標メモリ領域は、メッセージを保持できるだけの大きさでなければなりません。つまり、*  \***destination_ptr** _ _によりポイントされるメッセージ送信先は、少なくともこのキューのメッセージ サイズと同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="ac9b0-1355">それ以外の場合、目標の容量が十分でないと、メモリ破損が次のメモリ領域で発生します。\*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1356">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1356">Parameters</span></span>

- <span data-ttu-id="ac9b0-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1357">**queue_ptr**</span></span> <br><span data-ttu-id="ac9b0-1358">以前に作成されたメッセージ キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="ac9b0-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1359">**destination_ptr**</span></span> <br><span data-ttu-id="ac9b0-1360">メッセージのコピー先の場所。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="ac9b0-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1361">**wait_option**</span></span> <br><span data-ttu-id="ac9b0-1362">メッセージ キューが空の場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="ac9b0-1363">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-1364">**TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-1365">これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="ac9b0-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、メッセージが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="ac9b0-1367">タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、メッセージを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1368">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1368">Return Values</span></span>

- <span data-ttu-id="ac9b0-1369">**TX_SUCCESS** (0x00) メッセージの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="ac9b0-1370">**TX_DELETED** (0x01) スレッドが中断されている間にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-1371">**TX_QUEUE_EMPTY** (0x0A) 指定された待機時間の間キューが空だったため、サービスはメッセージを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-1372">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-1373">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="ac9b0-1374">**TX_PTR_ERROR** (0x03) メッセージの目標ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="ac9b0-1375">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1376">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1376">Allowed From</span></span>

<span data-ttu-id="ac9b0-1377">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1378">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1378">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1379">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1380">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1380">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1381">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1381">See Also</span></span>

- <span data-ttu-id="ac9b0-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1382">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1383">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1384">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1390">tx_queue_send</span></span>
- <span data-ttu-id="ac9b0-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="ac9b0-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1392">tx_queue_send</span></span>

<span data-ttu-id="ac9b0-1393">メッセージ キューへのメッセージの送信</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1394">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1395">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1395">Description</span></span>

<span data-ttu-id="ac9b0-1396">このサービスを使用すると、指定したメッセージ キューにメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="ac9b0-1397">送信されたメッセージは、ソース ポインターによって指定されたメモリ領域からキューに **コピー** されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1398">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1398">Parameters</span></span>
- <span data-ttu-id="ac9b0-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1399">**queue_ptr**</span></span> <br><span data-ttu-id="ac9b0-1400">以前に作成されたメッセージ キューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="ac9b0-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1401">**source_ptr**</span></span> <br><span data-ttu-id="ac9b0-1402">メッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1402">Pointer to the message.</span></span>
- <span data-ttu-id="ac9b0-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1403">**wait_option**</span></span> <br><span data-ttu-id="ac9b0-1404">メッセージ キューがいっぱいの場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="ac9b0-1405">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-1406">**TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-1407">*これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです*。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="ac9b0-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、キューに空きができるまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="ac9b0-1409">タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、キューに空きができるのを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1410">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1410">Return Values</span></span>

- <span data-ttu-id="ac9b0-1411">**TX_SUCCESS** (0x00) メッセージの送信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="ac9b0-1412">**TX_DELETED** (0x01) スレッドが中断されている間にメッセージ キューが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-1413">**TX_QUEUE_FULL** (0x0B) 指定された待機時間の間キューがいっぱいだったため、サービスがメッセージを送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="ac9b0-1414">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-1415">**TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="ac9b0-1416">**TX_PTR_ERROR** (0x03) メッセージのソース ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="ac9b0-1417">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1418">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1418">Allowed From</span></span>

<span data-ttu-id="ac9b0-1419">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1420">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1420">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1421">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1422">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1422">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

<span data-ttu-id="ac9b0-1423">**参照**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1423">**See Also**</span></span>

- <span data-ttu-id="ac9b0-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1424">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1425">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1426">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1432">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="ac9b0-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="ac9b0-1435">メッセージがキューに送信されるときアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1436">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="ac9b0-1437">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1437">Description</span></span>

<span data-ttu-id="ac9b0-1438">このサービスを使用すると、指定されたキューにメッセージが送信されるたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="ac9b0-1439">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="ac9b0-1440">*アプリケーションのキュー送信通知コールバックで、中断オプションを指定した ThreadX API を呼び出してはなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1441">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1441">Parameters</span></span>

- <span data-ttu-id="ac9b0-1442">**queue_ptr** 以前に作成されたキューへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="ac9b0-1443">**queue_send_notify** アプリケーションのキュー送信通知関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="ac9b0-1444">この値が TX_NULL の場合は、通知が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1445">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1445">Return Values</span></span>

- <span data-ttu-id="ac9b0-1446">**TX_SUCCESS** (0x00) キュー送信通知の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="ac9b0-1447">**TX_QUEUE_ERROR** (0x09) キュー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="ac9b0-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1449">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1449">Allowed From</span></span>

<span data-ttu-id="ac9b0-1450">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1451">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1451">Example</span></span>

```c
TX_QUEUE my_queue;
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

### <a name="see-also"></a><span data-ttu-id="ac9b0-1452">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1452">See Also</span></span>

- <span data-ttu-id="ac9b0-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1453">tx_queue_create</span></span>
- <span data-ttu-id="ac9b0-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1454">tx_queue_delete</span></span>
- <span data-ttu-id="ac9b0-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1455">tx_queue_flush</span></span>
- <span data-ttu-id="ac9b0-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="ac9b0-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="ac9b0-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="ac9b0-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1461">tx_queue_receive</span></span>
- <span data-ttu-id="ac9b0-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="ac9b0-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="ac9b0-1464">シーリングがあるカウント セマフォにインスタンスを配置する</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1465">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1466">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1466">Description</span></span>

<span data-ttu-id="ac9b0-1467">このサービスは、指定されたカウント セマフォにインスタンスを 1 つ入れます。これにより、実際にカウント セマフォが 1 つインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="ac9b0-1468">カウント セマフォの現在の値が指定されたシーリング以上の場合、インスタンスは配置されず、TX_CEILING_EXCEEDED エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1469">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1469">Parameters</span></span>

- <span data-ttu-id="ac9b0-1470">**semaphore_ptr** 以前に作成されたセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="ac9b0-1471">**ceiling** セマフォに許可されている最大限度 (有効な値の範囲は 1 から 0xFFFFFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1472">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1472">Return Values</span></span>

- <span data-ttu-id="ac9b0-1473">**TX_SUCCESS (0x00)** セマフォ シーリング配置に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="ac9b0-1474">**TX_CEILING_EXCEEDED** (0x21) 配置要求がシーリングを超えています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="ac9b0-1475">**TX_INVALID_CEILING** (0x22) 無効な値 0 がシーリングに指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="ac9b0-1476">**TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1477">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1477">Allowed From</span></span>

<span data-ttu-id="ac9b0-1478">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1479">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1480">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1480">See Also</span></span>

- <span data-ttu-id="ac9b0-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="ac9b0-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1490">tx_semaphore_create</span></span>

<span data-ttu-id="ac9b0-1491">カウント セマフォの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1492">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1493">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1493">Description</span></span>

<span data-ttu-id="ac9b0-1494">このサービスを使用すると、スレッド間同期のためのカウント セマフォが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="ac9b0-1495">初期セマフォ数は、入力パラメーターとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1496">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1496">Parameters</span></span>

- <span data-ttu-id="ac9b0-1497">**semaphore_ptr** セマフォ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="ac9b0-1498">**name_ptr** セマフォの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="ac9b0-1499">**initial_count** このセマフォの最初の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="ac9b0-1500">有効な値の範囲は 0x00000000 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1501">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1501">Return Values</span></span>

- <span data-ttu-id="ac9b0-1502">**TX_SUCCESS** (0x00) セマフォの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="ac9b0-1503">**TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="ac9b0-1504">ポインターが NULL であるか、セマフォが既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="ac9b0-1505">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1506">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1506">Allowed From</span></span>

<span data-ttu-id="ac9b0-1507">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1508">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1508">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1509">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1510">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1510">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1511">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1511">See Also</span></span>

- <span data-ttu-id="ac9b0-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="ac9b0-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="ac9b0-1522">カウント セマフォの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1523">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1524">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1524">Description</span></span>

<span data-ttu-id="ac9b0-1525">このサービスを使用すると、指定されたカウント セマフォが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="ac9b0-1526">セマフォ インスタンスを待機しているすべてのスレッドが再開され、TX_DELETED 戻りステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1527">*アプリケーションは、このセマフォの put 通知コールバックが、セマフォを削除する前に完了する (または無効になる) ようにしなければなりません。さらに、アプリケーションは、削除されたセマフォが今後使用されないようにしなければなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1528">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1528">Parameters</span></span>

- <span data-ttu-id="ac9b0-1529">**semaphore_ptr** 以前に作成されたセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1530">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1530">Return Values</span></span>

- <span data-ttu-id="ac9b0-1531">**TX_SUCCESS** (0x00) カウント セマフォの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="ac9b0-1532">**TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="ac9b0-1533">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1534">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1534">Allowed From</span></span>

<span data-ttu-id="ac9b0-1535">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1536">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1536">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1537">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1538">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="ac9b0-1539">**参照**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1539">**See Also**</span></span>

- <span data-ttu-id="ac9b0-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="ac9b0-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1549">tx_semaphore_get</span></span>

<span data-ttu-id="ac9b0-1550">カウント セマフォからのインスタンスの取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1551">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1552">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1552">Description</span></span>

<span data-ttu-id="ac9b0-1553">このサービスを使用すると、指定されたカウント セマフォからインスタンスが (ひとつだけ) 取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="ac9b0-1554">その結果、指定されたセマフォのカウントが 1 つ減少します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1555">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1555">Parameters</span></span>

- <span data-ttu-id="ac9b0-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="ac9b0-1557">以前に作成されたカウント セマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="ac9b0-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1558">**wait_option**</span></span> <br><span data-ttu-id="ac9b0-1559">使用可能なセマフォのインスタンスがない場合、つまり、セマフォのカウントが 0 の場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="ac9b0-1560">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ac9b0-1561">**TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="ac9b0-1562">*これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="ac9b0-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、セマフォ インスタンスが使用可能になるまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="ac9b0-1564">タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、セマフォ インスタンスを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1565">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1565">Return Values</span></span>

- <span data-ttu-id="ac9b0-1566">**TX_SUCCESS** (0x00) セマフォ インスタンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="ac9b0-1567">**TX_DELETED** (0x01) スレッドが中断されている間にカウント セマフォが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="ac9b0-1568">**TX_NO_INSTANCE** (0x0D) サービスがカウント セマフォのインスタンスを取得できませんでした (指定された待機時間内のセマフォ数は0です)。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="ac9b0-1569">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-1570">**TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="ac9b0-1571">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1572">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1572">Allowed From</span></span>

<span data-ttu-id="ac9b0-1573">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1574">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1574">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1575">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1576">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1576">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1577">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1577">See Also</span></span>

- <span data-ttu-id="ac9b0-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="ac9b0-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="ac9b0-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="ac9b0-1587">セマフォに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1588">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1589">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1589">Description</span></span>

<span data-ttu-id="ac9b0-1590">このサービスを使用すると、指定したセマフォに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1591">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1591">Parameters</span></span>

- <span data-ttu-id="ac9b0-1592">**semaphore_ptr** セマフォ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="ac9b0-1593">**name** セマフォの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="ac9b0-1594">**current_value** 現在のセマフォのカウントの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="ac9b0-1595">**first_suspended** このセマフォの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="ac9b0-1596">**suspended_count** このセマフォで現在中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="ac9b0-1597">**next_semaphore** 次に作成されるセマフォのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1598">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1599">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1599">Return Values</span></span>

- <span data-ttu-id="ac9b0-1600">**TX_SUCCESS** (0x00) 情報が取得されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="ac9b0-1601">**TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1602">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1602">Allowed From</span></span>

<span data-ttu-id="ac9b0-1603">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1604">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1604">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1605">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1606">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1606">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1607">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1607">See Also</span></span>

- <span data-ttu-id="ac9b0-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="ac9b0-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="ac9b0-1618">セマフォ パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1619">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1620">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1620">Description</span></span>

<span data-ttu-id="ac9b0-1621">このサービスを使用すると、指定したセマフォに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1622">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="ac9b0-1623">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1623">**Parameters**</span></span>

-  <span data-ttu-id="ac9b0-1624">**semaphore_ptr** 以前に作成されたセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="ac9b0-1625">**puts** このセマフォで実行される配置要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="ac9b0-1626">**gets**  このセマフォで実行される取得要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="ac9b0-1627">**suspensions** このセマフォで中断されているスレッド数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="ac9b0-1628">**timeouts** このセマフォのスレッド中断タイムアウトの数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1629">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1630">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1630">Return Values</span></span>

- <span data-ttu-id="ac9b0-1631">**TX_SUCCESS** (0x00) セマフォのパフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="ac9b0-1632">**TX_PTR_ERROR** (0x03) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="ac9b0-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1634">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1634">Allowed From</span></span>

<span data-ttu-id="ac9b0-1635">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1636">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1636">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1637">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1637">See Also</span></span>

- <span data-ttu-id="ac9b0-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="ac9b0-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-1648">セマフォ システム パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1649">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1650">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1650">Description</span></span>

<span data-ttu-id="ac9b0-1651">このサービスを使用すると、システム内のすべてのセマフォに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1652">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1653">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1653">Parameters</span></span>

- <span data-ttu-id="ac9b0-1654">**puts** すべてのセマフォで実行される put 要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="ac9b0-1655">**gets** すべてのセマフォで実行される取得要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="ac9b0-1656">**suspensions** すべてのセマフォのスレッド保留の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="ac9b0-1657">**suspensions** すべてのセマフォのスレッド保留タイムアウトの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1658">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1659">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1659">Return Values</span></span>

- <span data-ttu-id="ac9b0-1660">**TX_SUCCESS** (0x00) システム パフォーマンス取得。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="ac9b0-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1662">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1662">Allowed From</span></span>

<span data-ttu-id="ac9b0-1663">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1664">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1664">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1665">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1665">See Also</span></span>

- <span data-ttu-id="ac9b0-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="ac9b0-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="ac9b0-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="ac9b0-1676">セマフォの中断リストの優先順位の設定</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1677">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1678">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1678">Description</span></span>

<span data-ttu-id="ac9b0-1679">このサービスを使用すると、セマフォのインスタンスに対して中断されている最も優先度の高いスレッドが、中断リストの先頭に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="ac9b0-1680">他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1681">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1681">Parameters</span></span>

- <span data-ttu-id="ac9b0-1682">**semaphore_ptr** 以前に作成されたセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1683">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1683">Return Values</span></span>

- <span data-ttu-id="ac9b0-1684">**TX_SUCCESS** (0x00) セマフォの優先度付けに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="ac9b0-1685">**TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1686">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1686">Allowed From</span></span>

<span data-ttu-id="ac9b0-1687">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1688">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1688">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1689">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1690">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1690">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1691">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1691">See Also</span></span>

- <span data-ttu-id="ac9b0-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="ac9b0-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1697">tx_semaphore_put</span></span>

<span data-ttu-id="ac9b0-1698">カウント セマフォへのインスタンスの配置</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1699">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1700">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1700">Description</span></span>

<span data-ttu-id="ac9b0-1701">このサービスは、指定されたカウント セマフォにインスタンスを 1 つ入れます。これにより、実際にカウント セマフォが 1 つインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1702">*セマフォがオールワン (OxFFFFFFFF) のときにこのサービスが呼び出されると、新しい配置操作によってセマフォはゼロにリセットされます。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1703">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1703">Parameters</span></span>

- <span data-ttu-id="ac9b0-1704">**semaphore_ptr** 以前に作成されたカウント セマフォ制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1705">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1705">Return Values</span></span>

- <span data-ttu-id="ac9b0-1706">**TX_SUCCESS** (0x00) セマフォへの配置に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="ac9b0-1707">**TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1708">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1708">Allowed From</span></span>

<span data-ttu-id="ac9b0-1709">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1710">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1710">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1711">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1712">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1713">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1713">See Also</span></span>

- <span data-ttu-id="ac9b0-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="ac9b0-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="ac9b0-1724">セマフォの配置時にアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1725">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="ac9b0-1726">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1726">Description</span></span>

<span data-ttu-id="ac9b0-1727">このサービスを使用すると、指定されたセマフォが配置されるたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="ac9b0-1728">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1729">*アプリケーションのセマフォ通知コールバックで、中断オプションを指定した ThreadX API を呼び出してはなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1730">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1730">Parameters</span></span>

- <span data-ttu-id="ac9b0-1731">**semaphore_ptr** 以前に作成されたセマフォへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="ac9b0-1732">**semaphore_put_notify** アプリケーションのセマフォ配置通知関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="ac9b0-1733">この値が TX_NULL の場合は、通知が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1734">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1734">Return Values</span></span>

- <span data-ttu-id="ac9b0-1735">**TX_SUCCESS** (0x00) セマフォ配置通知の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="ac9b0-1736">**TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="ac9b0-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1738">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1738">Allowed From</span></span>

<span data-ttu-id="ac9b0-1739">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1740">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1740">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1741">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1741">See Also</span></span>

- <span data-ttu-id="ac9b0-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="ac9b0-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="ac9b0-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="ac9b0-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="ac9b0-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="ac9b0-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="ac9b0-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="ac9b0-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1751">tx_thread_create</span></span>

<span data-ttu-id="ac9b0-1752">アプリケーション スレッドの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1753">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1753">Prototype</span></span>

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1754">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1754">Description</span></span>

<span data-ttu-id="ac9b0-1755">このサービスを使用すると、指定されたタスク エントリ関数で実行を開始するアプリケーション スレッドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="ac9b0-1756">入力パラメーターによって指定される属性の中には、スタック、優先度、プリエンプションしきい値、およびタイムスライスがあります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="ac9b0-1757">さらに、スレッドの初期実行状態も指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="ac9b0-1758">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1758">**Parameters**</span></span>

- <span data-ttu-id="ac9b0-1759">**thread_ptr** スレッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="ac9b0-1760">**name_ptr** スレッドの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="ac9b0-1761">**entry_function** スレッド実行の初期 C 関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="ac9b0-1762">スレッドはこのエントリ関数から戻ると、"*完了*" 状態になり、無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="ac9b0-1763">**entry_input** 最初の実行時にスレッドのエントリ関数に渡される 32 ビット値。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="ac9b0-1764">この入力の使用は、アプリケーションによってのみ決定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="ac9b0-1765">**stack_start** スタックのメモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="ac9b0-1766">**stack_size** スタック メモリ領域内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="ac9b0-1767">スレッドのスタック領域は、最悪の場合の関数呼び出し入れ子とローカル変数の使用に対処できるだけの大きさでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="ac9b0-1768">**priority** スレッドの数値優先度。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="ac9b0-1769">有効な値の範囲は 0 から (TX_MAX_PRIORITES-1) です。0 の値は最高の優先度を表します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="ac9b0-1770">**preempt_threshold** 無効なプリエンプションの最高優先度レベル (0 から (TX_MAX_PRIORITIES-1))。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="ac9b0-1771">このレベルより高い優先度のみが、このスレッドをプリエンプションできます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="ac9b0-1772">この値は、指定された優先度以下でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="ac9b0-1773">値がスレッド優先度と等しいと、プリエンプションしきい値が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="ac9b0-1774">**time_slice** このスレッドの実行が、同じ優先度の他の準備完了スレッドが実行されるより前に許可されるタイマー刻みの数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="ac9b0-1775">プリエンプションしきい値を使用すると、タイムスライスが無効になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="ac9b0-1776">有効なタイムスライス値の範囲は、1 から 0xFFFFFFFF までです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="ac9b0-1777">値が **TX_NO_TIME_SLICE** (0 の値) の場合、このスレッドのタイムスライスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ac9b0-1778">*タイム スライシングを使用すると、わずかなシステム オーバーヘッドが発生します。タイム スライシングは、複数のスレッドが同じ優先度を共有している場合にのみ役立ちます。一意の優先度を持つスレッドにはタイム スライスを割り当てないようにしてください。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="ac9b0-1779">**auto_start** スレッドをすぐに開始するか、保留状態にするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="ac9b0-1780">有効なオプションは **TX_AUTO_START** (0x01) と **TX_DONT_START** (0x00) です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="ac9b0-1781">TX_DONT_START が指定されている場合、スレッドを実行するためにアプリケーションは後で tx_thread_resume を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1782">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1782">Return Values</span></span>

- <span data-ttu-id="ac9b0-1783">**TX_SUCCESS** (0x00) スレッドの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="ac9b0-1784">**TX_THREAD_ERROR** (0x0E) スレッド制御ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="ac9b0-1785">ポインターが NULL であるか、スレッドは既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="ac9b0-1786">**TX_PTR_ERROR** (0x03) エントリ ポイントの開始アドレスが無効であるか、スタック領域は無効 (通常は NULL) です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="ac9b0-1787">**TX_SIZE_ERROR** (0x05) スタック領域のサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="ac9b0-1788">スレッドは **TX_MINIMUM_STACK** バイト以上でないと実行できません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="ac9b0-1789">**TX_PRIORITY_ERROR** (0x0F) スレッド優先度の値が (0 から (TX_MAX_PRIORITIES-1)) の範囲外であるため、無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="ac9b0-1790">**TX_THRESH_ERROR** (0X18) 無効なプリエンプションしきい値が指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="ac9b0-1791">この値は、スレッドの初期優先度以下の有効な優先度でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="ac9b0-1792">**TX_START_ERROR** (0x10) 自動開始の選択が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="ac9b0-1793">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1794">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1794">Allowed From</span></span>

<span data-ttu-id="ac9b0-1795">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1796">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1796">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1797">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1798">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1798">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
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

### <a name="see-also"></a><span data-ttu-id="ac9b0-1799">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1799">See Also</span></span>

- <span data-ttu-id="ac9b0-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1800">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1802">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1809">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1810">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="ac9b0-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1817">tx_thread_delete</span></span>

<span data-ttu-id="ac9b0-1818">アプリケーション スレッドの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1819">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1820">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1820">Description</span></span>

<span data-ttu-id="ac9b0-1821">このサービスを使用すると、指定されたアプリケーション スレッドが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="ac9b0-1822">指定されたスレッドは終了または完了した状態でなければならないため、このサービスは、自身を削除しようとしているスレッドから呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1823">*スレッドのスタックに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、このサービスの完了後に利用できます。また、このアプリケーションでは削除されたスレッドの使用を防ぐ必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1824">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1824">Parameters</span></span>

- <span data-ttu-id="ac9b0-1825">**thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1826">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1826">Return Values</span></span>

- <span data-ttu-id="ac9b0-1827">**TX_SUCCESS** (0x00) スレッドの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="ac9b0-1828">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-1829">**TX_DELETE_ERROR** (0X11) 指定されたスレッドが終了または完了した状態でありません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="ac9b0-1830">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1831">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1831">Allowed From</span></span>

<span data-ttu-id="ac9b0-1832">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1833">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1833">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1834">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1835">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1835">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1836">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1836">See Also</span></span>

- <span data-ttu-id="ac9b0-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1837">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1839">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1846">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1847">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="ac9b0-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="ac9b0-1855">スレッドの開始または終了時にアプリケーションに通知</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1856">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="ac9b0-1857">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1857">Description</span></span>

<span data-ttu-id="ac9b0-1858">このサービスを使用すると、指定されたスレッドが開始または終了するたびに呼び出される通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="ac9b0-1859">通知コールバックの処理は、アプリケーションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1860">アプリケーションのスレッド開始/終了通知コールバックでは、中断オプションを指定した ThreadX API を呼び出してはなりません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1861">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1861">Parameters</span></span>

- <span data-ttu-id="ac9b0-1862">**thread_ptr** 以前作成されたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="ac9b0-1863">**entry_exit_notify** アプリケーションのスレッド開始/終了通知関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="ac9b0-1864">開始/終了通知関数の 2 番目のパラメーターは、開始または終了が存在するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="ac9b0-1865">値 **TX_THREAD_ENTRY** (0x00) は、スレッドが開始されたことを示します。値 **TX_THREAD_EXIT** (0x01) は、スレッドが終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="ac9b0-1866">この値が **TX_NULL** の場合は、通知が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1867">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1867">Return Values</span></span>

- <span data-ttu-id="ac9b0-1868">**TX_SUCCESS** (0x00) スレッド開始/終了通知関数の登録に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="ac9b0-1869">**TX_THREAD_ERROR** (0x0E) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="ac9b0-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1871">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1871">Allowed From</span></span>

<span data-ttu-id="ac9b0-1872">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1873">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1873">Example</span></span>

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
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

### <a name="see-also"></a><span data-ttu-id="ac9b0-1874">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1874">See Also</span></span>

- <span data-ttu-id="ac9b0-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1875">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1876">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1878">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1885">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1886">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="ac9b0-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1893">tx_thread_identify</span></span>

<span data-ttu-id="ac9b0-1894">現在実行中のスレッドへのポインターを取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1895">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="ac9b0-1896">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1896">Description</span></span>

<span data-ttu-id="ac9b0-1897">このサービスを使用すると、現在実行中のスレッドへのポインターが返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="ac9b0-1898">実行中のスレッドがない場合、このサービスは null ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1899">*このサービスが ISR から呼び出された場合、戻り値は、実行中の割り込みハンドラーの前に実行されているスレッドを表します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1900">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1900">Parameters</span></span>

<span data-ttu-id="ac9b0-1901">None</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="ac9b0-1902">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1902">Retuen Values</span></span>

- <span data-ttu-id="ac9b0-1903">**thread pointer** 現在実行中のスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="ac9b0-1904">実行しているスレッドがない場合、戻り値は **TX_NULL** です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1905">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1905">Allowed From</span></span>

<span data-ttu-id="ac9b0-1906">スレッドと ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1907">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1907">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1908">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1909">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1909">Example</span></span>

<span data-ttu-id="ac9b0-1910">TX_THREAD \*my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1910">TX_THREAD \*my_thread_ptr;</span></span>

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1911">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1911">See Also</span></span>

- <span data-ttu-id="ac9b0-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1912">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1913">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1921">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1922">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="ac9b0-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1929">tx_thread_info_get</span></span>

<span data-ttu-id="ac9b0-1930">スレッドに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1931">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1931">Prototype</span></span>

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1932">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1932">Description</span></span>

<span data-ttu-id="ac9b0-1933">このサービスを使用すると、指定したスレッドに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1934">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1934">Parameters</span></span>
- <span data-ttu-id="ac9b0-1935">**thread_ptr** スレッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="ac9b0-1936">**name** スレッドの名前を指すポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="ac9b0-1937">**state** スレッドの現在の実行状態の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="ac9b0-1938">有効値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="ac9b0-1939">**TX_READY** (0x00)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="ac9b0-1940">**TX_COMPLETED** (0x01)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="ac9b0-1941">**TX_TERMINATED** (0x02)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="ac9b0-1942">**TX_SUSPENDED** (0x03)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="ac9b0-1943">**TX_SLEEP** (0x04)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="ac9b0-1944">**TX_QUEUE_SUSP** (0x05)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="ac9b0-1945">**TX_SEMAPHORE_SUSP** (0x06)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="ac9b0-1946">**TX_EVENT_FLAG** (0x07)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="ac9b0-1947">**TX_BLOCK_MEMORY** (0x08)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="ac9b0-1948">**TX_BYTE_MEMORY** (0x09)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="ac9b0-1949">**TX_MUTEX_SUSP** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="ac9b0-1950">**run_count** スレッドの実行カウントの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="ac9b0-1951">**priority** スレッドの優先度の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="ac9b0-1952">**preemption_threshold** スレッドのプリエンプションしきい値の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="ac9b0-1953">**time_slice** スレッドのタイムスライスの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="ac9b0-1954">**next_thread** 次に作成されるスレッド ポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="ac9b0-1955">**suspended_thread** 中断リスト内の次のスレッドへのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-1956">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-1957">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1957">Return Values</span></span>

- <span data-ttu-id="ac9b0-1958">**TX_SUCCESS** (0x00) スレッド情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="ac9b0-1959">**TX_THREAD_ERROR** (0x0E) スレッド制御ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-1960">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1960">Allowed From</span></span>

<span data-ttu-id="ac9b0-1961">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-1962">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1962">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-1963">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-1964">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1964">Example</span></span>

```c
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

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-1965">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1965">See Also</span></span>

- <span data-ttu-id="ac9b0-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1966">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1967">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1969">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1975">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1976">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="ac9b0-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="ac9b0-1984">スレッド パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-1985">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1985">Prototype</span></span>

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a><span data-ttu-id="ac9b0-1986">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1986">Description</span></span>

<span data-ttu-id="ac9b0-1987">このサービスを使用すると、指定したスレッドに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-1988">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-1989">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1989">Parameters</span></span>
- <span data-ttu-id="ac9b0-1990">**thread_ptr** 以前作成されたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="ac9b0-1991">**resumptions** このスレッドの再開数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="ac9b0-1992">**resumptions** このスレッドの中断数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="ac9b0-1993">**solicited_preemptions** ThreadX API サービス呼び出しがこのスレッドにより行われた結果としてのプリエンプション数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="ac9b0-1994">**interrupt_preemptions** 割り込み処理の結果であるこのスレッドのプリエンプション数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="ac9b0-1995">**priority_inversions** このスレッドの優先度逆転数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="ac9b0-1996">**time_slices** このスレッドのタイムスライス数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="ac9b0-1997">**relinquishes** このスレッドにより実行されたスレッド放棄の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="ac9b0-1998">**timeouts** このスレッドでの保留タイムアウトの数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="ac9b0-1999">**wait_aborts** このスレッドで実行された待機中止の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="ac9b0-2000">**last_preempted_by** このスレッドを最後にプリエンプションしたスレッド ポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2001">*パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2002">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2002">Return Values</span></span>

- <span data-ttu-id="ac9b0-2003">**TX_SUCCESS** (0x00) スレッド パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="ac9b0-2004">**TX_PTR_ERROR** (0x03) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2006">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2006">Allowed From</span></span>

<span data-ttu-id="ac9b0-2007">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2008">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2008">Example</span></span>

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

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

### <a name="see-also"></a><span data-ttu-id="ac9b0-2009">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2009">See Also</span></span>

- <span data-ttu-id="ac9b0-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2010">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2011">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2013">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2019">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2020">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="ac9b0-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-2028">スレッド システムのパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2029">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2029">Prototype</span></span>

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2030">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2030">Description</span></span>

<span data-ttu-id="ac9b0-2031">このサービスを使用すると、システム内のすべてのスレッドに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="ac9b0-2032">*このサービスがパフォーマンス情報を返すためには、ThreadX ライブラリとアプリケーションが*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="ac9b0-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _が定義された状態でビルドされる必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2034">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2034">Parameters</span></span>

- <span data-ttu-id="ac9b0-2035">**resumptions** スレッド再開の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="ac9b0-2036">**suspensions** スレッド保留の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="ac9b0-2037">**solicited_preemptions** スレッドが ThreadX API サービスを呼び出した結果としてのスレッド プリエンプションの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="ac9b0-2038">**interrupt_preemptions** 割り込み処理の結果としてのスレッド プリエンプションの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="ac9b0-2039">**priority_inversions** スレッド優先度逆転の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="ac9b0-2040">**time_slices** スレッド タイムスライスの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="ac9b0-2041">**resumptions** スレッド放棄の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="ac9b0-2042">**timeouts** スレッド保留タイムアウトの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="ac9b0-2043">**wait_aborts** スレッド待機中止の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="ac9b0-2044">**non_idle_returns** 別のスレッドの実行準備が整ったときにスレッドがシステムに戻る回数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="ac9b0-2045">**idle_returns** 実行する準備ができているスレッドが他にない場合 (アイドル状態のシステム) にスレッドがシステムに戻る回数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2046">*パラメーターに **TX_NULL** を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2047">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2047">Return Values</span></span>

- <span data-ttu-id="ac9b0-2048">**TX_SUCCESS** (0x00) スレッド システム パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="ac9b0-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2050">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2050">Allowed From</span></span>

<span data-ttu-id="ac9b0-2051">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2052">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2052">Example</span></span>

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

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

### <a name="see-also"></a><span data-ttu-id="ac9b0-2053">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2053">See Also</span></span>

- <span data-ttu-id="ac9b0-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2054">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2055">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2057">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2063">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2064">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="ac9b0-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="ac9b0-2072">アプリケーション スレッドのプリエンプションしきい値の変更</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2073">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2074">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2074">Description</span></span>

<span data-ttu-id="ac9b0-2075">このサービスを使用すると、指定されたスレッドのプリエンプションしきい値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="ac9b0-2076">プリエンプションしきい値により、そのプリエンプションしきい値以下のスレッドにより、指定されたスレッドがプリエンプションされることがなくなります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="ac9b0-2077">*プリエンプションしきい値を使用すると、指定されたスレッドのタイム スライシングが無効になります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2078">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2078">Parameters</span></span>
- <span data-ttu-id="ac9b0-2079">**thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="ac9b0-2080">**new_threshold** 新しいプリエンプションしきい値の優先度レベルl (0 から (TX_MAX_PRIORITIES-1))。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="ac9b0-2081">**old_threshold** 前のプリエンプションしきい値を返す場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2082">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2082">Return Values</span></span>

- <span data-ttu-id="ac9b0-2083">**TX_SUCCESS** (0x00) プリエンプションしきい値の変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="ac9b0-2084">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2085">**TX_THRESH_ERROR** (0x18) 指定された新しいプリエンプションしきい値が、有効なスレッド優先度でない ((0 から (**TX_MAX_PRIORITIES**-1) 以外の値) か、現在のスレッド優先度より大きい (優先度が低い) です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="ac9b0-2086">**TX_PTR_ERROR** (0x03) 前のプリエンプションしきい値保存場所へのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="ac9b0-2087">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2088">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2088">Allowed From</span></span>

<span data-ttu-id="ac9b0-2089">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2090">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2090">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2091">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2092">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2092">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

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

### <a name="see-also"></a><span data-ttu-id="ac9b0-2093">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2093">See Also</span></span>

- <span data-ttu-id="ac9b0-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2094">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2095">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2097">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2103">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2104">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="ac9b0-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="ac9b0-2112">アプリケーション スレッドの優先度の変更</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2113">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2114">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2114">Description</span></span>

<span data-ttu-id="ac9b0-2115">このサービスを使用すると、指定されたスレッドの優先度が変更されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="ac9b0-2116">有効な優先順位の範囲は 0 から (TX_MAX_PRIORITES-1) です。0 は最高の優先度レベルを表します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-2117">\*指定されたスレッドのプリエンプションしきい値は、自動的に新しい優先度に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="ac9b0-2118">新しいしきい値が必要な場合は、\***tx_thread_preemption_change** _ サービスをこの呼び出しの後に使用する必要があります。_</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2119">Parameters</span></span>

- <span data-ttu-id="ac9b0-2120">**thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="ac9b0-2121">**new_priority** 新しいスレッド優先度レベル (0 から (TX_MAX_PRIORITIES-1))。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="ac9b0-2122">**old_priority** スレッドの前の優先度を返す場所を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2123">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2123">Return Values</span></span>

- <span data-ttu-id="ac9b0-2124">**TX_SUCCESS** (0x00) 優先度の変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="ac9b0-2125">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2126">**TX_PRIORITY_ERROR** (0x0F) 定された新しい優先度が無効 ((0 から (TX_MAX_PRIORITIES-1) 以外の値) です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="ac9b0-2127">**TX_PTR_ERROR** (0x03) 前の優先度保存場所へのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="ac9b0-2128">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2129">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2129">Allowed From</span></span>

<span data-ttu-id="ac9b0-2130">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2131">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2131">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2132">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2133">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2133">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="ac9b0-2134">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2134">See Also</span></span>

- <span data-ttu-id="ac9b0-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2135">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2136">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2138">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2144">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2145">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="ac9b0-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="ac9b0-2153">制御を他のアプリケーション スレッドに放棄</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2155">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2155">Description</span></span>

<span data-ttu-id="ac9b0-2156">このサービスは、同等以上の優先順位で実行可能な他のスレッドに対してプロセッサ制御を放棄します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2157">*このサービスは、同じ優先順位のスレッドに対して制御を放棄するだけでなく、現在のスレッドのプリエンプションしきい値の設定によって実行できない最高優先順位のスレッドに対しても制御を放棄します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2158">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2158">Parameters</span></span>

<span data-ttu-id="ac9b0-2159">None</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2160">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2160">Return Values</span></span>

<span data-ttu-id="ac9b0-2161">None</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2162">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2162">Allowed From</span></span>

<span data-ttu-id="ac9b0-2163">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2164">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2164">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2165">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="ac9b0-2166">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2166">Examples</span></span>

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
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

### <a name="see-also"></a><span data-ttu-id="ac9b0-2167">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2167">See Also</span></span>

- <span data-ttu-id="ac9b0-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2168">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2169">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2171">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2177">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2178">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="ac9b0-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2185">tx_thread_reset</span></span>

<span data-ttu-id="ac9b0-2186">スレッドのリセット</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2187">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2188">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2188">Description</span></span>

<span data-ttu-id="ac9b0-2189">このサービスを使用すると、スレッドの作成時に定義されたエントリ ポイントで実行するように、指定されたスレッドをリセットします。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="ac9b0-2190">スレッドは、リセットするためには **TX_COMPLETED** または **TX_TERMINATED** の状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-2191">*スレッドは、再実行するためには再開する必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2192">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2192">Parameters</span></span>

- <span data-ttu-id="ac9b0-2193">**thread_ptr** 以前作成されたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2194">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2194">Return Values</span></span>

- <span data-ttu-id="ac9b0-2195">**TX_SUCCESS** (0x00) スレッドのリセットに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="ac9b0-2196">**TX_NOT_DONE** (0X20) 指定されたスレッドが **TX_COMPLETED** または **TX_TERMINATED** の状態でありません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="ac9b0-2197">**TX_THREAD_ERROR** (0x0E) スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2198">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2199">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2199">Allowed From</span></span>

<span data-ttu-id="ac9b0-2200">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2201">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2201">Example</span></span>

<span data-ttu-id="ac9b0-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2203">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2203">See Also</span></span>

- <span data-ttu-id="ac9b0-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2204">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2205">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2207">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2214">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="ac9b0-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2221">tx_thread_resume</span></span>

<span data-ttu-id="ac9b0-2222">中断されたアプリケーション スレッドの再開</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2223">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2224">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2224">Description</span></span>

<span data-ttu-id="ac9b0-2225">このサービスを使用すると、***tx_thread_suspend*** 呼び出しによって以前に中断されたスレッドの実行が再開または準備されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="ac9b0-2226">さらに、このサービスは、自動開始なしで作成されたスレッドを再開します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2227">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2227">Parameters</span></span>

- <span data-ttu-id="ac9b0-2228">**thread_ptr** 中断されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2229">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2229">Return Values</span></span>

- <span data-ttu-id="ac9b0-2230">**TX_SUCCESS** (0x00) スレッドの再開に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="ac9b0-2231">**TX_SUSPEND_LIFTED** (0x19) 以前に設定された遅延中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="ac9b0-2232">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2233">**TX_RESUME_ERROR** (0X12) 指定されたスレッドは中断されていないか、以前に **_tx_thread_suspend_** 以外のサービスによって中断されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2234">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2234">Allowed From</span></span>

<span data-ttu-id="ac9b0-2235">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2236">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2236">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2237">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2237">Yes</span></span>

<span data-ttu-id="ac9b0-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2239">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2240">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2240">See Also</span></span>

- <span data-ttu-id="ac9b0-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2241">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2242">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2244">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2251">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="ac9b0-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2258">tx_thread_sleep</span></span>

<span data-ttu-id="ac9b0-2259">現在のスレッドを指定された時間だけ中断</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2260">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2261">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2261">Description</span></span>

<span data-ttu-id="ac9b0-2262">このサービスによって、呼び出し元のスレッドは、指定したタイマー刻み数だけ中断されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="ac9b0-2263">タイマー刻みに関連付けられている物理時間の量は、アプリケーション固有です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="ac9b0-2264">このサービスを呼び出せるのはアプリケーション スレッドからだけです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2265">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2265">Parameters</span></span>

- <span data-ttu-id="ac9b0-2266">**timer_ticks** 呼び出し元のアプリケーション スレッドを中断するタイマー刻み数 (0 から 0xFFFFFFFF まで)。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="ac9b0-2267">0 を指定した場合、サービスはすぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2268">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2268">Return Values</span></span>

- <span data-ttu-id="ac9b0-2269">**TX_SUCCESS** (0x00) スレッドのスリープに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="ac9b0-2270">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ac9b0-2271">**TX_CALLER_ERROR** (0X13) サービスが非スレッドから呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2272">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2272">Allowed From</span></span>

<span data-ttu-id="ac9b0-2273">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2274">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2274">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2275">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2276">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2277">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2277">See Also</span></span>

- <span data-ttu-id="ac9b0-2278">tx_thread_create, tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2280">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2287">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2288">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="ac9b0-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="ac9b0-2295">スレッド スタック エラー通知コールバックの登録</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2296">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="ac9b0-2297">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2297">Description</span></span>

<span data-ttu-id="ac9b0-2298">このサービスを使用すると、スレッド スタック エラーを処理するための通知コールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="ac9b0-2299">ThreadX は実行中にスレッド スタック エラーを検出すると、この通知関数を呼び出してエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="ac9b0-2300">エラーの処理は、アプリケーションによって完全に定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="ac9b0-2301">違反しているスレッドの中断からシステム全体のリセットまであらゆることが行なわれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-2302">*ThreadX ライブラリは、このサービスがパフォーマンス情報を返すために定義された* **TX_ENABLE_STACK_CHECKING** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2303">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2303">Parameters</span></span>
- <span data-ttu-id="ac9b0-2304">**error_handler** アプリケーションのスタック エラー処理関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="ac9b0-2305">この値が TX_NULL の場合、通知は無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2306">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2306">Return Values</span></span>

- <span data-ttu-id="ac9b0-2307">**TX_SUCCESS** (0x00) スレッドのリセットに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="ac9b0-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2309">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2309">Allowed From</span></span>

<span data-ttu-id="ac9b0-2310">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2311">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2312">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2312">See Also</span></span>

- <span data-ttu-id="ac9b0-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2313">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2314">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2316">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2323">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2324">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="ac9b0-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2330">tx_thread_suspend</span></span>

<span data-ttu-id="ac9b0-2331">アプリケーション スレッドの中断</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2333">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2333">Description</span></span>

<span data-ttu-id="ac9b0-2334">このサービスを使用すると、指定されたアプリケーション スレッドが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="ac9b0-2335">スレッドがこのサービスを呼び出して自身を中断する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2336">*指定されたスレッドが既に別の理由で中断されている場合、この中断は、前の中断が解除されるまで内部的に保持されます。この場合、指定されたスレッドの無条件の中断が実行されます。後続の無条件中断要求は無効です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="ac9b0-2337">中断された後、スレッドを再実行するには ***tx_thread_resume*** によって再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2338">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2338">Parameters</span></span>

- <span data-ttu-id="ac9b0-2339">**thread_ptr** アプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2340">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2340">Return Values</span></span>

- <span data-ttu-id="ac9b0-2341">**TX_SUCCESS** (0x00) スレッドの中断に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="ac9b0-2342">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2343">**TX_SUSPEND_ERROR** (0X14) 指定されたスレッドは終了または完了の状態です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="ac9b0-2344">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2345">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2345">Allowed From</span></span>

<span data-ttu-id="ac9b0-2346">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2347">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2347">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2348">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2349">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2350">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2350">See Also</span></span>

- <span data-ttu-id="ac9b0-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2351">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2352">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2354">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2361">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2362">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="ac9b0-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2368">tx_thread_terminate</span></span>

<span data-ttu-id="ac9b0-2369">アプリケーション スレッドを終了</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2370">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="ac9b0-2371">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2371">Description</span></span>

<span data-ttu-id="ac9b0-2372">このサービスを使用すると、指定されたアプリケーションスレッドを、スレッドが中断されているかどうかに関係なく終了します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="ac9b0-2373">スレッドはこのサービスを呼び出して自身を終了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2374">*スレッドが終了に適した状態になるようにするのは、アプリケーションの責任です。たとえば、スレッドは、重要なアプリケーションの処理中、または他のミドルウェア コンポーネント内で終了して、その処理が不明な状態のままになるようにしてはなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-2375">*終了した後、スレッドは、再実行するためにはリセットする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2376">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2376">Parameters</span></span>

- <span data-ttu-id="ac9b0-2377">**thread_ptr** アプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2378">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2378">Return Values</span></span>
- <span data-ttu-id="ac9b0-2379">**TX_SUCCESS** (0x00) スレッドの終了に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="ac9b0-2380">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2381">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2382">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2382">Allowed From</span></span>

<span data-ttu-id="ac9b0-2383">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2384">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2384">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2385">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2386">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2387">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2387">See Also</span></span>

- <span data-ttu-id="ac9b0-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2390">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2397">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2398">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="ac9b0-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="ac9b0-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="ac9b0-2405">アプリケーション スレッドのタイムスライスを変更します</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2406">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2407">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2407">Description</span></span>

<span data-ttu-id="ac9b0-2408">このサービスを使用すると、指定されたアプリケーション スレッドのタイムスライスが変更されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="ac9b0-2409">スレッドのタイムスライスを選択すると、それが、優先度が同等以上の他のスレッドが実行可能になるまで、指定したタイマー刻み数を超えて実行されることがなくなります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2410">*プリエンプションしきい値を使用すると、指定されたスレッドのタイム スライシングが無効になります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2411">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2411">Parameters</span></span>

- <span data-ttu-id="ac9b0-2412">**thread_ptr** アプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="ac9b0-2413">**new_time_slice** 新しいタイム スライス値。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="ac9b0-2414">有効な値は TX_NO_TIME_SLICE と 1 から 0xFFFFFFFF の数値です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="ac9b0-2415">**old_time_slice** 指定したスレッドの前のタイムスライス値を格納する場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2416">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2416">Return Values</span></span>

- <span data-ttu-id="ac9b0-2417">**TX_SUCCESS** (0x00) タイムスライスの変更が成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="ac9b0-2418">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2419">**TX_PTR_ERROR** (0x03) 前のタイムスライス保存場所へのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="ac9b0-2420">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2421">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2421">Allowed From</span></span>

<span data-ttu-id="ac9b0-2422">スレッドとタイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2423">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2423">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2424">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2425">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2425">Example</span></span>

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

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

### <a name="see-also"></a><span data-ttu-id="ac9b0-2426">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2426">See Also</span></span>

- <span data-ttu-id="ac9b0-2427">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2427">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2428">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2430">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2437">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2438">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="ac9b0-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="ac9b0-2445">指定されたスレッドの中断を中止</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2446">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2447">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2447">Description</span></span>

<span data-ttu-id="ac9b0-2448">このサービスは、指定されたスレッドのスリープまたはその他のオブジェクトの中断を中止します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="ac9b0-2449">待機が中止されると、スレッドが待機していたサービスから **TX_WAIT_ABORTED** 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2450">*このサービスでは、tx_thread_suspend サービスによって行われた明示的な中断は解放されません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2451">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2451">Parameters</span></span>

- <span data-ttu-id="ac9b0-2452">**thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2453">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2453">Return Values</span></span>

- <span data-ttu-id="ac9b0-2454">**TX_SUCCESS** (0x00) スレッド待機中止に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="ac9b0-2455">**TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="ac9b0-2456">**TX_WAIT_ABORT_ERROR** (0x1B) 指定されたスレッドが待ち状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2457">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2457">Allowed From</span></span>

<span data-ttu-id="ac9b0-2458">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2459">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2459">Preemption Possible</span></span>
<span data-ttu-id="ac9b0-2460">はい</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2461">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2462">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2462">See Also</span></span>

- <span data-ttu-id="ac9b0-2463">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2463">tx_thread_create</span></span>
- <span data-ttu-id="ac9b0-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2464">tx_thread_delete</span></span>
- <span data-ttu-id="ac9b0-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="ac9b0-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2466">tx_thread_identify</span></span>
- <span data-ttu-id="ac9b0-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="ac9b0-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="ac9b0-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="ac9b0-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="ac9b0-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="ac9b0-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2473">tx_thread_reset</span></span>
- <span data-ttu-id="ac9b0-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2474">tx_thread_resume</span></span>
- <span data-ttu-id="ac9b0-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="ac9b0-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="ac9b0-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="ac9b0-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="ac9b0-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="ac9b0-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2480">tx_time_get</span></span>

<span data-ttu-id="ac9b0-2481">現在の時刻を取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2481">Retrieves the current time</span></span>

<span data-ttu-id="ac9b0-2482">アプリケーション タイマー</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2483">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2484">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2484">Description</span></span>

<span data-ttu-id="ac9b0-2485">このサービスを使用すると、内部システム クロックの内容が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="ac9b0-2486">タイマー刻みごとに内部システム クロックが 1 つ増えます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="ac9b0-2487">システム クロックは初期化中に 0 に設定されますが、サービス ***tx_time_set*** によって特定の値に変更できます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2488">*各タイマー刻みが表す実際の時間は、アプリケーションに固有です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="ac9b0-2489">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2489">**Parameters**</span></span>

<span data-ttu-id="ac9b0-2490">None</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2491">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2491">Return Values</span></span>

- <span data-ttu-id="ac9b0-2492">**system clock ticks** 自走の内部システム クロックの値。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2493">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2493">Allowed From</span></span>

<span data-ttu-id="ac9b0-2494">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2495">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2495">Preemption Possible</span></span>
<span data-ttu-id="ac9b0-2496">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2497">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2498">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2498">See Also</span></span>

- <span data-ttu-id="ac9b0-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="ac9b0-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2500">tx_time_set</span></span>

<span data-ttu-id="ac9b0-2501">現在の時刻を設定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2502">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2503">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2503">Description</span></span>

<span data-ttu-id="ac9b0-2504">このサービスは、内部システム クロックを指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="ac9b0-2505">タイマー刻みごとに内部システム クロックが 1 つ増えます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2506">*各タイマー刻みが表す実際の時間は、アプリケーションに固有です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2507">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2507">Parameters</span></span>

- <span data-ttu-id="ac9b0-2508">**new_time** システム クロックに設定する新しい時間。有効な値の範囲は 0 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2509">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2509">Return Values</span></span>

<span data-ttu-id="ac9b0-2510">None</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2511">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2511">Allowed From</span></span>

<span data-ttu-id="ac9b0-2512">スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2513">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2513">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2514">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2515">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2516">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2516">See Also</span></span>

- <span data-ttu-id="ac9b0-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="ac9b0-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2518">tx_timer_activate</span></span>

<span data-ttu-id="ac9b0-2519">アプリケーション タイマーのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2520">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2521">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2521">Description</span></span>

<span data-ttu-id="ac9b0-2522">このサービスを使用すると、指定されたアプリケーション タイマーがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="ac9b0-2523">同じ時刻に期限が切れるタイマーの期限切れルーチンは、アクティブになった順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2524">*期限切れになったワンショット タイマーは、再びアクティブにする前に*  ***tx_timer_change** _ _によってリセットしなければなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2525">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2525">Parameters</span></span>

- <span data-ttu-id="ac9b0-2526">**timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="ac9b0-2527">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2527">**Return Values**</span></span>

- <span data-ttu-id="ac9b0-2528">**TX_SUCCESS** (0x00) アプリケーション タイマーのアクティブ化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="ac9b0-2529">**TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="ac9b0-2530">**TX_ACTIVATE_ERROR** (0x17) タイマーは既にアクティブであるか、あるいは既に期限が切れているワンショット タイマーです。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2531">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2531">Allowed From</span></span>

<span data-ttu-id="ac9b0-2532">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2533">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2533">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2534">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2535">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2536">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2536">See Also</span></span>

- <span data-ttu-id="ac9b0-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2537">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2538">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2540">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="ac9b0-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2544">tx_timer_change</span></span>

<span data-ttu-id="ac9b0-2545">アプリケーション タイマーの変更</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2546">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2547">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2547">Description</span></span>

<span data-ttu-id="ac9b0-2548">このサービスを使用すると、指定されたアプリケーション タイマーの有効期限特性が変更されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="ac9b0-2549">このサービスを呼び出す前に、タイマーを非アクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2550">*このサービスの後に、タイマーを再び開始するために*  ***tx_timer_activate** _ _サービスの呼び出しが必要になります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2551">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2551">Parameters</span></span>

- <span data-ttu-id="ac9b0-2552">**timer_ptr** タイマー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="ac9b0-2553">**initial_ticks** タイマー有効期限の最初のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="ac9b0-2554">有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="ac9b0-2555">**reschedule_ticks** 最初の後の、すべてのタイマー有効期限のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="ac9b0-2556">このパラメーターにゼロを指定すると、タイマーは "*ワンショット*" タイマーになります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="ac9b0-2557">それ以外の定期的なタイマーの場合、有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2558">*期限切れになったワンショット タイマーは、再びアクティブにする前に*
***tx_timer_change** _ _によってリセットしなければなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2559">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2559">Return Values</span></span>

- <span data-ttu-id="ac9b0-2560">**TX_SUCCESS** (0x00) アプリケーション タイマーの変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="ac9b0-2561">**TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="ac9b0-2562">**TX_TICK_ERROR** (0x16) 最初のティックに無効な値 (0) が指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="ac9b0-2563">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2564">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2564">Allowed From</span></span>

<span data-ttu-id="ac9b0-2565">スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2566">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2566">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2567">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2568">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2568">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2569">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2569">See Also</span></span>

- <span data-ttu-id="ac9b0-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2570">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2571">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2573">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="ac9b0-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2577">tx_timer_create</span></span>

<span data-ttu-id="ac9b0-2578">アプリケーション タイマーの作成</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2579">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2579">Prototype</span></span>

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2580">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2580">Description</span></span>

<span data-ttu-id="ac9b0-2581">このサービスを使用すると、有効期限関数が指定された定期的なアプリケーション タイマーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2582">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2582">Parameters</span></span>

- <span data-ttu-id="ac9b0-2583">**timer_ptr** タイマー制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="ac9b0-2584">**name_ptr** タイマーの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="ac9b0-2585">**expiration_function** タイマーの期限が切れたとき呼び出すアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="ac9b0-2586">**expiration_input** タイマーの期限が切れたとき有効期限関数に渡す入力。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="ac9b0-2587">**initial_ticks** タイマー有効期限の最初のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="ac9b0-2588">有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="ac9b0-2589">**reschedule_ticks** 最初の後の、すべてのタイマー有効期限のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="ac9b0-2590">このパラメーターにゼロを指定すると、タイマーは "*ワンショット*" タイマーになります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="ac9b0-2591">それ以外の定期的なタイマーの場合、有効な値の範囲は 1 から 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ac9b0-2592">*ワンショット タイマーが期限切れになったら、再びアクティブにする前に tx_timer_change によってリセットしなければなりません。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="ac9b0-2593">**auto_activate** タイマーを作成時に自動的にアクティブにするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="ac9b0-2594">この値が **TX_AUTO_ACTIVATE** (0x01) の場合、タイマーはアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="ac9b0-2595">それ以外の場合、値 **TX_NO_ACTIVATE** (0x00) を選択すると、タイマーは非アクティブ状態で作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="ac9b0-2596">この場合、タイマーを実際に開始するために、その後に **_tx_timer_activate_** サービスの呼び出しが必要になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2597">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2597">Return Values</span></span>

- <span data-ttu-id="ac9b0-2598">**TX_SUCCESS** (0x00) アプリケーション タイマーの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="ac9b0-2599">**TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="ac9b0-2600">ポインターが NULL であるか、タイマーは既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="ac9b0-2601">**TX_TICK_ERROR** (0x16) 最初のティックに無効な値 (0) が指定されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="ac9b0-2602">**TX_ACTIVATE_ERROR** (0x17) 無効なアクティブ化が選択されました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="ac9b0-2603">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2604">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2604">Allowed From</span></span>

<span data-ttu-id="ac9b0-2605">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2606">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2606">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2607">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2608">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2608">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2609">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2609">See Also</span></span>

- <span data-ttu-id="ac9b0-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2610">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2611">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2613">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="ac9b0-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="ac9b0-2618">アプリケーション タイマーの非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2619">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2620">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2620">Description</span></span>

<span data-ttu-id="ac9b0-2621">このサービスを使用すると、指定されたアプリケーション タイマーが非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="ac9b0-2622">タイマーが既に非アクティブ化されている場合、このサービスは無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2623">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2623">Parameters</span></span>

- <span data-ttu-id="ac9b0-2624">**timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2625">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2625">Return Values</span></span>

- <span data-ttu-id="ac9b0-2626">**TX_SUCCESS** (0x00) アプリケーション タイマーの非アクティブ化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="ac9b0-2627">**TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2628">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2628">Allowed From</span></span>

<span data-ttu-id="ac9b0-2629">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2630">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2630">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2631">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2632">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2633">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2633">See Also</span></span>

- <span data-ttu-id="ac9b0-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2634">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2635">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2636">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2637">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="ac9b0-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2641">tx_timer_delete</span></span>

<span data-ttu-id="ac9b0-2642">アプリケーション タイマーの削除</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2643">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2644">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2644">Description</span></span>

<span data-ttu-id="ac9b0-2645">このサービスを使用すると、指定されたアプリケーション タイマーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2646">*削除されたタイマーを使用できないようにするのは、アプリケーションの役割です。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2647">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2647">Parameters</span></span>

- <span data-ttu-id="ac9b0-2648">**timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2649">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2649">Return Values</span></span>

- <span data-ttu-id="ac9b0-2650">**TX_SUCCESS** (0x00) アプリケーション タイマーの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="ac9b0-2651">**TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="ac9b0-2652">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2653">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2653">Allowed From</span></span>

<span data-ttu-id="ac9b0-2654">Threads</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2655">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2655">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2656">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2657">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2658">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2658">See Also</span></span>

- <span data-ttu-id="ac9b0-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2659">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2660">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2661">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="ac9b0-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2666">tx_timer_info_get</span></span>

<span data-ttu-id="ac9b0-2667">アプリケーション タイマーに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2668">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2669">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2669">Description</span></span>

<span data-ttu-id="ac9b0-2670">このサービスを使用すると、指定されたアプリケーション タイマーに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2671">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2671">Parameters</span></span>

- <span data-ttu-id="ac9b0-2672">**timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="ac9b0-2673">**name** タイマーの名前へのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="ac9b0-2674">**active** タイマーのアクティブ表示の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="ac9b0-2675">タイマーがアクティブでない場合やこのサービスがタイマー自体から呼び出された場合は、**TX_FALSE** 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="ac9b0-2676">それ以外の場合、タイマーがアクティブな場合は、**TX_TRUE** 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="ac9b0-2677">**remaining_ticks** タイマーが期限切れになるまでのタイマー刻み数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="ac9b0-2678">**reschedule_ticks** このタイマーを自動的に再スケジュールするために使用されるタイマー刻み数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="ac9b0-2679">値がゼロの場合、タイマーはワンショットであり、再スケジュールされません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="ac9b0-2680">**next_timer** 次に作成されるアプリケーション タイマーのポインターの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2681">*パラメーターに **TX_NULL** を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2682">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2682">Return Values</span></span>

- <span data-ttu-id="ac9b0-2683">**TX_SUCCESS** (0x00) タイマー情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="ac9b0-2684">**TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2685">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2685">Allowed From</span></span>

<span data-ttu-id="ac9b0-2686">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ac9b0-2687">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2687">Preemption Possible</span></span>

<span data-ttu-id="ac9b0-2688">いいえ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2689">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2689">Example</span></span>

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2690">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2690">See Also</span></span>

- <span data-ttu-id="ac9b0-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2691">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2692">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2693">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2695">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="ac9b0-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="ac9b0-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="ac9b0-2700">タイマー パフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2701">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2702">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2702">Description</span></span>

<span data-ttu-id="ac9b0-2703">このサービスを使用すると、指定されたアプリケーション タイマーに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-2704">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ac9b0-2705">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2705">Parameters</span></span>
- <span data-ttu-id="ac9b0-2706">**timer_ptr** 以前に作成されたタイマーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="ac9b0-2707">**activates** このタイマーで実行されたアクティブ化要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="ac9b0-2708">**reactivates** この周期的なタイマーに従って実行された自動再アクティブ化の回数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="ac9b0-2709">**deactivates** このタイマーで実行された非アクティブ化要求数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="ac9b0-2710">**expirations** このタイマーの有効期限切れの回数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="ac9b0-2711">**expiration_adjusts** このタイマーで実行される内部有効期限調整の数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="ac9b0-2712">これらの調整は、既定のタイマー一覧サイズより大きいタイマー (既定では有効期限が 32 刻みを超えるタイマー) のタイマー割り込み処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="ac9b0-2713">[注] *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2714">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2714">Return Values</span></span>

- <span data-ttu-id="ac9b0-2715">**TX_SUCCESS** (0x00) タイマー パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="ac9b0-2716">**TX_PTR_ERROR** (0x03) タイマー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="ac9b0-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2718">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2718">Allowed From</span></span>

<span data-ttu-id="ac9b0-2719">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2720">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2720">Example</span></span>

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2721">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2721">See Also</span></span>

- <span data-ttu-id="ac9b0-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2722">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2723">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2724">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2726">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="ac9b0-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="ac9b0-2730">タイマー システムに関するパフォーマンス情報の取得</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="ac9b0-2731">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="ac9b0-2732">説明</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2732">Description</span></span>

<span data-ttu-id="ac9b0-2733">このサービスを使用すると、システム内のすべてのアプリケーション タイマーに関するパフォーマンス情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac9b0-2734">*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="ac9b0-2735">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2735">**Parameters**</span></span>

- <span data-ttu-id="ac9b0-2736">**activates** すべてのタイマーで実行されたアクティブ化要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="ac9b0-2737">**reactivates** すべての周期的なタイマーに従って実行された自動再アクティブ化の合計回数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="ac9b0-2738">**deactivates** すべてのタイマーで実行された非アクティブ化要求の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="ac9b0-2739">**expirations** すべてのタイマーの有効期限切れの合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="ac9b0-2740">**expiration_adjusts** すべてのタイマーで実行された内部有効期限調整の合計数の保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="ac9b0-2741">これらの調整は、既定のタイマー一覧サイズより大きいタイマー (既定では有効期限が 32 刻みを超えるタイマー) のタイマー割り込み処理で行われます。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="ac9b0-2742">*パラメーターに **TX_NULL** を指定することは、そのパラメーターが必須ではないことを示します。*</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="ac9b0-2743">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2743">Return Values</span></span>

- <span data-ttu-id="ac9b0-2744">**TX_SUCCESS** (0x00) タイマー システム パフォーマンスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="ac9b0-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ac9b0-2746">許可元</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2746">Allowed From</span></span>

<span data-ttu-id="ac9b0-2747">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="ac9b0-2748">例</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2748">Example</span></span>

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ac9b0-2749">参照</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2749">See Also</span></span>

- <span data-ttu-id="ac9b0-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2750">tx_timer_activate</span></span>
- <span data-ttu-id="ac9b0-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2751">tx_timer_change</span></span>
- <span data-ttu-id="ac9b0-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2752">tx_timer_create</span></span>
- <span data-ttu-id="ac9b0-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="ac9b0-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2754">tx_timer_delete</span></span>
- <span data-ttu-id="ac9b0-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="ac9b0-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="ac9b0-2756">tx_timer_performance_info_get</span></span>
