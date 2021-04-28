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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a><span data-ttu-id="a05b4-103">第 2 章 - Azure RTOS NetX Duo MQTT クライアントのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="a05b4-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo MQTT client</span></span>

<span data-ttu-id="a05b4-104">この章では、Azure RTOS NetX Duo MQTT クライアント コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="a05b4-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo MQTT client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="a05b4-105">製品ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="a05b4-105">Product Distribution</span></span>

<span data-ttu-id="a05b4-106">NetX Duo 用 MQTT クライアントは [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="a05b4-106">MQTT Client for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="a05b4-107">パッケージには、以下に示すように、2 つのソース ファイル、1 つのインクルード ファイル、およびこのドキュメントを含む 1 つのファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a05b4-107">The package includes two source files, one include file, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="a05b4-108">**nxd_mqtt_client.h**: NetX Duo 用 MQTT クライアントのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="a05b4-108">**nxd_mqtt_client.h** Header file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="a05b4-109">**nxd_mqtt_client.c**: NetX Duo 用 MQTT クライアントの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="a05b4-109">**nxd_mqtt_client.c** C Source file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="a05b4-110">**nxd_mqtt_client.pdf**: NetX Duo 用 MQTT クライアントの説明</span><span class="sxs-lookup"><span data-stu-id="a05b4-110">**nxd_mqtt_client.pdf** Description of MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="a05b4-111">**demo_mqtt_client.c**: NetX Duo MQTT デモンストレーション</span><span class="sxs-lookup"><span data-stu-id="a05b4-111">**demo_mqtt_client.c** NetX Duo MQTT demonstration</span></span>

## <a name="mqtt-client-installation"></a><span data-ttu-id="a05b4-112">MQTT クライアントのインストール</span><span class="sxs-lookup"><span data-stu-id="a05b4-112">MQTT Client Installation</span></span>

<span data-ttu-id="a05b4-113">NetX Duo 用 MQTT クライアントを使用するためには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-113">In order to use MQTT Client for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="a05b4-114">たとえば、NetX Duo が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、NetX Duo MQTT クライアントの *nxd_mqtt_client.h* と *nxd_mqtt_client.c* をこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-114">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_mqtt_client.h* and *nxd_mqtt_client.c* for NetX Duo MQTT Client need to be copied into this directory.</span></span>

## <a name="using-mqtt-client"></a><span data-ttu-id="a05b4-115">MQTT クライアントの使用</span><span class="sxs-lookup"><span data-stu-id="a05b4-115">Using MQTT Client</span></span>

<span data-ttu-id="a05b4-116">NetX Duo 用 MQTT クライアントは簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a05b4-116">Using MQTT Client for NetX Duo is easy.</span></span> <span data-ttu-id="a05b4-117">基本的には、ThreadX と NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_mqtt_client.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-117">Basically, the application code must include *nxd_mqtt_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX, and NetX Duo, respectively.</span></span> <span data-ttu-id="a05b4-118">MQTT クライアントのヘッダー ファイルがインクルードされると、このガイドで後述する MQTT サービスをアプリケーション コードで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-118">Once the MQTT Client header files are included, the application code is then able to use the MQTT services described later in this guide.</span></span> <span data-ttu-id="a05b4-119">アプリケーションでは、ビルド プロセスで *nxd_mqtt_client.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-119">The application must also include *nxd_mqtt_client.c* in the build process.</span></span> <span data-ttu-id="a05b4-120">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="a05b4-121">NetX Duo MQTT クライアントを使用するために必要なものはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="a05b4-121">This is all that is required to use NetX Duo MQTT Client.</span></span>

## <a name="using-mqtt-client-with-netx-secure-tls"></a><span data-ttu-id="a05b4-122">NetX Secure TLS での MQTT クライアントの使用</span><span class="sxs-lookup"><span data-stu-id="a05b4-122">Using MQTT Client with NetX Secure TLS</span></span>

<span data-ttu-id="a05b4-123">NetX Secure TLS モジュールで MQTT クライアントを使用するには、アプリケーションに NetX Secure TLS モジュールがインストールされていて、*nx_secure_tls_api.h* および *nx_crypto.h* がインクルードされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-123">To use MQTT client with NetX Secure TLS module, application must have NetX Secure TLS module installed, and include *nx_secure_tls_api.h* and *nx_crypto.h*.</span></span> <span data-ttu-id="a05b4-124">MQTT ライブラリは、シンボル ***NX_SECURE_ENABLE*** を定義して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-124">The MQTT library must be built with the symbol ***NX_SECURE_ENABLE*** defined.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="a05b4-125">構成オプション</span><span class="sxs-lookup"><span data-stu-id="a05b4-125">Configuration Options</span></span>

<span data-ttu-id="a05b4-126">NetX Duo 用 MQTT クライアントを構築するためのいくつかの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-126">There are several configuration options for building MQTT client for NetX Duo.</span></span> <span data-ttu-id="a05b4-127">すべてのオプションとそれぞれの詳細を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a05b4-127">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="a05b4-128">既定値が示されていますが、*nxd_mqtt_client.h* をインクルードする前に再定義することができます。</span><span class="sxs-lookup"><span data-stu-id="a05b4-128">The default values are listed, but can be redefined prior to inclusion of *nxd_mqtt_client.h.*</span></span>

- <span data-ttu-id="a05b4-129">**NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な MQTT クライアント エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="a05b4-129">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic MQTT client error checking.</span></span> <span data-ttu-id="a05b4-130">通常は、アプリケーションがデバッグされた後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a05b4-130">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="a05b4-131">**NX_SECURE_ENABLE**: 定義すると、MQTT クライアントは TLS サポート付きで構築されます。</span><span class="sxs-lookup"><span data-stu-id="a05b4-131">**NX_SECURE_ENABLE**: Defined, MQTT Client is built with TLS support.</span></span>
<span data-ttu-id="a05b4-132">このシンボルを定義するには、NetX Secure TLS モジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-132">Defining this symbol requires NetX Secure TLS module to be installed.</span></span>
<span data-ttu-id="a05b4-133">*NX_SECURE_ENABLE* は既定では有効になっていません。\*\*</span><span class="sxs-lookup"><span data-stu-id="a05b4-133">*NX_SECURE_ENABLE* is not enabled by default.\*\*</span></span>
- <span data-ttu-id="a05b4-134">**NXD_MQTT_REQUIRE_TLS**: 定義すると、アプリケーションは TLS を使用して MQTT ブローカーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-134">**NXD_MQTT_REQUIRE_TLS**: Defined, application must use TLS to connect to MQTT broker.</span></span> <span data-ttu-id="a05b4-135">この機能を使用するには、*NX_SECURE_ENABLE* が定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-135">This feature requires *NX_SECURE_ENABLE* defined.</span></span> <span data-ttu-id="a05b4-136">既定では、このシンボルは定義されません。</span><span class="sxs-lookup"><span data-stu-id="a05b4-136">By default, this symbol is not defined.</span></span>
- <span data-ttu-id="a05b4-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: 非推奨です。</span><span class="sxs-lookup"><span data-stu-id="a05b4-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="a05b4-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: 非推奨です。</span><span class="sxs-lookup"><span data-stu-id="a05b4-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="a05b4-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: MQTT タイマー レートを定義します (ThreadX タイマー ティック単位)。</span><span class="sxs-lookup"><span data-stu-id="a05b4-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Defines the MQTT timer rate, in ThreadX timer ticks.</span></span> <span data-ttu-id="a05b4-140">このタイマーは、最後の MQTT 制御メッセージが送信されてからの時間を追跡するために使用され、キープアライブ時間の有効期限が切れる前に MQTT PINGREQ メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="a05b4-140">This timer is used to keep track of the time since last MQTT control message was sent, and sends out an MQTT PINGREQ message before the keep-alive time expires.</span></span> <span data-ttu-id="a05b4-141">このタイマーは、クライアントがキープアライブ タイマー値を設定してブローカーに接続した場合にアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="a05b4-141">This timer is activated if the client connects to the broker with a keep-alive timer value set.</span></span> <span data-ttu-id="a05b4-142">既定値は TX_TIMER_TICKS_PER_SECOND で、これは 1 秒のタイマーです。</span><span class="sxs-lookup"><span data-stu-id="a05b4-142">The default value is TX_TIMER_TICKS_PER_SECOND, which is a one-second timer.</span></span>
- <span data-ttu-id="a05b4-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: MQTT クライアントが MQTT PINGREQ を送信した後にブローカーからの PINGRESP を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="a05b4-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Defines the time the MQTT client waits for PINGRESP from the broker after it sends out MQTT PINGREQ.</span></span> <span data-ttu-id="a05b4-144">このタイムアウト遅延後に PINGRESP が受信されなかった場合、クライアントはブローカーを無応答として扱い、ブローカーから自身を切断します。</span><span class="sxs-lookup"><span data-stu-id="a05b4-144">If no PINGRESP is received after this timeout delay, the client treats the broker as non-responsive and disconnects itself from the broker.</span></span> <span data-ttu-id="a05b4-145">既定の PING タイムアウト遅延は TX_TIMER_TICKS_PER_SECOND で、これは 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="a05b4-145">The default PING timeout delay is TX_TIMER_TICKS_PER_SECOND, which is one second.</span></span>
- <span data-ttu-id="a05b4-146">**NXD_MQTT_SOCKET_TIMEOUT**: MQTT サーバーから切断するときの TCP ソケット切断呼び出しのタイムアウトを定義します (タイマー ティック単位)。</span><span class="sxs-lookup"><span data-stu-id="a05b4-146">**NXD_MQTT_SOCKET_TIMEOUT**: Defines the time out in the TCP socket disconnect call when disconnecting from the MQTT server in timer ticks.</span></span> <span data-ttu-id="a05b4-147">既定値は NX_WAIT_FOREVER です。</span><span class="sxs-lookup"><span data-stu-id="a05b4-147">The default value is NX_WAIT_FOREVER.</span></span>

## <a name="sample-mqtt-program"></a><span data-ttu-id="a05b4-148">サンプル MQTT プログラム</span><span class="sxs-lookup"><span data-stu-id="a05b4-148">Sample MQTT program</span></span>

<span data-ttu-id="a05b4-149">次のプログラムは、単純な MQTT アプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="a05b4-149">The following program illustrates a simple MQTT application.</span></span> <span data-ttu-id="a05b4-150">わかりやすくするために、リターン コードは成功と見なされ、それ以上のエラー チェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="a05b4-150">For simplicity, the return codes are assumed to be successful, therefore no further error checking is done.</span></span>

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
