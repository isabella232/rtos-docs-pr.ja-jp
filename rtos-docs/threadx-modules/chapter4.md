---
title: 第 4 章 - モジュール API
author: philmea
ms.author: philmea
description: この記事では、モジュールで使用できる追加の API の概要を示します。
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810304"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="f9109-103">第 4 章 - モジュール API</span><span class="sxs-lookup"><span data-stu-id="f9109-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="f9109-104">モジュール API の概要</span><span class="sxs-lookup"><span data-stu-id="f9109-104">Summary of Module APIs</span></span>

<span data-ttu-id="f9109-105">次のように、モジュールではいくつかの追加の API 関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9109-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="f9109-106">***txm_module_application_request** _ - _常駐コードに対するアプリケーション固有の要求*</span><span class="sxs-lookup"><span data-stu-id="f9109-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="f9109-107">***txm_module_object_allocate** _ - _オブジェクトに対してモジュールの外部でメモリを割り当てます*</span><span class="sxs-lookup"><span data-stu-id="f9109-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="f9109-108">***txm_module_object_deallocate** _ - _以前に割り当てられたオブジェクト メモリの割り当てを解除します*</span><span class="sxs-lookup"><span data-stu-id="f9109-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="f9109-109">***txm_module_object_pointer_get** _ - _システム オブジェクトを見つけ、オブジェクト ポインターを取得します*</span><span class="sxs-lookup"><span data-stu-id="f9109-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="f9109-110">***txm_module_object_pointer_get_extended** _ - _システム オブジェクトを見つけ、名前の長さに関して安全なオブジェクト ポインターを取得します*</span><span class="sxs-lookup"><span data-stu-id="f9109-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="f9109-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9109-111">Return values</span></span>

<span data-ttu-id="f9109-112">一部の Azure RTOS API では、追加のエラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="f9109-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="f9109-113">これらの追加のエラー コードは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="f9109-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="f9109-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): モジュールに API 呼び出しを行うための適切なプロパティがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f9109-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="f9109-115">たとえば、ユーザー モードでのトレース API の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="f9109-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="f9109-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): モジュールによって指定されたメモリが無効であるか、または無効な場所にあることを示します。</span><span class="sxs-lookup"><span data-stu-id="f9109-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="f9109-117">たとえば、メモリ保護モジュールでは、オブジェクト コントロール ブロックを、モジュールがアクセスできるメモリ内に配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="f9109-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="f9109-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): API に指定されたコールバックが、モジュールのコードの範囲外であるため、無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="f9109-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="f9109-119">txm_module_application_request</span></span>

<span data-ttu-id="f9109-120">常駐コードに対するアプリケーション固有の要求。</span><span class="sxs-lookup"><span data-stu-id="f9109-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="f9109-121">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f9109-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="f9109-122">説明</span><span class="sxs-lookup"><span data-stu-id="f9109-122">Description</span></span>

<span data-ttu-id="f9109-123">このサービスは、アプリケーションの常駐部分に対して指定された要求を行います。</span><span class="sxs-lookup"><span data-stu-id="f9109-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="f9109-124">要求構造体が呼び出しの前に準備されていることが前提になっています。</span><span class="sxs-lookup"><span data-stu-id="f9109-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="f9109-125">要求の実際の処理は、関数 ***_txm_module_manager_application_request*** 内の常駐コードで行われます。</span><span class="sxs-lookup"><span data-stu-id="f9109-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="f9109-126">既定では、この関数は空のままになっていて、常駐アプリケーションの開発者が変更するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="f9109-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f9109-127">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-127">Input parameters</span></span>

- <span data-ttu-id="f9109-128">**request** (アプリケーションで定義された) 要求 ID</span><span class="sxs-lookup"><span data-stu-id="f9109-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="f9109-129">**param_1** 最初のパラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-129">**param_1** First parameter</span></span>
- <span data-ttu-id="f9109-130">**param_2** 2 番目のパラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="f9109-131">**param_3** 3 番目のパラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="f9109-132">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9109-132">Return values</span></span>

- <span data-ttu-id="f9109-133">**TX_SUCCESS** (0x00) 要求に成功しました。</span><span class="sxs-lookup"><span data-stu-id="f9109-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="f9109-134">**TX_NOT_AVAILABLE** (0x1D) 要求は、常駐コードによってサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f9109-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9109-135">許可元</span><span class="sxs-lookup"><span data-stu-id="f9109-135">Allowed from</span></span>

<span data-ttu-id="f9109-136">モジュール スレッド</span><span class="sxs-lookup"><span data-stu-id="f9109-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="f9109-137">例</span><span class="sxs-lookup"><span data-stu-id="f9109-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="f9109-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="f9109-138">txm_module_object_allocate</span></span>

<span data-ttu-id="f9109-139">モジュール オブジェクト コントロール ブロックに対し、(常駐アプリケーションによって作成された) オブジェクト プールのメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f9109-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="f9109-140">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f9109-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="f9109-141">説明</span><span class="sxs-lookup"><span data-stu-id="f9109-141">Description</span></span>

<span data-ttu-id="f9109-142">このサービスは、モジュールの外部のメモリからモジュール オブジェクトにメモリを割り当てます。これにより、モジュールのコードによってオブジェクト コントロール ブロックが破損するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="f9109-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="f9109-143">メモリ保護システムでは、すべてのオブジェクト コントロール ブロックは、この API を使用して割り当てられてからでないと、作成できません。</span><span class="sxs-lookup"><span data-stu-id="f9109-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f9109-144">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-144">Input parameters</span></span>

- <span data-ttu-id="f9109-145">**object_ptr** 割り当てが成功したときのオブジェクト ポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="f9109-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="f9109-146">**object_size** 割り当てられるオブジェクトのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="f9109-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9109-147">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9109-147">Return values</span></span>

- <span data-ttu-id="f9109-148">**TX_SUCCESS** (0x00) オブジェクトの割り当てが成功しました。</span><span class="sxs-lookup"><span data-stu-id="f9109-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="f9109-149">**TX_NO_MEMORY** (0x10) 十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="f9109-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="f9109-150">**TX_NOT_AVAILABLE** (0x1D) モジュール マネージャーによって、割り当て元のオブジェクト プールが作成されていません</span><span class="sxs-lookup"><span data-stu-id="f9109-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9109-151">許可元</span><span class="sxs-lookup"><span data-stu-id="f9109-151">Allowed from</span></span>

<span data-ttu-id="f9109-152">モジュール スレッド</span><span class="sxs-lookup"><span data-stu-id="f9109-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="f9109-153">例</span><span class="sxs-lookup"><span data-stu-id="f9109-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="f9109-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9109-154">See also</span></span>

- <span data-ttu-id="f9109-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="f9109-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="f9109-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="f9109-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="f9109-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="f9109-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="f9109-158">以前に割り当てられたオブジェクト メモリの割り当てを解除します</span><span class="sxs-lookup"><span data-stu-id="f9109-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="f9109-159">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f9109-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="f9109-160">説明</span><span class="sxs-lookup"><span data-stu-id="f9109-160">Description</span></span>

<span data-ttu-id="f9109-161">***このサービスは、不要になったため非推奨となりました***。</span><span class="sxs-lookup"><span data-stu-id="f9109-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="f9109-162">以前 \*\**txm_module_object_allocate* *_ によって割り当てられたメモリが、"_* _tx_\__delete サービス\*\*\*" で割り当て解除されます。</span><span class="sxs-lookup"><span data-stu-id="f9109-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f9109-163">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-163">Input parameters</span></span>

- <span data-ttu-id="f9109-164">**object_ptr** 割り当てを解除するオブジェクト ポインター。</span><span class="sxs-lookup"><span data-stu-id="f9109-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9109-165">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9109-165">Return values</span></span>

- <span data-ttu-id="f9109-166">**TX_SUCCESS** (0x00) オブジェクトの割り当てが成功しました。</span><span class="sxs-lookup"><span data-stu-id="f9109-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9109-167">許可元</span><span class="sxs-lookup"><span data-stu-id="f9109-167">Allowed from</span></span>

<span data-ttu-id="f9109-168">モジュール スレッド</span><span class="sxs-lookup"><span data-stu-id="f9109-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="f9109-169">例</span><span class="sxs-lookup"><span data-stu-id="f9109-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="f9109-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9109-170">See also</span></span>

- <span data-ttu-id="f9109-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="f9109-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="f9109-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="f9109-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="f9109-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="f9109-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="f9109-174">システム オブジェクトを見つけて、オブジェクト ポインターを取得します</span><span class="sxs-lookup"><span data-stu-id="f9109-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9109-175">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f9109-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="f9109-176">説明</span><span class="sxs-lookup"><span data-stu-id="f9109-176">Description</span></span>

<span data-ttu-id="f9109-177">このサービスは、特定の名前を持つ特定の種類のオブジェクト ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f9109-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="f9109-178">オブジェクトが見つからない場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="f9109-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="f9109-179">そうでなく、オブジェクトが見つかった場合は、そのオブジェクトのアドレスが "object_ptr" に入れられます。</span><span class="sxs-lookup"><span data-stu-id="f9109-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="f9109-180">これで、このポインターを使用して、システム サービス呼び出しを行って、常駐コードやシステム内の他の読み込み済みモジュールと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="f9109-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f9109-181">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-181">Input parameters</span></span>

- <span data-ttu-id="f9109-182">**object_type** 要求された ThreadX オブジェクトの種類。</span><span class="sxs-lookup"><span data-stu-id="f9109-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="f9109-183">有効な種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f9109-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="f9109-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="f9109-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="f9109-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="f9109-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="f9109-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="f9109-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="f9109-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="f9109-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="f9109-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="f9109-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="f9109-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="f9109-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="f9109-196">**name** オブジェクトの作成時に定義された、アプリケーション固有のオブジェクト名。</span><span class="sxs-lookup"><span data-stu-id="f9109-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="f9109-197">**object_ptr** オブジェクト ポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="f9109-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9109-198">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9109-198">Return values</span></span>

- <span data-ttu-id="f9109-199">**TX_SUCCESS** (0x00) オブジェクトの取得が成功しました。</span><span class="sxs-lookup"><span data-stu-id="f9109-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="f9109-200">**TX_OPTION_ERROR** (0x08) オブジェクトの種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="f9109-201">**TX_PTR_ERROR** (0x03) 宛先が無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="f9109-202">**TX_SIZE_ERROR** (0x05) サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="f9109-203">**TX_NO_INSTANCE** (0x0D) オブジェクトが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f9109-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9109-204">許可元</span><span class="sxs-lookup"><span data-stu-id="f9109-204">Allowed from</span></span>

<span data-ttu-id="f9109-205">モジュール スレッド</span><span class="sxs-lookup"><span data-stu-id="f9109-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="f9109-206">例</span><span class="sxs-lookup"><span data-stu-id="f9109-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="f9109-207">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9109-207">See also</span></span>

- <span data-ttu-id="f9109-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="f9109-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="f9109-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="f9109-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="f9109-210">システム オブジェクトを見つけて、オブジェクト ポインターを取得します</span><span class="sxs-lookup"><span data-stu-id="f9109-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9109-211">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f9109-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="f9109-212">説明</span><span class="sxs-lookup"><span data-stu-id="f9109-212">Description</span></span>

<span data-ttu-id="f9109-213">このサービスは、特定の名前を持つ特定の種類のオブジェクト ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f9109-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="f9109-214">オブジェクトが見つからない場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="f9109-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="f9109-215">そうでなく、オブジェクトが見つかった場合は、そのオブジェクトのアドレスが "object_ptr" に入れられます。</span><span class="sxs-lookup"><span data-stu-id="f9109-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="f9109-216">これで、このポインターを使用して、システム サービス呼び出しを行って、常駐コードやシステム内の他の読み込み済みモジュールと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="f9109-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f9109-217">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9109-217">Input parameters</span></span>

- <span data-ttu-id="f9109-218">**object_type** 要求された ThreadX オブジェクトの種類。</span><span class="sxs-lookup"><span data-stu-id="f9109-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="f9109-219">有効な種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f9109-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="f9109-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="f9109-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="f9109-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="f9109-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="f9109-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="f9109-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="f9109-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="f9109-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="f9109-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="f9109-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="f9109-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="f9109-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="f9109-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="f9109-232">**name** オブジェクトの作成時に定義された、アプリケーション固有のオブジェクト名。</span><span class="sxs-lookup"><span data-stu-id="f9109-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="f9109-233">**name_length** 名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="f9109-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="f9109-234">**object_ptr** オブジェクト ポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="f9109-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9109-235">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9109-235">Return values</span></span>

- <span data-ttu-id="f9109-236">**TX_SUCCESS** (0x00) オブジェクトの取得が成功しました。</span><span class="sxs-lookup"><span data-stu-id="f9109-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="f9109-237">**TX_OPTION_ERROR** (0x08) オブジェクトの種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="f9109-238">**TX_PTR_ERROR** (0x03) 宛先が無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="f9109-239">**TX_SIZE_ERROR** (0x05) サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="f9109-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="f9109-240">**TX_NO_INSTANCE** (0x0D) オブジェクトが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f9109-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9109-241">許可元</span><span class="sxs-lookup"><span data-stu-id="f9109-241">Allowed from</span></span>

<span data-ttu-id="f9109-242">モジュール スレッド</span><span class="sxs-lookup"><span data-stu-id="f9109-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="f9109-243">例</span><span class="sxs-lookup"><span data-stu-id="f9109-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="f9109-244">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9109-244">See also</span></span>

- <span data-ttu-id="f9109-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="f9109-245">txm_module_manager_object_pointer_get</span></span>
