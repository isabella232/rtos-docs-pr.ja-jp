---
title: 第 3 章 - モジュール マネージャーの要件
description: この記事では、ThreadX モジュール マネージャーをビルドするために必要な手順について説明します。
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6c4d0993284c8e0b8264020d721ac12bdfe8117df4480fb54ee4d5b20a1f677e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799185"
---
# <a name="chapter-3---module-manager-requirements"></a>第 3 章 - モジュール マネージャーの要件

ThreadX モジュール マネージャーは、ThreadX の RTO と共にアプリケーションの常駐部分に存在します。 これは、モジュールを起動し、ThreadX API サービスのすべてのモジュール要求をフィールディングしてディスパッチする役割を担います。

> [!NOTE]
> ThreadX モジュール **マネージャー** のソース ファイル (C とアセンブリ) を Threadx ライブラリ プロジェクト "**tx**" に追加する必要があります。

ThreadX モジュール マネージャーをビルドするには、以下の手順が必要です (それぞれの手順については、以下で詳しく説明します)。

1. モジュール情報を含めるには、**TX_THREAD** 制御ブロックを拡張する必要があります。 これを実現する最も簡単な方法は、**_tx_port.h_*ファイル内の **TX_THREAD_EXTENSION_2** の定義を、**_txm_module_port.h_** で見つかった* TX_THREAD_EXTENSION_2** に置き換えることです。 ポート固有の拡張機能については[付録](appendix.md)を参照してください。

拡張機能の例:

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   次の拡張機能は ***tx_port.h*** で定義する必要があります。

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. すべての ***txm_module_manager_\**** C とアセンブリ ファイルを ThreadX ライブラリ プロジェクト **_tx_** に追加します。
3. すべてのライブラリと実行可能なプロジェクトをリビルドします。 NetX Duo が必要な場合は、**TXM_MODULE_ENABLE_NETX_DUO** を定義して、すべてのモジュールとモジュール マネージャーの C コードをビルドする必要があります。

## <a name="module-manager-sources"></a>モジュール マネージャーのソース

ThreadX モジュール マネージャーには、ソース ファイルのセットがあります。これは、常駐する ThreadX コードにリンクされ直接配置されるように設計されています。 これらのファイルには、モジュールを起動し、以降の ThreadX API 要求をそのモジュールからフィールディングする機能があります。 モジュール マネージャーのファイルは以下のとおりです。

| **[ファイル名]** |  **Contents** |
|-------------- | ------------- |
| ***txm_module.h*** | モジュール情報を定義するインクルード ファイル (モジュールのソース コードにも含まれます)。 |
| ***txm_module_manager_dispatch.h*** | ディスパッチ ヘルパー関数を定義するインクルード ファイル。|
| ***txm_module_manager_util.h*** | 内部的なユーティリティ ヘルパー マクロと関数を定義するインクルード ファイル。 |
| ***txm_module_port.h*** | ポート固有のモジュール情報を定義するインクルード ファイル (モジュールのソース コードにも含まれます)。 |
| ***tx_initialize_low_level.\[s,S,68\]** _ | 既存の ThreadX ライブラリ ファイルを置き換えます。 モジュール マネージャーとメモリ例外のために更新されたベクトル テーブルと、追加のベクトル ハンドラー。 このファイルは、Cortex-A7/ARM、Cortex-M7/ARM、Cortex-R4/ARM、Cortex-R4/IAR、MCF544xx/GHS、RX63/IAR、RX65N/IAR にのみ存在します。*|
| ***tx_thread_context_restore.s** _ | 既存の ThreadX ライブラリ ファイルを置き換えます。 割り込み処理後にスレッド コンテキストを復元します。 このファイルは Cortex-A7/ARM、Cortex-R4/ARM、Cortex-R4/IAR にのみ存在します。*|
| ***tx_thread_schedule.\[s,S,68\]*** | 既存の ThreadX ライブラリ ファイルを置き換えます。 拡張されたスケジューラ コード。この場合は、メモリ管理レジスタを更新するために使用します。 |
| ***tx_thread_stack_build.s** _ | 既存の ThreadX ライブラリ ファイルを置き換えます。 スレッドのスタック フレームをビルドします。 このファイルは Cortex-A7/ARM、Cortex-R4/ARM、Cortex-R4/IAR にのみ存在します。*|
| ***txm_module_manager_thread_stack_build.\[s,S,68\]*** | すべてのモジュール初期スタックをビルドし、位置に依存しないデータ アクセスのセットアップをインクルードします。 |
| ***txm_module_manager_user_mode_entry.\[s,S\]** _ | モジュールがカーネル モードに入ることを許可します。 このファイルは Cortex-A7/ARM、Cortex-R4/ARM、Cortex-R4/IAR にのみ存在します。*|
| ***txm_module_manager_alignment_adjust.c*** | ポート固有のアラインメント要件を処理します。|
| ***txm_module_manager_application_request.c*** | 常駐コードに対するアプリケーション固有の要求を処理します。 |
| ***txm_module_manager_callback_request.c*** | コールバック要求をモジュールに送信します。 |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | ThreadX からのイベント フラグ設定通知呼び出しを処理します。 |
| ***txm_module_manager_external_memory_enable.c*** | モジュールがアクセスできる共有メモリ空間のエントリを、メモリ管理テーブルに作成します。 |
| ***txm_module_manager_file_load.c*** | バイナリ モジュール ファイルを割り当ててモジュールのメモリ領域に読み込み、実行できるように準備します。 |
| ***txm_module_manager_in_place_load.c*** | モジュール データ領域を割り当て、指定されたコード アドレスからのモジュール実行を準備します。 |
| ***txm_module_manager_initialize.c*** | モジュールの読み込みと実行に使用できるモジュール メモリ領域を指定するなど、モジュール マネージャーを初期化します。 |
| ***txm_module_manager_initialize_mmu.c** _ | MMU を初期化します。 ユーザーは、それぞれのメモリ マップに従ってこのファイルを編集できます。 このファイルは Cortex-A7/ARM にのみ存在します* |
| ***txm_module_manager_mm_initialize.c** _ | MPU/MMU を初期化します。 ユーザーは、それぞれのメモリ マップに従ってこのファイルを編集できます。 このファイルは Cortex-A7/ARM にのみ存在します* |
| ***txm_module_manager_kernel_dispatch.c*** | 要求 ID に基づいて、モジュールの API 要求を処理します。 |
| ***txm_module_manager_maximum_module_priority_set.c*** | モジュールで許可されるスレッドの最大優先度を設定します。 |
| ***txm_module_manager_memory_fault_handler.c*** | 実行中のモジュールで検出されたメモリ エラーを処理します。 |
| ***txm_module_manager_memory_fault_notify.c*** | メモリ エラーが発生するたびに、アプリケーション通知コールバックを登録します。 |
| ***txm_module_manager_memory_load.c*** | モジュールのコードとデータを割り当てて読み込み、実行するモジュールを準備します。 |
| ***txm_module_manager_mm_register_setup.c*** | コードとデータが読み込まれる場所に基づいて、モジュールの MPU/MMU レジスタを設定します。 |
| ***txm_module_manager_object_allocate.c*** | モジュール オブジェクトのメモリを割り当てます。 |
| ***txm_module_manager_object_deallocate.c*** | モジュール オブジェクトのメモリの割り当てを解除します。 |
| ***txm_module_manager_object_pointer_get.c*** | 指定されたオブジェクトの種類と名前を検索し、見つかった場合はオブジェクト ポインターを返します。 |
| ***txm_module_manager_object_pointer_get_extended.c*** | 指定されたオブジェクトの種類と名前を検索し、見つかった場合はオブジェクト ポインターを返します。 安全のために指定された名前の長さ。 |
| ***txm_module_manager_object_pool_create.c***  | モジュール アプリケーションが割り当て元にできる、モジュールのデータ領域の外側に、オブジェクトのプールを作成します。 |
| ***txm_module_manager_properties_get.c*** | 指定されたモジュールのプロパティを取得します。 |
| ***txm_module_manager_queue_notify_trampoline.c*** | ThreadX からのキュー通知呼び出しを処理します。 |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | ThreadX からのセマフォ put 通知呼び出しを処理します。|
| ***txm_module_manager_start.c*** | モジュールの実行を開始します。 |
| ***txm_module_manager_stop.c*** | モジュールの実行を停止します。 |
| ***txm_module_manager_thread_create.c*** | すべてのモジュール スレッドを作成します。 |
| ***txm_module_manager_thread_notify_trampoline.c*** | ThreadX からのスレッド開始/終了通知呼び出しを処理します。 |
| ***txm_module_manager_thread_reset.c*** | モジュール スレッドをリセットします。 |
| ***txm_module_manager_timer_notify_trampoline.c*** | ThreadX からのタイマー有効期限を処理します。 |
| ***txm_module_manager_unload.c*** | モジュールのメモリ領域からモジュールをアンロードします。 |
| ***txm_module_manager_util.c*** | マネージャーの内部ヘルパー関数。 |

## <a name="module-manager-initialization"></a>モジュール マネージャーの初期化

アプリケーションの常駐部分は、モジュール マネージャー初期化関数 ***txm_module_manager_initialize*** を呼び出す役割を担います。 この関数は、モジュール メモリの割り当てに使用されるメモリ領域を設定するなど、モジュールの読み込みとアンロードのための内部構造を設定します。

## <a name="module-manager-loading"></a>モジュール マネージャーの読み込み

モジュール マネージャーは、バイナリ モジュール ファイルから、または常駐コード領域に既に存在するモジュール コード セクションから、モジュール メモリにモジュールを動的に読み込むことができます。 また、モジュール マネージャーはコードを適切に実行できます。つまり、モジュール データのみがモジュール メモリに割り当てられ、コードの実行が適切に実行されます。 次のモジュール マネージャー読み込み API 関数を使用できます。

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

メモリ保護されたバージョンのモジュール マネージャーでは、モジュールに適切なアラインメントが読み込まれていることと、メモリ管理レジスタがモジュールごとに適切に設定されていることも確認されます。 モジュール プリアンブル オプションを使用してメモリ保護を有効にすると、モジュール メモリ アクセスはモジュール コードとデータ領域に制限されます。

## <a name="module-manager-starting"></a>Module Manager の開始

モジュール マネージャーは、***txm_module_manager_start*** API 関数を使用して、以前に読み込まれたモジュールの実行を開始します。 モジュールの実行を開始するために、この関数は、モジュール プリアンブルで指定された開始位置にモジュールに入るスレッドを作成します。 このスレッドの優先度とスタック サイズは、モジュール プリアンブルでも指定されています。

## <a name="module-manager-stopping"></a>モジュール マネージャーの停止

モジュール マネージャーは、***txm_module_manager_stop*** 関数を使用して、以前に読み込まれ実行中のモジュールの実行を終了します。 この API 関数は、最初に開始されているスレッドをまず終了して削除します。 モジュール プリアンブルに停止スレッドが指定されている場合、このスレッドが作成されて実行されます。 モジュール マネージャーは、停止スレッドが完了するまで一定期間待機します。 完了すると、モジュールによって作成されたすべてのシステム リソースが削除され、モジュールは休止状態になります。この状態から、再起動またはアンロードできます。

## <a name="module-manager-unloading"></a>モジュール マネージャーのアンロード

モジュール マネージャーは、以前に読み込まれたが実行中ではないモジュールを、***txm_module_manager_unload*** 関数を介してアンロードします。 この API は、モジュールに関連付けられているすべてのメモリをリリースし、これ以降に別のモジュールで使用できるように解放します。

## <a name="module-manager-requests"></a>モジュール マネージャーの要求

モジュールによって行われるモジュール マネージャーへの要求は、***txm_module.h*** に含まれるマクロを使用して実行されます。このマクロは ThreadX 呼び出しをマップして、モジュール マネージャーによってモジュールに指定された関数ポインターを介してモジュール マネージャー ディスパッチ関数を呼び出します。

***txm_module_application_request*** を呼び出すモジュールを介して実行されるアプリケーション固有の追加サービスは、ThreadX API のために使用されるのと同じマクロの仕組みによって処理されます。 既定では、モジュール マネージャーのこの処理関数は空であり、アプリケーション固有の要求を処理するために必要なコードがアプリケーションで追加されるように設計されています。

モジュール マネージャーによって要求が実装されない場合は、モジュール マネージャーによって **TX_NOT_AVAILABLE** エラー状態の値が返されます。 このエラー コードは、モジュールのアクセス権の範囲外にある操作をモジュールが要求した場合にも返されます。 たとえば、モジュールは、モジュールのコード領域の外部にあるタイマー制御ブロックまたはコールバック アドレスを使用してタイマーを作成することはできません。

## <a name="module-manager-example"></a>モジュール マネージャーの例

次に示すのは、前に第 2 章で定義したサンプル モジュールを起動するモジュール マネージャー コードの例です。 このモジュールは、たとえばデバッガーによって、ROM アドレス 0x00800000 に既に読み込まれていると仮定しています。

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a>モジュール マネージャーのビルド

***txm_module_manager_\**** ソース ファイルを ThreadX ライブラリに追加する必要があります。

ThreadX モジュール マネージャー アプリケーションは、標準の ThreadX アプリケーションと実質的に同じで、これは ThreadX ライブラリ ***tx.a*** を使用してリンクされた 1 つ以上のアプリケーション ファイルです。 モジュール マネージャー アプリケーションのビルドは、使用されているツール チェーンに依存します。 ポート固有の例については[付録](appendix.md)を参照してください。
