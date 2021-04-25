---
title: 第 3 章 - LWM2M クライアントの機能の説明
description: この章では、LWM2M クライアントの機能について説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810754"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="81dd8-103">第 3 章  LWM2M クライアントの機能の説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="81dd8-104">この章では、LWM2M クライアントの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="81dd8-105">LWM2M クライアントの初期化</span><span class="sxs-lookup"><span data-stu-id="81dd8-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="81dd8-106">LWM2M クライアントは、***nx_lwm2m_client_create*** サービスを呼び出すことによって初期化されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="81dd8-107">LWM2M クライアントは独自のスレッドで実行され、コールバックを使用するか、アプリケーションによって実装されたカスタム オブジェクトのメソッドを呼び出すことによって、アプリケーションにいくつかのイベントを報告できます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="81dd8-108">さらに、1 つ以上のサーバーとの通信を有効にするために、***nx_lwm2m_client_session_create*** を呼び出すことによって、LWM2M クライアント セッションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="81dd8-109">セッションは、ブートストラップ サーバーまたは LWM2M サーバー (デバイス管理) という 2 つの異なる種類のサーバーと通信できます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="81dd8-110">ブートストラップ サーバー セッション</span><span class="sxs-lookup"><span data-stu-id="81dd8-110">Bootstrap Server Session</span></span>

<span data-ttu-id="81dd8-111">ブートストラップ サーバーとの通信セッションを使用して、LWM2M クライアントに重要な情報を提供し、LWM2M クライアントが 1 つ以上の LWM2M サーバーに対して "登録" 操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="81dd8-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="81dd8-112">この種類のサーバーは、クライアントによって開始され、サーバーによって開始されたブートストラップ モードで使用されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="81dd8-113">アプリケーションから ***nx_lwm2m_client_session_bootstrap** _ または _*_nx_lwm2m_client_session_bootstrap_dtls_\*_ を呼び出すことによってブートストラップ セッションを開始できます。サーバーの IP アドレスとポート番号、およびオプションのセキュリティ オブジェクト インスタンス ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="81dd8-114">_*_nx_lwm2m_client_session_bootstrap_*_ 関数は、セキュリティで保護されていない通信を使用します。一方、_ *_nx_lwm2m_client_session_bootstrap_dtls_*\* は、サーバーとのセキュリティで保護された dtls 接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="81dd8-115">ブートストラップ操作が成功した場合、ブートストラップ サーバーでは、ブートストラップ サーバーと LWM2M サーバーのセキュリティ オブジェクト インスタンス、および LWM2M サーバーのサーバー オブジェクト インスタンスが作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="81dd8-116">アプリケーションから ***nx_lwm2m_client_session_register_info_get*** が呼び出されて LWM2M サーバーの情報が取得され、この情報を使用して LWM2M サーバーとのセッションが確立されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="81dd8-117">ブートストラップ データは、デバイスの次回の再起動時に LWM2M クライアントを構成するために、アプリケーションによって不揮発性メモリに保存される必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="81dd8-118">LWM2M サーバー セッション</span><span class="sxs-lookup"><span data-stu-id="81dd8-118">LWM2M Server Session</span></span>

<span data-ttu-id="81dd8-119">LWM2M サーバーとの通信セッションは、登録、デバイス管理、およびサービスの有効化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="81dd8-120">アプリケーションから ***nx_lwm2m_client_session_register** _ または _*_nx_lwm2m_client_session_register_dtls_\*_ が呼び出されることによって LWM2M クライアントがサーバーに登録されます。また、サーバーの IP アドレスとポート番号、および既存のサーバー オブジェクト インスタンスに対応する短いサーバー ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="81dd8-121">_*_nx_lwm2m_client_session_register_*_ 関数では、セキュリティで保護されていない通信が使用されます。一方、_ *_nx_lwm2m_client_session_register_dtls_*\* によって、サーバーとのセキュリティで保護された dtls 接続が確立されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="81dd8-122">アプリケーションから ***nx_lwm2m_client_session_deregister** _ が呼び出されて LWM2M クライアントが登録解除され、_*_nx_lwm2m_client_session_update_\*\* が呼び出されて、クライアントに "更新" メッセージを送信するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="81dd8-123">セッション状態のコールバック</span><span class="sxs-lookup"><span data-stu-id="81dd8-123">Session State Callback</span></span>

<span data-ttu-id="81dd8-124">アプリケーションは、セッションの作成時にコールバックを登録します。これは、セッションの状態が更新されたときに呼び出されます。コールバック関数 **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** には、次のプロトタイプがあります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="81dd8-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span><span class="sxs-lookup"><span data-stu-id="81dd8-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="81dd8-126">次の状態が定義されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-126">The following states are defined.</span></span>

| <span data-ttu-id="81dd8-127">Session&nbsp;State</span><span class="sxs-lookup"><span data-stu-id="81dd8-127">Session&nbsp;State</span></span> | <span data-ttu-id="81dd8-128">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="81dd8-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="81dd8-130">セッション作成後の初期状態です。</span><span class="sxs-lookup"><span data-stu-id="81dd8-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="81dd8-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="81dd8-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="81dd8-132">クライアントは、"Hold Off" タイマーまたはサーバー開始ブートストラップの有効期限が切れるのを待機しています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="81dd8-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="81dd8-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="81dd8-134">クライアントが "要求" メッセージをブートストラップ サーバー (クライアントが開始したブートストラップ) に送信しました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="81dd8-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="81dd8-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="81dd8-136">クライアントがブートストラップ サーバーからデータを受信しています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="81dd8-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="81dd8-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="81dd8-138">ブートストラップ サーバーから "完了" メッセージが送信されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="81dd8-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="81dd8-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="81dd8-140">ブートストラップ セッションが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="81dd8-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="81dd8-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="81dd8-142">クライアントから LWM2M サーバーに "登録" メッセージが送信されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="81dd8-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="81dd8-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="81dd8-144">クライアントが LWM2M サーバーに登録されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="81dd8-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="81dd8-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="81dd8-146">クライアントから LWM2M サーバーに "更新" メッセージが送信されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="81dd8-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="81dd8-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="81dd8-148">クライアントから LWM2M サーバーに "登録解除" メッセージが送信されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="81dd8-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="81dd8-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="81dd8-150">クライアントが、LWM2M サーバーから登録解除されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="81dd8-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="81dd8-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="81dd8-152">LWM2M サーバーが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="81dd8-153">無効化タイマーの有効期限が切れると、'Register' が送信されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="81dd8-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="81dd8-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="81dd8-155">LWM2M サーバーへの登録または更新操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="81dd8-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="81dd8-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="81dd8-157">LWM2M サーバーに対応するサーバー オブジェクト インスタンスが削除されました。</span><span class="sxs-lookup"><span data-stu-id="81dd8-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="81dd8-158">エラーが発生した場合、アプリケーションから ***nx_lwm2m_client_session_error_get*** が呼び出されることによってエラーの原因を取得できます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="81dd8-159">ローカル デバイス管理</span><span class="sxs-lookup"><span data-stu-id="81dd8-159">Local Device Management</span></span>

<span data-ttu-id="81dd8-160">アプリケーションからは、ローカル デバイス管理機能を使用して、LWM2M クライアントのオブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="81dd8-161">次の関数が提供されています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-161">The following functions are provided.</span></span>

| <span data-ttu-id="81dd8-162">関数&nbsp;名</span><span class="sxs-lookup"><span data-stu-id="81dd8-162">Function&nbsp;Name</span></span> | <span data-ttu-id="81dd8-163">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="81dd8-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="81dd8-165">オブジェクト インスタンスからリソースを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="81dd8-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="81dd8-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="81dd8-167">オブジェクト インスタンスのリソースのリストを取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="81dd8-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="81dd8-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="81dd8-169">オブジェクト インスタンスにリソースを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="81dd8-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="81dd8-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="81dd8-171">オブジェクト インスタンスのリソースに対して実行操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="81dd8-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="81dd8-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="81dd8-173">新しいオブジェクト インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="81dd8-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="81dd8-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="81dd8-175">既存のオブジェクト インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="81dd8-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="81dd8-177">LWM2M クライアントによって次のオブジェクト ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="81dd8-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="81dd8-179">オブジェクトの次のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="81dd8-180">リソース情報</span><span class="sxs-lookup"><span data-stu-id="81dd8-180">Resource Information</span></span>

<span data-ttu-id="81dd8-181">オブジェクトへの読み取りと書き込みを行う場合、リソースは NX_LWM2M_CLIENT_RESOURCE 構造体によって表されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="81dd8-182">この構造体には、リソースまたはインスタンスの ID とその値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="81dd8-183">リソースの情報と値を設定するために、次の関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="81dd8-184">関数&nbsp;名</span><span class="sxs-lookup"><span data-stu-id="81dd8-184">Function&nbsp;Name</span></span> | <span data-ttu-id="81dd8-185">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="81dd8-187">リソース情報の設定: リソース ID と操作: 読み取り、書き込み、実行可能。</span><span class="sxs-lookup"><span data-stu-id="81dd8-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="81dd8-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="81dd8-189">リソース値を文字列として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="81dd8-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="81dd8-191">リソース値を 32 ビット整数として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="81dd8-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="81dd8-193">リソース値を 64 ビット整数として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="81dd8-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="81dd8-195">リソース値を 32 ビット浮動小数点数として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="81dd8-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="81dd8-197">リソース値を 64 ビット浮動小数点数として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="81dd8-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="81dd8-199">リソース値をブール値として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="81dd8-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="81dd8-201">リソース値をオブジェクト リンクとして設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="81dd8-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="81dd8-203">リソース値を不透明として設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="81dd8-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="81dd8-205">リソース値を複数のリソースのインスタンスとして設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="81dd8-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="81dd8-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="81dd8-207">検出する複数のリソースのリソース ディメンションを設定します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="81dd8-208">リソースの情報と値を取得するために、次の関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="81dd8-209">関数&nbsp;名</span><span class="sxs-lookup"><span data-stu-id="81dd8-209">Function&nbsp;Name</span></span> | <span data-ttu-id="81dd8-210">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="81dd8-212">リソース情報の取得: リソース ID と操作: 読み取り、書き込み、実行可能。</span><span class="sxs-lookup"><span data-stu-id="81dd8-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="81dd8-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="81dd8-214">文字列リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="81dd8-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="81dd8-216">32 ビット整数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="81dd8-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="81dd8-218">64 ビット整数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="81dd8-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="81dd8-220">32 ビット浮動小数点数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="81dd8-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="81dd8-222">64 ビット浮動小数点数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="81dd8-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="81dd8-224">ブール値リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="81dd8-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="81dd8-226">オブジェクト リンク リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="81dd8-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="81dd8-228">不透明なリソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="81dd8-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="81dd8-230">複数のリソースのリソース インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="81dd8-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="81dd8-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="81dd8-232">複数のリソースのリソース ディメンションを取得します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="81dd8-233">オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="81dd8-233">Object Implementation</span></span>

<span data-ttu-id="81dd8-234">LWM2M クライアントによって、必須の OMA LWM2M オブジェクトが実装されます: セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)。</span><span class="sxs-lookup"><span data-stu-id="81dd8-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="81dd8-235">その他のデバイス固有のオブジェクトは、アプリケーションによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="81dd8-236">オブジェクトを定義するには、2 つのデータ構造体を使用します。NX_LWM2M_CLIENT_OBJECT 構造体は、オブジェクト ID とオブジェクト メソッドを含むオブジェクトの実装を定義し、NX_LWM2M_CLIENT_OBJECT_INSTANCE 構造体はオブジェクト インスタンスのデータを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="81dd8-237">次の関数が提供されています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-237">The following functions are provided.</span></span>

| <span data-ttu-id="81dd8-238">関数&nbsp;名</span><span class="sxs-lookup"><span data-stu-id="81dd8-238">Function&nbsp;Name</span></span> | <span data-ttu-id="81dd8-239">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="81dd8-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="81dd8-241">オブジェクトの実装を LwM2M クライアントに追加します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="81dd8-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="81dd8-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="81dd8-243">オブジェクトの実装を LwM2M クライアントから削除します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="81dd8-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="81dd8-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="81dd8-245">オブジェクト インスタンスをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="81dd8-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="81dd8-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="81dd8-247">オブジェクト インスタンスをオブジェクトから削除します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="81dd8-248">オブジェクト メソッドのコールバック関数には、次に示すシグネチャがあります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="81dd8-249">"Read" メソッド</span><span class="sxs-lookup"><span data-stu-id="81dd8-249">The ‘Read’ Method</span></span>

<span data-ttu-id="81dd8-250">"Read" メソッドは、オブジェクト インスタンスからリソース値を読み取るために使用されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="81dd8-251">パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="81dd8-252">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dd8-252">Parameter</span></span> | <span data-ttu-id="81dd8-253">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-254">**operation**</span><span class="sxs-lookup"><span data-stu-id="81dd8-254">**operation**</span></span> | <span data-ttu-id="81dd8-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="81dd8-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="81dd8-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-256">**object_ptr**</span></span> | <span data-ttu-id="81dd8-257">オブジェクトの実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="81dd8-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-258">**instance_ptr**</span></span> | <span data-ttu-id="81dd8-259">オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="81dd8-260">**resource**</span><span class="sxs-lookup"><span data-stu-id="81dd8-260">**resource**</span></span> | <span data-ttu-id="81dd8-261">読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="81dd8-262">返されると、配列には対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="81dd8-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="81dd8-263">**resource_count**</span></span> | <span data-ttu-id="81dd8-264">読み取るリソースの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="81dd8-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-265">**args_ptr**</span></span> | <span data-ttu-id="81dd8-266">読み取り用の未使用のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="81dd8-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="81dd8-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="81dd8-267">**args_length**</span></span> | <span data-ttu-id="81dd8-268">読み取り用の未使用のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="81dd8-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="81dd8-269">"Discover" メソッド</span><span class="sxs-lookup"><span data-stu-id="81dd8-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="81dd8-270">"Discover" メソッドは、オブジェクトによって実装されているすべてのリソースのリスト取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="81dd8-271">パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="81dd8-272">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dd8-272">Parameter</span></span> | <span data-ttu-id="81dd8-273">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-274">**operation**</span><span class="sxs-lookup"><span data-stu-id="81dd8-274">**operation**</span></span> | <span data-ttu-id="81dd8-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="81dd8-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="81dd8-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-276">**object_ptr**</span></span> | <span data-ttu-id="81dd8-277">オブジェクトの実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="81dd8-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-278">**instance_ptr**</span></span> | <span data-ttu-id="81dd8-279">オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="81dd8-280">**resource**</span><span class="sxs-lookup"><span data-stu-id="81dd8-280">**resource**</span></span> | <span data-ttu-id="81dd8-281">NX_LWM2M_CLIENT_RESOURCE の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="81dd8-282">返されると、配列には対応するリソース情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="81dd8-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="81dd8-283">**resource_count**</span></span> | <span data-ttu-id="81dd8-284">検出するリソースの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="81dd8-285">戻り時には、このパラメーターを true 値として更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="81dd8-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-286">**args_ptr**</span></span> | <span data-ttu-id="81dd8-287">検出用の未使用のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="81dd8-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="81dd8-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="81dd8-288">**args_length**</span></span> | <span data-ttu-id="81dd8-289">検出用の未使用のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="81dd8-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="81dd8-290">"Write" メソッド</span><span class="sxs-lookup"><span data-stu-id="81dd8-290">The ‘Write’ Method</span></span>

<span data-ttu-id="81dd8-291">"Write" メソッドは、オブジェクト インスタンスのリソースを更新または置換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="81dd8-292">パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="81dd8-293">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dd8-293">Parameter</span></span>  | <span data-ttu-id="81dd8-294">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-295">**operation**</span><span class="sxs-lookup"><span data-stu-id="81dd8-295">**operation**</span></span> | <span data-ttu-id="81dd8-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="81dd8-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="81dd8-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-297">**object_ptr**</span></span> | <span data-ttu-id="81dd8-298">オブジェクトの実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="81dd8-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-299">**instance_ptr**</span></span> | <span data-ttu-id="81dd8-300">オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="81dd8-301">**resource**</span><span class="sxs-lookup"><span data-stu-id="81dd8-301">**resource**</span></span> | <span data-ttu-id="81dd8-302">読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="81dd8-303">返されると、配列には対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="81dd8-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="81dd8-304">**resource_count**</span></span> | <span data-ttu-id="81dd8-305">検出するリソースの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="81dd8-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-306">**args_ptr**</span></span> | <span data-ttu-id="81dd8-307">書き込みフラグ。</span><span class="sxs-lookup"><span data-stu-id="81dd8-307">Write flags.</span></span> |
| <span data-ttu-id="81dd8-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="81dd8-308">**args_length**</span></span> | <span data-ttu-id="81dd8-309">引数の長さ。</span><span class="sxs-lookup"><span data-stu-id="81dd8-309">The length of the arguments.</span></span> |

<span data-ttu-id="81dd8-310">次の書き込み操作を *flag* パラメーターに対して指定できます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="81dd8-311">Operation</span><span class="sxs-lookup"><span data-stu-id="81dd8-311">Operation</span></span> | <span data-ttu-id="81dd8-312">アクション</span><span class="sxs-lookup"><span data-stu-id="81dd8-312">Action</span></span> | <span data-ttu-id="81dd8-313">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="81dd8-314">0</span><span class="sxs-lookup"><span data-stu-id="81dd8-314">0</span></span> | <span data-ttu-id="81dd8-315">部分更新</span><span class="sxs-lookup"><span data-stu-id="81dd8-315">Partial Update</span></span> | <span data-ttu-id="81dd8-316">新しい値で提供されるリソースを追加または更新し、他の既存のリソースを変更せずにそのままにします。</span><span class="sxs-lookup"><span data-stu-id="81dd8-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="81dd8-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="81dd8-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="81dd8-318">インスタンスの置換</span><span class="sxs-lookup"><span data-stu-id="81dd8-318">Replace Instance</span></span> | <span data-ttu-id="81dd8-319">オブジェクト インスタンスを、提供された新しいリソース値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="81dd8-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="81dd8-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="81dd8-321">リソースの置換</span><span class="sxs-lookup"><span data-stu-id="81dd8-321">Replace Resource</span></span> | <span data-ttu-id="81dd8-322">リソースを、提供された新しいリソース値に置き換えます (複数のリソースを置き換えるために使用されます)。</span><span class="sxs-lookup"><span data-stu-id="81dd8-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="81dd8-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="81dd8-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="81dd8-324">Create Instance]\(基本モード: インスタンスの作成\)</span><span class="sxs-lookup"><span data-stu-id="81dd8-324">Create Instance</span></span> | <span data-ttu-id="81dd8-325">指定されたリソース値を使用して、新しく作成されたオブジェクト インスタンスを初期化します (**_nx_lwm2m_object_create_** メソッドから呼び出されます)。</span><span class="sxs-lookup"><span data-stu-id="81dd8-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="81dd8-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="81dd8-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="81dd8-327">ブートストラップ書き込み</span><span class="sxs-lookup"><span data-stu-id="81dd8-327">Bootstrap Write</span></span> | <span data-ttu-id="81dd8-328">ブートストラップ シーケンス中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="81dd8-329">"Execute" メソッド</span><span class="sxs-lookup"><span data-stu-id="81dd8-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="81dd8-330">"Execute" メソッドは、オブジェクト リソースの実行を実装します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="81dd8-331">入力パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="81dd8-332">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dd8-332">Parameter</span></span>  | <span data-ttu-id="81dd8-333">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-334">**operation**</span><span class="sxs-lookup"><span data-stu-id="81dd8-334">**operation**</span></span> | <span data-ttu-id="81dd8-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="81dd8-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="81dd8-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-336">**object_ptr**</span></span> | <span data-ttu-id="81dd8-337">オブジェクトの実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="81dd8-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-338">**instance_ptr**</span></span> | <span data-ttu-id="81dd8-339">オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="81dd8-340">**resource**</span><span class="sxs-lookup"><span data-stu-id="81dd8-340">**resource**</span></span> | <span data-ttu-id="81dd8-341">読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="81dd8-342">返されると、配列には対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="81dd8-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="81dd8-343">**resource_count**</span></span> | <span data-ttu-id="81dd8-344">検出するリソースの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="81dd8-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-345">**args_ptr**</span></span> | <span data-ttu-id="81dd8-346">引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="81dd8-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="81dd8-347">**args_length**</span></span> | <span data-ttu-id="81dd8-348">引数の長さ。</span><span class="sxs-lookup"><span data-stu-id="81dd8-348">The length of the arguments.</span></span>  |

<span data-ttu-id="81dd8-349">関数は、リソース ID が存在しない場合は **NX_LWM2M_CLIENT_NOT_FOUND** を返し、実行をサポートしていない場合は **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="81dd8-350">"Create" メソッド</span><span class="sxs-lookup"><span data-stu-id="81dd8-350">The ‘Create’ Method</span></span>

<span data-ttu-id="81dd8-351">"Create" メソッドは、新しいオブジェクト インスタンスの作成を実装します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="81dd8-352">入力パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="81dd8-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="81dd8-353">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dd8-353">Parameter</span></span>  | <span data-ttu-id="81dd8-354">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-355">**operation**</span><span class="sxs-lookup"><span data-stu-id="81dd8-355">**operation**</span></span> | <span data-ttu-id="81dd8-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="81dd8-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="81dd8-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-357">**object_ptr**</span></span> | <span data-ttu-id="81dd8-358">オブジェクトの実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="81dd8-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-359">**instance_ptr**</span></span> | <span data-ttu-id="81dd8-360">未使用のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-360">Unused parameter.</span></span> |
| <span data-ttu-id="81dd8-361">**resource**</span><span class="sxs-lookup"><span data-stu-id="81dd8-361">**resource**</span></span> | <span data-ttu-id="81dd8-362">読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="81dd8-363">返されると、配列には対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="81dd8-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="81dd8-364">**resource_count**</span></span> | <span data-ttu-id="81dd8-365">検出するリソースの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="81dd8-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-366">**args_ptr**</span></span> | <span data-ttu-id="81dd8-367">オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="81dd8-367">Object instance id.</span></span> |
| <span data-ttu-id="81dd8-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="81dd8-368">**args_length**</span></span> | <span data-ttu-id="81dd8-369">引数の長さ。</span><span class="sxs-lookup"><span data-stu-id="81dd8-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="81dd8-370">"Delete" メソッド</span><span class="sxs-lookup"><span data-stu-id="81dd8-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="81dd8-371">"Delete" メソッドは、オブジェクト インスタンスの削除を実装します。入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="81dd8-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="81dd8-372">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81dd8-372">Parameter</span></span>  | <span data-ttu-id="81dd8-373">説明</span><span class="sxs-lookup"><span data-stu-id="81dd8-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81dd8-374">**operation**</span><span class="sxs-lookup"><span data-stu-id="81dd8-374">**operation**</span></span> | <span data-ttu-id="81dd8-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="81dd8-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="81dd8-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-376">**object_ptr**</span></span> | <span data-ttu-id="81dd8-377">オブジェクトの実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="81dd8-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-378">**instance_ptr**</span></span> | <span data-ttu-id="81dd8-379">オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="81dd8-380">**resource**</span><span class="sxs-lookup"><span data-stu-id="81dd8-380">**resource**</span></span> | <span data-ttu-id="81dd8-381">未使用のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-381">Unused parameter.</span></span> |
| <span data-ttu-id="81dd8-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="81dd8-382">**resource_count**</span></span> | <span data-ttu-id="81dd8-383">未使用のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-383">Unused parameter.</span></span> |
| <span data-ttu-id="81dd8-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="81dd8-384">**args_ptr**</span></span> | <span data-ttu-id="81dd8-385">未使用のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-385">Unused parameter.</span></span> |
| <span data-ttu-id="81dd8-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="81dd8-386">**args_length**</span></span> | <span data-ttu-id="81dd8-387">未使用のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="81dd8-387">Unused parameter.</span></span> |

<span data-ttu-id="81dd8-388">成功した場合、オブジェクトはオブジェクト インスタンスのデータおよびインスタンスによって割り当てられたその他のリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81dd8-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="81dd8-389">LWM2M クライアント アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="81dd8-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="81dd8-390">次のコードは、温度センサーとライト スイッチで構成されるカスタム デバイスを実装する単純な LWM2M クライアント アプリケーションの例です。</span><span class="sxs-lookup"><span data-stu-id="81dd8-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="81dd8-391">このデバイスを使用すると、サーバーは、温度センサーの値とライト スイッチのブール値を読み取り、ライトスイッチのオン/オフに設定できます。</span><span class="sxs-lookup"><span data-stu-id="81dd8-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```