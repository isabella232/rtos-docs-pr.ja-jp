---
title: チャプター 3 - Azure RTOS NetX Duo SNTP クライアントのサービスの説明
description: この章では、NetX Duo SNTP クライアントのすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7aee18642e480ec61488515164c8a6816753dca86eb8f6d146ea22d4956e037a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791671"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>チャプター 3 - Azure RTOS NetX Duo SNTP クライアントのサービスの説明

この章では、Azure RTOS NetX Duo SNTP クライアントのすべてのサービス (以下に記載) をアルファベット順に説明します。

次の API の説明の「戻り値」セクションで、**太字** の値は、API のエラー チェックを有効にするための **NX_DISABLE_ERROR_CHECKING** を有効にしてもその影響を受けないことを表します。太字でない値は完全に無効になります。

- **nx_sntp_client_create**: *SNTP クライアントを作成します*
- **nx_sntp_client_delete**: *SNTP クライアントを削除します*
- **nx_sntp_client_get_local_time**: *SNTP クライアントのローカル時刻を取得します*
- **nx_sntp_client_get_local_time_extended**: *SNTP クライアントのローカル時刻を取得します*
- **nx_sntp_client_initialize_broadcast**: *IPv4 ブロードキャスト使用のためにクライアントを初期化します*
- **nxd_sntp_client_initialize_broadcast**: *IPv6 または IPv4 ブロードキャスト使用のためにクライアントを初期化します*
- **nx_sntp_client_initialize_unicast**: *IPv4 ユニキャスト使用のためにクライアントを初期化します*
- **nxd_sntp_client_initialize_unicast**: *IPv4 または IPv6 ユニキャスト使用のためにクライアントを初期化します*
- **nx_sntp_client_receiving_udpates**: *クライアントで有効な SNTP 更新を受信中です*
- **nx_sntp_client_request_unicast_time**: *ユニキャスト要求を直接 NTP サーバーに送信します*
- **nx_sntp_client_run_broadcast**: *クライアントをブロードキャスト モードで実行します*
- **nx_sntp_client_run_unicast**: *クライアントをユニキャスト モードで実行します*
- **nx_sntp_client_set_local_time**: *SNTP クライアントの最初のローカル時刻を設定します*
- **nx_sntp_client_set_time_update_notify**: *SNTP 更新コールバックを設定します*
- **nx_sntp_client_stop**: *SNTP クライアント スレッドを停止します*
- **nx_sntp_client_utility_display_date_and_time**: *NTP 時刻を秒単位で表示します*
- **nx_sntp_client_utility_msecs_to_fraction**: *ミリ秒を NPT 時刻の小数部に変換します*
- **nx_sntp_client_utility_usecs_to_fraction**: *マイクロ秒を NTP 時刻の小数部に変換します*
- **nx_sntp_client_utility_fraction_to_usecs**: *NTP 時刻の小数部をミリ秒に変換します*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

SNTP クライアントを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>説明

このサービスでは、SNTP クライアント インスタンスを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **ip_ptr** クライアントの IP インスタンスへのポインター

- **iface_index** SNTP ネットワーク インターフェイスのインデックス

- **packet_pool_ptr** クライアントのパケット プールへのポインター

- **leap_second_handler** アプリケーションで間近な閏秒に対応するためのコールバック

- **kiss_of_death_handler** アプリケーションで受信した Kiss of Death パケットに対応するためのコールバック

- **random_number_generator** 乱数生成サービスのコールバック

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの作成に成功

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) ポインターではない無効な値の入力

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_INVALID_INTERFACE (0x4C) 無効なネットワーク インターフェイス

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

SNTP クライアントを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、SNTP クライアント インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの作成に成功

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

SNTP クライアントのローカル時刻を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>説明

このサービスでは、文字列メッセージ形式でデータを受信するためのオプション バッファーへのポインターの入力により、SNTP クライアントのローカル時刻を取得します。

このサービスは推奨されなくなりました。 開発者は *nx_sntp_client_get_local_time_extended*() に移行することを推奨します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **seconds** ローカル時刻の秒へのポインター

- **fraction** ローカル時刻の小数部

- **buffer** 時刻データを書き込むバッファーへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの作成に成功

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

SNTP クライアントの拡張ローカル時刻を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>説明

このサービスでは、文字列メッセージ形式でデータを受信するためのオプション バッファー ポインターの入力により、SNTP クライアントの拡張ローカル時刻を取得します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **seconds** ローカル時刻の秒へのポインター

- **fraction** 小数部へのポインター

- **buffer** 時刻データを書き込むバッファーへのポインター

- **buffer_size** バッファーの長さ

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの作成に成功

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

- NX_SIZE_ERROR (0x09) バッファーのサイズの確認に失敗

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

ブロードキャスト使用のためにクライアントを初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>説明

このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP 起動パラメーターとタイムアウト時間を初期化することによって、ブロードキャスト使用のためにクライアントを初期化します。 マルチキャスト アドレスとブロードキャスト アドレスがどちらも NULL でない場合は、マルチキャスト アドレスが選択されます。 どちらのアドレスも NULL である場合はエラーが返ります。 このサービスは IPv4 のサーバー アドレスのみをサポートしています。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **multicast_server_address** SNTP マルチキャスト アドレス

- **broadcast_time_server** SNTP サーバーのブロードキャスト アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの作成に成功

- **NX_INVALID_PARAMETERS** (0x4D) ポインターではない無効な値の入力

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

IPv4 または IPv6 ブロードキャスト使用のためにクライアントを初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>説明

このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP 起動パラメーターとタイムアウト時間を初期化することによって、ブロードキャスト使用のためにクライアントを初期化します。 ブロードキャスト アドレスとマルチキャスト アドレスへのポインターがどちらも NULL でない場合は、マルチキャストアドレスが選択されます。 どちらのアドレスへのポインターも NULL である場合はエラーが返ります。 このサービスは IPv4 と IPv6 アドレスを両方サポートしています。 IPv6 はブロードキャストをサポートしていないため、ブロードキャスト アドレスへのポインターを IPv6 に設定するとエラーが返ります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **multicast_server_address** SNTP サーバーのマルチキャスト アドレス

- **broadcast_server_address** SNTP サーバーのブロードキャスト アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの初期化に成功

- NX_SNTP_PARAM_ERROR (0xD0D) ポインターではない無効な値の入力

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効


### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

SNTP クライアントをユニキャストで実行するように設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>説明

このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP の起動パラメーターとタイムアウト時間を初期化することによって、ユニキャスト使用のためにクライアントを初期化します。 このサービスは IPv4 のサーバー アドレスのみをサポートしています。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **unicast_time_server** SNTP サーバーの IP アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの初期化に成功

- NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

SNTP クライアントを IPv4 または IPv6 ユニキャストで実行するように設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>説明

このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP の起動パラメーターとタイムアウト時間を初期化することによって、ユニキャスト使用のためにクライアントを初期化します。 このサービスは IPv4 と IPv6 アドレスを両方サポートしています。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **unicast_time_server** SNTP サーバーの IP アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントの初期化に成功

- NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

クライアントで有効な更新を受信しているかどうかを示します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>説明

このサービスでは、クライアントで有効な SNTP 更新を受信しているかどうかを示します。 有効な更新がないまま上限時間が経過するか、連続する無効な更新の受信が上限数を超えた場合、false の受信状態が返されます。 SNTP クライアントは引き続き稼働します。アプリケーションで、別のユニキャストまたはブロードキャスト/マルチキャスト サーバーを使用するように SNTP クライアントを再起動する必要がある場合、*nx_sntp_client_stop* サービスを使用して SNTP クライアントを停止し、いずれかの初期化サービスを用いて、別のサーバーを使用するようにクライアントを再初期化する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター。

- **receive_status** クライアントが有効な更新を受信しているかどうかを示す情報へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントで状態の更新の受信に成功

- NX_PTR_ERROR (0x07) 無効なポインターの入力

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

NTP サーバーにユニキャスト要求を直接送信します


### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>説明

アプリケーションでこのサービスを使用すると、SNTP クライアント スレッドのタスクから非同期で直接 NTP サーバーにユニキャスト要求を送信できます。 待機オプションで応答を待つ時間の長さを指定します。 操作に成功した場合、アプリケーションで、SNTP クライアントの他のサービスを使用して最新の時刻を取得できます。 詳細は「 **SNTP 非同期ユニキャスト要求** 」セクションをご覧ください。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター。

- **Wait_option** NTP 応答を待つ、タイマー刻み単位の待機時間。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントがユニキャスト更新の送受信に成功

- **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) クライアント スレッドを開始していません

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

クライアントをブロードキャスト モードで実行します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、クライアントをブロードキャスト モードで起動します。このモードでは、クライアントは SNTP サーバーからブロードキャストを受信するのを待ちます。 有効なブロードキャスト SNTP メッセージを受信すると、SNTP クライアントで更新を受け取らないまま経過した時間をカウントするタイムアウトのタイマーと、連続して受信した無効メッセージのカウントをリセットします。 それらいずれかの上限を超えた場合は、SNTP クライアントにおけるサーバーの状態の設定が無効に変更されますが、クライアントは引き続き更新の受信を待ちます。 アプリケーションでは、SNTP クライアントのタスクをポーリングしてサーバーの状態を確認し、それが無効であれば、SNTP クライアントを停止し、別の SNTP ブロードキャスト アドレスを使用して再初期化できます。 ユニキャスト SNTP サーバーに切り替えることもできます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **status** -------- 実際の完了ステータス

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) クライアントが起動済み

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) クライアントが初期化されていません

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

クライアントをユニキャスト モードで実行します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、クライアントをユニキャスト モードで起動します。このモードでは、クライアントから SNTP サーバーに定期的にユニキャスト要求を送信して時刻を更新します。 有効な SNTP メッセージを受信すると、SNTP クライアントで更新を受け取らないまま経過した時間をカウントするタイムアウトのタイマー、最初のポーリング間隔、連続して受信した無効メッセージのカウントをリセットします。 それらいずれかの上限を超えた場合は、SNTP クライアントにおけるサーバーの状態の設定が無効に変更されますが、クライアントは引き続きポーリングを行い、更新の受信を待ちます。 アプリケーションでは、SNTP クライアントのタスクをポーリングしてサーバーの状態を確認し、それが無効であれば、SNTP クライアントを停止し、別の SNTP ユニキャスト アドレスを使用して再初期化できます。 ブロードキャスト SNTP サーバーに切り替えることもできます。

.

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントをユニキャスト モードで起動することに成功

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) クライアントが起動済み

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) クライアントが初期化されていません

- NX_PTR_ERROR (0x07) 無効なポインターの入力

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

SNTP クライアントのローカル時刻を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>説明

このサービスでは、時刻の入力により SNTP クライアントのローカル時刻を設定します。たとえば、秒と “小数” (1 秒未満の時間を 16 進数で表現する形式) の SNTP 形式で設定します。 リアル タイム クロックなどの独立した時計から SNTP クライアントのローカル時刻を更新することを想定しています。 SNTP プロトコルでは、SNTP の時刻更新によって、ローカルの時計の時刻がずれるのを防ぐことを意図しています。 アプリケーションのデバイスに独立した時計がない場合は、SNTP サーバーによる時刻更新を唯一の入力として SNTP クライアントのローカル時刻を保つこともできますが、これは本来の方法とは異なります。

この API を使用して、SNTP クライアント スレッドの開始前に、SNTP クライアントに基準時間を与えることもできます。 SNTP クライアントのローカル時刻を受信した更新と比較することで、時刻データの有効性を確保します。 はじめて更新を受信するときは、とても大きなずれが存在する場合があります。 そのため、最初の更新におけるずれを SNTP クライアントで無視するオプションを用意しています。 そうすることで、SNTP クライアントを基準時間なしで起動できます。 入力する時刻は、既知のエポック時刻 (通常インターネットで利用可能) から取得でき、(新しい “エポック” が始まる 2036 年までは) 1900 年 1 月 1 日からの秒数として計算されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **seconds** 入力時刻の整数秒部分

- **fraction** 1 秒未満の部分 (SNTP 時刻の小数部の形式で表現されます)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ローカル時刻の設定に成功

- NX_PTR_ERROR (0x07) 無効なポインターの入力

### <a name="allowed-from"></a>許可元

初期化

### <a name="example"></a>例

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

SNTP 更新コールバックを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>説明

このサービスでは、SNTP クライアントが有効な時刻の更新を受信したときにアプリケーションに通知を行うコールバックを設定します。 SNTP メッセージのローカル時刻と SNTP クライアントのローカル時刻 (通常は同じ) を NTP 形式で通知します。 アプリケーションでは、NTP データを直接使用することも、*nx_sntp_client_utility_display_date_time サービス* を呼び出して人間が判読できる形式に時刻を変換することもできます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

- **time_update_cb** コールバック関数へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックの設定に成功

- NX_PTR_ERROR (0x07) 無効なポインターの入力

### <a name="allowed-from"></a>許可元

初期化

### <a name="example"></a>例

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

SNTP クライアント スレッドを停止します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、SNTP クライアント スレッドを停止します。 SNTP クライアント スレッドのタスク (無限ループで実行されます) ですべての反復処理を一時停止して SNTP クライアントの状態を制御することをやめさせ、アプリケーションが SNTP クライアントで API 呼び出しを実行できるようにします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SNTP クライアント制御ブロックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアント スレッドの停止に成功

- **NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP クライアント スレッドを開始していません

- NX_PTR_ERROR (0x07) 無効なポインターの入力

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

NTP 時刻を日付と時刻の文字列に変換します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>説明

このサービスでは、SNTP クライアントのローカル時刻を年月日形式に変換し、その日付を指定されたバッファーに返します。 NX_SNTP_CURRENT_YEAR は、クライアントの現在時刻と同じ年である必要はありませんが、指定する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr SNTP クライアントへのポインター**

- **buffer** 日付を保存するバッファーへのポインター

- **length** 入力バッファーのサイズ

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 変換に成功

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR を指定していないか、クライアントのローカル時刻を設定できていません

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) バッファーの長さが不足


### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

ミリ秒を NTP 時刻の小数部に変換します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>説明

このサービスでは、入力されるミリ秒を NTP 時刻の小数部に変換します。 SNTP クライアント用の開始基準時刻があるものの NTP の “整数秒+小数” 形式になっていないアプリケーションでの使用を意図しています。 有効な小数を作成するには、ミリ秒の数字が 1000 未満である必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **milliseconds 変換するミリ秒**

- **fraction** 小数に変換するミリ秒へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 変換に成功

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) 時刻から日付への変換のエラー

- NX_SNTP_INVALID_TIME (0xD30) 入力された SNTP データが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

マイクロ秒を NTP 時刻の小数部に変換します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>説明

このサービスでは、入力されるマイクロ秒を NTP 時刻の小数部に変換します。 SNTP クライアント用の開始基準時刻があるものの NTP の “整数秒+小数” 形式になっていないアプリケーションでの使用を意図しています。 有効な小数を作成するには、マイクロ秒の数字が 1000000 未満である必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **microseconds** 変換するマイクロ秒

- **fraction** 小数に変換するマイクロ秒へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 変換に成功

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) 時刻から日付への変換のエラー

- NX_SNTP_INVALID_TIME (0xD30) 入力された SNTP データが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

NTP 時刻の小数部をマイクロ秒に変換する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>説明

このサービスでは、入力される NTP 時刻小数部をマイクロ秒に変換します。

### <a name="input-parameters"></a>入力パラメーター

- **fraction 変換する小数**

- **microseconds** マイクロ秒に変換する小数へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 変換に成功

- NX_SNTP_INVALID_TIME (0xD30) 入力された SNTP データが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```