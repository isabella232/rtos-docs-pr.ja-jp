---
title: 第 3 章 - ARMv8-M 用の ThreadX API
description: この章では、ARMv8-M 固有の ThreadX サービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377510"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="a072a-103">第 3 章  ARMv8-M 用の ThreadX API</span><span class="sxs-lookup"><span data-stu-id="a072a-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="a072a-104">この章では、ARMv8-M 固有の ThreadX サービスについてアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="a072a-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="a072a-105">これらの名前は、類似するすべてのサービスがグループ化されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a072a-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="a072a-106">以下の説明にある「戻り値」セクション内で **太字** で記載されている値は、API エラー チェックを無効にする際に使用される **TX_DISABLE_ERROR_CHECKING** 定義の影響を受けません。一方、太字ではない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="a072a-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="a072a-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) セキュア メモリ内でスレッド スタックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a072a-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="a072a-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) セキュア メモリ内のスレッド スタックを解放します</span><span class="sxs-lookup"><span data-stu-id="a072a-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="a072a-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="a072a-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="a072a-110">セキュア メモリ内でスレッド スタックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a072a-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="a072a-111">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="a072a-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="a072a-112">説明</span><span class="sxs-lookup"><span data-stu-id="a072a-112">Description</span></span>

<span data-ttu-id="a072a-113">このサービスは、セキュア メモリ内でサイズ stack_size バイトのスタックを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a072a-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="a072a-114">この関数は、セキュアな関数を呼び出すすべてのスレッドに対して呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a072a-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a072a-115">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="a072a-115">Input Parameters</span></span>

- <span data-ttu-id="a072a-116">**thread_ptr** 以前作成されたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a072a-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="a072a-117">**stack_size** セキュア スタックのサイズ。</span><span class="sxs-lookup"><span data-stu-id="a072a-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="a072a-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="a072a-118">Return Values</span></span>

- <span data-ttu-id="a072a-119">**TX_SUCCESS** (0x00) 要求に成功しました。</span><span class="sxs-lookup"><span data-stu-id="a072a-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="a072a-120">**TX_SIZE_ERROR** (0x05) スタック サイズが範囲外です。</span><span class="sxs-lookup"><span data-stu-id="a072a-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="a072a-121">**TX_THREAD_ERROR** (0x0E) 無効なスレッド ポインターです。</span><span class="sxs-lookup"><span data-stu-id="a072a-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="a072a-122">**TX_NO_MEMORY** (0x10) メモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="a072a-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="a072a-123">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="a072a-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="a072a-124">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはセキュア モードで実行するようコンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="a072a-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a072a-125">許可元</span><span class="sxs-lookup"><span data-stu-id="a072a-125">Allowed From</span></span>

<span data-ttu-id="a072a-126">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="a072a-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="a072a-127">例</span><span class="sxs-lookup"><span data-stu-id="a072a-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="a072a-128">参照</span><span class="sxs-lookup"><span data-stu-id="a072a-128">See Also</span></span>

<span data-ttu-id="a072a-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="a072a-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="a072a-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="a072a-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="a072a-131">セキュア メモリ内のスレッド スタックを解放します。</span><span class="sxs-lookup"><span data-stu-id="a072a-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="a072a-132">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="a072a-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="a072a-133">説明</span><span class="sxs-lookup"><span data-stu-id="a072a-133">Description</span></span>

<span data-ttu-id="a072a-134">このサービスは、セキュア メモリ内のスレッドのセキュア スタックを解放します。</span><span class="sxs-lookup"><span data-stu-id="a072a-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="a072a-135">スレッドにセキュア スタックが存在し、スレッドがセキュアな関数を呼び出す必要がなくなった場合またはスレッドが削除された場合は、この関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a072a-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a072a-136">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="a072a-136">Input Parameters</span></span>

- <span data-ttu-id="a072a-137">**thread_ptr** 以前作成されたスレッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a072a-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="a072a-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="a072a-138">Return Values</span></span>

- <span data-ttu-id="a072a-139">**TX_SUCCESS** (0x00) 要求に成功しました。</span><span class="sxs-lookup"><span data-stu-id="a072a-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="a072a-140">**TX_THREAD_ERROR** (0x0E) 無効なスレッド ポインターです。</span><span class="sxs-lookup"><span data-stu-id="a072a-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="a072a-141">**TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="a072a-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="a072a-142">**TX_FEATURE_NOT_ENABLED** (0xFF) システムはセキュア モードで実行するようコンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="a072a-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a072a-143">許可元</span><span class="sxs-lookup"><span data-stu-id="a072a-143">Allowed From</span></span>

<span data-ttu-id="a072a-144">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="a072a-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="a072a-145">例</span><span class="sxs-lookup"><span data-stu-id="a072a-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="a072a-146">参照</span><span class="sxs-lookup"><span data-stu-id="a072a-146">See Also</span></span>

<span data-ttu-id="a072a-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="a072a-147">tx_thread_secure_stack_allocate</span></span>
