---
title: Azure RTOS FileX を理解する
description: Azure RTO FileX は、ファイル アロケーション テーブル (FAT) 互換のハイ パフォーマンスのファイル システムであり、Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル管理操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。 FileX は、RAM、Azure RTOS USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアをサポートしています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171354"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="28d14-105">Azure RTOS FileX の概要</span><span class="sxs-lookup"><span data-stu-id="28d14-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="28d14-106">Azure RTOS FileX の埋め込みファイル システムは、Microsoft FAT ファイル形式の高度な商用ソリューションであり、深く埋め込まれたリアルタイムの IoT アプリケーション向けに特別に設計されました。</span><span class="sxs-lookup"><span data-stu-id="28d14-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="28d14-107">Azure RTOS FileX では、Microsoft のすべてのファイル形式 (FAT12、FAT16、FAT32、exFAT など) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="28d14-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="28d14-108">FileX では、[Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/) と呼ばれるアドオン製品を使用した省略可能なフォールト トレランスや FLASH 消耗平準化も提供されます。</span><span class="sxs-lookup"><span data-stu-id="28d14-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="28d14-109">これらすべてを小さな占有領域、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS FileX は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="28d14-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="28d14-110">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="28d14-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="28d14-111">Media Services</span><span class="sxs-lookup"><span data-stu-id="28d14-111">Media Services</span></span>

- <span data-ttu-id="28d14-112">FAT 12/16/32 と exFAT のサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="28d14-113">最小 6 KB のフラッシュ、2.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="28d14-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="28d14-114">完全なメディア アクセス サービス</span><span class="sxs-lookup"><span data-stu-id="28d14-114">Complete media access services</span></span>
- <span data-ttu-id="28d14-115">無制限のメディア インスタンス数</span><span class="sxs-lookup"><span data-stu-id="28d14-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="28d14-116">単純な読み取り/書き込み論理セクター ドライバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28d14-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="28d14-117">複数パーティションのサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-117">Multiple partition support</span></span>
- <span data-ttu-id="28d14-118">論理セクター キャッシュ</span><span class="sxs-lookup"><span data-stu-id="28d14-118">Logical sector cache</span></span>
- <span data-ttu-id="28d14-119">FAT エントリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="28d14-119">FAT entry cache</span></span>
- <span data-ttu-id="28d14-120">省略可能なフォールト トレランスのサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="28d14-121">セカンダリ FAT の遅延更新</span><span class="sxs-lookup"><span data-stu-id="28d14-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="28d14-122">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="28d14-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="28d14-123">次のような直感的なメディア アクセス API:</span><span class="sxs-lookup"><span data-stu-id="28d14-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="28d14-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="28d14-124">fx_media_open</span></span>
  - <span data-ttu-id="28d14-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="28d14-125">fx_media_close</span></span>
  - <span data-ttu-id="28d14-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="28d14-126">fx_media_format</span></span>
  - <span data-ttu-id="28d14-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="28d14-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="28d14-128">ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="28d14-128">Directory Services</span></span>

- <span data-ttu-id="28d14-129">最大 256 バイトのパス</span><span class="sxs-lookup"><span data-stu-id="28d14-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="28d14-130">長い 8.3 ディレクトリ名をサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="28d14-131">ディレクトリの作成と削除</span><span class="sxs-lookup"><span data-stu-id="28d14-131">Directory create & delete</span></span>
- <span data-ttu-id="28d14-132">ディレクトリの移動と走査</span><span class="sxs-lookup"><span data-stu-id="28d14-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="28d14-133">ディレクトリ属性の管理</span><span class="sxs-lookup"><span data-stu-id="28d14-133">Directory attributes management</span></span>
- <span data-ttu-id="28d14-134">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="28d14-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="28d14-135">次のような直感的なディレクトリ アクセス API:</span><span class="sxs-lookup"><span data-stu-id="28d14-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="28d14-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="28d14-136">fx_directory_create</span></span>
  - <span data-ttu-id="28d14-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="28d14-137">fx_directory_delete</span></span>
  - <span data-ttu-id="28d14-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="28d14-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="28d14-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="28d14-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="28d14-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="28d14-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="28d14-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="28d14-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="28d14-142">ファイル サービス</span><span class="sxs-lookup"><span data-stu-id="28d14-142">File Services</span></span>

- <span data-ttu-id="28d14-143">最小 3.3 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="28d14-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="28d14-144">無制限の開いているファイル数</span><span class="sxs-lookup"><span data-stu-id="28d14-144">Unlimited open files</span></span>
- <span data-ttu-id="28d14-145">読み取り専用ファイルを複数回開くことが可能</span><span class="sxs-lookup"><span data-stu-id="28d14-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="28d14-146">長い 8.3 ディレクトリ名をサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="28d14-147">連続ファイルのサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-147">Contiguous file support</span></span>
- <span data-ttu-id="28d14-148">高速シーク ロジック</span><span class="sxs-lookup"><span data-stu-id="28d14-148">Fast seek logic</span></span>
- <span data-ttu-id="28d14-149">クラスターの事前割り当て</span><span class="sxs-lookup"><span data-stu-id="28d14-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="28d14-150">ファイルの作成、削除、名前の変更</span><span class="sxs-lookup"><span data-stu-id="28d14-150">File create, delete, and rename</span></span>
- <span data-ttu-id="28d14-151">ファイルの読み取り、書き込み、参照</span><span class="sxs-lookup"><span data-stu-id="28d14-151">File read, write, and see</span></span>
- <span data-ttu-id="28d14-152">ファイル属性の管理</span><span class="sxs-lookup"><span data-stu-id="28d14-152">File attributes management</span></span>
- <span data-ttu-id="28d14-153">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="28d14-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="28d14-154">次のような直感的なファイル アクセス API:</span><span class="sxs-lookup"><span data-stu-id="28d14-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="28d14-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="28d14-155">fx_file_create</span></span>
  - <span data-ttu-id="28d14-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="28d14-156">fx_file_delete</span></span>
  - <span data-ttu-id="28d14-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="28d14-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="28d14-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="28d14-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="28d14-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="28d14-159">fx_file_read</span></span>
  - <span data-ttu-id="28d14-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="28d14-160">fx_file_seek</span></span>
  - <span data-ttu-id="28d14-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="28d14-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="28d14-162">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="28d14-162">Advanced technology</span></span>

<span data-ttu-id="28d14-163">Azure RTOS FileX は、次のような高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="28d14-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="28d14-164">FAT 12/16/32 と exFAT のサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="28d14-165">複数パーティションのサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-165">Multiple partition support</span></span>
- <span data-ttu-id="28d14-166">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="28d14-166">Automatic scaling</span></span>
- <span data-ttu-id="28d14-167">エンディアン ニュートラル</span><span class="sxs-lookup"><span data-stu-id="28d14-167">Endian neutral</span></span>
- <span data-ttu-id="28d14-168">長いファイル名と 8.3 のサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="28d14-169">省略可能なフォールト トレランスのサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="28d14-170">論理セクター キャッシュ</span><span class="sxs-lookup"><span data-stu-id="28d14-170">Logical sector cache</span></span>
- <span data-ttu-id="28d14-171">FAT エントリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="28d14-171">FAT entry cache</span></span>
- <span data-ttu-id="28d14-172">クラスターの事前割り当て</span><span class="sxs-lookup"><span data-stu-id="28d14-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="28d14-173">連続ファイルのサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-173">Contiguous file support</span></span>
- <span data-ttu-id="28d14-174">省略可能なパフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="28d14-174">Optional performance metrics</span></span>
- <span data-ttu-id="28d14-175">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="28d14-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="28d14-176">NOR/NAND 消耗平準化 (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="28d14-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="28d14-177">Azure RTOS LevelX は、Microsoft の NOR/NAND FLASH 消耗平準化製品です。</span><span class="sxs-lookup"><span data-stu-id="28d14-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="28d14-178">Azure RTOS LevelX は、FileX と共に使用することも、アプリケーション用のスタンドアロンの直接読み取り/書き込み FLASH セクター ライブラリとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="28d14-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
