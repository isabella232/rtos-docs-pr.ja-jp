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
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="18141-103">第 3 章 - Azure RTOS NetX Duo MQTT クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="18141-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="18141-104">この章では、すべての Azure RTOS NetX Duo MQTT クライアント サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="18141-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="18141-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="18141-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="18141-106">**nxd_mqtt_client_create** *MQTT クライアントインスタンスを作成します*</span><span class="sxs-lookup"><span data-stu-id="18141-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="18141-107">**nxd_mqtt_client_will_message_set** *will メッセージを設定します*</span><span class="sxs-lookup"><span data-stu-id="18141-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="18141-108">**nxd_mqtt_client_client_login_set** *et MQTT クライアントのログインのユーザー名とパスワードを設定します*</span><span class="sxs-lookup"><span data-stu-id="18141-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="18141-109">**nxd_mqtt_client_connect** *MQTT クライアントをブローカーに接続します*</span><span class="sxs-lookup"><span data-stu-id="18141-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="18141-110">**nxd_mqtt_client_secure_connect** *TLS セキュリティを使用して MQTT クライアントをブローカーに接続します*</span><span class="sxs-lookup"><span data-stu-id="18141-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="18141-111">**nxd_mqtt_client_publish** *ブローカーを介してメッセージを発行します。*</span><span class="sxs-lookup"><span data-stu-id="18141-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="18141-112">**nxd_mqtt_client_subscribe** *トピックをサブスクライブします*</span><span class="sxs-lookup"><span data-stu-id="18141-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="18141-113">**nxd_mqtt_client_unsubscribe** *トピックをサブスクライブ解除します*</span><span class="sxs-lookup"><span data-stu-id="18141-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="18141-114">**nxd_mqtt_client_receive_notify_set** *MQTT メッセージ受信通知コールバック関数を設定します*</span><span class="sxs-lookup"><span data-stu-id="18141-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="18141-115">**nxd_mqtt_client_message_get** *ブローカーからメッセージを取得します*</span><span class="sxs-lookup"><span data-stu-id="18141-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="18141-116">**nxd_mqtt_client_disconnect_notify_set** *MQTT メッセージ切断通知コールバック関数を設定します*</span><span class="sxs-lookup"><span data-stu-id="18141-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="18141-117">**nxd_mqtt_client_disconnect** *ブローカーから MQTT クライアントを切断します*</span><span class="sxs-lookup"><span data-stu-id="18141-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="18141-118">**nxd_mqtt_client_delete** *MQTT クライアント インスタンスを削除します*</span><span class="sxs-lookup"><span data-stu-id="18141-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="18141-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="18141-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="18141-120">MQTT クライアント インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="18141-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-121">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="18141-122">説明</span><span class="sxs-lookup"><span data-stu-id="18141-122">Description</span></span>

<span data-ttu-id="18141-123">このサービスを使用すると、指定した IP インスタンス上に MQTT クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="18141-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="18141-124">*client_id* の文字列は、MQTT 接続フェーズの間に "*クライアント識別子 (ClientId)* " としてサーバーに渡されます。</span><span class="sxs-lookup"><span data-stu-id="18141-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="18141-125">また、必要な ThreadX リソース (MQTT クライアント タスク スレッド、ミューテックス、イベント フラグ グループ、TCP ソケット) も作成されます。</span><span class="sxs-lookup"><span data-stu-id="18141-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-126">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-126">Input Parameters</span></span>

- <span data-ttu-id="18141-127">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-128">**client_name** クライアント名の文字列。</span><span class="sxs-lookup"><span data-stu-id="18141-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="18141-129">**client_id** 接続フェーズの間に使用されるクライアント ID 文字列。</span><span class="sxs-lookup"><span data-stu-id="18141-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="18141-130">MQTT ブローカーにより、この client_id を使用してクライアントが一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="18141-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="18141-131">**client_id_length** クライアント ID 文字列の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="18141-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="18141-132">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="18141-133">**pool_ptr** MQTT クライアントによって操作に使用されるパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="18141-134">**stack_ptr** MQTT クライアント スレッド用のスタック領域。</span><span class="sxs-lookup"><span data-stu-id="18141-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="18141-135">**stack_size** スタック領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="18141-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="18141-136">**mqtt_thread_priority** MQTT スレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="18141-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="18141-137">**memory_ptr** 非推奨。</span><span class="sxs-lookup"><span data-stu-id="18141-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="18141-138">使用されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="18141-138">Not used anymore.</span></span>
- <span data-ttu-id="18141-139">**memory_size** 非推奨。</span><span class="sxs-lookup"><span data-stu-id="18141-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="18141-140">使用されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="18141-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-141">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-141">Return Values</span></span>

- <span data-ttu-id="18141-142">**NXD_MQTT_SUCCESS** (0x00) MQTT クライアントが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="18141-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="18141-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー</span><span class="sxs-lookup"><span data-stu-id="18141-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="18141-144">NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="18141-145">NXD_MQTT_INVALID_PARAMETER (0x10009) will トピック文字列、will_retrain_flag、または will_QoS 値が無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-146">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-146">Allowed From</span></span>

<span data-ttu-id="18141-147">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-148">例</span><span class="sxs-lookup"><span data-stu-id="18141-148">Example</span></span>

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

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="18141-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="18141-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="18141-150">will メッセージを設定します</span><span class="sxs-lookup"><span data-stu-id="18141-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-151">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-151">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="18141-152">説明</span><span class="sxs-lookup"><span data-stu-id="18141-152">Description</span></span>

<span data-ttu-id="18141-153">このサービスを使用すると、クライアントがサーバーに接続する前に、オプションの will トピックと Will メッセージが設定されます。</span><span class="sxs-lookup"><span data-stu-id="18141-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="18141-154">will トピックは、UTF-8 でエンコードされた文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="18141-155">will メッセージは (設定されている場合)、CONNECT メッセージの一部としてブローカーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="18141-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="18141-156">したがって、will メッセージを使用するアプリケーションは、MQTT 接続を行う前に、このサービスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-157">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-157">Input Parameters</span></span>

- <span data-ttu-id="18141-158">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-159">**will_topic** UTF-8 でエンコードされた will トピックの文字列。</span><span class="sxs-lookup"><span data-stu-id="18141-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="18141-160">will トピックが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-160">Will topic must be present.</span></span> <span data-ttu-id="18141-161">呼び出し元は、*nx_mqtt_client_connect* の呼び出しが行われるまで、will_topic の文字列を有効な状態に保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="18141-162">**will_topic_length** will トピックの文字列のバイト数</span><span class="sxs-lookup"><span data-stu-id="18141-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="18141-163">**will_message** アプリケーションで定義された will メッセージ。</span><span class="sxs-lookup"><span data-stu-id="18141-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="18141-164">will メッセージが必要ない場合は、アプリケーションでこのフィールドを *NX_NULL* に設定できます。</span><span class="sxs-lookup"><span data-stu-id="18141-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="18141-165">**will_message_length** will メッセージ文字列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="18141-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="18141-166">will_message が NULL に設定されている場合は、will_message_length を 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="18141-167">**will_retain_flag** サーバーで will メッセージが保持メッセージとして発行されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="18141-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="18141-168">有効な値は、*NX_TRUE* または *NX_FALSE* です。</span><span class="sxs-lookup"><span data-stu-id="18141-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="18141-169">**will_QoS** will メッセージの送信時にサーバーによって使用される QoS 値。</span><span class="sxs-lookup"><span data-stu-id="18141-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="18141-170">有効な値は 0 または 1 です。</span><span class="sxs-lookup"><span data-stu-id="18141-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="18141-171">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-171">Return Values</span></span>

- <span data-ttu-id="18141-172">**NXD_MQTT_SUCCESS** (0x00) will メッセージは正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="18141-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="18141-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS レベル 2 メッセージはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="18141-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="18141-174">NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="18141-175">NXD_MQTT_INVALID_PARAMETER (0x10009) will トピック文字列、will_retrain_flag、または will_QoS 値が無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-176">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-176">Allowed From</span></span>

<span data-ttu-id="18141-177">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-178">例</span><span class="sxs-lookup"><span data-stu-id="18141-178">Example</span></span>

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

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="18141-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="18141-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="18141-180">MQTT クライアント ログインのユーザー名とパスワードを設定します</span><span class="sxs-lookup"><span data-stu-id="18141-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-181">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="18141-182">説明</span><span class="sxs-lookup"><span data-stu-id="18141-182">Description</span></span>

<span data-ttu-id="18141-183">このサービスを使用すると、MQTT 接続フェーズの間にログイン認証のために使用されるユーザー名とパスワードが設定されます。</span><span class="sxs-lookup"><span data-stu-id="18141-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="18141-184">ユーザー名とパスワードを使用した MQTT クライアント ログインはオプションです。</span><span class="sxs-lookup"><span data-stu-id="18141-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="18141-185">サーバーでユーザー名とパスワードが必要な場合は、接続が確立される前にユーザー名とパスワードを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-186">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-186">Input Parameters</span></span>

- <span data-ttu-id="18141-187">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-188">**username** UTF-8 でエンコードされたユーザー名の文字列。</span><span class="sxs-lookup"><span data-stu-id="18141-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="18141-189">呼び出し元は、*nx_mqtt_client_connect* の呼び出しが行われるまで、username の文字列を有効な状態に保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="18141-190">**username_length** ユーザー名の文字列のバイト数</span><span class="sxs-lookup"><span data-stu-id="18141-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="18141-191">**password** パスワードの文字列。</span><span class="sxs-lookup"><span data-stu-id="18141-191">**password** Password string.</span></span> <span data-ttu-id="18141-192">パスワードが必要ない場合は、このフィールドを NX_NULL に設定できます。</span><span class="sxs-lookup"><span data-stu-id="18141-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-193">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-193">Return Values</span></span>

- <span data-ttu-id="18141-194">**NXD_MQTT_SUCCESS** (0x00) will メッセージは正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="18141-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="18141-195">NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="18141-196">NXD_MQTT_INVALID_PARAMETER (0x10009) ユーザー名またはパスワードの文字列が無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-197">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-197">Allowed From</span></span>

<span data-ttu-id="18141-198">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-199">例</span><span class="sxs-lookup"><span data-stu-id="18141-199">Example</span></span>

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

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="18141-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="18141-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="18141-201">MQTT クライアントをブローカーに接続します</span><span class="sxs-lookup"><span data-stu-id="18141-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-202">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="18141-203">説明</span><span class="sxs-lookup"><span data-stu-id="18141-203">Description</span></span>

<span data-ttu-id="18141-204">このサービスを使用すると、ブローカーへの接続が開始されます。</span><span class="sxs-lookup"><span data-stu-id="18141-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="18141-205">最初に、TCP ソケットへのバインドが行われた後、TCP 接続が確立されます。</span><span class="sxs-lookup"><span data-stu-id="18141-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="18141-206">成功すると、MQTT キープ アライブ機能が有効になっている場合はタイマーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="18141-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="18141-207">その後、MQTT サーバー (ブローカー) と接続されます。</span><span class="sxs-lookup"><span data-stu-id="18141-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="18141-208">このサービスによって作成される MQTT 接続は、TLS で保護されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="18141-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="18141-209">セキュリティで保護された MQTT 接続を作成するには、アプリケーションでサービス ***nxd_mqtt_client_secure_connect()*** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="18141-210">接続時に、クライアントによって *clean_session* が NX_FALSE に設定されると、まだ受信確認されていないメッセージがクライアントによって再送信されます。</span><span class="sxs-lookup"><span data-stu-id="18141-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-211">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-211">Input Parameters</span></span>

- <span data-ttu-id="18141-212">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-213">**server_ip** ブローカーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="18141-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="18141-214">**server_port** ブローカーのポート番号。</span><span class="sxs-lookup"><span data-stu-id="18141-214">**server_port** Broker port number.</span></span> <span data-ttu-id="18141-215">MQTT の既定のポートは、**_NXD_MQTT_PORT_** (1883) として定義されています。</span><span class="sxs-lookup"><span data-stu-id="18141-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="18141-216">**keep_alive** セッションの間に使用されるキープ アライブの値 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="18141-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="18141-217">この値は、ブローカーによってこのクライアントがタイムアウトされることのない、ブローカーに送信される 2 つの MQTT 制御メッセージ間の最大時間を示します。</span><span class="sxs-lookup"><span data-stu-id="18141-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="18141-218">値 0 は、キープ アライブ機能がオフになります。</span><span class="sxs-lookup"><span data-stu-id="18141-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="18141-219">**clean_session** サーバーがこのセッションをクリーンに開始する必要があるかどうか。</span><span class="sxs-lookup"><span data-stu-id="18141-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="18141-220">有効なオプションは、**_NX_TRUE_ *_ または _* _NX_FALSE_** です。</span><span class="sxs-lookup"><span data-stu-id="18141-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="18141-221">**wait_option** 接続の待機時間。</span><span class="sxs-lookup"><span data-stu-id="18141-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-222">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-222">Return Values</span></span>

- <span data-ttu-id="18141-223">**NXD_MQTT_SUCCESS** (0x00) MQTT の接続が成功しました</span><span class="sxs-lookup"><span data-stu-id="18141-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="18141-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) クライアントは既にブローカーに接続されています。</span><span class="sxs-lookup"><span data-stu-id="18141-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="18141-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="18141-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="18141-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー</span><span class="sxs-lookup"><span data-stu-id="18141-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="18141-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) ブローカーに接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="18141-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="18141-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。</span><span class="sxs-lookup"><span data-stu-id="18141-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="18141-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) サーバーがエラーで応答しました</span><span class="sxs-lookup"><span data-stu-id="18141-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="18141-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="18141-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="18141-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="18141-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="18141-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="18141-235">NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-236">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-236">Allowed From</span></span>

<span data-ttu-id="18141-237">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-238">例</span><span class="sxs-lookup"><span data-stu-id="18141-238">Example</span></span>

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

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="18141-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="18141-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="18141-240">TLS セキュリティを使用して MQTT クライアントをブローカーに接続します</span><span class="sxs-lookup"><span data-stu-id="18141-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-241">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-241">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="18141-242">説明</span><span class="sxs-lookup"><span data-stu-id="18141-242">Description</span></span>

<span data-ttu-id="18141-243">このサービスは ***nxd_mqtt_client_connect*** と同じですが、TCP ではなく TLS レイヤー経由で接続が行われる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="18141-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="18141-244">したがって、クライアントとブローカーの間の通信はセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="18141-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="18141-245">ユーザー定義の *tls_setup* は、MQTT クライアント接続を行う前に MQTT クライアントによって使用されるコールバック関数です。</span><span class="sxs-lookup"><span data-stu-id="18141-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="18141-246">アプリケーションで、NetX Secure TLS を初期化し、セキュリティ パラメーターを構成して、TLS ハンドシェイクの間に使用される関連する証明書を読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="18141-247">実際の TLS ハンドシェイクは、ブローカーの MQTT TLS ポート (既定の TCP ポート 8883) で TCP 接続が確立された後に発生します。</span><span class="sxs-lookup"><span data-stu-id="18141-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="18141-248">TLS ハンドシェイクが成功すると、MQTT CONNECT 制御パケットが TLS 経由で送信されます。</span><span class="sxs-lookup"><span data-stu-id="18141-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="18141-249">セキュリティで保護された接続を行うには、NetX Secure TLS ライブラリが使用可能であり、NetX Duo MQTT クライアントが ***NX_SECURE_ENABLE*** を定義してビルドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-250">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-250">Input Parameters</span></span>

- <span data-ttu-id="18141-251">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-252">**server_ip** ブローカーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="18141-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="18141-253">**server_port** ブローカーのポート番号。</span><span class="sxs-lookup"><span data-stu-id="18141-253">**server_port** Broker port number.</span></span> <span data-ttu-id="18141-254">MQTT の既定のポートは、**_NXD_MQTT_TLS_PORT_** (8883) として定義されています。</span><span class="sxs-lookup"><span data-stu-id="18141-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="18141-255">**tls_setup** ユーザーが提供する TLS セットアップ コールバック関数。</span><span class="sxs-lookup"><span data-stu-id="18141-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="18141-256">このコールバック関数は、TLS クライアントの接続パラメーターを設定するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="18141-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="18141-257">**keep_alive** セッションの間に使用されるキープ アライブの値。</span><span class="sxs-lookup"><span data-stu-id="18141-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="18141-258">値 0 は、キープ アライブ機能がオフになります。</span><span class="sxs-lookup"><span data-stu-id="18141-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="18141-259">**clean_session** サーバーがこのセッションをクリーンに開始する必要があるかどうか。</span><span class="sxs-lookup"><span data-stu-id="18141-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="18141-260">有効なオプションは、**_NX_TRUE_ *_ または _* _NX_FALSE_** です。</span><span class="sxs-lookup"><span data-stu-id="18141-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="18141-261">**wait_option** 接続の待機時間。</span><span class="sxs-lookup"><span data-stu-id="18141-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-262">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-262">Return Values</span></span>

- <span data-ttu-id="18141-263">**NXD_MQTT_SUCCESS** (0x00) TLS を使用して MQTT クライアント接続が正常に確立されました。</span><span class="sxs-lookup"><span data-stu-id="18141-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="18141-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) クライアントは既にブローカーに接続されています。</span><span class="sxs-lookup"><span data-stu-id="18141-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="18141-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="18141-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="18141-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー</span><span class="sxs-lookup"><span data-stu-id="18141-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="18141-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) ブローカーに接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="18141-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="18141-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。</span><span class="sxs-lookup"><span data-stu-id="18141-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="18141-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) サーバーがエラー メッセージで応答しました。</span><span class="sxs-lookup"><span data-stu-id="18141-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="18141-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="18141-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="18141-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="18141-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="18141-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="18141-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="18141-275">NX_PTR_ERROR (0x07) MQTT コントロール ブロックまたはサーバー アドレスの構造が無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="18141-276">NX_INVALID_PORT (0x46) サーバー ポートを 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="18141-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="18141-277">NXD_MQTT_INVALID_PARAMETER (0x10009) 入力パラメーター エラー</span><span class="sxs-lookup"><span data-stu-id="18141-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="18141-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT スレッドの実行はまだ開始されていません。</span><span class="sxs-lookup"><span data-stu-id="18141-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-279">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-279">Allowed From</span></span>

<span data-ttu-id="18141-280">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-281">例</span><span class="sxs-lookup"><span data-stu-id="18141-281">Example</span></span>

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

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="18141-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="18141-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="18141-283">ブローカーを介してメッセージを発行します</span><span class="sxs-lookup"><span data-stu-id="18141-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-284">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="18141-285">説明</span><span class="sxs-lookup"><span data-stu-id="18141-285">Description</span></span>

<span data-ttu-id="18141-286">このサービスを使用すると、ブローカーを介してメッセージが発行されます。</span><span class="sxs-lookup"><span data-stu-id="18141-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="18141-287">QoS レベル 2 のメッセージの発行はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="18141-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-288">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-288">Input Parameters</span></span>

- <span data-ttu-id="18141-289">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-290">**topic_name** 発行先のトピック。</span><span class="sxs-lookup"><span data-stu-id="18141-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="18141-291">**topic_name_length** トピックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="18141-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="18141-292">**message** メッセージ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="18141-293">**message_length** メッセージのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="18141-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="18141-294">**retain** ブローカーでメッセージを保持する必要があるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="18141-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="18141-295">**QoS** 必要な QoS 値: 0 または 1。</span><span class="sxs-lookup"><span data-stu-id="18141-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="18141-296">**timeout** タイムアウト値</span><span class="sxs-lookup"><span data-stu-id="18141-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-297">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-297">Return Values</span></span>

- <span data-ttu-id="18141-298">**NXD_MQTT_SUCCESS** (0x00) MQTT クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="18141-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="18141-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー。</span><span class="sxs-lookup"><span data-stu-id="18141-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="18141-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) パケット プールからパケットを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="18141-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="18141-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーとの通信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="18141-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="18141-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS レベル 2 メッセージはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="18141-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="18141-303">NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="18141-304">NXD_MQTT_INVALID_PARAMETER (0x10009) 入力パラメーター エラー</span><span class="sxs-lookup"><span data-stu-id="18141-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-305">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-305">Allowed From</span></span>

<span data-ttu-id="18141-306">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-307">例</span><span class="sxs-lookup"><span data-stu-id="18141-307">Example</span></span>

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

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="18141-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="18141-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="18141-309">トピックのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="18141-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-310">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="18141-311">説明</span><span class="sxs-lookup"><span data-stu-id="18141-311">Description</span></span>

<span data-ttu-id="18141-312">このサービスを使用すると、特定のトピックがサブスクライブされます。</span><span class="sxs-lookup"><span data-stu-id="18141-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="18141-313">QoS レベル 2 のメッセージのサブスクライブはまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="18141-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-314">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-314">Input Parameters</span></span>

- <span data-ttu-id="18141-315">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-316">**topic_name** 発行先のトピック。</span><span class="sxs-lookup"><span data-stu-id="18141-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="18141-317">**topic_name_length** トピックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="18141-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="18141-318">**QoS** 必要な QoS レベル: 0 または 1。</span><span class="sxs-lookup"><span data-stu-id="18141-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-319">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-319">Return Values</span></span>

- <span data-ttu-id="18141-320">**NXD_MQTT_SUCCESS** (0x00) トピックが正常にサブスクライブされました。</span><span class="sxs-lookup"><span data-stu-id="18141-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="18141-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) クライアントがブローカーに接続されていません。</span><span class="sxs-lookup"><span data-stu-id="18141-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="18141-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="18141-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="18141-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー</span><span class="sxs-lookup"><span data-stu-id="18141-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="18141-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。</span><span class="sxs-lookup"><span data-stu-id="18141-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="18141-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS レベル 2 メッセージはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="18141-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="18141-326">NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="18141-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name が設定されていないか、topic_name_length が 0 であるか、QoS の値が無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-328">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-328">Allowed From</span></span>

<span data-ttu-id="18141-329">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-330">例</span><span class="sxs-lookup"><span data-stu-id="18141-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="18141-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="18141-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="18141-332">トピックのサブスクライブを解除します</span><span class="sxs-lookup"><span data-stu-id="18141-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-333">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="18141-334">説明</span><span class="sxs-lookup"><span data-stu-id="18141-334">Description</span></span>

<span data-ttu-id="18141-335">このサービスを使用すると、トピックのサブスクライブが解除されます。</span><span class="sxs-lookup"><span data-stu-id="18141-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-336">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-336">Input Parameters</span></span>

- <span data-ttu-id="18141-337">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-338">**topic_name** サブスクライブを解除するトピック。</span><span class="sxs-lookup"><span data-stu-id="18141-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="18141-339">**topic_name_length** トピックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="18141-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-340">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-340">Return Values</span></span>

- <span data-ttu-id="18141-341">**NXD_MQTT_SUCCESS** (0x00) トピックのサブスクライブが正常に解除されました。</span><span class="sxs-lookup"><span data-stu-id="18141-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="18141-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) クライアントがブローカーに接続されていません。</span><span class="sxs-lookup"><span data-stu-id="18141-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="18141-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="18141-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="18141-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー</span><span class="sxs-lookup"><span data-stu-id="18141-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="18141-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) ブローカーにメッセージを送信できません。</span><span class="sxs-lookup"><span data-stu-id="18141-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="18141-346">NX_PTR_ERROR (0x07) MQTT 制御ブロック ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="18141-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name が設定されていないか、topic_name_length が 0 です。</span><span class="sxs-lookup"><span data-stu-id="18141-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-348">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-348">Allowed From</span></span>

<span data-ttu-id="18141-349">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-350">例</span><span class="sxs-lookup"><span data-stu-id="18141-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="18141-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="18141-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="18141-352">MQTT メッセージ受信通知コールバック関数を設定します</span><span class="sxs-lookup"><span data-stu-id="18141-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-353">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="18141-354">説明</span><span class="sxs-lookup"><span data-stu-id="18141-354">Description</span></span>

<span data-ttu-id="18141-355">このサービスを使用すると、コールバック関数が MQTT クライアントに登録されます。</span><span class="sxs-lookup"><span data-stu-id="18141-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="18141-356">ブローカーによって発行されたメッセージを受信すると、メッセージは MQTT クライアントにより受信キューに格納されます。</span><span class="sxs-lookup"><span data-stu-id="18141-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="18141-357">コールバック関数が設定されている場合は、コールバック関数が呼び出されて、メッセージを取得する準備ができたことがアプリケーションに通知されます。</span><span class="sxs-lookup"><span data-stu-id="18141-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="18141-358">受信通知関数は、MQTT クライアント制御ブロックへのポインターと、受信キューで使用できるメッセージの数を示す *message_count* を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="18141-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="18141-359">この値は、受信通知から、アプリケーションでこれらのメッセージを取得するまでの間に、変わる可能性があることに注意してください。これは、その間に新しいメッセージが到着する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="18141-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-360">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-360">Input Parameters</span></span>

- <span data-ttu-id="18141-361">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-362">**receive_notify** メッセージの受信時に呼び出される、ユーザー提供のコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="18141-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-363">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-363">Return Values</span></span>

- <span data-ttu-id="18141-364">**NXD_MQTT_SUCCESS** (0x00) 受信通知関数が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="18141-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="18141-365">NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-366">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-366">Allowed From</span></span>

<span data-ttu-id="18141-367">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-368">例</span><span class="sxs-lookup"><span data-stu-id="18141-368">Example</span></span>

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

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="18141-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="18141-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="18141-370">ブローカーからメッセージを取得します</span><span class="sxs-lookup"><span data-stu-id="18141-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-371">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="18141-372">説明</span><span class="sxs-lookup"><span data-stu-id="18141-372">Description</span></span>

<span data-ttu-id="18141-373">このサービスを使用すると、ブローカーによって発行されたメッセージが取得されます。</span><span class="sxs-lookup"><span data-stu-id="18141-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="18141-374">着信したメッセージはすべて受信キューに格納されます。</span><span class="sxs-lookup"><span data-stu-id="18141-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="18141-375">アプリケーションでは、このサービスを使用してこれらのメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="18141-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="18141-376">この呼び出しは非ブロックです。</span><span class="sxs-lookup"><span data-stu-id="18141-376">This call is non-blocking.</span></span> <span data-ttu-id="18141-377">受信キューが空の場合、このサービスからは \***NXD_MQTT_NO_MESSAGE** _ が返されます。</span><span class="sxs-lookup"><span data-stu-id="18141-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="18141-378">受信メッセージの通知を希望するアプリケーションは、サービスの _ *_nxd_mqtt_client_receive_notify_set_*\* を呼び出して、受信コールバック関数を登録できます。</span><span class="sxs-lookup"><span data-stu-id="18141-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="18141-379">呼び出し元は、トピック文字列とメッセージ本文のためのメモリ領域を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="18141-380">これら 2 つのバッファーのサイズは、*topic_buffer_size* と *message_buffer_size* を使用して渡します。</span><span class="sxs-lookup"><span data-stu-id="18141-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="18141-381">トピック文字列とメッセージ本文の実際のバイト数は、*actual_topic_length* と *actual_message_length* で返されます。</span><span class="sxs-lookup"><span data-stu-id="18141-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="18141-382">トピックの長さまたはメッセージの長さが指定したバッファー領域より大きい場合は、このサービスからエラー コード *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE* が返されます。</span><span class="sxs-lookup"><span data-stu-id="18141-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="18141-383">アプリケーションで、より大きなバッファーを割り当ててから再試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-384">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-384">Input Parameters</span></span>

- <span data-ttu-id="18141-385">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-386">**topic_buffer** トピック文字列のコピー先のメモリ位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="18141-387">**topic_buffer_size** トピック バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="18141-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="18141-388">**actual_topic_length** 実際のトピック長が返されるメモリ位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="18141-389">**message_buffer** メッセージ文字列のコピー先のメモリ位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="18141-390">**message_buffer_size** メッセージ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="18141-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="18141-391">**actual_message_length** メッセージ長が返されるメモリ位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-392">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-392">Return Values</span></span>

- <span data-ttu-id="18141-393">**NXD_MQTT_SUCCESS** (0x00) メッセージが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="18141-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="18141-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 内部論理エラー</span><span class="sxs-lookup"><span data-stu-id="18141-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="18141-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) 受信キューが空です。</span><span class="sxs-lookup"><span data-stu-id="18141-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="18141-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) トピック バッファーまたはメッセージ バッファーが、トピックまたはメッセージに対して小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="18141-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="18141-397">NX_PTR_ERROR (0x07) MQTT 制御ブロック、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="18141-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer または topic_buffer のポインターが NULL です</span><span class="sxs-lookup"><span data-stu-id="18141-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-399">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-399">Allowed From</span></span>

<span data-ttu-id="18141-400">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-401">例</span><span class="sxs-lookup"><span data-stu-id="18141-401">Example</span></span>

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

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="18141-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="18141-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="18141-403">MQTT メッセージ切断通知コールバック関数を設定します</span><span class="sxs-lookup"><span data-stu-id="18141-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-404">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="18141-405">説明</span><span class="sxs-lookup"><span data-stu-id="18141-405">Description</span></span>

<span data-ttu-id="18141-406">このサービスを使用すると、コールバック関数が MQTT クライアントに登録されます。</span><span class="sxs-lookup"><span data-stu-id="18141-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="18141-407">MQTT によってブローカーへの接続が失われたことが検出されると、この通知関数が呼び出されて、アプリケーションに警告されます。</span><span class="sxs-lookup"><span data-stu-id="18141-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="18141-408">このため、アプリケーションでこのコールバック関数を使用して失われた接続を検出し、ブローカーへの接続を再確立することができます。</span><span class="sxs-lookup"><span data-stu-id="18141-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="18141-409">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-409">Input Parameters</span></span>

- <span data-ttu-id="18141-410">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="18141-411">**disconnect_notify** MQTT によってブローカーへの接続が失われたことが検出されたときに呼び出されるユーザー提供のコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="18141-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-412">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-412">Return Values</span></span>

- <span data-ttu-id="18141-413">**NXD_MQTT_SUCCESS** (0x00) 切断通知関数が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="18141-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="18141-414">NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です。</span><span class="sxs-lookup"><span data-stu-id="18141-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-415">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-415">Allowed From</span></span>

<span data-ttu-id="18141-416">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-417">例</span><span class="sxs-lookup"><span data-stu-id="18141-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="18141-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="18141-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="18141-419">ブローカーから MQTT クライアントを切断します</span><span class="sxs-lookup"><span data-stu-id="18141-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-420">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="18141-421">説明</span><span class="sxs-lookup"><span data-stu-id="18141-421">Description</span></span>

<span data-ttu-id="18141-422">このサービスを使用すると、ブローカーからクライアントが切断されます。</span><span class="sxs-lookup"><span data-stu-id="18141-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="18141-423">受信キューにあるメッセージは解放されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="18141-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="18141-424">送信キュー内の QoS 1 のメッセージは解放されません。</span><span class="sxs-lookup"><span data-stu-id="18141-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="18141-425">クライアントが *clean_session* フラグを ***NX_TRUE*** に設定してサーバーに再接続しない限り、クライアントがサーバーに再接続した後で、QoS 1 のメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="18141-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="18141-426">TLS セキュリティ保護を使用して接続が行われた場合、TCP 接続が切断される前に、このサービスによって TLS セッションが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="18141-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="18141-427">実際の TCP ソケット切断呼び出しには、NXD_MQTT_SOCKET_TIMEOUT (タイマー ティック) によって待機オプションが定義されています。</span><span class="sxs-lookup"><span data-stu-id="18141-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="18141-428">既定値は NX_WAIT_FOREVER です。</span><span class="sxs-lookup"><span data-stu-id="18141-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="18141-429">ネットワーク接続が失われたり、サーバーが応答していない場合に、無限の中断を回避するには、このオプションを有限の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="18141-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-430">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-430">Input Parameters</span></span>

- <span data-ttu-id="18141-431">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-432">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-432">Return Values</span></span>

- <span data-ttu-id="18141-433">**NXD_MQTT_SUCCESS** (0x00) がブローカーから正常に切断されました</span><span class="sxs-lookup"><span data-stu-id="18141-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="18141-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT ミューテックスを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="18141-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="18141-435">NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-436">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-436">Allowed From</span></span>

<span data-ttu-id="18141-437">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-438">例</span><span class="sxs-lookup"><span data-stu-id="18141-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="18141-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="18141-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="18141-440">MQTT クライアントのインスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="18141-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="18141-441">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="18141-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="18141-442">説明</span><span class="sxs-lookup"><span data-stu-id="18141-442">Description</span></span>

<span data-ttu-id="18141-443">このサービスを使用すると、MQTT クライアント インスタンスが削除され、内部リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="18141-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="18141-444">クライアントがまだ接続されている場合、このサービスによりブローカーから自動的に切断されます。</span><span class="sxs-lookup"><span data-stu-id="18141-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="18141-445">まだ送信されていない、または受信確認されていないメッセージは解放されます。</span><span class="sxs-lookup"><span data-stu-id="18141-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="18141-446">受信されたがアプリケーションによって取得されていないメッセージも解放されます。</span><span class="sxs-lookup"><span data-stu-id="18141-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="18141-447">TLS セキュリティ保護を使用して接続が行われた場合、TCP 接続が切断される前に、このサービスによって TLS セッションが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="18141-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="18141-448">クライアントが削除された後、MQTT サービスの使用を望むアプリケーションは、新しいインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18141-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="18141-449">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="18141-449">Input Parameters</span></span>

- <span data-ttu-id="18141-450">**client_ptr** MQTT クライアント制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="18141-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="18141-451">戻り値</span><span class="sxs-lookup"><span data-stu-id="18141-451">Return Values</span></span>

- <span data-ttu-id="18141-452">**NXD_MQTT_SUCCESS** (0x00) MQTT クライアントが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="18141-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="18141-453">NX_PTR_ERROR (0x07) MQTT 制御ブロックが無効です</span><span class="sxs-lookup"><span data-stu-id="18141-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="18141-454">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="18141-454">Allowed From</span></span>

<span data-ttu-id="18141-455">Threads</span><span class="sxs-lookup"><span data-stu-id="18141-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="18141-456">例</span><span class="sxs-lookup"><span data-stu-id="18141-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
