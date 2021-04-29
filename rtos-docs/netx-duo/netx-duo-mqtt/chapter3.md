---
title: 第 3 章 - Azure RTOS NetX Duo MQTT クライアント サービスの説明
description: この章では、すべての NetX Duo MQTT クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810712"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>第 3 章 - Azure RTOS NetX Duo MQTT クライアント サービスの説明

この章では、すべての Azure RTOS NetX Duo MQTT クライアント サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nxd_mqtt_client_create** *MQTT クライアントインスタンスを作成します*
- **nxd_mqtt_client_will_message_set** *will メッセージを設定します*
- **nxd_mqtt_client_client_login_set** *et MQTT クライアントのログインのユーザー名とパスワードを設定します*
- **nxd_mqtt_client_connect** *MQTT クライアントをブローカーに接続します*
- **nxd_mqtt_client_secure_connect** *TLS セキュリティを使用して MQTT クライアントをブローカーに接続します*
- **nxd_mqtt_client_publish** *ブローカーを介してメッセージを発行します。*
- **nxd_mqtt_client_subscribe** *トピックをサブスクライブします*
- **nxd_mqtt_client_unsubscribe** *トピックをサブスクライブ解除します*
- **nxd_mqtt_client_receive_notify_set** *MQTT メッセージ受信通知コールバック関数を設定します*
- **nxd_mqtt_client_message_get** *ブローカーからメッセージを取得します*
- **nxd_mqtt_client_disconnect_notify_set** *MQTT メッセージ切断通知コールバック関数を設定します*
- **nxd_mqtt_client_disconnect** *ブローカーから MQTT クライアントを切断します*
- **nxd_mqtt_client_delete** *MQTT クライアント インスタンスを削除します*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

MQTT クライアント インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンス上に MQTT クライアント インスタンスが作成されます。 *client_id* の文字列は、MQTT 接続フェーズの間に "*クライアント識別子 (ClientId)* " としてサーバーに渡されます。 また、必要な ThreadX リソース (MQTT クライアント タスク スレッド、ミューテックス、イベント フラグ グループ、TCP ソケット) も作成されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **client_name** クライアント名の文字列。
- **client_id** 接続フェーズの間に使用されるクライアント ID 文字列。 MQTT ブローカーにより、この client_id を使用してクライアントが一意に識別されます。
- **client_id_length** クライアント ID 文字列の長さ (バイト単位)。
- **ip_ptr** IP インスタンスへのポインター。
- **pool_ptr** MQTT クライアントによって操作に使用されるパケット プールへのポインター。
- **stack_ptr** MQTT クライアント スレッド用のスタック領域。
- **stack_size** スタック領域のサイズ (バイト単位)。
- **mqtt_thread_priority** MQTT スレッドの優先順位。
- **memory_ptr** 非推奨。 使用されなくなりました。
- **memory_size** 非推奨。 使用されなくなりました。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) MQTT クライアントが正常に作成されました。
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー
- NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です。
- NXD_MQTT_INVALID_PARAMETER (0x10009) will トピック文字列、will_retrain_flag、または will_QoS 値が無効です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

will メッセージを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>説明

このサービスを使用すると、クライアントがサーバーに接続する前に、オプションの will トピックと Will メッセージが設定されます。 will トピックは、UTF-8 でエンコードされた文字列である必要があります。

will メッセージは (設定されている場合)、CONNECT メッセージの一部としてブローカーに送信されます。 したがって、will メッセージを使用するアプリケーションは、MQTT 接続を行う前に、このサービスを使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **will_topic** UTF-8 でエンコードされた will トピックの文字列。 will トピックが存在する必要があります。 呼び出し元は、*nx_mqtt_client_connect* の呼び出しが行われるまで、will_topic の文字列を有効な状態に保つ必要があります。
- **will_topic_length** will トピックの文字列のバイト数
- **will_message** アプリケーションで定義された will メッセージ。 will メッセージが必要ない場合は、アプリケーションでこのフィールドを *NX_NULL* に設定できます。
- **will_message_length** will メッセージ文字列のバイト数。 will_message が NULL に設定されている場合は、will_message_length を 0 に設定する必要があります。
- **will_retain_flag** サーバーで will メッセージが保持メッセージとして発行されるかどうか。 有効な値は、*NX_TRUE* または *NX_FALSE* です。
- **will_QoS** will メッセージの送信時にサーバーによって使用される QoS 値。 有効な値は 0 または 1 です。  

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) will メッセージは正常に設定されました。
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS レベル 2 メッセージはサポートされていません。
- NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。
- NXD_MQTT_INVALID_PARAMETER (0x10009) will トピック文字列、will_retrain_flag、または will_QoS 値が無効です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

MQTT クライアント ログインのユーザー名とパスワードを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>説明

このサービスを使用すると、MQTT 接続フェーズの間にログイン認証のために使用されるユーザー名とパスワードが設定されます。

ユーザー名とパスワードを使用した MQTT クライアント ログインはオプションです。 サーバーでユーザー名とパスワードが必要な場合は、接続が確立される前にユーザー名とパスワードを設定する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **username** UTF-8 でエンコードされたユーザー名の文字列。 呼び出し元は、*nx_mqtt_client_connect* の呼び出しが行われるまで、username の文字列を有効な状態に保つ必要があります。
- **username_length** ユーザー名の文字列のバイト数
- **password** パスワードの文字列。 パスワードが必要ない場合は、このフィールドを NX_NULL に設定できます。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) will メッセージは正常に設定されました。
- NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。
- NXD_MQTT_INVALID_PARAMETER (0x10009) ユーザー名またはパスワードの文字列が無効です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

MQTT クライアントをブローカーに接続します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>説明

このサービスを使用すると、ブローカーへの接続が開始されます。 最初に、TCP ソケットへのバインドが行われた後、TCP 接続が確立されます。 成功すると、MQTT キープ アライブ機能が有効になっている場合はタイマーが作成されます。 その後、MQTT サーバー (ブローカー) と接続されます。

このサービスによって作成される MQTT 接続は、TLS で保護されていないことに注意してください。 セキュリティで保護された MQTT 接続を作成するには、アプリケーションでサービス ***nxd_mqtt_client_secure_connect()*** を使用する必要があります。

接続時に、クライアントによって *clean_session* が NX_FALSE に設定されると、まだ受信確認されていないメッセージがクライアントによって再送信されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **server_ip** ブローカーの IP アドレス。
- **server_port** ブローカーのポート番号。 MQTT の既定のポートは、**_NXD_MQTT_PORT_** (1883) として定義されています。
- **keep_alive** セッションの間に使用されるキープ アライブの値 (秒単位)。 この値は、ブローカーによってこのクライアントがタイムアウトされることのない、ブローカーに送信される 2 つの MQTT 制御メッセージ間の最大時間を示します。 値 0 は、キープ アライブ機能がオフになります。
- **clean_session** サーバーがこのセッションをクリーンに開始する必要があるかどうか。 有効なオプションは、**_NX_TRUE_ *_ または _* _NX_FALSE_** です。
- **wait_option** 接続の待機時間。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) MQTT の接続が成功しました
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) クライアントは既にブローカーに接続されています。
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) ブローカーに接続できませんでした。
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) サーバーがエラーで応答しました
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) サーバーの応答コード
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) サーバーの応答コード
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) サーバーの応答コード
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) サーバーの応答コード
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) サーバーの応答コード
- NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

TLS セキュリティを使用して MQTT クライアントをブローカーに接続します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>説明

このサービスは ***nxd_mqtt_client_connect*** と同じですが、TCP ではなく TLS レイヤー経由で接続が行われる点が異なります。 したがって、クライアントとブローカーの間の通信はセキュリティで保護されます。

ユーザー定義の *tls_setup* は、MQTT クライアント接続を行う前に MQTT クライアントによって使用されるコールバック関数です。 アプリケーションで、NetX Secure TLS を初期化し、セキュリティ パラメーターを構成して、TLS ハンドシェイクの間に使用される関連する証明書を読み込む必要があります。 実際の TLS ハンドシェイクは、ブローカーの MQTT TLS ポート (既定の TCP ポート 8883) で TCP 接続が確立された後に発生します。 TLS ハンドシェイクが成功すると、MQTT CONNECT 制御パケットが TLS 経由で送信されます。

セキュリティで保護された接続を行うには、NetX Secure TLS ライブラリが使用可能であり、NetX Duo MQTT クライアントが ***NX_SECURE_ENABLE*** を定義してビルドされている必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **server_ip** ブローカーの IP アドレス。
- **server_port** ブローカーのポート番号。 MQTT の既定のポートは、**_NXD_MQTT_TLS_PORT_** (8883) として定義されています。
- **tls_setup** ユーザーが提供する TLS セットアップ コールバック関数。 このコールバック関数は、TLS クライアントの接続パラメーターを設定するために呼び出されます。
- **keep_alive** セッションの間に使用されるキープ アライブの値。 値 0 は、キープ アライブ機能がオフになります。
- **clean_session** サーバーがこのセッションをクリーンに開始する必要があるかどうか。 有効なオプションは、**_NX_TRUE_ *_ または _* _NX_FALSE_** です。
- **wait_option** 接続の待機時間。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) TLS を使用して MQTT クライアント接続が正常に確立されました。
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) クライアントは既にブローカーに接続されています。
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) ブローカーに接続できませんでした。
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) サーバーがエラー メッセージで応答しました。
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) サーバーの応答コード
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) サーバーの応答コード
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) サーバーの応答コード
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) サーバーの応答コード
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) サーバーの応答コード
- NX_PTR_ERROR (0x07) MQTT コントロール ブロックまたはサーバー アドレスの構造が無効です。
- NX_INVALID_PORT (0x46) サーバー ポートを 0 にすることはできません。
- NXD_MQTT_INVALID_PARAMETER (0x10009) 入力パラメーター エラー
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT スレッドの実行はまだ開始されていません。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

ブローカーを介してメッセージを発行します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>説明

このサービスを使用すると、ブローカーを介してメッセージが発行されます。 QoS レベル 2 のメッセージの発行はまだサポートされていません。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **topic_name** 発行先のトピック。
- **topic_name_length** トピックの長さ (バイト単位)。
- **message** メッセージ バッファーへのポインター。
- **message_length** メッセージのサイズ (バイト単位)
- **retain** ブローカーでメッセージを保持する必要があるかどうかを決定します。
- **QoS** 必要な QoS 値: 0 または 1。
- **timeout** タイムアウト値

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) MQTT クライアントが正常に作成されました
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー。
- **NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) パケット プールからパケットを取得できませんでした。
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーとの通信に失敗しました。
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS レベル 2 メッセージはサポートされていません。
- NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です
- NXD_MQTT_INVALID_PARAMETER (0x10009) 入力パラメーター エラー

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

トピックのサブスクライブ

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>説明

このサービスを使用すると、特定のトピックがサブスクライブされます。 QoS レベル 2 のメッセージのサブスクライブはまだサポートされていません。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **topic_name** 発行先のトピック。
- **topic_name_length** トピックの長さ (バイト単位)。
- **QoS** 必要な QoS レベル: 0 または 1。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) トピックが正常にサブスクライブされました。
- **NXD_MQTT_NOT_CONNECTED** (0x10002) クライアントがブローカーに接続されていません。
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS レベル 2 メッセージはサポートされていません。
- NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name が設定されていないか、topic_name_length が 0 であるか、QoS の値が無効です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

トピックのサブスクライブを解除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>説明

このサービスを使用すると、トピックのサブスクライブが解除されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **topic_name** サブスクライブを解除するトピック。
- **topic_name_length** トピックの長さ (バイト単位)。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) トピックのサブスクライブが正常に解除されました。
- **NXD_MQTT_NOT_CONNECTED** (0x10002) クライアントがブローカーに接続されていません。
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした。
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。
- NX_PTR_ERROR (0x07) MQTT 制御ブロック ポインターが無効です
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name が設定されていないか、topic_name_length が 0 です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

MQTT メッセージ受信通知コールバック関数を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>説明

このサービスを使用すると、コールバック関数が MQTT クライアントに登録されます。 ブローカーによって発行されたメッセージを受信すると、メッセージは MQTT クライアントにより受信キューに格納されます。 コールバック関数が設定されている場合は、コールバック関数が呼び出されて、メッセージを取得する準備ができたことがアプリケーションに通知されます。 受信通知関数は、MQTT クライアント制御ブロックへのポインターと、受信キューで使用できるメッセージの数を示す *message_count* を受け取ります。 この値は、受信通知から、アプリケーションでこれらのメッセージを取得するまでの間に、変わる可能性があることに注意してください。これは、その間に新しいメッセージが到着する可能性があるためです。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **receive_notify** メッセージの受信時に呼び出される、ユーザー提供のコールバック関数。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) 受信通知関数が正常に設定されました。
- NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

ブローカーからメッセージを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>説明

このサービスを使用すると、ブローカーによって発行されたメッセージが取得されます。 着信したメッセージはすべて受信キューに格納されます。 アプリケーションでは、このサービスを使用してこれらのメッセージを取得します。 この呼び出しは非ブロックです。 受信キューが空の場合、このサービスからは ***NXD_MQTT_NO_MESSAGE** _ が返されます。 受信メッセージの通知を希望するアプリケーションは、サービスの _ *_nxd_mqtt_client_receive_notify_set_** を呼び出して、受信コールバック関数を登録できます。

呼び出し元は、トピック文字列とメッセージ本文のためのメモリ領域を提供する必要があります。 これら 2 つのバッファーのサイズは、*topic_buffer_size* と *message_buffer_size* を使用して渡します。 トピック文字列とメッセージ本文の実際のバイト数は、*actual_topic_length* と *actual_message_length* で返されます。 トピックの長さまたはメッセージの長さが指定したバッファー領域より大きい場合は、このサービスからエラー コード *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE* が返されます。

アプリケーションで、より大きなバッファーを割り当ててから再試行する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **topic_buffer** トピック文字列のコピー先のメモリ位置へのポインター。
- **topic_buffer_size** トピック バッファーのサイズ。
- **actual_topic_length** 実際のトピック長が返されるメモリ位置へのポインター。
- **message_buffer** メッセージ文字列のコピー先のメモリ位置へのポインター。
- **message_buffer_size** メッセージ バッファーのサイズ。
- **actual_message_length** メッセージ長が返されるメモリ位置へのポインター。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) メッセージが正常に取得されました。
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー
- **NXD_MQTT_NO_MESSAGE** (0x1000A) 受信キューが空です。
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) トピック バッファーまたはメッセージ バッファーが、トピックまたはメッセージに対して小さすぎます。
- NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer または topic_buffer のポインターが NULL です

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

MQTT メッセージ切断通知コールバック関数を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>説明

このサービスを使用すると、コールバック関数が MQTT クライアントに登録されます。 MQTT によってブローカーへの接続が失われたことが検出されると、この通知関数が呼び出されて、アプリケーションに警告されます。 このため、アプリケーションでこのコールバック関数を使用して失われた接続を検出し、ブローカーへの接続を再確立することができます。

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。
- **disconnect_notify** MQTT によってブローカーへの接続が失われたことが検出されたときに呼び出されるユーザー提供のコールバック関数。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) 切断通知関数が正常に設定されました。
- NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

ブローカーから MQTT クライアントを切断します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、ブローカーからクライアントが切断されます。 受信キューにあるメッセージは解放されることに注意してください。 送信キュー内の QoS 1 のメッセージは解放されません。 クライアントが *clean_session* フラグを ***NX_TRUE*** に設定してサーバーに再接続しない限り、クライアントがサーバーに再接続した後で、QoS 1 のメッセージを処理できます。

TLS セキュリティ保護を使用して接続が行われた場合、TCP 接続が切断される前に、このサービスによって TLS セッションが閉じられます。

実際の TCP ソケット切断呼び出しには、NXD_MQTT_SOCKET_TIMEOUT (タイマー ティック) によって待機オプションが定義されています。 既定値は NX_WAIT_FOREVER です。 ネットワーク接続が失われたり、サーバーが応答していない場合に、無限の中断を回避するには、このオプションを有限の値に設定します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) がブローカーから正常に切断されました
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした。
- NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

MQTT クライアントのインスタンスを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、MQTT クライアント インスタンスが削除され、内部リソースが解放されます。 クライアントがまだ接続されている場合、このサービスによりブローカーから自動的に切断されます。 まだ送信されていない、または受信確認されていないメッセージは解放されます。 受信されたがアプリケーションによって取得されていないメッセージも解放されます。

TLS セキュリティ保護を使用して接続が行われた場合、TCP 接続が切断される前に、このサービスによって TLS セッションが閉じられます。

クライアントが削除された後、MQTT サービスの使用を望むアプリケーションは、新しいインスタンスを作成する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** MQTT クライアント制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NXD_MQTT_SUCCESS** (0x00) MQTT クライアントが正常に削除されました。
- NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
