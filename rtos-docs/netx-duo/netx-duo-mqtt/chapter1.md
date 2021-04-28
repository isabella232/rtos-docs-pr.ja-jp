---
title: 第 1 章 - Azure RTOS NetX Duo MQTT の概要
description: NetX Duo MQTT クライアント パッケージを使用するには、NetX Duo (バージョン 5.10 以降) がインストールされ、適切に構成されていることと、IP インスタンスが作成されていることが必要です。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810727"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a><span data-ttu-id="2271d-103">第 1 章 - Azure RTOS NetX Duo MQTT の概要</span><span class="sxs-lookup"><span data-stu-id="2271d-103">Chapter 1 - Introduction to Azure RTOS NetX Duo MQTT</span></span>

## <a name="netx-duo-mqtt-requirements"></a><span data-ttu-id="2271d-104">NetX Duo MQTT の要件</span><span class="sxs-lookup"><span data-stu-id="2271d-104">NetX Duo MQTT Requirements</span></span>

<span data-ttu-id="2271d-105">Azure RTOS NetX Duo MQTT クライアント パッケージを使用するには、NetX Duo (バージョン 5.10 以降) がインストールされて適切に構成されていて、IP インスタンスが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-105">The Azure RTOS NetX Duo MQTT client package requires that NetX Duo (version 5.10 or later) be installed, properly configured, and the IP instance has been created.</span></span> <span data-ttu-id="2271d-106">システムで TCP モジュールが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-106">The TCP module must be enabled in the system.</span></span> <span data-ttu-id="2271d-107">さらに、TLS セキュリティが必要な場合は、ブローカーが必要とするセキュリティ パラメーターに従って NetX Secure TLS モジュールを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-107">In addition, if TLS security is required, the NetX Secure TLS module needs to be configured according to the security parameter required by the broker.</span></span>

## <a name="netx-duo-mqtt-specification"></a><span data-ttu-id="2271d-108">NetX Duo MQTT の仕様</span><span class="sxs-lookup"><span data-stu-id="2271d-108">NetX Duo MQTT Specification</span></span>

<span data-ttu-id="2271d-109">NetX Duo MQTT クライアントの実装は、OASIS MQTT バージョン 3.1.1 (2014 年 10 月 29 日) に準拠しています。<sup></sup></span><span class="sxs-lookup"><span data-stu-id="2271d-109">NetX Duo MQTT client implement is compliant with OASIS MQTT Version 3.1.1 Oct 29<sup>th</sup> 2014.</span></span> <span data-ttu-id="2271d-110">この仕様は次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="2271d-110">The specification can be found at:</span></span>

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a><span data-ttu-id="2271d-111">NetX Duo MQTT の基本的な動作</span><span class="sxs-lookup"><span data-stu-id="2271d-111">NetX Duo MQTT Basic Operation</span></span>

<span data-ttu-id="2271d-112">MQTT (メッセージ キュー テレメトリ転送) は、パブリッシャー/サブスクライバー モデルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="2271d-112">MQTT (Message Queue Telemetry Transport) is based on publisher-subscriber model.</span></span> <span data-ttu-id="2271d-113">クライアントは、ブローカーを介して他のクライアントに情報を公開できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-113">A client can publish information to other clients through a broker.</span></span> <span data-ttu-id="2271d-114">クライアントは、トピックに関心がある場合、そのトピックをブローカーを通じてサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="2271d-114">A client, if interested in a topic, can subscribe to the topic through the broker.</span></span> <span data-ttu-id="2271d-115">ブローカーの役割は、公開されたメッセージを、トピックをサブスクライブしているクライアントに配信することです。</span><span class="sxs-lookup"><span data-stu-id="2271d-115">A broker is responsible for delivering published messages to its clients who subscribe to the topic.</span></span> <span data-ttu-id="2271d-116">このパブリッシャー/サブスクライバー モデルでは、複数のクライアントが同じトピックのデータを公開できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-116">In this publisher-subscriber model, multiple clients may publish data with the same topic.</span></span> <span data-ttu-id="2271d-117">クライアントは、同じトピックをサブスクライブしている場合、自身が公開するメッセージを受信することになります。</span><span class="sxs-lookup"><span data-stu-id="2271d-117">A client will receive a message it publishes if the client subscribes to the same topic.</span></span>

<span data-ttu-id="2271d-118">クライアントは、ユース ケースに応じて、メッセージの公開時に 3 つの QoS レベルのいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-118">Depending on the use case, a client may choose one of the 3 QoS levels when publishing a message:</span></span>

- <span data-ttu-id="2271d-119">**QoS 0**: メッセージは最大で 1 回配信されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-119">**QoS 0**: The message is delivered at most once.</span></span> <span data-ttu-id="2271d-120">QoS 0 で送信されるメッセージは失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-120">Messages sent with QoS 0 may be lost.</span></span>
- <span data-ttu-id="2271d-121">**QoS 1**: メッセージは少なくとも 1 回配信されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-121">**QoS 1**: The message is delivered at least once.</span></span> <span data-ttu-id="2271d-122">QoS 1 で送信されるメッセージは、複数回配信される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-122">Messages sent with QoS 1 may be delivered more than once.</span></span>
- <span data-ttu-id="2271d-123">**QoS 2**: メッセージは 1 回だけ配信されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-123">**QoS 2**: The message is delivered exactly once.</span></span> <span data-ttu-id="2271d-124">QoS 2 で送信されるメッセージは、重複することなく配信されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-124">Messages sent with QoS 2 is guaranteed to be delivered, with no duplication.</span></span>

> [!NOTE]
> <span data-ttu-id="2271d-125">この MQTT クライアントの実装では、QoS レベル 2 のメッセージはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2271d-125">This implementation of MQTT client does not support QoS level 2 messages.</span></span>

<span data-ttu-id="2271d-126">QoS 1 と QoS 2 では配信されることが保証されるため、ブローカーは、各クライアントに送信された QoS 1 と QoS 2 のメッセージの状態を追跡します。</span><span class="sxs-lookup"><span data-stu-id="2271d-126">Since QoS 1 and QoS 2 are guaranteed to be delivered, the broker keeps track the state of QoS 1 and QoS 2 messages sent to each client.</span></span> <span data-ttu-id="2271d-127">これは、QoS1 または QoS 2 のメッセージを想定しているクライアントにとって特に重要です。</span><span class="sxs-lookup"><span data-stu-id="2271d-127">This is particularly important for clients that expect QoS1 or QoS 2 messages.</span></span> <span data-ttu-id="2271d-128">クライアントは、(たとえば、クライアントが再起動したときや通信リンクが一時的に失われたときに) ブローカーから切断される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-128">The client may be disconnected from the broker (for example when the client reboots, or the communication link is temporarily lost).</span></span> <span data-ttu-id="2271d-129">ブローカーは、クライアントがブローカーに再接続されたらメッセージを配信できるように QoS 1 と QoS 2 のメッセージを格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-129">The broker must store QoS 1 and QoS 2 messages so the messages can be delivered later once the client is reconnected to the broker.</span></span> <span data-ttu-id="2271d-130">ただし、クライアントは、再接続後にブローカーから古いメッセージを受信しないことを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-130">However, the client may choose not to receive any stale messages from the broker after reconnection.</span></span> <span data-ttu-id="2271d-131">クライアントは、そのために、*clean_session* フラグを \***NX_TRUE** _ に設定して接続を開始します。</span><span class="sxs-lookup"><span data-stu-id="2271d-131">The client can do so by initiating the connection with the *clean_session* flag set to \***NX_TRUE** _.</span></span> <span data-ttu-id="2271d-132">この場合、ブローカーは、MQTT CONNECT メッセージの受信時に、未配信または未確認の QoS 1 または QoS 2 メッセージを含む、このクライアントに関連付けられたすべてのセッション情報を破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-132">In this case, upon receiving the MQTT CONNECT message, the broker shall discard any session information associated with this client, including undelivered or unconfirmed QoS 1 or QoS 2 messages.</span></span> <span data-ttu-id="2271d-133">_clean_session\* フラグが \***NX_FALSE**_ に設定されている場合、サーバーは QoS 1 および QoS 2 メッセージを再送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-133">If the _clean_session\* flag is to \***NX_FALSE**_, the server shall resend the QoS 1 and QoS 2 messages.</span></span> <span data-ttu-id="2271d-134">また、_clean_session\* が ***NX_TRUE*** に設定されている場合、MQTT クライアントは、未確認メッセージを再送信します。</span><span class="sxs-lookup"><span data-stu-id="2271d-134">The MQTT Client also resends any un-acknowledged messages if _clean_session\* is set to \***NX_TRUE\*.**</span></span> <span data-ttu-id="2271d-135">この受信確認は TCP 層の ACK とは異なりますが、同様に発生します。</span><span class="sxs-lookup"><span data-stu-id="2271d-135">This acknowledgment is different from the TCP layer ACK, although that happens as well.</span></span> <span data-ttu-id="2271d-136">MQTT クライアントは、受信確認をブローカーに送信します。</span><span class="sxs-lookup"><span data-stu-id="2271d-136">The MQTT client sends an acknowledgment to the broker.</span></span>

<span data-ttu-id="2271d-137">アプリケーションは、\***nxd_mqtt_client_create()** _ を呼び出して MQTT クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2271d-137">An application creates an MQTT client instance by calling \***nxd_mqtt_client_create()** _.</span></span> <span data-ttu-id="2271d-138">クライアントが作成されると、アプリケーションは _*_nxd_mqtt_client_connect()_*_ を呼び出すことによってブローカーに接続できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-138">Once the client is created, the application can connect to the broker by calling _*_nxd_mqtt_client_connect()_*_.</span></span> <span data-ttu-id="2271d-139">ブローカーに接続した後、クライアントは、_*_nxd_mqtt_client_subscribe()_*_ を呼び出してトピックをサブスクライブすることも、_\*_nxd_mqtt_client_publish()_ \*\* を呼び出してトピックを公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="2271d-139">After connecting to the broker, the client can subscribe to a topic by calling _*_nxd_mqtt_client_subscribe()_*_, or publish a topic by calling _\*_nxd_mqtt_client_publish()_\*\*.</span></span>

<span data-ttu-id="2271d-140">受信した MQTT メッセージは、MQTT クライアント インスタンスの受信キューに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-140">Incoming MQTT messages are stored in the receive queue in the MQTT client instance.</span></span> <span data-ttu-id="2271d-141">アプリケーションは、***nxd_mqtt_client_message_get()*** を呼び出すことによって、これらのメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="2271d-141">Application retrieves these message by calling ***nxd_mqtt_client_message_get()***.</span></span> <span data-ttu-id="2271d-142">受信キューにメッセージがある場合、キューの最初のメッセージ (たとえば、最も古いメッセージ) が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-142">If there are messages in the receive queue, the first message (e.g. the oldest) from the queue is returned to the caller.</span></span> <span data-ttu-id="2271d-143">メッセージのトピック文字列も返されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-143">The topic string from the message is also returned.</span></span>

> [!NOTE]
> <span data-ttu-id="2271d-144">MQTT クライアントの受信キューが空の場合、\***nxd_mqtt_client_message_get()** _ 関数はブロックされません。</span><span class="sxs-lookup"><span data-stu-id="2271d-144">The function \***nxd_mqtt_client_message_get()** _ does not block if the MQTT client receive queue is empty.</span></span> <span data-ttu-id="2271d-145">この関数は、リターン コード _*_NXD_MQTT_NO_MESSAGE_*\* と共に即座に返されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-145">The function returns immediately with the return code _\*_NXD_MQTT_NO_MESSAGE_\*\*.</span></span> <span data-ttu-id="2271d-146">アプリケーションでは、この戻り値を、エラーではなく、受信キューが空であることを示すものとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-146">The application shall treat this return value as an indication that the receive queue is empty, not an error.</span></span>

<span data-ttu-id="2271d-147">アプリケーションでは、受信メッセージ用の受信キューのポーリングを回避するために、***nxd_mqtt_client_recieve_notify_set()*** を呼び出すことによって、コールバック関数を MQTT クライアントに登録できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-147">To avoid polling the receive queue for incoming messages, the application can register a callback function with the MQTT client by calling ***nxd_mqtt_client_recieve_notify_set()***.</span></span> <span data-ttu-id="2271d-148">コールバック関数は次のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-148">The callback function is declared as:</span></span>

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

<span data-ttu-id="2271d-149">MQTT クライアントは、ブローカーからメッセージを受信すると、コールバック関数を呼び出します (関数が設定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="2271d-149">As the MQTT client receives messages from the broker, it invokes the callback function if the function is set.</span></span> <span data-ttu-id="2271d-150">このコールバック関数は、クライアント制御ブロックを指すポインターとメッセージ カウント値を渡します。</span><span class="sxs-lookup"><span data-stu-id="2271d-150">The callback function passes the pointer to the client control block and a message count value.</span></span> <span data-ttu-id="2271d-151">メッセージ カウント値は、受信キュー内の MQTT メッセージの数を示します。</span><span class="sxs-lookup"><span data-stu-id="2271d-151">The message count value indicates the number of MQTT messages in the receive queue.</span></span> <span data-ttu-id="2271d-152">このコールバック関数は MQTT クライアント スレッドのコンテキストで実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2271d-152">Note that this callback function executes in the MQTT client thread context.</span></span> <span data-ttu-id="2271d-153">そのため、コールバック関数では、MQTT クライアント スレッドをブロックする可能性のあるプロシージャは実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="2271d-153">Therefore, the callback function should not execute any procedures that may block the MQTT client thread.</span></span> <span data-ttu-id="2271d-154">コールバック関数により、***nxd_mqtt_client_message_get()*** を呼び出してメッセージを取得するアプリケーション スレッドがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="2271d-154">The callback function should trigger the application thread to call ***nxd_mqtt_client_message_get()*** to retrieve the messages.</span></span>

<span data-ttu-id="2271d-155">MQTT クライアント サービスを切断して終了するには、アプリケーションでサービスの ***nxd_mqtt_client_disconnect()** _ と _*_nxd_mqtt_client_delete()_\*_ を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-155">To disconnect and terminate the MQTT client service, the application shall use the service ***nxd_mqtt_client_disconnect()** _ and _*_nxd_mqtt_client_delete()._\*_</span></span> <span data-ttu-id="2271d-156">_*_nxd_mqtt_client_disconnect()_*_ を呼び出した場合は、ブローカーへの TCP 接続が切断されるだけです。</span><span class="sxs-lookup"><span data-stu-id="2271d-156">Calling _*_nxd_mqtt_client_disconnect()_*_ simply disconnects the TCP connection to the broker.</span></span> <span data-ttu-id="2271d-157">既に受信されて受信キューに格納されているメッセージは解放されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-157">It releases messages already received and stored in the receive queue.</span></span> <span data-ttu-id="2271d-158">ただし、送信キューにある QoS レベル 1 のメッセージは解放されません。</span><span class="sxs-lookup"><span data-stu-id="2271d-158">However, it does not release QoS level 1 messages in the transmit queue.</span></span> <span data-ttu-id="2271d-159">QoS レベル 1 のメッセージは、接続時に再送信されます (_*_clean_session_*_ フラグが _ *_NX_FALSE_*\* に設定されていると想定)。</span><span class="sxs-lookup"><span data-stu-id="2271d-159">QoS level 1 messages are retransmitted upon connection, assuming the _*_clean_session_*_ flag is set to _ *_NX_FALSE._*\*</span></span>

<span data-ttu-id="2271d-160">ブローカーは、クライアントから切断することもできます。</span><span class="sxs-lookup"><span data-stu-id="2271d-160">The broker may also disconnect from the client.</span></span> <span data-ttu-id="2271d-161">クライアントとブローカーの間の TCP 接続が終了すると、切断通知機能でアプリケーションに通知できます。</span><span class="sxs-lookup"><span data-stu-id="2271d-161">When the TCP connection between the client and the broker is terminated, the application can be notified by the disconnect notify function.</span></span> <span data-ttu-id="2271d-162">この通知メカニズムを使用するには、アプリケーションで ***nxd_mqtt_client_disconnect_notify_set*** を呼び出して、切断通知機能をインストールします。</span><span class="sxs-lookup"><span data-stu-id="2271d-162">To use the notification mechanism, application installs the disconnect notify function by calling \***nxd_mqtt_client_disconnect_notify_set\*.**</span></span> <span data-ttu-id="2271d-163">TCP 切断が確認され、MQTT セッションが作成されていると、通知機能が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-163">Once a TCP disconnect is observed and the MQTT session has been created, the notification function is invoked.</span></span>

<span data-ttu-id="2271d-164">***nxd_mqtt_client_delete()*** を呼び出すと、送信キューと受信キュー内のすべてのメッセージ ブロックが解放されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-164">Calling ***nxd_mqtt_client_delete()*** releases all message blocks in the transmit queue and the receive queue.</span></span> <span data-ttu-id="2271d-165">未確認の QoS レベル 1 のメッセージも削除されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-165">Unacknowledged QoS level 1 messages are also deleted.</span></span>

## <a name="secure-mqtt-connection"></a><span data-ttu-id="2271d-166">セキュリティで保護された MQTT 接続</span><span class="sxs-lookup"><span data-stu-id="2271d-166">Secure MQTT Connection</span></span>

<span data-ttu-id="2271d-167">MQTT クライアントは、NetX Secure TLS モジュールを使用して、ブローカーへのセキュリティで保護された接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="2271d-167">The MQTT client makes a secure connection to the broker using the NetX Secure TLS module.</span></span> <span data-ttu-id="2271d-168">TLS セキュリティを使用する MQTT の既定のポート番号は 8883 で、***NXD_MQTT_TLS_PORT*** で定義されています。</span><span class="sxs-lookup"><span data-stu-id="2271d-168">The default port number for MQTT with TLS security is 8883, defined in ***NXD_MQTT_TLS_PORT***.</span></span>

<span data-ttu-id="2271d-169">ブローカーへのセキュリティで保護された MQTT 接続を作成するには、TCP 接続が確立されてから MQTT CONNECT メッセージをブローカーに送信するまでに、TLS セッションをネゴシエートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2271d-169">To create a secure MQTT connection to the broker, a TLS session needs to be negotiated after a TCP connection is established, before MQTT CONNECT messages can be sent to the broker.</span></span> <span data-ttu-id="2271d-170">TLS セッションの設定を行うには、***nxd_mqtt_client_secure_connect()*** を呼び出し、ユーザー定義の TLS 設定コールバック関数を渡します。</span><span class="sxs-lookup"><span data-stu-id="2271d-170">The TLS session set up is accomplished by calling ***nxd_mqtt_client_secure_connect()*** and passing in a user-defined TLS setup callback function.</span></span> <span data-ttu-id="2271d-171">MQTT 接続フェーズでは、TCP 接続が確立されると、クライアントが TLS 設定コールバック関数を呼び出して、適切な TLS ハンドシェイク プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="2271d-171">During the MQTT connection phase, once the TCP connection is established, the client invokes the TLS setup callback function to start a proper TLS handshake process.</span></span> <span data-ttu-id="2271d-172">TLS セッションが確立された後、クライアントは、セキュリティで保護されたチャネルを介して MQTT CONNECT メッセージを続行します。</span><span class="sxs-lookup"><span data-stu-id="2271d-172">After the TLS session is established, the client continues the MQTT CONNECT message over the secure channel.</span></span>

<span data-ttu-id="2271d-173">ユーザー定義のコールバック関数は、5 つの入力値を受け取り、次のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-173">The user defined callback function takes five input values and is declared as:</span></span>

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

<span data-ttu-id="2271d-174">入力パラメーターの説明を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2271d-174">Below is a description of the input parameters:</span></span>

- <span data-ttu-id="2271d-175">**client_ptr**: MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="2271d-175">**client_ptr**: Pointer to the MQTT client control block.</span></span>
- <span data-ttu-id="2271d-176">**session_ptr**: TLS セッション制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="2271d-176">**session_ptr**: Pointer to the TLS session control block.</span></span>
- <span data-ttu-id="2271d-177">**certificate_ptr**: 証明書制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="2271d-177">**certificate_ptr**: Pointer to the certificate control block.</span></span> <span data-ttu-id="2271d-178">この証明書は、ブローカーに送信される前に設定関数によって構成されます。</span><span class="sxs-lookup"><span data-stu-id="2271d-178">The setup function configures this certificate before sending it to the broker.</span></span>
- <span data-ttu-id="2271d-179">**trusted_certificate_ptr**: 信頼できる証明書を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="2271d-179">**trusted_certificate_ptr**: Pointer to the trusted certificate.</span></span> <span data-ttu-id="2271d-180">TLS 設定関数は、サーバーを認証するために信頼できる証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="2271d-180">TLS setup function configures the trusted certificate to authenticate the server.</span></span>

<span data-ttu-id="2271d-181">この TLS 設定関数において、アプリケーションの役割は、TLS セッションを作成し、適切な証明書を使用してそのセッションを構成することです。</span><span class="sxs-lookup"><span data-stu-id="2271d-181">In the TLS setup function, the application is responsible for creating a TLS session, and configuring the session with a proper certificate.</span></span> <span data-ttu-id="2271d-182">次の擬似コードは、一般的な TLS セッションの開始手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="2271d-182">The following pseudo code outlines a typical TLS session start up procedure.</span></span> <span data-ttu-id="2271d-183">TLS API シリーズの使用の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2271d-183">The reader is referred to the NetX Secure TLS User Guide for details on using TLS APIs.</span></span>

<span data-ttu-id="2271d-184">TLS 設定コールバックの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2271d-184">Below is an example TLS setup callback:</span></span>

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a><span data-ttu-id="2271d-185">NetX Duo MQTT クライアントの既知の制限事項</span><span class="sxs-lookup"><span data-stu-id="2271d-185">Known Limitations of the NetX Duo MQTT Client</span></span>

- <span data-ttu-id="2271d-186">NetX Duo MQTT では、QoS レベル 2 のメッセージの送受信がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2271d-186">NetX Duo MQTT does not support sending or receiving QoS level 2 messages.</span></span>
- <span data-ttu-id="2271d-187">NetX Duo MQTT では、連鎖パケットがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2271d-187">NetX Duo MQTT does not support chained-packets.</span></span>
