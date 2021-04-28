---
title: チャプター 6 - Azure RTOS LevelX NOR API
description: アプリケーションで使用できる Azure RTOS LevelX NOR API。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811867"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="ad3cf-103">チャプター 6 - Azure RTOS LevelX NOR API</span><span class="sxs-lookup"><span data-stu-id="ad3cf-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="ad3cf-104">アプリケーションで使用できる Azure RTOS LevelX NOR API の関数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="ad3cf-105">***lx_nor_flash_close** _: NOR フラッシュ インスタンスを閉じる*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="ad3cf-106">***lx_nor_flash_defragment** _: NOR フラッシュ インスタンスのデフラグを行う*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="ad3cf-107">***lx_nor_flash_extended_cache_enable** _: 拡張 NOR キャッシュを有効化/無効化する*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="ad3cf-108">***lx_nor_flash_initialize** _: NOR フラッシュのサポートを初期化する*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="ad3cf-109">***lx_nor_flash_open** _: NOR フラッシュ インスタンスを開く*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="ad3cf-110">***lx_nor_flash_partial_defragment** _: NOR フラッシュ インスタンスの部分的なデフラグ*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="ad3cf-111">***lx_nor_flash_sector_read** _: NOR フラッシュ セクタを読み出す*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="ad3cf-112">***lx_nor_flash_sector_release** _: NOR フラッシュ セクタを開放する*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="ad3cf-113">***lx_nor_flash_sector_write** _: NOR フラッシュ セクタに書き込む*</span><span class="sxs-lookup"><span data-stu-id="ad3cf-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="ad3cf-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-114">lx_nor_flash_close</span></span>

<span data-ttu-id="ad3cf-115">NOR フラッシュ インスタンスを閉じる</span><span class="sxs-lookup"><span data-stu-id="ad3cf-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-116">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="ad3cf-117">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-117">Description</span></span>

<span data-ttu-id="ad3cf-118">このサービスでは、開いている NOR フラッシュ インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-119">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-119">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-120">*nor_flash*: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-121">Return Values</span></span>

- <span data-ttu-id="ad3cf-122">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-123">**LX_ERROR**: (0x01) フラッシュ インスタンスを閉じる際のエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-124">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-124">Allowed From</span></span>

<span data-ttu-id="ad3cf-125">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-126">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-127">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-127">See Also</span></span>

- <span data-ttu-id="ad3cf-128">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-129">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-130">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-131">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-132">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-133">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-134">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-135">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="ad3cf-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="ad3cf-137">NOR フラッシュ インスタンスのデフラグを行う</span><span class="sxs-lookup"><span data-stu-id="ad3cf-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-138">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="ad3cf-139">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-139">Description</span></span>

<span data-ttu-id="ad3cf-140">このサービスでは、開いている NOR フラッシュ インスタンスのデフラグを行います。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="ad3cf-141">デフラグ処理では、空きセクタと空きブロックの数を最大まで増やします。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-142">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-142">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-143">*nor_flash*: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-144">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-144">Return Values</span></span>

- <span data-ttu-id="ad3cf-145">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-146">**LX_ERROR**: (0x01) フラッシュ インスタンス デフラグ時のエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-147">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-147">Allowed From</span></span>

<span data-ttu-id="ad3cf-148">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-149">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-150">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-150">See Also</span></span>

- <span data-ttu-id="ad3cf-151">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-152">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-153">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-154">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-155">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-156">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-157">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-158">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="ad3cf-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="ad3cf-160">NOR 拡張キャッシュを有効/無効にする</span><span class="sxs-lookup"><span data-stu-id="ad3cf-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-161">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="ad3cf-162">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-162">Description</span></span>

<span data-ttu-id="ad3cf-163">このサービスでは、アプリケーションにより用意されるメモリを使用して、RAM にセクタ キャッシュ レイヤーを実装します。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="ad3cf-164">用意されたメモリは 512 バイトごとに、1 つのキャッシュ可能な NOR セクタとして使用します。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="ad3cf-165">キャッシュされたセクタは、消去数、空きセクタのマップ、セクタ マッピングの情報などのブロック制御情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="ad3cf-166">データ セクタはこのキャッシュに保存されません。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-167">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-167">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-168">**nor_flash**: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="ad3cf-169">**memory**: ULONG アクセス用にアラインされた、キャッシュ メモリの開始位置。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="ad3cf-170">LX_NULL を指定するとキャッシュを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="ad3cf-171">**size**: 用意するメモリのbyte 単位のサイズ (512 byte の倍数を指定します)。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-172">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-172">Return Values</span></span>

- <span data-ttu-id="ad3cf-173">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-174">**LX_ERROR**: (0x01) 特定の NOR セクタのメモリ不足。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="ad3cf-175">**LX_DISABLED**: (0x09) 構成オプションにより NOR 拡張キャッシュが無効。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-176">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-176">Allowed From</span></span>

<span data-ttu-id="ad3cf-177">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-178">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-179">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-179">See Also</span></span>

- <span data-ttu-id="ad3cf-180">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-181">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-182">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-183">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-184">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-185">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-186">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-187">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="ad3cf-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="ad3cf-189">NOR フラッシュのサポートの初期化</span><span class="sxs-lookup"><span data-stu-id="ad3cf-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-190">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="ad3cf-191">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-191">Description</span></span>

<span data-ttu-id="ad3cf-192">このサービスでは、LevelX の NOR フラッシュのサポートを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="ad3cf-193">他のどの LevelX NOR API よりも先に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-194">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-194">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-195">**なし**</span><span class="sxs-lookup"><span data-stu-id="ad3cf-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-196">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-196">Return Values</span></span>

- <span data-ttu-id="ad3cf-197">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-198">**LX_ERROR**: (0x01) NOR フラッシュのサポートの初期化エラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-199">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-199">Allowed From</span></span>

<span data-ttu-id="ad3cf-200">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ad3cf-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-201">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-202">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-202">See Also</span></span>

- <span data-ttu-id="ad3cf-203">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-204">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-205">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-206">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-207">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-208">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-209">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-210">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="ad3cf-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-211">lx_nor_flash_open</span></span>

<span data-ttu-id="ad3cf-212">NOR フラッシュ インスタンスを開く</span><span class="sxs-lookup"><span data-stu-id="ad3cf-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-213">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="ad3cf-214">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-214">Description</span></span>

<span data-ttu-id="ad3cf-215">このサービスでは、指定された NOR フラッシュ制御ブロックとドライバー初期化関数を使用して、NOR フラッシュ インスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="ad3cf-216">この NOR フラッシュ インスタンスに関連付けられた NOR ハードウェアのブロックの読み出し、書き込み、消去を行うためのさまざまな関数ポインターのインストールは、ドライバー初期化関数で行います。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-217">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-217">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-218">*nor_flash*: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="ad3cf-219">*name*: NOR フラッシュ インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="ad3cf-220">*nor_driver_initialize*: NOR フラッシュ ドライバー初期化関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="ad3cf-221">NOR フラッシュ ドライバーの機能の詳細は、このガイドのチャプター 5 をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-222">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-222">Return Values</span></span>

- <span data-ttu-id="ad3cf-223">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-224">**LX_ERROR**: (0x01) NOR フラッシュ インスタンスを開く際のエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="ad3cf-225">**LX_NO_MEMORY**:  (0x08) セクタを RAM に読み出すためのバッファーをドライバーで用意できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-226">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-226">Allowed From</span></span>

<span data-ttu-id="ad3cf-227">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-228">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-229">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-229">See Also</span></span>

- <span data-ttu-id="ad3cf-230">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-231">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-232">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-233">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-234">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-235">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-236">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-237">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="ad3cf-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="ad3cf-239">NOR フラッシュ インスタンスの部分的なデフラグ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-240">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="ad3cf-241">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-241">Description</span></span>

<span data-ttu-id="ad3cf-242">このサービスでは、開いている NOR フラッシュ インスタンスを、最大で指定した最大ブロック数までデフラグします。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="ad3cf-243">デフラグ処理では、空きセクタと空きブロックの数を最大まで増やします。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-244">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-244">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-245">*nor_flash*: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="ad3cf-246">*max_blocks*: ブロックの最大数。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-247">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-247">Return Values</span></span>

- <span data-ttu-id="ad3cf-248">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-249">**LX_ERROR**: (0x01) フラッシュ インスタンス デフラグ時のエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-250">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-250">Allowed From</span></span>

<span data-ttu-id="ad3cf-251">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-252">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-253">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-253">See Also</span></span>

- <span data-ttu-id="ad3cf-254">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-255">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-256">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-257">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-258">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-259">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-260">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-261">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="ad3cf-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="ad3cf-263">NOR フラッシュ セクタを読み出す</span><span class="sxs-lookup"><span data-stu-id="ad3cf-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-264">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="ad3cf-265">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-265">Description</span></span>

<span data-ttu-id="ad3cf-266">このサービスでは、論理セクタを NOR フラッシュ インスタンスから読み出し、成功した場合は、用意されたバッファーにその内容を返します。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="ad3cf-267">NOR セクタのサイズは常に 512 byteです。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-268">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-268">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-269">*nor_flash* NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="ad3cf-270">*logical_sector*: 読み出す論理セクタ。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="ad3cf-271">*buffer*: 論理セクタの内容の書き込み先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="ad3cf-272">バッファーは 512 byteであり、ULONG アクセス用にアラインされていることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-273">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-273">Return Values</span></span>

- <span data-ttu-id="ad3cf-274">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-275">**LX_ERROR**: (0x01) NOR フラッシュ セクタの読み出しエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-276">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-276">Allowed From</span></span>

<span data-ttu-id="ad3cf-277">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-278">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-279">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-279">See Also</span></span>

- <span data-ttu-id="ad3cf-280">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-281">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-282">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-283">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-284">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-285">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-286">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="ad3cf-287">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="ad3cf-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="ad3cf-289">NOR フラッシュ セクタを解放する</span><span class="sxs-lookup"><span data-stu-id="ad3cf-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-290">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="ad3cf-291">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-291">Description</span></span>

<span data-ttu-id="ad3cf-292">このサービスでは、NOR フラッシュ インスタンスの論理セクタのマッピングを解放します。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="ad3cf-293">使用していない論理セクタを解放することで、LevelX のウェア レベリングを効果的に実施できます。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-294">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-294">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-295">*nor_flash*: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="ad3cf-296">*logical_sector*: 解放する論理セクタ。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-297">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-297">Return Values</span></span>

- <span data-ttu-id="ad3cf-298">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-299">**LX_ERROR**: (0x01) NOR フラッシュ セクタの書き込みエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-300">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-300">Allowed From</span></span>

<span data-ttu-id="ad3cf-301">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-302">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-303">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-303">See Also</span></span>

- <span data-ttu-id="ad3cf-304">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-305">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-306">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-307">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-308">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-309">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-310">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-311">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="ad3cf-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ad3cf-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="ad3cf-313">NOR フラッシュ セクタを書き込む</span><span class="sxs-lookup"><span data-stu-id="ad3cf-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ad3cf-314">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ad3cf-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="ad3cf-315">説明</span><span class="sxs-lookup"><span data-stu-id="ad3cf-315">Description</span></span>

<span data-ttu-id="ad3cf-316">このサービスでは、NOR フラッシュ インスタンスの指定された論理セクタを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad3cf-317">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad3cf-317">Input Parameters</span></span>

- <span data-ttu-id="ad3cf-318">*nor_flash*: NOR フラッシュ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="ad3cf-319">*logical_sector*: 書き込む論理セクタ。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="ad3cf-320">*buffer*: 論理セクタの内容へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="ad3cf-321">バッファーは、ULONG アクセス用に 512 byte でアラインされているとみなされます。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="ad3cf-322">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad3cf-322">Return Values</span></span>

- <span data-ttu-id="ad3cf-323">**LX_SUCCESS**: (0x00) 要求に成功。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ad3cf-324">**LX_NO_SECTORS**: (0x02) 書き込みに使用できる空きセクタがありません。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="ad3cf-325">**LX_ERROR**: (0x01) NOR フラッシュ セクタを解放する際のエラー。</span><span class="sxs-lookup"><span data-stu-id="ad3cf-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad3cf-326">許可元</span><span class="sxs-lookup"><span data-stu-id="ad3cf-326">Allowed From</span></span>

<span data-ttu-id="ad3cf-327">Threads</span><span class="sxs-lookup"><span data-stu-id="ad3cf-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ad3cf-328">例</span><span class="sxs-lookup"><span data-stu-id="ad3cf-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="ad3cf-329">参照</span><span class="sxs-lookup"><span data-stu-id="ad3cf-329">See Also</span></span>

- <span data-ttu-id="ad3cf-330">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="ad3cf-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="ad3cf-331">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="ad3cf-332">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ad3cf-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ad3cf-333">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ad3cf-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="ad3cf-334">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="ad3cf-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="ad3cf-335">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ad3cf-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="ad3cf-336">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ad3cf-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="ad3cf-337">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ad3cf-337">lx_nor_flash_sector_release</span></span>
