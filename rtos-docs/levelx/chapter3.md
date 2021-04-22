---
title: Azure RTOS LevelX NAND のサポート
description: 一般に、ファイル システムのような大規模なデータ ストレージでは、LevelX 内で NAND フラッシュ メモリが使用されます。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811084"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a><span data-ttu-id="ac6e1-103">第 3 章 - Azure RTOS LevelX NAND のサポート</span><span class="sxs-lookup"><span data-stu-id="ac6e1-103">Chapter 3 - Azure RTOS LevelX NAND support</span></span>

<span data-ttu-id="ac6e1-104">一般に、ファイル システムのような大規模なデータ ストレージでは、NAND フラッシュ メモリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-104">NAND flash memory is commonly utilized for large data storage, which is typical of file systems.</span></span> <span data-ttu-id="ac6e1-105">NAND メモリは "*ブロック*" で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-105">NAND memory consists of *blocks*.</span></span> <span data-ttu-id="ac6e1-106">各 NAND ブロック内には、一連の "*ページ*" があります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-106">Within each NAND block is a series of *pages*.</span></span> <span data-ttu-id="ac6e1-107">NAND ブロックは消去可能です。つまり、NAND ブロック内のすべてのページが消去されます (すべて 1 に設定されます)。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-107">NAND blocks are erasable, which means that all pages within the NAND block are erased (set to all ones).</span></span> <span data-ttu-id="ac6e1-108">各 NAND ブロック ページには、Azure RTOS LevelX でブックキーピング、不良ブロックの管理、エラーの検出に使用される一連の "*予備バイト*" があります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-108">Each NAND block page has a set of *spare bytes* that are utilized by Azure RTOS LevelX for bookkeeping, bad block management, and error detection.</span></span> <span data-ttu-id="ac6e1-109">NAND ブロック ページは、さまざまなサイズで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-109">NAND block pages are available in a variety of sizes.</span></span> <span data-ttu-id="ac6e1-110">最も一般的なページ サイズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-110">The most common page sizes are:</span></span> 

| <span data-ttu-id="ac6e1-111">**ページ サイズ**</span><span class="sxs-lookup"><span data-stu-id="ac6e1-111">**Page Size**</span></span> | <span data-ttu-id="ac6e1-112">**予備バイト**</span><span class="sxs-lookup"><span data-stu-id="ac6e1-112">**Spare Bytes**</span></span> |
| ------------- | --------------- |
| <span data-ttu-id="ac6e1-113">256</span><span class="sxs-lookup"><span data-stu-id="ac6e1-113">256</span></span>           | <span data-ttu-id="ac6e1-114">8</span><span class="sxs-lookup"><span data-stu-id="ac6e1-114">8</span></span>               |
| <span data-ttu-id="ac6e1-115">512</span><span class="sxs-lookup"><span data-stu-id="ac6e1-115">512</span></span>           | <span data-ttu-id="ac6e1-116">16</span><span class="sxs-lookup"><span data-stu-id="ac6e1-116">16</span></span>              |
| <span data-ttu-id="ac6e1-117">2048</span><span class="sxs-lookup"><span data-stu-id="ac6e1-117">2048</span></span>          | <span data-ttu-id="ac6e1-118">64</span><span class="sxs-lookup"><span data-stu-id="ac6e1-118">64</span></span>              |

<span data-ttu-id="ac6e1-119">NAND メモリは、直接アクセスされないという点で、NOR メモリとは異なります。つまり、プロセッサやメモリなどから NAND メモリを直接読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-119">NAND memory differs from NOR memory in that there is no direct access, i.e., NAND memory cannot be read directly from the processor like NOR memory.</span></span> <span data-ttu-id="ac6e1-120">制限された回数の消去後にのみ、NAND メモリに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-120">NAND memory can only be written to after an erase a limited number of times.</span></span> <span data-ttu-id="ac6e1-121">また、書き込み要求で設定されたビットがクリアされる場合に、無制限の回数書き込むことができるという点でも NOR メモリと異なります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-121">Again, this differs from NOR memory that can be written an unlimited number of times providing the write request is clearing set bits.</span></span> <span data-ttu-id="ac6e1-122">最後に、各ページに関連付けられている予備バイトは、NAND フラッシュに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-122">Finally, the spare bytes associated with each page are unique to NAND flash.</span></span> <span data-ttu-id="ac6e1-123">次の表に、一般的な予備バイトの構成を示します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-123">Typical spare byte configurations are as shown in the table below.</span></span>

| <span data-ttu-id="ac6e1-124">**予備バイト**</span><span class="sxs-lookup"><span data-stu-id="ac6e1-124">**Spare Bytes**</span></span> | <span data-ttu-id="ac6e1-125">**バイト番号**</span><span class="sxs-lookup"><span data-stu-id="ac6e1-125">**Byte numbers**</span></span> | <span data-ttu-id="ac6e1-126">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="ac6e1-126">**Configuration**</span></span>     |
| ------------------------- | -------------- | --------------------- |
| <span data-ttu-id="ac6e1-127">8</span><span class="sxs-lookup"><span data-stu-id="ac6e1-127">8</span></span>                         | <span data-ttu-id="ac6e1-128">バイト 0-2:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-128">Bytes 0-2:</span></span>     | <span data-ttu-id="ac6e1-129">ECC バイト</span><span class="sxs-lookup"><span data-stu-id="ac6e1-129">ECC bytes</span></span>             |
|                           | <span data-ttu-id="ac6e1-130">バイト 3、4、6、7:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-130">Bytes 3,4,6,7:</span></span> | <span data-ttu-id="ac6e1-131">LevelX セクター マッピング</span><span class="sxs-lookup"><span data-stu-id="ac6e1-131">LevelX Sector Mapping</span></span> |
|                           | <span data-ttu-id="ac6e1-132">バイト 5:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-132">Byte 5:</span></span>        | <span data-ttu-id="ac6e1-133">不良ブロック フラグ</span><span class="sxs-lookup"><span data-stu-id="ac6e1-133">Bad block flag</span></span>        |
| <span data-ttu-id="ac6e1-134">16</span><span class="sxs-lookup"><span data-stu-id="ac6e1-134">16</span></span>                        | <span data-ttu-id="ac6e1-135">バイト 0-3、6-7:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-135">Bytes 0-3,6-7:</span></span> | <span data-ttu-id="ac6e1-136">ECC バイト</span><span class="sxs-lookup"><span data-stu-id="ac6e1-136">ECC bytes</span></span>             |
|                           | <span data-ttu-id="ac6e1-137">バイト 8-11:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-137">Bytes 8-11:</span></span>    | <span data-ttu-id="ac6e1-138">LevelX セクター マッピング</span><span class="sxs-lookup"><span data-stu-id="ac6e1-138">LevelX Sector Mapping</span></span> |
|                           | <span data-ttu-id="ac6e1-139">バイト 12-15:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-139">Bytes 12-15:</span></span>   | <span data-ttu-id="ac6e1-140">未使用</span><span class="sxs-lookup"><span data-stu-id="ac6e1-140">Unused</span></span>                |
|                           | <span data-ttu-id="ac6e1-141">バイト 5:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-141">Byte 5:</span></span>        | <span data-ttu-id="ac6e1-142">不良ブロック フラグ</span><span class="sxs-lookup"><span data-stu-id="ac6e1-142">Bad block flag</span></span>        |
| <span data-ttu-id="ac6e1-143">64</span><span class="sxs-lookup"><span data-stu-id="ac6e1-143">64</span></span>                        | <span data-ttu-id="ac6e1-144">バイト 0:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-144">Byte 0:</span></span>        | <span data-ttu-id="ac6e1-145">不良ブロック フラグ</span><span class="sxs-lookup"><span data-stu-id="ac6e1-145">Bad block flag</span></span>        |
|                           | <span data-ttu-id="ac6e1-146">バイト 2-5:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-146">Bytes 2-5:</span></span>     | <span data-ttu-id="ac6e1-147">LevelX セクター マッピング</span><span class="sxs-lookup"><span data-stu-id="ac6e1-147">LevelX Sector Mapping</span></span> |
|                           | <span data-ttu-id="ac6e1-148">バイト 6-39:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-148">Bytes 6-39:</span></span>    | <span data-ttu-id="ac6e1-149">未使用</span><span class="sxs-lookup"><span data-stu-id="ac6e1-149">Unused</span></span>                |
|                           | <span data-ttu-id="ac6e1-150">バイト 40-63:</span><span class="sxs-lookup"><span data-stu-id="ac6e1-150">Bytes 40-63:</span></span>   | <span data-ttu-id="ac6e1-151">ECC バイト</span><span class="sxs-lookup"><span data-stu-id="ac6e1-151">ECC bytes</span></span>             |

<span data-ttu-id="ac6e1-152">LevelX では、各 NAND ページの予備の 4 バイトを利用して、物理 NAND ページにマップされた論理セクターが追跡されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-152">LevelX Utilizes 4 of the spare bytes of each NAND page for keeping track of the logical sector mapped to the physical NAND page.</span></span> <span data-ttu-id="ac6e1-153">これらの 4 バイトは、LevelX 専用の形式で 32 ビット符号なし整数を実装するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-153">These 4 bytes are used to implement a 32-bit unsigned integer with a LevelX proprietary format.</span></span> <span data-ttu-id="ac6e1-154">32 ビット フィールドの上位ビット (ビット 31) は、論理セクターとページのマッピングが有効であることを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-154">The upper bit of the 32-bit field (bit 31) is used to indicate the logical sector-to-page mapping is valid.</span></span> <span data-ttu-id="ac6e1-155">このビットが 0 の場合は、このページの情報が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-155">If this bit is 0, the information in this page is no longer valid.</span></span> <span data-ttu-id="ac6e1-156">次のビット (ビット 30) は、このページが廃止されるプロセス内にあり、新しいセクターが書き込まれていることを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-156">The next bit—bit 30—is used to indicate this page is in the process of becoming obsolete and a new sector is being written.</span></span> <span data-ttu-id="ac6e1-157">ビット 29 は、マッピング エントリの書き込みが完了したことを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-157">Bit 29 is used to indicate when the mapping entry write is complete.</span></span> <span data-ttu-id="ac6e1-158">ビット 29 が 0 の場合、マッピング エントリの書き込みは完了です。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-158">If bit 29 is 0, the mapping entry write is complete.</span></span> <span data-ttu-id="ac6e1-159">ビット 29 が設定されている場合、マッピング エントリは書き込み処理中でした。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-159">If bit 29 is set, the mapping entry was in the process of being written.</span></span> <span data-ttu-id="ac6e1-160">ビット 30 と 29 は、新しいフラッシュ ページを更新するときのパワー ロスの可能性から回復するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-160">Bits 30 and 29 are used in recovering from a potential power loss while updating a new flash page.</span></span> <span data-ttu-id="ac6e1-161">最後に、下位 29 ビット (28-0) にページの論理セクター番号が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-161">Finally, the lower 29-bits (28-0) contain the logical sector number for the page.</span></span>

<span data-ttu-id="ac6e1-162">**LevelX マッピング エントリ**</span><span class="sxs-lookup"><span data-stu-id="ac6e1-162">**LevelX Mapping Entry**</span></span>

| <span data-ttu-id="ac6e1-163">ビット</span><span class="sxs-lookup"><span data-stu-id="ac6e1-163">Bit(s)</span></span> | <span data-ttu-id="ac6e1-164">意味</span><span class="sxs-lookup"><span data-stu-id="ac6e1-164">Meaning</span></span> |
| ------ | ------- |
| <span data-ttu-id="ac6e1-165">31</span><span class="sxs-lookup"><span data-stu-id="ac6e1-165">31</span></span>     | <span data-ttu-id="ac6e1-166">有効なフラグ。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-166">Valid flag.</span></span> <span data-ttu-id="ac6e1-167">設定され、論理セクターがすべて 1 ではない場合、マッピングが有効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-167">When set and logical sector is not all ones indicates mapping is valid</span></span> |
| <span data-ttu-id="ac6e1-168">30</span><span class="sxs-lookup"><span data-stu-id="ac6e1-168">30</span></span>     | <span data-ttu-id="ac6e1-169">廃止されたフラグ。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-169">Obsolete flag.</span></span> <span data-ttu-id="ac6e1-170">クリアすると、このマッピングは廃止されるか、廃止のプロセスに入れられます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-170">When clear, this mapping is either obsolete or is in the process of becoming obsolete.</span></span> |
| <span data-ttu-id="ac6e1-171">29</span><span class="sxs-lookup"><span data-stu-id="ac6e1-171">29</span></span>     | <span data-ttu-id="ac6e1-172">このビットが 0 の場合、マッピング エントリの書き込みが完了します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-172">Mapping entry write is complete when this bit is 0</span></span> |
| <span data-ttu-id="ac6e1-173">0-28</span><span class="sxs-lookup"><span data-stu-id="ac6e1-173">0-28</span></span>   | <span data-ttu-id="ac6e1-174">この物理ページにマップされている論理セクター (すべて 1 ではない場合)。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-174">Logical sector mapped to this physical page—when not all ones.</span></span> |

<span data-ttu-id="ac6e1-175">LevelX では、ブロック消去カウントの各 NAND ブロックの最初のページ、およびブロックがいっぱいになったときのマップされたページのリストも利用されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-175">LevelX also utilizes the first page of each NAND block for the block erase count as well as the list of mapped pages when the block is full.</span></span> <span data-ttu-id="ac6e1-176">LevelX の NAND ブロックの最初のページの形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-176">The format of the first page of a NAND block in LevelX is shown below:</span></span>

| <span data-ttu-id="ac6e1-177">LevelX ブロック ページ 0 形式</span><span class="sxs-lookup"><span data-stu-id="ac6e1-177">LevelX Block Page 0 Format</span></span> |
|:--------------------------:|
| <span data-ttu-id="ac6e1-178">[ブロック消去カウント]</span><span class="sxs-lookup"><span data-stu-id="ac6e1-178">[Block Erase Count]</span></span>        |
| <span data-ttu-id="ac6e1-179">[ページ 1 セクター マッピング]</span><span class="sxs-lookup"><span data-stu-id="ac6e1-179">[Page 1 Sector Mapping]</span></span>    |
| <span data-ttu-id="ac6e1-180">...</span><span class="sxs-lookup"><span data-stu-id="ac6e1-180">...</span></span>                        |
| <span data-ttu-id="ac6e1-181">[ページ "n" セクター マッピング]</span><span class="sxs-lookup"><span data-stu-id="ac6e1-181">[Page "n" Sector Mapping]</span></span>  |
| <span data-ttu-id="ac6e1-182">[0xF0F0F0F0]</span><span class="sxs-lookup"><span data-stu-id="ac6e1-182">[0xF0F0F0F0]</span></span>               |

> [!NOTE]
> <span data-ttu-id="ac6e1-183">ページ マッピング情報は、ブロックがいっぱいになったときにのみ書き込まれます。つまり、ブロックのページがすべて書き込まれています。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-183">The page mapping information is only written when the block is full, i.e., all the pages of the block have been written to.</span></span> <span data-ttu-id="ac6e1-184">これにより、実行時に空きページと論理セクターのマッピングを迅速に検索できます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-184">This enables faster search for free pages and logical sector mapping during run-time.</span></span>

## <a name="nand-bad-block-support"></a><span data-ttu-id="ac6e1-185">NAND 不良ブロックのサポート</span><span class="sxs-lookup"><span data-stu-id="ac6e1-185">NAND Bad Block Support</span></span>

<span data-ttu-id="ac6e1-186">NAND メモリには、NOR メモリよりも多くの不良ブロックがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-186">NAND memory is also more likely to have bad blocks than NOR memory.</span></span> <span data-ttu-id="ac6e1-187">この原因の大部分は、NAND の製造元が不良ブロックを許可し、このような不良ブロックを回避するようにソフトウェアに要求することで、利益を上げることができるためです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-187">This is largely because NAND manufacturers can increase yield by allowing bad blocks and requiring software to work-around such bad blocks.</span></span> <span data-ttu-id="ac6e1-188">LevelX では、単に不良ブロックに関するマッピングを行うだけで、NAND の不良ブロック管理が処理されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-188">LevelX handles NAND bad block management by simply mapping around bad blocks.</span></span>

<span data-ttu-id="ac6e1-189">また、LevelX では、基になる LevelX ドライバーで新しい ECC コードを計算するために利用したり、ページの各 256 バイト セクション内でページが読み取られる際に 1 ビットのエラー修正を実行したりするために、256 バイトのハミング エラー修正コード (ECC) 用の API も提供されています。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-189">LevelX also provides APIs for 256-byte Hamming Error Correction Codes (ECC) for the underlying LevelX driver to utilize for calculating new ECC codes or to perform 1-bit error correction on page reading within each 256-byte section of the page.</span></span>

## <a name="nand-driver-requirements"></a><span data-ttu-id="ac6e1-190">NAND ドライバーの要件</span><span class="sxs-lookup"><span data-stu-id="ac6e1-190">NAND Driver Requirements</span></span>

<span data-ttu-id="ac6e1-191">LevelX には、基になるフラッシュ パーツとハードウェアの実装に固有の基になる NAND フラッシュ ドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-191">LevelX requires an underlying NAND flash driver that is specific to the underlying flash part and hardware implementation.</span></span> <span data-ttu-id="ac6e1-192">ドライバーは、API ***lx_nand_flash_open*** を使用した初期化中に、LevelX に指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-192">The driver is specified to LevelX during initialization via the API ***lx_nand_flash_open***.</span></span> <span data-ttu-id="ac6e1-193">LevelX ドライバーのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-193">The prototype of the LevelX driver is as follows.</span></span>

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

<span data-ttu-id="ac6e1-194">*Instance* パラメーターには、LevelX NAND コントロール ブロックが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-194">The *instance* parameter specifies the LevelX NAND control block.</span></span> <span data-ttu-id="ac6e1-195">ドライバー初期化関数では、関連する LevelX インスタンスの他のすべてのドライバー レベル サービスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-195">The driver initialization function is responsible for setting up all the other driver-level services for the associated LevelX instance.</span></span> <span data-ttu-id="ac6e1-196">次の一覧に、各 LevelX NAND インスタンスに必要なサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-196">The services required for each LevelX NAND instance are shown in the list below.</span></span>

- <span data-ttu-id="ac6e1-197">ページの読み取り</span><span class="sxs-lookup"><span data-stu-id="ac6e1-197">Read Page</span></span>
- <span data-ttu-id="ac6e1-198">ページの書き込み</span><span class="sxs-lookup"><span data-stu-id="ac6e1-198">Write Page</span></span>
- <span data-ttu-id="ac6e1-199">ブロック消去</span><span class="sxs-lookup"><span data-stu-id="ac6e1-199">Block Erase</span></span>
- <span data-ttu-id="ac6e1-200">ブロック消去の確認</span><span class="sxs-lookup"><span data-stu-id="ac6e1-200">Block Erased Verify</span></span>
- <span data-ttu-id="ac6e1-201">ページ消去の確認</span><span class="sxs-lookup"><span data-stu-id="ac6e1-201">Page Erased Verify</span></span>
- <span data-ttu-id="ac6e1-202">ブロック状態の取得</span><span class="sxs-lookup"><span data-stu-id="ac6e1-202">Block Status Get</span></span>
- <span data-ttu-id="ac6e1-203">ブロック状態の設定</span><span class="sxs-lookup"><span data-stu-id="ac6e1-203">Block Status Set</span></span>
- <span data-ttu-id="ac6e1-204">ブロック追加バイトの取得</span><span class="sxs-lookup"><span data-stu-id="ac6e1-204">Block Extra Bytes Get</span></span>
- <span data-ttu-id="ac6e1-205">ブロック追加バイトの設定</span><span class="sxs-lookup"><span data-stu-id="ac6e1-205">Block Extra Bytes Set</span></span>
- <span data-ttu-id="ac6e1-206">システム エラー ハンドラー</span><span class="sxs-lookup"><span data-stu-id="ac6e1-206">System Error Handler</span></span>

## <a name="driver-initialization"></a><span data-ttu-id="ac6e1-207">ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="ac6e1-207">Driver Initialization</span></span>

<span data-ttu-id="ac6e1-208">これらのサービスは、ドライバーの初期化関数内の **LX_NAND_FLASH** インスタンスに関数ポインターを設定することで設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-208">These services are setup via setting function pointers in the **LX_NAND_FLASH** instance within the driver's initialization function.</span></span> <span data-ttu-id="ac6e1-209">ドライバー初期化関数では、ブロックの合計数、1 ブロックあたりのページ数、1 ページあたりのバイト数、1 ページをメモリに読み込むのに十分な大きさの RAM 領域が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-209">The driver initialization function also specifies the total number of block, pages per block, bytes per page, and a RAM area large enough to read one page into memory.</span></span> <span data-ttu-id="ac6e1-210">また、ドライバー初期化関数では、**LX_SUCCESS** が返される前に、追加のデバイスまたは実装固有の初期化処理 (あるいは両方) も実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-210">The driver initialization function likely also performs additional device and/or implementation-specific initialization duties before returning **LX_SUCCESS**.</span></span>

## <a name="driver-read-page"></a><span data-ttu-id="ac6e1-211">ドライバーの読み取りページ</span><span class="sxs-lookup"><span data-stu-id="ac6e1-211">Driver Read Page</span></span>

<span data-ttu-id="ac6e1-212">LevelX NAND ドライバーの "ページの読み取り" サービスでは、NAND フラッシュの特定のブロック内で特定のページが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-212">The LevelX NAND driver "read page" service is responsible for reading a specific page in a specific block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-213">すべてのエラー チェックと修正ロジックは、ドライバー サービスの役割です。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-213">All error checking and correcting logic is the responsibility of the driver service.</span></span> <span data-ttu-id="ac6e1-214">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-214">If successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-215">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-215">If not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-216">LevelX NAND ドライバーの "ページの読み取り" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-216">The prototype of the LevelX NAND driver "read page" service is given below.</span></span>

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

<span data-ttu-id="ac6e1-217">ここでは、*block* と *page* で読み取られるページが識別され、*destination* と *words* でページのコンテンツが配置される場所と読み取られる 32 ビットのワード数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-217">Where *block* and *page* identify which page to read and *destination* and *words* specify where to place the page contents and how many 32-bit words to read.</span></span>

## <a name="driver-write-page"></a><span data-ttu-id="ac6e1-218">ドライバーの書き込みページ</span><span class="sxs-lookup"><span data-stu-id="ac6e1-218">Driver Write Page</span></span>

<span data-ttu-id="ac6e1-219">LevelX NAND ドライバーの "ページの書き込み" サービスでは、特定のページが NAND フラッシュの指定したブロックに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-219">The LevelX NAND driver "write page" service is responsible for writing a specific page into the specified block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-220">すべてのエラー チェックと ECC 計算は、ドライバー サービスの役割です。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-220">All error checking and ECC computation is the responsibility of the driver service.</span></span> <span data-ttu-id="ac6e1-221">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-221">If successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-222">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-222">If not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-223">LevelX NAND ドライバーの "ページの書き込み" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-223">The prototype of the LevelX NAND driver "write page" service is shown below.</span></span>

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

<span data-ttu-id="ac6e1-224">ここでは、*block* と *page* で書き込まれるページが識別され、*source* と *words* で書き込み元と書き込まれる 32 ビットのワード数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-224">Where *block* and *page* identify which page to write and *source* and *words* specify the source of the write and how many 32-bit words to write.</span></span>

> [!NOTE]
> <span data-ttu-id="ac6e1-225">LevelX では、フラッシュ ページへの書き込み時に、ドライバーに依存して低レベルのエラー検出が行われます。一般に、書き込みに成功したことを確認するために、ページが読み取られ、書き込みバッファーと比較されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-225">LevelX relies on the driver for low-level error detection when writing to the flash page, which typically involves reading back the page and comparing with the write buffer to ensure the write was successful.</span></span>

## <a name="driver-block-erase"></a><span data-ttu-id="ac6e1-226">ドライバー ブロック消去</span><span class="sxs-lookup"><span data-stu-id="ac6e1-226">Driver Block Erase</span></span>

<span data-ttu-id="ac6e1-227">LevelX NAND ドライバーの "ブロック消去" サービスでは、NOR フラッシュの指定したブロックが消去されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-227">The LevelX NAND driver "block erase" service is responsible for erasing the specified block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-228">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-228">If successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-229">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-229">If not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-230">LevelX NAND ドライバーの "ブロック消去" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-230">The prototype of the LevelX NAND driver "block erase" service is as follows.</span></span>

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

<span data-ttu-id="ac6e1-231">ここでは、*block* で消去するブロックが識別されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-231">Where *block* identifies which block to erase.</span></span> <span data-ttu-id="ac6e1-232">*erase_count* パラメーターは、診断のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-232">The parameter *erase_count* is provided for diagnostic purposes.</span></span> <span data-ttu-id="ac6e1-233">たとえば、消去数が特定のしきい値を超えた場合、ドライバーは、アプリケーション ソフトウェアの別の部分を警告することがあります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-233">For example, the driver may want to alert another portion of the application software when the erase count exceeds a specific threshold.</span></span>

> [!NOTE]
> <span data-ttu-id="ac6e1-234">LevelX では、ブロックの消去時に、ドライバーに依存して低レベルのエラー検出が行われます。一般に、ブロックのすべてのページがすべて 1 であることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-234">LevelX relies on the driver for low-level error detection when the block is erased, which typically involves ensuring that all pages of the block are all ones.</span></span>

## <a name="driver-block-erased-verify"></a><span data-ttu-id="ac6e1-235">ドライバー ブロック消去の確認</span><span class="sxs-lookup"><span data-stu-id="ac6e1-235">Driver Block Erased Verify</span></span>

<span data-ttu-id="ac6e1-236">LevelX NAND ドライバーの "ブロック消去の確認" サービスでは、NAND フラッシュの指定したブロックが消去されていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-236">The LevelX NAND driver "block erased verify" service is responsible for verifying that the specified block of the NAND flash is erased.</span></span> <span data-ttu-id="ac6e1-237">消去されている場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-237">If it is erased, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-238">ブロックが消去されていない場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-238">If the block is not erased, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-239">LevelX NAND ドライバーの "ブロック消去の確認" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-239">The prototype of the LevelX NAND driver "block erased verify" service is:</span></span>

```c
INT nand_driver_block_erased_verify(ULONG block);
```

<span data-ttu-id="ac6e1-240">ここでは、*block* で消去されていることを確認するブロックが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-240">Where *block* specifies which block to verify that it is erased.</span></span>

> [!NOTE]
> <span data-ttu-id="ac6e1-241">LevelX では、ドライバーに依存して、すべてのページと各ページのすべてのバイト (予備バイトとデータ バイトを含む) が消去されている (すべて 1 が含まれている) ことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-241">LevelX relies on the driver to examine all pages and all bytes of each page – including spare and data bytes – to ensure they are erased (contain all ones).</span></span>

## <a name="driver-page-erased-verify"></a><span data-ttu-id="ac6e1-242">ドライバー ページ消去の確認</span><span class="sxs-lookup"><span data-stu-id="ac6e1-242">Driver Page Erased Verify</span></span>

<span data-ttu-id="ac6e1-243">LevelX NAND ドライバーの "ブロック消去の確認" サービスでは、NAND フラッシュの指定したブロックの指定したページが消去されていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-243">The LevelX NAND driver "page erased verify" service is responsible for verifying that the specified page of the specified block of the NAND flash is erased.</span></span> <span data-ttu-id="ac6e1-244">消去されている場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-244">If it is erased, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-245">ページが消去されていない場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-245">If the page is not erased, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-246">LevelX NAND ドライバーの "ページ消去の確認" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-246">The prototype of the LevelX NAND driver "page erased verify" service is:</span></span>

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
<span data-ttu-id="ac6e1-247">ここでは、*block* でブロックが指定され、*page* で消去されていることを確認するページが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-247">Where *block* specifies which block and *page* specifies the page to verify that it is erased.</span></span>

> [!NOTE]
> <span data-ttu-id="ac6e1-248">LevelX では、ドライバーに依存して、指定したページのすべてのバイト (予備バイトとデータ バイトを含む) が消去されている (すべて 1 が含まれている) ことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-248">LevelX relies on the driver to examine all bytes of the specified page – including spare and data bytes – to ensure they are erased (contain all ones).</span></span>

## <a name="driver-block-status-get"></a><span data-ttu-id="ac6e1-249">ドライバー ブロック状態の取得</span><span class="sxs-lookup"><span data-stu-id="ac6e1-249">Driver Block Status Get</span></span>

<span data-ttu-id="ac6e1-250">LevelX NAND ドライバーの "ブロック状態の取得" サービスでは、NAND フラッシュの指定したブロックの不良ブロック フラグが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-250">The LevelX NAND driver "block status get" service is responsible for retrieving the bad block flag of the specified block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-251">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-251">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-252">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-252">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-253">LevelX NAND ドライバーの "ブロック状態の取得" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-253">The prototype of the LevelX NAND driver "block status get" service is: shown below.</span></span>

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

<span data-ttu-id="ac6e1-254">ここでは、*block* でブロックが指定され、*bad_block_byte* で不良ブロック フラグの宛先が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-254">Where *block* specifies which block and *bad_block_byte* specifies the destination for the bad block flag.</span></span>

## <a name="driver-block-status-set"></a><span data-ttu-id="ac6e1-255">ドライバー ブロック状態の設定</span><span class="sxs-lookup"><span data-stu-id="ac6e1-255">Driver Block Status Set</span></span>

<span data-ttu-id="ac6e1-256">LevelX NAND ドライバーの "ブロック状態の設定" サービスでは、NAND フラッシュの指定したブロックの不良ブロック フラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-256">The LevelX NAND driver "block status set" service is responsible for setting the bad block flag of the specified block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-257">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-257">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-258">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-258">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-259">LevelX NAND ドライバーの "ブロック状態の設定" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-259">The prototype of the LevelX NAND driver "block status set" service is:</span></span>

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

<span data-ttu-id="ac6e1-260">ここでは、*block* でブロックが指定され、*bad_block_byte* で不良ブロック フラグの値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-260">Where *block* specifies which block and *bad_block_byte* specifies the value of the bad block flag.</span></span>

## <a name="driver-block-extra-bytes-get"></a><span data-ttu-id="ac6e1-261">ドライバー ブロック追加バイトの取得</span><span class="sxs-lookup"><span data-stu-id="ac6e1-261">Driver Block Extra Bytes Get</span></span>

<span data-ttu-id="ac6e1-262">LevelX NAND ドライバーの "ブロック追加バイトの取得" サービスでは、NAND フラッシュの特定のブロックの特定のページに関連付けられた追加バイトが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-262">The LevelX NAND driver "block extra bytes get" service is responsible for retrieving extra bytes associated with a specific page of a specific block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-263">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-263">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-264">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-264">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-265">LevelX NAND ドライバーの "ブロック追加バイトの取得" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-265">The prototype of the LevelX NAND driver "block extra bytes get" service is:</span></span>

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

<span data-ttu-id="ac6e1-266">ここでは、*block* でブロックが指定され、*page* で特定のページが指定され、*destination* で追加バイトの宛先が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-266">Where *block* specifies which block, *page* specifies the specific page and *destination* specifies the destination for the extra bytes.</span></span> <span data-ttu-id="ac6e1-267">*size* パラメーターには、取得する追加バイトの数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-267">The parameter *size* specifies how many extra bytes to get.</span></span>

## <a name="driver-block-extra-bytes-set"></a><span data-ttu-id="ac6e1-268">ドライバー ブロック追加バイトの設定</span><span class="sxs-lookup"><span data-stu-id="ac6e1-268">Driver Block Extra Bytes Set</span></span>

<span data-ttu-id="ac6e1-269">LevelX NAND ドライバーの "ブロック追加バイトの設定" サービスでは、NAND フラッシュの特定のブロックの特定のページに追加バイトが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-269">The LevelX NAND driver "block extra bytes set" service is responsible for setting extra bytes in a specific page of a specific block of the NAND flash.</span></span> <span data-ttu-id="ac6e1-270">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-270">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-271">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-271">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-272">LevelX NAND ドライバーの "ブロック追加バイトの設定" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-272">The prototype of the LevelX NAND driver "block extra bytes set" service is:</span></span>

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

<span data-ttu-id="ac6e1-273">ここでは、*block* でブロックが指定され、*page* で特定のページが指定され、*source* で追加バイトのソースが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-273">Where *block* specifies which block, *page* specifies the specific page and *source* specifies the source of the extra bytes.</span></span> <span data-ttu-id="ac6e1-274">*size* パラメーターには、設定する追加バイトの数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-274">The parameter *size* specifies how many extra bytes to set.</span></span>

## <a name="driver-system-error"></a><span data-ttu-id="ac6e1-275">ドライバー システム エラー</span><span class="sxs-lookup"><span data-stu-id="ac6e1-275">Driver System Error</span></span>

<span data-ttu-id="ac6e1-276">LevelX NAND ドライバーの "システム エラー ハンドラー" サービスでは、LevelX で検出されたシステム エラーの処理が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-276">The LevelX NAND driver "system error handler" service is responsible for setting handling system errors detected by LevelX.</span></span> <span data-ttu-id="ac6e1-277">このルーチンでの処理は、アプリケーションに依存します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-277">The processing in this routine is application dependent.</span></span> <span data-ttu-id="ac6e1-278">成功した場合、LevelX NAND ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-278">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="ac6e1-279">成功しなかった場合、LevelX NAND ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-279">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="ac6e1-280">LevelX NAND ドライバーの "システム エラー" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-280">The prototype of the LevelX NAND driver "system error" service is:</span></span>

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

<span data-ttu-id="ac6e1-281">ここでは、*block* でブロックが指定され、*page* で *error_code* が表すエラーが発生した特定のページが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-281">Where *block* specifies which block, and *page* specifies the specific page the error represented by *error_code* occurred.</span></span>

## <a name="nand-simulated-driver"></a><span data-ttu-id="ac6e1-282">NAND シミュレート済みドライバー</span><span class="sxs-lookup"><span data-stu-id="ac6e1-282">NAND Simulated Driver</span></span>

<span data-ttu-id="ac6e1-283">LevelX では、単純に RAM を使用して NAND フラッシュ部分の操作をシミュレートするシミュレート済み NAND フラッシュ ドライバーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-283">LevelX provides a simulated NAND flash driver that simply uses RAM to simulate the operation of a NAND flash part.</span></span> <span data-ttu-id="ac6e1-284">既定では、NAND のシミュレート済みドライバーで、1 ブロックあたり 16 ページで、1 ページあたり 2048 バイトの NAND フラッシュ ブロックが 8 つ提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-284">By default, the NAND simulated driver provides 8 NAND flash blocks with 16 pages per block and 2048 bytes per page.</span></span>

<span data-ttu-id="ac6e1-285">シミュレート済み NAND フラッシュ ドライバー初期化関数は、***lx_nand_flash_simulator_initialize** _ であり、_*_lx_nand_flash_simulator.c_\*\* で定義されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-285">The simulated NAND flash driver initialization function is ***lx_nand_flash_simulator_initialize** _ and is defined in _*_lx_nand_flash_simulator.c_\*\*.</span></span> <span data-ttu-id="ac6e1-286">このドライバーでは、特定の NAND フラッシュ ドライバーを作成するための便利なテンプレートも提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-286">This driver also provides a good template for writing specific NAND flash drivers.</span></span>

## <a name="nand-filex-integration"></a><span data-ttu-id="ac6e1-287">NAND FileX の統合</span><span class="sxs-lookup"><span data-stu-id="ac6e1-287">NAND FileX Integration</span></span>

<span data-ttu-id="ac6e1-288">前述のように、LevelX の操作では FileX が使用されません。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-288">As mentioned earlier, LevelX does not rely on FileX for operation.</span></span> <span data-ttu-id="ac6e1-289">LevelX で提供される論理セクターに生データを格納または取得するために、すべての LevelX API は、アプリケーション ソフトウェアから直接呼び出される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-289">All the LevelX APIs may be called directly by the application software to store/retrieve raw data to the logical sectors provided by LevelX.</span></span> <span data-ttu-id="ac6e1-290">ただし、LevelX では FileX もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-290">However, LevelX also supports FileX.</span></span>

<span data-ttu-id="ac6e1-291">ファイル ***fx_nand_flash_simulated_driver.c*** には、NAND フラッシュのシミュレーションで使用する FileX ドライバーの例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-291">The file ***fx_nand_flash_simulated_driver.c*** contains an example FileX driver for use with the NAND flash simulation.</span></span> <span data-ttu-id="ac6e1-292">このドライバーの興味深い点は、2048 バイトのページを使用することで、一般に FileX で使用される 512 バイトの論理セクターと、LevelX シミュレーターへの単一の論理セクターの読み取り/書き込み要求が結合されることです。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-292">An interesting aspect of this driver is that it combines 512-byte logical sectors typically used by FileX into single logical sector read/write requests to the LevelX simulator using 2048-byte pages.</span></span> <span data-ttu-id="ac6e1-293">これにより、NAND フラッシュ メモリをより効率的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-293">This results in more efficient use of the NAND flash memory.</span></span> <span data-ttu-id="ac6e1-294">LevelX 用の NAND フラッシュ FileX ドライバーでは、カスタム FileX ドライバーを作成するための効果的な出発点が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-294">The NAND flash FileX driver for LevelX provides a good starting point for writing custom FileX drivers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac6e1-295">FileX NAND フラッシュの形式は、NAND フラッシュで提供されるものよりも小さいセクターの 1 つの完全なブロック サイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-295">The FileX NAND flash format should be one full block size of sectors less than the NAND flash provides.</span></span> <span data-ttu-id="ac6e1-296">これにより、消耗レベルの処理中に最適なパフォーマンスを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-296">This will help ensure best performance during the wear level processing.</span></span> <span data-ttu-id="ac6e1-297">LevelX の消耗平準化アルゴリズムでは、次のような書き込みパフォーマンスを向上させるための追加の手法があります。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-297">Additional techniques to improve write performance in the LevelX wear leveling algorithm include the following.</span></span>

1. <span data-ttu-id="ac6e1-298">すべての書き込みが、正確に 1 つ以上のクラスターのサイズになり、正確なクラスター境界で開始されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-298">Ensure that all writes are exactly one or more clusters in size and start on exact cluster boundaries.</span></span>
1. <span data-ttu-id="ac6e1-299">API の FileX ***fx_file_allocate*** クラスを使用して大きなファイル書き込み操作を実行する前に、クラスターを事前に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-299">Pre-allocate clusters before performing large file write operations via the FileX ***fx_file_allocate*** class of APIs.</span></span>
1. <span data-ttu-id="ac6e1-300">リリース セクター情報を受信するために FileX ドライバーが有効になっていること、およびセクターをリリースするためにドライバーに対して行われた要求が、***lx_nor_flash_sector_release*** を呼び出すことによってドライバーで処理されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-300">Ensure the FileX driver is enabled to receive release sector information and requests made to the driver to release sectors are handled in the driver by calling ***lx_nor_flash_sector_release***.</span></span>
1. <span data-ttu-id="ac6e1-301">***lx_nand_flash_defragment*** を定期的に使用して、可能な限り多くの NAND ブロックを解放し、書き込みパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-301">Periodic use of ***lx_nand_flash_defragment*** to free up as many NAND blocks as possible and thus improve write performance.</span></span>
1. <span data-ttu-id="ac6e1-302">***lx_nand_flash_extended_cache_enable*** API を使用すると、パフォーマンスを向上させるためにさまざまな NAND ブロック リソースの RAM キャッシュが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac6e1-302">Utilize the ***lx_nand_flash_extended_cache_enable*** API to provide a RAM cache of various NAND block resources for faster performance.</span></span>
