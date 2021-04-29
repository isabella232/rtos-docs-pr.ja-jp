---
title: 第 11 章 - イベント トレース バッファーの形式
description: ThreadX には、すべての Azure RTOS ThreadX サービス、スレッド状態の変更、およびユーザー定義イベントに対する組み込みのイベント トレース サポートが用意されています。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812392"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>第 11 章 - イベント トレース バッファーの形式

Azure RTOS ThreadX には、すべての ThreadX サービス、スレッド状態の変更、およびユーザー定義イベントに対する組み込みのイベント トレース サポートが用意されています。 イベント トレースを使用するには、**TX_ENABLE_EVENT_TRACE** が定義された ThreadX、NetX、および FileX ライブラリをビルドし、**_tx_trace_enable_** 関数を呼び出してトレースを有効にします。 この章では、そのプロセスについて説明します。

## <a name="event-trace-format"></a>イベント トレース形式

ThreadX イベント トレース バッファーの形式は、コントロール ヘッダー、オブジェクト レジストリ、およびトレース エントリの 3 つのセクションに分かれています。 以下に示すのは、ThreadX イベント トレース バッファーの一般的なレイアウトです。

**コントロール ヘッダー**

**オブジェクト レジストリ エントリ 0**

**…**

**オブジェクト レジストリ エントリ "n"**

**イベント トレース エントリ 0**

**…**

**イベント トレース エントリ "n"**

### <a name="event-trace-control-header"></a>イベント トレース コントロール ヘッダー

コントロール ヘッダーでは、イベント トレース バッファーの厳密なレイアウトが定義されます。 これには、登録できる ThreadX オブジェクトの数や、記録できるイベントの数が含まれます。 さらに、コントロール ヘッダーでは、トレース バッファーの各要素が存在する場所も定義されます。 次のデータ構造は、コントロール ヘッダーを定義したものです。

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a>コントロール ヘッダー ID

コントロール ヘッダー ID は、32 ビットの 16 進数値 (0x54585442) で構成されます。これは、ASCII 文字 ***TXTB*** に対応します。 この値は、32 ビットの符号なし変数として書き込まれるため、イベント トレース バッファーのエンディアンを検出するために使用することもできます。 たとえば、メモリの最初の 4 つのバイトの値が 0x54、0x58、0x54、0x42 の場合、イベント トレース バッファーはビッグ エンディアン形式で書き込まれています。 それ以外の場合、イベント トレース バッファーはリトル エンディアン形式で書き込まれています。

### <a name="timer-valid-mask"></a>タイマー有効マスク

タイマー有効マスクでは、実際のイベント トレース エントリ内での、有効なタイムスタンプのビット数が定義されます。 たとえば、タイムスタンプ ソースに 16 ビットが含まれている場合、このフィールドの値は 0xFFFF とする必要があります。 32 ビットのタイムスタン プソースの場合、値は 0xFFFFFFFF になります。 この値は、_*_tx_port h_** 内の ***TX_TRACE_TIME_MASK** _ 定数によって定義されます。

### <a name="trace-base-address"></a>トレース ベース アドレス

トレース バッファー ベース アドレスは、***tx_trace_enable*** 呼び出しでのトレース バッファーの開始点として、アプリケーションによって指定されたアドレスです。 このアドレスは、バッファー内のさまざまな要素に対するバッファー相対オフセットを分析ツールで取得する目的専用に保持されます。 たとえば、トレース バッファー内の現在のイベントのバッファー相対オフセットは、現在のイベント アドレスからベース アドレスを単純に減算することで計算されます。

### <a name="registry-start-and-end-pointers"></a>レジストリの開始ポインターと終了ポインター

レジストリ開始ポインターは、最初のオブジェクト レジストリ エントリのアドレスを指し、レジストリ終了ポインターは、最後のレジスタ エントリの直後のアドレスを指します。 これらの値は *tx_trace_enable* の処理中に設定され、トレース中は変更されません。

### <a name="registry-name-size"></a>レジストリ名サイズ

レジストリ名サイズでは、レジストリ エントリ内の各オブジェクト名の最大サイズがバイト単位で定義されます。これは、シンボル ***TX_TRACE_OBJECT_REGISTRY_NAME** _ によって定義されます。 既定値は 32 であり、_*_tx_trace.h_*_ で定義されています。 オブジェクト名は、オブジェクトの作成時にアプリケーションによって指定された名前に対応します。 たとえば、スレッドのオブジェクト レジストリ名は、_*_tx_thread_create_** の呼び出しに対してアプリケーションによって指定された名前です。

### <a name="buffer-start-and-end-pointers"></a>バッファーの開始ポインターと終了ポインター

イベント トレース バッファーの開始ポインターは、最初のトレース エントリのアドレスを指し、レジストリ終了ポインターは、最後のトレース エントリの直後のアドレスを指します。 これらの値は ***tx_trace_enable*** の処理中に設定され、トレース中は変更されません。

### <a name="current-buffer-pointer"></a>現在のバッファー ポインター

イベント トレース バッファーの現在のポインターは、最も古いトレース エントリのアドレスを指します。 トレース エントリは循環リストで保持されるため、現在のバッファー ポインターは次に書き込まれるトレース エントリも表します。 |

## <a name="event-trace-object-registry"></a>イベント トレース オブジェクト レジストリ

イベント トレース オブジェクト レジストリには、アプリケーションによって作成されたオブジェクトに対応する、***n** _ 個のオブジェクト レジストリ エントリが格納されます。 オブジェクト レジストリの主な目的は、外部分析ツールで実際のオブジェクト名をトレース バッファー エントリのオブジェクト アドレスと関連付けできるようにすることです。 レジストリ エントリの数は、_ *_tx_trace_enable_** 呼び出しでアプリケーションによって指定されます。

各オブジェクト レジスタ エントリには、アプリケーションによって以前に作成された特定の ThreadX オブジェクトに関する情報が格納されます。 次のデータ構造は、各オブジェクトのレジストリ エントリを定義したものです。

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a>オブジェクト使用可能フラグ

オブジェクト レジストリ エントリが使用可能な場合は、オブジェクト使用可能フラグが 1 に設定されます。 それ以外の場合 (値が 1 ではない場合)、オブジェクト レジストリ エントリは使用できません。 なお、使用可能な場合でも、エントリに有効な情報が含まれている可能性はあるという点に注意してください。

### <a name="object-entry-type"></a>オブジェクト エントリの種類

オブジェクト エントリの種類では、そのエントリ内のオブジェクトの種類を識別します。 次に示すのは、有効なオブジェクトの種類の一覧です。

| **Value** | **オブジェクトの種類** |
|---------- | --------------- |
| 0         | 無効       |
| 1         | スレッド          |
| 2         | Timer |
| 3         | キュー |
| 4         | Semaphore |
| 5         | Mutex |
| 6         | イベント フラグ グループ |
| 7         | ブロック プール |
| 8         | バイト プール |
| 9         | メディア |
| 10        | ファイル |
| 11        | IP |
| 12        | パケット プール |
| 13        | TCP ソケット |
| 14        | UDP ソケット |
| 15-20     | 予約済み |  
| 21        | USB ホスト スタック デバイス |
| 22        | USB ホスト スタック インターフェイス |
| 23        | USB ホスト エンドポイント |
| 24        | USB ホスト クラス |
| 25        | USB デバイス |
| 26        | USB デバイス インターフェイス |
| 27        | USB デバイス エンドポイント |
| 28        | USB デバイス クラス |

### <a name="object-pointer"></a>オブジェクト ポインター

オブジェクト ポインターでは、ThreadX API を使用してオブジェクトにアクセスするために使用されるオブジェクト アドレスを指定します。

### <a name="object-reserved-fields"></a>オブジェクト予約済みフィールド

スレッド以外のすべてのオブジェクトについては、これらの予約済みフィールドは 0 にする必要があります。 スレッドの場合は、レジストリに入力された時点でのスレッドの優先度が、この 2 つの予約済みフィールドに配置されます。

### <a name="object-parameters"></a>オブジェクト パラメーター

オブジェクト パラメーターには、オブジェクトに関する補足情報が格納されます。 次に示すのは、各 ThreadX オブジェクトの補足情報に関する説明です。

| **オブジェクトの種類**        | **パラメーター 1**  | **パラメーター 2** |
|----------------------- | ---------------- | --------------- |
| スレッド                 | スタックの開始      | スタック サイズ |
| Timer                  | 初期ティック | ティックの再スケジュール |
| キュー                  | キュー サイズ | メッセージ サイズ |
| Semaphore              | 初期インスタンス | - |
| Mutex                  | 継承フラグ | - |
| イベント フラグ グループ      | - | - |
| ブロック プール             | 合計ブロック数 | ブロック サイズ |
| バイト プール              | Total Bytes | - |
| メディア                  | FAT キャッシュ サイズ | セクター キャッシュ サイズ |
| ファイル                   | - | - |
| IP                     | スタックの開始 | スタック サイズ |
| パケット プール            | Packet Size | パケット数 |
| TCP ソケット             | IP アドレス | ウィンドウ サイズ |
| UDP ソケット             | IP アドレス | RX キューの最大数 |

### <a name="object-name"></a>オブジェクト名

オブジェクト名には、ThreadX オブジェクトの名前が格納されます。 この名前は、オブジェクトの作成時に ThreadX に対して指定された名前です。 既定では、オブジェクト名の最大文字数は 32 文字です。 実際の名前が 32 文字を超える場合は、名前が切り捨てられます。

## <a name="event-trace-entries"></a>イベント トレース エントリ

イベント トレース エントリは、イベント トレース バッファーの下部にあります。 エントリは循環リストに保持され、現在のエントリ ポインターは最も古いエントリを指します。 リスト内のエントリの数は、***tx_trace_enable*** の呼び出しによって計算されます。

各オブジェクト レジスタ エントリには、特定の ThreadX トレース イベントに関する情報が格納されます。 次のデータ構造は、各トレース イベント エントリを定義したものです。

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a>スレッド ポインター

スレッド ポインターには、このイベントの発生時に実行されているスレッドのアドレスが格納されます。 初期化中にイベントが発生した場合 (スレッドが実行されていない場合)、このポインターの値は 0xF0F0F0F0 になります。 割り込みサービス ルーチン (ISR) の実行中にイベントが発生した場合、このポインターの値は 0xFFFFFFFF になります。 エントリがまだ使用されていない場合、このポインターの値は 0 になります。

### <a name="thread-priority"></a>スレッド優先度

スレッド優先度フィールドには、そのイベントの発生時に実行されていたスレッドの優先度とプリエンプションしきい値が格納されます。 割り込みコンテキストが存在する場合 (スレッド ポインターが 0xFFFFFFFF の場合)、このフィールドの値は優先度ではなく、イベント時点での ***_tx_thread_current_ptr*** の値になります。 その他の場合、このフィールドの値は 0 になります。

### <a name="event-id"></a>イベント ID

イベント ID では、発生したイベントが指定されます。 有効な ThreadX トレース イベント ID の範囲は、1 - 1024 です。 1025 以降で始まる値は、ユーザー固有のイベント用に予約されています。 ThreadX イベント ID の完全な定義については、***tx_trace.h*** ファイルを参照してください。</td>

### <a name="information-fields-1-4"></a>情報フィールド (1-4)

情報フィールドには、特定のイベントに関する追加情報が格納されます。 定義されている各 ThreadX イベント ID の情報フィールドの完全な説明については、***tx_trace.h*** ファイルを参照してください。