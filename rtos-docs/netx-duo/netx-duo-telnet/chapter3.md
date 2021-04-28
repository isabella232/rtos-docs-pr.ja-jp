---
title: チャプター 3 - Azure RTOS NetX Duo Telnet のサービスの説明
description: このチャプターでは、Azure RTOS NetX Duo Telnet の全サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810529"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>チャプター 3 - Azure RTOS NetX Duo Telnet のサービスの説明

このチャプターでは、Azure RTOS NetX Duo Telnet の全サービス (以下に記載) をアルファベット順に説明します。

次の API の説明の「戻り値」セクションでは、API のエラー チェックを無効にする **NX_DISABLE_ERROR_CHECKING** の影響を受けない値を **太字** で示します。太字でない値は完全に無効になります。

- **nx_telnet_client_connect**: *Telnet クライアントを IPv4 アドレスで接続します*
- **nxd_telnet_client_connect**: *IPv6 Telnet クライアントを IPv6 アドレスで接続します*
- **nx_telnet_client_create**: *Telnet クライアントを作成します*
- **nx_telnet_client_delete**: *Telnet クライアントを削除します*
- **nx_telnet_client_disconnect**: *Telnet クライアントの接続を切断します*
- **nx_telnet_client_packet_receive**: *Telnet クライントを通じてパケットを受信します*
- **nx_telnet_client_packet_send**: *Telnet クライアントを通じてパケットを送信します*
- **nx_telnet_server_create**: *Telnet サーバーを作成します*
- **nx_telnet_server_delete**: *Telnet サーバーを削除します*
- **nx_telnet_server_disconnect**: *Telnet クライアントの接続を切断します*
- **nx_telnet_server_get_open_connection_count**: *有効な接続の数を取得します*
- **nx_telnet_server_packet_send**: *クライアント接続を通じてパケットを送信します*
- **nx_telnet_server_packet_pool_set**: *パケット プールを Telnet サーバーのパケット プールに設定します*
- **nx_telnet_server_start**: *Telnet サーバーを起動します*
- **nx_telnet_server_stop**: *Telnet サーバーを停止します*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

IPv4 アドレスを使用して Telnet クライアントを接続します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、作成済みの Telnet クライアント インスタンスを、指定した IPv4 アドレスとポートを使用して、Telnet サーバーに接続します。 このサービスでは、サーバーの IP アドレスを ULONG 型で NXD_ADDRESS 制御ブロックに挿入し、IP のバージョンを IPv4 に設定してから、次に説明する *nxd_telnet_client_connect* サービスを呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。
- **server_ip**: Telnet サーバーの IPv4 アドレス。
- **server_port**: サーバーの TCP ポート (Telnet サーバーはポート 23)。
- **wait_option**: このサービスで、Telnet クライントが接続するのを待つ時間を指定します。 待機オプションは次のように定義されています:

    - **タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限で一時停止します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアント接続に成功。
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) クライアントが接続済み。
- NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。
- NX_IP_ADDRESS_ERROR: (0x21) 無効な IP アドレス。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

IPv6 または IPv4 アドレスを使用して Telnet クライアントを接続します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、作成済みの Telnet クライアント インスタンスを、指定した IPv6 アドレスとポートを使用して Telnet サーバーに接続します。 このサービスでは、IPv4 または IPv6 アドレスを使用できますが、それが NXD_ADDRESS の *server_ip_address* 変数に入っている必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。
- **server_ip_address**: サーバーの IP アドレス。
- **server_port**: サーバーの TCP ポート (Telnet サーバーはポート 23)。
- **wait_option**: このサービスで、Telnet クライントが接続するのを待つ時間を指定します。 待機オプションは次のように定義されています:

    - **タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアント接続に成功。
- **NX_TELNET_ERROR**: (0xF0) クライアント接続エラー。
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) クライアントが接続済み。
- NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。
- NX_TELNET_INVALID_PARAMETER: (0xF5) ポインターではない無効な値の入力

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

Telnet クライアントを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>説明

このサービスでは、Telnet クライアント インスタンスを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。
- **client_name**: クライアント インスタンスの名前。
- **ip_ptr**: IP インスタンスへのポインター。
- **window_size**: このクライアントの TCP 受信ウィンドウのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントの作成に成功。
- **NX_TELNET_ERROR**: (0xF0) ソケット作成エラー。
- NX_PTR_ERROR: (0x07) 無効なクライアントまたは IP アドレスへのポインター。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

Telnet クライアントを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、作成済みの Telnet クライアント インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントの削除に成功。
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) クライアントが接続されたままです。
- NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

Telnet クライアントの接続を切断します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、接続済みの Telnet クライアント インスタンスの接続を切断します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。
- **wait_option**: このサービスで、Telnet クライアントの接続の切断を待つ時間を指定します。 待機オプションは次のように定義されています:

    - **タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアント接続切断に成功。
- **NX_TELNET_NOT_CONNECTED**: (0xF3) クライアントが未接続。
- NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Telnet クライアントを通じてパケットを受信します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、接続済みの Telnet クライアント インスタンスからパケットを受信します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。
- **packet_ptr**: 受信パケットの保存先へのポインター。
- **wait_option**: このサービスで、Telnet クライアントによりパケットを受信するのを待つ時間を指定します。 待機オプションは次のように定義されています:
    - **タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントによるパケットの受信に成功。
- NX_PTR_ERROR: (0x07) 無効なポインターの入力
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Telnet クライアントを通じてパケットを送信します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、接続済みの Telnet クライアント インスタンスを通じてパケットを送信します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: Telnet クライアント制御ブロックへのポインター。
- **packet_ptr**: 送信するパケットへのポインター。
- **wait_option**: このサービスで、Telnet クライアントからパケットが送信されるのを待つ時間を指定します。 待機オプションは次のように定義されています:
    - **タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントパケット送信に成功。
- **NX_TELNET_ERROR**: (0xF0) パケットの送信に失敗 – 呼び出し元がパケットを解放します。
- NX_PTR_ERROR: (0x07) 無効なポインターの入力
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Telnet サーバーを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>説明

このサービスでは、指定した IP インスタンスに Telnet サーバーを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。
- **server_name**: Telnet サーバー インスタンスの名前。
- **ip_ptr**: 関連付けられた IP インスタンスへのポインター。
- **stack_ptr**: サーバー内部のスレッド スタックへのポインター。
- **sack_size**: バイト単位のスタック サイズ。
- **new_connection**: アプリケーション コールバック ルーチン関数ポインター。 新しい Telnet クライアント接続要求をサーバーで検出するたびに、このルーチンを呼び出します。
- **receive_data**: アプリケーション コールバック ルーチン関数ポインター。 新しい Telnet クライアント データが接続に持ち込まれるたびに、このルーチンを呼び出します。 パケットの解放はこのルーチンによって行います。
- **end_connection**: アプリケーション コールバック ルーチン関数ポインター。 Telnet クライアントの接続がクライアントによって切断されるたびに、またはクライアント接続がタイムアウトする (“操作タイムアウト” になる) たびに、このルーチンを呼び出します。 サーバーでは、次に説明する *nx_telnet_server_disconnect* サービスを使用して接続を切断することもできます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) サーバーの作成に成功。
- NX_PTR_ERROR: (0x07) サーバー、IP アドレス、スタック、またはアプリケーション コールバックへのポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

Telnet サーバーを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>説明

このサービスでは、作成済みの Telnet サーバー インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) サーバーの削除に成功。
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

Telnet クライアントの接続を切断します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>説明

このサービスでは、この Telnet サーバー インスタンス上で接続済みのクライアントの接続を切断します。 このルーチンは通常、受信したデータで検出された状態へ応答として、アプリケーションの受信データ コールバック関数で呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。
- **logical_connection**: このサーバー上のクライアント接続に対応する論理接続。 有効な値の範囲は 0 - NX_TELENET_MAX_CLIENTS です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) サーバーの接続切断に成功。
- **NX_TELNET_ERROR**: (0xF0) サーバーの接続切断に失敗。
- NX_OPTION_ERROR: (0x0A) 無効な論理接続。
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

現在有効な接続の数を返します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>説明

このサービスでは、接続中の Telnet クライアントの数を返します。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。
- **Connection_count**: 接続数を保存するメモリへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 完了。
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

クライアント接続を通じてパケットを送信します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、この Telnet サーバー インスタンス上のクライアント接続にパケットを送信します。 このルーチンは通常、受信したデータで検出された状態へ応答として、アプリケーションの受信データ コールバック関数で呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。
- **logical_connection**: このサーバー上のクライアント接続に対応する論理接続。 有効な値の範囲は 0 - NX_TELENET_MAX_CLIENTS です。
- **packet_ptr**: 受信パケットへのポインター。
- **wait_option**: このサービスで、Telnet サーバーからパケットが送信されるのを待つ時間を指定します。 待機オプションは次のように定義されています:
    - **タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。 

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) パケットの送信に成功。
- **NX_TELNET_FAILED**: (0xF2) TCP ソケットによる送信に失敗。
- NX_OPTION_ERROR: (0x0A) 無効な論理接続。
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

作成済みのパケット プールを Telnet サーバーのパケット プールに設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>説明

このサービスでは、NX_TELNET_SERVER_USER_CREATE_PACKET_POOL が有効である場合、作成済みのパケット プールを Telnet サーバーのパケット プールに設定します。 また、このサービスを使用するには、X_TELNET_SERVER_OPTION_DISABLE が有効になっておらず、Telnet オプションを Telnet クライアントに送信するためのパケット プールが Telnet サーバーに必要であることも必要です。

このサービスにより、アプリケーションで、Telnet サーバーのスタック以外のメモリ (キャッシュ メモリ以外のメモリなど) にパケット プールを作成できるようになります。 この関数では、Telnet サーバーのパケット プールが既に設定されていないかどうかを確認しません。 Telnet サーバーのパケット プールへの NULL でないポインターでこれを呼び出した場合、入力したポインターが指し示すパケット プールで既存のパケット プールを置き換えて上書きします。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター
- **packet_pool_ptr**: 作成済みパケット プールへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) プールの設定に成功。
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。

### <a name="allowed-from"></a>許可元

Init、スレッド

### <a name="example"></a>例

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

Telnet サーバーを起動します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>説明

このサービスでは、作成済みの Telnet サーバー インスタンスを開始します。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 開始に成功。
- **NX_TELNET_NO_PACKET_POOL**: (0xF6) パケット プールが実設定
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Telnet サーバーを停止します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>説明

このサービスでは、作成・開始済みの Telnet サーバー インスタンスを停止します。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: Telnet サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 停止に成功
- NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```