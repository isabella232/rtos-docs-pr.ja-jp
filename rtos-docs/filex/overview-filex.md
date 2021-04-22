---
title: Azure RTOS FileX を理解する
description: Azure RTO FileX は、ファイル アロケーション テーブル (FAT) 互換のハイ パフォーマンスのファイル システムであり、Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル管理操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。 FileX は、RAM、Azure RTOS USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアをサポートしています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812137"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="642ea-105">Azure RTOS FileX の概要</span><span class="sxs-lookup"><span data-stu-id="642ea-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="642ea-106">Azure RTOS FileX の埋め込みファイル システムは、Microsoft FAT ファイル形式の高度な商用ソリューションであり、深く埋め込まれたリアルタイムの IoT アプリケーション向けに特別に設計されました。</span><span class="sxs-lookup"><span data-stu-id="642ea-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="642ea-107">Azure RTOS FileX では、Microsoft のすべてのファイル形式 (FAT12、FAT16、FAT32、exFAT など) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="642ea-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="642ea-108">FileX では、[Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/) と呼ばれるアドオン製品を使用した省略可能なフォールト トレランスや FLASH 消耗平準化も提供されます。</span><span class="sxs-lookup"><span data-stu-id="642ea-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="642ea-109">これらすべてを小さな占有領域、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS FileX は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="642ea-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="642ea-110">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="642ea-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="642ea-111">Azure RTOS FileX API</span><span class="sxs-lookup"><span data-stu-id="642ea-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="642ea-112">直感的で一貫性のある API</span><span class="sxs-lookup"><span data-stu-id="642ea-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="642ea-113">名詞 - 動詞の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="642ea-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="642ea-114">すべての API の先頭を *fx_* にして FileX として簡単に識別</span><span class="sxs-lookup"><span data-stu-id="642ea-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="642ea-115">ブロックしている API にオプションのスレッド タイムアウトがある</span><span class="sxs-lookup"><span data-stu-id="642ea-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="642ea-116">メディアとファイルを操作するための省略可能なユーザー通知コールバック</span><span class="sxs-lookup"><span data-stu-id="642ea-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="642ea-117">詳細については、「[Azure RTOS FileX ユーザー ガイド](about-this-guide.md)」を参照</span><span class="sxs-lookup"><span data-stu-id="642ea-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="642ea-118">Media Services</span><span class="sxs-lookup"><span data-stu-id="642ea-118">Media Services</span></span>

- <span data-ttu-id="642ea-119">FAT 12/16/32 と exFAT のサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="642ea-120">最小 6 KB のフラッシュ、2.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="642ea-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="642ea-121">完全なメディア アクセス サービス</span><span class="sxs-lookup"><span data-stu-id="642ea-121">Complete media access services</span></span>
- <span data-ttu-id="642ea-122">無制限のメディア インスタンス数</span><span class="sxs-lookup"><span data-stu-id="642ea-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="642ea-123">単純な読み取り/書き込み論理セクター ドライバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="642ea-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="642ea-124">複数パーティションのサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-124">Multiple partition support</span></span>
- <span data-ttu-id="642ea-125">論理セクター キャッシュ</span><span class="sxs-lookup"><span data-stu-id="642ea-125">Logical sector cache</span></span>
- <span data-ttu-id="642ea-126">FAT エントリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="642ea-126">FAT entry cache</span></span>
- <span data-ttu-id="642ea-127">省略可能なフォールト トレランスのサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="642ea-128">セカンダリ FAT の遅延更新</span><span class="sxs-lookup"><span data-stu-id="642ea-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="642ea-129">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="642ea-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="642ea-130">次のような直感的なメディア アクセス API:</span><span class="sxs-lookup"><span data-stu-id="642ea-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="642ea-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="642ea-131">fx_media_open</span></span>
  - <span data-ttu-id="642ea-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="642ea-132">fx_media_close</span></span>
  - <span data-ttu-id="642ea-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="642ea-133">fx_media_format</span></span>
  - <span data-ttu-id="642ea-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="642ea-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="642ea-135">ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="642ea-135">Directory Services</span></span>

- <span data-ttu-id="642ea-136">最大 256 バイトのパス</span><span class="sxs-lookup"><span data-stu-id="642ea-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="642ea-137">長い 8.3 ディレクトリ名をサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="642ea-138">ディレクトリの作成と削除</span><span class="sxs-lookup"><span data-stu-id="642ea-138">Directory create & delete</span></span>
- <span data-ttu-id="642ea-139">ディレクトリの移動と走査</span><span class="sxs-lookup"><span data-stu-id="642ea-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="642ea-140">ディレクトリ属性の管理</span><span class="sxs-lookup"><span data-stu-id="642ea-140">Directory attributes management</span></span>
- <span data-ttu-id="642ea-141">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="642ea-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="642ea-142">次のような直感的なディレクトリ アクセス API:</span><span class="sxs-lookup"><span data-stu-id="642ea-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="642ea-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="642ea-143">fx_directory_create</span></span>
  - <span data-ttu-id="642ea-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="642ea-144">fx_directory_delete</span></span>
  - <span data-ttu-id="642ea-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="642ea-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="642ea-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="642ea-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="642ea-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="642ea-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="642ea-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="642ea-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="642ea-149">ファイル サービス</span><span class="sxs-lookup"><span data-stu-id="642ea-149">File Services</span></span>

- <span data-ttu-id="642ea-150">最小 3.3 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="642ea-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="642ea-151">無制限の開いているファイル数</span><span class="sxs-lookup"><span data-stu-id="642ea-151">Unlimited open files</span></span>
- <span data-ttu-id="642ea-152">読み取り専用ファイルを複数回開くことが可能</span><span class="sxs-lookup"><span data-stu-id="642ea-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="642ea-153">長い 8.3 ディレクトリ名をサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="642ea-154">連続ファイルのサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-154">Contiguous file support</span></span>
- <span data-ttu-id="642ea-155">高速シーク ロジック</span><span class="sxs-lookup"><span data-stu-id="642ea-155">Fast seek logic</span></span>
- <span data-ttu-id="642ea-156">クラスターの事前割り当て</span><span class="sxs-lookup"><span data-stu-id="642ea-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="642ea-157">ファイルの作成、削除、名前の変更</span><span class="sxs-lookup"><span data-stu-id="642ea-157">File create, delete, and rename</span></span>
- <span data-ttu-id="642ea-158">ファイルの読み取り、書き込み、参照</span><span class="sxs-lookup"><span data-stu-id="642ea-158">File read, write, and see</span></span>
- <span data-ttu-id="642ea-159">ファイル属性の管理</span><span class="sxs-lookup"><span data-stu-id="642ea-159">File attributes management</span></span>
- <span data-ttu-id="642ea-160">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="642ea-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="642ea-161">次のような直感的なファイル アクセス API:</span><span class="sxs-lookup"><span data-stu-id="642ea-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="642ea-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="642ea-162">fx_file_create</span></span>
  - <span data-ttu-id="642ea-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="642ea-163">fx_file_delete</span></span>
  - <span data-ttu-id="642ea-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="642ea-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="642ea-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="642ea-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="642ea-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="642ea-166">fx_file_read</span></span>
  - <span data-ttu-id="642ea-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="642ea-167">fx_file_seek</span></span>
  - <span data-ttu-id="642ea-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="642ea-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="642ea-169">小さなメモリ専有領域</span><span class="sxs-lookup"><span data-stu-id="642ea-169">Small-footprint</span></span>

<span data-ttu-id="642ea-170">Azure RTOS FileX の埋め込みファイル システムでは、基本的なファイルの読み取り/書き込みをサポートするために、8.6 KB から 12 KB の非常に小さな最小占有領域が実現されています。</span><span class="sxs-lookup"><span data-stu-id="642ea-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="642ea-171">最小限の Azure RTOS FileX RAM の使用量は、1 メディア インスタンスあたり約 1.8 KB であり、論理セクター キャッシュは 512 バイトのみです。</span><span class="sxs-lookup"><span data-stu-id="642ea-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="642ea-172">Azure RTOS ThreadX と同様に、Azure RTOS FileX のサイズは、アプリケーションで使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="642ea-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="642ea-173">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="642ea-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="642ea-174">高速実行</span><span class="sxs-lookup"><span data-stu-id="642ea-174">Fast execution</span></span>

<span data-ttu-id="642ea-175">Azure RTOS FileX では、論理セクター キャッシュと FAT エントリ キャッシュが提供されます。</span><span class="sxs-lookup"><span data-stu-id="642ea-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="642ea-176">どちらのサイズも、アプリケーションで直接制御されます。</span><span class="sxs-lookup"><span data-stu-id="642ea-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="642ea-177">さらに、Azure RTOS FileX では、連続したクラスターの割り当てと連続したクラスターの読み取り/書き込みも実現されます。</span><span class="sxs-lookup"><span data-stu-id="642ea-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="642ea-178">セクター全体の読み取り/書き込み要求は、アプリケーション バッファーとメディア間で直接実行されます。つまり、中間バッファーは実行されません。</span><span class="sxs-lookup"><span data-stu-id="642ea-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="642ea-179">このように設計された一般的な考え方はすべて、Azure RTOS FileX が最高のパフォーマンスを実現するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="642ea-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="642ea-180">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="642ea-180">Advanced technology</span></span>

<span data-ttu-id="642ea-181">Azure RTOS FileX は、次のような高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="642ea-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="642ea-182">FAT 12/16/32 と exFAT のサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="642ea-183">複数パーティションのサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-183">Multiple partition support</span></span>
- <span data-ttu-id="642ea-184">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="642ea-184">Automatic scaling</span></span>
- <span data-ttu-id="642ea-185">エンディアン ニュートラル</span><span class="sxs-lookup"><span data-stu-id="642ea-185">Endian neutral</span></span>
- <span data-ttu-id="642ea-186">長いファイル名と 8.3 のサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="642ea-187">省略可能なフォールト トレランスのサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="642ea-188">論理セクター キャッシュ</span><span class="sxs-lookup"><span data-stu-id="642ea-188">Logical sector cache</span></span>
- <span data-ttu-id="642ea-189">FAT エントリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="642ea-189">FAT entry cache</span></span>
- <span data-ttu-id="642ea-190">クラスターの事前割り当て</span><span class="sxs-lookup"><span data-stu-id="642ea-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="642ea-191">連続ファイルのサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-191">Contiguous file support</span></span>
- <span data-ttu-id="642ea-192">省略可能なパフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="642ea-192">Optional performance metrics</span></span>
- <span data-ttu-id="642ea-193">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="642ea-194">NOR/NAND 消耗平準化 (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="642ea-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="642ea-195">Azure RTOS LevelX は、Microsoft の NOR/NAND FLASH 消耗平準化製品です。</span><span class="sxs-lookup"><span data-stu-id="642ea-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="642ea-196">Azure RTOS LevelX は、FileX と共に使用することも、アプリケーション用のスタンドアロンの直接読み取り/書き込み FLASH セクター ライブラリとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="642ea-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="642ea-197">市場投入までの時間を短縮</span><span class="sxs-lookup"><span data-stu-id="642ea-197">Fastest time-to-market</span></span>

<span data-ttu-id="642ea-198">Azure RTOS FileX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。</span><span class="sxs-lookup"><span data-stu-id="642ea-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="642ea-199">そのため、Azure RTOS FileX は、埋め込み IoT デバイス用の最も一般的な FAT ファイル システムの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="642ea-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="642ea-200">一貫した市場投入まで時間が利点となる理由の一部は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="642ea-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="642ea-201">質の高いドキュメント - [Azure RTOS FileX ユーザー ガイド](about-this-guide.md)をご覧になり、ご自身でお確かめください。</span><span class="sxs-lookup"><span data-stu-id="642ea-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="642ea-202">完全なソース コードを提供</span><span class="sxs-lookup"><span data-stu-id="642ea-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="642ea-203">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="642ea-203">Easy-to-use API</span></span>
- <span data-ttu-id="642ea-204">包括的かつ高度な機能セット</span><span class="sxs-lookup"><span data-stu-id="642ea-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="642ea-205">TUV と UL による多くの安全性標準による事前認定</span><span class="sxs-lookup"><span data-stu-id="642ea-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="642ea-207">Azure RTOS FileX は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。</span><span class="sxs-lookup"><span data-stu-id="642ea-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="642ea-208">この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で FileX を使用できることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="642ea-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="642ea-209">ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。</span><span class="sxs-lookup"><span data-stu-id="642ea-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="642ea-210">工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="642ea-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU UL 認定":::

<span data-ttu-id="642ea-212">Azure RTOS FileX は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。</span><span class="sxs-lookup"><span data-stu-id="642ea-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="642ea-213">UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。</span><span class="sxs-lookup"><span data-stu-id="642ea-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="642ea-214">TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。</span><span class="sxs-lookup"><span data-stu-id="642ea-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="642ea-215">アプリケーションで追加の認定が必要な場合は、Microsoft を通じて認定サービスを利用し、実際のハードウェア プラットフォームを使用してさまざまな標準にターンキー認定を提供したり、アプリケーション コードをカバーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="642ea-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="642ea-216">シンプルな 1 つのライセンス</span><span class="sxs-lookup"><span data-stu-id="642ea-216">One Simple License</span></span>

<span data-ttu-id="642ea-217">ソース コードの使用とテストに費用はかからず、事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスにはコストがかかりません。その他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="642ea-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="642ea-218">完全な最高品質のソース コード</span><span class="sxs-lookup"><span data-stu-id="642ea-218">Full, highest-quality source code</span></span>

<span data-ttu-id="642ea-219">長年にわたり、Azure RTOS FileX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="642ea-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="642ea-220">また、ファイルごとに 1 つの関数を使用するという規則により、簡単にソースを移動できます。</span><span class="sxs-lookup"><span data-stu-id="642ea-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="642ea-221">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="642ea-221">Supports most popular architectures</span></span>

<span data-ttu-id="642ea-222">Azure RTOS FileX は、すぐに利用可能で完全なテストとサポートが実現されている、最も一般的な 32/64 ビットのマイクロプロセッサで動作します。</span><span class="sxs-lookup"><span data-stu-id="642ea-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="642ea-223">**Analog Devices**: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="642ea-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="642ea-224">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="642ea-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="642ea-225">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="642ea-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="642ea-226">**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="642ea-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="642ea-227">**Cadence**: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="642ea-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="642ea-228">**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="642ea-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="642ea-229">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="642ea-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="642ea-230">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="642ea-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="642ea-231">**Infineon**: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="642ea-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="642ea-232">**Intel**、**Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="642ea-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="642ea-233">**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="642ea-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="642ea-234">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="642ea-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="642ea-235">**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="642ea-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="642ea-236">**Renesas**: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="642ea-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="642ea-237">**Silicon** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="642ea-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="642ea-238">**Synopsys**: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="642ea-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="642ea-239">**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="642ea-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="642ea-240">**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="642ea-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="642ea-241">**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="642ea-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="642ea-242">**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="642ea-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="642ea-243">*表示されるすべてのタイミングとサイズの数値は推定値であり、開発プラットフォームによって異なる場合があります。*</span><span class="sxs-lookup"><span data-stu-id="642ea-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
