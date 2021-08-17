---
title: 第 4 章 - モジュール API
author: philmea
ms.author: philmea
description: この記事では、モジュールで使用できる追加の API の概要を示します。
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1c7590d0ccddc606a6cacdfeb3b3a99631e125554b524c4ce65c8154e65a20ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799134"
---
# <a name="chapter-4---module-apis"></a>第 4 章 - モジュール API

## <a name="summary-of-module-apis"></a>モジュール API の概要

次のように、モジュールではいくつかの追加の API 関数を使用できます。

- ***txm_module_application_request** _ - _常駐コードに対するアプリケーション固有の要求*
- ***txm_module_object_allocate** _ - _オブジェクトに対してモジュールの外部でメモリを割り当てます*
- ***txm_module_object_deallocate** _ - _以前に割り当てられたオブジェクト メモリの割り当てを解除します*
- ***txm_module_object_pointer_get** _ - _システム オブジェクトを見つけ、オブジェクト ポインターを取得します*
- ***txm_module_object_pointer_get_extended** _ - _システム オブジェクトを見つけ、名前の長さに関して安全なオブジェクト ポインターを取得します*

## <a name="return-values"></a>戻り値

一部の Azure RTOS API では、追加のエラー コードが返されます。 これらの追加のエラー コードは次のように定義されます。

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): モジュールに API 呼び出しを行うための適切なプロパティがないことを示します。 たとえば、ユーザー モードでのトレース API の呼び出しです。
- **TXM_MODULE_INVALID_MEMORY** (0xF4): モジュールによって指定されたメモリが無効であるか、または無効な場所にあることを示します。 たとえば、メモリ保護モジュールでは、オブジェクト コントロール ブロックを、モジュールがアクセスできるメモリ内に配置することはできません。
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): API に指定されたコールバックが、モジュールのコードの範囲外であるため、無効です。

---

## <a name="txm_module_application_request"></a>txm_module_application_request

常駐コードに対するアプリケーション固有の要求。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>説明

このサービスは、アプリケーションの常駐部分に対して指定された要求を行います。 要求構造体が呼び出しの前に準備されていることが前提になっています。 要求の実際の処理は、関数 ***_txm_module_manager_application_request*** 内の常駐コードで行われます。 既定では、この関数は空のままになっていて、常駐アプリケーションの開発者が変更するように設計されています。

### <a name="input-parameters"></a>入力パラメーター

- **request** (アプリケーションで定義された) 要求 ID
- **param_1** 最初のパラメーター
- **param_2** 2 番目のパラメーター
- **param_3** 3 番目のパラメーター

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 要求に成功しました。
- **TX_NOT_AVAILABLE** (0x1D) 要求は、常駐コードによってサポートされていません。

### <a name="allowed-from"></a>許可元

モジュール スレッド

### <a name="example"></a>例

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

モジュール オブジェクト コントロール ブロックに対し、(常駐アプリケーションによって作成された) オブジェクト プールのメモリを割り当てます。

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>説明

このサービスは、モジュールの外部のメモリからモジュール オブジェクトにメモリを割り当てます。これにより、モジュールのコードによってオブジェクト コントロール ブロックが破損するのを防ぐことができます。 メモリ保護システムでは、すべてのオブジェクト コントロール ブロックは、この API を使用して割り当てられてからでないと、作成できません。

### <a name="input-parameters"></a>入力パラメーター

- **object_ptr** 割り当てが成功したときのオブジェクト ポインターの宛先。
- **object_size** 割り当てられるオブジェクトのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) オブジェクトの割り当てが成功しました。
- **TX_NO_MEMORY** (0x10) 十分なメモリがありません。
- **TX_NOT_AVAILABLE** (0x1D) モジュール マネージャーによって、割り当て元のオブジェクト プールが作成されていません

### <a name="allowed-from"></a>許可元

モジュール スレッド

### <a name="example"></a>例

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>関連項目

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

以前に割り当てられたオブジェクト メモリの割り当てを解除します

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>説明

***このサービスは、不要になったため非推奨となりました***。

以前 ***txm_module_object_allocate* *_ によって割り当てられたメモリが、"_* _tx_\__delete サービス***" で割り当て解除されます。

### <a name="input-parameters"></a>入力パラメーター

- **object_ptr** 割り当てを解除するオブジェクト ポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) オブジェクトの割り当てが成功しました。

### <a name="allowed-from"></a>許可元

モジュール スレッド

### <a name="example"></a>例

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>関連項目

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

システム オブジェクトを見つけて、オブジェクト ポインターを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>説明

このサービスは、特定の名前を持つ特定の種類のオブジェクト ポインターを取得します。 オブジェクトが見つからない場合は、エラーが返されます。 そうでなく、オブジェクトが見つかった場合は、そのオブジェクトのアドレスが "object_ptr" に入れられます。 これで、このポインターを使用して、システム サービス呼び出しを行って、常駐コードやシステム内の他の読み込み済みモジュールと対話することができます。

### <a name="input-parameters"></a>入力パラメーター

- **object_type** 要求された ThreadX オブジェクトの種類。 有効な種類は次のとおりです。
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** オブジェクトの作成時に定義された、アプリケーション固有のオブジェクト名。
- **object_ptr** オブジェクト ポインターの宛先。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) オブジェクトの取得が成功しました。
- **TX_OPTION_ERROR** (0x08) オブジェクトの種類が無効です。
- **TX_PTR_ERROR** (0x03) 宛先が無効です。
- **TX_SIZE_ERROR** (0x05) サイズが無効です。
- **TX_NO_INSTANCE** (0x0D) オブジェクトが見つかりません。

### <a name="allowed-from"></a>許可元

モジュール スレッド

### <a name="example"></a>例

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>関連項目

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

システム オブジェクトを見つけて、オブジェクト ポインターを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>説明

このサービスは、特定の名前を持つ特定の種類のオブジェクト ポインターを取得します。 オブジェクトが見つからない場合は、エラーが返されます。 そうでなく、オブジェクトが見つかった場合は、そのオブジェクトのアドレスが "object_ptr" に入れられます。 これで、このポインターを使用して、システム サービス呼び出しを行って、常駐コードやシステム内の他の読み込み済みモジュールと対話することができます。

### <a name="input-parameters"></a>入力パラメーター

- **object_type** 要求された ThreadX オブジェクトの種類。 有効な種類は次のとおりです。
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** オブジェクトの作成時に定義された、アプリケーション固有のオブジェクト名。
- **name_length** 名前の長さ。
- **object_ptr** オブジェクト ポインターの宛先。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) オブジェクトの取得が成功しました。
- **TX_OPTION_ERROR** (0x08) オブジェクトの種類が無効です。
- **TX_PTR_ERROR** (0x03) 宛先が無効です。
- **TX_SIZE_ERROR** (0x05) サイズが無効です。
- **TX_NO_INSTANCE** (0x0D) オブジェクトが見つかりません。

### <a name="allowed-from"></a>許可元

モジュール スレッド

### <a name="example"></a>例

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>関連項目

- txm_module_manager_object_pointer_get
