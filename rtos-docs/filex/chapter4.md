---
title: 第 4 章 - Azure RTOS FileX サービスの説明
description: この章は、すべての Azure RTOS FileX サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811360"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>第 4 章 - Azure RTOS FileX サービスの説明

この章は、すべての Azure RTOS FileX サービスの説明をアルファベット順にまとめたものです。 サービス名は、類似するすべてのサービスがグループ化されるよう命名されています。

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

ディレクトリ属性を読み取ります

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>説明

このサービスは、指定されたメディアからディレクトリの属性を読み取ります。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: 要求されたディレクトリの名前へのポインター (ディレクトリ パスは省略可能です)。
- **attributes** _ptr: 配置されるディレクトリの属性の宛先へのポインター。 ディレクトリ属性は、次の設定が可能なビットマップ形式で返されます。
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ディレクトリ属性の読み取りに成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX _NOT FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした
- **FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

ディレクトリ属性を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>説明

このサービスは、ディレクトリの属性を、呼び出し元によって指定された属性に設定します。

> [!WARNING]
> *このアプリケーションでは、このサービスを使用してディレクトリの属性のサブセットを変更することのみが許可されています。追加の属性を設定しようとすると、エラーが発生します。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: 要求されたディレクトリの名前へのポインター (ディレクトリ パスは省略可能です)。
- **attributes**: このディレクトリへの新しい属性。 有効なディレクトリ属性は次のように定義されます。
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ディレクトリ属性の設定に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NOT_FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした
- **FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター
- **FX_INVALID_ATTR** (0x19) 無効な属性が選択されました。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

サブディレクトリを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>説明

このサービスは、現在のデフォルト ディレクトリ、またはディレクトリ名に指定されたパスにサブディレクトリを作成します。 ルート ディレクトリとは異なり、サブディレクトリには、保持できるファイルの数に制限はありません。 ルート ディレクトリには、ブート レコードによって決定されたエントリの数のみ保持できます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: 作成するディレクトリの名前を指すポインター (ディレクトリ パスは省略可能です)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ディレクトリの作成に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NOT_FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした
- **FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター
- **FX_INVALID_ATTR** (0x19) 無効な属性が選択されました。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

最後のデフォルト ディレクトリを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>説明

このサービスは、***fx_directory_default_set*** によって最後に設定されたパスへのポインターを返します。 デフォルト ディレクトリが設定されていない場合、または現在のデフォルト ディレクトリがルート ディレクトリである場合は、FX_NULL の値が返されます。

> [!IMPORTANT]
> *内部パス文字列のデフォルト サイズは 256 文字です。これは **fx_api.h** の **FX_MAXIMUM_PATH** を変更し、FileX ライブラリ全体を再構築することによって変更できます。文字列のパスはアプリケーション用に保持され、FileX によって内部的に使用されません。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **return_path_name**: 最後のデフォルト ディレクトリ文字列の宛先へのポインター。 デフォルト ディレクトリの現在の設定がルートである場合は、FX_NULL の値が返されます。 メディアをオープンしたとき、ルートが既定値になります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) デフォルト ディレクトリの取得に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

デフォルト ディレクトリを設定します

### <a name="prototype"></a>プロトタイプ

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>説明

このサービスは、メディアのデフォルト ディレクトリを設定します。 FX_NULL の値が指定されている場合、デフォルト ディレクトリはメディアのルート ディレクトリに設定されます。 パスを明示的に指定していない後続のすべてのファイル操作は、デフォルトでこのディレクトリに設定されます。

> [!IMPORTANT]
> *内部パス文字列のデフォルト サイズは 256 文字です。これは **fx_api.h** の **FX_MAXIMUM_PATH** を変更し、FileX ライブラリ全体を再構築することによって変更できます。文字列のパスはアプリケーション用に保持され、FileX によって内部的に使用されません。*

> [!IMPORTANT]
> *アプリケーションによって提供される名前の場合、FileX では、ディレクトリ、サブディレクトリ、およびファイル名を区切るために円記号 (\\) とスラッシュ (/) の両方の文字がサポートされます。ただし FileX では、アプリケーションに返されるパスで円記号のみを使用します。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **new_path_name**: 新しいデフォルト ディレクトリ名へのポインター。 FX_NULL の値が指定されている場合、メディアのデフォルト ディレクトリはメディアのルート ディレクトリに設定されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) デフォルト ディレクトリの設定に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_INVALID_PATH** (0x0D) 新しいディレクトリが見つかりませんでした
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

サブディレクトリを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>説明

このサービスは、指定されたディレクトリを削除します。 削除するにはディレクトリを空にする必要があることに注意してください。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: 削除するディレクトリの名前へのポインター (ディレクトリ パスは省略可能です)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ディレクトリの削除に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NOT_FOUND** (0x04) 指定されたディレクトリが見つかりませんでした
- **FX_DIR_NOT_EMPTY** (0x10) 指定されたディレクトリは空ではありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません
- **FX_NOT_DIRECTORY** (0x0E) ディレクトリ エントリではありません
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

最初のディレクトリ エントリを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>説明

このサービスは、デフォルト ディレクトリ内の最初のエントリ名を取得し、指定した宛先にコピーします。

> [!WARNING]
> *指定された宛先は、**FX_MAX_LONG_NAME_LEN** で定義されているように、最大サイズの FileX 名を保持するのに十分な大きさである必要があります。*

> [!WARNING]
> *ローカル以外のパスを使用する場合は、ディレクトリ トラバーサルの実行中に他のアプリケーション スレッドによってこのディレクトリが変更されることを (ThreadX セマフォ、ミューテックス、または優先度レベルの変更により) 防ぐことが重要です。そうでないと、無効な結果が得られる可能性があります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **return_entry_name**: デフォルト ディレクトリにある最初のエントリ名の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 最初のディレクトリ エントリの検索に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

完全な情報を含む最初のディレクトリ エントリを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: ディレクトリ エントリの名前の宛先を指すポインター。 FX_MAX_LONG_NAME_LEN 以上の大きさである必要があります。
- **attributes**: null 以外の場合、配置されるエントリの属性の宛先を指すポインター。 属性は、次の設定が可能なビットマップ形式で返されます。
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: null 以外の場合、エントリのサイズの宛先を指すポインター (バイト単位)。
- **year**: null 以外の場合、エントリが変更された年の宛先を指すポインター。
- **month**: null 以外の場合、エントリが変更された月の宛先を指すポインター。
- **day**: null 以外の場合、エントリが変更された日の宛先を指すポインター。
- **hour**: null 以外の場合、エントリが変更された時間の宛先を指すポインター。
- **minute**: null 以外の場合、エントリが変更された分の宛先を指すポインター。
- **second**: null 以外の場合、エントリが変更された秒の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 最初のディレクトリ エントリの検索に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

ディレクトリ エントリの情報を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: ディレクトリ エントリの名前へのポインター。
- **attributes**: 属性の宛先へのポインター。
- **size**: サイズの宛先へのポインター。
- **year**: 年の宛先へのポインター。
- **month**: 月の宛先へのポインター。
- **day**: 日の宛先へのポインター。
- **hour**: 時間の宛先へのポインター。
- **minute**: 分の宛先へのポインター。
- **second**: 秒の宛先へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 最初のディレクトリ エントリの検索に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NOT_FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

デフォルト ローカル パスをクリアします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>説明

このサービスは、呼び出し元のスレッド用に設定された前のローカル パスをクリアします。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: 以前に開いたメディアへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ローカル パスのクリアに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが現在開いていません
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH が定義されています
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

現在のローカル パス文字列を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>説明

このサービスは、指定されたメディアのローカル パス ポインターを返します。 ローカル パスが設定されていない場合は、呼び出し元に NULL が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **return_path_name**: 格納されるローカル パス文字列の宛先文字列ポインターへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ローカル パスの取得に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが現在開いていません
- **FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

前のローカル パスを復元します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に設定したローカル パスを復元します。 このローカル パスに対して行われたディレクトリの検索位置も復元されるため、このルーチンは、アプリケーションによる再帰的なディレクトリのトラバーサルに役立ちます。

> [!IMPORTANT]
> *各ローカル パスには **FX_MAXIMUM_PATH** のローカル パス文字列のサイズが含まれており、既定で 256 文字です。この内部パス文字列は FileX では使用されず、アプリケーションで使用するためにのみ提供されています。**FX_LOCAL_PATH** がローカル変数として宣言される場合、ユーザーは、この構造体のサイズによって増加しているスタックに注意する必要があります。ユーザーは **FX_MAXIMUM_PATH** のサイズを小さくし、FileX ライブラリ ソースを再構築することが推奨されます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **local_path_ptr**: 以前に設定されたローカル パスへのポインター。 このポインターが、以前に使用されていてそのまま保持されているローカル パスをポイントするようにすることは非常に重要です。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ローカル パスの復元に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが現在開いていません。
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH が定義されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはローカル パス ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

スレッド固有のローカルパスを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>説明

このサービスは、***new_path_string** _ によって指定されたスレッド固有のパスを設定します。 このルーチンが正常に完了すると、_ *_local_path_ptr_** に格納されているローカル パス情報が、このスレッドによって実行されるすべてのファイルおよびディレクトリ操作のグローバル メディア パスよりも優先されます。 これは、システム内の他のスレッドには影響しません 
> [!IMPORTANT]
> *ローカル パス文字列のデフォルト サイズは 256 文字です。これは **fx_api.h** の **FX_MAXIMUM_PATH** を変更し、FileX ライブラリ全体を再構築することによって変更できます。文字列のパスはアプリケーション用に保持され、FileX によって内部的に使用されません。*

> [!IMPORTANT]
> *アプリケーションによって提供される名前の場合、FileX では、ディレクトリ、サブディレクトリ、およびファイル名を区切るために円記号 (\\) とスラッシュ (/) の両方の文字がサポートされます。ただし FileX では、アプリケーションに返されるパスで円記号のみを使用します。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: 以前に開いたメディアへのポインター。
- **local_path_ptr**: スレッド固有のローカル パス情報を保持するための宛先。 この構造体のアドレスは、後でローカル パスの復元関数に渡すことができます。
- **new_path_name**: セットアップするローカル パスを指定します。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) デフォルト ディレクトリの設定に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_IMPLEMENTED** (0x22) **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH** (0x0D) 新しいディレクトリが見つかりませんでした。
- **FX_NOT_IMPLEMENTED** (0x22)- **FX_NO_LOCAL_PATH が定義されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはローカル パス ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

短い名前から長い名前を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>説明

このサービスは、指定された短い名前 (8.3 形式) に関連付けられている長い名前 (存在する場合) を取得します。 短い名前には、ファイル名またはディレクトリ名を指定できます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **short_name**: ソースの短い名前 (8.3 形式) へのポインター。
- **long_name**: 長い名前の宛先へのポインター。 長い名前がない場合は、短い名前が返されます。 長い名前の宛先は、FX_MAX_LONG_NAME_LEN 文字を保持するのに十分な大きさである必要があることに注意してください。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 長い名前の取得に成功しました
- **FX_NOT_FOUND** (0x04) 短い名前が見つかりませんでした
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー
- **FX_MEDIA_INVALID** (0x02) 無効なメディア
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_SECTOR_INVALID** (0x89) 無効なセクター
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

短い名前から長い名前を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>説明

このサービスは、指定された短い名前 (8.3 形式) に関連付けられている長い名前 (存在する場合) を取得します。 短い名前には、ファイル名またはディレクトリ名を指定できます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **short_name**: ソースの短い名前 (8.3 形式) へのポインター。
- **long_name**: 長い名前の宛先へのポインター。 長い名前がない場合は、短い名前が返されます。 注: 長い名前の宛先は、**FX_MAX_LONG_NAME_LEN** 文字を保持するのに十分な大きさである必要があることに注意してください。
- **long_file_name_buffer_length**: 長い名前バッファーの長さ。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 長い名前の取得に成功しました。
- **FX_NOT_FOUND** (0x04) 短い名前が見つかりませんでした。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

ディレクトリをテストします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>説明

このサービスは、指定された名前がディレクトリであるかどうかをテストします。 そうであれば、FX_SUCCESS が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: ディレクトリ エントリの名前へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 指定された名前はディレクトリです。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません
- **FX_NOT_FOUND** (0x04) ディレクトリ エントリが見つかりませんでした。
- **FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

次のディレクトリ エントリを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>説明

このサービスは、現在のデフォルト ディレクトリ内の次のエントリ名を返します。

> [!WARNING]
> *ローカル以外のパスを使用する場合は、ディレクトリ トラバーサルの実行中に他のアプリケーション スレッドによってこのディレクトリが変更されることを (ThreadX セマフォまたはスレッド優先度レベルにより) 防ぐことも重要です。そうでないと、無効な結果が得られる可能性があります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **return_entry_name**: デフォルト ディレクトリ内の次のエントリ名の宛先へのポインター。 このポインターが指すバッファーは、**_FX_MAX_LONG_NAME_LEN_** によって定義される FileX 名の最大サイズを保持するのに十分な大きさである必要があります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 次のエントリの検索に成功しました
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

完全な情報を含む次のディレクトリ エントリを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a>説明

このサービスは、デフォルト ディレクトリ内の次のエントリ名を取得し、指定した宛先にコピーします。 また、追加の入力パラメーターによって指定されたエントリに関する完全な情報も返します。

> [!WARNING]
> *指定された宛先は、***FX_MAX_LONG_NAME_LEN*** で定義されているように、最大サイズの FileX 名を保持するのに十分な大きさである必要があります*

> [!WARNING]
> *ローカル以外のパスを使用する場合は、ディレクトリ トラバーサルの実行中に他のアプリケーション スレッドによってこのディレクトリが変更されることを (ThreadX セマフォ、ミューテックス、または優先度レベルの変更により) 防ぐことが重要です。そうでないと、無効な結果が得られる可能性があります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **directory_name**: ディレクトリ エントリの名前の宛先を指すポインター。 **FX_MAX_LONG_NAME_LEN** 以上の大きさである必要があります。
- **attributes**: null 以外の場合、配置されるエントリの属性の宛先へのポインター。属性は、次の設定が可能なビットマップ形式で返されます。
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: null 以外の場合、エントリのサイズの宛先を指すポインター (バイト単位)。
- **month**: null 以外の場合、エントリが変更された月の宛先を指すポインター。
- **year**: null 以外の場合、エントリが変更された年の宛先を指すポインター。
- **day**: null 以外の場合、エントリが変更された日の宛先を指すポインター。
- **hour**: null 以外の場合、エントリが変更された時間の宛先を指すポインター。
- **minute**: null 以外の場合、エントリが変更された分の宛先を指すポインター。
- **second**: null 以外の場合、エントリが変更された秒の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ディレクトリ内の次のエントリの検索に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインターまたはすべての入力パラメーターが NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

ディレクトリ名を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>説明

このサービスは、ディレクトリ名を、指定された新しいディレクトリ名に変更します。 名前の変更は、指定されたパスまたはデフォルト パスに対しても実行されます。 新しいディレクトリ名にパスが指定されている場合、名前が変更されたディレクトリは指定したパスに事実上移動します。 パスが指定されていない場合、名前が変更されたディレクトリは現在のデフォルト パスに配置されます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **old_directory_name**: 現在のディレクトリ名へのポインター。
- **new_directory_name**: 新しいディレクトリ名へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ディレクトリの名前変更に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) ディレクトリ エントリが見つかりませんでした。
- **FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません。
- **FX_INVALID_NAME** (0x0C) 新しいディレクトリ名が無効です。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません。
- **FX_INVALID_PATH** (0x0D) ディレクトリ名に無効なパスが指定されています。
- **FX_ALREADY_CREATED** (0x0B) 指定されたディレクトリは既に作成されています。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

長い名前から短い名前を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>説明

このサービスは、指定された長い名前に関連付けられている短い名前 (8.3 形式) を取得します。 長い名前には、ファイル名またはディレクトリ名を指定できます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **long_name**: ソースの長い名前へのポインター。
- **short_name**: 短い名前 (8.3 形式) の宛先へのポインター。 短い名前の宛先は、14 文字を保持するのに十分な大きさである必要があることに注意してください。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 短い名前の取得に成功しました。
- **FX_NOT_FOUND** (0x04) 長い名前が見つかりませんでした。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

長い名前から短い名前を取得します

### <a name="prototype"></a>プロトタイプ

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>説明

このサービスは、指定された長い名前に関連付けられている短い名前 (8.3 形式) を取得します。 長い名前には、ファイル名またはディレクトリ名を指定できます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **long_name**: ソースの長い名前へのポインター。
- **short_name**: 短い名前 (8.3 形式) の宛先へのポインター。 注: 短い名前の宛先は、14 文字を保持するのに十分な大きさである必要があります。
- **short_file_name_length**: 短い名前のバッファーの長さ。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 短い名前の取得に成功しました。
- **FX_NOT_FOUND** (0x04) 長い名前が見つかりませんでした。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

フォールト トレラント サービスを有効にします

### <a name="prototype"></a>プロトタイプ

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>説明

このサービスは、フォールト トレラント モジュールを有効にします。 開始時に、フォールト トレラント モジュールは、ファイル システムが FileX フォールト トレラントで保護されているかどうかを検出します。 されていない場合、このサービスはファイル システム上で使用可能なセクターを検出し、ファイル システムのトランザクションに関するログを格納します。 ファイル システムが FileX フォールト トレラントで保護されている場合は、ログをファイル システムに適用して整合性を維持します。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **memory_ptr**: フォールト トレラント モジュールによってスクラッチ メモリとして使用されるメモリのブロックへのポインター。
- **memory_size**: スクラッチ メモリのサイズ。 フォールト トレラントを正常に機能させるには、スクラッチ メモリのサイズが 3072 バイト以上で、セクター サイズの倍数である必要があります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) フォールト トレラントが正常に有効になりました。
- **FX_NOT_ENOUGH_MEMORY** (0x91) メモリ サイズが小さすぎます。
- **FX_BOOT_ERROR** (0x01) ブート セクター エラー。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_NO_MORE_ENTRIES** (0x0F) 使用可能な空きクラスターがありません。
- **FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。
- **FX_SECTOR_INVALID** (0x89) セクターが無効です
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>参照

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

ファイルの領域を割り当てます

### <a name="prototype"></a>プロトタイプ

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>説明

このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。 FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。 結果はクラスター数が整数になるように切り上げられます。

4 GB を超える領域を割り当てるには、アプリケーションでサービス *fx_file_extended_allocate* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **size**: ファイルに割り当てるバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの割り当てに成功しました。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができませんでした。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_NO_MORE_ENTRIES** (0x0F) 使用可能な空きクラスターがありません。
- **FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。
- **FX_SECTOR_INVALID** (0x89) セクターが無効です
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>参照

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

ファイル属性を読み取ります

### <a name="prototype"></a>プロトタイプ

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>説明

このサービスは、指定されたメディアからファイル属性を読み取ります。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **file_name**: 要求されたファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。
- **attributes_ptr**: 配置されるファイルの属性の宛先へのポインター。 ファイル属性は、次の設定が可能なビットマップ形式で返されます。
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 属性の読み取りに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) 指定されたファイルはメディア内で見つかりませんでした。
- **FX_NOT_A_FILE** (0x05) 指定されたファイルはディレクトリです。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは属性ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

ファイル属性を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>説明

このサービスは、ファイルの属性を、呼び出し元によって指定された属性に設定します。

> [!WARNING]
> *このアプリケーションでは、このサービスを使用してファイルの属性のサブセットを変更することのみが許可されています。追加の属性を設定しようとすると、エラーが発生します。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **file_name**: 要求されたファイルの名前を指すポインター** (ディレクトリ パスは省略可能です)。
- **attributes**: ファイルの新しい属性。 有効なファイル属性は次のように定義されます。
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 属性の設定に成功しました。
- **FX_ACCESS_ERROR** (0x06) ファイルが開いているため属性を設定できません。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT テーブルまたは exFAT クラスター マップにはこれ以上エントリがありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_NOT_FOUND** (0x04) 指定されたファイルはメディア内で見つかりませんでした。
- **FX_NOT_A_FILE** (0x05) 指定されたファイルはディレクトリです。
- **FX_SECTOR_INVALID** (0x89) セクターが無効です
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_INVALID_ATTR** (0x19) 無効な属性が選択されました。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

ファイルの領域をベスト エフォートで割り当てます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>説明

このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。 FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。 結果はクラスター数が整数になるように切り上げられます。 利用可能な連続するクラスターがメディア内に不足している場合、このサービスでは、利用可能な最大の連続するクラスターのブロックをファイルにリンクします。 ファイルに実際に割り当てられた領域の量が呼び出し元に返されます。

4 GB を超える領域を割り当てるには、アプリケーションでサービス *fx_file_extended_best_effort_allocate* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **size**: ファイルに割り当てるバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ベストエフォートのファイル割り当てに成功しました。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインターまたは宛先。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

ファイルを閉じます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>説明

このサービスは、指定されたファイルをクローズします。 ファイルが書き込み用に開かれており、ファイルが変更されている場合、このサービスは、新しいサイズと現在のシステム時刻および日付を使用してディレクトリ エントリを更新することで、ファイル変更プロセスを完了します。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルのクローズに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは属性ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

ファイルを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>説明

このサービスは、指定されたファイルを、デフォルト ディレクトリまたはファイル名と共に指定されたディレクトリ パスに作成します。

> [!WARNING]
> *このサービスでは、長さゼロのファイルが作成されます。つまり、クラスターが割り当てられません。割り当ては、以降のファイルの書き込み時に自動的に実行されます。または、fx_file_allocate サービス (または 4 GB を超える領域の場合は fx_file_extended_allocate サービス) で事前に行うことができます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **file_name**: 作成するファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの作成に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_ALREADY_CREATED** (0x0B) 指定されたファイルは既に作成されています。
- **FX_NO_MORE_SPACE** (0x0A) ルート ディレクトリにエントリがこれ以上存在しないか、使用可能なクラスターがありません。
- **FX_INVALID_PATH** (0x0D) ファイル名に無効なパスが指定されています。
- **FX_INVALID_NAME** (0x0C) ファイル名が無効です。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはファイル名のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>参照
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>ファイルの日付と時刻を設定します

ファイルの日付と時刻の設定

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a>説明

このサービスは、指定されたファイルの日付と時刻を設定します。

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **file_name**: ファイルの名前へのポインター。
- **year**: 年の値 (1980 から 2107、両端を含む)。
- **month**: 月の値 (1 から 12、両端を含む)。
- **day**: 日の値 (1 から 31、両端を含む)。
- **hour**: 時間の値 (0 から 23、両端を含む)。
- **minute**: 分の値 (0 から 59、両端を含む)。
- **second**: 秒の値 (0 から 59、両端を含む)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 日付/時刻の設定に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) ファイルが見つかりませんでした。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。
- **FX_INVALID_YEAR** (0x12) 年が無効です。
- **FX_INVALID_MONTH** (0x13) 月が無効です。
- **FX_INVALID_DAY** (0x14) 日が無効です。
- **FX_INVALID_HOUR** (0x15) 時間が無効です。
- **FX_INVALID_MINUTE** (0x16) 分が無効です。
- **FX_INVALID_SECOND** (0x17) 秒が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>ファイルを削除します

ファイルの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>説明

このサービスは、指定されたファイルを削除します。


### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **file_name**: 削除するファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの削除に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) 指定されたファイルは見つかりませんでした。
- **FX_NOT_A_FILE** (0x05) 指定されたファイル名はディレクトリまたはボリュームでした。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルは現在開いています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

ファイルの領域を割り当てます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>説明

このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。 FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。 結果はクラスター数が整数になるように切り上げられます。

このサービスは、exFAT 向けに設計されています。 *size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて領域を事前に割り当てることができます。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **size**: ファイルに割り当てるバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの割り当てに成功しました。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

ファイルの領域をベスト エフォートで割り当てます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>説明

このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。 FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。 結果はクラスター数が整数になるように切り上げられます。 利用可能な連続するクラスターがメディア内に不足している場合、このサービスでは、利用可能な最大の連続するクラスターのブロックをファイルにリンクします。 ファイルに実際に割り当てられた領域の量が呼び出し元に返されます。

このサービスは、exFAT 向けに設計されています。 *size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて領域を事前に割り当てることができます。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **size**: ファイルに割り当てるバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの割り当てに成功しました。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

相対バイト オフセットに配置します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>説明

このサービスは、指定された相対バイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。 それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。

このサービスは、exFAT 向けに設計されています。 *byte_offset* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は読み取り/書き込みポインターを 4 GB の範囲を超えて再配置できます。

> [!IMPORTANT]
> *シーク操作がファイルの末尾を越えてシークしようとすると、ファイルの読み取り/書き込みポインターはファイルの末尾に配置されます。逆に、シーク操作によってファイルの先頭を越える位置に移動しようとすると、ファイルの読み取り/書き込みポインターはファイルの先頭に配置されます。*

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **byte_offset**: ファイル内の目標の相対バイト オフセット。
- **seek_from**: 相対シークの実行元の方向と位置。 有効なシーク オプションは次のように定義されます。
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03) FX_SEEK_BEGIN を指定した場合、シーク操作はファイルの先頭から実行されます。 FX_SEEK_END を指定した場合、シーク操作はファイルの末尾からさかのぼって実行されます。 FX_SEEK_FORWARD を指定した場合、シーク操作は現在のファイルの位置から順に実行されます。 FX_SEEK_BACK を指定した場合、シーク操作は現在のファイルの位置からさかのぼって実行されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの相対シークに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

バイト オフセットに配置します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>説明

このサービスは、指定されたバイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。 それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。

このサービスは、exFAT 向けに設計されています。 *byte_offset* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は読み取り/書き込みポインターを 4 GB の範囲を超えて再配置できます。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **byte_offset**: ファイル内の目標のバイト オフセット。 値を 0 にすると、読み取り/書き込みポインターがファイルの先頭に配置され、ファイルのサイズより大きい値にすると、読み取り/書き込みポインターがファイルの末尾に配置されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルのシークに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

ファイルを切り捨てます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>説明

このサービスは、指定されたサイズにファイルのサイズを切り捨てます。 指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。 ファイルに関連付けられているメディア クラスターは解放されません。

> [!WARNING]
> *読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*

このサービスは、exFAT 向けに設計されています。 *size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて動作できます。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **size**: 新しいファイル サイズ。 この新しいファイル サイズを超えるバイトは破棄されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

ファイルを切り捨ててクラスターを解放します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>説明

このサービスは、指定されたサイズにファイルのサイズを切り捨てます。 指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。 ***fx_file_extended_truncate*** サービスとは異なり、このサービスでは未使用のクラスターが解放されます。

> [!WARNING]
> *読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*

このサービスは、exFAT 向けに設計されています。 *size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて動作できます。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **size**: 新しいファイル サイズ。 この新しいファイル サイズを超えるバイトは破棄されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

ファイルを開きます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>説明

このサービスは、指定されたファイルを読み取りまたは書き込み用に開きます。 ファイルは、読み取り用には複数回開くことができますが、書き込み用には、書き込み側がファイルを閉じるまで 1 回だけ開くことができます。

> [!IMPORTANT]
> *ファイルを読み取りと書き込み用に同時に開いている場合は、注意が必要です。読み取り用にファイルを開くのと同時に実行されたファイルの書き込みは、読み取り側がファイルを閉じて再度読み取り用に開かない限り、読み取り側に表示されない場合があります。同様に、ファイルの書き込み側はファイルの切り捨てサービスを使用する場合に注意する必要があります。ファイルが書き込み側によって切り捨てられた場合、同じファイルの読み取り側が無効なデータを返す可能性があります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **file_ptr**: ファイル制御ブロックへのポインター。
- **file_name**: 開くファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。
- **open_type**: ファイルのオープンの型。 オープンの型の有効なオプションは次のとおりです。
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

FX_OPEN_FOR_READ および FX_OPEN_FOR_READ_FAST でのファイルのオープンは類似しています。

- FX_OPEN_FOR_READ では、ファイルを構成するクラスターのリンクされたリストが破損していないことを検査します。 FX_OPEN_FOR_READ_FAST では、この検査が行われないため、処理が高速になります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルのオープンに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) 指定されたファイルは見つかりませんでした。
- **FX_NOT_A_FILE** (0x05) 指定されたファイル名はディレクトリまたはボリュームでした。
- **FX_FILE_CORRUPT** (0x08) 指定されたファイルが壊れており、開けませんでした。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが既に開いているか、オープンの型が無効です。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_MEDIA_INVALID** (0x02) 無効なメディア。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

ファイルからバイトを読み取ります

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>説明

このサービスは、ファイルからバイトを読み取り、指定されたバッファーに格納します。 読み取りが完了すると、ファイルの内部読み取りポインターは、ファイル内の次のバイトを指すように調整されます。 要求に残っているバイトが少ない場合、残っているバイトだけがバッファーに格納されます。 いずれの場合も、バッファーに配置されたバイトの総数が、呼び出し元に返されます。

> [!WARNING]
> *アプリケーションでは、指定されたバッファーが、指定された数の要求バイトを格納できるようにする必要があります。*

> [!WARNING]
> *宛先バッファーが長いワード境界にあり、要求されたサイズが sizeof (**ULONG**) で均等に割り切れる場合、パフォーマンスが向上します。*

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **buffer_ptr**: 読み取り用の宛先バッファーへのポインター。
- **request_size**: 読み取る最大バイト数。
- **actual_size**: 指定されたバッファーに読み取られた実際のバイト数を保持する変数へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの読み取りに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_FILE_CORRUPT** (0x08) 指定されたファイルが壊れており、読み取れませんでした。
- **FX_END_OF_FILE** (0x09) ファイルの終わりに達しました。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なファイルまたはバッファー ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a>参照

- fx_file_allocate、
- fx_file_attributes_read、
- fx_file_attributes_set、
- fx_file_best_effort_allocate、
- fx_file_close、
- fx_file_create、
- fx_file_date_time_set、
- fx_file_delete、
- fx_file_extended_allocate、
- fx_file_extended_best_effort_allocate、
- fx_file_extended_relative_seek、
- fx_file_extended_seek、
- fx_file_extended_truncate、
- fx_file_extended_truncate_release、
- fx_file_open、
- fx_file_relative_seek、
- fx_file_rename、
- fx_file_seek、
- fx_file_truncate、
- fx_file_truncate_release、
- fx_file_write、
- fx_file_write_notify_set、
- fx_unicode_file_create、
- fx_unicode_file_rename、
- fx_unicode_name_get、
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

相対バイト オフセットに配置します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>説明

このサービスは、指定された相対バイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。 それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。

> [!IMPORTANT]
> *シーク操作がファイルの末尾を越えてシークしようとすると、ファイルの読み取り/書き込みポインターはファイルの末尾に配置されます。逆に、シーク操作によってファイルの先頭を越える位置に移動しようとすると、ファイルの読み取り/書き込みポインターはファイルの先頭に配置されます。*

4 GB を超えるオフセット値を使用してシークするには、アプリケーションでサービス *fx_file_extended_relative_seek* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **byte_offset**: ファイル内の目標の相対バイト オフセット。
- **seek_from**: 相対シークの実行元の方向と位置。 有効なシーク オプションは次のように定義されます。
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

FX_SEEK_BEGIN を指定した場合、シーク操作はファイルの先頭から実行されます。 FX_SEEK_END を指定した場合、シーク操作はファイルの末尾からさかのぼって実行されます。 FX_SEEK_FORWARD を指定した場合、シーク操作は現在のファイルの位置から順に実行されます。 FX_SEEK_BACK を指定した場合、シーク操作は現在のファイルの位置からさかのぼって実行されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの相対シークに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

ファイルの名前を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>説明

このサービスは、*old_file_name* によって指定されたファイルの名前を変更します。 名前の変更は、指定されたパスまたはデフォルト パスに対しても実行されます。 新しいファイル名にパスが指定されている場合、名前が変更されたファイルは指定したパスに事実上移動します。 パスが指定されていない場合、名前が変更されたファイルは現在のデフォルト パスに配置されます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **old_file_name**: 名前を変更するファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。
- **new_file_name**: 新しいファイル名へのポインター。 ディレクトリ パスは許可されていません。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの名前変更に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) 指定されたファイルは見つかりませんでした。
- **FX_NOT_A_FILE** (0x05) 指定されたファイルはディレクトリです。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルは既に開いています。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_INVALID_NAME** (0x0C) 指定された新しいファイル名は有効なファイル名ではありません。
- **FX_INVALID_PATH** (0x0D) パスが無効です。
- **FX_ALREADY_CREATED** (0x0B) 新しいファイル名は使用されています。
- **FX_MEDIA_INVALID** (0x02) メディアが無効です。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

バイト オフセットに配置します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>説明

このサービスは、指定されたバイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。 それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。

4 GB を超えるオフセット値を使用してシークするには、アプリケーションでサービス *fx_file_extended_seek* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **byte_offset**: ファイル内の目標のバイト オフセット。 値を 0 にすると、読み取り/書き込みポインターがファイルの先頭に配置され、ファイルのサイズより大きい値にすると、読み取り/書き込みポインターがファイルの末尾に配置されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルのシークに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

ファイルを切り捨てます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>説明

このサービスは、指定されたサイズにファイルのサイズを切り捨てます。 指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。 ファイルに関連付けられているメディア クラスターは解放されません。

> [!WARNING]
> *読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*

4 GB を超える操作を行うには、アプリケーションでサービス *fx_file_extended_truncate* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **size**: 新しいファイル サイズ。 この新しいファイル サイズを超えるバイトは破棄されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

ファイルを切り捨ててクラスターを解放します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>説明

このサービスは、指定されたサイズにファイルのサイズを切り捨てます。 指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。 ***fx_file_truncate*** サービスとは異なり、このサービスでは未使用のクラスターが解放されます。

> [!WARNING]
> *読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*

4 GB を超える操作を行うには、アプリケーションでサービス *fx_file_extended_truncate_release* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: 以前に開いたファイルへのポインター。
- **size**: 新しいファイル サイズ。 この新しいファイル サイズを超えるバイトは破棄されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。
- **FX_PTR_ERROR** (0x18) 無効なファイル ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

ファイルにバイトを書き込みます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>説明

このサービスは、ファイルの現在位置を開始位置として、指定されたバッファーからバイトを書き込みます。 書き込みが完了すると、ファイルの内部読み取りポインターは、ファイル内の次のバイトを指すように調整されます。

> [!WARNING]
> *ソース バッファーが長いワード境界にあり、要求されたサイズが sizeof (**ULONG**) で均等に割り切れる場合、パフォーマンスが向上します。*

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **buffer_ptr**: 書き込み用のソース バッファーへのポインター。
- **size**: 書き込むバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの書き込みに成功しました。
- **FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。
- **FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。
- **FX_NO_MORE_SPACE** (0x0A) この書き込みを実行するための空き領域がメディアにありません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。
- **FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。
- **FX_PTR_ERROR** (0x18) 無効なファイルまたはバッファー ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>参照

- fx_file_allocate、
- fx_file_attributes_read、
- fx_file_attributes_set、
- fx_file_best_effort_allocate、
- fx_file_close、
- fx_file_create、
- fx_file_date_time_set、
- fx_file_delete、
- fx_file_extended_allocate、
- fx_file_extended_best_effort_allocate、
- fx_file_extended_relative_seek、
- fx_file_extended_seek、
- fx_file_extended_truncate、
- fx_file_extended_truncate_release、
- fx_file_open、
- fx_file_read、
- fx_file_relative_seek、
- fx_file_rename、
- fx_file_seek、
- fx_file_truncate、
- fx_file_truncate_release、
- fx_file_write_notify_set、
- fx_unicode_file_create、
- fx_unicode_file_rename、
- fx_unicode_name_get、
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

ファイル書き込み通知関数を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>説明

このサービスは、ファイル書き込み操作に成功した後に呼び出されるコールバック関数をインストールします。

### <a name="input-parameters"></a>入力パラメーター

- **file_ptr**: ファイル制御ブロックへのポインター。
- **file_write_notify**: インストールするファイル書き込みコールバック関数。 コールバック関数を NULL に設定すると、コールバック関数が無効になります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) コールバック関数が正常にインストールされました。
- **FX_PTR_ERROR** (0x18) file_ptr が NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

メディア アクティビティを中止します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>説明

このサービスは、メディアに関連付けられている現在のすべてのアクティビティを中止します。たとえば、開いているすべてのファイルを閉じ、関連付けられているドライバーに中止要求を送信し、メディアを中止状態にします。 このサービスは通常、I/O エラーが検出されたときに呼び出されます。

> [!WARNING]
> *中止操作の実行後にメディアを再度使用するには、再度開く必要があります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアの中止に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

論理セクター キャッシュを無効にします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>説明

このサービスは、キャッシュ内のすべてのダーティ セクターをフラッシュし、論理セクター キャッシュ全体を無効にします。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア キャッシュの無効化に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはスクラッチ ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

メディアにエラーがないかチェックします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>説明

このサービスは、ファイルまたはディレクトリのクロスリンク、無効な FAT チェーン、および失われたクラスターなど、指定されたメディアの基本的な構造エラーを確認します。 このサービスには、検出されたエラーを修正する機能も用意されています。

fx_media_check サービスでは、メディア内のディレクトリとファイルの深さ優先分析用のスクラッチ メモリが必要です。 具体的には、メディア チェック サービスに提供されるスクラッチ メモリは、複数のディレクトリ エントリ、サブディレクトリに入る前に現在のディレクトリ エントリの位置を "スタック" するデータ構造、そして論理的な FAT のビットマップを保持するのに十分な大きさである必要があります。 スクラッチ メモリには、少なくとも 512 から 1024 バイトと、論理的な FAT のビットマップ用のメモリが必要で、これにはメディア内のクラスターと同じ数のビットが必要です。 たとえば、8000 クラスターを持つデバイスを表すのに 1000 バイトが必要な場合、必要なスクラッチ領域の合計は約 2048 バイトとなります。

> [!WARNING]
> *このサービスは、fx_media_open の直後に、他のファイル システムの活動がないときにのみ呼び出す必要があります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **scratch_memory_ptr**: スクラッチ メモリの先頭へのポインター。
- **scratch_memory_size**: スクラッチ メモリのサイズ (バイト単位)。
- **error_correction_option**: エラー修正オプション ビット。ビットが設定されると、エラー修正が実行されます。 エラー修正オプション ビットは次のように定義されています。
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) 必要なエラー修正オプションを単純に、または組み合わせて指定します。 エラー修正が不要な場合は、値 0 を指定する必要があります。
- **errors_detected_ptr**: 下のように定義されているエラー検出ビットの宛先。
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア チェックに成功し、検出されたエラーの詳細を確認します。
- **FX_ACCESS_ERROR** (0x06) 開いているファイルでチェックを実行できません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NO_MORE_SPACE** (0x0A) メディアに空き領域がありません。
- **FX_NOT_ENOUGH_MEMORY** (0x91) 指定されたスクラッチ メモリの大きさが十分ではありません。
- **FX_ERROR_NOT_FIXED** (0x93) 修正できない FAT32 ルート ディレクトリの破損。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_SECTOR_INVALID** (0x89) セクターが無効です。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはスクラッチ ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

メディアをクローズします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>説明

このサービスは、指定されたメディアをクローズします。 メディアをクローズするプロセスでは、開いているすべてのファイルがクローズされ、残っているバッファーは物理メディアにフラッシュされます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアのクローズに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

メディア クローズ通知関数を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>説明

このサービスは、メディアのクローズに成功した後に呼び出される通知コールバック関数を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **media_close_notify**: インストールされるメディア クローズ通知コールバック関数。 コールバック関数として NULL を渡すと、メディア クローズ コールバックが無効になります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) コールバック関数が正常にインストールされました。
- **FX_PTR_ERROR** (0x18) media_ptr is が NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

メディアをフォーマットします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a>説明

このサービスは、指定されたパラメーターに基づいて、指定されたメディアを exFAT 互換の方法でフォーマットします。 このサービスは、メディアを開く前に呼び出す必要があります。

> [!WARNING]
> *既にフォーマットされたメディアをフォーマットすると、メディア上のすべてのファイルとディレクトリが実質的に消去されます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。 これは、ドライバーが動作するために必要な基本的な情報を提供するためにのみ使用されます。
- **driver**: このメディアの I/O ドライバーへのポインター。 これは通常、後続の fx_media_open 呼び出しに指定されたドライバーと同じです。
- **driver_info_ptr**: I/O ドライバーが使用できるオプション情報へのポインター。
- **memory_ptr**: メディアの作業メモリへのポインター。 memory_size: 作業メディア メモリのサイズを指定します。 サイズは、メディアのセクター サイズ以上である必要があります。
- **volume_name**: 最大 11 文字のボリューム名の文字列を指すポインター。
- **number_of_fats**: メディア内の FAT の数。 現在の実装では、メディア上に 1 つの FAT がサポートされています。
- **hidden_sectors**: このメディアのブート セクターの前に隠されたセクターの数。 これは複数のパーティションが存在する場合に一般的です。
- **total_sectors**: メディア内のセクターの合計数。
- **bytes_per_sector**: 1 セクターあたりのバイト数 (通常は 512)。 FileX では 32 の倍数である必要があります。
- **sectors_per_cluster**: 各クラスター内のセクター数。 クラスターは FAT ファイル システムの最小のアロケーション ユニットです。
- **volumne_serial_number**: このボリュームに使用するシリアル番号。
- **boundary_unit**: 物理データ領域の配置サイズ (セクターの数)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアのフォーマットに成功しました。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディア、ドライバー、またはメモリ ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

利用可能なメディア領域を返します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>説明

このサービスは、メディアで使用可能なバイト数を返します。

このサービスは、exFAT 向けに設計されています。 *available_bytes* パラメーターへのポインターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB を超えるメディアを操作できます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: 以前に開いたメディアへのポインター。
- **available_bytes_ptr**: メディアに残っている使用可能なバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア上の使用可能な領域を正常に取得しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_PTR_ERROR** (0x18) 無効なメディアポインターまたは使用可能なバイト ポインターが NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

物理メディアにデータをフラッシュします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>説明

このサービスは、変更されたファイルのキャッシュされたセクターとディレクトリ エントリを物理メディアにフラッシュします。

> [!WARNING]
> *このルーチンは、ターゲットで突然電力が失われた場合に、ファイルの破損やデータ損失のリスクを軽減するために、アプリケーションによって定期的に呼び出されることがあります。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアのフラッシュに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

メディアをフォーマットします

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a>説明

このサービスは、指定されたパラメーターに基づいて、指定されたメディアを FAT 12/16/32 互換の方法でフォーマットします。 このサービスは、メディアを開く前に呼び出す必要があります。

> [!WARNING]
> *既にフォーマットされたメディアをフォーマットすると、メディア上のすべてのファイルとディレクトリが実質的に消去されます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。 これは、ドライバーが動作するために必要な基本的な情報を提供するためにのみ使用されます。
- **driver**: このメディアの I/O ドライバーへのポインター。 これは通常、後続の fx_media_open 呼び出しに指定されたドライバーと同じです。
- **driver_info_ptr**: I/O ドライバーが使用できるオプション情報へのポインター。
- **memory_ptr**: メディアの作業メモリへのポインター。
- **memory_size**: 作業メディア メモリのサイズを指定します。 サイズは、メディアのセクター サイズ以上である必要があります。
- **volume_name**: 最大 11 文字のボリューム名の文字列を指すポインター。
- **number_of_fats**: メディア内の FAT の数。 最小値は、プライマリ FAT を示す 1 になります。 1 より大きい値を指定すると、FAT の追加のコピーが実行時に維持されます。
- **directory_entries**: ルート ディレクトリ内のディレクトリ エントリの数。
- **hidden_sectors**: このメディアのブート セクターの前に隠されたセクターの数。 これは複数のパーティションが存在する場合に一般的です。
- **total_sectors**: メディア内のセクターの合計数。
- **bytes_per_sector**: 1 セクターあたりのバイト数 (通常は 512)。 FileX では 32 の倍数である必要があります。
- **sectors_per_cluster**: 各クラスター内のセクター数。 クラスターは FAT ファイル システムの最小のアロケーション ユニットです。
- **head**: 物理ヘッドの数。
- **sectors_per_track**: 1 トラックあたりのセクター数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアのフォーマットに成功しました。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディア、ドライバー、またはメモリ ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

ファイル アクセス用のメディアを開きます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>説明

このサービスは、指定された I/O ドライバーを使用してファイル アクセス用のメディアを開きます。

> [!WARNING]
> *このサービスに提供されるメモリは、内部論理セクター キャッシュの実装に使用されるため、提供されるメモリが多くなるほど、多くの物理 I/O が削減されます。FileX では、少なくとも 1 つの論理セクター (メディアの 1 セクターあたりのバイト数) のキャッシュが必要です。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **media_name**: メディアの名前へのポインター。
- **media_driver**: このメディアの I/O ドライバーへのポインター。 I/O ドライバーは、5 章で定義されている FileX ドライバーの要件に準拠している必要があります。
- **driver_info_ptr**: 指定された I/O ドライバーが使用できるオプション情報へのポインター。
- **memory_ptr**: メディアの作業メモリへのポインター。
- **memory_size**: 作業メディア メモリのサイズを指定します。 サイズはメディアのセクター サイズ (通常は 512 バイト) の大きさにする必要があります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアのオープンに成功しました。
- **FX_BOOT_ERROR** (0x01) メディアのブート セクターの読み取り中にエラーが発生しました。
- **FX_MEDIA_INVALID** (0x02) 指定されたメディアのブート セクターが破損しているか無効です。 また、このリターン コードは、論理セクター キャッシュのサイズまたは FAT エントリのサイズのいずれかが 2 の累乗でないことを示すために使用されます。
- **FX_FAT_READ_ERROR** (0x03) メディア FAT の読み取り中にエラーが発生しました。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 1 つ以上のポインターが NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

メディア オープン通知関数を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>説明

このサービスは、メディアのオープンに成功した後に呼び出される通知コールバック関数を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **media_open_notify**: インストールされるメディア オープン通知コールバック関数。 コールバック関数として NULL を渡すと、メディア オープン コールバックが無効になります。

### <a name="return-values"></a>戻り値


- **FX_SUCCESS** (0x00) コールバック関数が正常にインストールされました。
- **FX_PTR_ERROR** (0x18) media_ptr is が NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

メディアから論理セクターを読み取ります

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>説明

このサービスは、メディアから論理セクターを読み取り、指定されたバッファーに格納します。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: 以前に開いたメディアへのポインター。
- **logical_sector**: 読み取る論理セクター。
- **buffer_ptr**: 読み取る論理セクターの宛先へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアの読み取りに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはバッファー ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

利用可能なメディア領域を返します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>説明

このサービスは、メディアで使用可能なバイト数を返します。

4 GB を超えるメディアを使用するには、アプリケーションでサービス *fx_media_extended_space_available* を使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: 以前に開いたメディアへのポインター。
- **available_bytes_ptr**: メディアに残っている使用可能なバイト数。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア上の使用可能な領域を正常に返しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_PTR_ERROR** (0x18) 無効なメディアポインターまたは使用可能なバイト ポインターが NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

メディアのボリューム名を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>説明

このサービスは、以前に開いたメディアのボリューム名を取得します。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **volume_name**: ボリューム名の宛先へのポインター。 宛先は、12 文字を保持するのに十分な大きさである必要があることに注意してください。
- **volume_source**: 名前を取得する場所を、ブート セクターまたはルート ディレクトリのいずれかから指定します。 このパラメーターの有効な値は次のとおりです。
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア ボリュームの取得に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) ボリュームが見つかりません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはボリュームの宛先ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

以前に開いたメディアのメディア ボリューム名を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>説明

このサービスは、以前に開いたメディアのボリューム名を取得します。

> [!IMPORTANT]
> このサービスは ***fx_media_volume_get ()** _ と同じですが、呼び出し元が _ *volume_name** バッファーのサイズを渡す点が異なります。

### <a name="input-parameters"></a>入力パラメーター


- **media_ptr**: メディア コントロール ブロックへのポインター。
- **volume_name**: ボリューム名の宛先へのポインター。 宛先は、12 文字を保持するのに十分な大きさである必要があることに注意してください。
- **volume_name_buffer_length**: volume_name バッファーのサイズ。
- **volume_source**: 名前を取得する場所を、ブート セクターまたはルート ディレクトリのいずれかから指定します。 このパラメーターの有効な値は次のとおりです。
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア ボリュームの取得に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) ボリュームが見つかりません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはボリュームの宛先ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

メディアのボリューム名を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>説明

このサービスは、以前に開いたメディアのボリューム名を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **volume_name**: ボリューム名へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディア ボリュームの設定に成功しました。
- **FX_INVALID_NAME** (0x0C) Volume_name が無効です。
- **FX_MEDIA_INVALID** (0x02) ボリューム名を設定できません。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたはボリューム名のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

論理セクターを書き込みます

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>説明

このサービスは、指定されたバッファーを指定された論理セクターに書き込みます。

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: 以前に開いたメディアへのポインター。
- **logical_sector**: 書き込む論理セクター。
- **buffer_ptr**: 論理セクター書き込みのソースへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアの書き込みに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディア ポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a>参照

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

ファイル システム日付を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>説明

このサービスは、現在のシステム日付を返します。

### <a name="input-parameters"></a>入力パラメーター

- **year**: 年の宛先へのポインター。
- **month**: 月の宛先へのポインター。
- **day**: 日の宛先へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 日付の取得に成功しました。
- **FX_PTR_ERROR** (0x18) 1 つ以上の入力パラメーターが NULL です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a>参照

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

システム日付を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>説明

このサービスは、指定されたシステム日付を設定します。

> [!WARNING]
> *このサービスは、最初のシステム日付を設定するために **fx_system_initialize** の直後に呼び出す必要があります。既定では、システム日付は最後の汎用 FileX リリースの日付です。*

### <a name="input-parameters"></a>入力パラメーター

- **year**: 新しい年。 有効な範囲は 1980 年から 2107 年までです。
- **month**: 新しい月。 有効な範囲は 1 から 12 までです。
- **day**: 新しい日付。 有効な範囲は、月と閏年の条件に応じて 1 から 31 までです。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 日付の設定に成功しました。
- **FX_INVALID_YEAR** (0x12) 無効な年が指定されました。
- **FX_INVALID_MONTH** (0x13) 無効な月が指定されました。
- **FX_INVALID_DAY** (0x14) 無効な日付が指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>参照

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

システム全体を初期化します

### <a name="prototype"></a>プロトタイプ

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>説明

このサービスは、すべての主要な FileX データ構造を初期化します。 これは ***tx_application_define*** または初期化スレッドから呼び出す必要があり、他の FileX サービスを使用する前に呼び出す必要があります。

> [!WARNING]
> \* この呼び出しによって初期化されると、アプリケーションは正確なシステム日付と時刻で開始するために、***fx_system_date_set** _ および _ *fx_system_time_set** を呼び出す必要があります。*

### <a name="input-parameters"></a>入力パラメーター

None

### <a name="return-values"></a>戻り値

[なし] :

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a>参照

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

現在のシステム時刻を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>説明

このサービスは、現在のシステム時刻を取得します。

### <a name="input-parameters"></a>入力パラメーター

- **hour**: 時間の宛先へのポインター。
- **minute**: 分の宛先へのポインター。
- **second**: 秒の宛先へのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) システム時刻の取得に成功しました。
- **FX_PTR_ERROR** (0x18) 1 つ以上の入力パラメーター

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a>参照

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

現在のシステム時刻を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>説明

このサービスは、現在のシステム時刻を、入力パラメーターによって指定されたものに設定します。

> [!WARNING]
> *このサービスは、最初のシステム時刻を設定するために **fx_system_initialize** の直後に呼び出す必要があります。既定では、システム時刻は0:0:0 です。*

### <a name="input-parameters"></a>入力パラメーター

- **hour**: 新しい時間 (0 から 23)。
- **minute**: 新しい分 (0 から 59)。
- **second**: 新しい秒 (0 から 59)。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) システム時刻の取得に成功しました。
- **FX_INVALID_HOUR** (0x15) 新しい時間が無効です。
- **FX_INVALID_MINUTE** (0x16) 新しい分が無効です。
- **FX_INVALID_SECOND** (0x17) 新しい秒が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>参照

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

Unicode ディレクトリを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>説明

このサービスでは、Unicode 名が付いたサブディレクトリが現在のデフォルト ディレクトリに作成されます。Unicode ソース名パラメーターではパス情報は使用できません。 成功した場合は、新しく作成された Unicode サブディレクトリの短い名前 (8.3 形式) がサービスによって返されます。

> [!WARNING]
> *Unicode サブディレクトリに対するすべての操作 (デフォルト パスへの設定、削除など) は、返された短い名前 (8.3 形式) を標準の FileX ディレクトリ サービスに渡すことによって行う必要があります。*

> [!IMPORTANT]
> *このサービスは、exFAT メディアではサポートされていません。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **source_unicode_name**: 新しいサブディレクトリの Unicode 名へのポインター。
- **source_unicode_length**: Unicode 名の長さ。
- **short_name**: 新しい Unicode サブディレクトリの短い名前 (8.3 形式) の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) Unicode ディレクトリの作成に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_ALREADY_CREATED** (0x0B) 指定されたディレクトリは既に存在します。
- **FX_NO_MORE_SPACE** (0x0A) 新しいディレクトリ エントリについて使用できるクラスターはメディア内にこれ以上ありません。
- **FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。
- **FX_IO_ERROR (0x90)** ドライバーの I/O エラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

Unicode 文字列を使用してディレクトリの名前を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>説明

このサービスは、現在の作業ディレクトリ内で、Unicode 名が付いたサブディレクトリを指定された新しい Unicode 名に変更します。 Unicode 名のパラメーターにパス情報を指定することはできません。

> [!IMPORTANT]
> *このサービスは、exFAT メディアではサポートされていません。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **old_unicode_name**: 現在のファイルの Unicode 名へのポインター。
- **old_unicode_name_length**: 現在の Unicode 名の長さ。
- **new_unicode_name**: 新しい Unicode ファイル名へのポインター。
- **old_unicode_name_length**: 新しい Unicode 名の長さ。
- **new_short_name**: 名前が変更された Unicode ファイルの短い名前 (8.3 形式) の宛先を指すポインター。 Unicode でディレクトリ名を変更する

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) メディアのオープンに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_ALREADY_CREATED** (0x0B) 指定されたディレクトリ名は既に存在します。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 1 つ以上のポインターが NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>参照

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

Unicode ファイルを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>説明

このサービスでは、Unicode 名が付いたファイルが現在のデフォルト ディレクトリに作成されます。Unicode ソース名パラメーターではパス情報は使用できません。 成功した場合は、新しく作成された Unicode ファイルの短い名前 (8.3 形式) がサービスによって返されます。

> [!WARNING]
> *Unicode ファイルに対するすべての操作 (開く、書き込み、読み取り、終了など) は、返された短い名前 (8.3 形式) を標準の FileX ファイル サービスに渡すことによって行う必要があります。*

### <a name="input-parameters"></a>入力パラメーター


- **media_ptr**: メディア コントロール ブロックへのポインター。
- **source_unicode_name**: 新しいファイルの Unicode 名へのポインター。
- **source_unicode_length**: Unicode 名の長さ。
- **short_name**: 新しい Unicode ファイルの短い名前 (8.3 形式) の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) ファイルの作成に成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_ALREADY_CREATED** (0x0B) 指定されたファイルは既に存在します。
- **FX_NO_MORE_SPACE** (0x0a) 新しいファイル エントリについて使用できるクラスターはメディア内にこれ以上ありません。
- **FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

Unicode 文字列を使用してファイルの名前を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>説明

このサービスは、現在のデフォルト ディレクトリ内で、Unicode 名が付いたファイル名を、指定された新しい Unicode 名に変更します。 Unicode 名のパラメーターにパス情報を指定することはできません。

> [!IMPORTANT]
> *このサービスは、exFAT メディアではサポートされていません。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **old_unicode_name**: 現在のファイルの Unicode 名へのポインター。
- **old_unicode_name_length**: 現在の Unicode 名の長さ。
- **new_unicode_name**: 新しい Unicode ファイル名へのポインター。
- **new_unicode_name_length**: 新しい Unicode 名の長さ。
- **new_short_name**: 名前が変更された Unicode ファイルの短い名前 (8.3 形式) の宛先を指すポインター。

### <a name="return-values"></a>戻り値


- **FX_SUCCESS** (0x00) メディアのオープンに成功しました。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_ALREADY_CREATED** (0x0B) 指定されたファイル名は既に存在します。
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_PTR_ERROR** (0x18) 1 つ以上のポインターが NULL です。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。
- **FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

Unicode 名の長さを取得します

### <a name="prototype"></a>プロトタイプ

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>説明

このサービスは、指定された Unicode 名の長さを判断します。 Unicode 文字は 2 バイトで表されます。 Unicode 名は一連の 2 バイトの Unicode 文字で、2 つの NULL バイト (値 0 の 2 バイト) で終了します。

### <a name="input-parameters"></a>入力パラメーター

**unicode_name**: Unicode 名へのポインター。

### <a name="return-values"></a>戻り値

**length**: Unicode 名の長さ (名前に含まれる Unicode 文字の数)。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

Unicode 名の長さを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>説明

このサービスは、指定された Unicode 名の長さを取得します。 Unicode 文字は 2 バイトで表されます。 Unicode 名は一連の 2 バイトの Unicode 文字で、2 つの NULL バイト (値 0 の 2 バイト) で終了します。

> [!IMPORTANT]
> *このサービスは **fx_unicode_length_get()** と同じですが、呼び出し元が、2 つの NULL 文字を含む **unicode_name** バッファーのサイズを渡す点が異なります。*

### <a name="input-parameters"></a>入力パラメーター

- **unicode_name**: Unicode 名へのポインター。
- **buffer_length**: Unicode 名のバッファーのサイズ。

### <a name="return-values"></a>戻り値

**length**: Unicode 名の長さ (名前に含まれる Unicode 文字の数)。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

短い名前から Unicode 名を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>説明

このサービスは、現在のデフォルト ディレクトリ内の指定された短い名前 (8.3 形式) に関連付けられている Unicode 名を取得します。短い名前のパラメーターではパス情報は使用できません。 成功した場合、短い名前に関連付けられている Unicode 名がサービスによって返されます。

> [!IMPORTANT]
> *このサービスを使用して、ファイルとサブディレクトリの両方の Unicode 名を取得できます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **short_name**: 短い名前 (8.3 形式) へのポインター。
- **destination_unicode_name**: 指定された短い名前に関連付けられている Unicode 名の宛先へのポインター。
- **destination_unicode_length**: 返された Unicode 名の長さへのポインター。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) Unicode 名の取得に成功しました。
- **FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) 短い名前が見つからなかったか、Unicode の宛先サイズが小さすぎます。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

短い名前から Unicode 名を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>説明

このサービスは、現在のデフォルト ディレクトリ内の指定された短い名前 (8.3 形式) に関連付けられている Unicode 名を取得します。短い名前のパラメーターではパス情報は使用できません。 成功した場合、短い名前に関連付けられている Unicode 名がサービスによって返されます。

> [!IMPORTANT]
> *このサービスは ***fx_unicode_name_get** _と同じですが、呼び出し元が入力引数として宛先の Unicode バッファーのサイズを指定する点が異なります。これにより、サービスでは宛先の Unicode バッファーが上書きされないことが保証されます_

> [!IMPORTANT]
> *このサービスを使用して、ファイルとサブディレクトリの両方の Unicode 名を取得できます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **short_name**: 短い名前 (8.3 形式) へのポインター。
- **destination_unicode_name**: 指定された短い名前に関連付けられている Unicode 名の宛先へのポインター。
- **destination_unicode_length**: 返された Unicode 名の長さへのポインター。
- **unicode_name_buffer_length**: Unicode 名のバッファーのサイズ。 注: NULL 終端文字が必要です。これによって 1 バイトが追加されます。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) Unicode 名の取得に成功しました。
- **FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) 短い名前が見つからなかったか、Unicode の宛先サイズが小さすぎます。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

Unicode 名から短い名前を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

このサービスは、現在のデフォルト ディレクトリ内で Unicode 名に関連付けられている短い名前 (8.3 形式) を取得します。Unicode 名のパラメーターではパス情報は使用できません。 成功した場合、Unicode 名に関連付けられている短い名前がサービスによって返されます。

> [!IMPORTANT]
> *このサービスを使用して、ファイルとサブディレクトリの両方の短い名前を取得できます。*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **source_unicode_name**: Unicode 名へのポインター。
- **source_unicode_length**: Unicode 名の長さ。
- **destination_short_name**: 短い名前 (8.3 形式) の宛先へのポインター。 これは、少なくとも 13 バイトのサイズである必要があります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 短い名前の取得に成功しました。
- **FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) Unicode 名が見つかりませんでした。
- **FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

Unicode 名から短い名前を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>説明

このサービスは、現在のデフォルト ディレクトリ内で Unicode 名に関連付けられている短い名前 (8.3 形式) を取得します。Unicode 名のパラメーターではパス情報は使用できません。 成功した場合、Unicode 名に関連付けられている短い名前がサービスによって返されます。

> [!IMPORTANT]
> *このサービスは **fx_unicode_short_name_get()** と同じですが、呼び出し元が入力引数として宛先バッファーのサイズを指定する点が異なります。これにより、サービスでは短い名前が宛先バッファーを超えないことが保証されます。*

*このサービスを使用して、ファイルとサブディレクトリの両方の短い名前を取得できます*

### <a name="input-parameters"></a>入力パラメーター

- **media_ptr**: メディア コントロール ブロックへのポインター。
- **source_unicode_name**: Unicode 名へのポインター。
- **source_unicode_length**: Unicode 名の長さ。
- **destination_short_name**: 短い名前 (8.3 形式) の宛先へのポインター。 これは、少なくとも 13 バイトのサイズである必要があります。
- **short_name_buffer_length**: 宛先バッファーのサイズ。 バッファー サイズは 14 バイト以上である必要があります。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) 短い名前の取得に成功しました。
- **FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。
- **FX_FILE_CORRUPT** (0x08) ファイルが破損しています
- **FX_IO_ERROR** (0x90) ドライバーの I/O エラー。
- **FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。
- **FX_NOT_FOUND** (0x04) Unicode 名が見つかりませんでした。
- **FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。
- **FX_SECTOR_INVALID** (0x89) 無効なセクター。
- **FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。
- **FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>参照

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
