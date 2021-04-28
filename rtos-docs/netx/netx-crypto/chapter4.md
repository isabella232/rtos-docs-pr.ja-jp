---
title: 第 4 章 - Azure RTOS NetX Crypto API の説明
description: Azure RTOS NetX Crypto API の説明
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811627"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>第 4 章 - Azure RTOS NetX Crypto API の説明

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

NetX Secure ライブラリを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>説明

この関数では、Azure RTOS NetX Crypto ライブラリ モジュールを初期化します。 アプリケーションは、他のいずれかの暗号化関数を使用する前に、この関数を呼び出して初期化を実行し、ライブラリの整合性を検証する必要があります。 他の NetX Crypto サービスを使用する前にこの関数を呼び出さないと、エラーが返されることになります。

### <a name="parameters"></a>パラメーター

- **なし**

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) NetX Crypto ライブラリが正常に初期化されました。 これでライブラリ関数の準備が整い、使用できます。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリを初期化できなかったか、整合性チェックに失敗しました。 アプリケーションでこのライブラリを使用することはできません。

### <a name="example"></a>例

TODO

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

FIPS 対応モジュールの現在の状態を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>説明

このサービスは、FIPS ビルド ライブラリでのみ使用できます。 NetX Crypto ライブラリの現在の状態を返します。

### <a name="parameters"></a>パラメーター

- **なし**

### <a name="return-values"></a>戻り値

- **状態フラグ:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **その他のすべての値は無効です。**

### <a name="example"></a>例

TODO

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

AES 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、AES 制御ブロックを初期化します。 いったん AES 制御ブロックが初期化されると、後続の AES 操作では、同じキーとキー サイズが使用されます。

アプリケーションは複数の AES 制御ブロックを作成することがあり、それぞれがセッションを表します。 キーは制御ブロックに割り当てられます。 後続の暗号化や暗号化解除の操作では、同じ AES 制御ブロックを参照することができ、AES 制御ブロックを再初期化する必要はありません。 セッションのキーが変更された場合、アプリケーションでは、更新されたキーを使用して AES 制御ブロックを再初期化する必要があります。

_ *Nx_crypto_method_aes_init()* を呼び出すと、以前に構成されたキーとキー サイズが、新しいキーに自動的に更新されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な AES 暗号化メソッド制御ブロックへのポインター。 以下の定義済み AES 暗号化メソッドを使用できます。
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **key** AES キーを格納しているバッファーを指し示します
- **key_size_in_bits** キーのサイズ (ビット単位)。 次の値を指定できます。
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **その他のすべての値は無効です。**
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** AES 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 AES の場合、メタデータ サイズは *sizeof(NX_AES)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、AES 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) キー サイズが、AES では有効ではありません。

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

AES 操作 (暗号化または暗号化解除) を実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>説明

この関数では、AES の暗号化または暗号化解除の操作を実行します。 AES 制御ブロックは、_ *nx_crypto_method_aes_init()* を使用して初期化されている必要があります。 実行される AES アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

入力バッファーのサイズは、16 バイトの倍数である必要があります。 暗号化が解除されたデータのサイズは、入力データ サイズと同じサイズです。 AES ブロック サイズの偶数倍にするために、暗号化されたデータがパディングされた場合、そのパディングは出力バッファーに含められます。また、そのパディングはアプリケーションによって処理される必要があります。

この操作では、状態情報は保持されず、AES 制御ブロック内のキー マテリアルは変更されません。

op が NX_CRYPTO_SET_ADDITIONAL_DATA で、アルゴリズムが AES-CCM8 の場合、入力は追加データを指し示し、input_length_in_byte は追加データの長さになります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (AES-XCBC のみ)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 のみ)*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な AES 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、*nx_crypto_method_aes_init()* で使用されるものと同じである必要があります。
- **input_data** 暗号化されたテキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。 入力データのサイズは、16 バイトの倍数である必要があります。
- **iv_ptr** 初期ベクトルへのポインター。 IV バッファーに関する制限はありません。
- **iv_size** 初期ベクトル ブロックのサイズ (バイト単位)。このフィールドは 16 である必要があります。
- **output_buffer** クリア テキスト データを格納する AES 用メモリ領域へのポインター。 アプリケーションで出力バッファーに領域を割り当てる必要があります。 出力バッファーは、入力バッファーと重複することがあります。 出力バッファーと入力バッファーが同じ開始アドレスを共有している場合は、これらが重複することがあります。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。 出力バッファー サイズは、少なくとも入力バッファー サイズと同じである必要があり、出力バッファー サイズは 16 バイトの倍数である必要があります。
- **crypto_metadata** *_nx_crypto_method_aes_init()\*\** で使用される AES 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 AES の場合、メタデータ サイズは *sizeof(NX_AES)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** - このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) AES 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な AES アルゴリズムが指定されています**。

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

AES 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この AES セッションが不要になったと判断した後にこの関数を呼び出して、AES 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_aes_init()\*\** で使用される AES 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) AES セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

3DES 制御ブロックを初期化します。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定された 3 つのキー文字列を使用して、Triple DES (3DES) 制御ブロックを初期化します。 キー文字列は、それぞれ 8 バイトである必要があります。 3 つの DES キーは、24 バイトのバッファーの連続するメモリに連結する必要があります。 FIPS に準拠しているビルドの場合、3 つのキーがそれぞれ異なっている必要があります。そうでないと、関数から NX_CRYPTO_INVALID_KEY エラーが返されます。 いったん 3DES 制御ブロックが初期化されると、後続の 3DES 操作では同じキーが使用されます。

アプリケーションは複数の 3DES 制御ブロックを作成することがあり、それぞれがセッションを表します。 キーは制御ブロックに割り当てられ、後続の暗号化または暗号化解除の操作では、再初期化不要で同じ制御ブロックを参照できます。 セッションのキーが変更された場合、アプリケーションでは、更新されたキーを使用して制御ブロックを再初期化する必要があります。

_ *nx_crypto_method_3des_init()* を呼び出すと、以前に構成されたキーが、新しいキーに自動的に更新されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な 3DES 暗号化メソッド制御ブロックへのポインター。 次の定義済み 3DES 暗号化メソッドを使用できます: ***crypto_method_3des***
- **key** 3 つの DES キーを格納しているバッファーを指し示します。
- **key_size_in_bits** 192 である必要があります (それぞれが 64 ビットのキーが 3 つ)。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 このハンドルで、初期化中の 3DES 制御ブロックが識別されます。 後続の 3DES 操作 (暗号化、暗号化の解除、クリーンアップ) では、このハンドルを使用して 3DES 制御ブロックにアクセスします。
- **crypto_metadata** 3DES 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 3DES の場合、メタデータ サイズは *sizeof(NX_3DES)* である必要があります

### <a name="return-value"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、3DES 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) キー サイズが、3DES では有効ではありません。

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

3DES を使用して暗号化または暗号化解除を行います。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、3DES の暗号化または暗号化解除の操作を実行します。 3DES 制御ブロックは、_ *nx_crypto_method_3des_init()* を使用して初期化されている必要があります。 実行される 3DES アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

入力バッファーのサイズは、8 バイトの倍数である必要があります。 暗号化が解除されたデータのサイズは、入力データ サイズと同じサイズです。 3DES ブロック サイズの偶数倍にするために、暗号化されたデータがパディングされた場合、そのパディングは出力バッファーに含められます。また、そのパディングはアプリケーションによって処理される必要があります。

この操作では、状態情報は保持されず、3DES 制御ブロック内のキー マテリアルは変更されません。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **handle** *_nx_crypto_method_3des_init()* によって初期化されたハンドル。
- **method** 有効な 3DES 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、*nx_crypto_method_3des_init()* で使用されるものと同じである必要があります。
- **input_data** 暗号化されたテキスト データを格納しているバッファーを指し示します。
入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。 入力データのサイズは、8 バイトの倍数である必要があります。
- **iv_ptr** 初期ベクトルへのポインター。 IV バッファーに関する制限はありません。
- **iv_size** 初期ベクトル ブロックのサイズ (バイト単位)。このフィールドは 8 である必要があります。
- **output_buffer** クリア テキスト データを格納する 3DES 用メモリ領域へのポインター。 アプリケーションで出力バッファーに領域を割り当てる必要があります。 出力バッファーは、入力バッファーと重複することがあります。 出力バッファーと入力バッファーが同じ開始アドレスを共有している場合は、これらが重複することがあります。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。 出力バッファー サイズは、少なくとも入力バッファー サイズと同じである必要があり、出力バッファー サイズは 8 バイトの倍数である必要があります。
- **crypto_metadata** *_nx_crypto_method_3des_init()* で使用される 3DES 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 3DES の場合、メタデータ サイズは *sizeof(NX_3DES)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="description"></a>説明

この関数では、3DES 暗号化を実行します。 3DES 制御ブロックは、_ *nx_crypto_moethod_3des_init()* を使用して初期化されている必要があります。 この操作では、状態情報は保持されず、3DES 制御ブロック内のキー マテリアルは変更されません。 この関数ではパディングは追加されないため、暗号化操作を呼び出す前に、呼び出し元でパディングを処理する必要があることに注意してください。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、3DES 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

3DES 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この 3DES セッションが不要になったと判断した後にこの関数を呼び出して、3DES 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **handle** *_nx_crypto_method_3des_init()* によって初期化されたハンドル。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) 3DES セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

DRBG 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、DRBG 制御ブロックを初期化します。 いったん DRBG 制御ブロックが初期化されると、後続の DRBG 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の DRBG 制御ブロックを作成することがあり、それぞれがセッションを表します。 DRBG 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 DRBG 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な DRBG 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_drbg*
- **key** このフィールドは DRBG では使用されません。
- **key_size_in_bits** このフィールドは DRBG では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** DRBG 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 DRBG の場合、メタデータ サイズは *sizeof(NX_CRYPTO_DRBG)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、DRBG 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

DRBG 操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、DRBG 操作を実行します。 DRBG 制御ブロックは、_ *nx_crypto_method_drbg_init()* を使用して初期化されている必要があります。 実行される DRBG アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。 既定では、DRBG には AE-128 が使用されます。

操作が NX_CRYPTO_DRBG_OPTIONS_SET である場合、入力は、NX_CRYPTO_DRBG_OPTIONS 構造体を指し示します。 操作が NX_CRYPTO_DRBG_INSTANTIATE である場合、キーは nonce を指し示し、入力はパーソナル化文字列を指し示します。 操作が NX_CRYPTO_DRBG_RESEED または NX_CRYPTO_DRBG_GENERATE である場合、入力は追加の入力を指し示します。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な DRBG 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_drbg_init()* で使用されるものと同じである必要があります。
- **key** インスタンス作成操作の nonce へのポインター。 このフィールドは他の操作には使用されません。
- **key_size_in_bits** nonce のサイズ (ビット単位)。 このフィールドは他の操作には使用されません。
- **input** op が NX_CRYPTO_DRBG_OPTIONS_SET である場合、このフィールドは DRBG オプションを指し示します。 op が NX_CRYPTO_DRBG_INSTANTIATE である場合、このフィールドはパーソナル化文字列を指し示します。 op が NX_CRYPTO_DRBG_RESEED または NX_CRYPTO_DRBG_GENERATE である場合、このフィールドは追加の入力データを指し示します。
- **input_length_in_byte** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは DRBG では使用されません。
- **output** op が NX_CRYPTO_DRBG_GENERATE である場合、このフィールドは、生成された DRBG のメモリ領域を指し示します。 その他の場合、このフィールドは使用されません。
- **output_length_in_byte** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_drbg_init()* で使用される DRBG 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 DRBG の場合、メタデータ サイズは *sizeof(NX_CRYPTO_DRBG)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) DRBG 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な DRBG アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

DRBG 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この DRBG セッションが不要になったと判断した後にこの関数を呼び出して、DRBG 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_drbg_init()* で使用される DRBG 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) DRBG セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

ECDH 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、ECDH 制御ブロックを初期化します。 いったん ECDH 制御ブロックが初期化されると、後続の ECDH 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の ECDH 制御ブロックを作成することがあり、それぞれがセッションを表します。 ECDH 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 ECDH 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な ECDH 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_ecdh*
- **key** このフィールドは ECDH では使用されません。
- **key_size_in_bits** このフィールドは ECDH では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** ECDH 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 ECDH の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDH)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、ECDH 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

ECDH 操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、ECDH 操作を実行します。 ECDH 制御ブロックは、_ *nx_crypto_method_ecdh_init()* を使用して初期化されている必要があります。 実行される ECDH アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

操作が NX_CRYPTO_EC_CURVE_SET である場合、入力は楕円曲線暗号化メソッドを指し示します。 操作が NX_CRYPTO_EC_KEY_PAIR_GENERATE である場合、出力は NX_CRYPTO_EXTENDED_OUTPUT 構造体を指し示し、キーの組が nx_crypto_extended_output_data にコピーされます。 操作が NX_CRYPTO_DH_SETUP である場合、公開キーが nx_crypto_extended_output_data に返されます。 操作が NX_CRYPTO_DH_KEY_PAIR_IMPORT である場合、入力は公開キーを指し示し、キーは秘密キーを指し示します。 操作が NX_CRYPTO_DH_PRIVATE_KEY_EXPORT である場合、秘密キーが nx_crypto_extended_output_data にコピーされます。 操作が NX_CRYPTO_DH_CALCULATE である場合、入力はリモートの公開キーを指し示し、共有シークレットが nx_crypto_extended_output_data にコピーされます。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な ECDH 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_ecdh_init()* で使用されるものと同じである必要があります。
- **key** op が NX_CRYPTO_DH_IMPORT_KEY_PAIR である場合、このフィールドは秘密キーを指し示します。 その他の場合、このフィールドは ECDH では使用されません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **input** op が NX_CRYPTO_EC_CURVE_SET である場合、このフィールドは楕円曲線暗号化メソッドを指し示します。 op が NX_CRYPTO_DH_SETUP である場合、このフィールドは使用されません。 op が NX_CRYPTO_DH_CALCULATE である場合、このフィールドは、入力テキスト データを格納しているバッファーを指し示します。 op が NX_CRYPTO_DH_IMPORT_KEY_PAIR である場合、このフィールドは公開キーを指し示します。
- **input_length_in_byte** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは ECDH では使用されません。
- **output** op が NX_CRYPTO_EC_CURVE_SET または NX_CRYPTO_DH_IMPORT_KEY_PAIR である場合、このフィールドは使用されません。 op が NX_CRYPTO_DH_SETUP である場合、このフィールドは、生成された ECDH 公開キーのメモリ領域を指し示します。 op が NX_CRYPTO_DH_CALCULATE である場合、このフィールドは、生成された ECDH 共有シークレットのメモリ領域を指し示します。
- **output_length_in_byte** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_ecdh_init()* で使用される ECDH 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 ECDH の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDH)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) ECDH 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な ECDH アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

ECDH 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この ECDH セッションが不要になったと判断した後にこの関数を呼び出して、ECDH 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_ecdh_init()* で使用される ECDH 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) ECDH セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

ECDSA 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、ECDSA 制御ブロックを初期化します。 いったん ECDSA 制御ブロックが初期化されると、後続の ECDSA 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の ECDSA 制御ブロックを作成することがあり、それぞれがセッションを表します。 ECDSA 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 ECDSA 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な ECDSA 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_ecdsa*
- **key** このフィールドは ECDSA では使用されません。
- **key_size_in_bits** このフィールドは ECDSA では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** ECDSA 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 ECDSA の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDSA)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、ECDSA 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

ECDSA 操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、ECDSA 操作を実行します。 ECDSA 制御ブロックは、_ *nx_crypto_method_ecdsa_init()* を使用して初期化されている必要があります。 実行される ECDH アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

操作が NX_CRYPTO_EC_CURVE_SET である場合、入力は楕円曲線暗号化メソッドを指し示します。 操作が NX_CRYPTO_EC_KEY_PAIR_GENERATE である場合、出力は NX_CRYPTO_EXTENDED_OUTPUT 構造体を指し示し、キーの組が nx_crypto_extended_output_data にコピーされます。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な ECDSA 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_ecdsa_init()* で使用されるものと同じである必要があります。
- **key** op が NX_CRYPTO_VERIFY である場合にキーを指し示します。 キー バッファーに関する制限はありません。 このフィールドは、op の他の値に対しては使用されません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **input** op が NX_CRYPTO_EC_CURVE_SET である場合、このフィールドは楕円曲線暗号化メソッドを指し示します。 それ以外の場合、このフィールドは入力テキスト データを格納しているバッファーを指し示します。
- **input_length_in_byte** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは ECDSA では使用されません。
- **output** op が NX_CRYPTO_EC_CURVE_SET である場合、このフィールドは使用されません。 op が NX_CRYPTO_AUTHENTICATE である場合、このフィールドは、生成された ECDSA シグネチャのメモリ領域を指し示します。 op が NX_CRYPTO_VERIFY である場合、このフィールドは、検証される ECDSA シグネチャのメモリ領域を指し示します。
- **output_length_in_byte** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_ecdsa_init()* で使用される ECDSA 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 ECDSA の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDSA)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) ECDSA 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な ECDSA アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

ECDSA 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この ECDSA セッションが不要になったと判断した後にこの関数を呼び出して、ECDSA 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_ecdsa_init()* で使用される ECDSA 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) ECDSA セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

HMAC MD5 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、HMAC MD5 制御ブロックを初期化します。 いったん HMAC MD5 制御ブロックが初期化されると、後続の HMAC MD5 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の HMAC MD5 制御ブロックを作成することがあり、それぞれがセッションを表します。 HMAC MD5 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 HMAC MD5 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な HMAC MD5 暗号化メソッド制御ブロックへのポインター。
以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_hmac_md5*
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** HMAC MD5 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5_HMAC)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC MD5 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

HMAC MD5 ハッシュ操作を実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、HMAC MD5 ハッシュ操作を実行します。 HMAC MD5 制御ブロックは、_ *nx_crypto_method_hmac_md5_init()* を使用して初期化されている必要があります。 実行される HMAC MD5 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 16 バイトである必要があります。

この操作では、状態情報は保持されず、HMAC MD5 制御ブロック内のキー マテリアルは変更されません。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な HMAC MD5 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、*nx_crypto_method_hmac_md5_init()* で使用されるものと同じである必要があります。
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは HMAC MD5 では使用されません。
- **iv_size** このフィールドは HMAC MD5 では使用されません。
- **output_buffer** 生成された HMAC MD5 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_hmac_md5_init()* で使用される HMAC MD5 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5_HMAC)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC MD5 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC MD5 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

HMAC SHA1 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、HMAC SHA1 制御ブロックを初期化します。 いったん HMAC SHA1 制御ブロックが初期化されると、後続の HMAC SHA1 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の HMAC SHA1 制御ブロックを作成することがあり、それぞれがセッションを表します。 HMAC SHA1 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 HMAC SHA1 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な HMAC SHA1 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_hmac_sha1*
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** HMAC SHA1 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1_HMAC)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC SHA1 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

HMAC SHA1 ハッシュ操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、HMAC SHA1 ハッシュ操作を実行します。 HMAC SHA1 制御ブロックは、_ *nx_crypto_method_hmac_sha1_init()* を使用して初期化されている必要があります。 実行される HMAC SHA1 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 20 バイトである必要があります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な HMAC SHA1 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_hmac_sha1_init()* で使用されるものと同じである必要があります。
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは HMAC SHA1 では使用されません。
- **iv_size** このフィールドは HMAC SHA1 では使用されません。
- **output_buffer** 生成された HMAC SHA1 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* で使用される HMAC SHA1 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1_HMAC)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC SHA1 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

HMAC SHA1 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この HMAC SHA1 セッションが不要になったと判断した後にこの関数を呼び出して、HMAC SHA1 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* で使用される HMAC SHA1 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

HMAC SHA256 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、HMAC SHA256 制御ブロックを初期化します。 いったん HMAC SHA256 制御ブロックが初期化されると、後続の HMAC SHA256 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の HMAC SHA256 制御ブロックを作成することがあり、それぞれがセッションを表します。 HMAC SHA256 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 HMAC SHA256 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な HMAC SHA256 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** HMAC SHA256 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYTPO_SHA256_HMAC)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC SHA256 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

HMAC SHA256 ハッシュ操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、HMAC SHA256 ハッシュ操作を実行します。 HMAC SHA256 制御ブロックは、_ *nx_crypto_method_hmac_sha256_init()* を使用して初期化されている必要があります。 実行される HMAC SHA256 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA256 の場合は 32 バイト、SHA224 の場合は 28 バイトである必要があります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な HMAC SHA256 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_hmac_sha256_init()* で使用されるものと同じである必要があります。
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは HMAC SHA256 では使用されません。
- **iv_size** このフィールドは HMAC SHA256 では使用されません。
- **output_buffer** 生成された HMAC SHA256 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* で使用される HMAC SHA256 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA256_HMAC)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC SHA256 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

HMAC SHA256 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この HMAC SHA256 セッションが不要になったと判断した後にこの関数を呼び出して、HMAC SHA256 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* で使用される HMAC SHA256 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

HMAC SHA512 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、HMAC SHA512 制御ブロックを初期化します。 いったん HMAC SHA512 制御ブロックが初期化されると、後続の HMAC SHA512 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の HMAC SHA512 制御ブロックを作成することがあり、それぞれがセッションを表します。 HMAC SHA512 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 HMAC SHA512 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な HMAC SHA512 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** HMAC SHA512 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512_HMAC)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC SHA512 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

HMAC SHA512 ハッシュ操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、HMAC SHA512 ハッシュ操作を実行します。 HMAC SHA512 制御ブロックは、_ *nx_crypto_method_hmac_sha512_init()* を使用して初期化されている必要があります。 実行される HMAC SHA512 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA512 の場合は 64 バイト、SHA384 の場合は 48 バイトである必要があります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な HMAC SHA512 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_hmac_sha512_init()* で使用されるものと同じである必要があります。
- **key** キーを指し示します。 キー バッファーに関する制限はありません。
- **key_size_in_bits** キーのサイズ (ビット単位)。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは HMAC SHA512 では使用されません。
- **iv_size** このフィールドは HMAC SHA512 では使用されません。
- **output_buffer** 生成された HMAC SHA512 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。
- **crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* で使用される HMAC SHA512 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 HMAC SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512_HMAC)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC SHA512 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

HMAC SHA512 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この HMAC SHA512 セッションが不要になったと判断した後にこの関数を呼び出して、HMAC SHA512 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* で使用される HMAC SHA512 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

### <a name="example"></a>例 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

MD5 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、MD5 制御ブロックを初期化します。 いったん MD5 制御ブロックが初期化されると、後続の MD5 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の MD5 制御ブロックを作成することがあり、それぞれがセッションを表します。 MD5 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 MD5 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な MD5 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_md5*
- **key** このフィールドは MD5 では使用されません。
- **key_size_in_bits** このフィールドは MD5 では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** MD5 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、MD5 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

### <a name="example"></a>例

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

MD5 ハッシュ操作を実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、MD5 ハッシュ操作を実行します。 MD5 制御ブロックは、_ *nx_crypto_method_md5_init()* を使用して初期化されている必要があります。 実行される MD5 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 16 バイトである必要があります。

この操作では、状態情報は保持されず、MD5 制御ブロック内のキー マテリアルは変更されません。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な MD5 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、*nx_crypto_method_md5_init()* で使用されるものと同じである必要があります。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは MD5 では使用されません。
- **iv_size** このフィールドは MD5 では使用されません。
- **output_buffer** 生成された MD5 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。 MD5 の場合、バッファー サイズは 16 バイトである必要があります。
- **crypto_metadata** *_nx_crypto_method_md5_init()* で使用される MD5 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) MD5 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な MD5 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

MD5 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この MD5 セッションが不要になったと判断した後にこの関数を呼び出して、MD5 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_md5_init()* で使用される MD5 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) MD5 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

SHA1 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、SHA1 制御ブロックを初期化します。 いったん SHA1 制御ブロックが初期化されると、後続の SHA1 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の SHA1 制御ブロックを作成することがあり、それぞれがセッションを表します。 SHA1 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 SHA1 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な SHA1 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_sha1*
- **key** このフィールドは SHA1 では使用されません。
- **key_size_in_bits** このフィールドは SHA1 では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** SHA1 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、SHA1 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

SHA1 ハッシュ操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、SHA1 ハッシュ操作を実行します。 SHA1 制御ブロックは、_ *nx_crypto_method_sha1_init()* を使用して初期化されている必要があります。 実行される SHA1 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 20 バイトである必要があります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な SHA1 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、*nx_crypto_method_sha1_init()* で使用されるものと同じである必要があります。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは SHA1 では使用されません。
- **iv_size** このフィールドは SHA1 では使用されません。
- **output_buffer** 生成された SHA1 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。 SHA1 の場合、バッファー サイズは 20 バイトである必要があります。
- **crypto_metadata** *_nx_crypto_method_sha1_init()* で使用される SHA1 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) SHA1 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な SHA1 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

### <a name="example"></a>例

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

SHA1 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この SHA1 セッションが不要になったと判断した後にこの関数を呼び出して、SHA1 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_sha1_init()* で使用される SHA1 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) SHA1 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

SHA256 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、SHA256 制御ブロックを初期化します。 いったん SHA256 制御ブロックが初期化されると、後続の SHA256 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の SHA256 制御ブロックを作成することがあり、それぞれがセッションを表します。 SHA256 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 SHA256 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な SHA256 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **key** このフィールドは SHA256 では使用されません。
- **key_size_in_bits** このフィールドは SHA256 では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** SHA256 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA256)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、SHA256 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

SHA256 ハッシュ操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>説明

この関数では、SHA256 ハッシュ操作を実行します。 SHA256 制御ブロックは、_ ***nx_crypto_method_sha256_init()*** を使用して初期化されている必要があります。 実行される SHA256 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA256 の場合は 32 バイト、SHA224 の場合は 28 バイトである必要があります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な SHA256 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_sha256_init()* で使用されるものと同じである必要があります。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは SHA256 では使用されません。
- **iv_size** このフィールドは SHA256 では使用されません。
- **output_buffer** 生成された SHA256 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。 SHA256 の場合、バッファー サイズは 32 バイトである必要があります。 SHA224 の場合、バッファー サイズは 28 バイトである必要があります。
- **crypto_metadata** *_nx_crypto_method_sha2_init()* で使用される SHA2 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA256)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) SHA256 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な SHA256 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

SHA256 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この SHA256 セッションが不要になったと判断した後にこの関数を呼び出して、SHA256 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_sha256_init()* で使用される SHA256 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) SHA256 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

SHA512 暗号化制御ブロックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>説明

この関数では、指定されたキー文字列を使用して、SHA512 制御ブロックを初期化します。 いったん SHA512 制御ブロックが初期化されると、後続の SHA512 操作では、同じ制御ブロックが使用されることになっています。

アプリケーションは複数の SHA512 制御ブロックを作成することがあり、それぞれがセッションを表します。 SHA512 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。 SHA512 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。

### <a name="parameters"></a>パラメーター

- **method** 有効な SHA512 暗号化メソッド制御ブロックへのポインター。 以下の定義済み DRBG 暗号化メソッドを使用できます。
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **key** このフィールドは SHA512 では使用されません。
- **key_size_in_bits** このフィールドは SHA512 では使用されません。
- **handle** このサービスでは、呼び出し元へのハンドルが返されます。 ハンドルは実装に依存しており、この実装では使用されていません。 アプリケーションでは、このハンドルには NULL を渡す必要があります。
- **crypto_metadata** SHA512 制御ブロック用の有効なメモリ領域へのポインター。 メモリ領域の開始アドレスは、4 バイトで整列している必要があります。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512)* である必要があります

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、SHA512 制御ブロックが正常に初期化されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

SHA512 ハッシュ操作を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>説明

この関数では、SHA512 ハッシュ操作を実行します。 SHA512 制御ブロックは、_ *nx_crypto_method_sha512_init()* を使用して初期化されている必要があります。 実行される SHA512 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。

最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA512 の場合は 64 バイト、SHA384 の場合は 48 バイトである必要があります。

### <a name="parameters"></a>パラメーター

- **op** 実行する操作の種類。 有効な操作は次のとおりです。
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **method** 有効な SHA512 暗号化メソッドへのポインター。 ここで使用される暗号化メソッドは、_ *nx_crypto_method_sha512_init()* で使用されるものと同じである必要があります。
- **input_data** 入力テキスト データを格納しているバッファーを指し示します。 入力バッファーに関する制限はありません。
- **input_data_size** 入力データのサイズ (バイト単位)。
- **iv_ptr** このフィールドは SHA512 では使用されません。
- **iv_size** このフィールドは SHA512 では使用されません。
- **output_buffer** 生成された SHA512 ハッシュのメモリ領域へのポインター。
- **output_buffer_size** 出力バッファーのサイズ (バイト単位)。 SHA512 の場合、バッファー サイズは 64 バイトである必要があります。 SHA384 の場合、バッファー サイズは 48 バイトである必要があります。
- **crypto_metadata** *_nx_crypto_method_sha512_init()* で使用される SHA512 制御ブロックへのポインター。
- **crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。 SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512)* である必要があります
- **packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。
- **nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。 渡された値はすべて暗黙的に無視されます。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) SHA512 操作が正常に実行されました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。
- **NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な SHA512 アルゴリズムが指定されています。
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

SHA512 制御ブロックをクリーンアップします。

### <a name="prototype"></a>プロトタイプ

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>説明

アプリケーションでは、この SHA512 セッションが不要になったと判断した後にこの関数を呼び出して、SHA512 制御ブロックをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **crypto_metadata** *_nx_crypto_method_sha512_init()* で使用される SHA512 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_CRYPTO_SUCCESS** (0x00) SHA512 セッションが正常にクリーンアップされました。
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。