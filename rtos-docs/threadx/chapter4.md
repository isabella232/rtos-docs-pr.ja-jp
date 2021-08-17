---
title: 第 4 章 - Azure RTOS ThreadX サービスの説明
description: この章は、すべての Azure RTO ThreadX サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dabc1603423d8422ed6f8f540f8a06e80d14ec0098c886ca8731ac8ce981f15d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783409"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a>第 4 章 - Azure RTOS ThreadX サービスの説明

この章は、すべての Azure RTO ThreadX サービスの説明をアルファベット順にまとめたものです。 これらの名前は、類似するすべてのサービスがグループ化されるように設計されています。 次の説明の「戻り値」セクション内の **太字** で記載されている値は、API エラー チェックを無効にする際に使用される **TX_DISABLE_ERROR_CHECKING** 定義の影響を受けません。一方、太字以外の値は完全に無効になります。 さらに、「**割り込み可能**」というの見出しの下に「**はい**」と表示されているものは、そのサービスを呼び出すと優先順位の高いスレッドが再開され、呼び出し元のスレッドが割り込まれます。

## <a name="tx_block_allocate"></a>tx_block_allocate

固定サイズのメモリ ブロックを割り当てます

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメモリ プールから固定サイズのメモリ ブロックが割り当てられます。 メモリ ブロックの実際のサイズは、メモリ プールの作成時に決定されます。

> [!IMPORTANT]
> *アプリケーション コードで、割り当てられたメモリ ブロックの外部に書き込まないようにすることが重要です。これが発生すると、隣接する (通常は後続の) メモリ ブロックで破損が発生します。結果は予測不可能で、多くの場合、致命的です。*

### <a name="parameters"></a>パラメーター

- **pool_ptr** <br>以前に作成されたメモリ ブロック プールへのポインター。
- **block_ptr** <br>目標ブロック ポインターへのポインター。 割り当てが正常に行われると、割り当てられたメモリ ブロックのアドレスが、このパラメーターが指す位置に配置されます。
- **wait_option** <br>使用可能なメモリ ブロックがない場合のサービスの動作を定義します。 この待機オプションは次のように定義します。
  - **TX_NO_WAIT** (0x00000000) - **TX_NO_WAIT** を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 *これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです*。
  - **TX_WAIT_FOREVER** (0xFFFFFFF) - **TX_WAIT_FOREVER** を選択すると、呼び出し元のスレッドは、メモリ ブロックが使用可能になるまで無期限に一時停止になります。
  - "*タイムアウト値*" (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、メモリ ブロックを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ ブロックの割り当てに成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にメモリ ブロック プールが削除されました。
- **TX_NO_MEMORY** (0x10) サービスは指定した待機時間内に固定サイズのメモリ ブロックを割り当てることができませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_POOL_ERROR** (0x02) メモリ ブロック プール ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。
- **TX_PTR_ERROR** (0x03) 目標ポインターへのポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a>参照

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create

固定サイズのメモリ ブロック プールの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a>説明

このサービスを使用すると、固定サイズのメモリ ブロック プールが作成されます。 指定したメモリ領域は、次の式を使用して、可能な限り多くの固定サイズのメモリ ブロックに分割されます。

**合計ブロック** = (**合計バイト数**) / (**ブロック サイズ** + sizeof(void *))

> [!NOTE]
>*各メモリ ブロックには、ユーザーには見えない、前の数式の "sizeof(void *)" で表されるオーバー ヘッドのポインターが 1 つ含まれています。*

### <a name="parameters"></a>パラメーター

- **pool_ptr** メモリ ブロック プールの制御ブロックへのポインター。
- **name_ptr** メモリ ブロック プールの名前へのポインター。
- **block_size** 各メモリ ブロック内のバイト数。
- **pool_start** メモリ ブロック プールの開始アドレス。 開始アドレスは、ULONG データ型のサイズに合わせる必要があります。
- **pool_size** メモリ ブロック プールで使用可能な合計バイト数。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ ブロック プールの作成に成功しました。
- **TX_POOL_ERROR** (0x02) メモリ ブロック プール ポインターが無効です。 ポインターが NULL であるか、プールが既に作成されています。
- **TX_PTR_ERROR** (0x03) プールの開始アドレスが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。
- **TX_SIZE_ERROR** (0x05) プールのサイズが無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a>参照

- tx_block_allocate、tx_block_pool_delete
- tx_block_pool_info_get、tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize、tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

メモリ ブロック プールの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したブロック メモリ プールが削除されます。 このプールからのメモリ ブロックを待機しているすべてのスレッドが再開され、**TX_DELETED** 戻りステータスが返されます。

> [!NOTE]
> *プールに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、サービスの完了後に利用できます。また、このアプリケーションでは削除されたプールまたはその前のメモリ ブロックの使用を防ぐ必要があります。*

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたメモリ ブロック プールへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ ブロック プールの削除に成功しました。
- **TX_POOL_ERROR** (0x02) メモリ ブロック プールのポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a>参照

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get、tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize、tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

ブロック プールに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したブロック メモリ プールに関する情報が取得されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたメモリ ブロック プールへのポインター。
- **name** ブロック プールの名前へのポインターの保存先へのポインター。
- **available** ブロック プール内の使用可能なブロック数の保存先へのポインター。
- **total_blocks** ブロック プール内の合計ブロック数の保存先へのポインター。
- **first_suspended** このブロック プールの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。
- **suspended_count** このブロック プールで現在中断されているスレッド数の保存先へのポインター。
- **next_pool** 次に作成されたブロック プールのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ブロック プールの情報の取得に成功しました。
- **TX_POOL_ERROR** (0x02) メモリ ブロック プールのポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get、tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize、tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

ブロック プールのパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメモリ ブロック プールに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> "*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*" **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** " *を使用して構築する必要があります。* "

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたメモリ ブロック プールへのポインター。
- **allocates** このプールで実行される割り当て要求数の保存先へのポインター。
- **releases** このプールで実行されるリリース要求数の保存先へのポインター。
- **suspensions** このプールのスレッド割り当て保留の数の保存先へのポインター。
- **timeouts** このプールの割り当て保留タイムアウト数の保存先へのポインター。

>[!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ブロック プールのパフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) ブロック プールポ インターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされませんでした。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

ブロック プール システムのパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーション内のすべてのメモリ ブロック プールに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> "*ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*" **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** " *を使用して構築する必要があります。* "

### <a name="parameters"></a>パラメーター

- **allocates** すべてのブロック プールで実行される割り当て要求数の合計の保存先へのポインター。
- **releases** すべてのブロック プールで実行されるリリース要求数の合計の保存先へのポインター。
- **suspensions** すべてのブロック プールのスレッド割り当て保留の合計数の保存先へのポインター。
- **timeouts** すべてのブロック プールで実行される割り当て保留タイムアウトの合計の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ブロック プール システムのパフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

ブロック プールの中断リストの優先順位の設定

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、このプール上のメモリ ブロックで中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。 他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** メモリ ブロック プールの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ブロック プールの優先度付けに成功しました。
- **TX_POOL_ERROR** (0x02) メモリ ブロック プールのポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a>参照

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

固定サイズのメモリ ブロックの解放

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a>説明

このサービスを使用すると、以前に割り当てられたブロックが、関連付けられているメモリ プールに解放されます。 このプールからのメモリ ブロックを待機している中断中のスレッドが 1 つ以上ある場合、中断された最初のスレッドにこのメモリ ブロックが割り当てられ、再開されます。

>[!IMPORTANT]
>*アプリケーションは、プールに解放された後にメモリ ブロック領域使用しないようにする必要があります。*

### <a name="parameters"></a>パラメーター

- **block_ptr** 以前に割り当てられていたメモリ ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ ブロックの解放に成功しました。
- **TX_PTR_ERROR** (0x03) メモリ ブロックへのポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>参照

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

メモリのバイト数の割り当て

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したバイト数が、指定したメモリ バイト プールから割り当てられます。

> [!IMPORTANT]
> *アプリケーション コードで、割り当てられたメモリ ブロックの外部に書き込まないようにすることが重要です。これが発生すると、隣接する (通常は後続の) メモリ ブロックで破損が発生します。結果は予測不可能で、多くの場合、致命的です。*

> [!NOTE]
> *このサービスのパフォーマンスは、ブロック サイズとプール内の断片化の量によって機能します。このため、このサービスは、実行のタイムクリティカルなスレッドでは使用しないでください。*

### <a name="parameters"></a>パラメーター

- **pool_ptr** <br>以前に作成されたメモリ ブロック プールへのポインター。
- **memory_ptr** <br>目標メモリ ポインターへのポインター。 割り当てが正常に行われると、割り当てられたメモリ領域のアドレスが、このパラメーターが指す場所に配置されます。
- **memory_size** <br>要求されたバイト数。
- **wait_option** <br>使用可能なメモリが不足している場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
  - **TX_NO_WAIT** (0x00000000) - **TX_NO_WAIT** を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 *これは、サービスが初期化から呼び出された場合に唯一有効なオプションです。*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - **TX_WAIT_FOREVER** を選択すると、呼び出し元のスレッドは、十分なメモリが使用可能になるまで無期限に一時停止になります。
  - *タイムアウト値* (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、メモリを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリの割り当てに成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にメモリ プールが削除されました。
- **TX_NO_MEMORY** (0x10) サービスは指定した待機時間内にメモリを割り当てることができませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。
- **TX_PTR_ERROR** (0x03) 目標ポインターへのポインターが無効です。
- **TX_SIZE_ERROR** (0X05) 要求されたサイズが 0 である、またはプールより大きい値です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a>参照

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

メモリ バイト プールの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a>説明

このサービスを使用すると、指定した領域にメモリ バイト プールが作成されます。 最初のプールは、基本的に 1 つの非常に大きな空きブロックで構成されています。 ただし、割り当てが行われると、プールは小さいブロックに分割されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** メモリ プールの制御ブロックへのポインター。
- **name_ptr** メモリ プールの名前へのポインター。
- **pool_start** メモリ プールの開始アドレス。 開始アドレスは、ULONG データ型のサイズに合わせる必要があります。
- **pool_size** メモリ プールで使用可能な合計バイト数。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ プールの作成に成功しました。
- **TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。 ポインターが NULL であるか、プールが既に作成されています。
- **TX_PTR_ERROR** (0x03) プールの開始アドレスが無効です。
- **TX_SIZE_ERROR** (0x05) プールのサイズが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

メモリ バイト プールの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメモリ バイト プールが削除されます。 このプールからのメモリを待機しているすべてのスレッドが再開され、**TX_DELETED** 戻りステータスが返されます。

> [!IMPORTANT]
> *プールに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、サービスの完了後に利用できます。また、このアプリケーションでは削除されたプール、あるいは以前にそこから割り当てられたメモリの使用を防ぐ必要があります。*

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたメモリ プールへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ プールの削除に成功しました。
- **TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

バイト プールに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメモリ バイト プールに関する情報が取得されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたメモリ プールへのポインター。
- **name** バイト プールの名前へのポインターの保存先へのポインター。
- **available** プール内で使用可能なバイト数の保存先へのポインター。
- **fragments** バイト プール内のメモリ フラグメントの合計数の保存先のポインター。
- **first_suspended** このバイト プールの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。
- **suspended_count** このバイト プールで現在中断されているスレッド数の保存先へのポインター。
- **next_pool** 次に作成されるバイト プールのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) プールの情報の取得に成功しました。
- **TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

バイト プールのパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメモリ バイト プールに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたメモリ バイト プールへのポインター。
- **allocates** このプールで実行された割り当て要求数の保存先へのポインター。
- **releases** このプールで実行された解放要求数の保存先へのポインター。
- **fragments_searched** このプールで割り当て要求中に検索された内部メモリ フラグメントの数の保存先へのポインター。
- **merges** このプールで割り当て要求中に統合された内部メモリ ブロック数の保存先へのポインター。
- **splits** このプールで割り当て要求中に作成された内部メモリ ブロックの分割 (フラグメント) 数の保存先へのポインター。
- **suspensions** このプールのスレッド割り当て保留の数の保存先へのポインター。
- **timeouts** このプールの割り当て保留タイムアウト数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) バイト プールのパフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) バイト プール ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

バイト プール システムのパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのメモリ バイト プールに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **allocates** このプールで実行された割り当て要求数の保存先へのポインター。
- **releases** このプールで実行された解放要求数の保存先へのポインター。
- **fragments_searched** すべてのバイト プールで割り当て要求中に検索された内部メモリ フラグメントの合計数の保存先へのポインター。
- **merges** すべてのバイト プールで割り当て要求中に統合された内部メモリ ブロックの合計数の保存先へのポインター。
- **splits** すべてのバイト プールで割り当て要求中に作成された内部メモリ ブロックの分割 (フラグメント) の合計数の保存先へのポインター。
- **suspensions** すべてのバイト プールのスレッド割り当て保留の合計数の保存先へのポインター。
- **timeouts** すべてのバイト プールでの割り当て保留タイムアウトの合計の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) バイト プールのパフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

 初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

バイト プールの中断リストの優先順位の設定

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、このプール上のメモリで中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。 他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** メモリ プールの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリ プールの優先度付けに成功しました。
- **TX_POOL_ERROR** (0x02) メモリ プール ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

メモリ プールへバイトを解放

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、以前に割り当てられたメモリ領域が、関連付けられているプールに解放されます。 このプールからのメモリを待機しているスレッドが 1 つ以上ある場合、中断された各スレッドにはメモリが割り当てられ、メモリが使い果たされるか、中断されたスレッドがなくなるまで再開されます。 中断されたスレッドにメモリを割り当てるこのプロセスは、常に中断された最初のスレッドから開始されます。

> [!IMPORTANT]
> *アプリケーションは、解放された後にメモリ領域を使用しないようにする必要があります。*

### <a name="parameters"></a>パラメーター

- **memory_ptr** 以前に割り当てられていたメモリ領域へのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メモリの解放に成功しました。
- **TX_PTR_ERROR** (0x03) メモリ領域ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>参照

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

イベント フラグ グループの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、32 イベント フラグのグループが作成されます。 グループ内の 32 イベント フラグすべてが 0 に初期化されます。 各イベント フラグは、1 つのビットで表されます。

### <a name="parameters"></a>パラメーター

- **group_ptr** イベント フラグ グループ制御ブロックへのポインター。
- **name_ptr** イベント フラグ グループの名前へのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント グループの作成に成功しました。
- **TX_GROUP_ERROR** (0x06) イベント グループ ポインターが無効です。 ポインターが **NULL** であるか、イベント グループが既に作成されています。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a>参照

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

イベント フラグ グループの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したイベント フラグ グループが削除されます。 このグループからのイベントを待機しているすべての中断スレッドが再開され、TX_DELETED 戻りステータスが返されます。

>[!IMPORTANT]
> *アプリケーションは、このイベント フラグ グループを削除する前に、イベント フラグ グループに設定された通知コールバックが完了する (または無効になる) ようにしなければなりません。さらに、アプリケーションは、削除されたイベント フラグ グループがすべて今後使用されないようにしなければなりません。*

### <a name="parameters"></a>パラメーター

- **group_ptr** 以前に作成されたイベント フラグ グループへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント フラグ グループの削除に成功しました。
- **TX_GROUP_ERROR** (0x06) イベント フラグ グループ ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a>参照

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

イベント フラグ グループからのイベント フラグの取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したイベント フラグ グループからイベント フラグが取得されます。 各イベント フラグ グループには 32 イベント フラグが含まれています。 各フラグは、1 つのビットで表されます。 このサービスを使用すると、入力パラメーターで選択されているように、さまざまなイベント フラグの組み合わせが取得されます。

### <a name="parameters"></a>パラメーター

- **group_ptr** <br>以前に作成されたイベント フラグ グループへのポインター。
- **requested_flags** <br>32 ビットの符号なし変数。要求されたイベントフラグを表します。
- **get_option** <br>要求されるイベント フラグのすべてが必要か、あるいはいずれかが必要かを指定します。 有効な選択を以下に示します。

  - **TX_AND** (0x02)
  - **TX_AND_CLEAR** (0x03)
  - **TX_OR** (0x00)
  - **TX_OR_CLEAR** (0x01)

    TX_AND または TX_AND_CLEAR を選択すると、すべてのイベント フラグがグループ内に存在しなければならないことが指定されます。 TX_OR または TX_OR_CLEAR を選択すると、任意のイベント フラグで十分であることが指定されます。 TX_AND_CLEAR または TX_OR_CLEAR が指定されている場合は、要求を満たすイベント フラグがクリアされます (ゼロに設定されます)。

- **actual_flags_ptr** <br>取得したイベント フラグが配置されている場所へのポインター。 取得した実際のフラグには、要求されなかったフラグが含まれる場合があることに注意してください。
- **wait_option**  <br>選択したイベント フラグが設定されていない場合のサービスの動作を定義します。 この待機オプションは次のように定義します。
  - **TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 これは、初期化、タイマー、ISR など、サービスが非スレッドから呼び出された場合には唯一有効なオプションです。
  - **TX_WAIT_FOREVER** タイムアウト値 (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、イベントフラグが使用可能になるまで、呼び出し元のスレッドが無期限に中断されます。
  - タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、イベント フラグを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント フラグの取得に成功しました。
- **TX_DELETED** (0X01) スレッドが中断されている間にイベント フラグ グループが削除されました。
- **TX_NO_EVENTS** (0x07) サービスで、指定されたイベントを指定された待機時間内に取得できませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_GROUP_ERROR** (0x06) イベント フラグ グループ ポインターが無効です。
- **TX_PTR_ERROR** (0x03) 実際のイベント フラグのポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。
- **TX_OPTION_ERROR** (0x08) 無効な get オプションが指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

**参照**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

イベント フラグ グループに関する情報の取得

**プロトタイプ**

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

**説明**

このサービスを使用すると、指定したイベント フラグ グループに関する情報が取得されます。

**パラメーター**

- **group_ptr** イベント フラグ グループ制御ブロックへのポインター。
- **name** イベント フラグ グループの名前へのポインターの保存先へのポインター。
- **current_flags** イベント フラグ グループ内の現在の設定フラグの保存先へのポインター。
- **first_suspended** このイベント フラグ グループの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。
- **suspended_count** このイベント フラグ グループで現在中断されているスレッド数の保存先へのポインター。
- **next_group** 次に作成されるイベント フラグ グループのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント グループ情報の取得に成功しました。
- **TX_GROUP_ERROR** (0x06) イベント グループ ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
**参照**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

イベント フラグ グループのパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したイベント フラグ グループに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **group_ptr** 以前に作成されたイベント フラグ グループへのポインター。
- **sets** このグループで実行されたイベント フラグ設定要求数の保存先へのポインター。
- **gets** このグループで実行されたイベント フラグ取得要求数の保存先へのポインター。
- **suspensions** このグループのスレッド イベント フラグ取得中断数の保存先へのポインター。
- **timeouts** このグループのイベント フラグ取得中断タイムアウト数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント フラグ グループのパフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) イベント フラグ グループ ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a>参照

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

パフォーマンス システム情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのイベント フラグ グループに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **sets** すべてのグループで実行されたイベント フラグ設定要求の合計数の保存先へのポインター。
- **gets** すべてのグループで実行されたイベント フラグ取得要求の合計数の保存先へのポインター。
- **suspensions** すべてのグループのスレッド イベント フラグ取得中断の合計数の保存先へのポインター。
- **timeouts** すべてのグループのイベント フラグ取得中断タイムアウトの合計数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント フラグ システムのパフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="example"></a>例

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

イベント フラグ グループでのイベント フラグの設定

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したセット オプションに応じて、イベント フラグ グループ内のイベント フラグが設定またはクリアされます。 イベント フラグ要求が満たされている、中断されたスレッドが再開されます。

### <a name="parameters"></a>パラメーター

- **group_ptr** <br>以前に作成されたイベント フラグ グループ制御ブロックへのポインター。
- **flags_to_set** <br>選択した set オプションに基づいて設定またはクリアするイベント フラグを指定します。
- **set_option** <br>指定されたイベント フラグをグループの現在のイベント フラグへ AND演算するか OR 演算するかを指定します。 有効な選択を以下に示します。
  - **TX_AND** (0x02)
  - **TX_OR** (0x00)

  TX_AND を選択すると、指定されたイベント フラグがグループの現在のイベント フラグへ **AND** 演算することが指定されます。 このオプションは、グループ内のイベント フラグをクリアするためによく使用されます。 あるいは、TX_OR が指定されている場合、指定されたイベント フラグは、グループ内の現在のイベントで **OR** 演算されます。

### <a name="return-values"></a>戻り値
- **TX_SUCCESS** (0x00) イベント フラグの設定に成功しました。
- **TX_GROUP_ERROR** (0x06) イベント フラグ グループへのポインターが無効です。
- **TX_OPTION_ERROR** (0x08) 無効な set オプションが指定されました。

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a>参照

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

イベント フラグの設定時にアプリケーションに通知

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a>説明

このサービスを使用すると、指定したイベント フラグ グループで 1 つ以上のイベント フラグが設定されるたびに呼び出される通知コールバック関数が登録されます。 通知コールバックの処理は、アプリケーションによって定義されます。

### <a name="parameters"></a>パラメーター
- **group_ptr** 以前に作成されたイベント フラグ グループへのポインター。
- **events_set_notify** アプリケーションのイベント フラグ設定通知関数へのポインター。 この値が TX_NULL の場合は、通知が無効です。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント フラグ設定通知の登録に成功しました。
- **TX_GROUP_ERROR** (0x06) イベント フラグ グループ ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。

### <a name="example"></a>例

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a>参照

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

割り込みの有効化と無効化

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a>説明

このサービスを使用すると、入力パラメーター *new_posture* の指定に従って割り込みが有効または無効になります。

> [!NOTE]
> *このサービスがアプリケーション スレッドから呼び出された場合、割り込み状態はそのスレッドのコンテキストの一部のままになります。たとえば、スレッドがこのルーチンを呼び出して割り込みを無効にしてから中断した場合、再開されたとき、割り込みが再び無効になります。*

> [!WARNING]
> *このサービスを使用して、初期化中に割り込みを有効にしないでください。予期しない結果が起きる可能性があります。*

### <a name="parameters"></a>パラメーター

- **new_posture** このパラメーターは、割り込みを無効にするか有効にするかを指定します。 有効な値は、**TX_INT_DISABLE** と **TX_INT_ENABLE** です。 これらのパラメーターの実際の値はポートに固有です。 さらに、一部の処理アーキテクチャで追加の割り込み無効状態がサポートされている場合があります。

### <a name="return-values"></a>戻り値
- **前の状態** このサービスは、前の割り込み状態を呼び出し元に返します。 これにより、サービスのユーザーが、割り込みが無効になった後に前の状態を復元できます。

### <a name="allowed-from"></a>許可元

スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a>参照

None

## <a name="tx_mutex_create"></a>tx_mutex_create

相互排他ミューテックスの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a>説明

このサービスを使用すると、リソース保護のためにスレッド間の相互排他を行うミューテックスが作成されます。

### <a name="parameters"></a>パラメーター

- **mutex_ptr** ミューテックス制御ブロックへのポインター。
- **name_ptr** ミューテックスの名前へのポインター。
- **priority_inherit** このミューテックスが優先度の継承をサポートするかどうかを指定します。 この値が TX_INHERIT の場合、優先度の継承がサポートされます。 ただし、TX_NO_INHERIT が指定されている場合、優先度の継承はこのミューテックスではサポートされません。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックスの作成に成功しました。
- **TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。 ポインターが NULL であるか、ミューテックスが既に作成されています。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。
- **TX_INHERIT_ERROR** (0x1F) 優先度継承パラメーターが無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a>参照

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

相互排他ミューテックスの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したミューテックスが削除されます。 ミューテックスを待機しているすべてのスレッドが再開され、**TX_DELETED** 戻りステータスが返されます。

> [!NOTE]
> *削除されたミューテックスを使用できないようにするのは、アプリケーションの役割です。*

### <a name="parameters"></a>パラメーター

- **mutex_ptr** 以前作成されたミューテックスへのポインターです。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックスの削除に成功しました。
- **TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

ミューテックスの所有権の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したミューテックスの排他的所有権の取得が試みられます。 呼び出し元のスレッドによって既にミューテックスが所有されている場合は、内部カウンターがインクリメントされ、成功ステータスが返されます。

ミューテックスが別のスレッドによって所有されており、このスレッドの優先度が高く、優先度の継承がミューテックス作成時に指定されている場合、低優先度スレッドの優先度は一時的に呼び出し元スレッドの優先度まで上昇します。

> [!NOTE]
> *優先度の継承が指定されたミューテックスを所有する低優先度スレッドの優先度を、ミューテックス所有権を有している間に外部スレッドによって変更しないでください。*

### <a name="parameters"></a>パラメーター

- **mutex_ptr**   <br>以前に作成されたミューテックスへのポインター。
- **wait_option** <br>ミューテックスが既に別のスレッドによって所有されている場合のサービスの動作を定義します。 この待機オプションは次のように定義します。
  - **TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 *これは、サービスが初期化から呼び出された場合に唯一有効なオプションです。*
  - **TX_WAIT_FOREVER** タイムアウト (0xFFFFFFFF) - **TX_WAIT_FOREVER** を選択すると、ミューテックスが使用可能になるまで、呼び出し元のスレッドが無期限に中断されます。
  - タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、ミューテックスを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックスの取得操作に成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にミューテックスが削除されました。
- **TX_NOT_AVAILABLE** (0x1D) 指定された待機時間内にサービスでミューテックスの所有権を取得できませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

ミューテックスに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したミューテックスから情報が取得されます。

### <a name="parameters"></a>パラメーター

- **mutex_ptr** ミューテックス制御ブロックへのポインター。
- **name** ミューテックスの名前へのポインターの保存先へのポインター。
- **count** ミューテックスの所有権数の保存先へのポインター。
- **owner** 所有スレッドのポインターの保存先へのポインター。
- **first_suspended** このミューテックスの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。
- **suspended_count** このミューテックスで現在中断されているスレッド数の保存先へのポインター。
- **next_mutex** 次に作成されるミューテックスへのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックス情報の取得に成功しました。
- **TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

**例**

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

ミューテックスのパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したミューテックスに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **mutex_ptr** 以前作成されたミューテックスへのポインター。
- **puts** このミューテックスで実行された put 要求数の保存先へのポインター。
- **gets** このミューテックスで実行された取得要求数の保存先へのポインター。
- **suspensions** このミューテックスのスレッド ミューテックス取得中断数の保存先へのポインター。
- **timeouts** このミューテックスのミューテックス取得中断タイムアウト数の保存先へのポインター。
- **inversions** このミューテックスのスレッド優先度逆転数の保存先へのポインター。
- **inheritances** このミューテックスのスレッド優先度継承操作の数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックスのパフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) ミューテックス ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

ミューテックスのシステム パフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのミューテックスに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **puts** すべてのミューテックスで実行された配置要求の合計数の保存先へのポインター。
- **gets** すべてのミューテックスで実行された取得要求の合計数の保存先へのポインター。
- **suspensions** すべてのミューテックスのスレッド ミューテックス取得中断の合計数の保存先へのポインター。
- **timeouts** すべてのミューテックスのミューテックス取得中断タイムアウトの合計数の保存先へのポインター。
- **inversions** すべてのミューテックスのスレッド優先度逆転の合計数の保存先へのポインター。
- **inheritances** すべてのミューテックスのスレッド優先度の継承操作の合計数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックスのシステム パフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

ミューテックスの中断リストの優先順位の設定

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、このミューテックスの所有権をめぐって中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。 他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。

### <a name="parameters"></a>パラメーター

- **mutex_ptr** 以前に作成されたミューテックスへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) ミューテックスの優先度付けに成功しました。
- **TX_MUTEX_ERROR** (0x1C) ミューテックス ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

ミューテックスの所有権の解放

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したミューテックスの所有権カウントが減ります。 所有権カウントがゼロの場合は、ミューテックスが使用可能になります。

> [!NOTE]
> *ミューテックスの作成時に優先度の継承が選択された場合、解放するスレッドの優先度は、最初にミューテックスの所有権を取得したときの優先度に復元されます。解放するスレッドがミューテックスを所有している間に行われた他の優先度の変更は元に戻されます。*

### <a name="parameters"></a>パラメーター
- mutex_ptr 以前に作成されたミューテックスへのポインター。

### <a name="return-values"></a>戻り値
- **TX_SUCCESS** (0x00) ミューテックスの解放に成功しました。
- **TX_NOT_OWNED** (0x1E) ミューテックスが呼び出し元によって所有されていません。
- **TX_MUTEX_ERROR** (0x1C) ミューテックスへのポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a>参照

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

メッセージ キューの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a>説明

このサービスを使用すると、主にスレッド間通信に使用される、メッセージ キューが作成されます。 メッセージの合計数は、指定したメッセージ サイズと、キュー内の合計バイト数から計算されます。

> [!NOTE]
> *キューのメモリ領域で指定された合計バイト数が、指定したメッセージ サイズで均等に割り切れない場合、メモリ領域の残りのバイトは使用されません。*

### <a name="parameters"></a>パラメーター

- **queue_ptr** メッセージ キュー制御ブロックへのポインター。
- **name_ptr** メッセージ キューの名前へのポインター。
- **message_size** キュー内の各メッセージのサイズを指定します。 メッセージのサイズは、32 ビットの 1 ワードから 32 ビットの 16 ワードまでの範囲です。 有効なメッセージ サイズのオプションは、1 から 16 の数値です。
- **queue_start** メッセージ キューの開始アドレス。 開始アドレスは、ULONG データ型のサイズに合わせる必要があります。
- **queue_size** メッセージ キューで使用可能な合計バイト数。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メッセージ キューの作成に成功しました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。 ポインターが NULL であるか、キューが既に作成されています。
- **TX_PTR_ERROR** (0x03) メッセージ キューの開始アドレスが無効です。
- **TX_SIZE_ERROR** (0x05) メッセージ キューのサイズが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a>参照

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

メッセージ キューの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメッセージ キューが削除されます。 このキューからのメッセージを待機しているすべてのスレッドが再開され、TX_DELETED 戻りステータスが返されます。

>[!IMPORTANT]
> *アプリケーションは、このキューの送信通知コールバックが、キューを削除する前に完了する (または無効になる) ようにしなければなりません。さらに、アプリケーションは、削除されたキューが今後使用されないようにしなければなりません。* <br><br>*キューに関連付けられているメモリ領域を管理するのもアプリケーションの役割です。これは、サービスの完了後にも利用できます。*

### <a name="parameters"></a>パラメーター

- **queue_ptr** 以前に作成されたメッセージ キューへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 正常にメッセージ キューが削除されました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

メッセージ キューのメッセージを空にする

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメッセージ キューに格納されているすべてのメッセージが削除されます。

キューがいっぱいの場合、中断されたすべてのスレッドのメッセージが破棄されます。 中断された各スレッドが、メッセージ送信が成功したことを示す戻りステータスで再開されます。 キューが空の場合、このサービスは何も行いません。

### <a name="parameters"></a>パラメーター

- **queue_ptr** 以前に作成されたメッセージ キューへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メッセージ キューのフラッシュが成功しました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

メッセージをキューの先頭に送る

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメッセージ キューの前の場所にメッセージが送信されます。 メッセージは、ソース ポインターによって指定されたメモリ領域からキューの先頭に **コピー** されます。

### <a name="parameters"></a>パラメーター

- **queue_ptr** <br>メッセージ キュー コントロール ブロックへのポインター。
- **source_ptr** <br>メッセージへのポインター。
- **wait_option**  <br>メッセージ キューがいっぱいの場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
  - **TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 *これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです。*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、キューに空きができるまで、呼び出しスレッドを無期限に一時停止します。
  - タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、キューに空きができるのを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メッセージの送信に成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にメッセージ キューが削除されました。
- **TX_QUEUE_FULL** (0x0B) 指定された待機時間の間キューがいっぱいだったため、サービスがメッセージを送信できませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。
- **TX_PTR_ERROR** (0x03) メッセージのソース ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

キューに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメッセージ キューに関する情報が取得されます。

### <a name="parameters"></a>パラメーター

- **queue_ptr** 以前に作成されたメッセージ キューへのポインター。
- **name** キューの名前へのポインターの保存先へのポインター。
- **enqueued** 現在キューに入っているメッセージ数の保存先へのポインター。
- **available_storage** キューに現在余裕があるメッセージ数の保存先へのポインター。
- **first_suspended** このキューの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。
- **suspended_count** このキューで現在中断されているスレッド数の保存先へのポインター。
- **next_queue** 次に作成されるキューのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) キュー情報の取得に成功しました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

キューに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したキューに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ "_を使用してビルドする必要があります。*"

### <a name="parameters"></a>パラメーター

- **queue_ptr** 以前に作成されたキューへのポインター。
- **messages_sent** このキューで実行される送信要求の数の保存先へのポインター。
- **messages_received** このキューで実行される受信要求の数の保存先へのポインター。
- **empty_suspensions** このキューでキューが空になった中断数の保存先へのポインター。
- **empty_suspensions** このキューでキューが満杯になった中断数の保存先へのポインター。
- **full_errors** このキューでキューが満杯になったエラー数の保存先へのポインター。
- **timeouts** このキューのスレッド中断タイムアウトの数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) キューのパフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) キュー ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

キュー システムに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのキューに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ "_を使用してビルドする必要があります。*"

### <a name="parameters"></a>パラメーター

- **messages_sent** すべてのキューで実行される送信要求の合計数の保存先へのポインター。
- **messages_received** すべてのキューで実行される受信要求の合計数の保存先へのポインター。
- **empty_suspensions** すべてのキューでキューが空になった中断の合計数の保存先へのポインター。
- ほ **full_suspensions** すべてのキューでキューが満杯になった中断の合計数の保存先へのポインター。
- **full_errors** すべてのキューでキューが満杯になったエラーの合計数の保存先へのポインター。
- **timeouts** すべてのキューのスレッド保留タイムアウトの合計数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

**戻り値**

- **TX_SUCCESS** (0x00) キュー システムのパフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

キューの中断リストの優先順位の設定

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、このキューにメッセージを入れるために (またはメッセージを配置するために) 中断された最優先のスレッドが、中断リストの先頭に配置されます。

他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。

### <a name="parameters"></a>パラメーター

- **queue_ptr** 以前に作成されたメッセージ キューへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) キューの優先度付けに成功しました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

メッセージ キューからのメッセージの取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメッセージ キューからメッセージが取得されます。 取得されたメッセージは、キューから、宛先ポインターによって指定されたメモリ領域に **コピー** されます。 そのメッセージは、その後キューから削除されます。

> [!IMPORTANT]
> *指定された目標メモリ領域は、メッセージを保持できるだけの大きさでなければなりません。つまり、*  ***destination_ptr** _ _によりポイントされるメッセージ送信先は、少なくともこのキューのメッセージ サイズと同じでなければなりません。 それ以外の場合、目標の容量が十分でないと、メモリ破損が次のメモリ領域で発生します。*

### <a name="parameters"></a>パラメーター

- **queue_ptr** <br>以前に作成されたメッセージ キューへのポインター。
- **destination_ptr** <br>メッセージのコピー先の場所。
- **wait_option** <br>メッセージ キューが空の場合のサービスの動作を定義します。 この待機オプションは次のように定義します。
  - **TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです。
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、メッセージが使用可能になるまで無期限に一時停止になります。
  - タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、メッセージを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メッセージの取得に成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にメッセージ キューが削除されました。
- **TX_QUEUE_EMPTY** (0x0A) 指定された待機時間の間キューが空だったため、サービスはメッセージを取得できませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。
- **TX_PTR_ERROR** (0x03) メッセージの目標ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

メッセージ キューへのメッセージの送信

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したメッセージ キューにメッセージが送られます。 送信されたメッセージは、ソース ポインターによって指定されたメモリ領域からキューに **コピー** されます。

### <a name="parameters"></a>パラメーター
- **queue_ptr** <br>以前に作成されたメッセージ キューへのポインター。
- **source_ptr** <br>メッセージへのポインター。
- **wait_option** <br>メッセージ キューがいっぱいの場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
  - **TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 *これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです*。
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、キューに空きができるまで、呼び出しスレッドを無期限に一時停止します。
  - タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、キューに空きができるのを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) メッセージの送信に成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にメッセージ キューが削除されました。
- **TX_QUEUE_FULL** (0x0B) 指定された待機時間の間キューがいっぱいだったため、サービスがメッセージを送信できませんでした。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_QUEUE_ERROR** (0x09) メッセージ キュー ポインターが無効です。
- **TX_PTR_ERROR** (0x03) メッセージのソース ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

**参照**

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify

メッセージをキューに送信するときにアプリケーションに通知

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたキューにメッセージが送信されるたびに呼び出される通知コールバック関数が登録されます。 通知コールバックの処理は、アプリケーションによって定義されます。

>[!NOTE]
> *アプリケーションのキュー送信通知コールバックで、中断オプションを指定した ThreadX API を呼び出してはなりません。*

### <a name="parameters"></a>パラメーター

- **queue_ptr** 以前に作成されたキューへのポインター。
- **queue_send_notify** アプリケーションのキュー送信通知関数へのポインター。 この値が TX_NULL の場合は、通知が無効です。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) キュー送信通知の登録に成功しました。
- **TX_QUEUE_ERROR** (0x09) キュー ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a>参照

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

上限が設定されたカウント セマフォへのインスタンスの配置

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a>説明

このサービスは、指定されたカウント セマフォにインスタンスを 1 つ入れます。これにより、実際にカウント セマフォが 1 つインクリメントします。 カウント セマフォの現在の値が指定されたシーリング以上の場合、インスタンスは配置されず、TX_CEILING_EXCEEDED エラーが返されます。

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** 以前に作成されたセマフォへのポインター。
- **ceiling** セマフォに許可されている最大限度 (有効な値の範囲は 1 から 0xFFFFFFFF)。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS (0x00)** セマフォ シーリング配置に成功しました。
- **TX_CEILING_EXCEEDED** (0x21) 配置要求がシーリングを超えています。
- **TX_INVALID_CEILING** (0x22) 無効な値 0 がシーリングに指定されました。
- **TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a>参照

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

カウント セマフォの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a>説明

このサービスを使用すると、スレッド間同期のカウント セマフォが作成されます。 初期のセマフォ数は、入力パラメーターとして指定されます。

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** セマフォ制御ブロックへのポインター。
- **name_ptr** セマフォの名前へのポインター。
- **initial_count** このセマフォの最初の数を指定します。 有効な値の範囲は 0x00000000 から 0xFFFFFFFF です。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) セマフォの作成に成功しました。
- **TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。 ポインターが NULL であるか、セマフォが既に作成されています。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

カウント セマフォの削除

### <a name="prototype"></a>プロトタイプ
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたカウント セマフォが削除されます。 セマフォ インスタンスを待機しているすべてのスレッドが再開され、TX_DELETED 戻りステータスが返されます。

> [!IMPORTANT]
> *アプリケーションは、このセマフォの put 通知コールバックが、セマフォを削除する前に完了する (または無効になる) ようにしなければなりません。さらに、アプリケーションは、削除されたセマフォが今後使用されないようにしなければなりません。*

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** 以前に作成されたセマフォへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) カウント セマフォの削除に成功しました。
- **TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォ ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

**参照**

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

カウント セマフォからのインスタンスの取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたカウント セマフォからインスタンスが (ひとつだけ) 取得されます。 その結果、指定されたセマフォのカウントが 1 つ減少します。

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** <br>以前に作成されたカウント セマフォへのポインター。
- **wait_option** <br>使用可能なセマフォのインスタンスがない場合、つまり、セマフォのカウントが 0 の場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
  - **TX_NO_WAIT** (0x00000000) - TX_NO_WAIT を選択すると、成功したかどうかに関係なく、このサービスからすぐに戻ります。 *これは、サービスが非スレッドから呼び出された場合にのみ有効なオプションです。たとえば、初期化、タイマー、ISR などです。*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、セマフォ インスタンスが使用可能になるまで無期限に一時停止になります。
  - タイムアウト値 (0x00000001 から 0xFFFFFFFE) - 数値 (1 から 0xFFFFFFFE) を選択すると、セマフォ インスタンスを待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) セマフォ インスタンスの取得に成功しました。
- **TX_DELETED** (0x01) スレッドが中断されている間にカウント セマフォが削除されました。
- **TX_NO_INSTANCE** (0x0D) サービスがカウント セマフォのインスタンスを取得できませんでした (指定された待機時間内のセマフォ数は0です)。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォ ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

セマフォに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したセマフォに関する情報が取得されます。

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** セマフォ制御ブロックへのポインター。
- **name** セマフォの名前へのポインターの保存先へのポインター。
- **current_value** 現在のセマフォのカウントの保存先へのポインター。
- **first_suspended** このセマフォの中断リストの最初にあるスレッドへのポインターの保存先へのポインター。
- **suspended_count** このセマフォで現在中断されているスレッド数の保存先へのポインター。
- **next_semaphore** 次に作成されるセマフォのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 情報が取得されました。

- **TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

セマフォに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したセマフォに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*

**パラメーター**

-  **semaphore_ptr** 以前に作成されたセマフォへのポインター。
-  **puts** このセマフォで実行される配置要求数の保存先へのポインター。
-  **gets**  このセマフォで実行される取得要求数の保存先へのポインター。
-  **suspensions** このセマフォで中断されているスレッド数の保存先へのポインター。
-  **timeouts** このセマフォのスレッド中断タイムアウトの数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) セマフォのパフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) セマフォ ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

セマフォ システムに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのセマフォに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター

- **puts** すべてのセマフォで実行される put 要求の合計数の保存先へのポインター。
- **gets** すべてのセマフォで実行される取得要求の合計数の保存先へのポインター。
- **suspensions** すべてのセマフォのスレッド保留の合計数の保存先へのポインター。
- **suspensions** すべてのセマフォのスレッド保留タイムアウトの合計数の保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) システム パフォーマンス取得。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

セマフォの中断リストの優先順位の設定

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、セマフォのインスタンスをめぐって中断された最も優先度の高いスレッドが、中断リストの先頭に配置されます。 他のすべてのスレッドは、中断された時と同じ FIFO の順序で保持されます。

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** 以前に作成されたセマフォへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) セマフォの優先度付けに成功しました。
- **TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォ ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a>参照

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

カウント セマフォへのインスタンスの配置

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>説明

このサービスは、指定されたカウント セマフォにインスタンスを 1 つ入れます。これにより、実際にカウント セマフォが 1 つインクリメントします。

> [!NOTE]
> *セマフォがオールワン (OxFFFFFFFF) のときにこのサービスが呼び出されると、新しい配置操作によってセマフォはゼロにリセットされます。*

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** 以前に作成されたカウント セマフォ制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) セマフォへの配置に成功しました。
- **TX_SEMAPHORE_ERROR** (0x0C) カウント セマフォへのポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

セマフォの配置時にアプリケーションに通知

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたセマフォが配置されるたびに呼び出される通知コールバック関数が登録されます。 通知コールバックの処理は、アプリケーションによって定義されます。

> [!NOTE]
> *アプリケーションのセマフォ通知コールバックで、中断オプションを指定した ThreadX API を呼び出してはなりません。*

### <a name="parameters"></a>パラメーター

- **semaphore_ptr** 以前に作成されたセマフォへのポインター。
- **semaphore_put_notify** アプリケーションのセマフォ配置通知関数へのポインター。 この値が TX_NULL の場合は、通知が無効です。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) セマフォ配置通知の登録に成功しました。
- **TX_SEMAPHORE_ERROR** (0x0C) セマフォ ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a>参照

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

アプリケーション スレッドの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたタスク エントリ関数で実行が開始されるアプリケーション スレッドが作成されます。 スタック、優先度、プリエンプションしきい値、およびタイムスライスは、入力パラメーターによって指定される属性の中にあります。 さらに、スレッドの初期実行状態も指定されます。

**パラメーター**

- **thread_ptr** スレッド制御ブロックへのポインター。
- **name_ptr** スレッドの名前へのポインター。
- **entry_function** スレッド実行の初期 C 関数を指定します。 スレッドはこのエントリ関数から戻ると、"*完了*" 状態になり、無期限に中断されます。
- **entry_input** 最初の実行時にスレッドのエントリ関数に渡される 32 ビット値。 この入力の使用は、アプリケーションによってのみ決定されます。
- **stack_start** スタックのメモリ領域の開始アドレス。
- **stack_size** スタック メモリ領域内のバイト数。 スレッドのスタック領域は、最悪の場合の関数呼び出し入れ子とローカル変数の使用に対処できるだけの大きさでなければなりません。
- **priority** スレッドの数値優先度。 有効な値の範囲は 0 から (TX_MAX_PRIORITES-1) です。0 の値は最高の優先度を表します。
- **preempt_threshold** 無効なプリエンプションの最高優先度レベル (0 から (TX_MAX_PRIORITIES-1))。 このレベルより高い優先度のみが、このスレッドをプリエンプションできます。 この値は、指定された優先度以下でなければなりません。 値がスレッド優先度と等しいと、プリエンプションしきい値が無効になります。
- **time_slice** このスレッドの実行が、同じ優先度の他の準備完了スレッドが実行されるより前に許可されるタイマー刻みの数。 プリエンプションしきい値を使用すると、タイムスライスが無効になることに注意してください。 有効なタイムスライス値の範囲は、1 から 0xFFFFFFFF までです。 値が **TX_NO_TIME_SLICE** (0 の値) の場合、このスレッドのタイムスライスが無効になります。

  > [!NOTE]
  > *タイム スライシングを使用すると、わずかなシステム オーバーヘッドが発生します。タイム スライシングは、複数のスレッドが同じ優先度を共有している場合にのみ役立ちます。一意の優先度を持つスレッドにはタイム スライスを割り当てないようにしてください。*

- **auto_start** スレッドをすぐに開始するか、保留状態にするかを指定します。 有効なオプションは **TX_AUTO_START** (0x01) と **TX_DONT_START** (0x00) です。 TX_DONT_START が指定されている場合、スレッドを実行するためにアプリケーションは後で tx_thread_resume を呼び出す必要があります。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドの作成に成功しました。
- **TX_THREAD_ERROR** (0x0E) スレッド制御ポインターが無効です。 ポインターが NULL であるか、スレッドは既に作成されています。
- **TX_PTR_ERROR** (0x03) エントリ ポイントの開始アドレスが無効であるか、スタック領域は無効 (通常は NULL) です。
- **TX_SIZE_ERROR** (0x05) スタック領域のサイズが無効です。 スレッドは **TX_MINIMUM_STACK** バイト以上でないと実行できません。
- **TX_PRIORITY_ERROR** (0x0F) スレッド優先度の値が (0 から (TX_MAX_PRIORITIES-1)) の範囲外であるため、無効です。
- **TX_THRESH_ERROR** (0X18) 無効なプリエンプションしきい値が指定されました。 この値は、スレッドの初期優先度以下の有効な優先度でなければなりません。
- **TX_START_ERROR** (0x10) 自動開始の選択が無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a>参照

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

アプリケーション スレッドの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したアプリケーション スレッドが削除されます。 指定されたスレッドは終了または完了した状態でなければならないため、このサービスは、自身を削除しようとしているスレッドから呼び出すことはできません。

> [!NOTE]
> *スレッドのスタックに関連付けられているメモリ領域を管理するのはアプリケーションの役割です。これは、このサービスの完了後に利用できます。また、このアプリケーションでは削除されたスレッドの使用を防ぐ必要があります。*

### <a name="parameters"></a>パラメーター

- **thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドの削除に成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_DELETE_ERROR** (0X11) 指定されたスレッドが終了または完了した状態でありません。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッドとタイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

スレッドの開始または終了時にアプリケーションに通知

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたスレッドが開始または終了するたびに呼び出される通知コールバック関数が登録されます。 通知コールバックの処理は、アプリケーションによって定義されます。

> [!NOTE]
> アプリケーションのスレッド開始/終了通知コールバックでは、中断オプションを指定した ThreadX API を呼び出してはなりません。

### <a name="parameters"></a>パラメーター

- **thread_ptr** 以前作成されたスレッドへのポインター。
- **entry_exit_notify** アプリケーションのスレッド開始/終了通知関数へのポインター。 開始/終了通知関数の 2 番目のパラメーターは、開始または終了が存在するかどうかを指定します。 値 **TX_THREAD_ENTRY** (0x00) は、スレッドが開始されたことを示します。値 **TX_THREAD_EXIT** (0x01) は、スレッドが終了したことを示します。 この値が **TX_NULL** の場合は、通知が無効です。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッド開始/終了通知関数の登録に成功しました。
- **TX_THREAD_ERROR** (0x0E) スレッド ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムが通知機能を無効にしてコンパイルされています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

現在実行中のスレッドを指すポインターを取得

### <a name="prototype"></a>プロトタイプ

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>説明

このサービスを使用すると、現在実行中のスレッドを指すポインターが返されます。 実行中のスレッドがない場合、このサービスは null ポインターを返します。

> [!NOTE]
> *このサービスが ISR から呼び出された場合、戻り値は、実行中の割り込みハンドラーの前に実行されているスレッドを表します。*

### <a name="parameters"></a>パラメーター

None

### <a name="retuen-values"></a>戻り値

- **thread pointer** 現在実行中のスレッドへのポインター。 実行しているスレッドがない場合、戻り値は **TX_NULL** です。

### <a name="allowed-from"></a>許可元

スレッドと ISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

TX_THREAD *my_thread_ptr;

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

スレッドに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したスレッドに関する情報が取得されます。

### <a name="parameters"></a>パラメーター
- **thread_ptr** スレッド制御ブロックへのポインター。
- **name** スレッドの名前を指すポインターの保存先へのポインター。
- **state** スレッドの現在の実行状態の保存先へのポインター。 有効値は次のとおりです。
    - **TX_READY** (0x00)
    - **TX_COMPLETED** (0x01)
    - **TX_TERMINATED** (0x02)
    - **TX_SUSPENDED** (0x03)
    - **TX_SLEEP** (0x04)
    - **TX_QUEUE_SUSP** (0x05)
    - **TX_SEMAPHORE_SUSP** (0x06)
    - **TX_EVENT_FLAG** (0x07)
    - **TX_BLOCK_MEMORY** (0x08)
    - **TX_BYTE_MEMORY** (0x09)
    - **TX_MUTEX_SUSP** (0x0D)  

- **run_count** スレッドの実行カウントの保存先へのポインター。
- **priority** スレッドの優先度の保存先へのポインター。
- **preemption_threshold** スレッドのプリエンプションしきい値の保存先へのポインター。
**time_slice** スレッドのタイムスライスの保存先へのポインター。
**next_thread** 次に作成されるスレッド ポインターの保存先へのポインター。

**suspended_thread** 中断リスト内の次のスレッドへのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッド情報の取得に成功しました。
- **TX_THREAD_ERROR** (0x0E) スレッド制御ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

スレッドに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したスレッドに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター
- **thread_ptr** 以前作成されたスレッドへのポインター。
- **resumptions** このスレッドの再開数の保存先へのポインター。
- **resumptions** このスレッドの中断数の保存先へのポインター。
- **solicited_preemptions** ThreadX API サービス呼び出しがこのスレッドにより行われた結果としてのプリエンプション数の保存先へのポインター。
- **interrupt_preemptions** 割り込み処理の結果であるこのスレッドのプリエンプション数の保存先へのポインター。
- **priority_inversions** このスレッドの優先度逆転数の保存先へのポインター。
- **time_slices** このスレッドのタイムスライス数の保存先へのポインター。
- **relinquishes** このスレッドにより実行されたスレッド放棄の数の保存先へのポインター。
- **timeouts** このスレッドでの保留タイムアウトの数の保存先へのポインター。
- **wait_aborts** このスレッドで実行された待機中止の数の保存先へのポインター。
- **last_preempted_by** このスレッドを最後にプリエンプションしたスレッド ポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッド パフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) スレッド ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

スレッド システムに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのスレッドに関するパフォーマンス情報が取得されます。

*このサービスがパフォーマンス情報を返すためには、ThreadX ライブラリとアプリケーションが*

***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _が定義された状態でビルドされる必要があります。*

### <a name="parameters"></a>パラメーター

- **resumptions** スレッド再開の合計数の保存先へのポインター。
- **suspensions** スレッド保留の合計数の保存先へのポインター。
- **solicited_preemptions** スレッドが ThreadX API サービスを呼び出した結果としてのスレッド プリエンプションの合計数の保存先へのポインター。
- **interrupt_preemptions** 割り込み処理の結果としてのスレッド プリエンプションの合計数の保存先へのポインター。
- **priority_inversions** スレッド優先度逆転の合計数の保存先へのポインター。
- **time_slices** スレッド タイムスライスの合計数の保存先へのポインター。
- **resumptions** スレッド放棄の合計数の保存先へのポインター。
- **timeouts** スレッド保留タイムアウトの合計数の保存先へのポインター。
- **wait_aborts** スレッド待機中止の合計数の保存先へのポインター。
- **non_idle_returns** 別のスレッドの実行準備が整ったときにスレッドがシステムに戻る回数の保存先へのポインター。
- **idle_returns** 実行する準備ができているスレッドが他にない場合 (アイドル状態のシステム) にスレッドがシステムに戻る回数の保存先へのポインター。

> [!NOTE]
> *パラメーターに **TX_NULL** を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッド システム パフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

アプリケーション スレッドのプリエンプションしきい値の変更

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したスレッドのプリエンプションしきい値を変更できます。 プリエンプションしきい値により、そのプリエンプションしきい値以下のスレッドにより、指定されたスレッドがプリエンプションされることがなくなります。

>[!NOTE]
> *プリエンプションしきい値を使用すると、指定されたスレッドのタイム スライシングが無効になります。*

### <a name="parameters"></a>パラメーター
- **thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。
- **new_threshold** 新しいプリエンプションしきい値の優先度レベルl (0 から (TX_MAX_PRIORITIES-1))。
- **old_threshold** 前のプリエンプションしきい値を返す場所へのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) プリエンプションしきい値の変更に成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_THRESH_ERROR** (0x18) 指定された新しいプリエンプションしきい値が、有効なスレッド優先度でない ((0 から (**TX_MAX_PRIORITIES**-1) 以外の値) か、現在のスレッド優先度より大きい (優先度が低い) です。
- **TX_PTR_ERROR** (0x03) 前のプリエンプションしきい値保存場所へのポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッドとタイマー

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

アプリケーション スレッドの優先度の変更

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたスレッドの優先度が変更されます。 有効な優先順位の範囲は 0 から (TX_MAX_PRIORITES-1) です。0 は最高の優先度レベルを表します。

> [!IMPORTANT]
> *指定されたスレッドのプリエンプションしきい値は、自動的に新しい優先度に設定されます。 新しいしきい値が必要な場合は、***tx_thread_preemption_change** _ サービスをこの呼び出しの後に使用する必要があります。_

### <a name="parameters"></a>パラメーター

- **thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。
- **new_priority** 新しいスレッド優先度レベル (0 から (TX_MAX_PRIORITIES-1))。
- **old_priority** スレッドの前の優先度を返す場所を指すポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) 優先度の変更に成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_PRIORITY_ERROR** (0x0F) 定された新しい優先度が無効 ((0 から (TX_MAX_PRIORITIES-1) 以外の値) です。
- **TX_PTR_ERROR** (0x03) 前の優先度保存場所へのポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッドとタイマー

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

制御を他のアプリケーション スレッドに放棄

### <a name="prototype"></a>プロトタイプ

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a>説明

このサービスは、同等以上の優先順位で実行可能な他のスレッドに対してプロセッサ制御を放棄します。

> [!NOTE]
> *このサービスは、同じ優先順位のスレッドに対して制御を放棄するだけでなく、現在のスレッドのプリエンプションしきい値の設定によって実行できない最高優先順位のスレッドに対しても制御を放棄します。*

### <a name="parameters"></a>パラメーター

なし

### <a name="return-values"></a>戻り値

なし

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="examples"></a>例

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

スレッドのリセット

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、スレッドの作成時に定義されたエントリ ポイントで実行するよう指定されたスレッドがリセットされます。 スレッドは、リセットするためには **TX_COMPLETED** または **TX_TERMINATED** の状態である必要があります。

> [!IMPORTANT]
> *スレッドは、再実行するためには再開する必要があります。*

### <a name="parameters"></a>パラメーター

- **thread_ptr** 以前作成されたスレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドのリセットに成功しました。
- **TX_NOT_DONE** (0X20) 指定されたスレッドが **TX_COMPLETED** または **TX_TERMINATED** の状態でありません。
- **TX_THREAD_ERROR** (0x0E) スレッド ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

TX_THREAD my_thread;

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

中断したアプリケーション スレッドの再開

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、***tx_thread_suspend*** 呼び出しによって以前に中断されたスレッドの実行が再開または準備されます。 また、このサービスを使用すると、自動開始なしで作成されたスレッドが再開されます。

### <a name="parameters"></a>パラメーター

- **thread_ptr** 中断されたアプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドの再開に成功しました。
- **TX_SUSPEND_LIFTED** (0x19) 以前に設定された遅延中断が解除されました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_RESUME_ERROR** (0X12) 指定されたスレッドは中断されていないか、以前に **_tx_thread_suspend_** 以外のサービスによって中断されています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

TX_THREAD my_thread;

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

現在のスレッドを指定された時間だけ中断

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a>説明

このサービスによって、呼び出し元のスレッドは、指定したタイマー ティック数だけ中断されます。 タイマー刻みに関連付けられている物理時間の量は、アプリケーション固有です。 このサービスは、アプリケーション スレッドからのみ呼び出すことができます。

### <a name="parameters"></a>パラメーター

- **timer_ticks** 呼び出し元のアプリケーション スレッドを中断するタイマー刻み数 (0 から 0xFFFFFFFF まで)。 0 を指定した場合、サービスはすぐに戻ります。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドのスリープに成功しました。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_CALLER_ERROR** (0X13) サービスが非スレッドから呼び出されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a>参照

- tx_thread_create, tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

スレッド スタック エラー通知コールバックの登録

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a>説明

このサービスを使用すると、スレッド スタック エラーを処理するための通知コールバック関数が登録されます。 ThreadX は実行中にスレッド スタック エラーを検出すると、この通知関数を呼び出してエラーを処理します。 エラーの処理は、アプリケーションによって完全に定義されます。 違反しているスレッドの中断からシステム全体のリセットまであらゆることが行なわれる可能性があります。

> [!IMPORTANT]
> *ThreadX ライブラリは、このサービスがパフォーマンス情報を返すために定義された* **TX_ENABLE_STACK_CHECKING** *を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター
- **error_handler** アプリケーションのスタック エラー処理関数へのポインター。 この値が TX_NULL の場合、通知は無効です。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドのリセットに成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

アプリケーション スレッドの中断

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したアプリケーション スレッドが中断されます。 スレッドがこのサービスを呼び出して自身を中断する場合があります。

> [!NOTE]
> *指定されたスレッドが既に別の理由で中断されている場合、この中断は、前の中断が解除されるまで内部的に保持されます。この場合、指定されたスレッドの無条件の中断が実行されます。後続の無条件中断要求は無効です。*

中断された後、スレッドを再実行するには ***tx_thread_resume*** によって再開する必要があります。

### <a name="parameters"></a>パラメーター

- **thread_ptr** アプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッドの中断に成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_SUSPEND_ERROR** (0X14) 指定されたスレッドは終了または完了の状態です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

アプリケーション スレッドを終了

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したアプリケーション スレッドが、スレッドが中断されているかどうかに関係なく終了します。 スレッドはこのサービスを呼び出して自身を終了する場合があります。

> [!NOTE]
> *スレッドが終了に適した状態になるようにするのは、アプリケーションの責任です。たとえば、スレッドは、重要なアプリケーションの処理中、または他のミドルウェア コンポーネント内で終了して、その処理が不明な状態のままになるようにしてはなりません。*

> [!IMPORTANT]
> *終了した後、スレッドは、再実行するためにはリセットする必要があります。*

### <a name="parameters"></a>パラメーター

- **thread_ptr** アプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値
- **TX_SUCCESS** (0x00) スレッドの終了に成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッドとタイマー

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a>参照

- tx_thread_create tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

アプリケーション スレッドのタイムスライスの変更

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたアプリケーション スレッドのタイムスライスが変更されます。 スレッドのタイムスライスを選択すると、それが、優先度が同等以上の他のスレッドが実行可能になるまで、指定したタイマー刻み数を超えて実行されることがなくなります。

> [!NOTE]
> *プリエンプションしきい値を使用すると、指定されたスレッドのタイム スライシングが無効になります。*

### <a name="parameters"></a>パラメーター

- **thread_ptr** アプリケーション スレッドへのポインター。
- **new_time_slice** 新しいタイム スライス値。 有効な値は TX_NO_TIME_SLICE と 1 から 0xFFFFFFFF の数値です。
- **old_time_slice** 指定したスレッドの前のタイムスライス値を格納する場所へのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) タイムスライスの変更が成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_PTR_ERROR** (0x03) 前のタイムスライス保存場所へのポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッドとタイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

指定したスレッドの中断の停止

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>説明

このサービスは、指定されたスレッドのスリープまたはその他のオブジェクトの中断を中止します。 待機が中止されると、スレッドが待機していたサービスから **TX_WAIT_ABORTED** 値が返されます。

> [!NOTE]
> *このサービスでは、tx_thread_suspend サービスによって行われた明示的な中断は解放されません。*

### <a name="parameters"></a>パラメーター

- **thread_ptr** 以前に作成されたアプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) スレッド待機中止に成功しました。
- **TX_THREAD_ERROR** (0x0E) アプリケーション スレッド ポインターが無効です。
- **TX_WAIT_ABORT_ERROR** (0x1B) 指定されたスレッドが待ち状態ではありません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能
はい

### <a name="example"></a>例

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a>参照

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

現在の時刻を取得

アプリケーション タイマー

### <a name="prototype"></a>プロトタイプ

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a>説明

このサービスを使用すると、内部システム クロックの内容が返されます。 タイマー刻みごとに内部システム クロックが 1 つ増えます。 システム クロックは初期化中に 0 に設定されますが、サービス ***tx_time_set*** によって特定の値に変更できます。

> [!NOTE]
> *各タイマー刻みが表す実際の時間は、アプリケーションに固有です。*

**パラメーター**

None

### <a name="return-values"></a>戻り値

- **system clock ticks** 自走の内部システム クロックの値。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能
いいえ

### <a name="example"></a>例

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a>参照

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

現在の時刻の設定

### <a name="prototype"></a>プロトタイプ

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a>説明

このサービスを使用すると、内部システム クロックを指定した値に設定できます。 タイマー刻みごとに内部システム クロックが 1 つ増えます。

> [!NOTE]
> *各タイマー刻みが表す実際の時間は、アプリケーションに固有です。*

### <a name="parameters"></a>パラメーター

- **new_time** システム クロックに設定する新しい時間。有効な値の範囲は 0 から 0xFFFFFFFF です。

### <a name="return-values"></a>戻り値

なし

### <a name="allowed-from"></a>許可元

スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a>参照

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

アプリケーション タイマーのアクティブ化

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したアプリケーション タイマーがアクティブになります。 同じ時刻に期限が切れるタイマーの期限切れルーチンは、アクティブになった順序で実行されます。

> [!NOTE]
> *期限切れになったワンショット タイマーは、再びアクティブにする前に*  ***tx_timer_change** _ _によってリセットしなければなりません。*

### <a name="parameters"></a>パラメーター

- **timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。

**戻り値**

- **TX_SUCCESS** (0x00) アプリケーション タイマーのアクティブ化に成功しました。
- **TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。
- **TX_ACTIVATE_ERROR** (0x17) タイマーは既にアクティブであるか、あるいは既に期限が切れているワンショット タイマーです。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a>参照

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

アプリケーション タイマーの変更

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したアプリケーション タイマーの有効期限特性が変更されます。 このサービスを呼び出す前に、タイマーを非アクティブにする必要があります。

> [!NOTE]
> *このサービスの後に、タイマーを再び開始するために*  ***tx_timer_activate** _ _サービスの呼び出しが必要になります。*

### <a name="parameters"></a>パラメーター

- **timer_ptr** タイマー制御ブロックへのポインター。
- **initial_ticks** タイマー有効期限の最初のティック数を指定します。 有効な値の範囲は 1 から 0xFFFFFFFF です。
- **reschedule_ticks** 最初の後の、すべてのタイマー有効期限のティック数を指定します。 このパラメーターにゼロを指定すると、タイマーは "*ワンショット*" タイマーになります。 それ以外の定期的なタイマーの場合、有効な値の範囲は 1 から 0xFFFFFFFF です。

> [!NOTE]
> *期限切れになったワンショット タイマーは、再びアクティブにする前に*
***tx_timer_change** _ _によってリセットしなければなりません。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) アプリケーション タイマーの変更に成功しました。
- **TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。
- **TX_TICK_ERROR** (0x16) 最初のティックに無効な値 (0) が指定されました。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

アプリケーション タイマーの作成

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a>説明

このサービスを使用すると、指定した有効期限関数と期間でアプリケーション タイマーが作成されます。

### <a name="parameters"></a>パラメーター

- **timer_ptr** タイマー制御ブロックへのポインター
- **name_ptr** タイマーの名前へのポインター。
- **expiration_function** タイマーの期限が切れたとき呼び出すアプリケーション関数。
- **expiration_input** タイマーの期限が切れたとき有効期限関数に渡す入力。
- **initial_ticks** タイマー有効期限の最初のティック数を指定します。 有効な値の範囲は 1 から 0xFFFFFFFF です。
- **reschedule_ticks** 最初の後の、すべてのタイマー有効期限のティック数を指定します。 このパラメーターにゼロを指定すると、タイマーは "*ワンショット*" タイマーになります。 それ以外の定期的なタイマーの場合、有効な値の範囲は 1 から 0xFFFFFFFF です。

  > [!NOTE]
  > *ワンショット タイマーが期限切れになったら、再びアクティブにする前に tx_timer_change によってリセットしなければなりません。*

- **auto_activate** タイマーを作成時に自動的にアクティブにするかどうかを決定します。 この値が **TX_AUTO_ACTIVATE** (0x01) の場合、タイマーはアクティブになります。 それ以外の場合、値 **TX_NO_ACTIVATE** (0x00) を選択すると、タイマーは非アクティブ状態で作成されます。 この場合、その後にタイマーを実際に開始するには、**_tx_timer_activate_** サービスを呼び出す必要があります。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) アプリケーション タイマーの作成に成功しました。
- **TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。 ポインターが NULL であるか、タイマーは既に作成されています。
- **TX_TICK_ERROR** (0x16) 最初のティックに無効な値 (0) が指定されました。
- **TX_ACTIVATE_ERROR** (0x17) 無効なアクティブ化が選択されました。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

アプリケーション タイマーの非アクティブ化

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したアプリケーション タイマーが非アクティブになります。 タイマーが既に非アクティブ化されている場合、このサービスによる影響はありません。

### <a name="parameters"></a>パラメーター

- **timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) アプリケーション タイマーの非アクティブ化に成功しました。
- **TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

アプリケーション タイマーの削除

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたアプリケーション タイマーが削除されます。

> [!NOTE]
> *削除されたタイマーを使用できないようにするのは、アプリケーションの役割です。*

### <a name="parameters"></a>パラメーター

- **timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) アプリケーション タイマーの削除に成功しました。
- **TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。
- **TX_CALLER_ERROR** (0x13) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

アプリケーション タイマーに関する情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたアプリケーション タイマーに関する情報が取得されます。

### <a name="parameters"></a>パラメーター

- **timer_ptr** 以前に作成されたアプリケーション スレッドへのポインター。
- **name** タイマーの名前へのポインターの保存先へのポインター。
- **active** タイマーのアクティブ表示の保存先へのポインター。 タイマーがアクティブでない場合やこのサービスがタイマー自体から呼び出された場合は、**TX_FALSE** 値が返されます。 それ以外の場合、タイマーがアクティブな場合は、**TX_TRUE** 値が返されます。
- **remaining_ticks** タイマーが期限切れになるまでのタイマー刻み数の保存先へのポインター。
- **reschedule_ticks** このタイマーを自動的に再スケジュールするために使用されるタイマー刻み数の保存先へのポインター。 値がゼロの場合、タイマーはワンショットであり、再スケジュールされません。
- **next_timer** 次に作成されるアプリケーション タイマーのポインターの保存先へのポインター。

> [!NOTE]
> *パラメーターに **TX_NULL** を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) タイマー情報の取得に成功しました。
- **TX_TIMER_ERROR** (0x15) アプリケーション タイマー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

タイマーに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたアプリケーション タイマーに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された*  ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _を使用してビルドする必要があります。*

### <a name="parameters"></a>パラメーター
- **timer_ptr** 以前に作成されたタイマーへのポインター。
- **activates** このタイマーで実行されたアクティブ化要求数の保存先へのポインター。
- **reactivates** この周期的なタイマーに従って実行された自動再アクティブ化の回数の保存先へのポインター。
- **deactivates** このタイマーで実行された非アクティブ化要求数の保存先へのポインター。
- **expirations** このタイマーの有効期限切れの回数の保存先へのポインター。
- **expiration_adjusts** このタイマーで実行される内部有効期限調整の数の保存先へのポインター。 これらの調整は、既定のタイマー一覧サイズより大きいタイマー (既定では有効期限が 32 刻みを超えるタイマー) のタイマー割り込み処理で行われます。

> [注] *パラメーターに TX_NULL を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) タイマー パフォーマンスの取得に成功しました。
- **TX_PTR_ERROR** (0x03) タイマー ポインターが無効です。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

タイマー システムに関するパフォーマンス情報の取得

### <a name="prototype"></a>プロトタイプ

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a>説明

このサービスを使用すると、システム内のすべてのアプリケーション タイマーに関するパフォーマンス情報が取得されます。

> [!IMPORTANT]
> *ThreadX ライブラリとアプリケーションは、パフォーマンス情報を返すために、このサービス用に定義された* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *を使用してビルドする必要があります。*

**パラメーター**

- **activates** すべてのタイマーで実行されたアクティブ化要求の合計数の保存先へのポインター。
- **reactivates** すべての周期的なタイマーに従って実行された自動再アクティブ化の合計回数の保存先へのポインター。
- **deactivates** すべてのタイマーで実行された非アクティブ化要求の合計数の保存先へのポインター。
- **expirations** すべてのタイマーの有効期限切れの合計数の保存先へのポインター。
- **expiration_adjusts** すべてのタイマーで実行された内部有効期限調整の合計数の保存先へのポインター。 これらの調整は、既定のタイマー一覧サイズより大きいタイマー (既定では有効期限が 32 刻みを超えるタイマー) のタイマー割り込み処理で行われます。

> [!NOTE]
> *パラメーターに **TX_NULL** を指定することは、そのパラメーターが必須ではないことを示します。*

### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) タイマー システム パフォーマンスの取得に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムがパフォーマンス情報が有効な状態でコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="example"></a>例

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>参照

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
