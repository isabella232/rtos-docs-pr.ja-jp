---
title: 第 4 章 - Azure RTOS LevelX NAND API
description: アプリケーションで使用できる Azure RTOS LevelX NAND API。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811879"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="7edb6-103">第 4 章 - Azure RTOS LevelX NAND API</span><span class="sxs-lookup"><span data-stu-id="7edb6-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="7edb6-104">アプリケーションで使用できる Azure RTOS LevelX NAND API は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7edb6-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="7edb6-105">***lx_nand_flash_close** _: _NAND フラッシュ インスタンスを閉じる*</span><span class="sxs-lookup"><span data-stu-id="7edb6-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="7edb6-106">***lx_nand_flash_defragment** _: _NAND フラッシュ インスタンスをデフラグする*</span><span class="sxs-lookup"><span data-stu-id="7edb6-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="7edb6-107">***lx_nand_flash_extended_cache_enable** _: _拡張 NAND キャッシュを有効または無効にする*</span><span class="sxs-lookup"><span data-stu-id="7edb6-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="7edb6-108">***lx_nand_flash_initialize** _: _NAND フラッシュのサポートを初期化する*</span><span class="sxs-lookup"><span data-stu-id="7edb6-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="7edb6-109">***lx_nand_flash_open** _: _NAND フラッシュ インスタンスを開く*</span><span class="sxs-lookup"><span data-stu-id="7edb6-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="7edb6-110">***lx_nand_flash_page_ecc_check** _: _訂正ありの ECC エラーがないかどうかページを確認する*</span><span class="sxs-lookup"><span data-stu-id="7edb6-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="7edb6-111">***lx_nand_flash_page_ecc_compute** _: _ページの ECC を計算する*</span><span class="sxs-lookup"><span data-stu-id="7edb6-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="7edb6-112">***lx_nand_flash_partial_defragment** _: _NAND フラッシュ インスタンスの部分的なデフラグ*</span><span class="sxs-lookup"><span data-stu-id="7edb6-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="7edb6-113">***lx_nand_flash_sector_read** _: _NAND フラッシュ セクターを読み取る*</span><span class="sxs-lookup"><span data-stu-id="7edb6-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="7edb6-114">***lx_nand_flash_sector_release** _: _NAND フラッシュ セクターを解放する*</span><span class="sxs-lookup"><span data-stu-id="7edb6-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="7edb6-115">***lx_nand_flash_sector_write** _: _NAND フラッシュ セクターを書き込む*</span><span class="sxs-lookup"><span data-stu-id="7edb6-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="7edb6-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-116">lx_nand_flash_close</span></span>

<span data-ttu-id="7edb6-117">NAND フラッシュ インスタンスを閉じる</span><span class="sxs-lookup"><span data-stu-id="7edb6-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-118">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="7edb6-119">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-119">Description</span></span>

<span data-ttu-id="7edb6-120">このサービスでは、以前に開かれた NAND フラッシュ インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-121">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-121">Input Parameters</span></span>

- <span data-ttu-id="7edb6-122">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-123">Return Values</span></span>

- <span data-ttu-id="7edb6-124">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-125">**LX_ERROR**: (0x01) フラッシュ インスタンスを閉じているときにエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-126">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-126">Allowed From</span></span>

<span data-ttu-id="7edb6-127">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-128">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-129">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-129">See Also</span></span>

- <span data-ttu-id="7edb6-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="7edb6-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="7edb6-141">NAND フラッシュ インスタンスをデフラグする</span><span class="sxs-lookup"><span data-stu-id="7edb6-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-142">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="7edb6-143">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-143">Description</span></span>

<span data-ttu-id="7edb6-144">このサービスでは、以前に開かれた NAND フラッシュ インスタンスをデフラグします。</span><span class="sxs-lookup"><span data-stu-id="7edb6-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="7edb6-145">デフラグ プロセスでは、空きページと空きブロックの数を最大化します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-146">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-146">Input Parameters</span></span>

- <span data-ttu-id="7edb6-147">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-148">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-148">Return Values</span></span>

- <span data-ttu-id="7edb6-149">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-150">**LX_ERROR**: (0x01) フラッシュ インスタンスのデフラグ中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-151">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-151">Allowed From</span></span>

<span data-ttu-id="7edb6-152">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-153">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-154">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-154">See Also</span></span>

- <span data-ttu-id="7edb6-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="7edb6-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="7edb6-166">拡張 NAND キャッシュを有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="7edb6-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-167">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="7edb6-168">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-168">Description</span></span>

<span data-ttu-id="7edb6-169">このサービスでは、アプリケーションによって指定されたメモリを使用して、RAM 内にキャッシュ レイヤーを実装します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="7edb6-170">完全なキャッシュ操作に必要なメモリの合計量は、次のように計算できます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="7edb6-171">指定されたメモリに完全な NAND キャッシュを収容するための十分な大きさがない場合、このルーチンでは、指定されたメモリに基づいて、できるだけ大きな NAND フラッシュ キャッシュを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7edb6-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="7edb6-172">指定されたメモリ アドレスが NULL である場合、NAND キャッシュは無効になります。</span><span class="sxs-lookup"><span data-stu-id="7edb6-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="7edb6-173">そのため、NAND キャッシュは一時的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-174">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-174">Input Parameters</span></span>

- <span data-ttu-id="7edb6-175">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="7edb6-176">**memory**: ULONG アクセス用にアラインされたキャッシュ メモリの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="7edb6-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="7edb6-177">LX_NULL の値を指定すると、キャッシュは無効になります。</span><span class="sxs-lookup"><span data-stu-id="7edb6-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="7edb6-178">**size**: 指定されたメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="7edb6-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-179">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-179">Return Values</span></span>

- <span data-ttu-id="7edb6-180">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-181">**LX_ERROR**: (0x01) NAND キャッシュの 1 つの要素に十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="7edb6-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-182">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-182">Allowed From</span></span>

<span data-ttu-id="7edb6-183">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-184">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-185">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-185">See Also</span></span>

- <span data-ttu-id="7edb6-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="7edb6-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="7edb6-197">NAND フラッシュのサポートを初期化する</span><span class="sxs-lookup"><span data-stu-id="7edb6-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-198">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="7edb6-199">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-199">Description</span></span>

<span data-ttu-id="7edb6-200">このサービスでは、LevelX NAND フラッシュのサポートを初期化します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="7edb6-201">これは、他のどの LevelX NAND API よりも前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7edb6-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-202">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-202">Input Parameters</span></span>

- <span data-ttu-id="7edb6-203">**なし**</span><span class="sxs-lookup"><span data-stu-id="7edb6-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-204">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-204">Return Values</span></span>

- <span data-ttu-id="7edb6-205">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-206">**LX_ERROR**: (0x01) NAND フラッシュのサポートの初期化中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-207">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-207">Allowed From</span></span>

<span data-ttu-id="7edb6-208">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="7edb6-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-209">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-210">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-210">See Also</span></span>

- <span data-ttu-id="7edb6-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="7edb6-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-221">lx_nand_flash_open</span></span>

<span data-ttu-id="7edb6-222">NAND フラッシュ インスタンスを開く</span><span class="sxs-lookup"><span data-stu-id="7edb6-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-223">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="7edb6-224">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-224">Description</span></span>

<span data-ttu-id="7edb6-225">このサービスでは、指定された NAND フラッシュ コントロール ブロックとドライバー初期化関数を使用して NAND フラッシュ インスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="7edb6-226">このドライバー初期化関数は、この NAND フラッシュ インスタンスに関連付けられている NAND ハードウェアのブロックまたはページの読み取り、書き込み、消去を行うためのさまざまな関数ポインターのインストールを担当することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-227">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-227">Input Parameters</span></span>

- <span data-ttu-id="7edb6-228">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-229">**name**: NAND フラッシュ インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="7edb6-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="7edb6-230">**nand_driver_initialize**: NAND フラッシュ ドライバー初期化関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="7edb6-231">NAND フラッシュ ドライバーの処理の詳細については、このガイドの第 3 章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-232">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-232">Return Values</span></span>

- <span data-ttu-id="7edb6-233">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-234">**LX_ERROR**: (0x01) NAND フラッシュ インスタンスを開いているときにエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="7edb6-235">**LX_NO_MEMORY**: (0x08) ドライバーによって、1 ページを RAM に読み取るためのバッファーが提供されませんでした。</span><span class="sxs-lookup"><span data-stu-id="7edb6-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-236">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-236">Allowed From</span></span>

<span data-ttu-id="7edb6-237">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-238">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-239">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-239">See Also</span></span>

- <span data-ttu-id="7edb6-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="7edb6-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="7edb6-251">訂正ありの ECC エラーがないかどうかページを確認する</span><span class="sxs-lookup"><span data-stu-id="7edb6-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-252">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="7edb6-253">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-253">Description</span></span>

<span data-ttu-id="7edb6-254">このサービスでは、指定された NAND ページ バッファーの整合性を指定された ECC で確認します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="7edb6-255">ページ サイズ (NAND フラッシュ インスタンスのポインターで定義されます) は 256 バイトの倍数であると見なされ、指定された ECC コードでは、ページの 256 バイトの各部分の中の 1 ビット エラーを訂正できます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-256">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-256">Input Parameters</span></span>

- <span data-ttu-id="7edb6-257">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-258">**page_buffer**: NAND フラッシュ ページ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="7edb6-259">**ecc_buffer**: NAND フラッシュ ページの ECC へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="7edb6-260">ページの 256 バイトの部分ごとに 3 つの ECC バイトが存在することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-261">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-261">Return Values</span></span>

- <span data-ttu-id="7edb6-262">**LX_SUCCESS**: (0x00) NAND ページにはエラーがありません。</span><span class="sxs-lookup"><span data-stu-id="7edb6-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="7edb6-263">**LX_NAND_ERROR_CORRECTED**: (0x06) NAND ページで 1 ビット エラーが 1 つ以上訂正されました。訂正はページ バッファー内にあります。</span><span class="sxs-lookup"><span data-stu-id="7edb6-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="7edb6-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) NAND ページで訂正するエラーが多すぎます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-265">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-265">Allowed From</span></span>

<span data-ttu-id="7edb6-266">LevelX ドライバー</span><span class="sxs-lookup"><span data-stu-id="7edb6-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-267">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-268">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-268">See Also</span></span>

- <span data-ttu-id="7edb6-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="7edb6-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="7edb6-280">ページの ECC を計算する</span><span class="sxs-lookup"><span data-stu-id="7edb6-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-281">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="7edb6-282">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-282">Description</span></span>

<span data-ttu-id="7edb6-283">このサービスでは、指定された NAND ページ バッファーの ECC を計算し、その ECC を指定された ECC バッファーで返します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="7edb6-284">ページ サイズは 256 バイトの倍数であると見なされます (NAND フラッシュ インスタンスのポインターで定義されます)。</span><span class="sxs-lookup"><span data-stu-id="7edb6-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="7edb6-285">ECC コードは、ページの整合性を、そのページが後で読み取られたときに確認するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-286">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-286">Input Parameters</span></span>

- <span data-ttu-id="7edb6-287">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-288">**page_buffer**: NAND フラッシュ ページ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="7edb6-289">**ecc_buffer**: NAND フラッシュ ページの ECC の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="7edb6-290">ページの 256 バイトの部分ごとに 3 バイトの ECC ストレージが必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="7edb6-291">たとえば、2048 バイトのページでは ECC 用に 24 バイトが必要になります。</span><span class="sxs-lookup"><span data-stu-id="7edb6-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-292">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-292">Return Values</span></span>

- <span data-ttu-id="7edb6-293">**LX_SUCCESS**: (0x00) ECC が正常に計算されました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="7edb6-294">**LX_ERROR**: (0x01) ECC の計算中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-295">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-295">Allowed From</span></span>

<span data-ttu-id="7edb6-296">LevelX ドライバー</span><span class="sxs-lookup"><span data-stu-id="7edb6-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-297">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-298">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-298">See Also</span></span>

- <span data-ttu-id="7edb6-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="7edb6-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="7edb6-310">NAND フラッシュ インスタンスの部分的なデフラグ</span><span class="sxs-lookup"><span data-stu-id="7edb6-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-311">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="7edb6-312">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-312">Description</span></span>

<span data-ttu-id="7edb6-313">このサービスでは、以前に開かれた NAND フラッシュ インスタンスを、指定された最大ブロック数までデフラグします。</span><span class="sxs-lookup"><span data-stu-id="7edb6-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="7edb6-314">デフラグ プロセスでは、空きページと空きブロックの数を最大化します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-315">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-315">Input Parameters</span></span>

- <span data-ttu-id="7edb6-316">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-317">**max_blocks**: 最大ブロック数。</span><span class="sxs-lookup"><span data-stu-id="7edb6-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-318">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-318">Return Values</span></span>

- <span data-ttu-id="7edb6-319">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-320">**LX_ERROR**: (0x01) フラッシュ インスタンスのデフラグ中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-321">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-321">Allowed From</span></span>

<span data-ttu-id="7edb6-322">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-323">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-324">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-324">See Also</span></span>

- <span data-ttu-id="7edb6-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="7edb6-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="7edb6-336">NAND フラッシュ セクターを読み取る</span><span class="sxs-lookup"><span data-stu-id="7edb6-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-337">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="7edb6-338">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-338">Description</span></span>

<span data-ttu-id="7edb6-339">このサービスでは、NAND フラッシュ インスタンスから論理セクターを読み取り、成功した場合は、その内容を指定されたバッファーで返します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="7edb6-340">NAND セクターのサイズは常に、基になる NAND ハードウェアのページ サイズであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-341">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-341">Input Parameters</span></span>

- <span data-ttu-id="7edb6-342">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-343">**logical_sector**: 読み取る論理セクター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="7edb6-344">**buffer**: 論理セクターの内容の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="7edb6-345">このバッファーは NAND フラッシュ ページのサイズであり、ULONG アクセス用にアラインされていると見なされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-346">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-346">Return Values</span></span>

- <span data-ttu-id="7edb6-347">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-348">**LX_ERROR**: (0x01) NAND フラッシュ セクターの読み取り中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-349">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-349">Allowed From</span></span>

<span data-ttu-id="7edb6-350">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-351">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-352">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-352">See Also</span></span>

- <span data-ttu-id="7edb6-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="7edb6-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="7edb6-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="7edb6-364">NAND フラッシュ セクターを解放する</span><span class="sxs-lookup"><span data-stu-id="7edb6-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-365">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="7edb6-366">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-366">Description</span></span>

<span data-ttu-id="7edb6-367">このサービスでは、NAND フラッシュ インスタンス内の論理セクターのマッピングを解放します。</span><span class="sxs-lookup"><span data-stu-id="7edb6-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="7edb6-368">使用されていない論理セクターを解放すると、LevelX のウェア レベリングがより効率的になります。</span><span class="sxs-lookup"><span data-stu-id="7edb6-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-369">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-369">Input Parameters</span></span>

- <span data-ttu-id="7edb6-370">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-371">**logical_sector**: 解放する論理セクター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-372">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-372">Return Values</span></span>

- <span data-ttu-id="7edb6-373">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-374">**LX_ERROR**: (0x01) NAND フラッシュ セクターの書き込み中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-375">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-375">Allowed From</span></span>

<span data-ttu-id="7edb6-376">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-377">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-378">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-378">See Also</span></span>

- <span data-ttu-id="7edb6-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="7edb6-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="7edb6-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="7edb6-390">NAND フラッシュ セクターを書き込む</span><span class="sxs-lookup"><span data-stu-id="7edb6-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="7edb6-391">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="7edb6-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="7edb6-392">説明</span><span class="sxs-lookup"><span data-stu-id="7edb6-392">Description</span></span>

<span data-ttu-id="7edb6-393">このサービスでは、NAND フラッシュ インスタンス内の指定された論理セクターを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7edb6-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="7edb6-394">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="7edb6-394">Input Parameters</span></span>

- <span data-ttu-id="7edb6-395">**nand_flash**: NAND フラッシュ インスタンスのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="7edb6-396">**logical_sector**: 書き込む論理セクター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="7edb6-397">**buffer**: 論理セクターの内容へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7edb6-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="7edb6-398">このバッファーは NAND フラッシュ ページのサイズであり、ULONG アクセス用にアラインされていると見なされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7edb6-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="7edb6-399">戻り値</span><span class="sxs-lookup"><span data-stu-id="7edb6-399">Return Values</span></span>

- <span data-ttu-id="7edb6-400">**LX_SUCCESS**: (0x00) 要求が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="7edb6-401">**LX_NO_SECTORS**: (0x02) 書き込みを実行するために使用できる空きセクターがありません。</span><span class="sxs-lookup"><span data-stu-id="7edb6-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="7edb6-402">**LX_ERROR**: (0x01) NAND フラッシュ セクターの解放中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7edb6-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7edb6-403">許可元</span><span class="sxs-lookup"><span data-stu-id="7edb6-403">Allowed From</span></span>

<span data-ttu-id="7edb6-404">Threads</span><span class="sxs-lookup"><span data-stu-id="7edb6-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7edb6-405">例</span><span class="sxs-lookup"><span data-stu-id="7edb6-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="7edb6-406">参照</span><span class="sxs-lookup"><span data-stu-id="7edb6-406">See Also</span></span>

- <span data-ttu-id="7edb6-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="7edb6-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="7edb6-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="7edb6-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="7edb6-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="7edb6-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="7edb6-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="7edb6-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="7edb6-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="7edb6-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="7edb6-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="7edb6-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="7edb6-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="7edb6-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="7edb6-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="7edb6-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="7edb6-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="7edb6-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="7edb6-416">lx_nand_flash_sector_release</span></span>
