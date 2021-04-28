---
title: 第 1 章 - Azure RTOS NetX Duo PTP クライアントの概要
description: この章では、Azure RTOS NetX Duo PTP クライアントの概要を説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810622"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>第 1 章 - Azure RTOS NetX Duo PTP クライアントの概要

Azure RTOS NetX Duo PTP は、Precision Time Protocol (PTP) バージョン 2 (IEEE 1588-2008) のクライアント部分を実装しています。 これは、IPv4 または IPv6 マルチキャスト パケットを介して相互に通信することによって、ローカル ネットワーク上の MCU 間でクロックを同期するために使用されます。

## <a name="netx-duo-ptp-client-setup"></a>NetX Duo PTP クライアントのセットアップ

PTP クライアント パッケージを正しく機能させるには、NetX Duo IP インスタンスが既に作成されている必要があります。

既定では、PTP クライアントは IPv4 マルチキャスト グループに参加します。 IPv6 ネットワーク上で PTP クライアントを実行するには、NetX Duo ライブラリを構築するときに `NX_ENABLE_IPV6_MULTICAST` を定義する必要があります。

PTP クライアントの作成時に、着信および発信パケットのタイムスタンプを処理するコールバック関数をアプリケーションで提供する必要があります。 高解像度を実現するために、アプリケーションで高解像度タイマーを使用してタイムスタンプを生成することをお勧めします。 シミュレーターで PTP を実行するために、ソフトウェアベースの実装である `nx_ptp_client_soft_clock_callback` が用意されています。

PTP クライアントには、PTP メッセージを送信するためのパケット プールが必要です。 パケット プールのペイロード サイズは、`NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` (IPv4 の場合は 108 バイト、IPv6 が有効な場合は 128 バイト) 以上である必要があります。

PTP クライアントの作成後、アプリケーションで PTP クライアントを起動できます。 同期は PTP ヘルパー スレッドで実行されます。 イベント コールバック関数を指定できます。 これは、次のいずれかのイベントが発生したときに呼び出されます。
* マスターの選択。 
* 時間の調整。
* マスターのタイムアウト。

## <a name="netx-duo-ptp-client-messages"></a>NetX Duo PTP クライアント メッセージ

NetX Duo PTP クライアントは、遅延要求 - 応答メカニズムのみを実装しています。 PTP クライアントでは 2 つの UDP ポートを開きます。 **イベント** メッセージ用の *319* と、**一般** メッセージ用の *320* です。 このメカニズムには、5 種類のメッセージがあります。

* **Announce**: これはイベント メッセージです。 マスター クロックの選択に使用されます。
* **Sync**: これはイベント メッセージです。 発信元タイムスタンプを送信し、マスターからクライアントへのパス遅延を計算するために使用されます。
* **Follow_Up**: これは一般メッセージです。 関連する Sync メッセージの発信元タイムスタンプを修正するために、必要に応じて使用されます。 Sync フラグの 2 ステップ ビットが設定されている場合にのみ送信されます。
* **Delay_Req**: これはイベント メッセージです。 Delay_Resp の受信時に、クライアントからマスターへのパス遅延を計算するために、PTP クライアントから送信されます。
* **Delay_Resp**: これはイベント メッセージです。 クライアントからマスターへのパス遅延を計算するために、マスターからクライアントに送信されます。

" *"ベスト マスター クロック" アルゴリズムは実装されていないことに注意してください。PTP クライアントがリッスン状態の場合、最初のマスター クロックのみが受け入れられます。* "

## <a name="netx-duo-ptp-client-clock-callback"></a>NetX Duo PTP クライアントのクロック コールバック
マスターからのクロックを同期するには、PTP クライアントにローカル クロックが必要です。 クロック コールバック関数は、作成時に PTP クライアントに渡されます。 クロック コールバック ルーチンの形式は次のように定義されています。
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
入力パラメーターは次のように定義されています。
* *client_ptr* は、PTP クライアントを指します。
* *operation* では、コールバック操作を指定します。有効な値は次の一覧のように定義されています。
  * **NX_PTP_CLIENT_CLOCK_INIT**: クロックを初期化します。
  * **NX_PTP_CLIENT_CLOCK_SET**: `time_ptr` で指定された現在のタイムスタンプを設定します。
  * **NX_PTP_CLIENT_CLOCK_GET**: 現在のタイムスタンプを `time_ptr` に返します。
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT**: `packet_ptr` から `time_ptr` にタイムスタンプを抽出します。
  * **NX_PTP_CLIENT_CLOCK_ADJUST**: 現在のタイムスタンプを *1* 秒未満に調整します。
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE**: 送信されたタイムスタンプを PTP クライアントに通知する必要がある `packet_ptr` をマークします。
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE**: ソフト タイマーを更新します。 ハードウェア クロックではこれを無視できます。
* *time_ptr* はタイムスタンプを指します。
* *packet_ptr* はパケットを指します。
* *callback_data* は、不透明なコールバック データを指します。

NX_PTP_TIME データ型は、次のように定義されています。
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a>NetX Duo PTP クライアントのイベント コールバック
PTP クライアントの状態をアプリケーションに通知するために、イベント コールバック関数を設定できます。 イベント コールバック ルーチンの形式は次のように定義されています。
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
入力パラメーターは次のとおりです。
* *client_ptr* は、PTP クライアントを指します。
* *event* では、コールバック イベントを指定します。有効な値は、次のように定義されています。
  * **NX_PTP_CLIENT_EVENT_MASTER**: マスター クロックが選択されました。
  * **NX_PTP_CLIENT_EVENT_SYNC**: PTP クライアントが調整されました。
  * **NX_PTP_CLIENT_EVENT_TIMEOUT**: マスター クロックがタイムアウトしました。
* *event_data* では、イベントに関連するデータを指定します。 イベントが **NX_PTP_CLIENT_EVENT_MASTER** の場合、event_data は `NX_PTP_CLIENT_MASTER` インスタンスを参照します。 イベントが **NX_PTP_CLIENT_EVENT_SYNC** の場合、event_data は `NX_PTP_CLIENT_SYNC` インスタンスを参照します。

## <a name="netx-duo-ptp-client-communication"></a>NetX Duo PTP クライアント通信
前述のように、NetX Duo PTP クライアントでは、遅延要求 - 応答メカニズムのみがサポートされています。 このメカニズムでは、クライアントとマスター クロック間の平均パス遅延が次のように測定されます。
1. クライアントは、マスターから *Announce* メッセージを受信すると、それをベスト マスターとして選択します。
1. クライアントは、マスターから *Sync* メッセージを受信します。 タイムスタンプ *t1* は、このメッセージの発信元タイムスタンプです。 このメッセージを受信すると、タイムスタンプ *t2* がローカル クロックから読み取られます。
1. クライアントは、マスターから *Follow_Up* メッセージを受信します。 このメッセージは省略可能であり、*Sync* フラグの 2 ステップが設定されている場合にのみ有効です。 その後、タイムスタンプ *t1* がこのメッセージの発信元タイムスタンプに更新されます。
1. クライアントは、*Delay_Req* メッセージをマスターに送信します。 メッセージが送信されると、タイムスタンプ *t3* がローカル クロックから読み取られます。
1. クライアントは、マスターから *Delay_Resp* メッセージを受信します。 タイムスタンプ *t4* は、このメッセージの受信タイムスタンプです。

平均パス遅延は、次のように計算されます。
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
マスターからのオフセットは、次のように計算されます。
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> "****correctionField** _ は計算時に無視されます。_"