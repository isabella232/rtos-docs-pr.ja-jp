---
title: 第 7 章 - Azure RTOS FileX トレース イベント
description: この章では、Azure RTOS FileX イベントについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812308"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="6c9b4-103">第 7 章 - Azure RTOS FileX トレース イベント</span><span class="sxs-lookup"><span data-stu-id="6c9b4-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="6c9b4-104">この章では、Azure RTOS FileX イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="6c9b4-105">イベントとアイコンの一覧</span><span class="sxs-lookup"><span data-stu-id="6c9b4-105">List of Events and Icons</span></span>

<span data-ttu-id="6c9b4-106">**TraceX によって表示される FileX イベントの一覧を次に示します。**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="6c9b4-107">その後に、各イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-107">The following describes each event:</span></span>

| <span data-ttu-id="6c9b4-108">**アイコン**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-108">**Icon**</span></span>                         | <span data-ttu-id="6c9b4-109">**意味**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![内部論理セクターのキャッシュ ミス アイコン](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="6c9b4-111">内部論理セクターのキャッシュ ミス</span><span class="sxs-lookup"><span data-stu-id="6c9b4-111">Internal Logical Sector Cache Miss</span></span> |
| ![内部ディレクトリのキャッシュ ミス アイコン](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="6c9b4-113">内部ディレクトリのキャッシュ ミス</span><span class="sxs-lookup"><span data-stu-id="6c9b4-113">Internal Directory Cache Miss</span></span> |
| ![内部メディアのフラッシュ アイコン](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="6c9b4-115">内部メディアのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-115">Internal Media Flush</span></span> |
| ![内部ディレクトリ エントリの読み取りアイコン](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="6c9b4-117">内部ディレクトリ エントリの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-117">Internal Directory Entry Read</span></span> |
| ![内部ディレクトリ エントリの書き込みアイコン](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="6c9b4-119">内部ディレクトリ エントリの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-119">Internal Directory Entry Write</span></span> |
| ![内部 I / O ドライバーの読み取りアイコン](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="6c9b4-121">内部 I/O ドライバーの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-121">Internal I/O Driver Read</span></span> |
| ![内部 I / O ドライバーの書き込みアイコン](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="6c9b4-123">内部 I/O ドライバーの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-123">Internal I/O Driver Write</span></span> |
| ![内部 I / O ドライバーのフラッシュ アイコン](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="6c9b4-125">内部 I/O ドライバーのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-125">Internal I/O Driver Flush</span></span> |
| ![内部 I / O ドライバーの中止アイコン](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="6c9b4-127">内部 I/O ドライバーの中止</span><span class="sxs-lookup"><span data-stu-id="6c9b4-127">Internal I/O Driver Abort</span></span> |
| ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="6c9b4-129">内部 I/O ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="6c9b4-129">Internal I/O Driver Initialize</span></span> |
| ![内部 I / O ドライバーのブート読み取りアイコン](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="6c9b4-131">内部 I/O ドライバーのブート読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-131">Internal I/O Driver Boot Read</span></span> |
| ![内部 I / O ドライバーのリリース セクター アイコン](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="6c9b4-133">内部 I/O ドライバーのリリース セクター</span><span class="sxs-lookup"><span data-stu-id="6c9b4-133">Internal I/O Driver Release Sectors</span></span> |
| ![内部 I / O ドライバーのブート書き込みアイコン](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="6c9b4-135">内部 I/O ドライバーのブート書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-135">Internal I/O Driver Boot Write</span></span> |
| ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="6c9b4-137">内部 I/O ドライバーの初期化解除</span><span class="sxs-lookup"><span data-stu-id="6c9b4-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![ディレクトリ属性の読み取りアイコン](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="6c9b4-139">**ディレクトリ属性の読み取り** (*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![ディレクトリ属性の設定アイコン](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="6c9b4-141">**ディレクトリ属性の設定** (*fx_directory_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![ディレクトリの作成アイコン](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="6c9b4-143">**ディレクトリの作成** (*fx_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![既定のディレクトリの取得アイコン](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="6c9b4-145">**既定のディレクトリの取得** (*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![既定のディレクトリの設定アイコン](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="6c9b4-147">**既定のディレクトリの設定** (*fx_directory_default_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![ディレクトリの削除アイコン](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="6c9b4-149">**ディレクトリの削除** (*fx_directory_delete*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![ディレクトリの最初のエントリの検索アイコン](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="6c9b4-151">**ディレクトリの最初のエントリの検索** (*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![ディレクトリの最初の完全なエントリの検索アイコン](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="6c9b4-153">**ディレクトリの最初の完全なエントリの検索** (*fx_directory_first_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![ディレクトリ情報の取得アイコン](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="6c9b4-155">**ディレクトリ情報の取得** (*fx_directory_information_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![ディレクトリのローカル パスのクリア アイコン](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="6c9b4-157">**ディレクトリのローカル パスのクリア** (*fx_directory_local_path_clear*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![ディレクトリのローカル パスの取得アイコン](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="6c9b4-159">**ディレクトリのローカル パスの取得** (*fx_directory_local_path_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![ディレクトリのローカル パスの復元アイコン](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="6c9b4-161">**ディレクトリのローカル パスの復元** (*fx_directory_local_path_restore*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![ディレクトリのローカル パスの設定アイコン](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="6c9b4-163">**ディレクトリのローカル パスの設定** (*fx_directory_local_path_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![ディレクトリの長い名前の取得アイコン](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="6c9b4-165">**ディレクトリの長い名前の取得** (*fx_directory_long_name_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![ディレクトリ名のテスト アイコン](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="6c9b4-167">**ディレクトリ名のテスト** (*fx_directory_name_test*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![ディレクトリの次のエントリの検索アイコン](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="6c9b4-169">**ディレクトリの次のエントリの検索** (*fx_directory_next_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![ディレクトリの次の完全なエントリの検索アイコン](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="6c9b4-171">**ディレクトリの次の完全なエントリの検索** (*fx_directory_next_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="6c9b4-173">**ディレクトリ名の変更** (*fx_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![ディレクトリの短い名前の取得アイコン](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="6c9b4-175">**ディレクトリの短い名前の取得** (*fx_directory_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![ファイルの割り当てアイコン](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="6c9b4-177">**ファイルの割り当て** (*fx_file_allocate*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![ファイル属性の読み取りアイコン](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="6c9b4-179">**ファイル属性の読み取り** (*fx_file_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![ファイル属性の設定アイコン](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="6c9b4-181">**ファイル属性の設定** (*fx_file_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![ファイルのベスト エフォート割り当てアイコン](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="6c9b4-183">**ファイルのベスト エフォート割り当て** (*fx_file_best_effort_allocate*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![ファイルを閉じるアイコン](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="6c9b4-185">**ファイルを閉じる** (*fx_file_close*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-185">**File Close** (*fx_file_close*)</span></span> |
| ![ファイルの作成アイコン](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="6c9b4-187">**ファイルの作成** (*fx_file_create*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-187">**File Create** (*fx_file_create*)</span></span> |
| ![ファイルの日時の設定アイコン](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="6c9b4-189">**ファイルの日時の設定** (*fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![ファイルの削除アイコン](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="6c9b4-191">**ファイルの削除** (*fx_file_delete*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![ファイルを開くアイコン](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="6c9b4-193">**ファイルを開く** (*fx_file_open*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-193">**File Open** (*fx_file_open*)</span></span> |
| ![ファイルの読み取りアイコン](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="6c9b4-195">**ファイルの読み取り** (*fx_file_read*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-195">**File Read** (*fx_file_read*)</span></span> |
| ![ファイルの相対シーク アイコン](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="6c9b4-197">**ファイルの相対シーク** (*fx_file_relative_seek*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![ファイル名の変更アイコン](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="6c9b4-199">**ファイル名の変更** (*fx_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![ファイルのシーク アイコン](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="6c9b4-201">**ファイルのシーク** (*fx_file_seek*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![ファイルの切り詰めアイコン](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="6c9b4-203">**ファイルの切り詰め** (*fx_file_truncate*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![ファイルの切り詰め解除アイコン](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="6c9b4-205">**ファイルの切り詰め解除** (*fx_file_truncate_release*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![ファイルの書き込みアイコン](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="6c9b4-207">**ファイルの書き込み** (*fx_file_write*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-207">**File Write** (*fx_file_write*)</span></span> |
| ![メディアの中止アイコン](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="6c9b4-209">**メディアの中止** (*fx_media_abort*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![メディア キャッシュの無効化アイコン](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="6c9b4-211">**メディア キャッシュの無効化** (*fx_media_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![メディアのチェック アイコン](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="6c9b4-213">**メディアのチェック** (*fx_media_check*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\*メディアを閉じるアイコン](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="6c9b4-215">**メディアを閉じる** (*fx_media_close*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-215">**Media Close** (*fx_media_close*)</span></span> |
| ![メディアのフラッシュ アイコン](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="6c9b4-217">**メディアのフラッシュ** (*fx_media_flush*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![メディアのフォーマット アイコン](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="6c9b4-219">**メディアのフォーマット** (*fx_media_format*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-219">**Media Format** (*fx_media_format*)</span></span> |
| ![メディアを開くアイコン](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="6c9b4-221">**メディアを開く** (*fx_media_open*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-221">**Media Open** (*fx_media_open*)</span></span> |
| ![メディアの読み取りアイコン](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="6c9b4-223">**メディアの読み取り** (*fx_media_read*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-223">**Media Read** (*fx_media_read*)</span></span> |
| ![使用可能なメディア領域アイコン](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="6c9b4-225">**使用可能なメディア領域** (*fx_media_space_available*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![メディア ボリュームの取得アイコン](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="6c9b4-227">**メディア ボリュームの取得** (*fx_media_volume_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![メディア ボリュームの設定アイコン](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="6c9b4-229">**メディア ボリュームの設定** (*fx_media_volume_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![メディアの書き込みアイコン](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="6c9b4-231">**メディアの書き込み** (*fx_media_write*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-231">**Media Write** (*fx_media_write*)</span></span> |
| ![システム日付の取得アイコン](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="6c9b4-233">**システム日付の取得** (*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![システム日付の設定アイコン](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="6c9b4-235">**システム日付の設定** (*fx_system_date_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![システムの初期化アイコン](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="6c9b4-237">**システムの初期化** (*fx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![システム時刻の取得アイコン](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="6c9b4-239">**システム時刻の取得** (*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![システム時刻の設定アイコン](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="6c9b4-241">**システム時刻の設定** (*fx_system_time_set*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![Unicode ディレクトリの作成アイコン](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="6c9b4-243">**Unicode ディレクトリの作成** (*fx_unicode_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![Unicode ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="6c9b4-245">**Unicode ディレクトリ名の変更** (*fx_unicode_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![Unicode ファイルの作成アイコン](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="6c9b4-247">**Unicode ファイルの作成** (*fx_unicode_file_create*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![Unicode ファイル名の変更アイコン](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="6c9b4-249">**Unicode ファイル名の変更** (*fx_unicode_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![Unicode の長さの取得アイコン](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="6c9b4-251">**Unicode の長さの取得** (*fx_unicode_length_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![Unicode 名の取得アイコン](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="6c9b4-253">**Unicode 名の取得** (*fx_unicode_name_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![Unicode の短い名前の取得アイコン](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="6c9b4-255">**Unicode の短い名前の取得** (*fx_unicode_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="6c9b4-256">イベントの説明</span><span class="sxs-lookup"><span data-stu-id="6c9b4-256">Event Descriptions</span></span>

<span data-ttu-id="6c9b4-257">以下では個々のイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="6c9b4-258">内部論理セクターのキャッシュ ミス</span><span class="sxs-lookup"><span data-stu-id="6c9b4-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="6c9b4-259">内部論理セクターのキャッシュ ミス</span><span class="sxs-lookup"><span data-stu-id="6c9b4-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="6c9b4-260">**アイコン** ![内部論理セクターのキャッシュ ミス アイコン](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="6c9b4-261">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-261">**Description**</span></span>

<span data-ttu-id="6c9b4-262">このイベントは、内部 FileX 論理セクターのキャッシュ ミスを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="6c9b4-263">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-263">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-264">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-265">情報フィールド 2: セクター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="6c9b4-266">情報フィールド 3: ミスの総数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="6c9b4-267">情報フィールド 4: キャッシュ サイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="6c9b4-268">内部ディレクトリのキャッシュ ミス</span><span class="sxs-lookup"><span data-stu-id="6c9b4-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="6c9b4-269">内部ディレクトリのキャッシュ ミス</span><span class="sxs-lookup"><span data-stu-id="6c9b4-269">Internal directory cache miss</span></span>

<span data-ttu-id="6c9b4-270">**アイコン** ![内部ディレクトリのキャッシュ ミス アイコン](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="6c9b4-271">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-271">**Description**</span></span> 

<span data-ttu-id="6c9b4-272">このイベントは、内部 FileX ディレクトリのキャッシュ ミスを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="6c9b4-273">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-273">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-274">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-275">情報フィールド 2: ミスの総数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="6c9b4-276">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-277">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="6c9b4-278">内部メディアのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="6c9b4-279">内部メディアのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-279">Internal media flush</span></span>

<span data-ttu-id="6c9b4-280">**アイコン** ![内部メディアのフラッシュ アイコン](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="6c9b4-281">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-281">**Description**</span></span>

<span data-ttu-id="6c9b4-282">このイベントは、内部 FileX メディアのフラッシュを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="6c9b4-283">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-283">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-284">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-285">情報フィールド 2: ダーティ セクターの数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="6c9b4-286">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-287">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="6c9b4-288">内部ディレクトリ エントリの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="6c9b4-289">内部ディレクトリ エントリの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-289">Internal directory entry read</span></span>

<span data-ttu-id="6c9b4-290">**アイコン** ![内部ディレクトリ エントリの読み取りアイコン](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="6c9b4-291">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-291">**Description**</span></span>

<span data-ttu-id="6c9b4-292">このイベントは、内部 FileX ディレクトリ エントリの読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="6c9b4-293">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-293">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-294">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-295">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-296">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-297">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="6c9b4-298">内部ディレクトリ エントリの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="6c9b4-299">内部ディレクトリ エントリの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-299">Internal directory entry write</span></span>

<span data-ttu-id="6c9b4-300">**アイコン** ![内部ディレクトリ エントリの書き込みアイコン](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="6c9b4-301">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-301">**Description**</span></span>

<span data-ttu-id="6c9b4-302">このイベントは、内部 FileX ディレクトリ エントリの書き込みイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="6c9b4-303">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-303">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-304">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-305">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-306">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-307">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="6c9b4-308">内部 I/O ドライバーの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="6c9b4-309">内部 I/O ドライバーの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-309">Internal I/O driver read</span></span> 

<span data-ttu-id="6c9b4-310">**アイコン** ![内部 I / O ドライバーの読み取りアイコン](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="6c9b4-311">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-311">**Description**</span></span> 

<span data-ttu-id="6c9b4-312">このイベントは、内部 FileX I/O ドライバーの読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="6c9b4-313">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-313">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-314">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-315">情報フィールド 2: セクター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="6c9b4-316">情報フィールド 3: セクターの数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="6c9b4-317">情報フィールド 4: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="6c9b4-318">内部 I/O ドライバーの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="6c9b4-319">内部 I/O ドライバーの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-319">Internal I/O driver write</span></span> 

<span data-ttu-id="6c9b4-320">**アイコン** ![内部 I / O ドライバーの書き込みアイコン](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="6c9b4-321">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-321">**Description**</span></span> 

<span data-ttu-id="6c9b4-322">このイベントは、内部 FileX I/O ドライバーの書き込みイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="6c9b4-323">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-323">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-324">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-325">情報フィールド 2: セクター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="6c9b4-326">情報フィールド 3: セクターの数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="6c9b4-327">情報フィールド 4: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="6c9b4-328">内部 I/O ドライバーのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="6c9b4-329">内部 I/O ドライバーのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="6c9b4-330">**アイコン** ![内部 I / O ドライバーのフラッシュ アイコン](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="6c9b4-331">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-331">**Description**</span></span> 

<span data-ttu-id="6c9b4-332">このイベントは、内部 FileX I/O ドライバーのフラッシュ イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="6c9b4-333">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-333">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-334">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-335">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-336">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-337">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="6c9b4-338">内部 I/O ドライバーの中止</span><span class="sxs-lookup"><span data-stu-id="6c9b4-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="6c9b4-339">内部 I/O ドライバーの中止</span><span class="sxs-lookup"><span data-stu-id="6c9b4-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="6c9b4-340">**アイコン** ![内部 I / O ドライバーの中止アイコン](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="6c9b4-341">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-341">**Description**</span></span>

<span data-ttu-id="6c9b4-342">このイベントは、内部 FileX I/O ドライバーの中止イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="6c9b4-343">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-343">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-344">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-345">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-346">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-347">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="6c9b4-348">内部 I/O ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="6c9b4-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="6c9b4-349">内部 I/O ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="6c9b4-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="6c9b4-350">**アイコン** ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="6c9b4-351">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-351">**Description**</span></span> 

<span data-ttu-id="6c9b4-352">このイベントは、内部 FileX I/O ドライバーの初期化イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="6c9b4-353">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-353">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-354">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-355">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-356">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-357">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="6c9b4-358">内部 I/O ドライバーのブート セクターの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="6c9b4-359">内部 I/O ドライバーのブート セクターの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="6c9b4-360">**アイコン** ![内部 I / O ドライバーのブート セクターの読み取りアイコン](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="6c9b4-361">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-361">**Description**</span></span> 

<span data-ttu-id="6c9b4-362">このイベントは、内部 FileX I/O ドライバーのブート セクターの読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="6c9b4-363">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-363">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-364">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-365">情報フィールド 2: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="6c9b4-366">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-367">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="6c9b4-368">内部 I/O ドライバーのリリース セクター</span><span class="sxs-lookup"><span data-stu-id="6c9b4-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="6c9b4-369">内部 I/O ドライバーのリリース セクター</span><span class="sxs-lookup"><span data-stu-id="6c9b4-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="6c9b4-370">**アイコン** ![内部 I / O ドライバーのリリース セクター アイコン](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="6c9b4-371">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-371">**Description**</span></span> 

<span data-ttu-id="6c9b4-372">このイベントは、内部 FileX I/O ドライバーのリリース セクター イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="6c9b4-373">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-373">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-374">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-375">情報フィールド 2: セクター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="6c9b4-376">情報フィールド 3: セクターの数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="6c9b4-377">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="6c9b4-378">内部 I/O ドライバーのブート セクターの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="6c9b4-379">内部 I/O ドライバーのブート セクターの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="6c9b4-380">**アイコン** ![内部 I / O ドライバーのブート セクターの書き込みアイコン](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="6c9b4-381">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-381">**Description**</span></span> 

<span data-ttu-id="6c9b4-382">このイベントは、内部 FileX I/O ドライバーのブート セクターの書き込みイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="6c9b4-383">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-383">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-384">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-385">情報フィールド 2: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="6c9b4-386">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-387">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="6c9b4-388">内部 I/O ドライバーの初期化解除</span><span class="sxs-lookup"><span data-stu-id="6c9b4-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="6c9b4-389">内部 I/O ドライバーの初期化解除</span><span class="sxs-lookup"><span data-stu-id="6c9b4-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="6c9b4-390">**アイコン** ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="6c9b4-391">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-391">**Description**</span></span> 

<span data-ttu-id="6c9b4-392">このイベントは、内部 FileX I/O ドライバーの初期化解除イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="6c9b4-393">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-393">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-394">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-395">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-396">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-397">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="6c9b4-398">ディレクトリ属性の読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="6c9b4-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="6c9b4-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="6c9b4-400">**アイコン** ![ディレクトリ属性の読み取りアイコン](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="6c9b4-401">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-401">**Description**</span></span> 

<span data-ttu-id="6c9b4-402">このイベントは、ディレクトリ属性の読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="6c9b4-403">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-403">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-404">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-405">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-406">情報フィールド 3: 属性のビット マップ:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="6c9b4-407">属性</span><span class="sxs-lookup"><span data-stu-id="6c9b4-407">Attribute</span></span>                         | <span data-ttu-id="6c9b4-408">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-409">[読み取り専用]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-409">Read Only</span></span>                        | <span data-ttu-id="6c9b4-410">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-410">(0x01)</span></span>  |
  |  <span data-ttu-id="6c9b4-411">[非表示]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-411">Hidden</span></span>                           | <span data-ttu-id="6c9b4-412">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-412">(0x02)</span></span>  |
  |  <span data-ttu-id="6c9b4-413">システム</span><span class="sxs-lookup"><span data-stu-id="6c9b4-413">System</span></span>                           | <span data-ttu-id="6c9b4-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-414">(0x04)</span></span>  |
  |  <span data-ttu-id="6c9b4-415">ボリューム</span><span class="sxs-lookup"><span data-stu-id="6c9b4-415">Volume</span></span>                           | <span data-ttu-id="6c9b4-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-416">(0x08)</span></span>  |
  |  <span data-ttu-id="6c9b4-417">ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-417">Directory</span></span>                        | <span data-ttu-id="6c9b4-418">(0x10)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-418">(0x10)</span></span>  |
  |  <span data-ttu-id="6c9b4-419">アーカイブ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-419">Archive</span></span>                          | <span data-ttu-id="6c9b4-420">(0x20)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-420">(0x20)</span></span>  |
- <span data-ttu-id="6c9b4-421">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="6c9b4-422">ディレクトリ属性の設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="6c9b4-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="6c9b4-424">**アイコン** ![属性の設定アイコン](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="6c9b4-425">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-425">**Description**</span></span> 

<span data-ttu-id="6c9b4-426">このイベントは、ディレクトリ属性の設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="6c9b4-427">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-427">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-428">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-429">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-430">情報フィールド 3: 属性のビット マップ:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="6c9b4-431">属性</span><span class="sxs-lookup"><span data-stu-id="6c9b4-431">Attribute</span></span>                        | <span data-ttu-id="6c9b4-432">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-433">[読み取り専用]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-433">Read Only</span></span>                        | <span data-ttu-id="6c9b4-434">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-434">(0x01)</span></span>  |
  |  <span data-ttu-id="6c9b4-435">[非表示]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-435">Hidden</span></span>                           | <span data-ttu-id="6c9b4-436">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-436">(0x02)</span></span>  |
  |  <span data-ttu-id="6c9b4-437">システム</span><span class="sxs-lookup"><span data-stu-id="6c9b4-437">System</span></span>                           | <span data-ttu-id="6c9b4-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-438">(0x04)</span></span>  |
  |  <span data-ttu-id="6c9b4-439">アーカイブ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-439">Archive</span></span>                          | <span data-ttu-id="6c9b4-440">(0x20)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-440">(0x20)</span></span>  |
- <span data-ttu-id="6c9b4-441">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="6c9b4-442">ディレクトリの作成</span><span class="sxs-lookup"><span data-stu-id="6c9b4-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="6c9b4-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="6c9b4-443">fx_directory_create</span></span>

<span data-ttu-id="6c9b4-444">**アイコン** ![ディレクトリの作成アイコン](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="6c9b4-445">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-445">**Description**</span></span> 

<span data-ttu-id="6c9b4-446">このイベントは、ディレクトリの作成イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-446">This event represents a directory create event.</span></span>

<span data-ttu-id="6c9b4-447">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-447">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-448">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-449">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-450">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-451">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="6c9b4-452">既定のディレクトリの取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="6c9b4-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-453">fx_directory_default_get</span></span> 

<span data-ttu-id="6c9b4-454">**アイコン** ![既定のディレクトリの取得アイコン](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="6c9b4-455">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-455">**Description**</span></span> 

<span data-ttu-id="6c9b4-456">このイベントは、既定のディレクトリの取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="6c9b4-457">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-457">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-458">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-459">情報フィールド 2: リターン パス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="6c9b4-460">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-461">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="6c9b4-462">既定のディレクトリの設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="6c9b4-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-463">fx_directory_default_set</span></span> 

<span data-ttu-id="6c9b4-464">**アイコン** ![既定のディレクトリの設定アイコン](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="6c9b4-465">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-465">**Description**</span></span> 

<span data-ttu-id="6c9b4-466">このイベントは、既定のディレクトリの設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="6c9b4-467">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-467">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-468">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-469">情報フィールド 2: 新しい既定のパス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="6c9b4-470">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-471">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="6c9b4-472">ディレクトリの削除</span><span class="sxs-lookup"><span data-stu-id="6c9b4-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="6c9b4-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="6c9b4-473">fx_directory_delete</span></span>

<span data-ttu-id="6c9b4-474">**アイコン** ![ディレクトリの削除アイコン](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="6c9b4-475">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-475">**Description**</span></span> 

<span data-ttu-id="6c9b4-476">このイベントは、ディレクトリの削除イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="6c9b4-477">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-477">**Information Fields**</span></span>
- <span data-ttu-id="6c9b4-478">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-479">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-480">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-481">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="6c9b4-482">ディレクトリの最初のエントリの検索</span><span class="sxs-lookup"><span data-stu-id="6c9b4-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="6c9b4-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="6c9b4-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="6c9b4-484">**アイコン** ![ディレクトリの最初のエントリの検索アイコン](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="6c9b4-485">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-485">**Description**</span></span> 

<span data-ttu-id="6c9b4-486">このイベントは、ディレクトリの最初のエントリの検索イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="6c9b4-487">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-487">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-488">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-489">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-490">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-491">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="6c9b4-492">ディレクトリの最初の完全なエントリの検索</span><span class="sxs-lookup"><span data-stu-id="6c9b4-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="6c9b4-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="6c9b4-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="6c9b4-494">**アイコン** ![ディレクトリの最初の完全なエントリの検索アイコン](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="6c9b4-495">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-495">**Description**</span></span> 

<span data-ttu-id="6c9b4-496">このイベントは、ディレクトリの最初の完全なエントリの検索イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="6c9b4-497">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-497">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-498">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-499">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-500">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-501">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="6c9b4-502">ディレクトリ情報の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="6c9b4-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-503">fx_directory_information_get</span></span>

<span data-ttu-id="6c9b4-504">**アイコン** ![ディレクトリ情報の取得アイコン](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="6c9b4-505">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-505">**Description**</span></span> 

<span data-ttu-id="6c9b4-506">このイベントは、ディレクトリ情報の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="6c9b4-507">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-507">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-508">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-509">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-510">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-511">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="6c9b4-512">ディレクトリのローカル パスのクリア</span><span class="sxs-lookup"><span data-stu-id="6c9b4-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="6c9b4-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="6c9b4-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="6c9b4-514">**アイコン** ![ディレクトリのローカル パスのクリア アイコン](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="6c9b4-515">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-515">**Description**</span></span> 

<span data-ttu-id="6c9b4-516">このイベントは、ディレクトリのローカル パスのクリア イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="6c9b4-517">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-517">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-518">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-519">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-520">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-521">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="6c9b4-522">ディレクトリのローカル パスの取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="6c9b4-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="6c9b4-524">**アイコン** ![ディレクトリのローカル パスの取得アイコン](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="6c9b4-525">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-525">**Description**</span></span> 

<span data-ttu-id="6c9b4-526">このイベントは、ディレクトリのローカル パスの取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="6c9b4-527">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-527">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-528">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-529">情報フィールド 2: リターン パス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="6c9b4-530">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-531">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="6c9b4-532">ディレクトリのローカル パスの復元</span><span class="sxs-lookup"><span data-stu-id="6c9b4-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="6c9b4-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="6c9b4-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="6c9b4-534">**アイコン** ![ディレクトリのローカル パスの復元アイコン](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="6c9b4-535">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-535">**Description**</span></span> 

<span data-ttu-id="6c9b4-536">このイベントは、ディレクトリのローカル パスの復元イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="6c9b4-537">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-537">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-538">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-539">情報フィールド 2: ローカル パス構造へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="6c9b4-540">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-541">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="6c9b4-542">ディレクトリのローカル パスの設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="6c9b4-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="6c9b4-544">**アイコン** ![ディレクトリのローカル パスの設定アイコン](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="6c9b4-545">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-545">**Description**</span></span> 

<span data-ttu-id="6c9b4-546">このイベントは、ディレクトリのローカル パスの設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="6c9b4-547">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-547">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-548">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-549">情報フィールド 2: ローカル パス構造へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="6c9b4-550">情報フィールド 3: 新しいパス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="6c9b4-551">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="6c9b4-552">ディレクトリの長い名前の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="6c9b4-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="6c9b4-554">**アイコン** ![ディレクトリの長い名前の取得アイコン](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="6c9b4-555">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-555">**Description**</span></span> 

<span data-ttu-id="6c9b4-556">このイベントは、ディレクトリの長い名前の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="6c9b4-557">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-557">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-558">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-559">情報フィールド 2: 短いファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="6c9b4-560">情報フィールド 3: 長いファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="6c9b4-561">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="6c9b4-562">ディレクトリ名のテスト</span><span class="sxs-lookup"><span data-stu-id="6c9b4-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="6c9b4-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="6c9b4-563">fx_directory_name_test</span></span>

<span data-ttu-id="6c9b4-564">**アイコン** ![ディレクトリ名のテスト アイコン](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="6c9b4-565">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-565">**Description**</span></span> 

<span data-ttu-id="6c9b4-566">このイベントは、ディレクトリ名のテスト イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="6c9b4-567">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-567">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-568">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-569">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-570">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-571">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="6c9b4-572">ディレクトリの次のエントリの検索</span><span class="sxs-lookup"><span data-stu-id="6c9b4-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="6c9b4-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="6c9b4-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="6c9b4-574">**アイコン** ![ディレクトリの次のエントリの検索アイコン](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="6c9b4-575">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-575">**Description**</span></span> 

<span data-ttu-id="6c9b4-576">このイベントは、ディレクトリの次のエントリの検索イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="6c9b4-577">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-577">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-578">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-579">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-580">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-581">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="6c9b4-582">ディレクトリの次の完全なエントリの検索</span><span class="sxs-lookup"><span data-stu-id="6c9b4-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="6c9b4-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="6c9b4-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="6c9b4-584">**アイコン** ![ディレクトリの次の完全なエントリの検索アイコン](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="6c9b4-585">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-585">**Description**</span></span>

<span data-ttu-id="6c9b4-586">このイベントは、ディレクトリの次の完全なエントリの検索イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="6c9b4-587">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-587">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-588">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-589">情報フィールド 2: ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="6c9b4-590">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-591">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="6c9b4-592">ディレクトリ名の変更</span><span class="sxs-lookup"><span data-stu-id="6c9b4-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="6c9b4-593">fx_directory_rename event</span><span class="sxs-lookup"><span data-stu-id="6c9b4-593">fx_directory_rename event</span></span>

<span data-ttu-id="6c9b4-594">**アイコン** ![ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="6c9b4-595">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-595">**Description**</span></span>

<span data-ttu-id="6c9b4-596">このイベントは、ディレクトリ名の変更イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="6c9b4-597">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-597">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-598">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-599">情報フィールド 2: 古いディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="6c9b4-600">情報フィールド 3: 新しいディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="6c9b4-601">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="6c9b4-602">ディレクトリの短い名前の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="6c9b4-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="6c9b4-604">**アイコン** ![ディレクトリの短い名前の取得アイコン](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="6c9b4-605">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-605">**Description**</span></span>

<span data-ttu-id="6c9b4-606">このイベントは、ディレクトリの短い名前の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="6c9b4-607">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-607">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-608">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-609">情報フィールド 2: 長いファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="6c9b4-610">情報フィールド 3: 短いファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="6c9b4-611">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="6c9b4-612">ファイルの割り当て</span><span class="sxs-lookup"><span data-stu-id="6c9b4-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="6c9b4-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="6c9b4-613">fx_file_allocate</span></span>

<span data-ttu-id="6c9b4-614">**アイコン** ![ファイルの割り当てアイコン](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="6c9b4-615">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-615">**Description**</span></span>

<span data-ttu-id="6c9b4-616">このイベントは、ファイルの割り当てイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="6c9b4-617">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-617">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-618">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-619">情報フィールド 2: 要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="6c9b4-620">情報フィールド 3: 現在のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="6c9b4-621">情報フィールド 4: 新しいサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="6c9b4-622">ファイル属性の読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="6c9b4-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="6c9b4-623">fx_file_attributes_read</span></span>

<span data-ttu-id="6c9b4-624">**アイコン** ![ファイル属性の読み取りアイコン](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="6c9b4-625">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-625">**Description**</span></span>

<span data-ttu-id="6c9b4-626">このイベントは、ファイル属性の読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="6c9b4-627">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-627">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-628">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="6c9b4-629">情報フィールド 2: 属性のビット マップ:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="6c9b4-630">属性</span><span class="sxs-lookup"><span data-stu-id="6c9b4-630">Attribut</span></span>                         | <span data-ttu-id="6c9b4-631">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-632">[読み取り専用]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-632">Read Only</span></span>                        | <span data-ttu-id="6c9b4-633">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-633">(0x01)</span></span>  |
  |  <span data-ttu-id="6c9b4-634">[非表示]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-634">Hidden</span></span>                           | <span data-ttu-id="6c9b4-635">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-635">(0x02)</span></span>  |
  |  <span data-ttu-id="6c9b4-636">システム</span><span class="sxs-lookup"><span data-stu-id="6c9b4-636">System</span></span>                           | <span data-ttu-id="6c9b4-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-637">(0x04)</span></span>  |
  |  <span data-ttu-id="6c9b4-638">ボリューム</span><span class="sxs-lookup"><span data-stu-id="6c9b4-638">Volume</span></span>                           | <span data-ttu-id="6c9b4-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-639">(0x08)</span></span>  |
  |  <span data-ttu-id="6c9b4-640">ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-640">Directory</span></span>                        | <span data-ttu-id="6c9b4-641">(0x10)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-641">(0x10)</span></span>  |
  |  <span data-ttu-id="6c9b4-642">アーカイブ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-642">Archive</span></span>                          | <span data-ttu-id="6c9b4-643">(0x20)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-643">(0x20)</span></span>  |
- <span data-ttu-id="6c9b4-644">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-645">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="6c9b4-646">ファイル属性の設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="6c9b4-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-647">fx_file_attributes_set</span></span>

<span data-ttu-id="6c9b4-648">**アイコン** ![ファイル属性の設定アイコン](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="6c9b4-649">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-649">**Description**</span></span> 

<span data-ttu-id="6c9b4-650">このイベントは、ファイル属性の設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="6c9b4-651">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-651">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-652">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-653">情報フィールド 2: ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="6c9b4-654">情報フィールド 3: 属性のビット マップ:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="6c9b4-655">属性</span><span class="sxs-lookup"><span data-stu-id="6c9b4-655">Attribute</span></span>                         | <span data-ttu-id="6c9b4-656">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-657">[読み取り専用]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-657">Read Only</span></span>                        | <span data-ttu-id="6c9b4-658">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-658">(0x01)</span></span>  |
  |  <span data-ttu-id="6c9b4-659">[非表示]</span><span class="sxs-lookup"><span data-stu-id="6c9b4-659">Hidden</span></span>                           | <span data-ttu-id="6c9b4-660">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-660">(0x02)</span></span>  |
  |  <span data-ttu-id="6c9b4-661">システム</span><span class="sxs-lookup"><span data-stu-id="6c9b4-661">System</span></span>                           | <span data-ttu-id="6c9b4-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-662">(0x04)</span></span>  |
  |  <span data-ttu-id="6c9b4-663">アーカイブ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-663">Archive</span></span>                          | <span data-ttu-id="6c9b4-664">(0x20)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-664">(0x20)</span></span>  |
- <span data-ttu-id="6c9b4-665">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="6c9b4-666">ファイルのベスト エフォート割り当て</span><span class="sxs-lookup"><span data-stu-id="6c9b4-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="6c9b4-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="6c9b4-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="6c9b4-668">**アイコン** ![ファイルのベスト エフォート割り当てアイコン](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="6c9b4-669">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-669">**Description**</span></span> 

<span data-ttu-id="6c9b4-670">このイベントは、ファイルのベスト エフォート割り当てイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="6c9b4-671">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-671">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-672">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-673">情報フィールド 2: 要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="6c9b4-674">情報フィールド 3: 割り当てられた実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="6c9b4-675">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="6c9b4-676">ファイルを閉じる</span><span class="sxs-lookup"><span data-stu-id="6c9b4-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="6c9b4-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="6c9b4-677">fx_file_close</span></span>

<span data-ttu-id="6c9b4-678">**アイコン** ![ファイルを閉じるアイコン](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="6c9b4-679">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-679">**Description**</span></span> 

<span data-ttu-id="6c9b4-680">このイベントは、ファイルを閉じるイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-680">This event represents a file close event.</span></span>

<span data-ttu-id="6c9b4-681">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-681">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-682">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-683">情報フィールド 2: ファイル サイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="6c9b4-684">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-685">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="6c9b4-686">ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="6c9b4-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="6c9b4-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="6c9b4-687">fx_file_create</span></span>

<span data-ttu-id="6c9b4-688">**アイコン** ![ファイルの作成アイコン](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="6c9b4-689">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-689">**Description**</span></span>

<span data-ttu-id="6c9b4-690">このイベントは、ファイルの作成イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-690">This event represents a file create event.</span></span>

<span data-ttu-id="6c9b4-691">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-691">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-692">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-693">情報フィールド 2: ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="6c9b4-694">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-695">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="6c9b4-696">ファイルの日時の設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="6c9b4-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-697">fx_file_date_time_set</span></span>

<span data-ttu-id="6c9b4-698">**アイコン** ![ファイルの日時の設定アイコン](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="6c9b4-699">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-699">**Description**</span></span>

<span data-ttu-id="6c9b4-700">このイベントは、ファイルの日時の設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="6c9b4-701">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-701">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-702">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-703">情報フィールド 2: ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="6c9b4-704">情報フィールド 3: 年。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="6c9b4-705">情報フィールド 4: 月。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="6c9b4-706">ファイルの削除</span><span class="sxs-lookup"><span data-stu-id="6c9b4-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="6c9b4-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="6c9b4-707">fx_file_delete</span></span>

<span data-ttu-id="6c9b4-708">**アイコン** ![ファイルの削除アイコン](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="6c9b4-709">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-709">**Description**</span></span>

<span data-ttu-id="6c9b4-710">このイベントは、ファイルの削除イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-710">This event represents a file delete event.</span></span>

<span data-ttu-id="6c9b4-711">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-711">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-712">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-713">情報フィールド 2: ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="6c9b4-714">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-715">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="6c9b4-716">ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="6c9b4-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="6c9b4-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="6c9b4-717">fx_file_open</span></span>

<span data-ttu-id="6c9b4-718">**アイコン** ![ファイルを開くアイコン](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="6c9b4-719">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-719">**Description**</span></span>

<span data-ttu-id="6c9b4-720">このイベントは、ファイルを開くイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-720">This event represents a file open event.</span></span>

<span data-ttu-id="6c9b4-721">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-721">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-722">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-723">情報フィールド 2: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="6c9b4-724">情報フィールド 3: ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="6c9b4-725">情報フィールド 4: 開くの種類:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="6c9b4-726">開くの種類</span><span class="sxs-lookup"><span data-stu-id="6c9b4-726">Open Type</span></span>                        | <span data-ttu-id="6c9b4-727">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-728">読み取り用に開く</span><span class="sxs-lookup"><span data-stu-id="6c9b4-728">Open for Read</span></span>                    | <span data-ttu-id="6c9b4-729">(0x00)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-729">(0x00)</span></span>  |
  |  <span data-ttu-id="6c9b4-730">書き込み用に開く</span><span class="sxs-lookup"><span data-stu-id="6c9b4-730">Open for Write</span></span>                   | <span data-ttu-id="6c9b4-731">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-731">(0x01)</span></span>  |
  |  <span data-ttu-id="6c9b4-732">読み取り用に高速で開く</span><span class="sxs-lookup"><span data-stu-id="6c9b4-732">Fast Open for Read</span></span>               | <span data-ttu-id="6c9b4-733">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="6c9b4-734">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="6c9b4-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="6c9b4-735">fx_file_read</span></span>

<span data-ttu-id="6c9b4-736">**アイコン** ![ファイルの読み取りアイコン](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="6c9b4-737">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-737">**Description**</span></span>

<span data-ttu-id="6c9b4-738">このイベントは、ファイルの読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-738">This event represents a file read event.</span></span>

<span data-ttu-id="6c9b4-739">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-739">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-740">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-741">情報フィールド 2: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="6c9b4-742">情報フィールド 3: 要求サイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="6c9b4-743">情報フィールド 4: 読み取られた実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="6c9b4-744">ファイルの相対シーク</span><span class="sxs-lookup"><span data-stu-id="6c9b4-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="6c9b4-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="6c9b4-745">fx_file_relative_seek</span></span>

<span data-ttu-id="6c9b4-746">**アイコン** ![ファイルの相対シーク アイコン](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="6c9b4-747">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-747">**Description**</span></span>

<span data-ttu-id="6c9b4-748">このイベントは、ファイルの相対シーク イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="6c9b4-749">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-749">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-750">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-751">情報フィールド 2: バイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="6c9b4-752">情報フィールド 3: シークの開始位置:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="6c9b4-753">イベント</span><span class="sxs-lookup"><span data-stu-id="6c9b4-753">Event</span></span>                             | <span data-ttu-id="6c9b4-754">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-755">最初から</span><span class="sxs-lookup"><span data-stu-id="6c9b4-755">From Beginning</span></span>                   | <span data-ttu-id="6c9b4-756">(0x00)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-756">(0x00)</span></span>  |
  |  <span data-ttu-id="6c9b4-757">最後から</span><span class="sxs-lookup"><span data-stu-id="6c9b4-757">From End</span></span>                         | <span data-ttu-id="6c9b4-758">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="6c9b4-759">転送</span><span class="sxs-lookup"><span data-stu-id="6c9b4-759">Forward</span></span>                          | <span data-ttu-id="6c9b4-760">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-760">(0x02)</span></span>  |
  |  <span data-ttu-id="6c9b4-761">移動</span><span class="sxs-lookup"><span data-stu-id="6c9b4-761">Backward</span></span>                         | <span data-ttu-id="6c9b4-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-762">(0x03)</span></span>  |
- <span data-ttu-id="6c9b4-763">情報フィールド 4: 以前のオフセット。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="6c9b4-764">ファイル名の変更</span><span class="sxs-lookup"><span data-stu-id="6c9b4-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="6c9b4-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="6c9b4-765">fx_file_rename</span></span>

<span data-ttu-id="6c9b4-766">**アイコン** ![ファイル名の変更アイコン](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="6c9b4-767">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-767">**Description**</span></span>

<span data-ttu-id="6c9b4-768">このイベントは、ファイル名の変更イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-768">This event represents a file rename event.</span></span>

<span data-ttu-id="6c9b4-769">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-769">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-770">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-771">情報フィールド 2: 古いファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="6c9b4-772">情報フィールド 3: 新しいファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="6c9b4-773">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="6c9b4-774">ファイルのシーク</span><span class="sxs-lookup"><span data-stu-id="6c9b4-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="6c9b4-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="6c9b4-775">fx_file_seek</span></span>

<span data-ttu-id="6c9b4-776">**アイコン** ![ファイルのシーク アイコン](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="6c9b4-777">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-777">**Description**</span></span>

<span data-ttu-id="6c9b4-778">このイベントは、ファイルのシーク イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-778">This event represents a file seek event.</span></span>

<span data-ttu-id="6c9b4-779">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-779">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-780">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-781">情報フィールド 2: バイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="6c9b4-782">情報フィールド 3: 以前のオフセット。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="6c9b4-783">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="6c9b4-784">ファイルの切り詰め</span><span class="sxs-lookup"><span data-stu-id="6c9b4-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="6c9b4-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="6c9b4-785">fx_file_truncate</span></span>

<span data-ttu-id="6c9b4-786">**アイコン** ![ファイルの切り詰めアイコン](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="6c9b4-787">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-787">**Description**</span></span>

<span data-ttu-id="6c9b4-788">このイベントは、ファイルの切り詰めイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="6c9b4-789">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-789">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-790">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-791">情報フィールド 2: 要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="6c9b4-792">情報フィールド 3: 以前のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="6c9b4-793">情報フィールド 4: 新しいサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="6c9b4-794">ファイルの切り詰め解除</span><span class="sxs-lookup"><span data-stu-id="6c9b4-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="6c9b4-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="6c9b4-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="6c9b4-796">**アイコン** ![ファイルの切り詰め解除アイコン](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="6c9b4-797">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-797">**Description**</span></span>

<span data-ttu-id="6c9b4-798">このイベントは、ファイルの切り詰め解除イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="6c9b4-799">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-799">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-800">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-801">情報フィールド 2: 要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="6c9b4-802">情報フィールド 3: 以前のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="6c9b4-803">情報フィールド 4: 新しいサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="6c9b4-804">ファイルの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="6c9b4-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="6c9b4-805">fx_file_write</span></span> 

<span data-ttu-id="6c9b4-806">**アイコン** ![ファイルの書き込みアイコン](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="6c9b4-807">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-807">**Description**</span></span>

<span data-ttu-id="6c9b4-808">このイベントは、ファイルの書き込みイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-808">This event represents a file write event.</span></span>

<span data-ttu-id="6c9b4-809">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-809">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-810">情報フィールド 1: ファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="6c9b4-811">情報フィールド 2: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="6c9b4-812">情報フィールド 3: 要求サイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="6c9b4-813">情報フィールド 4: 書き込まれた実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="6c9b4-814">メディアの中止</span><span class="sxs-lookup"><span data-stu-id="6c9b4-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="6c9b4-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="6c9b4-815">fx_media_abort</span></span> 

<span data-ttu-id="6c9b4-816">**アイコン** ![メディアの中止アイコン](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="6c9b4-817">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-817">**Description**</span></span>

<span data-ttu-id="6c9b4-818">このイベントは、メディアの中止イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-818">This event represents a media abort event.</span></span>

<span data-ttu-id="6c9b4-819">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-819">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-820">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-821">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-822">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-823">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="6c9b4-824">メディア キャッシュの無効化</span><span class="sxs-lookup"><span data-stu-id="6c9b4-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="6c9b4-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="6c9b4-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="6c9b4-826">**アイコン** ![メディア キャッシュの無効化アイコン](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="6c9b4-827">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-827">**Description**</span></span>

<span data-ttu-id="6c9b4-828">このイベントは、メディア キャッシュの無効化イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="6c9b4-829">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-829">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-830">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-831">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-832">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-833">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="6c9b4-834">メディアのチェック</span><span class="sxs-lookup"><span data-stu-id="6c9b4-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="6c9b4-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="6c9b4-835">fx_media_check</span></span>

<span data-ttu-id="6c9b4-836">**アイコン** ![メディアのチェック アイコン](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="6c9b4-837">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-837">**Description**</span></span>

<span data-ttu-id="6c9b4-838">このイベントは、メディアのチェック イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-838">This event represents a media check event.</span></span>

<span data-ttu-id="6c9b4-839">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-839">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-840">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-841">情報フィールド 2: スクラッチ メモリのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="6c9b4-842">情報フィールド 3: スクラッチ メモリのサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="6c9b4-843">情報フィールド 4: エラーのビット マップ:</span><span class="sxs-lookup"><span data-stu-id="6c9b4-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="6c9b4-844">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="6c9b4-844">Error type</span></span>                        | <span data-ttu-id="6c9b4-845">値</span><span class="sxs-lookup"><span data-stu-id="6c9b4-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="6c9b4-846">FAT チェーン エラー</span><span class="sxs-lookup"><span data-stu-id="6c9b4-846">FAT Chain Error</span></span>                  | <span data-ttu-id="6c9b4-847">(0x01)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-847">(0x01)</span></span>  |
  |  <span data-ttu-id="6c9b4-848">ディレクトリ エラー</span><span class="sxs-lookup"><span data-stu-id="6c9b4-848">Directory Error</span></span>                  | <span data-ttu-id="6c9b4-849">(0x02)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-849">(0x02)</span></span>  |
  |  <span data-ttu-id="6c9b4-850">破損クラスター エラー</span><span class="sxs-lookup"><span data-stu-id="6c9b4-850">Lost Cluster Error</span></span>               | <span data-ttu-id="6c9b4-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-851">(0x04)</span></span>  |
  |  <span data-ttu-id="6c9b4-852">ファイル サイズ エラー</span><span class="sxs-lookup"><span data-stu-id="6c9b4-852">File Size Error</span></span>                  | <span data-ttu-id="6c9b4-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="6c9b4-854">メディアを閉じる</span><span class="sxs-lookup"><span data-stu-id="6c9b4-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="6c9b4-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="6c9b4-855">fx_media_close</span></span>

<span data-ttu-id="6c9b4-856">**アイコン** ![メディアを閉じるアイコン](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="6c9b4-857">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-857">**Description**</span></span>

<span data-ttu-id="6c9b4-858">このイベントは、メディアを閉じるイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-858">This event represents a media close event.</span></span>

<span data-ttu-id="6c9b4-859">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-859">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-860">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-861">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-862">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-863">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="6c9b4-864">メディアのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="6c9b4-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="6c9b4-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="6c9b4-865">fx_media_flush</span></span>

<span data-ttu-id="6c9b4-866">**アイコン** ![メディアのフラッシュ アイコン](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="6c9b4-867">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-867">**Description**</span></span>

<span data-ttu-id="6c9b4-868">このイベントは、メディアのフラッシュ イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-868">This event represents a media flush event.</span></span>

<span data-ttu-id="6c9b4-869">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-869">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-870">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-871">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-872">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-873">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="6c9b4-874">メディアのフォーマット</span><span class="sxs-lookup"><span data-stu-id="6c9b4-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="6c9b4-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="6c9b4-875">fx_media_format</span></span>

<span data-ttu-id="6c9b4-876">**アイコン** ![メディアのフォーマット アイコン](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="6c9b4-877">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-877">**Description**</span></span>

<span data-ttu-id="6c9b4-878">このイベントは、メディアのフォーマット イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-878">This event represents a media format event.</span></span>

<span data-ttu-id="6c9b4-879">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-879">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-880">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-881">情報フィールド 2: ルート エントリの数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="6c9b4-882">情報フィールド 3: セクター数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="6c9b4-883">情報フィールド 4: クラスターあたりのセクター数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="6c9b4-884">メディアを開く</span><span class="sxs-lookup"><span data-stu-id="6c9b4-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="6c9b4-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="6c9b4-885">fx_media_open</span></span>

<span data-ttu-id="6c9b4-886">**アイコン** ![メディアを開くアイコン](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="6c9b4-887">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-887">**Description**</span></span>

<span data-ttu-id="6c9b4-888">このイベントは、メディアを開くイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-888">This event represents a media open event.</span></span>

<span data-ttu-id="6c9b4-889">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-889">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-890">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-891">情報フィールド 2: メディア ドライバー エントリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="6c9b4-892">情報フィールド 3: メモリ ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="6c9b4-893">情報フィールド 4: メモリ サイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="6c9b4-894">メディアの読み取り</span><span class="sxs-lookup"><span data-stu-id="6c9b4-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="6c9b4-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="6c9b4-895">fx_media_read</span></span>

<span data-ttu-id="6c9b4-896">**アイコン** ![メディアの読み取りアイコン](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="6c9b4-897">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-897">**Description**</span></span>

<span data-ttu-id="6c9b4-898">このイベントは、メディアの読み取りイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-898">This event represents a media read event.</span></span>

<span data-ttu-id="6c9b4-899">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-899">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-900">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-901">情報フィールド 2: 論理セクター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="6c9b4-902">情報フィールド 3: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="6c9b4-903">情報フィールド 4: 読み取りバイト数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="6c9b4-904">使用可能なメディア領域</span><span class="sxs-lookup"><span data-stu-id="6c9b4-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="6c9b4-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="6c9b4-905">fx_media_space_available</span></span>

<span data-ttu-id="6c9b4-906">**アイコン** ![使用可能なメディア領域アイコン](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="6c9b4-907">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-907">**Description**</span></span>

<span data-ttu-id="6c9b4-908">このイベントは、使用可能なメディア領域イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-908">This event represents a media space available event.</span></span>

<span data-ttu-id="6c9b4-909">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-909">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-910">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-911">情報フィールド 2: 使用可能なバイト数ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="6c9b4-912">情報フィールド 3: 空きクラスターの数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="6c9b4-913">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="6c9b4-914">メディア ボリュームの取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="6c9b4-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-915">fx_media_volume_get</span></span>

<span data-ttu-id="6c9b4-916">**アイコン** ![メディア ボリュームの取得アイコン](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="6c9b4-917">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-917">**Description**</span></span>

<span data-ttu-id="6c9b4-918">このイベントは、メディア ボリュームの取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="6c9b4-919">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-919">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-920">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-921">情報フィールド 2: ボリューム名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="6c9b4-922">情報フィールド 3: ボリューム ソース。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="6c9b4-923">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="6c9b4-924">メディア ボリュームの設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="6c9b4-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-925">fx_media_volume_set</span></span>

<span data-ttu-id="6c9b4-926">**アイコン** ![メディア ボリュームの設定アイコン](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="6c9b4-927">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-927">**Description**</span></span>

<span data-ttu-id="6c9b4-928">このイベントは、メディア ボリュームの設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="6c9b4-929">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-929">**Information Fields**</span></span> 
- <span data-ttu-id="6c9b4-930">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-931">情報フィールド 2: ボリューム名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="6c9b4-932">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-933">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="6c9b4-934">メディアの書き込み</span><span class="sxs-lookup"><span data-stu-id="6c9b4-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="6c9b4-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="6c9b4-935">fx_media_write</span></span>

<span data-ttu-id="6c9b4-936">**アイコン** ![メディアの書き込みアイコン](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="6c9b4-937">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-937">**Description**</span></span>

<span data-ttu-id="6c9b4-938">このイベントは、メディアの書き込みイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-938">This event represents a media write event.</span></span>

<span data-ttu-id="6c9b4-939">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-939">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-940">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-941">情報フィールド 2: 論理セクター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="6c9b4-942">情報フィールド 3: バッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="6c9b4-943">情報フィールド 4: 書き込みバイト数。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="6c9b4-944">システム日付の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="6c9b4-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-945">fx_system_date_get</span></span> 

<span data-ttu-id="6c9b4-946">**アイコン** ![システム日付の取得アイコン](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="6c9b4-947">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-947">**Description**</span></span>

<span data-ttu-id="6c9b4-948">このイベントは、システム日付の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-948">This event represents a system date get event.</span></span>

<span data-ttu-id="6c9b4-949">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-949">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-950">情報フィールド 1: 年。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="6c9b4-951">情報フィールド 2: 月。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="6c9b4-952">情報フィールド 3: 日。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="6c9b4-953">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="6c9b4-954">システム日付の設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="6c9b4-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-955">fx_system_date_set</span></span> 

<span data-ttu-id="6c9b4-956">**アイコン** ![システム日付の設定アイコン](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="6c9b4-957">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-957">**Description**</span></span>

<span data-ttu-id="6c9b4-958">このイベントは、システム日付の設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-958">This event represents a system date set event.</span></span>

<span data-ttu-id="6c9b4-959">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-959">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-960">情報フィールド 1: 年。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="6c9b4-961">情報フィールド 2: 月。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="6c9b4-962">情報フィールド 3: 日。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="6c9b4-963">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="6c9b4-964">システムの初期化</span><span class="sxs-lookup"><span data-stu-id="6c9b4-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="6c9b4-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="6c9b4-965">fx_system_initialize</span></span> 

<span data-ttu-id="6c9b4-966">**アイコン** ![システムの初期化アイコン](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="6c9b4-967">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-967">**Description**</span></span>

<span data-ttu-id="6c9b4-968">このイベントは、システムの初期化イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="6c9b4-969">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-969">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-970">情報フィールド 1: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="6c9b4-971">情報フィールド 2: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="6c9b4-972">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-973">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="6c9b4-974">システム時刻の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="6c9b4-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-975">fx_system_time_get</span></span> 

<span data-ttu-id="6c9b4-976">**アイコン** ![システム時刻の取得アイコン](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="6c9b4-977">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-977">**Description**</span></span>

<span data-ttu-id="6c9b4-978">このイベントは、システム時刻の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-978">This event represents a system time get event.</span></span>

<span data-ttu-id="6c9b4-979">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-979">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-980">情報フィールド 1: 時。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="6c9b4-981">情報フィールド 2: 分。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="6c9b4-982">情報フィールド 3: 秒。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="6c9b4-983">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="6c9b4-984">システム時刻の設定</span><span class="sxs-lookup"><span data-stu-id="6c9b4-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="6c9b4-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="6c9b4-985">fx_system_time_set</span></span> 

<span data-ttu-id="6c9b4-986">**アイコン** ![システム時刻の設定アイコン](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="6c9b4-987">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-987">**Description**</span></span>

<span data-ttu-id="6c9b4-988">このイベントは、システム時刻の設定イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-988">This event represents a system time set event.</span></span>

<span data-ttu-id="6c9b4-989">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-989">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-990">情報フィールド 1: 時。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="6c9b4-991">情報フィールド 2: 分。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="6c9b4-992">情報フィールド 3: 秒。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="6c9b4-993">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="6c9b4-994">Unicode ディレクトリの作成</span><span class="sxs-lookup"><span data-stu-id="6c9b4-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="6c9b4-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="6c9b4-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="6c9b4-996">**アイコン** ![Unicode ディレクトリの作成アイコン](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="6c9b4-997">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-997">**Description**</span></span>

<span data-ttu-id="6c9b4-998">このイベントは、Unicode ディレクトリの作成イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="6c9b4-999">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-999">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-1000">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-1001">情報フィールド 2: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1002">情報フィールド 3: Unicode 名のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1003">情報フィールド 4: 短い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="6c9b4-1004">Unicode ディレクトリ名の変更</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="6c9b4-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="6c9b4-1006">**アイコン** ![Unicode ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="6c9b4-1007">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1007">**Description**</span></span>

<span data-ttu-id="6c9b4-1008">このイベントは、Unicode ディレクトリ名の変更イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="6c9b4-1009">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1009">**Information Fields**</span></span> 

- <span data-ttu-id="6c9b4-1010">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-1011">情報フィールド 2: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1012">情報フィールド 3: Unicode 名のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1013">情報フィールド 4: 短い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="6c9b4-1014">Unicode ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="6c9b4-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="6c9b4-1016">**アイコン** ![Unicode ファイルの作成アイコン](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="6c9b4-1017">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1017">**Description**</span></span>

<span data-ttu-id="6c9b4-1018">このイベントは、Unicode ファイルの作成イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="6c9b4-1019">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1019">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-1020">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-1021">情報フィールド 2: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1022">情報フィールド 3: Unicode 名のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1023">情報フィールド 4: 短い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="6c9b4-1024">Unicode ファイル名の変更</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="6c9b4-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="6c9b4-1026">**アイコン** ![Unicode ファイル名の変更アイコン](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="6c9b4-1027">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1027">**Description**</span></span>

<span data-ttu-id="6c9b4-1028">このイベントは、Unicode ファイル名の変更イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="6c9b4-1029">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1029">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-1030">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-1031">情報フィールド 2: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1032">情報フィールド 3: Unicode 名のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1033">情報フィールド 4: 短い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="6c9b4-1034">Unicode の長さの取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="6c9b4-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="6c9b4-1036">**アイコン** ![Unicode の長さの取得アイコン](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="6c9b4-1037">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1037">**Description**</span></span>

<span data-ttu-id="6c9b4-1038">このイベントは、Unicode の長さの取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="6c9b4-1039">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1039">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-1040">情報フィールド 1: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1041">情報フィールド 2: 長さ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="6c9b4-1042">情報フィールド 3: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="6c9b4-1043">情報フィールド 4: 使用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="6c9b4-1044">Unicode 名の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="6c9b4-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="6c9b4-1046">**アイコン** ![Unicode 名の取得アイコン](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="6c9b4-1047">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1047">**Description**</span></span>

<span data-ttu-id="6c9b4-1048">このイベントは、Unicode 名の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="6c9b4-1049">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1049">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-1050">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-1051">情報フィールド 2: ソースの短い名前。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="6c9b4-1052">情報フィールド 3: ターゲットの Unicode 名ポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="6c9b4-1053">情報フィールド 4: ターゲットの Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="6c9b4-1054">Unicode の短い名前の取得</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="6c9b4-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="6c9b4-1056">**アイコン** ![Unicode の短い名前の取得アイコン](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="6c9b4-1057">**説明**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1057">**Description**</span></span>

<span data-ttu-id="6c9b4-1058">このイベントは、Unicode の短い名前の取得イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="6c9b4-1059">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1059">**Information Fields**</span></span>

- <span data-ttu-id="6c9b4-1060">情報フィールド 1: メディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="6c9b4-1061">情報フィールド 2: ソースの Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1062">情報フィールド 3: Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="6c9b4-1063">情報フィールド 4: 短い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c9b4-1063">Info Field 4: Pointer to short name.</span></span>