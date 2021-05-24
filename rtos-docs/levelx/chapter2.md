---
title: 第 2 章 - Azure RTOS LevelX のインストールと使用
description: LevelX のインストールと使用は簡単で、この章の次のセクションで説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223317"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="a7779-103">第 2 章 - Azure RTOS LevelX のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="a7779-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="a7779-104">Azure RTOS LevelX のインストールと使用は簡単で、この章の次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="a7779-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="a7779-105">Distribution</span><span class="sxs-lookup"><span data-stu-id="a7779-105">Distribution</span></span>

<span data-ttu-id="a7779-106">LevelX は ANSI C で配布されます。各関数は、それぞれ個別の C ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7779-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="a7779-107">LevelX の配布に含まれるファイルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7779-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="a7779-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="a7779-108">lx_api.h</span></span>
- <span data-ttu-id="a7779-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="a7779-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="a7779-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="a7779-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="a7779-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="a7779-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="a7779-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="a7779-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="a7779-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="a7779-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="a7779-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="a7779-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="a7779-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="a7779-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="a7779-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="a7779-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="a7779-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="a7779-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="a7779-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="a7779-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="a7779-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="a7779-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="a7779-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="a7779-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="a7779-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="a7779-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="a7779-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="a7779-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="a7779-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="a7779-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="a7779-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="a7779-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="a7779-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="a7779-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="a7779-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="a7779-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="a7779-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="a7779-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="a7779-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="a7779-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="a7779-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="a7779-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="a7779-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="a7779-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="a7779-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="a7779-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="a7779-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="a7779-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="a7779-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="a7779-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="a7779-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="a7779-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="a7779-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="a7779-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="a7779-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="a7779-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="a7779-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="a7779-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="a7779-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="a7779-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="a7779-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="a7779-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="a7779-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="a7779-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="a7779-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="a7779-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="a7779-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="a7779-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="a7779-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="a7779-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="a7779-144">次に示すように、LevelX の NAND と NOR インスタンスの両方に対してシミュレーターと FileX ドライバーのサンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="a7779-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="a7779-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="a7779-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="a7779-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="a7779-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="a7779-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="a7779-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="a7779-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="a7779-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="a7779-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="a7779-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="a7779-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="a7779-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="a7779-151">NAND フラッシュのみが必要な場合は、LevelX NAND フラッシュ ファイル (***lx_nand_\*.c***) のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="a7779-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="a7779-152">同様に、NOR フラッシュのみが必要な場合は、NOR フラッシュ ファイル (\*\*_lx_nor_\_.c\*\*\*) のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="a7779-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="a7779-153">構成オプション</span><span class="sxs-lookup"><span data-stu-id="a7779-153">Configuration Options</span></span>

<span data-ttu-id="a7779-154">次に説明する条件定義を使用して、コンパイル時に LevelX を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a7779-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="a7779-155">オプションを使用するには、必要な定義を各 LevelX ソースのコンパイルに追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="a7779-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="a7779-156">**LX_DIRECT_READ**: このオプションを定義すると、NOR メモリの直接読み取りが優先されて、NOR フラッシュ ドライバーの読み取りルーチンがバイパスされるため、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="a7779-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="a7779-157">**LX_FREE_SECTOR_DATA_VERIFY**: これが定義されると、LevelX NOR インスタンスのオープン ロジックによって、空き NOR セクターがすべて 1 かどうかが検証されます。</span><span class="sxs-lookup"><span data-stu-id="a7779-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="a7779-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: 既定では、この値は 16 で、論理セクター マッピングのキャッシュ サイズが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a7779-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="a7779-159">大きい値を指定すると、パフォーマンスは向上しますが、メモリが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a7779-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="a7779-160">最小サイズは 8 で、すべての値は 2 の累乗でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a7779-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="a7779-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: これが定義されていると、キャッシュ ミスがないように直接マッピング キャッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7779-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="a7779-162">また、LX_NAND_SECTOR_MAPPING_CACHE_SIZE でフラッシュ デバイス内の合計ページ数を正確に表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7779-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="a7779-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: これが定義されていると、拡張された NOR キャッシュが無効になります。</span><span class="sxs-lookup"><span data-stu-id="a7779-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="a7779-164">**LX_NOR_EXTENDED_CACHE_SIZE**: この値の既定値は 8 です。これは、NOR インスタンスにキャッシュできる最大セクター数が 8 であることを表します。</span><span class="sxs-lookup"><span data-stu-id="a7779-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="a7779-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: 既定では、この値は 16 で、論理セクター マッピングのキャッシュ サイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="a7779-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="a7779-166">大きい値を指定すると、パフォーマンスは向上しますが、メモリが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a7779-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="a7779-167">最小サイズは 8 で、すべての値は 2 の累乗でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a7779-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="a7779-168">**LX_THREAD_SAFE_ENABLE**: これが定義されていると、API 全体で ThreadX ミューテックス オブジェクトを使用して LevelX がスレッドセーフになります。</span><span class="sxs-lookup"><span data-stu-id="a7779-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="a7779-169">**LX_STANDALONE_ENABLE**: 定義されている場合、LevelX をスタンドアロン モード (Azure RTOS なし) で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a7779-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="a7779-170">既定では、このシンボルは定義されません。</span><span class="sxs-lookup"><span data-stu-id="a7779-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7779-171">LevelX をスタンドアロン モードで使用する場合 (**LX_STANDALONE_ENABLE** を定義する必要があります)、ThreadX ファイルまたはライブラリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a7779-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="a7779-172">このモードでは、LevelX スレッドセーフ機能が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a7779-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="a7779-173">LevelX の使用</span><span class="sxs-lookup"><span data-stu-id="a7779-173">Using LevelX</span></span>

<span data-ttu-id="a7779-174">LevelX を単独で、または FileX と共に使用するには、LevelX API を参照するコードにファイル \***lx_api.h** _ を含めます。</span><span class="sxs-lookup"><span data-stu-id="a7779-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="a7779-175">また、LevelX オブジェクト コードがリンク時に使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7779-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="a7779-176">LevelX を使用する方法の例については、ファイル _*_demo_filex_nand_flash.c_*_ と _ *_demo_filex_nor_flash_*\* を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a7779-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
