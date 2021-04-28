---
title: 第 2 章 - Azure RTOS NetX Duo MQTT クライアントのインストールと使用
description: この章では、NetX Duo MQTT クライアント コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cde19a0e84f369f1199ea4027fa09e6bd038e837
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810724"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>第 2 章 - Azure RTOS NetX Duo MQTT クライアントのインストールと使用

この章では、Azure RTOS NetX Duo MQTT クライアント コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

NetX Duo 用 MQTT クライアントは [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 パッケージには、以下に示すように、2 つのソース ファイル、1 つのインクルード ファイル、およびこのドキュメントを含む 1 つのファイルが含まれています。

- **nxd_mqtt_client.h**: NetX Duo 用 MQTT クライアントのヘッダー ファイル
- **nxd_mqtt_client.c**: NetX Duo 用 MQTT クライアントの C ソース ファイル
- **nxd_mqtt_client.pdf**: NetX Duo 用 MQTT クライアントの説明
- **demo_mqtt_client.c**: NetX Duo MQTT デモンストレーション

## <a name="mqtt-client-installation"></a>MQTT クライアントのインストール

NetX Duo 用 MQTT クライアントを使用するためには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、NetX Duo MQTT クライアントの *nxd_mqtt_client.h* と *nxd_mqtt_client.c* をこのディレクトリにコピーする必要があります。

## <a name="using-mqtt-client"></a>MQTT クライアントの使用

NetX Duo 用 MQTT クライアントは簡単に使用できます。 基本的には、ThreadX と NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_mqtt_client.h* をインクルードする必要があります。 MQTT クライアントのヘッダー ファイルがインクルードされると、このガイドで後述する MQTT サービスをアプリケーション コードで使用できるようになります。 アプリケーションでは、ビルド プロセスで *nxd_mqtt_client.c* もインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX Duo MQTT クライアントを使用するために必要なものはこれだけです。

## <a name="using-mqtt-client-with-netx-secure-tls"></a>NetX Secure TLS での MQTT クライアントの使用

NetX Secure TLS モジュールで MQTT クライアントを使用するには、アプリケーションに NetX Secure TLS モジュールがインストールされていて、*nx_secure_tls_api.h* および *nx_crypto.h* がインクルードされている必要があります。 MQTT ライブラリは、シンボル ***NX_SECURE_ENABLE*** を定義して構築する必要があります。

## <a name="configuration-options"></a>構成オプション

NetX Duo 用 MQTT クライアントを構築するためのいくつかの構成オプションがあります。 すべてのオプションとそれぞれの詳細を以下に示します。 既定値が示されていますが、*nxd_mqtt_client.h* をインクルードする前に再定義することができます。

- **NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な MQTT クライアント エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。
- **NX_SECURE_ENABLE**: 定義すると、MQTT クライアントは TLS サポート付きで構築されます。
このシンボルを定義するには、NetX Secure TLS モジュールをインストールする必要があります。
*NX_SECURE_ENABLE* は既定では有効になっていません。**
- **NXD_MQTT_REQUIRE_TLS**: 定義すると、アプリケーションは TLS を使用して MQTT ブローカーに接続する必要があります。 この機能を使用するには、*NX_SECURE_ENABLE* が定義されている必要があります。 既定では、このシンボルは定義されません。
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: 非推奨です。
- **NXD_MQTT_MAX_MESSAGE_LENGTH**: 非推奨です。
- **NXD_MQTT_KEEPALIVE_TIMER_RATE**: MQTT タイマー レートを定義します (ThreadX タイマー ティック単位)。 このタイマーは、最後の MQTT 制御メッセージが送信されてからの時間を追跡するために使用され、キープアライブ時間の有効期限が切れる前に MQTT PINGREQ メッセージを送信します。 このタイマーは、クライアントがキープアライブ タイマー値を設定してブローカーに接続した場合にアクティブになります。 既定値は TX_TIMER_TICKS_PER_SECOND で、これは 1 秒のタイマーです。
- **NXD_MQTT_PING_TIMEOUT_DELAY**: MQTT クライアントが MQTT PINGREQ を送信した後にブローカーからの PINGRESP を待機する時間を定義します。 このタイムアウト遅延後に PINGRESP が受信されなかった場合、クライアントはブローカーを無応答として扱い、ブローカーから自身を切断します。 既定の PING タイムアウト遅延は TX_TIMER_TICKS_PER_SECOND で、これは 1 秒です。
- **NXD_MQTT_SOCKET_TIMEOUT**: MQTT サーバーから切断するときの TCP ソケット切断呼び出しのタイムアウトを定義します (タイマー ティック単位)。 既定値は NX_WAIT_FOREVER です。

## <a name="sample-mqtt-program"></a>サンプル MQTT プログラム

次のプログラムは、単純な MQTT アプリケーションを示しています。 わかりやすくするために、リターン コードは成功と見なされ、それ以上のエラー チェックは行われません。

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
