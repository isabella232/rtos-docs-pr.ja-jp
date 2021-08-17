---
title: 第 3 章 - Azure RTOS NetX Duo PTP クライアント サービスの説明
description: この章では、すべての NetX Duo PTP クライアント サービスをアルファベット順に説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 686db68181e3712f9f6a09a9f471626eff610fd7f45ec5b83ba56f8b7aa378cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798012"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>第 3 章 - Azure RTOS NetX Duo PTP クライアント サービスの説明

この章では、すべての NetX Duo PTP クライアント サービス (以下に記載) をアルファベット順に説明します。

[!NOTE]
> "*以下の API 関数の説明の「**戻り値**」セクションでは、**太字** の値は API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。* "

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

PTP クライアント インスタンスを作成します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>説明

このサービスでは、PTP クライアントのインスタンスを作成します。

アプリケーションでは、PTP クライアントがパケットを送信するための IP インスタンスとパケット プールを最初に作成する必要がある点に注意します。 パケット プールについては、アプリケーションは IP インスタンスで同じパケット プールを使用することも、PTP クライアント専用のパケット プールを作成することもできます。  専用パケット プールのアプローチには、小さいパケット (IPv6 が使用されている場合は 128 バイト、IPv4 のみの場合は 108 バイト) の使用という利点があります。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **ip_ptr**: IP インスタンスへのポインター
* **interface_index**: PTP ネットワーク インターフェイスのインデックス
* **packet_pool_ptr**: クライアントのパケット プールへのポインター
* **thread_priority**: PTP スレッドの優先順位
* **thread_stack**: スレッド スタックへのポインター
* **stack_size**: スレッド スタックのサイズ
* **clock_callback**: PTP クロック コールバック
* **clock_callback_data**: クロック コールバックのデータ

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD**: (0xD04) パケット ペイロードが小さすぎます
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE**: (0xD05) クロック コールバックに失敗しました
* **status**: NetX Duo および ThreadX サービス呼び出しの完了状態
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
* NX_INVALID_INTERFACE: (0x4C) インターフェイスが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

PTP クライアント インスタンスを削除します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、PTP クライアントのインスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 削除する PTP クライアントへのポインター

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に削除されました
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

マスター クロック情報を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>説明
このサービスは、マスター クロックの情報を取得します。 マスター制御ブロックは、イベント コールバック関数を介してユーザー アプリケーションに渡されます。

### <a name="input-parameters"></a>入力パラメーター
* **master_ptr**: PTP マスター クロックへのポインター
* **address**: マスター クロックのアドレス
* **port_identity**: PTP マスター ポートと ID
* **port_identity_length**: PTP マスター ポートと ID の長さ
* **priority1**: PTP マスター クロックの Priority1
* **priority2**: PTP マスター クロックの Priority2
* **clock_class**: PTP マスター クロックのクラス
* **clock_accuracy**: PTP マスター クロックの精度
* **clock_variance**: PTP マスター クロックの差異
* **grandmaster_identity**: グランドマスター クロックの ID
* **grandmaster_identity_length**: グランドマスター ID の長さ
* **steps_removed**: PTP ヘッダーから削除されたステップ
* **time_source**: グランドマスター クロックによって使用されるタイマーのソース

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) マスター クロック情報が正常に取得されました
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

パケットのタイムスタンプを PTP クライアントに通知します。

### <a name="prototype"></a>プロトタイプ

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>説明
このサービスは、パケットがタイムスタンプ付きで送信されたことを PTP クライアントに通知します。 このサービスはネットワーク ドライバー用に設計されており、パケットが送信されるときに呼び出されます。 通常、タイムスタンプはハードウェアによって生成されます。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **packet_ptr**: 送信される PTP パケットへのポインター
* **timestamp_ptr**: PTP パケットのタイムスタンプへのポインター

### <a name="return-values"></a>戻り値
なし

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

PTP クロックのソフトウェア実装。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>説明
このコールバック関数は、PTP のシミュレートされた低解像度クロック ソースとして機能します。 このルーチンは参照用として提供されており、運用環境では使用できません。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **operation**: コールバック操作。有効な値は次のように定義されています。
  * **NX_PTP_CLIENT_CLOCK_INIT**: クロックを初期化します。
  * **NX_PTP_CLIENT_CLOCK_SET**: `time_ptr` で指定された現在のタイムスタンプを設定します。
  * **NX_PTP_CLIENT_CLOCK_GET**: 現在のタイムスタンプを `time_ptr` に返します。
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT**: `packet_ptr` から `time_ptr` にタイムスタンプを抽出します。
  * **NX_PTP_CLIENT_CLOCK_ADJUST**: 現在のタイムスタンプを *1* 秒未満に調整します。
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE**: 送信されたタイムスタンプを PTP クライアントに通知する必要がある `packet_ptr` をマークします。
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE**: ソフト タイマーを更新します。 ハードウェア クロックではこれを無視できます。
* **time_ptr**: タイムスタンプへのポインター。
* **packet_ptr**: パケットへのポインター。
* **callback_data**: 不透明なコールバック データへのポインター。

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) 操作が正常に完了しました
* **NX_PTP_PARAM_ERROR**: (0xD03) パラメーターが無効です

### <a name="allowed-from"></a>許可元
PTP 内部

### <a name="example"></a>例
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

PTP クライアントを起動します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>説明
このサービスは、以前に作成された PTP クライアント インスタンスを起動します。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **client_port_identity_ptr**: クライアント ポートと ID へのポインター。NULL にすることもできます
* **client_port_identity_length**: クライアント ポートと ID の長さ。 client_port_identity_ptr が NULL または NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10) の場合は、0 である必要があります
* **domain**: PTP クロック ドメイン
* **transport_specific**: 4 ビットの転送固有
* **event_callback**: イベントで呼び出されるコールバック関数
* **event_callback_data**: イベント コールバックのデータ

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に起動されました
* **NX_PTP_CLIENT_ALREADY_STARTED**: (0xD02) PTP クライアントは既に起動されています
* **status**: NetX Duo および ThreadX サービス呼び出しの完了状態
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

PTP クライアントを停止します。  PTP クライアントを停止した後は、PTP パケットの処理も送信も行われなくなります。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明
このサービスは、以前に作成され、起動された PTP クライアント インスタンスを停止します。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 停止する PTP クライアントへのポインター

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に停止されました
* **NX_PTP_CLIENT_NOT_STARTED**: (0xD01) クライアントが起動していません
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

同期情報を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>説明
このサービスは、Sync メッセージの情報を取得します。 Sync 制御ブロックは、イベント コールバック関数を介してユーザー アプリケーションに渡されます。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **flags**: Sync メッセージのフラグ
* **utc_offset**: TAI と UTC の間のオフセット

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) 同期情報が正常に取得されました
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

現在の時刻を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>説明
このサービスは、PTP クロックの現在の値を取得します。 PTP クライアントがマスター クロックと同期されているかどうかに関係なく使用できます。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **time_ptr**: PTP 時刻へのポインター

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

現在の時刻を設定します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>説明
このサービスは、PTP クロックの現在の値を設定します。 PTP クライアントが起動する前に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター
* **client_ptr**: 作成する PTP クライアントへのポインター
* **time_ptr**: PTP 時刻へのポインター

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
* **NX_PTP_CLIENT_ALREADY_STARTED**: (0xD02) PTP クライアントは既に起動されています
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

PTP 時刻を UTC の日付と時刻に変換します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>説明
このサービスは、PTP 時刻を UTC の日付と時刻に変換します。

### <a name="input-parameters"></a>入力パラメーター
* **time_ptr**: PTP 時刻へのポインター
* **offset**: PTP 時刻を追加するための符号付き秒オフセット
* **date_time_ptr**: 変換後の日付へのポインター

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
* **変換後の日付へのポインター**: (0xD03) 入力パラメーターが無効です
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

2 つの PTP 時刻の差を計算します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>説明
このサービスは、2 つの PTP 時刻の差を計算します。

### <a name="input-parameters"></a>入力パラメーター
* **time1_ptr**: 最初の PTP 時刻へのポインター
* **time2_ptr**: 2 番目の PTP 時刻へのポインター
* **result_ptr**: 結果 time1-time2 へのポインター

### <a name="return-values"></a>戻り値
* **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
* NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元
Threads

### <a name="example"></a>例
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```