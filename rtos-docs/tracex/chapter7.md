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
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>第 7 章 - Azure RTOS FileX トレース イベント

この章では、Azure RTOS FileX イベントについて説明します。 

## <a name="list-of-events-and-icons"></a>イベントとアイコンの一覧

**TraceX によって表示される FileX イベントの一覧を次に示します。**

その後に、各イベントについて説明します。

| **アイコン**                         | **意味**                               |
| -------------------------------- | ----------------------------------------- |
| ![内部論理セクターのキャッシュ ミス アイコン](./media/user-guide/fx-events/image1.png)    | 内部論理セクターのキャッシュ ミス |
| ![内部ディレクトリのキャッシュ ミス アイコン](./media/user-guide/fx-events/image2.png)    | 内部ディレクトリのキャッシュ ミス |
| ![内部メディアのフラッシュ アイコン](./media/user-guide/fx-events/image3.png)    | 内部メディアのフラッシュ |
| ![内部ディレクトリ エントリの読み取りアイコン](./media/user-guide/fx-events/image4.png)    | 内部ディレクトリ エントリの読み取り |
| ![内部ディレクトリ エントリの書き込みアイコン](./media/user-guide/fx-events/image5.png)    | 内部ディレクトリ エントリの書き込み |
| ![内部 I / O ドライバーの読み取りアイコン](./media/user-guide/fx-events/image6.png)    | 内部 I/O ドライバーの読み取り |
| ![内部 I / O ドライバーの書き込みアイコン](./media/user-guide/fx-events/image7.png)    | 内部 I/O ドライバーの書き込み |
| ![内部 I / O ドライバーのフラッシュ アイコン](./media/user-guide/fx-events/image8.png)    | 内部 I/O ドライバーのフラッシュ |
| ![内部 I / O ドライバーの中止アイコン](./media/user-guide/fx-events/image9.png)    | 内部 I/O ドライバーの中止 |
| ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/fx-events/image10.png)    | 内部 I/O ドライバーの初期化 |
| ![内部 I / O ドライバーのブート読み取りアイコン](./media/user-guide/fx-events/image11.png)    | 内部 I/O ドライバーのブート読み取り |
| ![内部 I / O ドライバーのリリース セクター アイコン](./media/user-guide/fx-events/image12.png)    | 内部 I/O ドライバーのリリース セクター |
| ![内部 I / O ドライバーのブート書き込みアイコン](./media/user-guide/fx-events/image13.png)    | 内部 I/O ドライバーのブート書き込み |
| ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/fx-events/image14.png)    | 内部 I/O ドライバーの初期化解除 |
| ![ディレクトリ属性の読み取りアイコン](./media/user-guide/fx-events/image15.png)    | **ディレクトリ属性の読み取り** (*fx_directory_attributes_read*) |
| ![ディレクトリ属性の設定アイコン](./media/user-guide/fx-events/image16.png)    | **ディレクトリ属性の設定** (*fx_directory_attributes_set*) |
| ![ディレクトリの作成アイコン](./media/user-guide/fx-events/image17.png)    | **ディレクトリの作成** (*fx_directory_create*) |
| ![既定のディレクトリの取得アイコン](./media/user-guide/fx-events/image18.png)    | **既定のディレクトリの取得** (*fx_directory_default_get*) |
| ![既定のディレクトリの設定アイコン](./media/user-guide/fx-events/image19.png)    | **既定のディレクトリの設定** (*fx_directory_default_set*) |
| ![ディレクトリの削除アイコン](./media/user-guide/fx-events/image20.png)    | **ディレクトリの削除** (*fx_directory_delete*) |
| ![ディレクトリの最初のエントリの検索アイコン](./media/user-guide/fx-events/image21.png)    | **ディレクトリの最初のエントリの検索** (*fx_directory_first_entry_find*) |
| ![ディレクトリの最初の完全なエントリの検索アイコン](./media/user-guide/fx-events/image22.png)    | **ディレクトリの最初の完全なエントリの検索** (*fx_directory_first_full_entry_find*) |
| ![ディレクトリ情報の取得アイコン](./media/user-guide/fx-events/image23.png)    | **ディレクトリ情報の取得** (*fx_directory_information_get*) |
| ![ディレクトリのローカル パスのクリア アイコン](./media/user-guide/fx-events/image24.png)    | **ディレクトリのローカル パスのクリア** (*fx_directory_local_path_clear*) |
| ![ディレクトリのローカル パスの取得アイコン](./media/user-guide/fx-events/image25.png)    | **ディレクトリのローカル パスの取得** (*fx_directory_local_path_get*) |
| ![ディレクトリのローカル パスの復元アイコン](./media/user-guide/fx-events/image26.png)    | **ディレクトリのローカル パスの復元** (*fx_directory_local_path_restore*) |
| ![ディレクトリのローカル パスの設定アイコン](./media/user-guide/fx-events/image27.png)    | **ディレクトリのローカル パスの設定** (*fx_directory_local_path_set*) |
| ![ディレクトリの長い名前の取得アイコン](./media/user-guide/fx-events/image28.png)    | **ディレクトリの長い名前の取得** (*fx_directory_long_name_get*) |
| ![ディレクトリ名のテスト アイコン](./media/user-guide/fx-events/image29.png)    | **ディレクトリ名のテスト** (*fx_directory_name_test*) |
| ![ディレクトリの次のエントリの検索アイコン](./media/user-guide/fx-events/image30.png)    | **ディレクトリの次のエントリの検索** (*fx_directory_next_entry_find*) |
| ![ディレクトリの次の完全なエントリの検索アイコン](./media/user-guide/fx-events/image31.png)    | **ディレクトリの次の完全なエントリの検索** (*fx_directory_next_full_entry_find*) |
| ![ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image32.png)    | **ディレクトリ名の変更** (*fx_directory_rename*) |
| ![ディレクトリの短い名前の取得アイコン](./media/user-guide/fx-events/image33.png)    | **ディレクトリの短い名前の取得** (*fx_directory_short_name_get*) |
| ![ファイルの割り当てアイコン](./media/user-guide/fx-events/image34.png)    | **ファイルの割り当て** (*fx_file_allocate*) |
| ![ファイル属性の読み取りアイコン](./media/user-guide/fx-events/image35.png)    | **ファイル属性の読み取り** (*fx_file_attributes_read*) |
| ![ファイル属性の設定アイコン](./media/user-guide/fx-events/image36.png)    | **ファイル属性の設定** (*fx_file_attributes_set*) |
| ![ファイルのベスト エフォート割り当てアイコン](./media/user-guide/fx-events/image37.png)    | **ファイルのベスト エフォート割り当て** (*fx_file_best_effort_allocate*) |
| ![ファイルを閉じるアイコン](./media/user-guide/fx-events/image38.png)    | **ファイルを閉じる** (*fx_file_close*) |
| ![ファイルの作成アイコン](./media/user-guide/fx-events/image39.png)    | **ファイルの作成** (*fx_file_create*) |
| ![ファイルの日時の設定アイコン](./media/user-guide/fx-events/image40.png)    | **ファイルの日時の設定** (*fx_file_date_time_set*) |
| ![ファイルの削除アイコン](./media/user-guide/fx-events/image41.png)    | **ファイルの削除** (*fx_file_delete*) |
| ![ファイルを開くアイコン](./media/user-guide/fx-events/image42.png)    | **ファイルを開く** (*fx_file_open*) |
| ![ファイルの読み取りアイコン](./media/user-guide/fx-events/image43.png)    | **ファイルの読み取り** (*fx_file_read*) |
| ![ファイルの相対シーク アイコン](./media/user-guide/fx-events/image44.png)    | **ファイルの相対シーク** (*fx_file_relative_seek*) |
| ![ファイル名の変更アイコン](./media/user-guide/fx-events/image45.png)    | **ファイル名の変更** (*fx_file_rename*) |
| ![ファイルのシーク アイコン](./media/user-guide/fx-events/image46.png)    | **ファイルのシーク** (*fx_file_seek*) |
| ![ファイルの切り詰めアイコン](./media/user-guide/fx-events/image47.png)    | **ファイルの切り詰め** (*fx_file_truncate*) |
| ![ファイルの切り詰め解除アイコン](./media/user-guide/fx-events/image48.png)    | **ファイルの切り詰め解除** (*fx_file_truncate_release*) |
| ![ファイルの書き込みアイコン](./media/user-guide/fx-events/image49.png)    | **ファイルの書き込み** (*fx_file_write*) |
| ![メディアの中止アイコン](./media/user-guide/fx-events/image50.png)    | **メディアの中止** (*fx_media_abort*) |
| ![メディア キャッシュの無効化アイコン](./media/user-guide/fx-events/image51.png)    | **メディア キャッシュの無効化** (*fx_media_cache_invalidate*) |
| ![メディアのチェック アイコン](./media/user-guide/fx-events/image52.png)    | **メディアのチェック** (*fx_media_check*) |
| ![*メディアを閉じるアイコン](./media/user-guide/fx-events/image53.png)    | **メディアを閉じる** (*fx_media_close*) |
| ![メディアのフラッシュ アイコン](./media/user-guide/fx-events/image54.png)    | **メディアのフラッシュ** (*fx_media_flush*) |
| ![メディアのフォーマット アイコン](./media/user-guide/fx-events/image55.png)    | **メディアのフォーマット** (*fx_media_format*) |
| ![メディアを開くアイコン](./media/user-guide/fx-events/image56.png)    | **メディアを開く** (*fx_media_open*) |
| ![メディアの読み取りアイコン](./media/user-guide/fx-events/image57.png)    | **メディアの読み取り** (*fx_media_read*) |
| ![使用可能なメディア領域アイコン](./media/user-guide/fx-events/image58.png)    | **使用可能なメディア領域** (*fx_media_space_available*) |
| ![メディア ボリュームの取得アイコン](./media/user-guide/fx-events/image59.png)    | **メディア ボリュームの取得** (*fx_media_volume_get*) |
| ![メディア ボリュームの設定アイコン](./media/user-guide/fx-events/image60.png)    | **メディア ボリュームの設定** (*fx_media_volume_set*) |
| ![メディアの書き込みアイコン](./media/user-guide/fx-events/image61.png)    | **メディアの書き込み** (*fx_media_write*) |
| ![システム日付の取得アイコン](./media/user-guide/fx-events/image62.png)    | **システム日付の取得** (*fx_system_date_get*) |
| ![システム日付の設定アイコン](./media/user-guide/fx-events/image63.png)    | **システム日付の設定** (*fx_system_date_set*) |
| ![システムの初期化アイコン](./media/user-guide/fx-events/image64.png)    | **システムの初期化** (*fx_system_initialize*) |
| ![システム時刻の取得アイコン](./media/user-guide/fx-events/image65.png)    | **システム時刻の取得** (*fx_system_time_get*) |
| ![システム時刻の設定アイコン](./media/user-guide/fx-events/image66.png)    | **システム時刻の設定** (*fx_system_time_set*) |
| ![Unicode ディレクトリの作成アイコン](./media/user-guide/fx-events/image67.png)    | **Unicode ディレクトリの作成** (*fx_unicode_directory_create*) |
| ![Unicode ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image68.png)    | **Unicode ディレクトリ名の変更** (*fx_unicode_directory_rename*) |
| ![Unicode ファイルの作成アイコン](./media/user-guide/fx-events/image69.png)    | **Unicode ファイルの作成** (*fx_unicode_file_create*) |
| ![Unicode ファイル名の変更アイコン](./media/user-guide/fx-events/image70.png)    | **Unicode ファイル名の変更** (*fx_unicode_file_rename*) |
| ![Unicode の長さの取得アイコン](./media/user-guide/fx-events/image71.png)    | **Unicode の長さの取得** (*fx_unicode_length_get*) |
| ![Unicode 名の取得アイコン](./media/user-guide/fx-events/image72.png)    | **Unicode 名の取得** (*fx_unicode_name_get*) |
| ![Unicode の短い名前の取得アイコン](./media/user-guide/fx-events/image73.png)    | **Unicode の短い名前の取得** (*fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>イベントの説明

以下では個々のイベントについて説明します。

### <a name="internal-logical-sector-cache-miss"></a>内部論理セクターのキャッシュ ミス 

#### <a name="internal-logical-sector-cache-miss"></a>内部論理セクターのキャッシュ ミス

**アイコン** ![内部論理セクターのキャッシュ ミス アイコン](./media/user-guide/fx-events/image1.png)

**説明**

このイベントは、内部 FileX 論理セクターのキャッシュ ミスを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: セクター。
- 情報フィールド 3: ミスの総数。
- 情報フィールド 4: キャッシュ サイズ。

### <a name="internal-directory-cache-miss"></a>内部ディレクトリのキャッシュ ミス

#### <a name="internal-directory-cache-miss"></a>内部ディレクトリのキャッシュ ミス

**アイコン** ![内部ディレクトリのキャッシュ ミス アイコン](./media/user-guide/fx-events/image2.png)

**説明** 

このイベントは、内部 FileX ディレクトリのキャッシュ ミスを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ミスの総数。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-media-flush"></a>内部メディアのフラッシュ 

#### <a name="internal-media-flush"></a>内部メディアのフラッシュ

**アイコン** ![内部メディアのフラッシュ アイコン](./media/user-guide/fx-events/image3.png)

**説明**

このイベントは、内部 FileX メディアのフラッシュを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ダーティ セクターの数。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。


### <a name="internal-directory-entry-read"></a>内部ディレクトリ エントリの読み取り 

#### <a name="internal-directory-entry-read"></a>内部ディレクトリ エントリの読み取り

**アイコン** ![内部ディレクトリ エントリの読み取りアイコン](./media/user-guide/fx-events/image4.png)

**説明**

このイベントは、内部 FileX ディレクトリ エントリの読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-directory-entry-write"></a>内部ディレクトリ エントリの書き込み

#### <a name="internal-directory-entry-write"></a>内部ディレクトリ エントリの書き込み

**アイコン** ![内部ディレクトリ エントリの書き込みアイコン](./media/user-guide/fx-events/image5.png)

**説明**

このイベントは、内部 FileX ディレクトリ エントリの書き込みイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-read"></a>内部 I/O ドライバーの読み取り 

#### <a name="internal-io-driver-read"></a>内部 I/O ドライバーの読み取り 

**アイコン** ![内部 I / O ドライバーの読み取りアイコン](./media/user-guide/fx-events/image6.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーの読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: セクター。
- 情報フィールド 3: セクターの数。
- 情報フィールド 4: バッファー ポインター。

### <a name="internal-io-driver-write"></a>内部 I/O ドライバーの書き込み 

#### <a name="internal-io-driver-write"></a>内部 I/O ドライバーの書き込み 

**アイコン** ![内部 I / O ドライバーの書き込みアイコン](./media/user-guide/fx-events/image7.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーの書き込みイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: セクター。
- 情報フィールド 3: セクターの数。
- 情報フィールド 4: バッファー ポインター。

### <a name="internal-io-driver-flush"></a>内部 I/O ドライバーのフラッシュ 

#### <a name="internal-io-driver-flush"></a>内部 I/O ドライバーのフラッシュ 

**アイコン** ![内部 I / O ドライバーのフラッシュ アイコン](./media/user-guide/fx-events/image8.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーのフラッシュ イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-abort"></a>内部 I/O ドライバーの中止 

#### <a name="internal-io-dirver-abort"></a>内部 I/O ドライバーの中止

**アイコン** ![内部 I / O ドライバーの中止アイコン](./media/user-guide/fx-events/image9.png)

**説明**

このイベントは、内部 FileX I/O ドライバーの中止イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-initialize"></a>内部 I/O ドライバーの初期化 

#### <a name="internal-io-driver-initialize"></a>内部 I/O ドライバーの初期化 

**アイコン** ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/fx-events/image10.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーの初期化イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-boot-sector-read"></a>内部 I/O ドライバーのブート セクターの読み取り 

#### <a name="internal-io-driver-boot-sector-read"></a>内部 I/O ドライバーのブート セクターの読み取り 

**アイコン** ![内部 I / O ドライバーのブート セクターの読み取りアイコン](./media/user-guide/fx-events/image11.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーのブート セクターの読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: バッファー ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-release-sectors"></a>内部 I/O ドライバーのリリース セクター 

#### <a name="internal-io-driver-release-sectors"></a>内部 I/O ドライバーのリリース セクター 

**アイコン** ![内部 I / O ドライバーのリリース セクター アイコン](./media/user-guide/fx-events/image12.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーのリリース セクター イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: セクター。
- 情報フィールド 3: セクターの数。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-boot-sector-write"></a>内部 I/O ドライバーのブート セクターの書き込み

#### <a name="internal-io-driver-boot-sector-write"></a>内部 I/O ドライバーのブート セクターの書き込み 

**アイコン** ![内部 I / O ドライバーのブート セクターの書き込みアイコン](./media/user-guide/fx-events/image13.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーのブート セクターの書き込みイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: バッファー ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-un-initialize"></a>内部 I/O ドライバーの初期化解除 

#### <a name="internal-io-driver-un-initialize"></a>内部 I/O ドライバーの初期化解除 

**アイコン** ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/fx-events/image14.png)

**説明** 

このイベントは、内部 FileX I/O ドライバーの初期化解除イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。
</blockquote></td>

### <a name="directory-attributes-read"></a>ディレクトリ属性の読み取り 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**アイコン** ![ディレクトリ属性の読み取りアイコン](./media/user-guide/fx-events/image15.png)

**説明** 

このイベントは、ディレクトリ属性の読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 属性のビット マップ:

  | 属性                         | 値        |
  |---------------------------------- | --------|
  |  [読み取り専用]                        | (0x01)  |
  |  [非表示]                           | (0x02)  |
  |  システム                           | (0x04)  |
  |  ボリューム                           | (0x08)  |
  |  ディレクトリ                        | (0x10)  |
  |  アーカイブ                          | (0x20)  |
- 情報フィールド 4: 使用されていません。

### <a name="directory-attributes-set"></a>ディレクトリ属性の設定 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**アイコン** ![属性の設定アイコン](./media/user-guide/fx-events/image16.png)

**説明** 

このイベントは、ディレクトリ属性の設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 属性のビット マップ:

  |  属性                        | 値        |
  |---------------------------------- | --------|
  |  [読み取り専用]                        | (0x01)  |
  |  [非表示]                           | (0x02)  |
  |  システム                           | (0x04)  |
  |  アーカイブ                          | (0x20)  |
- 情報フィールド 4: 使用されていません。

### <a name="directory-create"></a>ディレクトリの作成 

#### <a name="fx_directory_create"></a>fx_directory_create

**アイコン** ![ディレクトリの作成アイコン](./media/user-guide/fx-events/image17.png)

**説明** 

このイベントは、ディレクトリの作成イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-default-get"></a>既定のディレクトリの取得 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**アイコン** ![既定のディレクトリの取得アイコン](./media/user-guide/fx-events/image18.png)

**説明** 

このイベントは、既定のディレクトリの取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: リターン パス名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-default-set"></a>既定のディレクトリの設定 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**アイコン** ![既定のディレクトリの設定アイコン](./media/user-guide/fx-events/image19.png)

**説明** 

このイベントは、既定のディレクトリの設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 新しい既定のパス名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-delete"></a>ディレクトリの削除 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**アイコン** ![ディレクトリの削除アイコン](./media/user-guide/fx-events/image20.png)

**説明** 

このイベントは、ディレクトリの削除イベントを表します。

**情報フィールド**
- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-first-entry-find"></a>ディレクトリの最初のエントリの検索 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**アイコン** ![ディレクトリの最初のエントリの検索アイコン](./media/user-guide/fx-events/image21.png)

**説明** 

このイベントは、ディレクトリの最初のエントリの検索イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-first-full-entry-find"></a>ディレクトリの最初の完全なエントリの検索 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**アイコン** ![ディレクトリの最初の完全なエントリの検索アイコン](./media/user-guide/fx-events/image22.png)

**説明** 

このイベントは、ディレクトリの最初の完全なエントリの検索イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-information-get"></a>ディレクトリ情報の取得 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**アイコン** ![ディレクトリ情報の取得アイコン](./media/user-guide/fx-events/image23.png)

**説明** 

このイベントは、ディレクトリ情報の取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-local-path-clear"></a>ディレクトリのローカル パスのクリア 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**アイコン** ![ディレクトリのローカル パスのクリア アイコン](./media/user-guide/fx-events/image24.png)

**説明** 

このイベントは、ディレクトリのローカル パスのクリア イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-local-path-get"></a>ディレクトリのローカル パスの取得 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**アイコン** ![ディレクトリのローカル パスの取得アイコン](./media/user-guide/fx-events/image25.png)

**説明** 

このイベントは、ディレクトリのローカル パスの取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: リターン パス名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-local-path-restore"></a>ディレクトリのローカル パスの復元 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**アイコン** ![ディレクトリのローカル パスの復元アイコン](./media/user-guide/fx-events/image26.png)

**説明** 

このイベントは、ディレクトリのローカル パスの復元イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ローカル パス構造へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-local-path-set"></a>ディレクトリのローカル パスの設定 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**アイコン** ![ディレクトリのローカル パスの設定アイコン](./media/user-guide/fx-events/image27.png)

**説明** 

このイベントは、ディレクトリのローカル パスの設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ローカル パス構造へのポインター。
- 情報フィールド 3: 新しいパス名へのポインター。
- 情報フィールド 4: 使用されていません。

### <a name="directory-long-name-get"></a>ディレクトリの長い名前の取得 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**アイコン** ![ディレクトリの長い名前の取得アイコン](./media/user-guide/fx-events/image28.png)

**説明** 

このイベントは、ディレクトリの長い名前の取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 短いファイル名へのポインター。
- 情報フィールド 3: 長いファイル名へのポインター。
- 情報フィールド 4: 使用されていません。

### <a name="directory-name-test"></a>ディレクトリ名のテスト 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**アイコン** ![ディレクトリ名のテスト アイコン](./media/user-guide/fx-events/image29.png)

**説明** 

このイベントは、ディレクトリ名のテスト イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-next-entry-find"></a>ディレクトリの次のエントリの検索 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**アイコン** ![ディレクトリの次のエントリの検索アイコン](./media/user-guide/fx-events/image30.png)

**説明** 

このイベントは、ディレクトリの次のエントリの検索イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-next-full-entry-find"></a>ディレクトリの次の完全なエントリの検索 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**アイコン** ![ディレクトリの次の完全なエントリの検索アイコン](./media/user-guide/fx-events/image31.png)

**説明**

このイベントは、ディレクトリの次の完全なエントリの検索イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ディレクトリ名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="directory-rename"></a>ディレクトリ名の変更 

#### <a name="fx_directory_rename-event"></a>fx_directory_rename event

**アイコン** ![ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image32.png)

**説明**

このイベントは、ディレクトリ名の変更イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 古いディレクトリ名へのポインター。
- 情報フィールド 3: 新しいディレクトリ名へのポインター。
- 情報フィールド 4: 使用されていません。

### <a name="directory-short-name-get"></a>ディレクトリの短い名前の取得 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**アイコン** ![ディレクトリの短い名前の取得アイコン](./media/user-guide/fx-events/image33.png)

**説明**

このイベントは、ディレクトリの短い名前の取得イベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 長いファイル名へのポインター。
- 情報フィールド 3: 短いファイル名へのポインター。
- 情報フィールド 4: 使用されていません。

### <a name="file-allocate"></a>ファイルの割り当て 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**アイコン** ![ファイルの割り当てアイコン](./media/user-guide/fx-events/image34.png)

**説明**

このイベントは、ファイルの割り当てイベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: 要求されたサイズ。
- 情報フィールド 3: 現在のサイズ。
- 情報フィールド 4: 新しいサイズ。

### <a name="file-attributes-read"></a>ファイル属性の読み取り 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**アイコン** ![ファイル属性の読み取りアイコン](./media/user-guide/fx-events/image35.png)

**説明**

このイベントは、ファイル属性の読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。 
- 情報フィールド 2: 属性のビット マップ:

  |  属性                         | 値        |
  |---------------------------------- | --------|
  |  [読み取り専用]                        | (0x01)  |
  |  [非表示]                           | (0x02)  |
  |  システム                           | (0x04)  |
  |  ボリューム                           | (0x08)  |
  |  ディレクトリ                        | (0x10)  |
  |  アーカイブ                          | (0x20)  |
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="file-attributes-set"></a>ファイル属性の設定 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**アイコン** ![ファイル属性の設定アイコン](./media/user-guide/fx-events/image36.png)

**説明** 

このイベントは、ファイル属性の設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ファイル名へのポインター。 
- 情報フィールド 3: 属性のビット マップ:

  | 属性                         | 値        |
  |---------------------------------- | --------|
  |  [読み取り専用]                        | (0x01)  |
  |  [非表示]                           | (0x02)  |
  |  システム                           | (0x04)  |
  |  アーカイブ                          | (0x20)  |
- 情報フィールド 4: 使用されていません。

### <a name="file-best-effort-allocate"></a>ファイルのベスト エフォート割り当て 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**アイコン** ![ファイルのベスト エフォート割り当てアイコン](./media/user-guide/fx-events/image37.png)

**説明** 

このイベントは、ファイルのベスト エフォート割り当てイベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: 要求されたサイズ。
- 情報フィールド 3: 割り当てられた実際のサイズ。
- 情報フィールド 4: 使用されていません。

### <a name="file-close"></a>ファイルを閉じる 

#### <a name="fx_file_close"></a>fx_file_close

**アイコン** ![ファイルを閉じるアイコン](./media/user-guide/fx-events/image38.png)

**説明** 

このイベントは、ファイルを閉じるイベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: ファイル サイズ。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="file-create"></a>ファイルの作成

#### <a name="fx_file_create"></a>fx_file_create

**アイコン** ![ファイルの作成アイコン](./media/user-guide/fx-events/image39.png)

**説明**

このイベントは、ファイルの作成イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ファイル名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="file-date-time-set"></a>ファイルの日時の設定 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**アイコン** ![ファイルの日時の設定アイコン](./media/user-guide/fx-events/image40.png)

**説明**

このイベントは、ファイルの日時の設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ファイル名へのポインター。
- 情報フィールド 3: 年。
- 情報フィールド 4: 月。

### <a name="file-delete"></a>ファイルの削除 

#### <a name="fx_file_delete"></a>fx_file_delete

**アイコン** ![ファイルの削除アイコン](./media/user-guide/fx-events/image41.png)

**説明**

このイベントは、ファイルの削除イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ファイル名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="file-open"></a>ファイルを開く 

#### <a name="fx_file_open"></a>fx_file_open

**アイコン** ![ファイルを開くアイコン](./media/user-guide/fx-events/image42.png)

**説明**

このイベントは、ファイルを開くイベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ファイル制御ブロックへのポインター。
- 情報フィールド 3: ファイル名へのポインター。
- 情報フィールド 4: 開くの種類:

  |  開くの種類                        | 値        |
  |---------------------------------- | --------|
  |  読み取り用に開く                    | (0x00)  |
  |  書き込み用に開く                   | (0x01)  |
  |  読み取り用に高速で開く               | (0x02)  |

### <a name="file-read"></a>ファイルの読み取り 

#### <a name="fx_file_read"></a>fx_file_read

**アイコン** ![ファイルの読み取りアイコン](./media/user-guide/fx-events/image43.png)

**説明**

このイベントは、ファイルの読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: バッファー ポインター。
- 情報フィールド 3: 要求サイズ。
- 情報フィールド 4: 読み取られた実際のサイズ。

### <a name="file-relative-seek"></a>ファイルの相対シーク 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**アイコン** ![ファイルの相対シーク アイコン](./media/user-guide/fx-events/image44.png)

**説明**

このイベントは、ファイルの相対シーク イベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: バイト オフセット。
- 情報フィールド 3: シークの開始位置:

  | イベント                             | 値        |
  |---------------------------------- | --------|
  |  最初から                   | (0x00)  |
  |  最後から                         | (0x01)  | 
  |  転送                          | (0x02)  |
  |  移動                         | (0x03)  |
- 情報フィールド 4: 以前のオフセット。

### <a name="file-rename"></a>ファイル名の変更 

#### <a name="fx_file_rename"></a>fx_file_rename

**アイコン** ![ファイル名の変更アイコン](./media/user-guide/fx-events/image45.png)

**説明**

このイベントは、ファイル名の変更イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 古いファイル名へのポインター。
- 情報フィールド 3: 新しいファイル名へのポインター。
- 情報フィールド 4: 使用されていません。

### <a name="file-seek"></a>ファイルのシーク 

#### <a name="fx_file_seek"></a>fx_file_seek

**アイコン** ![ファイルのシーク アイコン](./media/user-guide/fx-events/image46.png)

**説明**

このイベントは、ファイルのシーク イベントを表します。

**情報フィールド** 

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: バイト オフセット。
- 情報フィールド 3: 以前のオフセット。
- 情報フィールド 4: 使用されていません。

### <a name="file-truncate"></a>ファイルの切り詰め 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**アイコン** ![ファイルの切り詰めアイコン](./media/user-guide/fx-events/image47.png)

**説明**

このイベントは、ファイルの切り詰めイベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: 要求されたサイズ。
- 情報フィールド 3: 以前のサイズ。
- 情報フィールド 4: 新しいサイズ。

### <a name="file-truncate-release"></a>ファイルの切り詰め解除 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**アイコン** ![ファイルの切り詰め解除アイコン](./media/user-guide/fx-events/image48.png)

**説明**

このイベントは、ファイルの切り詰め解除イベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: 要求されたサイズ。
- 情報フィールド 3: 以前のサイズ。
- 情報フィールド 4: 新しいサイズ。

### <a name="file-write"></a>ファイルの書き込み 

#### <a name="fx_file_write"></a>fx_file_write 

**アイコン** ![ファイルの書き込みアイコン](./media/user-guide/fx-events/image49.png)

**説明**

このイベントは、ファイルの書き込みイベントを表します。

**情報フィールド**

- 情報フィールド 1: ファイルへのポインター。
- 情報フィールド 2: バッファー ポインター。
- 情報フィールド 3: 要求サイズ。
- 情報フィールド 4: 書き込まれた実際のサイズ。

### <a name="media-abort"></a>メディアの中止 

#### <a name="fx_media_abort"></a>fx_media_abort 

**アイコン** ![メディアの中止アイコン](./media/user-guide/fx-events/image50.png)

**説明**

このイベントは、メディアの中止イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="media-cache-invalidate"></a>メディア キャッシュの無効化

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**アイコン** ![メディア キャッシュの無効化アイコン](./media/user-guide/fx-events/image51.png)

**説明**

このイベントは、メディア キャッシュの無効化イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="media-check"></a>メディアのチェック 

#### <a name="fx_media_check"></a>fx_media_check

**アイコン** ![メディアのチェック アイコン](./media/user-guide/fx-events/image52.png)

**説明**

このイベントは、メディアのチェック イベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: スクラッチ メモリのポインター。
- 情報フィールド 3: スクラッチ メモリのサイズ。
- 情報フィールド 4: エラーのビット マップ:

  | エラーの種類                        | 値        |
  |---------------------------------- | --------|
  |  FAT チェーン エラー                  | (0x01)  |
  |  ディレクトリ エラー                  | (0x02)  |
  |  破損クラスター エラー               | (0x04)  |
  |  ファイル サイズ エラー                  | (0x08)  |

### <a name="media-close"></a>メディアを閉じる 

#### <a name="fx_media_close"></a>fx_media_close

**アイコン** ![メディアを閉じるアイコン](./media/user-guide/fx-events/image53.png)

**説明**

このイベントは、メディアを閉じるイベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="media-flush"></a>メディアのフラッシュ 

#### <a name="fx_media_flush"></a>fx_media_flush

**アイコン** ![メディアのフラッシュ アイコン](./media/user-guide/fx-events/image54.png)

**説明**

このイベントは、メディアのフラッシュ イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="media-format"></a>メディアのフォーマット 

#### <a name="fx_media_format"></a>fx_media_format

**アイコン** ![メディアのフォーマット アイコン](./media/user-guide/fx-events/image55.png)

**説明**

このイベントは、メディアのフォーマット イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ルート エントリの数。
- 情報フィールド 3: セクター数。
- 情報フィールド 4: クラスターあたりのセクター数。

### <a name="media-open"></a>メディアを開く 

#### <a name="fx_media_open"></a>fx_media_open

**アイコン** ![メディアを開くアイコン](./media/user-guide/fx-events/image56.png)

**説明**

このイベントは、メディアを開くイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: メディア ドライバー エントリへのポインター。
- 情報フィールド 3: メモリ ポインター。
- 情報フィールド 4: メモリ サイズ。

### <a name="media-read-media-read"></a>メディアの読み取り 

#### <a name="fx_media_read"></a>fx_media_read

**アイコン** ![メディアの読み取りアイコン](./media/user-guide/fx-events/image57.png)

**説明**

このイベントは、メディアの読み取りイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 論理セクター。
- 情報フィールド 3: バッファー ポインター。
- 情報フィールド 4: 読み取りバイト数。

### <a name="media-space-available"></a>使用可能なメディア領域 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**アイコン** ![使用可能なメディア領域アイコン](./media/user-guide/fx-events/image58.png)

**説明**

このイベントは、使用可能なメディア領域イベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 使用可能なバイト数ポインター。
- 情報フィールド 3: 空きクラスターの数。
- 情報フィールド 4: 使用されていません。

### <a name="media-volume-get"></a>メディア ボリュームの取得 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**アイコン** ![メディア ボリュームの取得アイコン](./media/user-guide/fx-events/image59.png)

**説明**

このイベントは、メディア ボリュームの取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ボリューム名へのポインター。
- 情報フィールド 3: ボリューム ソース。
- 情報フィールド 4: 使用されていません。

### <a name="media-volume-set"></a>メディア ボリュームの設定 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**アイコン** ![メディア ボリュームの設定アイコン](./media/user-guide/fx-events/image60.png)

**説明**

このイベントは、メディア ボリュームの設定イベントを表します。

**情報フィールド** 
- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ボリューム名へのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="media-write"></a>メディアの書き込み 

#### <a name="fx_media_write"></a>fx_media_write

**アイコン** ![メディアの書き込みアイコン](./media/user-guide/fx-events/image61.png)

**説明**

このイベントは、メディアの書き込みイベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: 論理セクター。
- 情報フィールド 3: バッファー ポインター。
- 情報フィールド 4: 書き込みバイト数。

### <a name="system-date-get"></a>システム日付の取得 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**アイコン** ![システム日付の取得アイコン](./media/user-guide/fx-events/image62.png)

**説明**

このイベントは、システム日付の取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: 年。
- 情報フィールド 2: 月。
- 情報フィールド 3: 日。
- 情報フィールド 4: 使用されていません。

### <a name="system-date-set"></a>システム日付の設定 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**アイコン** ![システム日付の設定アイコン](./media/user-guide/fx-events/image63.png)

**説明**

このイベントは、システム日付の設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: 年。
- 情報フィールド 2: 月。
- 情報フィールド 3: 日。
- 情報フィールド 4: 使用されていません。

### <a name="system-initialize"></a>システムの初期化 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**アイコン** ![システムの初期化アイコン](./media/user-guide/fx-events/image64.png)

**説明**

このイベントは、システムの初期化イベントを表します。

**情報フィールド**

- 情報フィールド 1: 使用されていません。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="system-time-get"></a>システム時刻の取得 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**アイコン** ![システム時刻の取得アイコン](./media/user-guide/fx-events/image65.png)

**説明**

このイベントは、システム時刻の取得イベントを表します。

**情報フィールド** 

- 情報フィールド 1: 時。
- 情報フィールド 2: 分。
- 情報フィールド 3: 秒。
- 情報フィールド 4: 使用されていません。

### <a name="system-time-set"></a>システム時刻の設定 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**アイコン** ![システム時刻の設定アイコン](./media/user-guide/fx-events/image66.png)

**説明**

このイベントは、システム時刻の設定イベントを表します。

**情報フィールド**

- 情報フィールド 1: 時。
- 情報フィールド 2: 分。
- 情報フィールド 3: 秒。
- 情報フィールド 4: 使用されていません。

### <a name="unicode-directory-create"></a>Unicode ディレクトリの作成 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**アイコン** ![Unicode ディレクトリの作成アイコン](./media/user-guide/fx-events/image67.png)

**説明**

このイベントは、Unicode ディレクトリの作成イベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: Unicode 名へのポインター。
- 情報フィールド 3: Unicode 名のサイズ。
- 情報フィールド 4: 短い名前へのポインター。

### <a name="unicode-directory-rename"></a>Unicode ディレクトリ名の変更 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**アイコン** ![Unicode ディレクトリ名の変更アイコン](./media/user-guide/fx-events/image68.png)

**説明**

このイベントは、Unicode ディレクトリ名の変更イベントを表します。

**情報フィールド** 

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: Unicode 名へのポインター。
- 情報フィールド 3: Unicode 名のサイズ。
- 情報フィールド 4: 短い名前へのポインター。

### <a name="unicode-file-create"></a>Unicode ファイルの作成 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**アイコン** ![Unicode ファイルの作成アイコン](./media/user-guide/fx-events/image69.png)

**説明**

このイベントは、Unicode ファイルの作成イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: Unicode 名へのポインター。
- 情報フィールド 3: Unicode 名のサイズ。
- 情報フィールド 4: 短い名前へのポインター。

### <a name="unicode-file-rename"></a>Unicode ファイル名の変更 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**アイコン** ![Unicode ファイル名の変更アイコン](./media/user-guide/fx-events/image70.png)

**説明**

このイベントは、Unicode ファイル名の変更イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: Unicode 名へのポインター。
- 情報フィールド 3: Unicode 名のサイズ。
- 情報フィールド 4: 短い名前へのポインター。

### <a name="unicode-length-get"></a>Unicode の長さの取得 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**アイコン** ![Unicode の長さの取得アイコン](./media/user-guide/fx-events/image71.png)

**説明**

このイベントは、Unicode の長さの取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: Unicode 名へのポインター。
- 情報フィールド 2: 長さ。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="unicode-name-get"></a>Unicode 名の取得 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**アイコン** ![Unicode 名の取得アイコン](./media/user-guide/fx-events/image72.png)

**説明**

このイベントは、Unicode 名の取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ソースの短い名前。
- 情報フィールド 3: ターゲットの Unicode 名ポインター。
- 情報フィールド 4: ターゲットの Unicode 名の長さ。

### <a name="unicode-short-name-get"></a>Unicode の短い名前の取得 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**アイコン** ![Unicode の短い名前の取得アイコン](./media/user-guide/fx-events/image73.png)

**説明**

このイベントは、Unicode の短い名前の取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: メディアへのポインター。
- 情報フィールド 2: ソースの Unicode 名へのポインター。
- 情報フィールド 3: Unicode 名の長さ。
- 情報フィールド 4: 短い名前へのポインター。