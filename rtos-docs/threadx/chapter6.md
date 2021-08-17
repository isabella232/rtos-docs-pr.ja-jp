---
title: 第 6 章 - Azure RTOS ThreadX のデモンストレーション システム
description: この章では、すべての Azure RTOS ThreadX プロセッサ サポート パッケージに付属するデモンストレーション システムについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 67054d67d0a6babc50a489c4ec4b738abf3efccab10060d307106e8344b00d02
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783375"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a>第 6 章 - Azure RTOS ThreadX のデモンストレーション システム

この章では、すべての Azure RTOS ThreadX プロセッサ サポート パッケージに付属するデモンストレーション システムについて説明します。

## <a name="overview"></a>概要

各 ThreadX 製品ディストリビューションには、サポートされているすべてのマイクロプロセッサで動作するデモンストレーション システムが含まれています。

このサンプル システムは、ディストリビューション ファイル ***demo_threadx.c*** で定義されており、組み込みのマルチスレッド環境で ThreadX がどのように使用されるかを示すように設計されています。 このデモンストレーションは、初期化、8 つのスレッド、1 つのバイト プール、1 つのブロック プール、1 つのキュー、1 つのセマフォ、1 つのミューテックス、および 1 つのイベント フラグ グループで構成されます。

> [!NOTE]
> "*スレッドのスタック サイズを除いて、このデモンストレーション アプリケーションは、ThreadX でサポートされるすべてのプロセッサで同じです。* "

この章の残りの部分で参照されている行番号を含む、***demo_threadx.c*** の完全な記述。

## <a name="application-define"></a>アプリケーションの定義

***tx_application_define*** 関数は、基本的な ThreadX の初期化が完了した後に実行されます。 これは、スレッド、キュー、セマフォ、ミューテックス、イベント フラグ、メモリ プールなど、最初のシステム リソースすべてを設定する役割を担います。

デモンストレーション システムの ***tx_application_define** _ ("_行番号 60 から 164*") では、デモンストレーション オブジェクトが次の順序で作成されます。

- byte_pool_0
- thread_0
- thread_1
- thread_2
- thread_3
- thread_4
- thread_5
- thread_6
- thread_7
- queue_0
- semaphore_0
- event_flags_0
- mutex_0
- block_pool_0

このデモンストレーション システムでは、その他の ThreadX オブジェクトは作成されません。 ただし、実際のアプリケーションでは、実行時に実行中のスレッド内でシステム オブジェクトが作成される場合があります。

### <a name="initial-execution"></a>最初の実行

すべてのスレッドは、**TX_AUTO_START** オプションを使用して作成されます。 これにより、最初の実行の準備が整います。 ***tx_application_define*** が完了すると、制御がスレッド スケジューラに移動し、そこから個々のスレッドに移動します。

スレッドが実行される順序は、その優先順位と作成された順序によって決まります。 デモンストレーション システムでは、***thread_0*** の優先順位が最も高いため ("*優先順位 1 で作成*")、これが最初に実行されます。 ***thread_0*** が中断されると、***thread_5*** が実行され、その後に ***thread_3** _、_*_thread_4_*_、_*_thread_6_*_、 _*_thread_7_**、***thread_1**_ の実行が続き、最後に _*_thread_2_** が実行されます。

> [!NOTE]
> "***thread_3** と **thread_4** の優先順位は同じですが (両方とも優先順位 8 で作成)、**thread_3** が最初に実行されます。これは、**thread_4** より前に **thread_3** が作成され、準備ができたためです。同じ優先順位のスレッドは FIFO 方式で実行されます。* "

## <a name="thread-0"></a>スレッド 0

関数 ***thread_0_entry*** により、スレッドのエントリ ポイントがマークされます ("*167 から 190 行目*")。 ***Thread_0*** は、デモンストレーション システムで最初に実行されるスレッドです。 その処理は単純です。そのカウンターをインクリメントし、10 タイマー ティックの間スリープ状態になり、***thread_5*** をウェイクアップするイベント フラグを設定した後、そのシーケンスを繰り返します。

***Thread_0*** は、システムで最も優先順位の高いスレッドです。 要求されたスリープは、期限切れになると、デモンストレーションで実行中の他のスレッドを横取りします。

## <a name="thread-1"></a>スレッド 1

関数 ***thread_1_entry** _ により、スレッドのエントリ ポイントがマークされます ("_193 から 216 行目 *")。***Thread_1*** は、デモンストレーション システムで最後から 2 番目に実行されるスレッドです。その処理は、カウンターのインクリメント、***thread_2*** へのメッセージの送信 ("***queue_0**** 経由*")、そのシーケンスの繰り返しで構成されます。_*_queue_0_*_ がいっぱいになるたびに ***thread_1**_ が中断されることに注意してください ("_207 行目*")。

## <a name="thread-2"></a>スレッド 2

関数 ***thread_2_entry*** により、スレッドのエントリ ポイントがマークされます ("*219 から 243 行目*")。 ***Thread_2*** は、デモンストレーション システムで最後に実行されるスレッドです。 その処理は、カウンターのインクリメント、***thread_1*** からのメッセージの取得 (***queue_0*** 経由)、そのシーケンスの繰り返しで構成されます。 ***thread_2** _ は _*_queue_0_*_ が空になるたびに中断されることに注意してください ("_233 行目*")。

***thread_1** _ と _ *_thread_2_** は、デモンストレーション システムで最も低い優先順位 ("* 優先順位 16*") を共有していますが、これら "*スレッド 3 および 4*"

は、ほとんどの場合実行の準備ができている限られた数のスレッドでもあります。 これらは、タイムスライシングを使用して作成される限られた数のスレッドでもあります ("*87 および 93 行目*")。 各スレッドは、他のスレッドが実行される前に最大 4 タイマー ティックの間実行できます。

## <a name="threads-3-and-4"></a>スレッド 3 と 4

関数 ***thread_3_and_4_entry*** により、***thread_3** _ と _ *_thread_4_** の両方のエントリ ポイントがマークされます (246 から 280 行目)。 どちらのスレッドも優先順位は 8 です。そのため、デモンストレーション システムで 3 番目と 4 番目に実行されるスレッドになります。 各スレッドの処理は同じです。カウンターをインクリメントし、***semaphore_0*** を取得して、2 タイマー ティックの間スリープ状態になり、***semaphore_0*** を解放した後、そのシーケンスを繰り返します。 ***semaphore_0*** が使用できなくなると必ず各スレッドが中断されることに注意してください (264 行目)。

また、どちらのスレッドでもメイン処理に同じ関数が使用されています。
両方にそれぞれ独自のスタックがあり、C は本来再入可能であるため、これは問題になりません。 各スレッドでは、スレッド入力パラメーターの調査によってどちらであるかが判明します (258 行目)。このパラメーターは、スレッドの作成時に設定されます (102 および 109 行目)。

> [!NOTE]
> "*スレッドの実行中に現在のスレッド ポイントを取得し、それを制御ブロックのアドレスと比較してスレッド ID を判定することも理にかなっています。* "

## <a name="thread-5"></a>スレッド 5

関数 ***thread_5_entry*** により、スレッドのエントリ ポイントがマークされます (283 から 305 行目)。 ***Thread_5*** は、デモンストレーション システムで 2 番目に実行されるスレッドです。 その処理は、カウンターのインクリメント、***thread_0*** からのイベント フラグの取得 (***event_flags_0*** 経由)、そのシーケンスの繰り返しで構成されます。 ***event_flags_0*** のイベント フラグが使用できなくなると必ず ***thread_5*** が中断されることに注意してください (298 行目)。

## <a name="threads-6-and-7"></a>スレッド 6 と 7

関数 ***thread_6_and_7_entry*** により、***thread_6** _ と _ *_thread_7_** 両方のエントリ ポイントがマークされます (307 から 358 行目)。 どちらのスレッドも優先順位は 8 です。そのため、デモンストレーション システムで 5 番目と 6 番目に実行されるスレッドになります。 各スレッドの処理は同じです。カウンターをインクリメントし、***mutex_0*** を取得して、2 タイマー ティックの間スリープ状態になり、***mutex_0*** を解放した後、そのシーケンスを繰り返します。 ***mutex_0*** が使用できなくなると必ず各スレッドが中断されることに注意してください (325 行目)。

また、どちらのスレッドでもメイン処理に同じ関数が使用されています。 両方にそれぞれ独自のスタックがあり、C は本来再入可能であるため、これは問題になりません。
各スレッドでは、スレッド入力パラメーターの調査によってどちらであるかが判明します (319 行目)。このパラメーターは、スレッドの作成時に設定されます (126 および 133 行目)。

## <a name="observing-the-demonstration"></a>デモンストレーションの観察

デモンストレーションのスレッドは、それぞれ独自の一意のカウンターをインクリメントします。
デモの動作を確認するために、次のカウンターを調べることができます。

- thread_0_counter
- thread_1_counter
- thread_2_counter
- thread_3_counter
- thread_4_counter
- thread_5_counter
- thread_6_counter
- thread_7_counter

これらの各カウンターは、デモンストレーションの実行に応じて増加し続けます。そのうち、***thread_1_counter** _ と _ *_thread_2_counter_** は最も速い速度で増加します。

## <a name="distribution-file-demo_threadxc"></a>ディストリビューション ファイル: demo_threadx.c

このセクションでは、この章全体で参照されている行番号を含む、***demo_threadx.c*** の完全な記述を示します。

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
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

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

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
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
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
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

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
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
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
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
