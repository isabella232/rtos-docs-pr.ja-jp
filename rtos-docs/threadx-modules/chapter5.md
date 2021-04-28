---
title: 第 5 章 - モジュール マネージャー API
author: philmea
description: この記事では、アプリケーションの常駐部分で使用できるモジュール マネージャー API の概要を示します。
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810301"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="d3bcd-103">第 5 章 - モジュール マネージャー API</span><span class="sxs-lookup"><span data-stu-id="d3bcd-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="d3bcd-104">モジュール マネージャー API の概要</span><span class="sxs-lookup"><span data-stu-id="d3bcd-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="d3bcd-105">アプリケーションの常駐部分では、次のような、いくつかの追加 API を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="d3bcd-106">***txm_module_manager_external_memory_enable** _ - _共有メモリ空間へのモジュール アクセスを有効にします*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="d3bcd-107">***txm_module_manager_file_load** _ - _FileX を介してファイルからモジュールを読み込みます*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="d3bcd-108">***txm_module_manager_in_place_load** _ - _モジュール データを読み込み、インプレースで実行します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="d3bcd-109">***txm_module_manager_initialize** _ - _モジュール マネージャーを初期化します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="d3bcd-110">***txm_module_manager_mm_initialize** _ - _メモリ管理ハードウェアを初期化します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="d3bcd-111">***txm_module_manager_maximum_module_priority_set** _ - _モジュールで許可されるスレッドの最大優先度を設定します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="d3bcd-112">***txm_module_manager_memory_fault_notify** _ - _メモリ エラー発生時にアプリケーション コールバックを登録します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="d3bcd-113">***txm_module_manager_memory_load** _ - _メモリからモジュールを読み込みます*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="d3bcd-114">***txm_module_manager_object_pool_create** _ - _モジュールのオブジェクト プールを作成します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="d3bcd-115">***txm_module_manager_properties_get** _ - _モジュールのプロパティを取得します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="d3bcd-116">***txm_module_manager_start** _ - _指定されたモジュールの実行を開始します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="d3bcd-117">***txm_module_manager_stop** _ - _指定されたモジュールの実行を停止します*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="d3bcd-118">***txm_module_manager_unload** _ - _モジュールをアンロードします*</span><span class="sxs-lookup"><span data-stu-id="d3bcd-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="d3bcd-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="d3bcd-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="d3bcd-120">モジュールが共有メモリ空間にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-121">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="d3bcd-122">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-122">Description</span></span>

<span data-ttu-id="d3bcd-123">このサービスは、モジュールがアクセスできる共有メモリ領域のエントリをメモリ管理ハードウェア テーブルに作成します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-124">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-124">Input parameters</span></span>

- <span data-ttu-id="d3bcd-125">**module_instance** モジュールのインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="d3bcd-126">**start_address** 共有メモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="d3bcd-127">**length** 共有メモリ領域の長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="d3bcd-128">**attributes** メモリ領域の属性 (キャッシュ、読み取り、書き込みなど)。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="d3bcd-129">属性はポートに固有です。属性の形式については、「[付録](appendix.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-130">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-130">Return values</span></span>

- <span data-ttu-id="d3bcd-131">**TX_SUCCESS** (0x00) メモリ エントリの作成が成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="d3bcd-132">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていないか、機能を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="d3bcd-133">**TX_PTR_ERROR** (0x03) モジュール インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="d3bcd-134">**TX_START_ERROR** (0x10) モジュールが読み込み済み状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="d3bcd-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 開始アドレスの配置が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="d3bcd-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-137">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-137">Allowed from</span></span>

<span data-ttu-id="d3bcd-138">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-139">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="d3bcd-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="d3bcd-141">FileX を介してファイルからモジュールを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-142">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="d3bcd-143">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-143">Description</span></span>

<span data-ttu-id="d3bcd-144">このサービスは、指定されたファイルに格納されているモジュールのバイナリ イメージをモジュールのメモリ領域に読み込み、実行できるように準備します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="d3bcd-145">指定されたメディアが既に開かれていることが前提となっています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="d3bcd-146">ファイルの読み込みには FileX システムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="d3bcd-147">FileX のアクセスを有効にするには、モジュール、モジュール ライブラリ、モジュール マネージャー、ThreadX ライブラリ (モジュール マネージャーのソースを含む) が、プロジェクトで定義されている **FX_FILEX_PRESENT** を使用してビルドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-148">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-148">Input parameters</span></span>

- <span data-ttu-id="d3bcd-149">**module_instance** モジュールのインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="d3bcd-150">**module_name** モジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="d3bcd-151">**media_ptr** 既に開かれている FileX メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="d3bcd-152">**file_name** モジュールのバイナリ ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-153">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-153">Return values</span></span>

- <span data-ttu-id="d3bcd-154">**TX_SUCCESS** (0x00) モジュールの読み込みが成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="d3bcd-155">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="d3bcd-156">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-157">**TX_NO_MEMORY** (0x10) モジュールを読み込むためのメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="d3bcd-158">**TX_NOT_DONE** (0x20) メディアが開いていないか、ファイルが見つからないか、ファイルが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="d3bcd-159">**TX_PTR_ERROR** (0x03) モジュール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="d3bcd-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 配置が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="d3bcd-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) モジュールは既に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="d3bcd-162">**TXM_MODULE_INVALID** (0xF2) | モジュール プリアンブルが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="d3bcd-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-164">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-164">Allowed from</span></span>

<span data-ttu-id="d3bcd-165">Threads</span><span class="sxs-lookup"><span data-stu-id="d3bcd-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-166">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-167">See also</span></span>

- <span data-ttu-id="d3bcd-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="d3bcd-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="d3bcd-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="d3bcd-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="d3bcd-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="d3bcd-172">モジュール データのみを読み込み、既存の場所でモジュールを実行します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="d3bcd-174">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-174">Description</span></span>

<span data-ttu-id="d3bcd-175">このサービスは、モジュールのデータ領域のみをモジュールのメモリ領域に読み込み、実行できるように準備します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="d3bcd-176">モジュール コードの実行は、インプレースで、つまり、指定された場所のモジュール プリアンブルによって指定されたアドレス オフセットから行われます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-177">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-177">Input parameters</span></span>

- <span data-ttu-id="d3bcd-178">**module_instance** モジュールのインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="d3bcd-179">**module_name** モジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="d3bcd-180">**location** モジュールのコード領域へのポインター。プリアンブルが最初になります。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-181">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-181">Return values</span></span>

- <span data-ttu-id="d3bcd-182">**TX_SUCCESS** (0x00) モジュールの読み込みが成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="d3bcd-183">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="d3bcd-184">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-185">**TX_NO_MEMORY** (0x10) モジュールを読み込むためのメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="d3bcd-186">**TX_PTR_ERROR** (0x03) ポインター、モジュール インスタンス、またはモジュール プリアンブルが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="d3bcd-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 配置が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="d3bcd-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) モジュールは既に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="d3bcd-189">**TXM_MODULE_INVALID** (0xF2) モジュール プリアンブルが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="d3bcd-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-191">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-191">Allowed from</span></span>

<span data-ttu-id="d3bcd-192">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-193">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-194">See also</span></span>

- <span data-ttu-id="d3bcd-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="d3bcd-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="d3bcd-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="d3bcd-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="d3bcd-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="d3bcd-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="d3bcd-199">モジュール マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="d3bcd-201">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-201">Description</span></span>

<span data-ttu-id="d3bcd-202">このサービスは、モジュール マネージャーの内部リソース (モジュールの読み込みに使用されるメモリ領域など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-203">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-203">Input parameters</span></span>

- <span data-ttu-id="d3bcd-204">**module_memory_start** モジュール メモリの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="d3bcd-205">**module_memory_size** モジュール メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-206">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-206">Return values</span></span>

- <span data-ttu-id="d3bcd-207">**TX_SUCCESS** (0x00) 初期化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="d3bcd-208">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-209">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-209">Allowed from</span></span>

<span data-ttu-id="d3bcd-210">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-211">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-212">See also</span></span>

- <span data-ttu-id="d3bcd-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="d3bcd-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="d3bcd-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="d3bcd-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="d3bcd-215">メモリ管理ハードウェアを初期化します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-216">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="d3bcd-217">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-217">Description</span></span>

<span data-ttu-id="d3bcd-218">このサービスは MMU を初期化します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-219">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-219">Input parameters</span></span>

<span data-ttu-id="d3bcd-220">なし</span><span class="sxs-lookup"><span data-stu-id="d3bcd-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-221">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-221">Return values</span></span>

- <span data-ttu-id="d3bcd-222">**TX_SUCCESS** (0x00) 初期化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="d3bcd-223">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-224">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-224">Allowed from</span></span>

<span data-ttu-id="d3bcd-225">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-226">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="d3bcd-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="d3bcd-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="d3bcd-228">モジュールで許可されるスレッドの最大優先度を設定します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-229">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="d3bcd-230">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-230">Description</span></span>

<span data-ttu-id="d3bcd-231">このサービスは、モジュールで許可されるスレッドの最大優先度を設定します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-232">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-232">Input parameters</span></span>

- <span data-ttu-id="d3bcd-233">**module_instance** モジュールのインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="d3bcd-234">**priority** スレッドの最大優先度。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-235">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-235">Return values</span></span>

- <span data-ttu-id="d3bcd-236">**TX_SUCCESS** (0x00) 初期化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="d3bcd-237">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-238">**TX_PTR_ERROR** (0x03) モジュール インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="d3bcd-239">**TX_START_ERROR** (0x10) モジュールが読み込み済み状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-240">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-240">Allowed from</span></span>

<span data-ttu-id="d3bcd-241">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-242">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="d3bcd-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="d3bcd-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="d3bcd-244">メモリ エラー発生時にアプリケーション コールバックを登録します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-245">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="d3bcd-246">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-246">Description</span></span>

<span data-ttu-id="d3bcd-247">このサービスは、指定されたアプリケーションのメモリ エラー通知コールバック関数をモジュール マネージャーに登録します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="d3bcd-248">メモリ エラーが発生すると、この関数が、問題のあるスレッドと問題のあるスレッドに対応するモジュール インスタンスへのポインターを指定して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="d3bcd-249">モジュール マネージャーの処理では、問題のあるスレッドが自動的に終了しますが、モジュール内の他のスレッドは何も行われないまま放置されます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="d3bcd-250">メモリ エラーに関連付けられているモジュールをどう処理するかは、アプリケーションによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="d3bcd-251">メモリ エラー自体に関する具体的な情報については、内部の **_txm_module_manager_memory_fault_info** 構造体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="d3bcd-252">メモリ エラー通知コールバック関数は、メモリ エラーの例外から直接実行されるため、割り込みサービス ルーチンから許可されている ThreadX API のみを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="d3bcd-253">したがって、問題のあるモジュールを停止してアンロードするには、アプリケーション通知コールバックによってアプリケーション タスクにシグナルが送信される必要があります。これにより、モジュールを停止しアンロードできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-254">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-254">Input parameters</span></span>

- <span data-ttu-id="d3bcd-255">**notify_function** アプリケーションのメモリ エラー通知コールバックへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="d3bcd-256">NULL 値を指定すると、メモリ エラー通知が無効になります。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-257">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-257">Return values</span></span>

- <span data-ttu-id="d3bcd-258">**TX_SUCCESS** (0x00) 通知関数の登録が成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-259">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-259">Allowed from</span></span>

<span data-ttu-id="d3bcd-260">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-261">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="d3bcd-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="d3bcd-263">メモリからモジュールを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-264">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="d3bcd-265">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-265">Description</span></span>

<span data-ttu-id="d3bcd-266">このサービスは、モジュールのコードおよびデータ領域を ***txm_module_manager_initialize*** によって設定されたモジュール メモリ領域に読み込み、実行できるように準備します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-267">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-267">Input parameters</span></span>

- <span data-ttu-id="d3bcd-268">**module_instance** モジュールのインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="d3bcd-269">**module_name** モジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="d3bcd-270">**location** モジュールのコード領域へのポインター。プリアンブルが最初になります。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-271">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-271">Return values</span></span>

- <span data-ttu-id="d3bcd-272">**TX_SUCCESS** (0x00) モジュールの読み込みが成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="d3bcd-273">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="d3bcd-274">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-275">**TX_NO_MEMORY** (0x10) モジュールを読み込むためのメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="d3bcd-276">**TX_PTR_ERROR** (0x03) ポインター、モジュール インスタンス、またはモジュール プリアンブルが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="d3bcd-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 配置が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="d3bcd-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) モジュールは既に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="d3bcd-279">**TXM_MODULE_INVALID** (0xF2) モジュール プリアンブルが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="d3bcd-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-281">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-281">Allowed from</span></span>

<span data-ttu-id="d3bcd-282">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-283">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-284">See also</span></span>

- <span data-ttu-id="d3bcd-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="d3bcd-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="d3bcd-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="d3bcd-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="d3bcd-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="d3bcd-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="d3bcd-289">モジュールのオブジェクト プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-290">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="d3bcd-291">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-291">Description</span></span>

<span data-ttu-id="d3bcd-292">このサービスは、モジュールが ThreadX/NetX オブジェクトの割り当て元とすることができるモジュール マネージャーのオブジェクト メモリ プールを作成します。これにより、システム オブジェクトがモジュールのメモリ領域に入らないようにします。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-293">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-293">Input parameters</span></span>

- <span data-ttu-id="d3bcd-294">**pool_memory_start** オブジェクト メモリの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="d3bcd-295">**pool_memory_size** オブジェクト メモリ プールのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-296">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-296">Return values</span></span>

- <span data-ttu-id="d3bcd-297">**TX_SUCCESS** (0x00) 初期化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="d3bcd-298">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-299">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-299">Allowed from</span></span>

<span data-ttu-id="d3bcd-300">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-301">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-302">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-302">See also</span></span>

- <span data-ttu-id="d3bcd-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="d3bcd-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="d3bcd-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="d3bcd-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="d3bcd-305">モジュールのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-306">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="d3bcd-307">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-307">Description</span></span>

<span data-ttu-id="d3bcd-308">このサービスは、モジュールのプロパティ (プリアンブルで指定) を返します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-309">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-309">Input parameters</span></span>

- <span data-ttu-id="d3bcd-310">**module_instance** モジュール インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="d3bcd-311">**module_properties_ptr** モジュールのプロパティの宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-312">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-312">Return values</span></span>

- <span data-ttu-id="d3bcd-313">**TX_SUCCESS** (0x00) 初期化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="d3bcd-314">**TX_PTR_ERROR** (0x03) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="d3bcd-315">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-316">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-316">Allowed from</span></span>

<span data-ttu-id="d3bcd-317">Threads</span><span class="sxs-lookup"><span data-stu-id="d3bcd-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-318">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="d3bcd-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="d3bcd-319">txm_module_manager_start</span></span>

<span data-ttu-id="d3bcd-320">モジュールの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-321">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="d3bcd-322">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-322">Description</span></span>

<span data-ttu-id="d3bcd-323">このサービスは、指定された読み込み済みモジュールの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-324">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-324">Input parameters</span></span>

- <span data-ttu-id="d3bcd-325">**module_instance** 前もって読み込まれているモジュール インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-326">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-326">Return values</span></span>

- <span data-ttu-id="d3bcd-327">**TX_SUCCESS** (0x00) モジュールの開始が成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="d3bcd-328">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="d3bcd-329">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-330">**TX_PTR_ERROR** (0x03) ポインターまたはモジュール インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="d3bcd-331">**TX_START_ERROR** (0x10) モジュールは既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-332">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-332">Allowed from</span></span>

<span data-ttu-id="d3bcd-333">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-334">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-335">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-335">See also</span></span>

- <span data-ttu-id="d3bcd-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="d3bcd-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="d3bcd-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="d3bcd-337">txm_module_manager_stop</span></span>

<span data-ttu-id="d3bcd-338">モジュールの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-339">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="d3bcd-340">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-340">Description</span></span>

<span data-ttu-id="d3bcd-341">このサービスは、前もって読み込まれ、開始されたモジュールを停止します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="d3bcd-342">モジュールの停止では、モジュールのオプションの停止スレッドの実行、すべてのスレッドの終了、モジュールに関連付けられたすべてのリソースの削除が行われます。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-343">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-343">Input parameters</span></span>

- <span data-ttu-id="d3bcd-344">**module_instance** モジュール インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-345">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-345">Return values</span></span>

- <span data-ttu-id="d3bcd-346">**TX_SUCCESS** (0x00) モジュールの停止が成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="d3bcd-347">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="d3bcd-348">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-349">**TX_PTR_ERROR** (0x03) ポインターまたはモジュール インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="d3bcd-350">**TX_START_ERROR** (0x10) モジュールが開始されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-351">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-351">Allowed from</span></span>

<span data-ttu-id="d3bcd-352">Threads</span><span class="sxs-lookup"><span data-stu-id="d3bcd-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-353">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-354">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-354">See also</span></span>

- <span data-ttu-id="d3bcd-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="d3bcd-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="d3bcd-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="d3bcd-356">txm_module_manager_unload</span></span>

<span data-ttu-id="d3bcd-357">モジュールをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bcd-358">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bcd-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="d3bcd-359">説明</span><span class="sxs-lookup"><span data-stu-id="d3bcd-359">Description</span></span>

<span data-ttu-id="d3bcd-360">このサービスは、前もって読み込まれ、停止されたモジュールをアンロードし、関連付けられているすべてのモジュール メモリ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d3bcd-361">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bcd-361">Input parameters</span></span>

- <span data-ttu-id="d3bcd-362">**module_instance** モジュールのインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bcd-363">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bcd-363">Return values</span></span>

- <span data-ttu-id="d3bcd-364">**TX_SUCCESS** (0x00) モジュールのアンロードが成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="d3bcd-365">**TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="d3bcd-366">**TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="d3bcd-367">**TX_NOT_DONE** (0x20) モジュールが無効であるか、モジュールが停止していません。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="d3bcd-368">**TX_PTR_ERROR** (0x03) ポインターまたはモジュール インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bcd-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d3bcd-369">許可元</span><span class="sxs-lookup"><span data-stu-id="d3bcd-369">Allowed from</span></span>

<span data-ttu-id="d3bcd-370">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="d3bcd-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="d3bcd-371">例</span><span class="sxs-lookup"><span data-stu-id="d3bcd-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="d3bcd-372">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3bcd-372">See also</span></span>

- <span data-ttu-id="d3bcd-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="d3bcd-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="d3bcd-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="d3bcd-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="d3bcd-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="d3bcd-376">txm_module_manager_stop</span></span>
