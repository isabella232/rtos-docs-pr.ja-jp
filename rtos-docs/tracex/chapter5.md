---
title: 第 5 章 - トレース バッファーの生成
description: この章では、Azure RTOS TraceX イベント バッファーを構築する方法について説明します。また、基になるバッファーの形式についても説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 7d5c90675728fc7e374d625f5a9ae27340268ca8398200c68fb7113a84aa2983
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801786"
---
# <a name="chapter-5---generating-trace-buffers"></a>第 5 章 - トレース バッファーの生成

この章では、Azure RTOS TraceX イベント バッファーを構築する方法について説明します。また、基になるバッファーの形式についても説明します。

## <a name="threadx-event-trace-support"></a>ThreadX イベント トレースのサポート

ThreadX には、すべての ThreadX サービス、スレッド状態の変更、およびユーザー定義イベントに対する組み込みのイベント トレース サポートが用意されています。 ThreadX イベント トレース機能は、主に、アプリケーションの最後の "n" 件のアクティビティを分析する事後分析ツールとして設計されています。 この情報から、開発者は、問題や最適化の対象となる可能性のあるターゲットを見つけることができます。

TraceX では、ThreadX によって作成されたイベント トレース バッファーをグラフィカルに表示します。 次に、バッファーの作成方法と、基になるバッファーの形式について説明します。

## <a name="enabling-event-trace"></a>イベント トレースの有効化

イベント トレースを有効にするには、タイムスタンプ定数を定義し、**TX_ENABLE_EVENT_TRACE** が定義された ThreadX ライブラリをビルドし、**tx_trace_enable** 関数を呼び出してトレースを有効にします。

## <a name="defining-time-stamp-constants"></a>タイムスタンプ定数の定義

タイムスタンプ定数は、イベント トレース エントリで使用されるタイムスタンプを開発者が制御できるように設計されています。 2 つのタイムスタンプ定数とその既定値は次のとおりです。

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

上記の定数は **tx_port.h** で定義され、各イベントで 1 つずつ増加する "偽の" タイムスタンプを作成します。 実際のタイムスタンプ定義の例を次に示します。

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

上記の定数は、アドレス 0x13000004 を読み取ることによって取得される 32 ビット タイマーを指定します。 ほとんどのアプリケーション固有のタイムスタンプは、同様の方法でセットアップする必要があります。

## <a name="exporting-the-trace-buffer"></a>トレース バッファーのエクスポート

TraceX では、ホスト上でバイナリ、Intel HEX、または Motorola S-Record ファイル形式のトレース バッファーが必要です。 これを実現する最も簡単な方法は、ターゲットを停止し、***tx_trace_enable*** 関数に指定したメモリ領域をホスト上のファイルにダンプするようにデバッガーに指示することです。

> [!WARNING]
>***トレース収集コード自体でターゲットを停止しないように注意してください。これにより、無効なトレース情報が生成される可能性があります。プログラムが ThreadX 内で停止した場合、トレース バッファーをダンプする前に、トレース挿入マクロをステップ オーバーすることをお勧めします。***

> [!IMPORTANT]
> *付録 D では、さまざまな開発ツール内からトレース バッファーをダンプする方法を示します。*

## <a name="extended-event-trace-api"></a>拡張イベント トレース API

**TX_ENABLE_EVENT_TRACE** が定義された状態で ThreadX をビルドすると、アプリケーションで次の新しいイベント トレース API を使用できるようになります。

- tx_trace_enable: *イベントのトレースを有効にする*
- tx_trace_event_filter: *指定されたイベントをフィルター処理する*
- tx_trace_event_unfilter: *指定されたイベントをフィルター解除する*
- tx_trace_disable: *イベントのトレースを無効にする*
- tx_trace_isr_enter_insert: *ISR トレース開始イベントを挿入する*
- tx_trace_isr_exit_insert: *ISR トレース終了イベントを挿入する*
- tx_trace_buffer_full_notify: *トレース バッファーの完全なアプリケーション コールバックを登録する*
- tx_trace_user_event_insert: *ユーザー イベントを挿入する*

### <a name="tx_trace_enable"></a>tx_trace_enable

イベントのトレースを有効にする

#### <a name="prototype"></a>プロトタイプ

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>説明
このサービスにより、ThreadX 内のイベント トレースが有効になります。 アプリケーションでは、トレース バッファーと ThreadX オブジェクトの最大数を指定します。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター

- **trace_buffer_start**: ユーザーが指定したトレース バッファーの先頭へのポインター。
- **trace_buffer_size**: トレース バッファーのメモリ内の合計バイト数。 トレース バッファーが大きいほど、格納できるエントリが増えます。
- **registry_entries**: トレース レジストリに保持するアプリケーション ThreadX オブジェクトの数。 レジストリは、オブジェクトのアドレスとオブジェクト名を関連付けるために使用されます。 これは、GUI トレース分析ツールで非常に便利です。

#### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント トレースの有効化に成功しました。
- **TX_SIZE_ERROR** (0x05) 指定されたトレース バッファー サイズが小さすぎます。 トレース ヘッダー、オブジェクト レジストリ、および少なくとも 1 つのトレース エントリに十分な大きさである必要があります。
- **TX_NOT_DONE** (0x20) イベント トレースは既に有効になっています。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。

#### <a name="allowed-from"></a>許可元

初期化とスレッド

#### <a name="example"></a>例

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>参照

tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

指定されたイベントをフィルター処理する

#### <a name="prototype"></a>プロトタイプ

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>説明

このサービスでは、指定されたイベントをフィルター処理して、アクティブなトレース バッファーに挿入されないようにします。 既定では、*tx_trace_enable* が呼び出された後にはイベントはフィルター処理されません。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター

- **event_filter_bits**: フィルター処理するイベントに対応するビット。 複数のイベントをフィルター処理するには、適切な定数の論理和を指定します。 この変数の有効な定数は、次のように定義されています。

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベントのフィルター処理に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。

#### <a name="allowed-from"></a>許可元

初期化とスレッド

#### <a name="example"></a>例

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

指定されたイベントをフィルター解除する

#### <a name="prototype"></a>プロトタイプ

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>説明

このサービスでは、指定されたイベントをフィルター解除して、アクティブなトレース バッファーに挿入されるようにします。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター

- **event_unfilter_bits**: フィルター解除するイベントに対応するビット。 複数のイベントをフィルター解除するには、適切な定数の論理和を指定します。 この変数の有効な定数は、次のように定義されています。

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベントのフィルター解除に成功しました。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。

#### <a name="allowed-from"></a>許可元

初期化とスレッド

#### <a name="example"></a>例

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_filter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>イベントのトレースを無効にする

#### <a name="prototype"></a>プロトタイプ

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>説明

このサービスにより、ThreadX 内のイベント トレースが無効になります。 これは、アプリケーションで現在のイベント トレース バッファーをフリーズし、場合によっては実行時に外部に転送する必要がある場合に便利です。 無効にした後は、**tx_trace_enable** を呼び出して、トレースを再度開始できます。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター

[なし] :

#### <a name="return-values"></a>戻り値

- **TX_SUCCESS** (0x00) イベント トレースの無効化に成功しました。
- **TX_NOT_DONE** (0x20) イベント トレースは有効になっていません。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。

#### <a name="allowed-from"></a>許可元

初期化とスレッド

#### <a name="example"></a>例 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>ISR 開始イベントを挿入する

#### <a name="prototype"></a>プロトタイプ

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>説明

このサービスでは、ISR 開始イベントをイベント トレース バッファーに挿入します。 これは、ISR 処理の開始時にアプリケーションによって呼び出される必要があります。 指定されたパラメーターは、アプリケーションに対して特定の ISR を識別する必要があります。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター 
- **isr_id**: ISR を識別するためのアプリケーション固有の値。

#### <a name="return-values"></a>戻り値

**なし**

#### <a name="allowed-from"></a>許可元 

ISR

#### <a name="example"></a>例

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>ISR 終了イベントを挿入する

#### <a name="prototype"></a>プロトタイプ

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>説明

このサービスでは、ISR 開始イベントをイベント トレース バッファーに挿入します。 これは、ISR 処理の開始時にアプリケーションによって呼び出される必要があります。 指定されたパラメーターは、アプリケーションに対して ISR を識別する必要があります。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター 

- **isr_id**: ISR を識別するためのアプリケーション固有の値。

#### <a name="return-values"></a>戻り値

**なし**

#### <a name="allowed-from"></a>許可元

ISR

#### <a name="example"></a>例

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_buffer_full_notify、tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>トレース バッファーの完全なアプリケーション コールバックを登録する

#### <a name="prototype"></a>プロトタイプ

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>説明

このサービスでは、トレース バッファーがいっぱいになったときに ThreadX によって呼び出されるアプリケーション コールバック関数を登録します。 その後、アプリケーションでトレースを無効にしたり、場合によっては新しいトレース バッファーを設定したりできます。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター

- **full_buffer_callback**: トレース バッファーがいっぱいになったときに呼び出すアプリケーション関数。 値が NULL の場合、通知コールバックは無効になります。

#### <a name="return-values"></a>戻り値

**なし**

#### <a name="allowed-from"></a>許可元

ISR

#### <a name="example"></a>例

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_user_event_insert

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>ユーザー イベントを挿入する

#### <a name="prototype"></a>プロトタイプ

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>説明

このサービスでは、ユーザー イベントをトレース バッファーに挿入します。 ユーザー イベント ID は、定数 **TX_TRACE_USER_EVENT_START** よりも大きくする必要があります。これは 4096 に定義されています。 最大ユーザー イベントは、定数 **TX_TRACE_USER_EVENT_END** によって定義されます。これは 65535 に定義されています。 この範囲内のすべてのイベントがアプリケーションで使用できます。 情報フィールドはアプリケーション固有です。

> [!IMPORTANT]
> ThreadX ライブラリとアプリケーションは、イベント トレースを使用するために定義された **TX_ENABLE_EVENT_TRACE** を使用してビルドする必要があります。

#### <a name="input-parameters"></a>入力パラメーター

- **event_id**: アプリケーション固有のイベント ID で、**TX_TRACE_USER_EVENT_START** より大きく、**TX_TRACE_USER_EVENT_END** 以下である必要があります。
- **info_field_1**: アプリケーション固有の情報フィールド。
- **info_field_2**: アプリケーション固有の情報フィールド。
- **info_field_3**: アプリケーション固有の情報フィールド。
- **info_field_4**: アプリケーション固有の情報フィールド。

#### <a name="return-values"></a>戻り値
- **TX_SUCCESS** (0x00) ユーザー イベントの挿入に成功しました。
- **TX_NOT_DONE** (0x20) イベント トレースは有効になっていません。
- **TX_FEATURE_NOT_ENABLED** (0xFF) システムはトレースを有効にしてコンパイルされませんでした。

#### <a name="allowed-from"></a>許可元

初期化とスレッド

#### <a name="example"></a>例

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>参照

tx_trace_enable、tx_trace_event_filter、tx_trace_event_unfilter、tx_trace_disable、tx_trace_isr_enter_insert、tx_trace_isr_exit_insert、tx_trace_buffer_full_notify