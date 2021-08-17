---
title: 第 3 章 - ARMv8-M 用の ThreadX API
description: この章では、ARMv8-M 固有の ThreadX サービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99633db55a5d93eb32ce4fb5429f3fe2f9ab5137cffc30b27982f702cece1ca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791501"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>第 3 章  ARMv8-M 用の ThreadX API

この章では、ARMv8-M 固有の ThreadX サービスについてアルファベット順に説明します。 これらの名前は、類似するすべてのサービスがグループ化されるように設計されています。 以下の説明にある「戻り値」セクション内で **太字** で記載されている値は、API エラー チェックを無効にする際に使用される **TX_DISABLE_ERROR_CHECKING** 定義の影響を受けません。一方、太字ではない値は完全に無効になります。

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) セキュア メモリ内でスレッド スタックを割り当てます。
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) セキュア メモリ内のスレッド スタックを解放します

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

セキュア メモリ内でスレッド スタックを割り当てます。

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>説明

このサービスは、セキュア メモリ内でサイズ stack_size バイトのスタックを割り当てます。 この関数は、セキュアな関数を呼び出すすべてのスレッドに対して呼び出される必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **thread_ptr** 以前作成されたスレッドへのポインター。

- **stack_size** セキュア スタックのサイズ。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 要求に成功しました。

- **TX_SIZE_ERROR** (0x05) スタック サイズが範囲外です。

- **TX_THREAD_ERROR** (0x0E) 無効なスレッド ポインターです。

- **TX_NO_MEMORY** (0x10) メモリを割り当てることができません。

- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはセキュア モードで実行するようコンパイルされました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>参照

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

セキュア メモリ内のスレッド スタックを解放します。 

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>説明

このサービスは、セキュア メモリ内のスレッドのセキュア スタックを解放します。 スレッドにセキュア スタックが存在し、スレッドがセキュアな関数を呼び出す必要がなくなった場合またはスレッドが削除された場合は、この関数を呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **thread_ptr** 以前作成されたスレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 要求に成功しました。

- **TX_THREAD_ERROR** (0x0E) 無効なスレッド ポインターです。

- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはセキュア モードで実行するようコンパイルされました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>参照

tx_thread_secure_stack_allocate
