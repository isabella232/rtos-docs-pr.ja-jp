---
title: 第 5 章-Azure RTOS LevelX NOR サポート
description: NOR フラッシュ メモリは、通常 512 バイトで均等に割り切れるブロックで構成されています。 Azure RTOS LevelX は、各 NOR フラッシュ ブロックを 512 バイトの論理セクターに分割します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3a0c73c2b45c32bf3f1ef56de684fa83c334b59e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811075"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a><span data-ttu-id="b7b69-104">第 5 章-Azure RTOS LevelX NOR サポート</span><span class="sxs-lookup"><span data-stu-id="b7b69-104">Chapter 5 - Azure RTOS LevelX NOR support</span></span>

<span data-ttu-id="b7b69-105">NOR フラッシュ メモリは、通常 512 バイトで均等に割り切れる "*ブロック*" で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b7b69-105">NOR flash memory is composed of *blocks* that are typically evenly divisible by 512 bytes.</span></span> <span data-ttu-id="b7b69-106">NOR フラッシュ メモリにはフラッシュ "*ページ*" の概念はありません。</span><span class="sxs-lookup"><span data-stu-id="b7b69-106">There are no concept of a flash *page* in NOR flash memory.</span></span> <span data-ttu-id="b7b69-107">また、NOR フラッシュ メモリには "*スペア*" バイトがないため、Azure RTOS LevelX では、すべての管理情報に NOR フラッシュ メモリ自体を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-107">Also, there are no *spare* bytes in NOR flash memory, hence Azure RTOS LevelX must use the NOR flash memory itself for all management information.</span></span> <span data-ttu-id="b7b69-108">NOR フラッシュ メモリでは直接読み取りアクセスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-108">Direct read access is possible in NOR flash memory.</span></span> <span data-ttu-id="b7b69-109">通常、書き込みアクセスには、特別な操作シーケンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7b69-109">Write access typically requires a special sequence of operations.</span></span> <span data-ttu-id="b7b69-110">ビットがクリアされている場合、NOR フラッシュ メモリが複数回書き込まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-110">NOR flash memory may be written to multiple times, providing that bits are being cleared.</span></span> <span data-ttu-id="b7b69-111">NOR フラッシュ メモリのビットは、ブロック消去操作によって一度だけ設定できます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-111">Bits in NOR flash memory can only be set once, via the erase block operation.</span></span>

<span data-ttu-id="b7b69-112">LevelX は、各 NOR フラッシュ ブロックを 512 バイトの論理 *セクター* に分割します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-112">LevelX divides each NOR flash block into 512-byte logical *sectors*.</span></span> <span data-ttu-id="b7b69-113">さらに、LevelX では、各 NOR フラッシュ ブロックの最初の "n" セクターを使用して、管理情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-113">Furthermore, LevelX uses the first "n" sectors of each NOR flash block to store management information.</span></span> <span data-ttu-id="b7b69-114">LevelX NOR フラッシュ メモリの管理情報の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-114">The format of the LevelX NOR flash memory management information is:</span></span>

<span data-ttu-id="b7b69-115">**LevelX NOR ブロック形式**</span><span class="sxs-lookup"><span data-stu-id="b7b69-115">**LevelX NOR Block Format**</span></span>

| <span data-ttu-id="b7b69-116">バイト オフセット</span><span class="sxs-lookup"><span data-stu-id="b7b69-116">Byte Offset</span></span>  | <span data-ttu-id="b7b69-117">内容</span><span class="sxs-lookup"><span data-stu-id="b7b69-117">Contents</span></span>                     |
| ------------ | ---------------------------- |
| <span data-ttu-id="b7b69-118">0</span><span class="sxs-lookup"><span data-stu-id="b7b69-118">0</span></span>            | <span data-ttu-id="b7b69-119">[ブロック消去カウント]</span><span class="sxs-lookup"><span data-stu-id="b7b69-119">[Block Erase Count]</span></span>          |
| <span data-ttu-id="b7b69-120">4</span><span class="sxs-lookup"><span data-stu-id="b7b69-120">4</span></span>            | <span data-ttu-id="b7b69-121">[最小マップ セクター]</span><span class="sxs-lookup"><span data-stu-id="b7b69-121">[Minimum Mapped Sector]</span></span>      |
| <span data-ttu-id="b7b69-122">8</span><span class="sxs-lookup"><span data-stu-id="b7b69-122">8</span></span>            | <span data-ttu-id="b7b69-123">[最大マップ セクター]</span><span class="sxs-lookup"><span data-stu-id="b7b69-123">[Maximum Mapped Sector]</span></span>      |
| <span data-ttu-id="b7b69-124">12</span><span class="sxs-lookup"><span data-stu-id="b7b69-124">12</span></span>           | <span data-ttu-id="b7b69-125">[空きセクター ビット マップ]</span><span class="sxs-lookup"><span data-stu-id="b7b69-125">[Free Sector Bit Map]</span></span>        |
| <span data-ttu-id="b7b69-126">m</span><span class="sxs-lookup"><span data-stu-id="b7b69-126">m</span></span>            | <span data-ttu-id="b7b69-127">[セクター 0 マッピング エントリ]</span><span class="sxs-lookup"><span data-stu-id="b7b69-127">[Sector 0 Mapping Entry]</span></span>     |
|              | <span data-ttu-id="b7b69-128">…</span><span class="sxs-lookup"><span data-stu-id="b7b69-128">…</span></span>                            |
| <span data-ttu-id="b7b69-129">m+4\*(n-1)</span><span class="sxs-lookup"><span data-stu-id="b7b69-129">m+4\*(n-1)</span></span>    | <span data-ttu-id="b7b69-130">[セクター "n" マッピング エントリ]</span><span class="sxs-lookup"><span data-stu-id="b7b69-130">[Sector "n" Mapping Entry]</span></span>   |
|              | <span data-ttu-id="b7b69-131">…</span><span class="sxs-lookup"><span data-stu-id="b7b69-131">…</span></span>                            |
| <span data-ttu-id="b7b69-132">s</span><span class="sxs-lookup"><span data-stu-id="b7b69-132">s</span></span>            | <span data-ttu-id="b7b69-133">[セクター 0 のコンテンツ]</span><span class="sxs-lookup"><span data-stu-id="b7b69-133">[Sector 0 Contents]</span></span>          |
|              | <span data-ttu-id="b7b69-134">…</span><span class="sxs-lookup"><span data-stu-id="b7b69-134">…</span></span>                            |
| <span data-ttu-id="b7b69-135">s+512\*(n-1)</span><span class="sxs-lookup"><span data-stu-id="b7b69-135">s+512\*(n-1)</span></span> | <span data-ttu-id="b7b69-136">[セクター "n" のコンテンツ]</span><span class="sxs-lookup"><span data-stu-id="b7b69-136">[Sector "n" Contents]</span></span>         |

<span data-ttu-id="b7b69-137">32 ビットの "*ブロック消去カウント*" には、ブロックが消去された回数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-137">The 32-bit *Block Erase Count* contains the number of times the block has been erased.</span></span> <span data-ttu-id="b7b69-138">LevelX の主な目的は、すべてのブロックの消去カウントを比較的近い状態に保つことで、1 つのブロックが早期に使い切られないようにすることです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-138">The main goal of LevelX is to keep the erase count of all blocks relatively close to help prevent any one block from wearing out prematurely.</span></span> <span data-ttu-id="b7b69-139">32 ビットの "*最小マップ セクター*" および "*最大マップ セクター*" フィールドは、ブロック内のすべての論理セクターがマップされ、書き込まれた場合にのみ書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-139">The 32-bit *Minimum Mapped Sector* and *Maximum Mapped Sector* fields are written only when all the logical sectors in the block have been mapped and written to.</span></span> <span data-ttu-id="b7b69-140">これらのフィールドは、セクターの読み取り操作の最適化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-140">These fields are useful for optimization of the sector read operation.</span></span> <span data-ttu-id="b7b69-141">"*空きセクター ビット マップ*" エントリは、各セット ビットがブロック内のマップされていないセクターに対応するビット マップです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-141">The *Free Sector Bit Map* entry is a bit map where each set bit corresponds to an unmapped sector in the block.</span></span> <span data-ttu-id="b7b69-142">このフィールドは、空きセクター検索の効率を高めるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-142">This field is used to make the free sector search more efficient.</span></span> <span data-ttu-id="b7b69-143">これは、ブロック内の 32 セクターごとに 1 ワードを必要とする可変長フィールドです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-143">This is a variable length field that requires one word for every 32 sectors in the block.</span></span> <span data-ttu-id="b7b69-144">"*セクター マッピング エントリ*" の配列には、ブロック内の各セクターのマッピング情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7b69-144">The *Sector Mapping Entry* array contains mapping information for each sector in the block.</span></span> <span data-ttu-id="b7b69-145">各エントリは次の形式になっています。</span><span class="sxs-lookup"><span data-stu-id="b7b69-145">Each entry has the following format:</span></span>

<span data-ttu-id="b7b69-146">**セクター マッピング エントリ**</span><span class="sxs-lookup"><span data-stu-id="b7b69-146">**Sector Mapping Entry**</span></span>

| <span data-ttu-id="b7b69-147">ビット</span><span class="sxs-lookup"><span data-stu-id="b7b69-147">Bit(s)</span></span> | <span data-ttu-id="b7b69-148">意味</span><span class="sxs-lookup"><span data-stu-id="b7b69-148">Meaning</span></span>  |
| ------ | -------- |
| <span data-ttu-id="b7b69-149">31</span><span class="sxs-lookup"><span data-stu-id="b7b69-149">31</span></span>     | <span data-ttu-id="b7b69-150">有効なフラグ。</span><span class="sxs-lookup"><span data-stu-id="b7b69-150">Valid flag.</span></span> <span data-ttu-id="b7b69-151">設定され、論理セクターがすべて 1 ではない場合、マッピングが有効であることを示します</span><span class="sxs-lookup"><span data-stu-id="b7b69-151">When set and logical sector not all ones indicates mapping is valid</span></span> |
| <span data-ttu-id="b7b69-152">30</span><span class="sxs-lookup"><span data-stu-id="b7b69-152">30</span></span>     | <span data-ttu-id="b7b69-153">廃止されたフラグ。</span><span class="sxs-lookup"><span data-stu-id="b7b69-153">Obsolete flag.</span></span> <span data-ttu-id="b7b69-154">クリアすると、このマッピングは廃止されるか、廃止のプロセスに入れられます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-154">When clear, this mapping is either obsolete or is in the process of becoming obsolete.</span></span> |
| <span data-ttu-id="b7b69-155">29</span><span class="sxs-lookup"><span data-stu-id="b7b69-155">29</span></span>     | <span data-ttu-id="b7b69-156">このビットが 0 の場合、マッピング エントリの書き込みが完了します</span><span class="sxs-lookup"><span data-stu-id="b7b69-156">Mapping entry write is complete when this bit is 0</span></span> |
| <span data-ttu-id="b7b69-157">0-28</span><span class="sxs-lookup"><span data-stu-id="b7b69-157">0-28</span></span>   | <span data-ttu-id="b7b69-158">この物理セクターにマップされている論理セクター。すべてが 1 ではない場合。</span><span class="sxs-lookup"><span data-stu-id="b7b69-158">Logical sector mapped to this physical sector—when not all ones.</span></span> |

<span data-ttu-id="b7b69-159">32 ビット フィールドの上位ビット (ビット 31) は、論理セクターのマッピングが有効であることを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-159">The upper bit of the 32-bit field (bit 31) is used to indicate the logical sector mapping is valid.</span></span> <span data-ttu-id="b7b69-160">このビットが 0 の場合、このエントリの情報 (および対応するセクターのコンテンツ) は無効になります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-160">If this bit is 0, the information in this entry (and corresponding sector contents) is no longer valid.</span></span> <span data-ttu-id="b7b69-161">次のビット (ビット 30) は、このセクターが廃止されるプロセス内にあり、新しいセクターが書き込まれていることを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-161">The next bit - bit 30 - is used to indicate this sector is in the process of becoming obsolete and a new sector is being written.</span></span> <span data-ttu-id="b7b69-162">ビット 29 は、マッピング エントリの書き込みがいつ完了するかを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-162">Bit 29 is used to indicate when the mapping entry write is complete.</span></span> <span data-ttu-id="b7b69-163">ビット 29 が 0 の場合、マッピング エントリの書き込みは完了です。</span><span class="sxs-lookup"><span data-stu-id="b7b69-163">If bit 29 is 0, the mapping entry write is complete.</span></span> <span data-ttu-id="b7b69-164">ビット 29 が設定されている場合、マッピング エントリは書き込み処理中でした。</span><span class="sxs-lookup"><span data-stu-id="b7b69-164">If bit 29 is set, the mapping entry was in the process of being written.</span></span> <span data-ttu-id="b7b69-165">ビット 30 と 29 は、新しいセクター マッピングを更新するときのパワー ロスの可能性から回復するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-165">Bits 30 and 29 are used in recovering from a potential power loss while updating a new sector mapping.</span></span> <span data-ttu-id="b7b69-166">最後に、下位 29 ビット (28 から 0) にセクターの論理セクター番号が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-166">Finally, the lower 29-bits (28-0) contain the logical sector number for the sector.</span></span> <span data-ttu-id="b7b69-167">セクターがマッピングされていない場合は、すべてのビットが設定されます。つまり、値は 0xFFFFFFFF になります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-167">If a sector has not been mapped, all bits will be set, i.e., it will have a value of 0xFFFFFFFF.</span></span>

## <a name="nor-driver-requirements"></a><span data-ttu-id="b7b69-168">NOR ドライバーの要件</span><span class="sxs-lookup"><span data-stu-id="b7b69-168">NOR Driver Requirements</span></span>

<span data-ttu-id="b7b69-169">LevelX には、基になるフラッシュ パーツとハードウェアの実装に固有の、基になる NOR フラッシュ ドライバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7b69-169">LevelX requires an underlying NOR flash driver that is specific to the underlying flash part and hardware implementation.</span></span> <span data-ttu-id="b7b69-170">ドライバーは、API ***lx_nor_flash_open*** を使用した初期化中に、LevelX に指定されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-170">The driver is specified to LevelX during initialization via the API ***lx_nor_flash_open***.</span></span> <span data-ttu-id="b7b69-171">LevelX ドライバーのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-171">The prototype of the LevelX driver is:</span></span>

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

<span data-ttu-id="b7b69-172">"*Instance*" パラメーターは、LevelX NOR コントロール ブロックを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-172">The "*instance*" parameter specifies the LevelX NOR control block.</span></span> <span data-ttu-id="b7b69-173">ドライバー初期化関数は、関連する LevelX インスタンスの他のすべてのドライバー レベル サービスを設定します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-173">The driver initialization function is responsible for setting up all the other driver-level services for the associated LevelX instance.</span></span> <span data-ttu-id="b7b69-174">各 LevelX NOR インスタンスに必要なサービスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-174">The services required for each LevelX NOR instance are:</span></span>

- <span data-ttu-id="b7b69-175">読み取りセクター</span><span class="sxs-lookup"><span data-stu-id="b7b69-175">Read Sector</span></span>
- <span data-ttu-id="b7b69-176">書き込みセクター</span><span class="sxs-lookup"><span data-stu-id="b7b69-176">Write Sector</span></span>
- <span data-ttu-id="b7b69-177">ブロック消去</span><span class="sxs-lookup"><span data-stu-id="b7b69-177">Block Erase</span></span>
- <span data-ttu-id="b7b69-178">ブロック消去の確認</span><span class="sxs-lookup"><span data-stu-id="b7b69-178">Block Erased Verify</span></span>
- <span data-ttu-id="b7b69-179">システム エラー ハンドラー</span><span class="sxs-lookup"><span data-stu-id="b7b69-179">System Error Handler</span></span>

## <a name="driver-initialization"></a><span data-ttu-id="b7b69-180">ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="b7b69-180">Driver Initialization</span></span>

<span data-ttu-id="b7b69-181">これらのサービスは、ドライバーの初期化関数内の **LX_NOR_FLASH** インスタンスに関数ポインターを設定することによって設定します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-181">These services are setup via setting function pointers in the **LX_NOR_FLASH** instance within the driver's initialization function.</span></span> <span data-ttu-id="b7b69-182">ドライバー初期化関数は、次の役割も実行します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-182">The driver initialization function also is responsible for:</span></span>

1. <span data-ttu-id="b7b69-183">フラッシュのベース アドレスを指定する。</span><span class="sxs-lookup"><span data-stu-id="b7b69-183">Specifying the base address of the flash.</span></span>
1. <span data-ttu-id="b7b69-184">ブロックの合計数とブロックあたりのワード数を指定する。</span><span class="sxs-lookup"><span data-stu-id="b7b69-184">Specifying the total number of blocks and the number of words per block.</span></span>
1. <span data-ttu-id="b7b69-185">フラッシュの 1 セクター (512 バイト) の読み取りおよび ULONG アクセス用に調整された RAM バッファー。</span><span class="sxs-lookup"><span data-stu-id="b7b69-185">A RAM buffer for reading one sector of flash (512 bytes) and aligned for ULONG access.</span></span>

<span data-ttu-id="b7b69-186">また、ドライバー初期化関数は、**LX_SUCCESS** を返す前に、追加のデバイスまたは実装固有の初期化処理も実行します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-186">The driver initialization function likely also performs additional device and/or implementation-specific initialization duties before returning **LX_SUCCESS**.</span></span>

## <a name="driver-read-sector"></a><span data-ttu-id="b7b69-187">ドライバー読み取りセクター</span><span class="sxs-lookup"><span data-stu-id="b7b69-187">Driver Read Sector</span></span>

<span data-ttu-id="b7b69-188">LevelX NOR ドライバー "読み取りセクター" サービスは、NOR フラッシュの特定のブロック内の特定のセクターを読み取りを実行します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-188">The LevelX NOR driver "read sector" service is responsible for reading a specific sector in a specific block of the NOR flash.</span></span> <span data-ttu-id="b7b69-189">すべてのエラー チェックと修正ロジックは、ドライバー サービスの役割です。</span><span class="sxs-lookup"><span data-stu-id="b7b69-189">All error checking and correcting logic is the responsibility of the driver service.</span></span> <span data-ttu-id="b7b69-190">成功した場合、LevelX NOR ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-190">If successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="b7b69-191">成功しなかった場合、LevelX NOR ドライバーから *LX_ERROR* が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-191">If not successful, the LevelX NOR driver returns *LX_ERROR*.</span></span> <span data-ttu-id="b7b69-192">LevelX NOR ドライバー "読み取りセクター" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-192">The prototype of the LevelX NOR driver "read sector" service is:</span></span>

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

<span data-ttu-id="b7b69-193">ここで、"*flash_address*" は、メモリの NOR フラッシュ ブロック内の論理セクターのアドレスを指定し、"*destination*" は、セクターのコンテンツを配置する場所、"*words*" は読み取る 32 ビット ワードの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-193">Where "*flash_address*" specifies the address of a logical sector within a NOR flash block of memory and "*destination*" and "*words*" specify where to place the sector contents and how many 32-bit words to read.</span></span>

## <a name="driver-write-sector"></a><span data-ttu-id="b7b69-194">ドライバー書き込みセクター</span><span class="sxs-lookup"><span data-stu-id="b7b69-194">Driver Write Sector</span></span>

<span data-ttu-id="b7b69-195">LevelX NOR ドライバー "書き込みセクター" サービスは、特定のセクターを NOR フラッシュのブロックに書き込む処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-195">The LevelX NOR driver "write sector" service is responsible for writing a specific sector into a block of the NOR flash.</span></span> <span data-ttu-id="b7b69-196">すべてのエラー チェックは、ドライバー サービスの役割です。</span><span class="sxs-lookup"><span data-stu-id="b7b69-196">All error checking is the responsibility of the driver service.</span></span> <span data-ttu-id="b7b69-197">成功した場合、LevelX NOR ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-197">If successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="b7b69-198">成功しなかった場合、LevelX NOR ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-198">If not successful, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="b7b69-199">LevelX NOR ドライバー "書き込みセクター" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-199">The prototype of the LevelX NOR driver "write sector" service is:</span></span>

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

<span data-ttu-id="b7b69-200">ここで、"*flash_address*" は、メモリーの NOR フラッシュ ブロック内の論理セクターのアドレスを指定し、"*source*" は書き込みのソース、"*words*" は書き込む 32 ビット ワードの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-200">Where "*flash_address*" specifies the address of a logical sector within a NOR flash block of memory and "*source*" and "*words*" specify the source of the write and how many 32-bit words to write.</span></span>

> [!NOTE]
> <span data-ttu-id="b7b69-201">LevelX は、ドライバーを使用して、書き込みセクターが正常に作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-201">LevelX relies on the driver to verify that the write sector was successful.</span></span> <span data-ttu-id="b7b69-202">通常、これは、プログラミングされた値を読み取って、書き込まれた要求値と照合することで行われます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-202">This is typically done by reading back the programmed value to ensure it matches the requested value to be written.</span></span>

## <a name="driver-block-erase"></a><span data-ttu-id="b7b69-203">ドライバー ブロック消去</span><span class="sxs-lookup"><span data-stu-id="b7b69-203">Driver Block Erase</span></span>

<span data-ttu-id="b7b69-204">LevelX NOR ドライバー "ブロック消去" サービスは、NOR フラッシュの指定されたブロックの消去を実行します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-204">The LevelX NOR driver "block erase" service is responsible for erasing the specified block of the NOR flash.</span></span> <span data-ttu-id="b7b69-205">成功した場合、LevelX NOR ドライバーから **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-205">If successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="b7b69-206">成功しなかった場合、LevelX NOR ドライバーから **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-206">If not successful, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="b7b69-207">LevelX NOR ドライバー "ブロック消去" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-207">The prototype of the LevelX NOR driver "block erase" service is:</span></span>

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

<span data-ttu-id="b7b69-208">ここで、"*block*" は、消去する NOR ブロックを識別します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-208">Where "*block*" identifies which NOR block to erase.</span></span> <span data-ttu-id="b7b69-209">パラメーター "*erase_count*" は診断のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="b7b69-209">The parameter "*erase_count*" is provided for diagnostic purposes.</span></span> <span data-ttu-id="b7b69-210">たとえば、消去数が特定のしきい値を超えた場合、ドライバーは、アプリケーション ソフトウェアの別の部分を警告することがあります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-210">For example, the driver may want to alert another portion of the application software when the erase count exceeds a specific threshold.</span></span>

> [!NOTE]
> <span data-ttu-id="b7b69-211">LevelX はドライバーを使用して、ブロックのすべてのバイトを検査し、それらが確実に消去されるようにします (すべて 1 を含む)。</span><span class="sxs-lookup"><span data-stu-id="b7b69-211">LevelX relies on the driver to examine all bytes of the block to ensure they are erased (contain all ones).</span></span>

## <a name="driver-block-erased-verify"></a><span data-ttu-id="b7b69-212">ドライバー ブロック消去の確認</span><span class="sxs-lookup"><span data-stu-id="b7b69-212">Driver Block Erased Verify</span></span>

<span data-ttu-id="b7b69-213">LevelX NOR ドライバー "ブロック消去の確認" サービスは、NOR フラッシュの指定されたブロックが消去されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-213">The LevelX NOR driver "block erased verify" service is responsible for verifying that the specified block of the NOR flash is erased.</span></span> <span data-ttu-id="b7b69-214">消去されている場合、LevelX NOR ドライバーによって **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-214">If it is erased, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="b7b69-215">ブロックが消去されていない場合、LevelX NOR ドライバーによって **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-215">If the block is not erased, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="b7b69-216">LevelX NOR ドライバー "ブロック消去の確認" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-216">The prototype of the LevelX NOR driver "block erased verify" service is:</span></span>

```c
INT nor_driver_block_erased_verify(ULONG block);
```

<span data-ttu-id="b7b69-217">ここで、"*block*" は、消去されていることを確認するブロックを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-217">Where "*block*" specifies which block to verify that it is erased.</span></span>

> [!NOTE]
> <span data-ttu-id="b7b69-218">LevelX はドライバーを使用して、指定されたすべてのバイトを検査し、それらが確実に消去されるようにします (すべて 1 を含む)。</span><span class="sxs-lookup"><span data-stu-id="b7b69-218">LevelX relies on the driver to examine all bytes of the specified to ensure they are erased (contain all ones).</span></span>

## <a name="driver-system-error"></a><span data-ttu-id="b7b69-219">ドライバー システム エラー</span><span class="sxs-lookup"><span data-stu-id="b7b69-219">Driver System Error</span></span>

<span data-ttu-id="b7b69-220">LevelX NOR ドライバーの "システム エラー ハンドラー" サービスは、LevelX によって検出されたシステム エラーの処理の設定を実行します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-220">The LevelX NOR driver "system error handler" service is responsible for setting handling system errors detected by LevelX.</span></span> <span data-ttu-id="b7b69-221">このルーチンでの処理は、アプリケーションに依存します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-221">The processing in this routine is application dependent.</span></span> <span data-ttu-id="b7b69-222">成功した場合、LevelX NOR ドライバーによって **LX_SUCCESS** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-222">If it is successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="b7b69-223">成功しなかった場合、LevelX NOR ドライバーによって **LX_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-223">If it is not successful, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="b7b69-224">LevelX NOR ドライバー "システム エラー" サービスのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7b69-224">The prototype of the LevelX NOR driver "system error" service is:</span></span>

```c
INT nor_driver_system_error(UINT error_code);
```

<span data-ttu-id="b7b69-225">"*Error_code*" は、発生したエラーを表します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-225">Where "*error_code*" represents the error that occurred.</span></span>

## <a name="nor-simulated-driver"></a><span data-ttu-id="b7b69-226">NOR シミュレート済みドライバー</span><span class="sxs-lookup"><span data-stu-id="b7b69-226">NOR Simulated Driver</span></span>

<span data-ttu-id="b7b69-227">LevelX は、単純に RAM を使用して NOR フラッシュ部分の操作をシミュレートする、シミュレート済み NOR フラッシュ ドライバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-227">LevelX provides a simulated NOR flash driver that simply uses RAM to simulate the operation of a NOR flash part.</span></span> <span data-ttu-id="b7b69-228">既定では、NOR シミュレート済みドライバーは、8 個の NOR フラッシュ ブロックと、ブロックあたり 16 の 512 バイトのセクター提供します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-228">By default, the NOR simulated driver provides 8 NOR flash blocks with 16 512-byte sectors per block.</span></span>

<span data-ttu-id="b7b69-229">シミュレート済み NOR フラッシュ ドライバー初期化関数は、***lx_nor_flash_simulator_initialize** _ であり、_*_lx_nor_flash_simulator.c_\*\* で定義されます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-229">The simulated NOR flash driver initialization function is ***lx_nor_flash_simulator_initialize** _ and is defined in _*_lx_nor_flash_simulator.c_\*\*.</span></span> <span data-ttu-id="b7b69-230">このドライバーは、特定の NOR フラッシュ ドライバーを作成するための便利なテンプレートも提供します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-230">This driver also provides a good template for writing specific NOR flash drivers.</span></span>

## <a name="nor-filex-integration"></a><span data-ttu-id="b7b69-231">NOR FileX の統合</span><span class="sxs-lookup"><span data-stu-id="b7b69-231">NOR FileX Integration</span></span>

<span data-ttu-id="b7b69-232">前述のように、LevelX は操作に FileX を使用しません。</span><span class="sxs-lookup"><span data-stu-id="b7b69-232">As mentioned earlier, LevelX does not rely on FileX for operation.</span></span> <span data-ttu-id="b7b69-233">LevelX によって提供される論理セクターに生データを格納または取得するために、すべての LevelX API は、アプリケーション ソフトウェアによって直接呼び出される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-233">All the LevelX APIs may be called directly by the application software to store/retrieve raw data to the logical sectors provided by LevelX.</span></span> <span data-ttu-id="b7b69-234">ただし、LevelX では FileX もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b7b69-234">However, LevelX also supports FileX.</span></span>

<span data-ttu-id="b7b69-235">ファイル ***fx_nor_flash_simulated_driver .c*** には、NOR フラッシュのシミュレーションで使用する FileX ドライバーの例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7b69-235">The file ***fx_nor_flash_simulated_driver.c*** contains an example FileX driver for use with the NOR flash simulation.</span></span> <span data-ttu-id="b7b69-236">また、LevelX 用の NOR フラッシュ FileX ドライバーは、カスタム FileX ドライバーを作成するための効果的な出発点を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-236">The NOR flash FileX driver for LevelX provides a good starting point for writing custom FileX drivers.</span></span>

> [!NOTE]
> <span data-ttu-id="b7b69-237">FileX NOR フラッシュの形式は、NOR フラッシュで提供されるものよりも小さい、セクターの完全なブロック サイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-237">The FileX NOR flash format should be one full block size of sectors less than the NOR flash provides.</span></span> <span data-ttu-id="b7b69-238">これにより、消耗レベルの処理中に最適なパフォーマンスを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-238">This will help ensure best performance during the wear level processing.</span></span> <span data-ttu-id="b7b69-239">LevelX の消耗平準化アルゴリズムでは、書き込みパフォーマンスを向上させるための追加の手法があります。</span><span class="sxs-lookup"><span data-stu-id="b7b69-239">Additional techniques to improve write performance in the LevelX wear leveling algorithm include:</span></span>
> 1. <span data-ttu-id="b7b69-240">すべての書き込みが、正確に 1 つ以上のクラスターのサイズになり、正確なクラスター境界で開始されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-240">Ensure that all writes are exactly one or more clusters in size and start on exact cluster boundaries.</span></span>
> 2. <span data-ttu-id="b7b69-241">API の FileX ***fx_file_allocate*** クラスを使用して大きなファイル書き込み操作を実行する前に、クラスターを事前に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-241">Pre-allocate clusters before performing large file write operations via the FileX ***fx_file_allocate*** class of APIs.</span></span>
> 3.  <span data-ttu-id="b7b69-242">***Lx_nor_flash_defragment*** を定期的に使用して、可能な限り多くの NOR ブロックを解放し、書き込みパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="b7b69-242">Periodic use of ***lx_nor_flash_defragment*** to free up as many NOR blocks as possible and thus improve write performance.</span></span>
> 4. <span data-ttu-id="b7b69-243">リリース セクター情報を受信するために FileX ドライバーが有効になっていること、およびセクターをリリースするためにドライバーに対して行われた要求が、***lx_nor_flash_sector_release*** を呼び出すことによってドライバーで処理されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7b69-243">Ensure the FileX driver is enabled to receive release sector information and requests made to the driver to release sectors are handled in the driver by calling ***lx_nor_flash_sector_release***.</span></span>
