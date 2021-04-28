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
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>第 4 章 - Azure RTOS LevelX NAND API

アプリケーションで使用できる Azure RTOS LevelX NAND API は次のとおりです。

- ***lx_nand_flash_close** _: _NAND フラッシュ インスタンスを閉じる*
- ***lx_nand_flash_defragment** _: _NAND フラッシュ インスタンスをデフラグする*
- ***lx_nand_flash_extended_cache_enable** _: _拡張 NAND キャッシュを有効または無効にする*
- ***lx_nand_flash_initialize** _: _NAND フラッシュのサポートを初期化する*
- ***lx_nand_flash_open** _: _NAND フラッシュ インスタンスを開く*
- ***lx_nand_flash_page_ecc_check** _: _訂正ありの ECC エラーがないかどうかページを確認する*
- ***lx_nand_flash_page_ecc_compute** _: _ページの ECC を計算する*
- ***lx_nand_flash_partial_defragment** _: _NAND フラッシュ インスタンスの部分的なデフラグ*
- ***lx_nand_flash_sector_read** _: _NAND フラッシュ セクターを読み取る*
- ***lx_nand_flash_sector_release** _: _NAND フラッシュ セクターを解放する*
- ***lx_nand_flash_sector_write** _: _NAND フラッシュ セクターを書き込む*

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

NAND フラッシュ インスタンスを閉じる

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>説明

このサービスでは、以前に開かれた NAND フラッシュ インスタンスを閉じます。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) フラッシュ インスタンスを閉じているときにエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

NAND フラッシュ インスタンスをデフラグする

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>説明

このサービスでは、以前に開かれた NAND フラッシュ インスタンスをデフラグします。 デフラグ プロセスでは、空きページと空きブロックの数を最大化します。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) フラッシュ インスタンスのデフラグ中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

拡張 NAND キャッシュを有効または無効にする

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>説明

このサービスでは、アプリケーションによって指定されたメモリを使用して、RAM 内にキャッシュ レイヤーを実装します。 完全なキャッシュ操作に必要なメモリの合計量は、次のように計算できます。

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

指定されたメモリに完全な NAND キャッシュを収容するための十分な大きさがない場合、このルーチンでは、指定されたメモリに基づいて、できるだけ大きな NAND フラッシュ キャッシュを有効にします。

指定されたメモリ アドレスが NULL である場合、NAND キャッシュは無効になります。 そのため、NAND キャッシュは一時的に使用できます。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。  
- **memory**: ULONG アクセス用にアラインされたキャッシュ メモリの開始アドレス。 LX_NULL の値を指定すると、キャッシュは無効になります。  
- **size**: 指定されたメモリのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) NAND キャッシュの 1 つの要素に十分なメモリがありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

NAND フラッシュのサポートを初期化する

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>説明

このサービスでは、LevelX NAND フラッシュのサポートを初期化します。 これは、他のどの LevelX NAND API よりも前に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **なし**

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) NAND フラッシュのサポートの初期化中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

NAND フラッシュ インスタンスを開く

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>説明

このサービスでは、指定された NAND フラッシュ コントロール ブロックとドライバー初期化関数を使用して NAND フラッシュ インスタンスを開きます。 このドライバー初期化関数は、この NAND フラッシュ インスタンスに関連付けられている NAND ハードウェアのブロックまたはページの読み取り、書き込み、消去を行うためのさまざまな関数ポインターのインストールを担当することに注意してください。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **name**: NAND フラッシュ インスタンスの名前。
- **nand_driver_initialize**: NAND フラッシュ ドライバー初期化関数への関数ポインター。 NAND フラッシュ ドライバーの処理の詳細については、このガイドの第 3 章を参照してください。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) NAND フラッシュ インスタンスを開いているときにエラーが発生しました。
- **LX_NO_MEMORY**: (0x08) ドライバーによって、1 ページを RAM に読み取るためのバッファーが提供されませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

訂正ありの ECC エラーがないかどうかページを確認する

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>説明

このサービスでは、指定された NAND ページ バッファーの整合性を指定された ECC で確認します。 ページ サイズ (NAND フラッシュ インスタンスのポインターで定義されます) は 256 バイトの倍数であると見なされ、指定された ECC コードでは、ページの 256 バイトの各部分の中の 1 ビット エラーを訂正できます。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **page_buffer**: NAND フラッシュ ページ バッファーへのポインター。
- **ecc_buffer**: NAND フラッシュ ページの ECC へのポインター。 ページの 256 バイトの部分ごとに 3 つの ECC バイトが存在することに注意してください。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) NAND ページにはエラーがありません。
- **LX_NAND_ERROR_CORRECTED**: (0x06) NAND ページで 1 ビット エラーが 1 つ以上訂正されました。訂正はページ バッファー内にあります。
- **LX_NAND_ERROR_NOT_CORRECTED**: (0x07) NAND ページで訂正するエラーが多すぎます。

### <a name="allowed-from"></a>許可元

LevelX ドライバー

### <a name="example"></a>例

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

ページの ECC を計算する

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>説明

このサービスでは、指定された NAND ページ バッファーの ECC を計算し、その ECC を指定された ECC バッファーで返します。 ページ サイズは 256 バイトの倍数であると見なされます (NAND フラッシュ インスタンスのポインターで定義されます)。 ECC コードは、ページの整合性を、そのページが後で読み取られたときに確認するために使用されます。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **page_buffer**: NAND フラッシュ ページ バッファーへのポインター。
- **ecc_buffer**: NAND フラッシュ ページの ECC の宛先へのポインター。 ページの 256 バイトの部分ごとに 3 バイトの ECC ストレージが必要であることに注意してください。 たとえば、2048 バイトのページでは ECC 用に 24 バイトが必要になります。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) ECC が正常に計算されました。
- **LX_ERROR**: (0x01) ECC の計算中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

LevelX ドライバー

### <a name="example"></a>例

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

NAND フラッシュ インスタンスの部分的なデフラグ

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>説明

このサービスでは、以前に開かれた NAND フラッシュ インスタンスを、指定された最大ブロック数までデフラグします。 デフラグ プロセスでは、空きページと空きブロックの数を最大化します。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **max_blocks**: 最大ブロック数。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) フラッシュ インスタンスのデフラグ中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

NAND フラッシュ セクターを読み取る

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>説明

このサービスでは、NAND フラッシュ インスタンスから論理セクターを読み取り、成功した場合は、その内容を指定されたバッファーで返します。 NAND セクターのサイズは常に、基になる NAND ハードウェアのページ サイズであることに注意してください。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **logical_sector**: 読み取る論理セクター。
- **buffer**: 論理セクターの内容の宛先へのポインター。 このバッファーは NAND フラッシュ ページのサイズであり、ULONG アクセス用にアラインされていると見なされることに注意してください。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) NAND フラッシュ セクターの読み取り中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

NAND フラッシュ セクターを解放する

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>説明

このサービスでは、NAND フラッシュ インスタンス内の論理セクターのマッピングを解放します。 使用されていない論理セクターを解放すると、LevelX のウェア レベリングがより効率的になります。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **logical_sector**: 解放する論理セクター。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_ERROR**: (0x01) NAND フラッシュ セクターの書き込み中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

NAND フラッシュ セクターを書き込む

### <a name="prototype"></a>プロトタイプ

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>説明

このサービスでは、NAND フラッシュ インスタンス内の指定された論理セクターを書き込みます。

### <a name="input-parameters"></a>入力パラメーター

- **nand_flash**: NAND フラッシュ インスタンスのポインター。
- **logical_sector**: 書き込む論理セクター。
- **buffer**: 論理セクターの内容へのポインター。 このバッファーは NAND フラッシュ ページのサイズであり、ULONG アクセス用にアラインされていると見なされることに注意してください。

### <a name="return-values"></a>戻り値

- **LX_SUCCESS**: (0x00) 要求が成功しました。
- **LX_NO_SECTORS**: (0x02) 書き込みを実行するために使用できる空きセクターがありません。
- **LX_ERROR**: (0x01) NAND フラッシュ セクターの解放中にエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>参照

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
