---
title: 第 6 章 - Azure RTOS ThreadX トレース イベント
description: この章では、Azure RTOS ThreadX イベントについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 9fefc43002d4e0d6df817ad56d79b3e41a3d649504be50f5a39f67c1896b2e9a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116800339"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>第 6 章 - Azure RTOS ThreadX トレース イベント

この章では、Azure RTOS ThreadX イベントについて説明します。 

## <a name="list-of-events-and-icons"></a>イベントとアイコンの一覧

次に、TraceX によって表示される ThreadX イベントの一覧を示します。

| **アイコン**                         | **意味** |
| -------------------------------- | ------------------------------------- |
| ![内部スレッド再開アイコン](./media/user-guide/tx-events/image1.png)    | 内部スレッド再開  |
| ![内部スレッド中断アイコン](./media/user-guide/tx-events/image2.png)    | 内部スレッド中断 |
| ![割り込みサービス ルーチン開始アイコン](./media/user-guide/tx-events/image3.png)    | 割り込みサービス ルーチン (ISR) 開始 |
| ![割り込みサービス ルーチン終了アイコン](./media/user-guide/tx-events/image4.png)    | 割り込みサービス ルーチン (ISR) 終了  |
| ![内部タイム スライス アイコン](./media/user-guide/tx-events/image5.png)    | 内部タイム スライス |
| ![実行中アイコン](./media/user-guide/tx-events/image6.png)    | 実行中 |
| ![ブロック プール割り当てアイコン](./media/user-guide/tx-events/image7.png)    | **ブロック プール割り当て** (*tx_block_allocate*)  |
| ![ブロック プール作成アイコン](./media/user-guide/tx-events/image8.png)    | **ブロック プール作成** (*tx_block_pool_create*) |
| ![ブロック プール削除アイコン](./media/user-guide/tx-events/image9.png)    | **ブロック プール削除** (*tx_block_pool_delete*) |
| ![ブロック プール情報取得アイコン](./media/user-guide/tx-events/image10.png)    | **ブロック プール情報取得** (*tx_block_pool_info_get*) |
| ![ブロック プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image11.png)    | **ブロック プール パフォーマンス情報取得** (*tx_block_pool_performance_info_get*) |
| ![ブロック プール システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image12.png)    | **ブロック プール システム パフォーマンス情報取得** (*tx_block_pool_performance_system_info_get*) |
| ![ブロック プール優先度付けアイコン](./media/user-guide/tx-events/image13.png)    | **ブロック プール優先度付け** (*tx_block_pool_prioritize*) |
| ![プールへのブロック解放アイコン](./media/user-guide/tx-events/image14.png)    | **プールへのブロック解放** (*tx_block_release*) |
| ![バイト プール メモリ割り当てアイコン](./media/user-guide/tx-events/image15.png)    | **バイト プール メモリ割り当て** (*tx_byte_allocate*) |
| ![バイト プール作成アイコン](./media/user-guide/tx-events/image16.png)    | **バイト プール作成** (*tx_byte_pool_create*) |
| ![バイト プール削除アイコン](./media/user-guide/tx-events/image17.png)    | **バイト プール削除** (*tx_byte_pool_delete*) |
| ![バイト プール情報取得アイコン](./media/user-guide/tx-events/image18.png)    | **バイト プール情報取得** (*tx_byte_pool_info_get*) |
| ![バイト プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image19.png)    | **バイト プール パフォーマンス情報取得** (*tx_byte_pool_performance_info_get*) |
| ![バイト プール システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image20.png)    | **バイト プール システム パフォーマンス情報取得** (*tx_byte_pool_performance_system_info_get*) |
| ![*バイト プール優先度付けアイコン](./media/user-guide/tx-events/image21.png)    | **バイト プール優先度付け** (*tx_byte_pool_prioritize*) |
| ![プールへのバイト メモリ解放アイコン](./media/user-guide/tx-events/image22.png)    | **プールへのバイト メモリ解放** (*tx_byte_release*) |
| ![イベント フラグ作成アイコン](./media/user-guide/tx-events/image23.png)    | **イベント フラグ作成** (*tx_event_flags_create*) |
| ![イベント フラグ削除アイコン](./media/user-guide/tx-events/image24.png)    | **イベント フラグ削除** (*tx_event_flags_delete*) |
| ![イベント フラグ取得アイコン](./media/user-guide/tx-events/image25.png)    | **イベント フラグ取得** (*tx_event_flags_get*) |
| ![イベント フラグ情報取得アイコン](./media/user-guide/tx-events/image26.png)    | **イベント フラグ情報取得** (*tx_event_flags_info_get*) |
| ![イベント フラグ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image27.png)    | **イベント フラグ パフォーマンス情報取得** (*tx_event_flags_performance_info_get*) |
| ![イベント フラグ システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image28.png)    | **イベント フラグ システム パフォーマンス情報取得** (*tx_event_flags_performance_system_info_get*) |
| ![イベント フラグ設定アイコン](./media/user-guide/tx-events/image29.png)    | **イベント フラグ設定** (*tx_event_flags_set*) |
| ![イベント フラグ設定通知アイコン](./media/user-guide/tx-events/image30.png)    | **イベント フラグ設定通知** (*tx_event_flags_set_notify*) |
| ![割り込み有効化/無効化アイコン](./media/user-guide/tx-events/image31.png)    | **割り込み有効化/無効化** (*tx_interrupt_control*) |
| ![ミューテックス作成アイコン](./media/user-guide/tx-events/image32.png)    | **ミューテックス作成** (*tx_mutex_create*) |
| ![ミューテックス削除アイコン](./media/user-guide/tx-events/image33.png)    | **ミューテックス削除** (*tx_mutex_delete*) |
| ![ミューテックス取得アイコン](./media/user-guide/tx-events/image34.png)    | **ミューテックス取得** (*tx_mutex_get*) |
| ![ミューテックス情報取得アイコン](./media/user-guide/tx-events/image35.png)    | **ミューテックス情報取得** (*tx_mutex_info_get*) |
| ![ミューテックス パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image36.png)    | **ミューテックス パフォーマンス情報取得** (*tx_mutex_performance_info_get*) |
| ![ミューテックス システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image37.png)    | **ミューテックス システム パフォーマンス情報取得** (*tx_mutex_performance_system_info_get*) |
| ![ミューテックス優先度付けアイコン](./media/user-guide/tx-events/image38.png)    | **ミューテックス優先度付け** (*tx_mutex_prioritize*) |
| ![ミューテックス配置アイコン](./media/user-guide/tx-events/image39.png)    | **ミューテックス配置** (*tx_mutex_put*) |
| ![キュー作成アイコン](./media/user-guide/tx-events/image40.png)    | **キュー作成** (*tx_queue_create*) |
| ![キュー削除アイコン](./media/user-guide/tx-events/image41.png)    | **キュー削除** (*tx_queue_delete*) |
| ![キュー フラッシュ アイコン](./media/user-guide/tx-events/image42.png)    | **キュー フラッシュ** (*tx_queue_flush*) |
| ![キュー先頭送信アイコン](./media/user-guide/tx-events/image43.png)    | **キュー先頭送信** (*tx_queue_front_send*) |
| ![キュー情報取得アイコン](./media/user-guide/tx-events/image44.png)    | **キュー情報取得** (*tx_queue_info_get*) |
| ![キュー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image45.png)    | **キュー パフォーマンス情報取得** (*tx_queue_performance_info_get*) |
| ![キュー システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image46.png)    | **キュー システム パフォーマンス情報取得** (*tx_queue_performance_system_info_get*) |
| ![キュー優先度付けアイコン](./media/user-guide/tx-events/image47.png)    | **キュー優先度付け** (*tx_queue_prioritize*) |
| ![キュー受信メッセージ アイコン](./media/user-guide/tx-events/image48.png)    | **キュー受信メッセージ** (*tx_queue_receive*) |
| ![キュー送信メッセージ アイコン](./media/user-guide/tx-events/image49.png)    | **キュー送信メッセージ** (*tx_queue_send*) |
| ![キュー送信通知アイコン](./media/user-guide/tx-events/image50.png)    | **キュー送信通知** (*tx_queue_send_notify*) |
| ![セマフォ シーリング配置アイコン](./media/user-guide/tx-events/image51.png)    | **セマフォ シーリング配置** (*tx_semaphore_ceiling_put*) |
| ![セマフォ作成アイコン](./media/user-guide/tx-events/image52.png)    | **セマフォ作成** (*tx_semaphore_create*) |
| ![セマフォ削除アイコン](./media/user-guide/tx-events/image53.png)    | **セマフォ削除** (*tx_semaphore_delete*) |
| ![セマフォ取得アイコン](./media/user-guide/tx-events/image54.png)    | **セマフォ取得** (*tx_semaphore_get*) |
| ![セマフォ情報取得アイコン](./media/user-guide/tx-events/image55.png)    | **セマフォ情報取得** (*tx_semaphore_info_get*) |
| ![セマフォ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image56.png)    | **セマフォ パフォーマンス情報取得** (*tx_semaphroe_performance_info_get*) |
| ![セマフォ システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image57.png)    | **セマフォ システム パフォーマンス情報取得** (*tx_semaphore_performance_system_info_get*) |
| ![セマフォ優先度付けアイコン](./media/user-guide/tx-events/image58.png)    | **セマフォ優先度付け** (*tx_semaphore_prioritize*) |
| ![セマフォ配置アイコン](./media/user-guide/tx-events/image59.png)    | **セマフォ配置** (*tx_semaphore_put*) |
| ![セマフォ配置通知アイコン](./media/user-guide/tx-events/image60.png)    | **セマフォ配置通知** (*tx_semaphore_put_notify*) |
| ![スレッド作成アイコン](./media/user-guide/tx-events/image61.png)    | **スレッド作成** (*tx_thread_create*) |
| ![スレッド削除アイコン](./media/user-guide/tx-events/image62.png)    | **スレッド削除** (*tx_thread_delete*) |
| ![スレッド終了/開始通知アイコン](./media/user-guide/tx-events/image63.png)    | **スレッド終了/開始通知** (*tx_thread_entry_exit_notify*) |
| ![スレッド識別アイコン](./media/user-guide/tx-events/image64.png)    | **スレッド識別** (*tx_thread_identify*) |
| ![スレッド情報取得アイコン](./media/user-guide/tx-events/image65.png)    | **スレッド情報取得** (*tx_thread_info_get*) |
| ![スレッド パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image66.png)    | **スレッド パフォーマンス情報取得** (*tx_thread_performance_info_get*) |
| ![スレッド パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image67.png)    | **スレッド パフォーマンス システム情報取得** (*tx_thread_performance_system_info_get*) |
| ![スレッド プリエンプション変更アイコン](./media/user-guide/tx-events/image68.png)    | **スレッド プリエンプション変更** (*tx_thread_preemption_change*) |
| ![スレッド優先度変更アイコン](./media/user-guide/tx-events/image69.png)    | **スレッド優先度変更** (*tx_thread_priority_change*) |
| ![スレッド放棄アイコン](./media/user-guide/tx-events/image70.png)    | **スレッド放棄** (*tx_thread_relinquish*) |
| ![スレッド リセット アイコン](./media/user-guide/tx-events/image71.png)    | **スレッド リセット** (*tx_thread_reset*) |
| ![*スレッド再開アイコン](./media/user-guide/tx-events/image72.png)    | **スレッド再開** (**tx_thread_resume*) |
| ![スレッド スリープ アイコン](./media/user-guide/tx-events/image73.png)    | **スレッド スリープ** (*tx_thread_sleep*)* |
| ![スレッド スタック エラー通知アイコン](./media/user-guide/tx-events/image74.png)    | **スレッド スタック エラー通知** (*tx_thread_stack_error_notify*) |
| ![スレッド中断アイコン](./media/user-guide/tx-events/image75.png)    | **スレッド中断** (*tx_thread_suspend*) |
| ![スレッド終了アイコン](./media/user-guide/tx-events/image76.png)    | **スレッド終了** (*tx_thread_terminate*) |
| ![スレッド タイム スライス変更アイコン](./media/user-guide/tx-events/image77.png)    | **スレッド タイム スライス変更** (*tx_thread_time_slice_change*) |
| ![スレッド待機中止アイコン](./media/user-guide/tx-events/image78.png)    | **スレッド待機中止** (*tx_thread_wait_abort*) |
| ![時間取得アイコン](./media/user-guide/tx-events/image79.png)    | **時間取得** (*tx_time_get*) |
| ![時間設定アイコン](./media/user-guide/tx-events/image80.png)    | **時間設定** (*tx_time_set*) |
| ![*タイマー アクティブ化アイコン](./media/user-guide/tx-events/image81.png)    | **タイマー アクティブ化** (*tx_timer_activate*) |
| ![タイマー変更アイコン](./media/user-guide/tx-events/image82.png)    | **タイマー変更** (*tx_timer_change*) |
| ![タイマー作成アイコン](./media/user-guide/tx-events/image83.png)    | **タイマー作成** (*tx_timer_create*) |
| ![タイマー非アクティブ化アイコン](./media/user-guide/tx-events/image84.png)    | **タイマー非アクティブ化** (*tx_timer_deactivate*) |
| ![タイマー削除アイコン](./media/user-guide/tx-events/image85.png)    | **タイマー削除** (*tx_timer_delete*) |
| ![タイマー情報取得アイコン](./media/user-guide/tx-events/image86.png)    | **タイマー情報取得** (*tx_timer_info_get*) |
| ![タイマー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image87.png)    | **タイマー パフォーマンス情報取得** (*tx_timer_performance_info_get*) |
| ![*タイマー パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image88.png)    | **タイマー パフォーマンス システム情報取得** (*tx_timer_performance_system_info_get*) |
| ![ユーザー定義イベント アイコン](./media/user-guide/tx-events/image0.png)    | **ユーザー定義イベント** (第 10 章を参照)    |

## <a name="event-descriptions"></a>イベントの説明

### <a name="internal-thread-resume"></a>内部スレッド再開

#### <a name="internal-thread-resume"></a>内部スレッド再開

**アイコン** ![内部スレッド再開アイコン](./media/user-guide/tx-events/image1.png)

**説明**

このイベントは、スレッドの実行を再開する ThreadX の内部処理を表します。 指定されたスレッドの優先順位が最も高く、プリエンプションしきい値によって実行がブロックされていない場合、システムではこの新しく準備されたスレッドの実行が開始されます。

**情報フィールド**

- 情報フィールド 1: 再開するスレッドへのポインター。
- 情報フィールド 2: 再開するスレッドの以前の状態。状態は次のとおりです。

  |  スレッドの状態                     | 値        |
  |---------------------------------- | --------|
  |  TX_READY                         | 0       |
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- 情報フィールド 3: 呼び出し中のスタック ポインターの値。 
- 情報フィールド 4: 次に実行優先順位の高いスレッドへのポインター。

### <a name="internal-thread-suspend"></a>内部スレッド中断

#### <a name="internal-thread-suspend"></a>内部スレッド中断

**アイコン** ![内部スレッド中断アイコン](./media/user-guide/tx-events/image2.png)

**説明**

このイベントは、スレッドの実行を中断する ThreadX の内部処理を表します。 実行の準備ができ、次に優先順位の高いスレッドが 4 番目の情報フィールドに配置されます。 この値が NULL の場合、実行の準備が整っているスレッドが他になく、システムはアイドル状態になります。

**情報フィールド**

- 情報フィールド 1: 中断するスレッドへのポインター。
- 情報フィールド 2: 中断するスレッドの新しい状態。状態は次のとおりです。

  |  スレッドの状態                     | 値        |
  |---------------------------------- | --------|
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- 情報フィールド 3: 呼び出し中のスタック ポインターの値。 情報フィールド 4: 次に実行優先順位の高いスレッドへのポインター。 NULL の場合、システムはアイドル状態です。

### <a name="interrupt-service-routine-isr-enter"></a>割り込みサービス ルーチン (ISR) 開始 

#### <a name="enter-isr"></a>ISR 開始 

**アイコン** ![ISR 開始アイコン](./media/user-guide/tx-events/image3.png)

**説明**

このイベントは、アプリケーションでの割り込みサービス ルーチン (ISR) の開始を表します。 割り込みサービス ルーチンの実行は、ISR 終了イベントが発生するまで続行されます。

**情報フィールド**

- 情報フィールド 1: 呼び出し中のスタック ポインターの値。
- 情報フィールド 2: アプリケーション定義の ISR 番号 (省略可能)。
- 情報フィールド 3: 入れ子になった割り込みカウント。
- 情報フィールド 4: 内部プリエンプション無効フラグ。

### <a name="interrupt-service-routine-isr-exit"></a>割り込みサービス ルーチン (ISR) 終了 

#### <a name="exit-isr"></a>ISR 終了

**アイコン** ![ISR 終了アイコン](./media/user-guide/tx-events/image4.png)

**説明**

このイベントは、アプリケーションでの割り込みサービス ルーチン (ISR) の終了を表します。

**情報フィールド**

- 情報フィールド 1: 呼び出し中のスタック ポインターの値。
- 情報フィールド 2: アプリケーション定義の ISR 番号 (省略可能)。
- 情報フィールド 3: 入れ子になった割り込みカウント。
- 情報フィールド 4: 内部プリエンプション無効フラグ。

### <a name="internal-time-slice"></a>内部タイム スライス

#### <a name="internal-time-slice"></a>内部タイム スライス

**アイコン** ![内部タイム スライス アイコン](./media/user-guide/tx-events/image5.png)

**説明**

このイベントは、タイム スライス操作を実行する ThreadX の内部処理を表します。 最初の情報フィールドには、同じ優先順位の次のスレッドが配置されます。 この値が現在のスレッドと同じ場合、タイム スライスは実行されませんでした。

- 情報フィールド 1: 次に実行するスレッドへのポインター。
- 情報フィールド 2: 入れ子になった割り込みカウント。
- 情報フィールド 3: 内部プリエンプション無効フラグ。
- 情報フィールド 4: 呼び出し中のスタック ポインターの値。

### <a name="running"></a>実行中

#### <a name="running-in-context"></a>コンテキストで実行中

**アイコン** ![実行中アイコン](./media/user-guide/tx-events/image6.png)

**説明**

このイベントは、スレッド コンテキストまたはアイドル システム内で実行されていることを表します。 これは、割り込みの結果としてコンテキストでの後続の変更を示すために使用されます。

**情報フィールド**
- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="block-allocate"></a>ブロック割り当て 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**アイコン** ![ブロック割り当てアイコン](./media/user-guide/tx-events/image7.png)

**説明**

このイベントは、tx_block_allocate を使用したメモリ ブロックの割り当てを表します。 成功した場合は、割り当てられたブロックのアドレスが 2 番目の情報フィールドに返されます。

**情報フィールド**
- 情報フィールド 1: 対応するブロック プールへのポインター。
- 情報フィールド 2: 返されるメモリ ブロックへのポインター (成功した場合)。
- 情報フィールド 3: tx_block_allocate 呼び出しに指定する待機オプション。
- 情報フィールド 4: この割り当て後にプール内で使用可能な残りのブロック数。

### <a name="block-pool-create"></a>ブロック プール作成

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**アイコン** ![ブロック プール作成アイコン](./media/user-guide/tx-events/image8.png)

**説明**

このイベントは、tx_block_pool_create を使用したメモリ ブロック プールの作成を表します。

**情報フィールド**

- 情報フィールド 1: 対応するブロック プール制御ブロックへのポインター。
- 情報フィールド 2: プールの開始メモリ領域へのポインター。
- 情報フィールド 3: プール内のブロックの数。 情報フィールド 4: プール内の各ブロックのサイズ (バイト単位)。

### <a name="block-pool-delete"></a>ブロック プール削除

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**アイコン** ![ブロック プール削除アイコン](./media/user-guide/tx-events/image9.png)

**説明**

このイベントは、tx_block_pool_delete を使用したメモリ ブロック プールの削除を表します。

**情報フィールド**

- 情報フィールド 1: ブロック プール制御ブロックへのポインター。
- 情報フィールド 2: 呼び出し中のスタック ポインターの値。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="block-pool-information-get"></a>ブロック プール情報取得 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**アイコン** ![ブロック プール情報取得アイコン](./media/user-guide/tx-events/image10.png)

**説明**

このイベントは、tx_block_pool_info_get を使用したメモリ ブロック プールに関する情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: ブロック プール制御ブロックへのポインター。
- 情報フィールド 2: 呼び出し中のスタック ポインターの値。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="block-pool-performance-information-get"></a>ブロック プール パフォーマンス情報取得

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**アイコン** ![ブロック プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image11.png)

**説明**

このイベントは、tx_block_pool_performance_info_get を使用したメモリ ブロック プールに関するパフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: ブロック プール制御ブロックへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="block-pool-performance-system-information-get"></a>ブロック プール パフォーマンス システム情報取得

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**アイコン** ![ブロック プール パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image12.png)

**説明**

このイベントは、tx_block_pool_performance_system_info_get を使用したすべてのメモリ ブロック プールに関するパフォーマンス情報の取得を表します。

**情報フィールド**
- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="block-pool-prioritize"></a>ブロック プール優先度付け

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**アイコン** ![ブロック プール優先度付けアイコン](./media/user-guide/tx-events/image13.png)

**説明**

このイベントは、ブロック プールの中断リストの先頭に優先順位が最も高い中断されたスレッドを配置することを表します。 tx_block_release を呼び出す前にこの処理が行われた場合、優先順位が最も高い中断されたスレッドが解放されたブロックを受け取ります。

**情報フィールド**
- 情報フィールド 1: メモリ ブロック プールのポインター。
- 情報フィールド 2: このブロック プールで中断されているスレッドの数。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="block-release"></a>ブロック解放 

#### <a name="tx_block_release"></a>tx_block_release

**アイコン** ![ブロック解放アイコン](./media/user-guide/tx-events/image14.png)

**説明**

このイベントは、以前に割り当てられたブロックを解放してブロック プールに戻すことを表します。

**情報フィールド**

- 情報フィールド 1: メモリ ブロック プールのポインター。
- 情報フィールド 2: 解放するブロックへのポインター。
- 情報フィールド 3: このブロック プールで中断されているスレッドの数。
- 情報フィールド 4: 呼び出し時のスタック ポインター。

### <a name="byte-allocate"></a>バイト割り当て 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**アイコン** ![バイト割り当てアイコン](./media/user-guide/tx-events/image15.png)

**説明**

このイベントは、tx_byte_allocate を使用したメモリの割り当てを表します。 成功した場合は、割り当てられたメモリのアドレスが 2 番目の情報フィールドに返されます。

**情報フィールド**
- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: 返されるメモリへのポインター (成功した場合)。
- 情報フィールド 3: 要求したバイト数。 情報フィールド 4: tx_byte_allocate 呼び出しに指定する待機オプション。

### <a name="byte-pool-create"></a>バイト プール作成

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**アイコン** ![バイト プール作成アイコン](./media/user-guide/tx-events/image16.png)

**説明**

このイベントは、tx_byte_pool_create を使用したバイト プールの作成を表します。

**情報フィールド**

- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: メモリ領域の先頭へのポインター。 情報フィールド 3: バイト プール内のバイト数。
- 情報フィールド 4: 呼び出し時のスタック ポインター。

### <a name="byte-pool-delete"></a>バイト プール削除 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**アイコン** ![バイト プール削除アイコン](./media/user-guide/tx-events/image17.png)

**説明**

このイベントは、tx_byte_pool_delete を使用したバイト プールの削除を表します。

**情報フィールド**

- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="byte-pool-information-get"></a>バイト プール情報取得

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**アイコン** ![バイト プール情報取得アイコン](./media/user-guide/tx-events/image18.png)

**説明**

このイベントは、tx_byte_pool_info_get を使用したバイト プール情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="byte-pool-performance-info-get"></a>バイト プール パフォーマンス情報取得 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**アイコン** ![バイト プール パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image19.png)

**説明**

このイベントは、tx_byte_pool_performance_info_get を使用したバイト プール パフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="byte-pool-performance-system-info-get"></a>バイト プール パフォーマンス システム情報取得 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**アイコン** ![バイト プール パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image20.png)

**説明**

このイベントは、tx_byte_pool_performance_system_info_get を使用したバイト プール パフォーマンス システム情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="byte-pool-prioritize"></a>バイト プール優先度付け

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**アイコン** ![バイト プール優先度付けアイコン](./media/user-guide/tx-events/image21.png)

**説明**

このイベントは、tx_byte_pool_prioritize を使用したバイト プールの中断リストの優先順位付けを表します。

**情報フィールド**

- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: バイト プールで現在中断されているスレッドの数。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="byte-release"></a>バイト解放

#### <a name="tx_byte_release"></a>tx_byte_release

**アイコン** ![バイト解放アイコン](./media/user-guide/tx-events/image22.png)

**説明**

このイベントは、tx_byte_release を使用したバイト プールから割り当てられたメモリ ブロックの解放を表します。

**情報フィールド**

- 情報フィールド 1: 対応するバイト プールへのポインター。
- 情報フィールド 2: 以前に割り当てられたバイト プール メモリへのポインター。
- 情報フィールド 3: このバイト プールで中断されているスレッドの数。
- 情報フィールド 4: 使用可能なメモリのバイト数。

### <a name="event-flags-create"></a>イベント フラグ作成 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**アイコン** ![イベント フラグ作成アイコン](./media/user-guide/tx-events/image23.png)

**説明**

このイベントは、tx_event_flags_create を使用した新しいイベント フラグ グループの作成を表します。

**情報フィールド** 
- 情報フィールド 1: イベント フラグ グループ制御ブロックへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="event-flags-delete"></a>イベント フラグ削除 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**アイコン** ![イベント フラグ削除アイコン](./media/user-guide/tx-events/image24.png)

**説明**

このイベントは、tx_event_flags_delete を使用したイベント フラグ グループの削除を表します。

**情報フィールド** 

- 情報フィールド 1: イベント フラグ グループへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="event-flags-get"></a>イベント フラグ取得 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**アイコン** ![イベント フラグ取得アイコン](./media/user-guide/tx-events/image25.png)

**説明**

このイベントは、tx_event_flags_get を使用した既存のイベント フラグ グループからのイベント フラグの取得を表します。

**情報フィールド**

- 情報フィールド 1: イベント フラグ グループへのポインター。
- 情報フィールド 2: 要求されたイベント フラグ。
- 情報フィールド 3: グループに現在設定されているイベント フラグ。
- 情報フィールド 4: イベント フラグ取得時に要求されたオプション。

### <a name="event-flags-information-get"></a>イベント フラグ情報取得

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**アイコン** ![イベント フラグ情報取得アイコン](./media/user-guide/tx-events/image26.png)

**説明**

このイベントは、tx_event_flags_info_get を使用した既存のイベント フラグ グループに関する情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: イベント フラグ グループへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="event-flags-performance-information-get"></a>イベント フラグ パフォーマンス情報取得 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**アイコン** ![イベント フラグ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image27.png)

**説明**

このイベントは、tx_event_flags_performance_info_get を使用した既存のイベント フラグ グループに関するパフォーマンス情報の取得を表します。

**情報フィールド** 
- 情報フィールド 1: イベント フラグ グループへのポインター。
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="event-flags-performance-system-info-get"></a>イベント フラグ パフォーマンス システム情報取得

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**アイコン** ![イベント フラグ パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image28.png)

**説明**

このイベントは、tx_event_flags_performance_system_info_get を使用した既存のイベント フラグ グループに関するパフォーマンス情報の取得を表します。

**情報フィールド**
- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="event-flags-set"></a>イベント フラグ設定 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**アイコン** ![イベント フラグ設定アイコン](./media/user-guide/tx-events/image29.png)

**説明**

このイベントは、tx_event_flags_set を使用した既存のイベント フラグ グループのイベント フラグの設定 (または消去) を表します。

**情報フィールド**

- 情報フィールド 1: イベント フラグ グループへのポインター。
- 情報フィールド 2: 設定 (または消去) するイベント フラグ。
- 情報フィールド 3: AND または OR のイベント フラグ オプション。
- 情報フィールド 4: イベント フラグ グループで中断されているスレッドの数。

### <a name="event-flags-set-notify"></a>イベント フラグ設定通知

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**アイコン** ![イベント フラグ設定通知アイコン](./media/user-guide/tx-events/image30.png)

**説明**

このイベントは、tx_event_flags_set_notify を使用した既存のイベント フラグ グループのイベント フラグ設定操作に対する通知コールバックの登録を表します。

**情報フィールド**

- 情報フィールド 1: イベント フラグ グループへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="interrupt-control"></a>割り込み制御 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**アイコン** ![割り込み制御アイコン](./media/user-guide/tx-events/image31.png)

**説明**

このイベントは、tx_interrupt_control を使用したプロセッサの割り込みロックアウト状態の変化を表します。

**情報フィールド**

- 情報フィールド 1: 新しい割り込み状態。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-create"></a>ミューテックス作成 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**アイコン** ![ミューテックス作成アイコン](./media/user-guide/tx-events/image32.png)

**説明**

このイベントは、tx_mutex_create を使用したミューテックスの作成を表します。

**情報フィールド**

- 情報フィールド 1: ミューテックス制御ブロックへのポインター。
- 情報フィールド 2: 優先度の継承オプション
- (TX_INHERIT または TX_NO_INHERIT)。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-delete"></a>ミューテックス削除 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**アイコン** ![ミューテックス削除アイコン](./media/user-guide/tx-events/image33.png)

**説明**

このイベントは、tx_mutex_delete を使用したミューテックスの削除を表します。

**情報フィールド** 

- 情報フィールド 1: ミューテックスへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-get"></a>ミューテックス取得 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**アイコン** ![ミューテックス取得アイコン](./media/user-guide/tx-events/image34.png)

**説明**

このイベントは、tx_mutex_get を使用したミューテックスの取得を表します。

**情報フィールド**

- 情報フィールド 1: ミューテックスへのポインター。
- 情報フィールド 2: tx_mutex_get 呼び出しに指定する待機オプション。
- 情報フィールド 3: ミューテックスを所有するスレッドへのポインター (NULL はミューテックスが所有されていないことを意味します)。
- 情報フィールド 4: 所有スレッドが tx_mutex_get を呼び出した回数。

### <a name="mutex-information-get"></a>ミューテックス情報取得

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**アイコン** ![ミューテックス情報取得アイコン](./media/user-guide/tx-events/image35.png)

**説明**

このイベントは、tx_mutex_info_get を使用したミューテックス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: ミューテックスへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-performance-information-get"></a>ミューテックス パフォーマンス情報取得 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**アイコン** ![ミューテックス パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image36.png)

**説明**

このイベントは、tx_mutex_performance_info_get を使用したミューテックス パフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: ミューテックスへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-performance-system-info-get"></a>ミューテックス パフォーマンス システム情報取得

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**アイコン** ![ミューテックス パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image37.png)

**説明**

このイベントは、tx_mutex_performance_system_info_get を使用したミューテックス システム パフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-prioritize"></a>ミューテックス優先度付け 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**アイコン** ![ミューテックス優先度付けアイコン](./media/user-guide/tx-events/image38.png)

**説明**

このイベントは、tx_mutex_prioritize を使用したミューテックスの中断リストの優先順位付けを表します。

**情報フィールド**

- 情報フィールド 1: 対応するミューテックスへのポインター。
- 情報フィールド 2: ミューテックスで現在中断されているスレッドの数。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="mutex-put"></a>ミューテックス配置 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**アイコン** ![ミューテックス配置アイコン](./media/user-guide/tx-events/image39.png)

**説明**

このイベントは、tx_mutex_put を使用した以前に所有されたミューテックスの解放を表します。

**情報フィールド**

- 情報フィールド 1: 対応するミューテックスへのポインター。
- 情報フィールド 2: ミューテックスを所有しているスレッドのポインター。
- 情報フィールド 3: 未処理のミューテックス取得要求の数。
- 情報フィールド 4: 呼び出し時のスタック ポインター。

### <a name="queue-create"></a>キュー作成 

#### <a name="tx_queue_create"></a>tx_queue_create

**アイコン** ![キュー作成アイコン](./media/user-guide/tx-events/image40.png)

**説明**

このイベントは、tx_queue_create を使用したメッセージ キューの作成を表します。

**情報フィールド**

- 情報フィールド 1: キュー制御ブロックへのポインター。
- 情報フィールド 2: 32 ビット ワードで見たメッセージのサイズ。
- 情報フィールド 3: キュー メモリ領域の先頭へのポインター。
- 情報フィールド 4: キュー メモリ領域内のバイト数。

### <a name="queue-delete"></a>キュー削除 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**アイコン** ![キュー削除アイコン](./media/user-guide/tx-events/image41.png)

**説明**

このイベントは、tx_queue_delete を使用したキューの削除を表します。

**情報フィールド**

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="queue-flush"></a>キュー フラッシュ 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**アイコン** ![キュー フラッシュ アイコン](./media/user-guide/tx-events/image42.png)

**説明**

このイベントは、tx_queue_flush を使用したキューのフラッシュ (すべてのキューの内容のクリア) を表します。

**情報フィールド**

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="queue-front-send"></a>キュー先頭送信 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**アイコン** ![キュー先頭送信アイコン](./media/user-guide/tx-events/image43.png)

**説明**

このイベントは、tx_queue_front_send を使用したキューの先頭へのメッセージの送信を表します。

**情報フィールド**

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: メッセージの先頭へのポインター。
- 情報フィールド 3:
- tx_queue_front_send 呼び出しに指定された待機オプション。
- 情報フィールド 4: 既にキューに登録されているメッセージの数。

### <a name="queue-information-get"></a>キュー情報取得 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**アイコン** ![キュー情報取得アイコン](./media/user-guide/tx-events/image44.png)

**説明**

このイベントは、tx_queue_info_get を使用したキューに関する情報の取得を表します。

**情報フィールド** 
- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="queue-performance-info-get"></a>キュー パフォーマンス情報取得 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**アイコン** ![キュー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image45.png)

**説明**

このイベントは、tx_queue_performance_info_get を使用したキューに関するパフォーマンス情報の取得を表します。

**情報フィールド** 

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="queue-performance-system-info-get"></a>キュー パフォーマンス システム情報取得 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**アイコン** ![キュー パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image46.png)

**説明**

このイベントは、システム内のすべてのキューに関するシステム パフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="queue-prioritize"></a>キュー優先度付け 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**アイコン** ![キュー優先度付けアイコン](./media/user-guide/tx-events/image47.png)

**説明**

このイベントは、tx_queue_prioritize を使用したキューの中断リストの優先順位付けを表します。

**情報フィールド** 

- 情報フィールド 1: 対応するキューへのポインター。
- 情報フィールド 2: キューで現在中断されているスレッドの数。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

#### <a name="queue-receive"></a>キュー受信 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**アイコン** ![キュー受信アイコン](./media/user-guide/tx-events/image48.png)

**説明**

このイベントは、tx_queue_receive を使用したキューからのメッセージの受信を表します。

**情報フィールド** 

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: メッセージの宛先へのポインター。 情報フィールド 3: 呼び出しに指定された待機オプション。
- 情報フィールド 4: 現在キューに置かれているメッセージの数。

### <a name="queue-send"></a>キュー送信 

#### <a name="tx_queue_send"></a>tx_queue_send

**アイコン** ![キュー送信アイコン](./media/user-guide/tx-events/image49.png)

**説明**

このイベントは、tx_queue_send を使用したキューへのメッセージの送信を表します。

**情報フィールド** 

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: メッセージへのポインター。
- 情報フィールド 3: 呼び出しに指定された待機オプション。
- 情報フィールド 4: 現在キューに置かれているメッセージの数。

### <a name="queue-send-notify"></a>キュー送信通知 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**アイコン** ![キュー送信通知アイコン](./media/user-guide/tx-events/image50.png)

**説明**

<p>このイベントは、メッセージがキューに送信されるたびに呼び出される tx_queue_send_notify を使用したコールバックの登録を表します。

**情報フィールド** 

- 情報フィールド 1: キューへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-ceiling-put"></a>セマフォ シーリング配置 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**アイコン** ![セマフォ シーリング配置アイコン](./media/user-guide/tx-events/image51.png)

**説明**

このイベントは、tx_semaphore_ceiling_put を使用したセマフォへの配置を表します。 これは、put 操作で最大値またはシーリングを超えることができないようにセマフォの最大値が検査されるという点で tx_semaphore_put とは異なります。

**情報フィールド**

- 情報フィールド 1: セマフォへのポインター。
- 情報フィールド 2: 現在のセマフォ数。
- 情報フィールド 3: セマフォで中断されているスレッドの数。
- 情報フィールド 4: 呼び出しに指定されたシーリング制限。

#### <a name="semaphore-create"></a>セマフォ作成 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**アイコン** ![セマフォ作成アイコン](./media/user-guide/tx-events/image52.png)

**説明**

このイベントは、tx_semaphore_create を使用したセマフォの作成を表します。

**情報フィールド**

- 情報フィールド 1: セマフォ制御ブロックへのポインター。
- 情報フィールド 2: 初期のセマフォ数。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-delete"></a>セマフォ削除 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**アイコン** ![セマフォ削除アイコン](./media/user-guide/tx-events/image53.png)

**説明**

このイベントは、tx_semaphore_delete を使用したセマフォの削除を表します。

**情報フィールド**

- 情報フィールド 1: セマフォへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-get"></a>セマフォ取得 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**アイコン** ![セマフォ取得アイコン](./media/user-guide/tx-events/image54.png)

**説明**

このイベントは、tx_semaphore_get を使用したセマフォの取得を表します。

**情報フィールド**

- 情報フィールド 1: セマフォへのポインター。
- 情報フィールド 2: 呼び出しに指定された待機オプション。
- 情報フィールド 3: 現在のセマフォ数。
- 情報フィールド 4: 呼び出し時のスタック ポインター。

### <a name="semaphore-information-get"></a>セマフォ情報取得 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**アイコン** ![セマフォ情報取得アイコン](./media/user-guide/tx-events/image55.png)

**説明**

このイベントは、tx_semaphore_info_get を使用したセマフォに関する情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: セマフォへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-performance-info-get"></a>セマフォ パフォーマンス情報取得 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**アイコン** ![セマフォ パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image56.png)

**説明**

このイベントは、tx_semaphore_performance_info_get を使用したセマフォに関するパフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: セマフォへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-performance-system-info"></a>セマフォ パフォーマンス システム情報 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**アイコン** ![セマフォ パフォーマンス システム情報アイコン](./media/user-guide/tx-events/image57.png)

**説明**

このイベントは、tx_semaphore_performance_system_info_get を使用したシステム内のすべてのセマフォに関するパフォーマンス情報の取得を表します。

**情報フィールド** 

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-prioritize"></a>セマフォ優先度付け 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**アイコン** ![セマフォ優先度付けアイコン](./media/user-guide/tx-events/image58.png)

**説明**

このイベントは、tx_semaphore_prioritize を使用したセマフォの中断リストの優先順位付けを表します。

**情報フィールド**

- 情報フィールド 1: 対応するセマフォへのポインター。
- 情報フィールド 2: セマフォで現在中断されているスレッドの数。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="semaphore-put"></a>セマフォ配置 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**アイコン** ![セマフォ配置アイコン](./media/user-guide/tx-events/image59.png)

**説明**

このイベントは、tx_semaphore_put を使用したセマフォ インスタンスの解放を表します。

**情報フィールド** 

- 情報フィールド 1: 対応するセマフォへのポインター。 情報フィールド 2: 現在のセマフォ数。
- 情報フィールド 3: セマフォで中断されているスレッドの数。
- 情報フィールド 4: 呼び出し時のスタック ポインター。

### <a name="semaphore-put-notify"></a>セマフォ配置通知 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**アイコン** ![セマフォ配置通知アイコン](./media/user-guide/tx-events/image60.png)

**説明**

このイベントは、セマフォ インスタンスが配置されるたびに呼び出される tx_semaphore_put_notify を使用したコールバックの登録を表します。

**情報フィールド** 

- 情報フィールド 1: セマフォへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-create"></a>スレッド作成 

#### <a name="tx_thread_create"></a>tx_thread_create

**アイコン** ![スレッド作成アイコン](./media/user-guide/tx-events/image61.png)

**説明**

このイベントは、tx_thread_create を使用したスレッドの作成を表します。

**情報フィールド**

- 情報フィールド 1: スレッド制御ブロックへのポインター。
- 情報フィールド 2: スレッドの優先順位。
- 情報フィールド 3: スレッドのスタック ポインター。
- 情報フィールド 4: スタックのサイズ (バイト単位)。

### <a name="thread-delete"></a>スレッド削除 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**アイコン** ![スレッド削除アイコン](./media/user-guide/tx-events/image62.png)

**説明**

このイベントは、tx_thread_delete を使用したスレッドの削除を表します。

**情報フィールド** 

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-entryexit-notify"></a>スレッド開始/終了通知 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**アイコン** ![スレッド開始/終了通知アイコン](./media/user-guide/tx-events/image63.png)

**説明**

このイベントは、スレッドが開始または終了するたびに呼び出される tx_thread_entry_exit_notify を使用したコールバックの登録を表します。

**情報フィールド** 

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 登録時のスレッド状態。
- 情報フィールド 3: 呼び出し時のスタックへのポインター。
- 情報フィールド 4: 使用されていません。

#### <a name="thread-identify"></a>スレッド識別 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**アイコン** ![スレッド識別アイコン](./media/user-guide/tx-events/image64.png)

**説明**

このイベントは、tx_thread_identify を使用した現在のスレッド ポインターの取得を表します。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-information-get"></a>スレッド情報取得 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**アイコン** ![スレッド情報取得アイコン](./media/user-guide/tx-events/image65.png)

**説明**

このイベントは、tx_thread_info_get を使用した指定されたスレッドに関する情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

#### <a name="thread-performance-information-get"></a>スレッド パフォーマンス情報取得 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**アイコン** ![スレッド パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image66.png)

**説明**

このイベントは、tx_thread_performance_info_get を使用した指定されたスレッドに関するパフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-performance-system-info-get"></a>スレッド パフォーマンス システム情報取得 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**アイコン** ![スレッド パフォーマンス システム情報取得アイコン](./media/user-guide/tx-events/image67.png)

**説明**

このイベントは、tx_thread_performance_system_info_get を使用したすべてのスレッドに関するパフォーマンス情報の取得を表します。

**情報フィールド** 

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-preemption-change"></a>スレッド プリエンプション変更 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**アイコン** ![スレッド プリエンプション変更アイコン](./media/user-guide/tx-events/image68.png)

**説明**

このイベントは、tx_thread_preemption_change を使用したスレッドのプリエンプションしきい値の変更を表します。

**情報フィールド** 

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 新しいプリエンプションしきい値。
- 情報フィールド 3: 以前のプリエンプションしきい値。
- 情報フィールド 4: 呼び出し時のスレッドの状態。

### <a name="thread-priority-change"></a>スレッド優先度変更 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**アイコン** ![スレッド優先度変更アイコン](./media/user-guide/tx-events/image69.png)

**説明**

このイベントは、tx_thread_priority_change を使用したスレッドの優先順位の変更を表します。

- 情報フィールド 
- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 新しい優先順位。
- 情報フィールド 3: 以前の優先順位。
- 情報フィールド 4: 呼び出し時のスレッドの状態。

### <a name="thread-relinquish"></a>スレッド放棄 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**アイコン** ![スレッド放棄アイコン](./media/user-guide/tx-events/image70.png)

**説明**

このイベントは、tx_thread_relinquish を使用したスレッドからのプロセッサの解放を表します。

**情報フィールド**

- 情報フィールド 1: 呼び出し時のスタック ポインター。
- 情報フィールド 2: 次に実行するスレッドへのポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-reset"></a>スレッド リセット 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**アイコン** ![スレッド リセット アイコン](./media/user-guide/tx-events/image71.png)

**説明**

このイベントは、tx_thread_reset を使用した完了または終了したスレッドのリセットを表します。

**情報フィールド**

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

#### <a name="thread-resume"></a>スレッド再開 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**アイコン** ![スレッド再開アイコン](./media/user-guide/tx-events/image72.png)

**説明**

このイベントは、tx_thread_resume を使用した中断されたスレッドの再開を表します。

**情報フィールド**

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="thread-sleep"></a>スレッド スリープ 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**アイコン** ![スレッド スリープ アイコン](./media/user-guide/tx-events/image73.png)

**説明**

このイベントは、tx_thread_sleep を使用した指定されたタイマー ティック数の現在のスレッドの中断を表します。

**情報フィールド**

- 情報フィールド 1: 中断するティック数。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="thread-stack-error-notify"></a>スレッド スタック エラー通知 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**アイコン** ![スレッド スタック エラー通知アイコン](./media/user-guide/tx-events/image74.png)

**説明**

このイベントは、tx_thread_stack_error_notify_event を使用したスレッド スタック エラー通知ルーチンの登録を表します。

**情報フィールド** 

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="thread-suspend"></a>スレッド中断 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**アイコン** ![スレッド中断アイコン](./media/user-guide/tx-events/image75.png)

**説明**

このイベントは、tx_thread_suspend を使用したスレッドの中断を表します。

**情報フィールド** 

- 情報フィールド 1: 中断するスレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="thread-terminate"></a>スレッド終了 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**アイコン** ![スレッド終了アイコン](./media/user-guide/tx-events/image76.png)

**説明**

このイベントは、tx_thread_terminate を使用したスレッドの終了を表します。

**情報フィールド** 

- 情報フィールド 1: 終了するスレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="thread-time-slice-change"></a>スレッド タイム スライス変更 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**アイコン** ![スレッド タイム スライス変更アイコン](./media/user-guide/tx-events/image77.png)

**説明**

このイベントは、tx_thread_time_slice_change を使用したスレッドのタイム スライスの変更を表します。

**情報フィールド**

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 新しいタイム スライス。
- 情報フィールド 3: 以前のタイム スライス。
- 情報フィールド 4: 使用されていません。

### <a name="thread-wait-abort"></a>スレッド待機中止 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**アイコン** ![スレッド待機中止アイコン](./media/user-guide/tx-events/image78.png)

**説明**

このイベントは、tx_thread_wait_abort を使用したスレッドの中断の中止を表します。

**情報フィールド**

- 情報フィールド 1: スレッドへのポインター。
- 情報フィールド 2: 呼び出し時のスレッドの状態。
- 情報フィールド 3: 呼び出し時のスタック ポインター。
- 情報フィールド 4: 使用されていません。

### <a name="time-get"></a>時間取得 

#### <a name="tx_time_get"></a>tx_time_get

**アイコン** ![時間取得アイコン](./media/user-guide/tx-events/image79.png)

**説明**

このイベントは、tx_time_get を使用した現在のタイマー ティック数の取得を表します。

**情報フィールド**

- 情報フィールド 1: 現在のタイマー ティック数。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="time-set"></a>時間設定 

#### <a name="tx_time_set"></a>tx_time_set

**アイコン** ![時間設定アイコン](./media/user-guide/tx-events/image80.png)

**説明**

このイベントは、tx_time_set を使用した現在のタイマー ティック数の設定を表します。

**情報フィールド**

- 情報フィールド 1: 新しいタイマー ティック数。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="timer-activate"></a>タイマー アクティブ化 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**アイコン** ![タイマー アクティブ化アイコン](./media/user-guide/tx-events/image81.png)

**説明**

このイベントは、tx_timer_activate を使用した指定されたタイマーのアクティブ化を表します。

**情報フィールド**

- 情報フィールド 1: タイマーへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="timer-change"></a>タイマー変更 

#### <a name="tx_timer_change"></a>tx_timer_change

**アイコン** ![タイマー変更アイコン](./media/user-guide/tx-events/image82.png)

**説明**

このイベントは、tx_timer_change を使用した指定されたタイマーの変更を表します。

**情報フィールド**

- 情報フィールド 1: タイマーへのポインター。
- 情報フィールド 2: 初期の有効期限のティック。
- 情報フィールド 3: 有効期限のティックの再スケジュール。
- 情報フィールド 4: 使用されていません。

### <a name="timer-create"></a>タイマー作成 

#### <a name="tx_timer_create"></a>tx_timer_create

**アイコン** ![タイマー作成アイコン](./media/user-guide/tx-events/image83.png)

**説明**

このイベントは、tx_timer_create を使用したタイマーの作成を表します。

**情報フィールド**

- 情報フィールド 1: タイマー制御ブロックへのポインター。
- 情報フィールド 2: 初期の有効期限のティック。
- 情報フィールド 3: 有効期限のティックの再スケジュール。
- 情報フィールド 4: 自動有効化値。TX_AUTO_ACTIVATE (1) または TX_NO_ACTIVATE (0) のいずれか。

### <a name="timer-deactivate"></a>タイマー非アクティブ化 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**アイコン** ![タイマー非アクティブ化アイコン](./media/user-guide/tx-events/image84.png)

**説明**

このイベントは、tx_timer_deactivate を使用したタイマーの非アクティブ化を表します。

**情報フィールド**

- 情報フィールド 1: タイマーへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="timer-delete"></a>タイマー削除 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**アイコン** ![タイマー削除アイコン](./media/user-guide/tx-events/image85.png)

**説明**

このイベントは、tx_timer_delete を使用したタイマーの削除を表します。

**情報フィールド** 

- 情報フィールド 1: タイマーへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="timer-information-get"></a>タイマー情報取得 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**アイコン** ![タイマー取得情報アイコン](./media/user-guide/tx-events/image86.png)

**説明**

このイベントは、tx_timer_info_get を使用したタイマー情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: タイマーへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="timer-performance-information-get"></a>タイマー パフォーマンス情報取得 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**アイコン** ![タイマー パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image87.png)

**説明** 

このイベントは、tx_timer_performance_info_get を使用したタイマー パフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: タイマーへのポインター。
- 情報フィールド 2: 呼び出し時のスタック ポインター。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="timer-system-performance-info-get"></a>タイマー システム パフォーマンス情報取得 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**アイコン** ![タイマー システム パフォーマンス情報取得アイコン](./media/user-guide/tx-events/image88.png)


**説明** 

このイベントは、tx_timer_performance_system_info_get を使用したすべてのタイマー パフォーマンス情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。