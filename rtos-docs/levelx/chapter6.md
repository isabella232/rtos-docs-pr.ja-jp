---
title: チャプター 6 - Azure RTOS LevelX NOR API
description: アプリケーションで使用できる Azure RTOS LevelX NOR API。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e109f5916a9e903aa3341f2855ade085e9d9a22b80ec7cb2e0c310e43ff3eac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790243"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>チャプター 6 - Azure RTOS LevelX NOR API

アプリケーションで使用できる Azure RTOS LevelX NOR API の関数は次のとおりです。

- ***lx_nor_flash_close** _: NOR フラッシュ インスタンスを閉じる*
- ***lx_nor_flash_defragment** _: NOR フラッシュ インスタンスのデフラグを行う*
- ***lx_nor_flash_extended_cache_enable** _: 拡張 NOR キャッシュを有効化/無効化する*
- ***lx_nor_flash_initialize** _: NOR フラッシュのサポートを初期化する*
- ***lx_nor_flash_open** _: NOR フラッシュ インスタンスを開く*
- ***lx_nor_flash_partial_defragment** _: NOR フラッシュ インスタンスの部分的なデフラグ*
- ***lx_nor_flash_sector_read** _: NOR フラッシュ セクタを読み出す*
- ***lx_nor_flash_sector_release** _: NOR フラッシュ セクタを開放する*
- ***lx_nor_flash_sector_write** _: NOR フラッシュ セクタに書き込む*

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

NOR フラッシュ インスタンスを閉じる

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>説明

このサービスでは、開いている NOR フラッシュ インスタンスを閉じます。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash*: NOR フラッシュ インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) フラッシュ インスタンスを閉じる際のエラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

NOR フラッシュ インスタンスのデフラグを行う

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>説明

このサービスでは、開いている NOR フラッシュ インスタンスのデフラグを行います。 デフラグ処理では、空きセクタと空きブロックの数を最大まで増やします。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash*: NOR フラッシュ インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) フラッシュ インスタンス デフラグ時のエラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

NOR 拡張キャッシュを有効/無効にする

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>説明

このサービスでは、アプリケーションにより用意されるメモリを使用して、RAM にセクタ キャッシュ レイヤーを実装します。 用意されたメモリは 512 バイトごとに、1 つのキャッシュ可能な NOR セクタとして使用します。 キャッシュされたセクタは、消去数、空きセクタのマップ、セクタ マッピングの情報などのブロック制御情報を保持します。 データ セクタはこのキャッシュに保存されません。

### <a name="input-parameters"></a>入力パラメーター

- **nor_flash**: NOR フラッシュ インスタンスへのポインター。  
- **memory**: ULONG アクセス用にアラインされた、キャッシュ メモリの開始位置。 LX_NULL を指定するとキャッシュを無効にします。  
- **size**: 用意するメモリのbyte 単位のサイズ (512 byte の倍数を指定します)。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) 特定の NOR セクタのメモリ不足。
- **LX_DISABLED**: (0x09) 構成オプションにより NOR 拡張キャッシュが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

NOR フラッシュのサポートの初期化

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>説明

このサービスでは、LevelX の NOR フラッシュのサポートを初期化します。 他のどの LevelX NOR API よりも先に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **なし**

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) NOR フラッシュのサポートの初期化エラー。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_partial_defragment
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

NOR フラッシュ インスタンスを開く

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>説明

このサービスでは、指定された NOR フラッシュ制御ブロックとドライバー初期化関数を使用して、NOR フラッシュ インスタンスを開きます。 この NOR フラッシュ インスタンスに関連付けられた NOR ハードウェアのブロックの読み出し、書き込み、消去を行うためのさまざまな関数ポインターのインストールは、ドライバー初期化関数で行います。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash*: NOR フラッシュ インスタンスへのポインター。
- *name*: NOR フラッシュ インスタンスの名前。
- *nor_driver_initialize*: NOR フラッシュ ドライバー初期化関数への関数ポインター。 NOR フラッシュ ドライバーの機能の詳細は、このガイドのチャプター 5 をご覧ください。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) NOR フラッシュ インスタンスを開く際のエラー。
- **LX_NO_MEMORY**:  (0x08) セクタを RAM に読み出すためのバッファーをドライバーで用意できませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

NOR フラッシュ インスタンスの部分的なデフラグ

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>説明

このサービスでは、開いている NOR フラッシュ インスタンスを、最大で指定した最大ブロック数までデフラグします。 デフラグ処理では、空きセクタと空きブロックの数を最大まで増やします。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash*: NOR フラッシュ インスタンスへのポインター。
- *max_blocks*: ブロックの最大数。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) フラッシュ インスタンス デフラグ時のエラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

NOR フラッシュ セクタを読み出す

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>説明

このサービスでは、論理セクタを NOR フラッシュ インスタンスから読み出し、成功した場合は、用意されたバッファーにその内容を返します。 NOR セクタのサイズは常に 512 byteです。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash* NOR フラッシュ インスタンスへのポインター。
- *logical_sector*: 読み出す論理セクタ。
- *buffer*: 論理セクタの内容の書き込み先へのポインター。 バッファーは 512 byteであり、ULONG アクセス用にアラインされていることを前提にしています。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) NOR フラッシュ セクタの読み出しエラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

NOR フラッシュ セクタを解放する

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>説明

このサービスでは、NOR フラッシュ インスタンスの論理セクタのマッピングを解放します。 使用していない論理セクタを解放することで、LevelX のウェア レベリングを効果的に実施できます。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash*: NOR フラッシュ インスタンスへのポインター。
- *logical_sector*: 解放する論理セクタ。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_ERROR**: (0x01) NOR フラッシュ セクタの書き込みエラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

NOR フラッシュ セクタを書き込む

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>説明

このサービスでは、NOR フラッシュ インスタンスの指定された論理セクタを書き込みます。

### <a name="input-parameters"></a>入力パラメーター

- *nor_flash*: NOR フラッシュ インスタンスへのポインター。
- *logical_sector*: 書き込む論理セクタ。
- *buffer*: 論理セクタの内容へのポインター。 バッファーは、ULONG アクセス用に 512 byte でアラインされているとみなされます。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求に成功。
- **LX_NO_SECTORS**: (0x02) 書き込みに使用できる空きセクタがありません。
- **LX_ERROR**: (0x01) NOR フラッシュ セクタを解放する際のエラー。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>参照

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
