---
title: 第 2 章 - モジュールの要件
description: この記事は、ThreadX モジュールをビルドするための要件の説明です。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b814e7c2b510093b809b70b02d9a11ed39996d114f2306e0993893799453cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791960"
---
# <a name="chapter-2---module-requirements"></a>第 2 章 - モジュールの要件

ThreadX モジュールには、モジュールの基本的な特性を定義するプリアンブルが含まれています。 プリアンブルに続くのは、モジュールの命令領域です。 モジュールは、インプレースで実行される場合もあれば、実行前にモジュール マネージャーによってモジュール メモリ領域にロードされる場合もあります。 唯一の要件は、プリアンブルが常にモジュールの最初のアドレスに位置していることです。 図 2 は、基本的なモジュール レイアウトを示しています。

| モジュール レイアウト |
|:---:|
| \[モジュール プリアンブル\]         |
| \[モジュール命令領域\] |
| \[モジュール RAM 領域\]         |

**図 2** - モジュール レイアウト

> [!NOTE]
> モジュールは、適切な位置独立コードと、データ コンパイラ/リンカー オプションを使用してビルドする必要があります。 これにより、どのメモリ領域でもモジュールを実行できるようになります。

モジュール スレッドが作成されると、スレッドがメモリ保護カーネルにあるときに使用する 2 番目のスタック空間が割り当てられます。 スレッドのカーネル スタック空間のサイズは、**_txm_module_port.h_ *_ で **TXM_MODULE_KERNEL_STACK_SIZE** を使用してユーザーが構成できます。_* _tx_thread_create_** の呼び出し時にユーザーが指定したスタックのみがモジュールで使用されるため、これによって、モジュール スレッドの作成時に使用するスタックのサイズを削減できます。

> [!NOTE]
> モジュール スレッド スタックの最上位にはスレッド エントリ情報構造体 (**TXM_MODULE_THREAD_ENTRY_INFO**) が含まれているため、利用可能なスタック サイズはこの構造体のサイズの分だけ減少します。 モジュールでスレッドを作成するときは、少なくとも、この構造体のサイズの分だけスタック サイズを増やします。

ThreadX モジュールを作成してビルドするには、以下の手順が必要です (それぞれの手順については、以下で詳しく説明します)。

1. モジュール内のすべての C ファイルでは、**_txm_module.h_** をインクルードする前に **TXM_MODULE** を #define する必要があります。 これは、コンパイル中のソース ファイルで、またはプロジェクト設定の一部として実行できます。 これにより、ThreadX API の呼び出しが、モジュール固有バージョンの API に再マップされます。この API により、常駐モジュール マネージャーでディスパッチ関数が呼び出され、実際の API 関数の呼び出しが実行されます。
2. 各モジュールの最初の命令領域アドレスに、モジュールの特性と必要なリソースを定義するプリアンブルが存在している必要があります。
3. 各モジュールでは、モジュール命令領域の先頭でプリアンブルをリンクする必要があります。
4. 各モジュールでは、ThreadX との対話に使用されるモジュール固有の関数を含むモジュール ライブラリ (***txm.a***) に対してリンクする必要があります。

## <a name="module-sources"></a>モジュール ソース

ThreadX モジュールが独自に備える一連のソース ファイルは、モジュールのソース コードと直接リンクして配置されるように設計されています。 これらのファイルは、個別のモジュールと常駐モジュール マネージャーの間のブリッジを提供します。 モジュール ファイルには以下のものがあります。

| ファイル名 | 内容 |
|---|---|
| **txm_module.h** | モジュール情報を定義するインクルード ファイル。 |
| **txm_module_port.h** | ポート固有のモジュール情報を定義するインクルード ファイル。 |
| **txm_module_user.h** | ユーザーがカスタマイズできる値を定義します。 |
| **txm_module_initialize.s [1][3]** | 組み込み関数をスタートアップ モジュールに呼び出します。 |
| **txm_module_preamble.\{s/S/68\}** | モジュール プリアンブル アセンブリ ファイル。 このファイルは、モジュール固有のさまざまな属性を定義し、モジュール アプリケーション コードとリンクされます。 |
| **txm_module_application_request.c [1]** | モジュール アプリケーション要求関数は、アプリケーション固有の要求を常駐コードに送信します。 |
| **txm_module_callback_request_thread_entry.c&nbsp;[1]** | タイマーや通知コールバックなど、モジュールによって要求されたコールバックの処理を担当するモジュール コールバック スレッド。 |
| **txm_*.c [1][2]** | 標準の ThreadX API サービスであり、これらはカーネル ディスパッチャーを呼び出します。
| **txm_module_object_allocate.c [1]** | マネージャーのメモリ プールに位置するモジュール オブジェクトにメモリを割り当てるためのモジュール関数。 |
| **txm_module_object_deallocate.c [1]** | マネージャーのメモリ プールに位置するモジュール オブジェクトへのメモリ割り当てを解除するためのモジュール関数。 |
| **txm_module_object_pointer_get.c [1]** | システム オブジェクトへのポインターを取得するためのモジュール関数。 |
| **txm_module_object_pointer_get_extended.c [1]** | システム オブジェクトへのポインターを取得するための、名前の長さに関して安全なモジュール関数。 |
| **txm_module_thread_shell_entry.c [1]** | モジュール スレッドのエントリ関数。 |
| **txm_module_thread_system_suspend.c [1]** | スレッドを中断するためのモジュール関数。 |

**[1]** Located in library **_txm.a_**.

**[2]** これらのファイルは ThreadX API ファイルと同じ名前ですが、プレフィックスは **tx_** ではなく **txm_** です。

**[3]** **txm_module_initialize.s** ファイルは、ARM ツールを使用するポート専用です。

## <a name="module-preamble"></a>モジュール プリアンブル

モジュール プリアンブルは、モジュールの特性とリソースを定義します。 スレッドに関連付けられる初期スレッド エントリ関数および初期メモリ領域などの情報は、プリアンブルで定義されます。 ポート固有のプリアンブルの例は[付録](appendix.md)にあります。 図 3 は、汎用ターゲット用の ThreadX モジュール プリアンブルの例を示しています (* で始まる行は、通常であればアプリケーションによって変更される値です)。

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

**図 3**

ほとんどの場合、開発者が行う必要があるのは、モジュールの開始スレッド (オフセット 0x1C)、モジュール ID (オフセット 0x10)、開始/停止スレッド優先度 (オフセット 0x24)、開始/停止スレッド スタック サイズ (オフセット 0x28) を定義することだけです。 上記のデモンストレーションの設定では、モジュールの開始スレッドは ***demo_module_start** _、モジュール ID は _*_0x12345678_*_、開始スレッドの優先度は _*_1_*_、スタック サイズは _ *_2048_** バイトです。

一部のアプリケーションでは、必要に応じて停止スレッドを定義する場合があります。これは、モジュール マネージャーがモジュールを停止するときに実行されます。 さらに、一部のアプリケーションでは、次のように定義されたモジュール プロパティ フィールドを利用する場合があります。

## <a name="module-properties-bit-map"></a>モジュール プロパティのビットマップ

次の表は、プロパティのビットマップの例を示しています。 ポート固有のプロパティ ビットマップは[付録](appendix.md)にあります。

| ビット | 値 | 意味 |
|---|---|---|
| 0 | 0<br />1 | 特権モード実行<br />ユーザー モード実行 |
| 1 | 0<br />1 | MPU 保護なし<br />MPU 保護 (ユーザー モードが選択されている必要があります) |
| 2 | 0<br />1 | 共有/外部メモリ アクセスを無効にする<br />共有/外部メモリ アクセスを有効にする |
| [23-3] | 0 | 予約されています。
| [31-24] | <br />0x01<br />0x02<br />0x03 | **コンパイラ ID**<br />IAR<br />ARM<br />GNU |


## <a name="module-linker-control-file"></a>モジュール リンカー制御ファイル

モジュールをビルドするとき、モジュール プリアンブルは、他のどのコード セクションよりも前に配置する必要があります。 モジュールは、位置独立のコードおよびデータ セクションを使用してビルドする必要があります。 ポート固有のリンカー ファイルの例は[付録](appendix.md)にあります。

## <a name="module-threadx-library"></a>モジュールの ThreadX ライブラリ

各モジュールは、特別な、モジュール中心の ThreadX ライブラリに対してリンクする必要があります。 このライブラリは、常駐コードで ThreadX サービスへのアクセスを提供します。 ほとんどのアクセスは ***txm_\*.c*** ファイルを介して行われます。 次に示すのは、( _*_ \_txm_thread_relinquish.c\**** 内の) ThreadX API 関数 **_tx_thread_relinquish_* _ に対するモジュール アクセス呼び出しの例です。

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

この例では、モジュール マネージャーによって提供された関数ポインターを使用して、***tx_thread_relinquish*** サービスに関連付けられた ID を持つ、モジュール マネージャーのディスパッチ関数を呼び出します。 このサービスはパラメーターを取りません。

## <a name="module-example"></a>モジュールの例

次に示すのは、モジュールの形式である標準 ThreadX デモンストレーションの例です。 標準 ThreadX デモンストレーションとモジュール デモンストレーションの主な違いは次のとおりです。

1. ***tx_api.h** _ を _ *_txm_module.h_** で置き換える
2. **_txm_module.h_** の前に **#define TXM_MODULE** を追加する
3. ***main** _ と _ *tx_application_define** を **_demo_module_start_** で置き換える
4. オブジェクト自体ではなく ThreadX オブジェクトへの *ポインター* を宣言する

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a>モジュールのビルド

モジュールのビルドは、使用しているツール チェーンに依存します。 ポート固有の例については[付録](appendix.md)を参照してください。 すべてのポートに共通のアクティビティには、次のものがあります。

- モジュール ライブラリのビルド
- モジュール アプリケーションのビルド

各モジュールは、(特にそのモジュールのために設定された) **txm_module_preamble** と、モジュール ライブラリ (例: **_txm.a_**) を備えている必要があります。
