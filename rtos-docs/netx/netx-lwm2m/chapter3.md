---
title: 第 3 章 - Azure RTOS NetX LWM2M の機能の説明
description: この章では、Azure RTOS NetX LWM2M の機能について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811495"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="e6ab4-103">第 3 章 - Azure RTOS NetX LWM2M の機能の説明</span><span class="sxs-lookup"><span data-stu-id="e6ab4-103">Chapter 3 - Functional description of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="e6ab4-104">この章では、Azure RTOS NetX LWM2M の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-104">This chapter contains a functional description of Azure RTOS NetX LWM2M.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="e6ab4-105">LWM2M クライアントの初期化</span><span class="sxs-lookup"><span data-stu-id="e6ab4-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="e6ab4-106">LWM2M クライアントは、***nx_lwm2m_client_create*** サービスを呼び出すことによって初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="e6ab4-107">LWM2M クライアントは独自のスレッドで実行され、コールバックを使用するか、アプリケーションによって実装されたカスタム オブジェクトのメソッドを呼び出すことによって、アプリケーションにイベントをレポートできます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="e6ab4-108">また、1 つ以上のサーバーとの通信を有効にするために、***nx_lwm2m_client_session_create*** を呼び出して、LWM2M クライアント セッションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="e6ab4-109">セッションでは、ブートストラップ サーバーおよび LWM2M サーバー (デバイス管理) の 2 種類のサーバーと通信できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="e6ab4-110">ブートストラップ サーバー セッション</span><span class="sxs-lookup"><span data-stu-id="e6ab4-110">Bootstrap Server Session</span></span>

<span data-ttu-id="e6ab4-111">ブートストラップ サーバーとの通信セッションは、LWM2M クライアントが 1 つ以上の LWM2M サーバーへの "登録" 操作を実行できるように、LWM2M クライアントに必須情報をプロビジョニングするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation "Register" with one or more LWM2M Servers.</span></span> <span data-ttu-id="e6ab4-112">この種類のサーバーは、クライアントおよびサーバーが開始したブートストラップ モード中に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="e6ab4-113">アプリケーションでは、***nx_lwm2m_client_session_bootstrap** _ または _*_nx_lwm2m_client_session_bootstrap_dtls_\*_ を呼び出すことによってブートストラップ セッションを開始できます。サーバーの IP アドレスとポート番号、およびオプションのセキュリティ オブジェクト インスタンス ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="e6ab4-114">_*_nx_lwm2m_client_session_bootstrap_*_ 関数では、セキュリティで保護されていない通信が使用されます。一方、_ *_nx_lwm2m_client_session_bootstrap_dtls_*\* では、サーバーとのセキュリティで保護された DTLS 接続が確立されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="e6ab4-115">ブートストラップ操作が成功した場合、ブートストラップ サーバーによって、ブートストラップ サーバーと LWM2M サーバーのセキュリティ オブジェクト インスタンス、および LWM2M サーバーのサーバー オブジェクト インスタンスが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="e6ab4-116">アプリケーションでは、この情報を使用して、LWM2M サーバーとのセッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-116">The application must use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="e6ab4-117">デバイスの次回の再起動時に LWM2M クライアントを構成するために、アプリケーションはブートストラップ データを不揮発性メモリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-117">The Bootstrap data should be saved to non-volatile memory by the application in order to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="e6ab4-118">LWM2M サーバー セッション</span><span class="sxs-lookup"><span data-stu-id="e6ab4-118">LWM2M Server Session</span></span>

<span data-ttu-id="e6ab4-119">LWM2M サーバーとの通信セッションは、登録、デバイス管理、サービスの有効化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="e6ab4-120">アプリケーションでは、***nx_lwm2m_client_session_register** _ または _*_nx_lwm2m_client_session_register_dtls_\*_ を呼び出すことによって、LWM2M クライアントをサーバーに登録できます。サーバーの IP アドレスとポート番号、および既存のサーバー オブジェクト インスタンスに対応する短いサーバー ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="e6ab4-121">_*_nx_lwm2m_client_session_register_*_ 関数では、セキュリティで保護されていない通信が使用されます。一方、_ *_nx_lwm2m_client_session_register_dtls_*\* では、サーバーとのセキュリティで保護された DTLS 接続が確立されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="e6ab4-122">アプリケーションでは、***nx_lwm2m_client_session_deregister** _ を呼び出して LWM2M クライアントを登録解除し、_*_nx_lwm2m_client_session_update_\*\* を呼び出して、"Update" メッセージを送信するようクライアントに要求できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an 'Update' message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="e6ab4-123">セッション状態のコールバック</span><span class="sxs-lookup"><span data-stu-id="e6ab4-123">Session State Callback</span></span>

<span data-ttu-id="e6ab4-124">アプリケーションではセッションの作成時に、セッションの状態が更新されたときに呼び出されるコールバックを登録します。コールバック関数 NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK のプロトタイプを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK has the following prototype:</span></span>

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

<span data-ttu-id="e6ab4-125">次の状態が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-125">The following states are defined :</span></span>

- <span data-ttu-id="e6ab4-126">**NX_LWM2M_CLIENT_SESSION_INIT**: セッション作成後の初期状態です。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-126">**NX_LWM2M_CLIENT_SESSION_INIT**: The initial state after session creation.</span></span>

- <span data-ttu-id="e6ab4-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: クライアントは、"Hold Off" タイマーまたはサーバーが開始したブートストラップの有効期限が切れるのを待機しています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: The client is waiting for the expiration of the 'Hold Off' timer or Server Initiated Bootstrap.</span></span>

- <span data-ttu-id="e6ab4-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: クライアントがブートストラップ サーバーに "Request" メッセージを送信しました (クライアントが開始したブートストラップ)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: The client has sent a 'Request' message to the Bootstrap Server (Client Initiated Bootstrap).</span></span>

- <span data-ttu-id="e6ab4-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: クライアントがブートストラップ サーバーからデータを受信しています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: The client is receiving data from the Bootstrap Server.</span></span>

- <span data-ttu-id="e6ab4-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: ブートストラップ サーバーが "Finished" メッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: The Bootstrap Server has sent a 'Finished' message.</span></span>

- <span data-ttu-id="e6ab4-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: ブートストラップ セッションが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: The bootstrap session has failed.</span></span>

- <span data-ttu-id="e6ab4-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: クライアントが LWM2M サーバーに "Register" メッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: The client has sent a 'Register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="e6ab4-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: クライアントが LWM2M サーバーに登録されました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: The client is registered to the LWM2M Server.</span></span>

- <span data-ttu-id="e6ab4-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: クライアントが LWM2M サーバーに "Update" メッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: The client has sent an 'Update' message to the LWM2M Server.</span></span>

- <span data-ttu-id="e6ab4-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: クライアントが LWM2M サーバーに "De-register" メッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: The client has sent an 'De-register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="e6ab4-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: クライアントが LWM2M サーバーから登録解除されました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: The client is de-registered from the LWM2M Server.</span></span>

- <span data-ttu-id="e6ab4-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: LWM2M サーバーが無効になりました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: The LWM2M Server is disabled.</span></span> <span data-ttu-id="e6ab4-138">無効化タイマーの有効期限が切れると、"Register" が送信されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-138">A 'Register' will be sent after the expiration of the disable timer.</span></span>

- <span data-ttu-id="e6ab4-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: LWM2M サーバーに対する登録または更新操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: The registration or update operation to the LWM2M Server has failed.</span></span>

- <span data-ttu-id="e6ab4-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: LWM2M サーバーに対応するサーバー オブジェクト インスタンスが削除されました。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> <span data-ttu-id="e6ab4-141">エラーが発生した場合、アプリケーションで **_nx_lwm2m_client_session_error_get_** を呼び出すことによってエラーの原因を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-141">In case of error the application can retrieve the cause of the error by calling **_nx_lwm2m_client_session_error_get_**.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="e6ab4-142">ローカル デバイス管理</span><span class="sxs-lookup"><span data-stu-id="e6ab4-142">Local Device Management</span></span>

<span data-ttu-id="e6ab4-143">アプリケーションでは、ローカル デバイス管理関数を使用して、LWM2M クライアントのオブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-143">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="e6ab4-144">次の関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-144">The following functions are provided:</span></span>

- <span data-ttu-id="e6ab4-145">***nx_lwm2m_client_object_read***: オブジェクト インスタンスからリソースを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-145">***nx_lwm2m_client_object_read***: Read resources from an Object Instance.</span></span>

- <span data-ttu-id="e6ab4-146">***nx_lwm2m_client_object_discover***: オブジェクト インスタンスのリソースのリストを取得します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-146">***nx_lwm2m_client_object_discover***: Get the list of the resources of an Object Instance.</span></span>

- <span data-ttu-id="e6ab4-147">***nx_lwm2m_client_object_write***: オブジェクト インスタンスにリソースを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-147">***nx_lwm2m_client_object_write***: Write resources to an Object Instance</span></span>

- <span data-ttu-id="e6ab4-148">***nx_lwm2m_client_object_execute***: オブジェクト インスタンスのリソースに対して Execute 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-148">***nx_lwm2m_client_object_execute***: Perform the Execute operation on a resource of an Object Instance.</span></span>

- <span data-ttu-id="e6ab4-149">***nx_lwm2m_client_object_create***: 新しいオブジェクト インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-149">***nx_lwm2m_client_object_create***: Create a new Object Instance.</span></span>

- <span data-ttu-id="e6ab4-150">***nx_lwm2m_client_object_delete***: 既存のオブジェクト インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-150">***nx_lwm2m_client_object_delete***: Delete an existing Object Instance.</span></span>

- <span data-ttu-id="e6ab4-151">***nx_lwm2m_client_object_get_next***: LWM2M クライアントで実装されている次のオブジェクト ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-151">***nx_lwm2m_client_object_get_next***: Get the next Object ID implemented by the LWM2M Client.</span></span>

- <span data-ttu-id="e6ab4-152">***nx_lwm2m_client_object_instance_get_next***: オブジェクトの次のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-152">***nx_lwm2m_client_object_instance_get_next***: Get the next Instance of an Object.</span></span>

## <a name="resource-information"></a><span data-ttu-id="e6ab4-153">リソース情報</span><span class="sxs-lookup"><span data-stu-id="e6ab4-153">Resource Information</span></span>

<span data-ttu-id="e6ab4-154">オブジェクトに対して読み取りおよび書き込みを行うう場合、リソースは NX_LWM2M_RESOURCE 構造体で表されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-154">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="e6ab4-155">この構造体には、リソースまたはインスタンスの ID とその値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-155">This structure contains the ID of the Resource/Instance and its value.</span></span> <span data-ttu-id="e6ab4-156">値のエンコードは、値の型とソース (アプリケーションまたはネットワーク) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-156">The encoding of the value depends on its type and its origin (application or network).</span></span>

<span data-ttu-id="e6ab4-157">NX_LWM2M_RESOURCE 構造体の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-157">The NX_LWM2M_RESOURCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- <span data-ttu-id="e6ab4-158">**nx_lwm2m_resource_id**: リソースまたはインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-158">**nx_lwm2m_resource_id**: The ID of the Resource or the Instance.</span></span>
- <span data-ttu-id="e6ab4-159">**nx_lwm2m_resource_type**: 値の型 (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-159">**nx_lwm2m_resource_type**: The type of the value, see below.</span></span>
- <span data-ttu-id="e6ab4-160">**nx_lwm2m_resource_value**: リソースの値。値の型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-160">**nx_lwm2m_resource_value**: The value of the Resource, depends on the type of the value.</span></span>

<span data-ttu-id="e6ab4-161">次の型の値が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-161">The following type of values are defined :</span></span>

- <span data-ttu-id="e6ab4-162">**NX_LWM2M_RESOURCE_NONE**: 空のリソース。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-162">**NX_LWM2M_RESOURCE_NONE**: Empty resource.</span></span>

- <span data-ttu-id="e6ab4-163">**NX_LWM2M_RESOURCE_STRING**: *nx_lwm2m_resource_stringdata* に格納される null で終わる UTF-8 文字列値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-163">**NX_LWM2M_RESOURCE_STRING**: A null-terminated UTF-8 string value stored in *nx_lwm2m_resource_stringdata*.</span></span>

- <span data-ttu-id="e6ab4-164">**NX_LWM2M_RESOURCE_INTEGER32**: *nx_lwm2m_resource_integer32data* に格納される 32 ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-164">**NX_LWM2M_RESOURCE_INTEGER32**: A 32-Bit Integer value stored in *nx_lwm2m_resource_integer32data*.</span></span>

- <span data-ttu-id="e6ab4-165">**NX_LWM2M_RESOURCE_INTEGER64**: *nx_lwm2m_resource_integer64data* に格納される 64 ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-165">**NX_LWM2M_RESOURCE_INTEGER64**: A 64-Bit Integer value stored in *nx_lwm2m_resource_integer64data*.</span></span>

- <span data-ttu-id="e6ab4-166">**NX_LWM2M_RESOURCE_FLOAT32**: *nx_lwm2m_resource_float32data* に格納される 32 ビット浮動小数点値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-166">**NX_LWM2M_RESOURCE_FLOAT32**: A 32-Bit Floating Point value stored in *nx_lwm2m_resource_float32data*.</span></span>

- <span data-ttu-id="e6ab4-167">**NX_LWM2M_RESOURCE_FLOAT64**: *nx_lwm2m_resource_float64data* に格納される 64 ビット浮動小数点値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-167">**NX_LWM2M_RESOURCE_FLOAT64**: A 64-Bit Floating Point value stored in *nx_lwm2m_resource_float64data*.</span></span>

- <span data-ttu-id="e6ab4-168">**NX_LWM2M_RESOURCE_BOOLEAN**: *nx_lwm2m_resource_booleandata* に格納されるブール値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-168">**NX_LWM2M_RESOURCE_BOOLEAN**: A Boolean value stored in *nx_lwm2m_resource_booleandata*.</span></span>

- <span data-ttu-id="e6ab4-169">**NX_LWM2M_RESOURCE_OPAQUE**: *nx_lwm2m_resource_bufferdata* で定義される Opaque 値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-169">**NX_LWM2M_RESOURCE_OPAQUE**: An Opaque value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="e6ab4-170">**NX_LWM2M_RESOURCE_OBJLNK**: *nx_lwm2m_resource_objlnkdata* に格納されるオブジェクト リンク値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-170">**NX_LWM2M_RESOURCE_OBJLNK**: An Object Link value stored in *nx_lwm2m_resource_objlnkdata*.</span></span>

- <span data-ttu-id="e6ab4-171">**NX_LWM2M_RESOURCE_TLV**: *nx_lwm2m_resource_bufferdata* で定義される TLV エンコードされた値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-171">**NX_LWM2M_RESOURCE_TLV**: A TLV encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="e6ab4-172">**NX_LWM2M_RESOURCE_TEXT**: *nx_lwm2m_resource_bufferdata* で定義されるプレーンテキスト エンコードされた値。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-172">**NX_LWM2M_RESOURCE_TEXT**: A Plain-Text encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="e6ab4-173">**NX_LWM2M_RESOURCE_MULTIPLE**: *nx_lwm2m_resource_multipledata* で定義される複数リソース。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-173">**NX_LWM2M_RESOURCE_MULTIPLE**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="e6ab4-174">*nx_lwm2m_resource_multiple_ptr* は、各リソース インスタンスに関する情報を格納する **NX_LWM2M_RESOURCE** 構造体の配列へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-174">*nx_lwm2m_resource_multiple_ptr* is a pointer to an array of **NX_LWM2M_RESOURCE** structures containing information about each Resource Instances.</span></span>

- <span data-ttu-id="e6ab4-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: *nx_lwm2m_resource_multipledata* で定義される複数リソース。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="e6ab4-176">*nx_lwm2m_resource_multiple_ptr* は、TLV エンコードされたバッファーへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-176">*nx_lwm2m_resource_multiple_ptr* is a pointer to a TLV encoded buffer.</span></span>

<span data-ttu-id="e6ab4-177">値を取得し、その型を確認するための便利な関数が用意されています。アプリケーションで NX_LWM2M_RESOURCE 構造体から値を取得するときに、*nx_lwm2m_resource_value* フィールドに直接アクセスしないでください。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-177">Convenience functions are provided for retrieving the value and checking its type, the application should never directly access the *nx_lwm2m_resource_value* field when getting a value from a NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="e6ab4-178">次の関数が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-178">The following functions are defined :</span></span>

- <span data-ttu-id="e6ab4-179">***nx_lwm2m_resource_get_***: 指定された型の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-179">***nx_lwm2m_resource_get_***: Get a value with the given type.</span></span>
- <span data-ttu-id="e6ab4-180">***nx_lwm2m_resource_multiple_get_***: 複数リソースから指定された型の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-180">***nx_lwm2m_resource_multiple_get_***: Get a value with the given type from a Multiple Resource.</span></span>

<span data-ttu-id="e6ab4-181">マクロ **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) を使用して、リソースの種類が複数リソースかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-181">The macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) can be used to check if a resource type is a Multiple Resource.</span></span>

## <a name="object-implementation"></a><span data-ttu-id="e6ab4-182">オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="e6ab4-182">Object Implementation</span></span>

<span data-ttu-id="e6ab4-183">LWM2M クライアントは、必須の OMA LWM2M オブジェクト (セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)) を実装します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-183">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="e6ab4-184">デバイス固有の他のオブジェクトは、アプリケーションによって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-184">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="e6ab4-185">オブジェクトを定義するには、2 つのデータ構造体を使用します。NX_LWM2M_OBJECT 構造体では、オブジェクト ID やオブジェクト メソッドなど、オブジェクト実装を定義し、NX_LWM2M_OBJECT_INSTANCE 構造体には、オブジェクト インスタンスのデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-185">Two data structures are used to define an Object: the NX_LWM2M_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="e6ab4-186">NX_LWM2M_OBJECT 構造体の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-186">The NX_LWM2M_OBJECT structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- <span data-ttu-id="e6ab4-187">**nx_lwm2m_object_next**: リスト内の次のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-187">**nx_lwm2m_object_next**: The next object in the list.</span></span>
- <span data-ttu-id="e6ab4-188">**nx_lwm2m_object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-188">**nx_lwm2m_object_id**: The Object ID.</span></span>
- <span data-ttu-id="e6ab4-189">**nx_lwm2m_object_read**: "Read" メソッド (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-189">**nx_lwm2m_object_read**: The 'Read' method, see below.</span></span>
- <span data-ttu-id="e6ab4-190">**nx_lwm2m_object_discover**: "Discover" メソッド (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-190">**nx_lwm2m_object_discover**: The 'Discover' method, see below.</span></span>
- <span data-ttu-id="e6ab4-191">**nx_lwm2m_object_write**: "Write" メソッド (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-191">**nx_lwm2m_object_write**: The 'Write' method, see below.</span></span>
- <span data-ttu-id="e6ab4-192">**nx_lwm2m_object_execute**: "Execute" メソッド (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-192">**nx_lwm2m_object_execute**: The 'Execute' method, see below.</span></span>
- <span data-ttu-id="e6ab4-193">**nx_lwm2m_object_create**: "Create" メソッド (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-193">**nx_lwm2m_object_create**: The 'Create' method, see below.</span></span>
- <span data-ttu-id="e6ab4-194">**nx_lwm2m_object_delete**: "Delete" メソッド (下記を参照)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-194">**nx_lwm2m_object_delete**: The 'Delete' method, see below.</span></span>
- <span data-ttu-id="e6ab4-195">**nx_lwm2m_object_instances**: オブジェクト インスタンスの NULL で終わるリスト。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-195">**nx_lwm2m_object_instances**: The NULL-terminated list of object instances.</span></span>

<span data-ttu-id="e6ab4-196">NX_LWM2M_OBJECT_INSTANCE 構造体の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-196">The NX_LWM2M_OBJECT_INSTANCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- <span data-ttu-id="e6ab4-197">**nx_lwm2m_object_instance_next**: リスト内の次のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-197">**nx_lwm2m_object_instance_next**: The next instance in the list.</span></span>
- <span data-ttu-id="e6ab4-198">**nx_lwm2m_object_instance_id**: オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-198">**nx_lwm2m_object_instance_id**: The Object Instance ID.</span></span>

<span data-ttu-id="e6ab4-199">オブジェクトでは、LWM2M デバイス管理インターフェイスで定義されている操作 ("Read"、"Discover"、"Write"、"Execute"、"Create"、"Delete") に対応するメソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-199">The Object must implement the methods corresponding to the operations defined by the LWM2M Device Management Interface: 'Read', 'Discover', 'Write', 'Execute', 'Create' and 'Delete'.</span></span> <span data-ttu-id="e6ab4-200">オブジェクトでインスタンスの動的作成がサポートされていない場合は、"Create" および "Delete" メソッドを NULL に設定できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-200">The 'Create' and 'Delete' methods can be set to NULL if the object doesn't support dynamic creation of instances.</span></span>

### <a name="the-read-method"></a><span data-ttu-id="e6ab4-201">"Read" メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ab4-201">The 'Read' Method</span></span>

<span data-ttu-id="e6ab4-202">"Read" メソッドを使用して、オブジェクト インスタンスからリソース値を読み取ります。関数の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-202">The 'Read' method is used to read Resource values from an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

<span data-ttu-id="e6ab4-203">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-203">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e6ab4-204">**object_ptr**: オブジェクト実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-204">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="e6ab4-205">**instance_ptr**: オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-205">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="e6ab4-206">**num_values**: 読み取るリソースの数。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-206">**num_values**: The number of resources to read.</span></span>

- <span data-ttu-id="e6ab4-207">**values_ptr**: 読み取るリソースの ID を格納する NX_LWM2M_RESOURCE の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-207">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="e6ab4-208">戻り時に、配列には対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-208">On return the array is filled with the corresponding types and values.</span></span>

### <a name="the-discover-method"></a><span data-ttu-id="e6ab4-209">"Discover" メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ab4-209">The 'Discover' Method</span></span>

<span data-ttu-id="e6ab4-210">"Discover" メソッドを使用して、オブジェクトで実装されているすべてのリソースのリストを取得します。関数の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-210">The 'Discover' method is used to retrieve the list of all Resources implemented by an Object, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

<span data-ttu-id="e6ab4-211">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-211">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e6ab4-212">**object_ptr**: オブジェクト実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-212">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="e6ab4-213">**instance_ptr**: オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-213">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="e6ab4-214">**num_resources_ptr**: 入力時はターゲット バッファーのサイズ、出力時はバッファーに書き込まれた要素の数。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-214">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>

- <span data-ttu-id="e6ab4-215">**resources_ptr**: 宛先バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-215">**resources_ptr**: Pointer to the destination buffer.</span></span>

<span data-ttu-id="e6ab4-216">リソース情報は、次のように定義された NX_LWM2M_RESOURCE_INFO 構造体で返されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-216">The resource information is returned in a NX_LWM2M_RESOURCE_INFO structure defined as follows:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- <span data-ttu-id="e6ab4-217">**nx_lwm2m_resource_info_id**: リソースの ID。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-217">**nx_lwm2m_resource_info_id**: The ID of the Resource.</span></span>

- <span data-ttu-id="e6ab4-218">**nx_lwm2m_resource_info_flags**: 下記を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-218">**nx_lwm2m_resource_info_flags**: See below.</span></span>

- <span data-ttu-id="e6ab4-219">**nx_lwm2m_resource_info_dim**: 複数リソースのディメンション (NX_LWM2M_RESOURCE_INFO_MULTIPLE フラグが設定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-219">**nx_lwm2m_resource_info_dim**: The dimension of Multiple Resource if the flag NX_LWM2M_RESOURCE_INFO_MULTIPLE is set.</span></span>

<span data-ttu-id="e6ab4-220">*nx_lwm2m_resource_flags* フィールドには、次の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-220">The field *nx_lwm2m_resource_flags* can have to the following values:</span></span>

- <span data-ttu-id="e6ab4-221">0: 読み取り可能な単一リソース。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-221">0: Single readable resource.</span></span>

- <span data-ttu-id="e6ab4-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: 複数リソース。*nx_lwm2m_resource_info_dim* を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: Multiple Resource, *nx_lwm2m_resource_info_dim* must be defined.</span></span>

- <span data-ttu-id="e6ab4-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: 実行可能ファイルまたは読み取り不可能なリソース。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: Executable or Non-Readable Resource.</span></span>

### <a name="the-write-method"></a><span data-ttu-id="e6ab4-224">"Write" メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ab4-224">The 'Write' Method</span></span>

<span data-ttu-id="e6ab4-225">"Write" メソッドを使用して、オブジェクト インスタンスのリソースを更新または置換します。関数の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-225">The 'Write' method is used to update or replace resources of an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

<span data-ttu-id="e6ab4-226">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-226">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e6ab4-227">**object_ptr**: オブジェクト実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-227">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="e6ab4-228">**instance_ptr**: オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-228">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="e6ab4-229">**num_values**: 書き込むリソースの数。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-229">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="e6ab4-230">**values_ptr**: リソース値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-230">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="e6ab4-231">**write_op**: 書き込み操作の種類。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-231">**write_op**: The type of write operations.</span></span>

<span data-ttu-id="e6ab4-232">*write_op* パラメーターには、次の書き込み操作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-232">The following write operations can be specified to the *write_op* parameter :</span></span>

- <span data-ttu-id="e6ab4-233">0 &mdash; 部分更新: 新しい値で提供されるリソースを追加または更新し、他の既存のリソースはそのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-233">0 &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="e6ab4-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; インスタンスの置換: オブジェクト インスタンスを、指定された新しいリソース値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="e6ab4-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; リソースの置換: リソースを、指定された新しいリソース値に置き換えます (複数リソースを置き換えるために使用されます)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="e6ab4-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; インスタンスの作成: 指定されたリソース値を使用して、新しく作成されたオブジェクト インスタンスを初期化します (*nx_lwm2m_object_create* メソッドから呼び出されます)。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: initializes the newly created Object Instance with the provided resource values (called from the *nx_lwm2m_object_create* method).</span></span>

- <span data-ttu-id="e6ab4-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; ブートストラップ書き込み: ブートストラップ シーケンス中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: called during Bootstrap sequence.</span></span>

### <a name="the-execute-method"></a><span data-ttu-id="e6ab4-238">"Execute" メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ab4-238">The 'Execute' Method</span></span>

<span data-ttu-id="e6ab4-239">"Execute" メソッドは、オブジェクト リソースの実行を実装します。関数の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-239">The 'Execute' method implements the execution of an Object Resource, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

<span data-ttu-id="e6ab4-240">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-240">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e6ab4-241">**object_ptr**: オブジェクト実装へのポインター</span><span class="sxs-lookup"><span data-stu-id="e6ab4-241">**object_ptr**: Pointer to the Object implementation</span></span>
- <span data-ttu-id="e6ab4-242">**instance_ptr**: オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-242">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="e6ab4-243">**resource_id**: リソース ID。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-243">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="e6ab4-244">**arguments_ptr**: 実行操作の引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-244">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="e6ab4-245">*arguments_length* が 0 の場合は、NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-245">Can be NULL if *arguments_length* is zero.</span></span>
- <span data-ttu-id="e6ab4-246">**arguments_length**: 引数の長さ。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-246">**arguments_length**: The length of the arguments.</span></span>

<span data-ttu-id="e6ab4-247">この関数では、リソース ID が存在しない場合は NX_LWM2M_NOT_FOUND を返し、実行をサポートしていない場合は NX_LWM2M_METHOD_NOT_ALLOWED を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-247">The function must return NX_LWM2M_NOT_FOUND if the Resource ID doesn't exist, or NX_LWM2M_METHOD_NOT_ALLOWED if it doesn't support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="e6ab4-248">"Create" メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ab4-248">The 'Create' Method</span></span>

<span data-ttu-id="e6ab4-249">"Create" メソッドは、新しいオブジェクト インスタンスの作成を実装します。関数の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-249">The 'Create' method implements the creation of a new Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

<span data-ttu-id="e6ab4-250">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-250">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e6ab4-251">**object_ptr**: オブジェクト実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-251">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="e6ab4-252">**instance_id**: 新しいインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-252">**instance_id**: The ID of the new Instance.</span></span>
- <span data-ttu-id="e6ab4-253">**num_values**: 初期化するリソースの数。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-253">**num_values**: The number of resources to initialize.</span></span>
- <span data-ttu-id="e6ab4-254">**values_ptr**: リソース値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-254">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="e6ab4-255">**instance_ptr**: 作成されたインスタンスの宛先ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-255">**instance_ptr**: Pointer to the destination pointer of the created instance.</span></span>
- <span data-ttu-id="e6ab4-256">**bootstrap**: ブートストラップ シーケンスから呼び出される場合は True。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-256">**bootstrap**: True if called from bootstrap sequence.</span></span>

<span data-ttu-id="e6ab4-257">オブジェクトは、リソース値の指定されたリストを使用して、新しいオブジェクト インスタンスを割り当てて初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-257">The Object must allocate and initialiaze a new Object instance, using the provided list of resource values.</span></span>

### <a name="the-delete-method"></a><span data-ttu-id="e6ab4-258">"Delete" メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ab4-258">The 'Delete' Method</span></span>

<span data-ttu-id="e6ab4-259">"Delete" メソッドは、オブジェクト インスタンスの削除を実装します。関数の定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-259">The 'Delete' method implements the deletion of an object instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

<span data-ttu-id="e6ab4-260">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-260">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e6ab4-261">**object_ptr**: オブジェクト実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-261">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="e6ab4-262">**instance_ptr**: オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-262">**instance_ptr**: Pointer to the Object Instance.</span></span>

<span data-ttu-id="e6ab4-263">成功した場合、オブジェクトはオブジェクト インスタンス データとインスタンスによって割り当てられたその他のリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-263">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a><span data-ttu-id="e6ab4-264">LWM2M クライアントへのオブジェクト実装およびインスタンスの追加</span><span class="sxs-lookup"><span data-stu-id="e6ab4-264">Adding Object Implementations and Instances to the LWM2M Client</span></span>

<span data-ttu-id="e6ab4-265">アプリケーションでは、***nx_lwm2m_client_object_add*** サービスを呼び出すことによって、新しいオブジェクト実装を LWM2M クライアントに追加できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-265">The application can add new object implementation to the LWM2M Client by calling the ***nx_lwm2m_client_object_add*** service.</span></span>

<span data-ttu-id="e6ab4-266">オブジェクトでインスタンスの動的作成がサポートされていない場合 (単一インスタンスのみのオブジェクトの場合など)、オブジェクト構造体の *nx_lwm2m_object_instances* フィールドは、静的インスタンス構造体のリストを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-266">If the Object doesn't support dynamic creation of Instances, for example if it's a single instance only Object, the *nx_lwm2m_object_instances* field of the object structure should point to the list of the static instances structures.</span></span>

<span data-ttu-id="e6ab4-267">オブジェクトでインスタンスの動的作成がサポートされている場合は、オブジェクトの "Create" メソッドを呼び出すために、*nx_lwm2m_object_instances* を NULL に設定し、代わりに ***nx_lwm2m_client_object_create*** サービスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-267">If the Object supports dynamic instance creation, *nx_lwm2m_object_instances* should be set to NULL and the ***nx_lwm2m_client_object_create*** service should be used instead in order to call the 'Create' method of the object.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="e6ab4-268">LWM2M クライアント アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="e6ab4-268">Example of LWM2M Client Application</span></span>

<span data-ttu-id="e6ab4-269">次のコードは、温度センサーとライト スイッチで構成されるカスタム デバイスを実装する単純な LWM2M クライアント アプリケーションの例です。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-269">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="e6ab4-270">このデバイスを使用すると、サーバーは、温度センサーの値とライト スイッチのブール値を読み取り、ライト スイッチをオン/オフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="e6ab4-270">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
