---
title: 第 4 章 - USBX ホスト サービスの説明
description: USBX ホスト サービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813271"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="c73ab-103">第 4 章 - USBX ホスト サービスの説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="c73ab-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="c73ab-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="c73ab-105">ホスト操作のために USBX を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-106">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="c73ab-107">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-107">Description</span></span>

<span data-ttu-id="c73ab-108">この関数は、USB ホスト スタックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="c73ab-109">USBX 内部で使用するために、指定されたメモリ領域が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="c73ab-110">UX_SUCCESS が返された場合、USBX はホスト コントローラーとクラス登録ができるようになっています。</span><span class="sxs-lookup"><span data-stu-id="c73ab-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="c73ab-111">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-111">Input Parameter</span></span>

- <span data-ttu-id="c73ab-112">**system_change_function**: デバイスの変更をアプリケーションに通知する省略可能なコールバック ルーチンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="c73ab-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-113">Return Value</span></span>

- <span data-ttu-id="c73ab-114">**NX_SUCCESS**: (0x00) 初期化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="c73ab-115">**UX_MEMORY_INSUFFICIENT**: (0x12) メモリの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-116">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="c73ab-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="c73ab-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="c73ab-118">エンドポイントの転送要求にアタッチされているすべてのトランザクションを中止します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-119">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="c73ab-120">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-120">Description</span></span>

<span data-ttu-id="c73ab-121">この関数は、エンドポイントにアタッチされている特定の転送要求の、アクティブまたは保留中のすべてのトランザクションをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="c73ab-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="c73ab-122">転送要求にコールバック関数がアタッチされている場合、コールバック関数は UX_TRANSACTION_ABORTED 状態で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="c73ab-123">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-123">Input Parameter</span></span>

- <span data-ttu-id="c73ab-124">**endpoint**: エンドポイントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-125">Return Values</span></span>

- <span data-ttu-id="c73ab-126">**UX_SUCCESS**: (0x00) エラーはありません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="c73ab-127">**UX_ENDPOINT_HANDLE_UNKNOWN**: (0x53) エンドポイント ハンドルが無効です。</span><span class="sxs-lookup"><span data-stu-id="c73ab-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-128">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="c73ab-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="c73ab-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="c73ab-130">クラス コンテナーへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-131">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="c73ab-132">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-132">Description</span></span>

<span data-ttu-id="c73ab-133">この関数は、クラス コンテナーへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="c73ab-134">クラスまたはアプリケーションがデバイスを開くとき、クラスはインスタンスを検索するために、そのコンテナーを USB スタックから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="c73ab-135">class_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は UX_MAX_CLASS_NAME_LENGTH よりも大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-136">Parameters</span></span>

- <span data-ttu-id="c73ab-137">**class_name**: クラス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="c73ab-138">**class**: クラスの名前のクラス コンテナーを含む関数呼び出しによって更新されるポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-139">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-139">Return Values</span></span>

- <span data-ttu-id="c73ab-140">**UX_SUCCESS**: (0x00) エラーはありません。返されるとき、クラス フィールドにはクラス コンテナーへのポインターが登録されます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="c73ab-141">**UX_HOST_CLASS_UNKNOWN**: (0x59) クラスがスタックによって認識されていません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-142">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="c73ab-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="c73ab-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="c73ab-144">USB クラスを USB スタックに登録します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-145">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="c73ab-146">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-146">Description</span></span>

<span data-ttu-id="c73ab-147">この関数は、USB クラスを USB スタックに登録します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="c73ab-148">クラスには、USB スタックが次のようなコマンドを送信するためのエントリ ポイントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="c73ab-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="c73ab-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="c73ab-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="c73ab-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="c73ab-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="c73ab-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="c73ab-152">*class_name* という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_MAX_CLASS_NAME_LENGTH** よりも大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-153">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-153">Parameters</span></span>

- <span data-ttu-id="c73ab-154">**class_name**: クラスの名前へのポインター。有効なエントリは、USBX の USB クラスの下にあるファイル ux_system_initialize.c にあります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="c73ab-155">**class_entry_address**: クラスのエントリ関数のアドレス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-156">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-156">Return Values</span></span>

- <span data-ttu-id="c73ab-157">**UX_SUCCESS**: (0x00) クラスが正常にインストールされました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="c73ab-158">**UX_MEMORY_ARRAY_FULL**: (0x1a) このクラスを格納するためのメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="c73ab-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="c73ab-159">**UX_HOST_CLASS_ALREADY_INSTALLED**: (0x58) ホスト クラスは既にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="c73ab-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-160">例:</span><span class="sxs-lookup"><span data-stu-id="c73ab-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="c73ab-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="c73ab-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="c73ab-162">クラス コンテナーの新しいクラス インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-163">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="c73ab-164">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-164">Description</span></span>

<span data-ttu-id="c73ab-165">この関数は、クラス コンテナーの新しいクラス インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="c73ab-166">クラスの複雑さを軽減するために、このクラス インスタンスは、クラス コードに含まれません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="c73ab-167">代わりに、各クラス インスタンスは、メイン スタックに存在するクラス コンテナーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-168">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-168">Parameters</span></span>

- <span data-ttu-id="c73ab-169">**class**: クラス コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="c73ab-170">**class_instance**: 作成されるクラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="c73ab-171">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-171">Return Value</span></span>

- <span data-ttu-id="c73ab-172">**UX_SUCCESS**: (0x00) クラス コンテナーにクラス インスタンスがアタッチされました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-173">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="c73ab-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="c73ab-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="c73ab-175">クラス コンテナーのクラス インスタンスを破棄します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-176">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="c73ab-177">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-177">Description</span></span>

<span data-ttu-id="c73ab-178">この関数は、クラス コンテナーのクラス インスタンスを破棄します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-179">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-179">Parameters</span></span>

- <span data-ttu-id="c73ab-180">**class**: クラス コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="c73ab-181">**class_instance**: 破棄するインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-182">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-182">Return Values</span></span>

- <span data-ttu-id="c73ab-183">**UX_SUCCESS**: (0x00) クラス インスタンスが破棄されました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="c73ab-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) クラス コンテナーにクラス インスタンスがアタッチされていません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-185">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="c73ab-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="c73ab-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="c73ab-187">特定のクラスのクラス インスタンス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-188">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="c73ab-189">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-189">Description</span></span>

<span data-ttu-id="c73ab-190">この関数は、特定のクラスのクラス インスタンス ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="c73ab-191">クラスの複雑さを軽減するために、このクラス インスタンスは、クラス コードに含まれません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="c73ab-192">代わりに、各クラス インスタンスはクラス コンテナーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="c73ab-193">この関数は、クラス コンテナー内のクラス インスタンスを検索するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-194">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-194">Parameters</span></span>

- <span data-ttu-id="c73ab-195">**class**: クラス コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="c73ab-196">**class_index**: コンテナーにアタッチされたクラスのリスト内で、関数呼び出しによって使用されるインデックス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="c73ab-197">**class_instance**: 関数呼び出しによって返されるインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-198">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-198">Return Values</span></span>

- <span data-ttu-id="c73ab-199">**UX_SUCCESS**: (0x00) クラス インスタンスが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="c73ab-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) クラス コンテナーにアタッチされているクラス インスタンスはありません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-201">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="c73ab-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="c73ab-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="c73ab-203">構成コンテナーへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-204">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="c73ab-205">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-205">Description</span></span>

<span data-ttu-id="c73ab-206">この関数は、デバイス ハンドルと構成インデックスに基づいて構成コンテナーを返します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-207">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-207">Parameters</span></span>

- <span data-ttu-id="c73ab-208">**device**: 要求された構成を所有しているデバイス コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="c73ab-209">**configuration_index**: 検索される構成のインデックス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="c73ab-210">**configuration**: 返される構成コンテナーへのポインターのアドレス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-211">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-211">Return Values</span></span>

- <span data-ttu-id="c73ab-212">**UX_SUCCESS**: (0x00) 構成が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="c73ab-213">**UX_DEVICE_HANDLE_UNKNOWN**: (0x50) デバイス コンテナーが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="c73ab-214">**UX_CONFIGURATION_HANDLE_UNKNOWN**: (0x51) インデックスの構成ハンドルが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-215">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="c73ab-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="c73ab-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="c73ab-217">デバイスの特定の構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-218">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="c73ab-219">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-219">Description</span></span>

<span data-ttu-id="c73ab-220">この関数は、デバイスの特定の構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="c73ab-221">この構成がデバイスに設定されている場合、既定では、各デバイス インターフェイスとそれに関連付けられている代替設定 0 がデバイスでアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="c73ab-222">デバイス/インターフェイス クラスで特定のインターフェイスの設定を変更する場合は、**ux_host_stack_interface_setting_select** サービス呼び出しを発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-223">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-223">Parameters</span></span>

- <span data-ttu-id="c73ab-224">**configuration**: このデバイスに対して有効にする構成コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-225">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-225">Return Values</span></span>

- <span data-ttu-id="c73ab-226">**UX_SUCCESS**: (0x00) 構成が正常に選択されました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="c73ab-227">**UX_CONFIGURATION_HANDLE_UNKNOWN**: (0x51) 構成ハンドルが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="c73ab-228">**UX_OVER_CURRENT_CONDITION**: (0x43) この構成は、バスに過電流の状態が存在します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-229">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="c73ab-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="c73ab-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="c73ab-231">デバイス コンテナーへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-232">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="c73ab-233">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-233">Description</span></span>

<span data-ttu-id="c73ab-234">この関数は、インデックスに基づいてデバイス コンテナーを返します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="c73ab-235">デバイス インデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-235">The device index starts with 0.</span></span> <span data-ttu-id="c73ab-236">コントローラーが複数あってバイト インデックスが十分でない可能性もあるため、インデックスは ULONG です。</span><span class="sxs-lookup"><span data-stu-id="c73ab-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="c73ab-237">デバイス インデックスを、バス固有のデバイス アドレスと混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c73ab-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-238">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-238">Parameters</span></span>

- <span data-ttu-id="c73ab-239">**device_index**: デバイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="c73ab-240">**device**: 返されるデバイス コンテナーのポインターのアドレス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-241">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-241">Return Values</span></span>

- <span data-ttu-id="c73ab-242">**UX_SUCCESS**: (0x00) デバイス コンテナーが存在し、返されます</span><span class="sxs-lookup"><span data-stu-id="c73ab-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="c73ab-243">**UX_DEVICE_HANDLE_UNKNOWN**: (0X50) デバイスが不明です</span><span class="sxs-lookup"><span data-stu-id="c73ab-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-244">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="c73ab-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="c73ab-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="c73ab-246">エンドポイント コンテナーを取得します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-247">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="c73ab-248">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-248">Description</span></span>

<span data-ttu-id="c73ab-249">この関数は、インターフェイス ハンドルとエンドポイント インデックスに基づいて、エンドポイント コンテナーを返します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="c73ab-250">エンドポイントを検索する前に、インターフェイスの代替設定が選択されている、または既定の設定が使用されていることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="c73ab-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-251">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-251">Parameters</span></span>

- <span data-ttu-id="c73ab-252">**interface**: 要求されたエンドポイントを含むインターフェイス コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="c73ab-253">**endpoint_index**: このインターフェイス内のエンドポイントのインデックス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="c73ab-254">**endpoint**: 返されるエンドポイント コンテナーのアドレス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-255">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-255">Return Values</span></span>

- <span data-ttu-id="c73ab-256">**UX_SUCCESS**: (0x00) エンドポイント コンテナーが存在し、返されます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="c73ab-257">**UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) 指定されたインターフェイスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="c73ab-258">**UX_ENDPOINT_HANDLE_UNKNOWN**: (0x53) エンドポイント インデックスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-259">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="c73ab-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="c73ab-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="c73ab-261">USB コントローラーを USB スタックに登録します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-262">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="c73ab-263">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-263">Description</span></span>

<span data-ttu-id="c73ab-264">この関数は、USB コントローラーを USB スタックに登録します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="c73ab-265">主として、このコントローラーによって使用されるメモリを割り当て、コントローラーに初期化コマンドを渡します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-266">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-266">Parameters</span></span>

- <span data-ttu-id="c73ab-267">**hcd_name**: ホスト コントローラーの名前</span><span class="sxs-lookup"><span data-stu-id="c73ab-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="c73ab-268">**hcd_function**: ホスト コントローラー内で初期化を実行する関数。</span><span class="sxs-lookup"><span data-stu-id="c73ab-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="c73ab-269">**hcd_param1**: hcd によって使用される IO またはメモリ リソース。</span><span class="sxs-lookup"><span data-stu-id="c73ab-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="c73ab-270">**hcd_param2**: ホスト コントローラーによって使用される IRQ。</span><span class="sxs-lookup"><span data-stu-id="c73ab-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-271">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-271">Return Values</span></span>

- <span data-ttu-id="c73ab-272">**UX_SUCCESS**: (0x00) コントローラーが適切に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="c73ab-273">**UX_MEMORY_INSUFFICIENT**: (0x12) このコントローラーに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="c73ab-274">**UX_PORT_RESET_FAILED**: (0x31) コントローラーのリセットに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="c73ab-275">**UX_CONTROLLER_INIT_FAILED**: (0x32) コントローラーを適切に初期化できませんでした。</span><span class="sxs-lookup"><span data-stu-id="c73ab-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-276">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="c73ab-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="c73ab-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="c73ab-278">インターフェイス コンテナーのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-279">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="c73ab-280">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-280">Description</span></span>

<span data-ttu-id="c73ab-281">この関数は、構成ハンドル、インターフェイス インデックス、代替設定インデックスに基づいて、インターフェイス コンテナーを返します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-282">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-282">Parameters</span></span>

- <span data-ttu-id="c73ab-283">**configuration**: インターフェイスを所有する構成コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="c73ab-284">**interface_index**: 検索するインターフェイス インデックス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="c73ab-285">**alternate_setting_index**: 検索するインターフェイス内の代替設定。</span><span class="sxs-lookup"><span data-stu-id="c73ab-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="c73ab-286">**interface**: 返されるインターフェイス コンテナー ポインターのアドレス。</span><span class="sxs-lookup"><span data-stu-id="c73ab-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-287">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-287">Return Values</span></span>

- <span data-ttu-id="c73ab-288">**UX_SUCCESS**: (0x00)、インターフェイス インデックスと代替設定のインターフェイス コンテナーが検出され、返されました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="c73ab-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** : (0x51) 構成が存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="c73ab-290">**UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) インターフェイスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-291">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="c73ab-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="c73ab-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="c73ab-293">インターフェイスの代替設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-294">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="c73ab-295">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-295">Description</span></span>

<span data-ttu-id="c73ab-296">この関数は、選択した構成に属する特定のインターフェイスの特定の代替設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="c73ab-297">この関数を使用すると、既定の代替設定から新しい設定に変更したり、既定の代替設定に戻したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="c73ab-298">新しい代替設定を選択すると、以前のエンドポイントの特性は無効になり、再度読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="c73ab-299">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-299">Input Parameter</span></span>

- <span data-ttu-id="c73ab-300">**interface**: 代替設定を選択するインターフェイス コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-301">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-301">Return Values</span></span>

- <span data-ttu-id="c73ab-302">**UX_SUCCESS**: (0x00) このインターフェイスの代替設定が正常に選択されました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="c73ab-303">**UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) インターフェイスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-304">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="c73ab-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="c73ab-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="c73ab-306">保留中の転送要求を中止します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-307">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="c73ab-308">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-308">Description</span></span>

<span data-ttu-id="c73ab-309">この関数は、以前に送信されて保留中になっている転送要求を中止します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="c73ab-310">この関数で取り消されるのは、特定の転送要求のみです。</span><span class="sxs-lookup"><span data-stu-id="c73ab-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="c73ab-311">この関数へのコールバックは、UX_TRANSFER REQUEST_STATUS_ABORT の状態になります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="c73ab-312">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-312">Parameters</span></span>

- <span data-ttu-id="c73ab-313">**transfer_request**: 中止する転送要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-314">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-314">Return Values</span></span>

- <span data-ttu-id="c73ab-315">**UX_SUCCESS**: (0x00) この転送要求の USB 転送が取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-316">例</span><span class="sxs-lookup"><span data-stu-id="c73ab-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="c73ab-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="c73ab-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="c73ab-318">USB 転送を要求します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="c73ab-319">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="c73ab-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="c73ab-320">説明</span><span class="sxs-lookup"><span data-stu-id="c73ab-320">Description</span></span>

<span data-ttu-id="c73ab-321">この関数は、USB トランザクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-321">This function performs a USB transaction.</span></span> <span data-ttu-id="c73ab-322">実行されると、この転送要求によって、このトランザクションに対してエンドポイント パイプが選択され、パラメーター (データ ペイロード、トランザクションの長さ) が転送に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="c73ab-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="c73ab-323">制御パイプの場合、トランザクションはブロック状態になり、制御転送の 3 つのフェーズが完了したとき、または前のエラーがある場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="c73ab-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="c73ab-324">他のパイプの場合、USB スタックは USB 上のトランザクションをスケジュールしますが、完了するまで待機はしません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="c73ab-325">ブロックしないパイプに対する各転送要求には、完了ルーチン ハンドラーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="c73ab-326">関数呼び出しから制御が戻ったら、トランザクションの結果が含まれているかどうか、転送要求の状態を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="c73ab-327">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="c73ab-327">Input Parameter</span></span>

- <span data-ttu-id="c73ab-328">**transfer_request**: 転送要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c73ab-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="c73ab-329">転送要求には、転送に必要なすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c73ab-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="c73ab-330">戻り値</span><span class="sxs-lookup"><span data-stu-id="c73ab-330">Return Values</span></span>

- <span data-ttu-id="c73ab-331">**UX_SUCCESS**: (0x00) この転送要求の USB 転送が適切にスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="c73ab-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="c73ab-332">転送要求の完了時には、転送要求の状態コードを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="c73ab-333">**UX_MEMORY_INSUFFICIENT**: (0x12) 必要なコントローラー リソースを割り当てるのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="c73ab-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="c73ab-334">**UX_TRANSFER_NOT_READY**: (0x25) デバイスが無効な状態でした。ATTACHED、ADDRESSED、または CONFIGURED である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c73ab-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="c73ab-335">例:</span><span class="sxs-lookup"><span data-stu-id="c73ab-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
