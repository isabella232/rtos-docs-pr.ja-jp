---
title: 第 5 章 - モジュール マネージャー API
author: philmea
description: この記事では、アプリケーションの常駐部分で使用できるモジュール マネージャー API の概要を示します。
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810301"
---
# <a name="chapter-5---module-manager-apis"></a>第 5 章 - モジュール マネージャー API

## <a name="summary-of-module-manager-apis"></a>モジュール マネージャー API の概要

アプリケーションの常駐部分では、次のような、いくつかの追加 API を使用できます。

- ***txm_module_manager_external_memory_enable** _ - _共有メモリ空間へのモジュール アクセスを有効にします*
- ***txm_module_manager_file_load** _ - _FileX を介してファイルからモジュールを読み込みます*
- ***txm_module_manager_in_place_load** _ - _モジュール データを読み込み、インプレースで実行します*
- ***txm_module_manager_initialize** _ - _モジュール マネージャーを初期化します*
- ***txm_module_manager_mm_initialize** _ - _メモリ管理ハードウェアを初期化します*
- ***txm_module_manager_maximum_module_priority_set** _ - _モジュールで許可されるスレッドの最大優先度を設定します*
- ***txm_module_manager_memory_fault_notify** _ - _メモリ エラー発生時にアプリケーション コールバックを登録します*
- ***txm_module_manager_memory_load** _ - _メモリからモジュールを読み込みます*
- ***txm_module_manager_object_pool_create** _ - _モジュールのオブジェクト プールを作成します*
- ***txm_module_manager_properties_get** _ - _モジュールのプロパティを取得します*
- ***txm_module_manager_start** _ - _指定されたモジュールの実行を開始します*
- ***txm_module_manager_stop** _ - _指定されたモジュールの実行を停止します*
- ***txm_module_manager_unload** _ - _モジュールをアンロードします*

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

モジュールが共有メモリ空間にアクセスできるようにします。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>説明

このサービスは、モジュールがアクセスできる共有メモリ領域のエントリをメモリ管理ハードウェア テーブルに作成します。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュールのインスタンスへのポインター。
- **start_address** 共有メモリ領域の開始アドレス。
- **length** 共有メモリ領域の長さ。
- **attributes** メモリ領域の属性 (キャッシュ、読み取り、書き込みなど)。 属性はポートに固有です。属性の形式については、「[付録](appendix.md)」を参照してください。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ エントリの作成が成功しました。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていないか、機能を使用できません。
- **TX_PTR_ERROR** (0x03) モジュール インスタンスが無効です。
- **TX_START_ERROR** (0x10) モジュールが読み込み済み状態ではありません。
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 開始アドレスの配置が無効です。
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

FileX を介してファイルからモジュールを読み込みます。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>説明

このサービスは、指定されたファイルに格納されているモジュールのバイナリ イメージをモジュールのメモリ領域に読み込み、実行できるように準備します。 指定されたメディアが既に開かれていることが前提となっています。

> [!NOTE]
> ファイルの読み込みには FileX システムが使用されます。 FileX のアクセスを有効にするには、モジュール、モジュール ライブラリ、モジュール マネージャー、ThreadX ライブラリ (モジュール マネージャーのソースを含む) が、プロジェクトで定義されている **FX_FILEX_PRESENT** を使用してビルドされている必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュールのインスタンスへのポインター。
- **module_name** モジュールの名前。
- **media_ptr** 既に開かれている FileX メディアへのポインター。
- **file_name** モジュールのバイナリ ファイルの名前。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) モジュールの読み込みが成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_NO_MEMORY** (0x10) モジュールを読み込むためのメモリが不足しています。
- **TX_NOT_DONE** (0x20) メディアが開いていないか、ファイルが見つからないか、ファイルが無効です。
- **TX_PTR_ERROR** (0x03) モジュール ポインターが無効です。
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 配置が無効です。
- **TXM_MODULE_ALREADY_LOADED** (0xF1) モジュールは既に読み込まれています。
- **TXM_MODULE_INVALID** (0xF2) | モジュール プリアンブルが無効です。
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

モジュール データのみを読み込み、既存の場所でモジュールを実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>説明

このサービスは、モジュールのデータ領域のみをモジュールのメモリ領域に読み込み、実行できるように準備します。 モジュール コードの実行は、インプレースで、つまり、指定された場所のモジュール プリアンブルによって指定されたアドレス オフセットから行われます。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュールのインスタンスへのポインター。
- **module_name** モジュールの名前。
- **location** モジュールのコード領域へのポインター。プリアンブルが最初になります。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) モジュールの読み込みが成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_NO_MEMORY** (0x10) モジュールを読み込むためのメモリが不足しています。
- **TX_PTR_ERROR** (0x03) ポインター、モジュール インスタンス、またはモジュール プリアンブルが無効です。
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 配置が無効です。
- **TXM_MODULE_ALREADY_LOADED** (0xF1) モジュールは既に読み込まれています。
- **TXM_MODULE_INVALID** (0xF2) モジュール プリアンブルが無効です。
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

モジュール マネージャーを初期化します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>説明

このサービスは、モジュール マネージャーの内部リソース (モジュールの読み込みに使用されるメモリ領域など) を初期化します。

### <a name="input-parameters"></a>入力パラメーター

- **module_memory_start** モジュール メモリの先頭へのポインター。
- **module_memory_size** モジュール メモリのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 初期化に成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

メモリ管理ハードウェアを初期化します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>説明

このサービスは MMU を初期化します。

### <a name="input-parameters"></a>入力パラメーター

なし

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 初期化に成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

モジュールで許可されるスレッドの最大優先度を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>説明

このサービスは、モジュールで許可されるスレッドの最大優先度を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュールのインスタンスへのポインター。
- **priority** スレッドの最大優先度。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 初期化に成功しました。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_PTR_ERROR** (0x03) モジュール インスタンスが無効です。
- **TX_START_ERROR** (0x10) モジュールが読み込み済み状態ではありません。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

メモリ エラー発生時にアプリケーション コールバックを登録します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>説明

このサービスは、指定されたアプリケーションのメモリ エラー通知コールバック関数をモジュール マネージャーに登録します。 メモリ エラーが発生すると、この関数が、問題のあるスレッドと問題のあるスレッドに対応するモジュール インスタンスへのポインターを指定して呼び出されます。 モジュール マネージャーの処理では、問題のあるスレッドが自動的に終了しますが、モジュール内の他のスレッドは何も行われないまま放置されます。 メモリ エラーに関連付けられているモジュールをどう処理するかは、アプリケーションによって決定されます。

メモリ エラー自体に関する具体的な情報については、内部の **_txm_module_manager_memory_fault_info** 構造体を参照してください。

> [!NOTE]
> メモリ エラー通知コールバック関数は、メモリ エラーの例外から直接実行されるため、割り込みサービス ルーチンから許可されている ThreadX API のみを呼び出すことができます。 したがって、問題のあるモジュールを停止してアンロードするには、アプリケーション通知コールバックによってアプリケーション タスクにシグナルが送信される必要があります。これにより、モジュールを停止しアンロードできるようになります。

### <a name="input-parameters"></a>入力パラメーター

- **notify_function** アプリケーションのメモリ エラー通知コールバックへの関数ポインター。 NULL 値を指定すると、メモリ エラー通知が無効になります。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 通知関数の登録が成功しました。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

メモリからモジュールを読み込みます。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>説明

このサービスは、モジュールのコードおよびデータ領域を ***txm_module_manager_initialize*** によって設定されたモジュール メモリ領域に読み込み、実行できるように準備します。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュールのインスタンスへのポインター。
- **module_name** モジュールの名前。
- **location** モジュールのコード領域へのポインター。プリアンブルが最初になります。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) モジュールの読み込みが成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_NO_MEMORY** (0x10) モジュールを読み込むためのメモリが不足しています。
- **TX_PTR_ERROR** (0x03) ポインター、モジュール インスタンス、またはモジュール プリアンブルが無効です。
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) 配置が無効です。
- **TXM_MODULE_ALREADY_LOADED** (0xF1) モジュールは既に読み込まれています。
- **TXM_MODULE_INVALID** (0xF2) モジュール プリアンブルが無効です。
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) 互換性のないプロパティです。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

モジュールのオブジェクト プールを作成します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>説明

このサービスは、モジュールが ThreadX/NetX オブジェクトの割り当て元とすることができるモジュール マネージャーのオブジェクト メモリ プールを作成します。これにより、システム オブジェクトがモジュールのメモリ領域に入らないようにします。

### <a name="input-parameters"></a>入力パラメーター

- **pool_memory_start** オブジェクト メモリの先頭へのポインター。
- **pool_memory_size** オブジェクト メモリ プールのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 初期化に成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

モジュールのプロパティを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>説明

このサービスは、モジュールのプロパティ (プリアンブルで指定) を返します。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュール インスタンスへのポインター。
- **module_properties_ptr** モジュールのプロパティの宛先へのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 初期化に成功しました。
- **TX_PTR_ERROR** (0x03) ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

モジュールの実行を開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>説明

このサービスは、指定された読み込み済みモジュールの実行を開始します。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** 前もって読み込まれているモジュール インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) モジュールの開始が成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_PTR_ERROR** (0x03) ポインターまたはモジュール インスタンスが無効です。
- **TX_START_ERROR** (0x10) モジュールは既に開始されています。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

モジュールの実行を停止します。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>説明

このサービスは、前もって読み込まれ、開始されたモジュールを停止します。 モジュールの停止では、モジュールのオプションの停止スレッドの実行、すべてのスレッドの終了、モジュールに関連付けられたすべてのリソースの削除が行われます。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュール インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) モジュールの停止が成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_PTR_ERROR** (0x03) ポインターまたはモジュール インスタンスが無効です。
- **TX_START_ERROR** (0x10) モジュールが開始されていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

モジュールをアンロードします。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>説明

このサービスは、前もって読み込まれ、停止されたモジュールをアンロードし、関連付けられているすべてのモジュール メモリ リソースを解放します。

### <a name="input-parameters"></a>入力パラメーター

- **module_instance** モジュールのインスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) モジュールのアンロードが成功しました。
- **TX_CALLER_ERROR** (0x13) 呼び出し元が無効です。
- **TX_NOT_AVAILABLE** (0x1D) マネージャーが初期化されていません。
- **TX_NOT_DONE** (0x20) モジュールが無効であるか、モジュールが停止していません。
- **TX_PTR_ERROR** (0x03) ポインターまたはモジュール インスタンスが無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>関連項目

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
