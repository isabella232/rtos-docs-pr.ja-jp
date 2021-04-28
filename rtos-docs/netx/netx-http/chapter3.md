---
title: 第 3 章 - NetX HTTP サービスの説明
description: この章には、すべての NetX HTTP サービス (以下に記載) の説明がアルファベット順で含まれています。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811528"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="65269-103">第 3 章 - NetX HTTP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="65269-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="65269-104">この章には、すべての NetX HTTP サービス (以下に記載) の説明がアルファベット順で含まれています。</span><span class="sxs-lookup"><span data-stu-id="65269-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="65269-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="65269-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="65269-106">**HTTP クライアントのサービス:**</span><span class="sxs-lookup"><span data-stu-id="65269-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="65269-107">nx_http_client_create *HTTP クライアント インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="65269-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="65269-108">nx_http_client_delete *HTTP クライアント インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="65269-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="65269-109">nx_http_client_get_start *HTTP GET 要求を開始する*</span><span class="sxs-lookup"><span data-stu-id="65269-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="65269-110">nx_http_client_get_start_extended *HTTP GET 要求を開始する*</span><span class="sxs-lookup"><span data-stu-id="65269-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="65269-111">nx_http_client_get_packet *次のリソース データ パケットを取得する*</span><span class="sxs-lookup"><span data-stu-id="65269-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="65269-112">nx_http_client_put_start *HTTP PUT 要求を開始する*</span><span class="sxs-lookup"><span data-stu-id="65269-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="65269-113">nx_http_client_put_start_extended *HTTP PUT 要求を開始する*</span><span class="sxs-lookup"><span data-stu-id="65269-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="65269-114">nx_http_client_put_packet *次のリソース データ パケットを送信する*</span><span class="sxs-lookup"><span data-stu-id="65269-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="65269-115">*nx_http_client_set_connect_port* *HTTP サーバーに接続するポートを変更する*</span><span class="sxs-lookup"><span data-stu-id="65269-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="65269-116">**HTTP サーバーのサービス:**</span><span class="sxs-lookup"><span data-stu-id="65269-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="65269-117">nx_http_server_cache_info_callback_set *指定された URL の有効期間と最終更新日を取得するコールバックを設定する*</span><span class="sxs-lookup"><span data-stu-id="65269-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="65269-118">nx_http_server_callback_data_send *コールバック関数から HTTP データを送信する*</span><span class="sxs-lookup"><span data-stu-id="65269-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="65269-119">nx_http_server_callback_generate_response_header *コールバック関数内で応答ヘッダーを作成する*</span><span class="sxs-lookup"><span data-stu-id="65269-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="65269-120">nx_http_server_callback_generate_response_header_extended *コールバック関数内で応答ヘッダーを作成する*</span><span class="sxs-lookup"><span data-stu-id="65269-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="65269-121">nx_http_server_callback_packet_send *HTTP コールバックから HTTP パケットを送信する*</span><span class="sxs-lookup"><span data-stu-id="65269-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="65269-122">nx_http_server_callback_response_send *コールバック関数から応答を送信する*</span><span class="sxs-lookup"><span data-stu-id="65269-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="65269-123">nx_http_server_callback_response_send_extended *コールバック関数から応答を送信する*</span><span class="sxs-lookup"><span data-stu-id="65269-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="65269-124">nx_http_server_content_get *要求からコンテンツを取得する*</span><span class="sxs-lookup"><span data-stu-id="65269-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="65269-125">nx_http_server_content_get_extended *要求からコンテンツを取得する (空 (コンテンツの長さがゼロ) の要求がサポートされます)*</span><span class="sxs-lookup"><span data-stu-id="65269-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="65269-126">nx_http_server_content_length_get *要求のコンテンツの長さを取得する*</span><span class="sxs-lookup"><span data-stu-id="65269-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="65269-127">nx_http_server_content_length_get_extended *要求のコンテンツの長さを取得する (空 (コンテンツの長さがゼロ) の要求がサポートされます)*</span><span class="sxs-lookup"><span data-stu-id="65269-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="65269-128">nx_http_server_create *HTTP サーバー インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="65269-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="65269-129">nx_http_server_delete *HTTP サーバー インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="65269-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="65269-130">nx_http_server_get_entity_content *URL のエンティティ コンテンツのサイズと場所を返す*</span><span class="sxs-lookup"><span data-stu-id="65269-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="65269-131">nx_http_server_get_entity_header *指定されたバッファーに URL エンティティ ヘッダーを抽出する*</span><span class="sxs-lookup"><span data-stu-id="65269-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="65269-132">nx_http_server_gmt_callback_set *GMT の日付と時刻を取得するコールバックを設定する*</span><span class="sxs-lookup"><span data-stu-id="65269-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="65269-133">nx_http_server_invalid_userpassword_notify_set *クライアント要求で無効なユーザー名とパスワードを受信した場合のコールバックを設定する*</span><span class="sxs-lookup"><span data-stu-id="65269-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="65269-134">nx_http_server_mime_maps_additional_set *HTML 用の追加の MIME マップを定義する*</span><span class="sxs-lookup"><span data-stu-id="65269-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="65269-135">nx_http_server_packet_content_find *HTTP ヘッダーからコンテンツの長さを抽出し、コンテンツ データの先頭にポインターを設定する*</span><span class="sxs-lookup"><span data-stu-id="65269-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="65269-136">nx_http_server_packet_get *クライアント パケットを直接受信する*</span><span class="sxs-lookup"><span data-stu-id="65269-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="65269-137">nx_http_server_param_get *要求からパラメーターを取得する*</span><span class="sxs-lookup"><span data-stu-id="65269-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="65269-138">nx_http_server_query_get *要求からクエリを取得する*</span><span class="sxs-lookup"><span data-stu-id="65269-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="65269-139">nx_http_server_start *HTTP サーバーを起動する*</span><span class="sxs-lookup"><span data-stu-id="65269-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="65269-140">nx_http_server_stop *HTTP サーバーを停止する*</span><span class="sxs-lookup"><span data-stu-id="65269-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="65269-141">nx_http_server_type_get *ヘッダーから HTTP の種類 (text/plain など) を抽出する*</span><span class="sxs-lookup"><span data-stu-id="65269-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="65269-142">nx_http_server_type_get_extended *ヘッダーから HTTP の種類 (text/plain など) を抽出する*</span><span class="sxs-lookup"><span data-stu-id="65269-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="65269-143">nx_http_server_digest_authenticate_notify_set *ダイジェスト認証コールバック関数を設定する*</span><span class="sxs-lookup"><span data-stu-id="65269-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="65269-144">nx_http_server_authentication_check_set *認証確認コールバック関数を設定する*</span><span class="sxs-lookup"><span data-stu-id="65269-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="65269-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="65269-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="65269-146">HTTP クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="65269-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="65269-147">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="65269-148">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-148">**Description**</span></span>

<span data-ttu-id="65269-149">このサービスは、指定された IP インスタンスに HTTP クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="65269-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="65269-150">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-150">**Input Parameters**</span></span>

- <span data-ttu-id="65269-151">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-152">**client_name** HTTP クライアント インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="65269-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="65269-153">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="65269-154">**pool_ptr** 既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="65269-155">このプール内のパケットはペイロードが応答ヘッダー全体を処理するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="65269-156">これは *nx_http_client.h* 内の NX_HTTP_CLIENT_MIN_PACKET_SIZE によって定義されています。</span><span class="sxs-lookup"><span data-stu-id="65269-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="65269-157">**window_size** クライアントの TCP ソケット受信ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="65269-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="65269-158">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-158">**Return Values**</span></span>

- <span data-ttu-id="65269-159">**NX_SUCCESS** (0x00) HTTP クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="65269-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="65269-160">NX_PTR_ERROR (0x16) HTTP、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="65269-161">NX_HTTP_POOL_ERROR (0xE9) パケット プールのペイロード サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="65269-162">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-162">**Allowed From**</span></span>

<span data-ttu-id="65269-163">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="65269-163">Initialization, Threads</span></span>

<span data-ttu-id="65269-164">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="65269-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="65269-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="65269-166">HTTP クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="65269-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="65269-167">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="65269-168">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-168">**Description**</span></span>

<span data-ttu-id="65269-169">このサービスは、以前に作成された HTTP クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="65269-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="65269-170">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-170">**Input Parameters**</span></span>

- <span data-ttu-id="65269-171">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="65269-172">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-172">**Return Values**</span></span>

- <span data-ttu-id="65269-173">**NX_SUCCESS** (0x00) HTTP クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="65269-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="65269-174">NX_PTR_ERROR (0x16) HTTP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="65269-175">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-176">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-176">**Allowed From**</span></span>

<span data-ttu-id="65269-177">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-177">Threads</span></span>

<span data-ttu-id="65269-178">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="65269-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="65269-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="65269-180">HTTP GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="65269-180">Start an HTTP GET request</span></span>

<span data-ttu-id="65269-181">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="65269-182">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-182">**Description**</span></span>

<span data-ttu-id="65269-183">このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="65269-184">このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="65269-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="65269-185">リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。</span><span class="sxs-lookup"><span data-stu-id="65269-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="65269-186">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-186">This service is deprecated.</span></span> <span data-ttu-id="65269-187">開発者は *nx_http_client_get_start_extended()* に移行することが推奨されます</span><span class="sxs-lookup"><span data-stu-id="65269-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="65269-188">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-188">**Input Parameters**</span></span>

- <span data-ttu-id="65269-189">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-190">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="65269-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="65269-191">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="65269-192">**input_ptr** GET 要求の追加データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="65269-193">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="65269-193">This is optional.</span></span> <span data-ttu-id="65269-194">有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="65269-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="65269-195">**input_size** input_ptr が指す省略可能な追加入力のバイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="65269-196">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="65269-197">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="65269-198">
-\*\*wait_option*\* サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="65269-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="65269-199">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="65269-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="65269-200">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="65269-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="65269-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="65269-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="65269-202">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="65269-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="65269-203">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="65269-204">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-204">**Return Values**</span></span>

- <span data-ttu-id="65269-205">**NX_SUCCESS** (0x00) HTTP クライアントの GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="65269-206">**NX_HTTP_ERROR** (0xE0) 内部 HTTP クライアント エラー</span><span class="sxs-lookup"><span data-stu-id="65269-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="65269-207">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="65269-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="65269-208">**NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー。</span><span class="sxs-lookup"><span data-stu-id="65269-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="65269-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です。</span><span class="sxs-lookup"><span data-stu-id="65269-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="65269-210">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-211">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="65269-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="65269-212">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-212">**Allowed From**</span></span>

<span data-ttu-id="65269-213">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-213">Threads</span></span>

<span data-ttu-id="65269-214">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="65269-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="65269-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="65269-216">HTTP GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="65269-216">Start an HTTP GET request</span></span>

<span data-ttu-id="65269-217">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="65269-218">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-218">**Description**</span></span>

<span data-ttu-id="65269-219">このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="65269-220">このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="65269-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="65269-221">リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。</span><span class="sxs-lookup"><span data-stu-id="65269-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="65269-222">このサービスは *nx_http_client_get_start()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="65269-223">呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="65269-224">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-224">**Input Parameters**</span></span>

- <span data-ttu-id="65269-225">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-226">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="65269-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="65269-227">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="65269-228">**resource_length** 要求されたリソースの URL 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="65269-229">**input_ptr** GET 要求の追加データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="65269-230">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="65269-230">This is optional.</span></span> <span data-ttu-id="65269-231">有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="65269-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="65269-232">**input_size** input_ptr が指す省略可能な追加入力のバイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="65269-233">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="65269-234">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="65269-235">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="65269-236">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="65269-237">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="65269-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="65269-238">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="65269-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="65269-239">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="65269-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="65269-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="65269-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="65269-241">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="65269-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="65269-242">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="65269-243">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-243">**Return Values**</span></span>

- <span data-ttu-id="65269-244">**NX_SUCCESS** (0x00) HTTP クライアントの GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="65269-245">**NX_HTTP_ERROR** (0xE0) 内部 HTTP クライアント エラー</span><span class="sxs-lookup"><span data-stu-id="65269-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="65269-246">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="65269-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="65269-247">**NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー。</span><span class="sxs-lookup"><span data-stu-id="65269-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="65269-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です。</span><span class="sxs-lookup"><span data-stu-id="65269-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="65269-249">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-250">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="65269-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="65269-251">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-251">**Allowed From**</span></span>

<span data-ttu-id="65269-252">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-252">Threads</span></span>

<span data-ttu-id="65269-253">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="65269-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="65269-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="65269-255">次のリソース データ パケットを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-255">Get next resource data packet</span></span>

<span data-ttu-id="65269-256">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="65269-257">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-257">**Description**</span></span>

<span data-ttu-id="65269-258">このサービスは、前の *nx_http_client_get_start* 呼び出しによって要求されたリソースのコンテンツの次のパケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="65269-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="65269-259">NX_HTTP_GET_DONE という戻りステータスを受け取るまで、このルーチンを連続で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="65269-260">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-260">**Input Parameters**</span></span>

- <span data-ttu-id="65269-261">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-262">**packet_ptr** 部分的なリソース コンテンツを含むパケット ポインターのコピー先。</span><span class="sxs-lookup"><span data-stu-id="65269-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="65269-263">**wait_option** サービスが HTTP クライアントのパケット取得を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="65269-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="65269-264">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="65269-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="65269-265">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="65269-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="65269-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="65269-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="65269-267">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="65269-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="65269-268">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="65269-269">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-269">**Return Values**</span></span>

- <span data-ttu-id="65269-270">**NX_SUCCESS** (0x00) HTTP クライアントのパケット取得が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="65269-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="65269-271">**NX_HTTP_GET_DONE** (0xEC) HTTP クライアントのパケット取得が完了しました</span><span class="sxs-lookup"><span data-stu-id="65269-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="65269-272">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントが GET モードではありません。</span><span class="sxs-lookup"><span data-stu-id="65269-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="65269-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) パケット長が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="65269-274">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-275">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-276">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-276">**Allowed From**</span></span>

<span data-ttu-id="65269-277">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-277">Threads</span></span>

<span data-ttu-id="65269-278">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="65269-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="65269-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="65269-280">HTTP PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="65269-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="65269-281">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="65269-282">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-282">**Description**</span></span>

<span data-ttu-id="65269-283">このサービスは、指定された IP アドレスの HTTP サーバーへの、指定されたリソースに対する PUT 要求の送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="65269-284">このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="65269-285">リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。</span><span class="sxs-lookup"><span data-stu-id="65269-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="65269-286">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-286">This service is deprecated.</span></span> <span data-ttu-id="65269-287">開発者は *nx_http_client_put_start_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="65269-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="65269-288">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-288">**Input Parameters**</span></span>

- <span data-ttu-id="65269-289">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-290">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="65269-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="65269-291">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="65269-292">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="65269-293">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="65269-294">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="65269-295">後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="65269-296">**wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="65269-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="65269-297">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="65269-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="65269-298">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="65269-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="65269-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="65269-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="65269-300">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="65269-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="65269-301">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="65269-302">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-302">**Return Values**</span></span>

- <span data-ttu-id="65269-303">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="65269-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="65269-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="65269-305">**(0xF1) ユーザー名がバッファーに対して大きすぎます**</span><span class="sxs-lookup"><span data-stu-id="65269-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="65269-306">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="65269-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="65269-307">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-308">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="65269-309">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-310">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-310">**Allowed From**</span></span>

<span data-ttu-id="65269-311">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-311">Threads</span></span>

<span data-ttu-id="65269-312">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="65269-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="65269-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="65269-314">HTTP PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="65269-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="65269-315">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="65269-316">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-316">**Description**</span></span>

<span data-ttu-id="65269-317">このサービスは、指定された IP アドレスの HTTP サーバーへの、指定されたリソースに対する PUT 要求の送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="65269-318">このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="65269-319">リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。</span><span class="sxs-lookup"><span data-stu-id="65269-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="65269-320">このサービスは *nx_http_client_put_start()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="65269-321">呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="65269-322">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-322">**Input Parameters**</span></span>

- <span data-ttu-id="65269-323">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-324">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="65269-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="65269-325">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="65269-326">**resource_length** サーバーに送信するリソースの URL 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="65269-327">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="65269-328">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="65269-329">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="65269-330">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="65269-331">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="65269-332">後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="65269-333">**wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="65269-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="65269-334">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="65269-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="65269-335">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="65269-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="65269-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="65269-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="65269-337">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="65269-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="65269-338">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="65269-339">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-339">**Return Values**</span></span>

- <span data-ttu-id="65269-340">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="65269-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="65269-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="65269-342">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="65269-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="65269-343">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-344">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="65269-345">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-346">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-346">**Allowed From**</span></span>

<span data-ttu-id="65269-347">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-347">Threads</span></span>

<span data-ttu-id="65269-348">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="65269-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="65269-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="65269-350">次のリソース データ パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="65269-350">Send next resource data packet</span></span>

<span data-ttu-id="65269-351">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="65269-352">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-352">**Description**</span></span>

<span data-ttu-id="65269-353">このサービスは、HTTP サーバーへの、リソース コンテンツの次のパケットの送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="65269-354">送信されるパケットの合計長が前の *nx_http_client_put_start()* 呼び出しで指定された "total_bytes" と等しくなるまで、このルーチンを繰り返し呼び出す必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="65269-355">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-355">**Input Parameters**</span></span>

- <span data-ttu-id="65269-356">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-357">**packet_ptr** HTTP サーバーに送信されるリソースの次のコンテンツへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="65269-358">**wait_option** サービスが HTTP クライアントのパケットの PUT を内部的に処理するのを待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="65269-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="65269-359">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="65269-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="65269-360">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="65269-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="65269-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="65269-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="65269-362">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="65269-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="65269-363">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="65269-364">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-364">**Return Values**</span></span>

- <span data-ttu-id="65269-365">**NX_SUCCESS** (0x00) HTTP クライアントのパケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="65269-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="65269-366">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="65269-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="65269-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) サーバー エラー コードを受信しました \*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) パケット長が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="65269-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="65269-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) PUT が完了する前にサーバーが応答しました</span><span class="sxs-lookup"><span data-stu-id="65269-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="65269-370">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-371">NX_INVALID_PACKET (0x12) パケットが TCP ヘッダーに対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="65269-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="65269-372">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-373">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-373">**Allowed From**</span></span>

<span data-ttu-id="65269-374">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-374">Threads</span></span>

<span data-ttu-id="65269-375">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="65269-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="65269-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="65269-377">サーバーへの接続ポートを設定する</span><span class="sxs-lookup"><span data-stu-id="65269-377">Set the connection port to the Server</span></span>

<span data-ttu-id="65269-378">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="65269-379">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-379">**Description**</span></span>

<span data-ttu-id="65269-380">このサービスは、実行時に HTTP サーバーに接続する際の接続ポートを指定されたポートに変更します。</span><span class="sxs-lookup"><span data-stu-id="65269-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="65269-381">それ以外の場合、接続ポートは既定で 80 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="65269-382">これは、*nx_http_client_get_start()* および *nx_http_client_put_start()* (HTTP クライアントがサーバーに接続する場合など) の前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="65269-383">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-383">**Input Parameters**</span></span>

- <span data-ttu-id="65269-384">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="65269-385">**port** サーバーに接続するためのポート。</span><span class="sxs-lookup"><span data-stu-id="65269-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="65269-386">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-386">**Return Values**</span></span>

- <span data-ttu-id="65269-387">**NX_SUCCESS** (0x00) 接続ポートが正常に変更されました</span><span class="sxs-lookup"><span data-stu-id="65269-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="65269-388">**NX_INVALID_PORT** (0x46) ポートが最大値 (0xFFFF) を超えているか、0 です。</span><span class="sxs-lookup"><span data-stu-id="65269-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="65269-389">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-390">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-390">**Allowed From**</span></span>

<span data-ttu-id="65269-391">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="65269-391">Threads, Initialization</span></span>

<span data-ttu-id="65269-392">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="65269-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="65269-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="65269-394">URL の最大有効期間と日付を取得するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="65269-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="65269-395">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="65269-396">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-396">**Description**</span></span>

<span data-ttu-id="65269-397">このサービスは、指定されたリソースの最大有効期間と最終更新日を取得するために呼び出されるコールバック サービスを設定します。</span><span class="sxs-lookup"><span data-stu-id="65269-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="65269-398">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-398">**Input Parameters**</span></span>

- <span data-ttu-id="65269-399">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-400">**cache_info_get** コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="65269-401">**max_age** リソースの最大有効期間へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="65269-402">**data** 返された最終更新日へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="65269-403">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-403">**Return Values**</span></span>

- <span data-ttu-id="65269-404">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="65269-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="65269-405">**NX_PTR_ERROR** (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-406">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-406">**Allowed From**</span></span>

<span data-ttu-id="65269-407">初期化</span><span class="sxs-lookup"><span data-stu-id="65269-407">Initialization</span></span>

<span data-ttu-id="65269-408">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="65269-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="65269-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="65269-410">コールバック関数からデータを送信する</span><span class="sxs-lookup"><span data-stu-id="65269-410">Send data from callback function</span></span>

<span data-ttu-id="65269-411">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="65269-412">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-412">**Description**</span></span>

<span data-ttu-id="65269-413">このサービスは、アプリケーションのコールバック ルーチンから、指定されたパケット内のデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="65269-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="65269-414">これは通常、GET または POST 要求に関連付けられた動的データを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="65269-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="65269-415">この関数を使用する場合、コールバック ルーチンから応答全体を適切な形式で送信する必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="65269-416">また、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="65269-417">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-417">**Input Parameters**</span></span>

- <span data-ttu-id="65269-418">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-419">**data_ptr** 送信するデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="65269-420">**data_length** 送信するバイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="65269-421">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-421">**Return Values**</span></span>

- <span data-ttu-id="65269-422">**NX_SUCCESS** (0x00) サーバー データが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="65269-423">**NX_PTR_ERROR** (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-424">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-424">**Allowed From**</span></span>

<span data-ttu-id="65269-425">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-425">Threads</span></span>

<span data-ttu-id="65269-426">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="65269-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="65269-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="65269-428">コールバック関数内で応答ヘッダーを作成する</span><span class="sxs-lookup"><span data-stu-id="65269-428">Create a response header in a callback function</span></span>

<span data-ttu-id="65269-429">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="65269-430">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-430">**Description**</span></span>

<span data-ttu-id="65269-431">このサービスは、HTTP サーバーがクライアントの GET、PUT、DELETE 要求に応答するときに、内部関数 *_nx_http_server_generate_response_header* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="65269-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="65269-432">これは、HTTP サーバー アプリケーションがクライアントへのその応答を設計しているときに、HTTP サーバーのコールバック関数内で使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="65269-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="65269-433">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-433">This service is deprecated.</span></span> <span data-ttu-id="65269-434">開発者は *nxd_http_server_callback_generate_response_header_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="65269-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="65269-435">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-435">**Input Parameters**</span></span>

- <span data-ttu-id="65269-436">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-437">**packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="65269-438">**status_code** リソースの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="65269-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="65269-439">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="65269-439">Examples:</span></span>
- <span data-ttu-id="65269-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="65269-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="65269-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="65269-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="65269-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="65269-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="65269-443">**content_length** コンテンツのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="65269-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="65269-444">**content_type** HTTP の種類 (例: "text/plain")</span><span class="sxs-lookup"><span data-stu-id="65269-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="65269-445">**additional_header** 追加のヘッダー テキストへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="65269-446">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-446">**Return Values**</span></span>

- <span data-ttu-id="65269-447">**NX_SUCCESS** (0x00) HTML ヘッダーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="65269-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="65269-448">**NX_PTR_ERROR** (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-449">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-449">**Allowed From**</span></span>

<span data-ttu-id="65269-450">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-450">Threads</span></span>

<span data-ttu-id="65269-451">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
            nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

/* Now send the packet! */
   status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
            resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
/* Let HTTP server know the response has been sent. */
   return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="65269-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="65269-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="65269-453">コールバック関数内で応答ヘッダーを作成する</span><span class="sxs-lookup"><span data-stu-id="65269-453">Create a response header in a callback function</span></span>

<span data-ttu-id="65269-454">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-454">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header_extended(
     NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr,
     CHAR *status_code, UINT status_code_length,
     UINT content_length,
     CHAR *content_type, UINT content_type_length,
     CHAR *additional_header,
     UINT additional_header_length);
```

<span data-ttu-id="65269-455">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-455">**Description**</span></span>

<span data-ttu-id="65269-456">このサービスは、HTTP サーバーがクライアントの GET、PUT、DELETE 要求に応答するときに、内部関数 *_nx_http_server_generate_response_header()* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="65269-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="65269-457">これは、HTTP サーバー アプリケーションがクライアントへのその応答を設計しているときに、HTTP サーバーのコールバック関数内で使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="65269-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="65269-458">このサービスは *nx_http_server_callback_generate_response_header()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="65269-459">このバージョンでは、コールバック関数に追加の長さの情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="65269-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="65269-460">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-460">**Input Parameters**</span></span>

- <span data-ttu-id="65269-461">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-462">**packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="65269-463">**status_code** リソースの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="65269-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="65269-464">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="65269-464">Examples:</span></span>
  - <span data-ttu-id="65269-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="65269-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="65269-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="65269-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="65269-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="65269-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="65269-468">**status_code** 状態コードの長さ</span><span class="sxs-lookup"><span data-stu-id="65269-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="65269-469">**content_length** コンテンツのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="65269-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="65269-470">**content_type** HTTP の種類 (例: "text/plain")</span><span class="sxs-lookup"><span data-stu-id="65269-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="65269-471">**content_type_length** HTTP の種類の長さ</span><span class="sxs-lookup"><span data-stu-id="65269-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="65269-472">**additional_header** 追加のヘッダー テキストへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="65269-473">**additional_header_length** 追加のヘッダー テキストの長さ</span><span class="sxs-lookup"><span data-stu-id="65269-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="65269-474">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-474">**Return Values**</span></span>

- <span data-ttu-id="65269-475">**NX_SUCCESS** (0x00) ヘッダーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="65269-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="65269-476">**NX_PTR_ERROR** (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-477">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-477">**Allowed From**</span></span>

<span data-ttu-id="65269-478">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-478">Threads</span></span>

<span data-ttu-id="65269-479">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
                       nx_http_server_request_resource, temp_string,
                       sizeof(temp_string));

    /* Null terminate the string. */
       temp_string[temp] = 0;

    /* Now build a response header with server status is OK and no additional header
      info. */
      status = nx_http_server_callback_generate_response_header_extended(
               http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
               sizeof(NX_HTTP_STATUS_OK) - 1, length,
               temp_string, string_length, NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
       status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                length, server_ptr ->
                nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
       status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                   resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
    /* Let HTTP server know the response has been sent. */
       return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="65269-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="65269-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="65269-481">コールバック関数から HTTP パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="65269-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="65269-482">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="65269-483">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-483">**Description**</span></span>

<span data-ttu-id="65269-484">このサービスは、HTTP コールバックから完全な HTTP サーバー応答を送信します。</span><span class="sxs-lookup"><span data-stu-id="65269-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="65269-485">HTTP サーバーは、NX_HTTP_SERVER _TIMEOUT_SEND を使用してパケットを送信します。</span><span class="sxs-lookup"><span data-stu-id="65269-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="65269-486">HTTP ヘッダーとデータをパケットに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="65269-487">戻りステータスがエラーを示している場合、HTTP アプリケーションはパケットを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="65269-488">このコールバックは NX_HTTP_CALLBACK_COMPLETED を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="65269-489">詳細な例については、*nx_http_server_callback_generate_response_header()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65269-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="65269-490">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-490">**Input Parameters**</span></span>

- <span data-ttu-id="65269-491">**server_ptr** HTTP サーバーの制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="65269-492">**packet_ptr** 送信するパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="65269-493">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-493">**Return Values**</span></span>

- <span data-ttu-id="65269-494">**NX_SUCCESS** (0x00) HTTP サーバー パケットが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="65269-495">**NX_PTR_ERROR** (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-496">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-496">**Allowed From**</span></span>

<span data-ttu-id="65269-497">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-497">Threads</span></span>

<span data-ttu-id="65269-498">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="65269-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="65269-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="65269-500">コールバック関数から応答を送信する</span><span class="sxs-lookup"><span data-stu-id="65269-500">Send response from callback function</span></span>

<span data-ttu-id="65269-501">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="65269-502">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-502">**Description**</span></span>

<span data-ttu-id="65269-503">このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="65269-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="65269-504">これは通常、GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="65269-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="65269-505">この関数を使用する場合、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="65269-506">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-506">This service is deprecated.</span></span> <span data-ttu-id="65269-507">開発者は *nx_http_server_callback_response_send_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="65269-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="65269-508">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-508">**Input Parameters**</span></span>

- <span data-ttu-id="65269-509">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-510">**header** 応答ヘッダー文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="65269-511">**information** 情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="65269-512">**additional_info** 追加の情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="65269-513">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-513">**Return Values**</span></span>

- <span data-ttu-id="65269-514">**NX_SUCCESS** (0x00) HTTP サーバー応答が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="65269-515">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-515">**Allowed From**</span></span>

<span data-ttu-id="65269-516">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-516">Threads</span></span>

<span data-ttu-id="65269-517">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
       {

            /* In this example, we will complete the GET processing with
               a resource not found response. */
               nx_http_server_callback_response_send(server_ptr,
                                                    "HTTP/1.0 404 ",
                                                    "NetX HTTP Server unable to find
                                                    file: ", resource);
            /* Return completion status. */
               return(NX_HTTP_CALLBACK_COMPLETED);
        }
        return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="65269-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="65269-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="65269-519">コールバック関数から応答を送信する</span><span class="sxs-lookup"><span data-stu-id="65269-519">Send response from callback function</span></span>

<span data-ttu-id="65269-520">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="65269-521">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-521">**Description**</span></span>

<span data-ttu-id="65269-522">このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="65269-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="65269-523">これは通常、GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="65269-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="65269-524">この関数を使用する場合、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="65269-525">このサービスは *nx_http_server_callback_response_send()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="65269-526">このバージョンでは、入力引数として長さの情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="65269-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="65269-527">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-527">**Input Parameters**</span></span>

- <span data-ttu-id="65269-528">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-529">**header** 応答ヘッダー文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="65269-530">**header_length** 応答ヘッダー文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="65269-531">**information** 情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="65269-532">**information_length** 情報文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="65269-533">**additional_info** 追加の情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="65269-534">**additional_info_length** 追加の情報文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="65269-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="65269-535">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-535">**Return Values**</span></span>

- <span data-ttu-id="65269-536">**NX_SUCCESS** (0x00) サーバー応答が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="65269-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="65269-537">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-537">**Allowed From**</span></span>

<span data-ttu-id="65269-538">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-538">Threads</span></span>

<span data-ttu-id="65269-539">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="65269-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="65269-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="65269-541">要求からコンテンツを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-541">Get content from the request</span></span>

<span data-ttu-id="65269-542">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="65269-543">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-543">**Description**</span></span>

<span data-ttu-id="65269-544">このサービスは、POST または PUT HTTP クライアント要求から指定された量のコンテンツの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="65269-545">これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="65269-546">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-546">This service is deprecated.</span></span> <span data-ttu-id="65269-547">開発者は nx_http_server_content_get_extended() に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="65269-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="65269-548">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-548">**Input Parameters**</span></span>

- <span data-ttu-id="65269-549">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-550">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="65269-551">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="65269-552">**byte_offset** コンテンツ領域にオフセットするバイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="65269-553">**destination_ptr** コンテンツのコピー先領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="65269-554">**destination_size** コピー先領域の使用可能な最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="65269-555">**actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="65269-556">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-556">**Return Values**</span></span>

- <span data-ttu-id="65269-557">**NX_SUCCESS** (0x00) HTTP サーバーのコンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="65269-558">**NX_HTTP_ERROR** (0xE0) HTTP サーバーの内部エラー</span><span class="sxs-lookup"><span data-stu-id="65269-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="65269-559">**NX_HTTP_DATA_END** (0xE7) 要求コンテンツの終わり</span><span class="sxs-lookup"><span data-stu-id="65269-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="65269-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP サーバーがコンテンツの次のパケットを取得中にタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="65269-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="65269-561">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-562">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-563">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-563">**Allowed From**</span></span>

<span data-ttu-id="65269-564">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-564">Threads</span></span>

<span data-ttu-id="65269-565">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="65269-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="65269-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="65269-567">要求からコンテンツを取得する (長さゼロのコンテンツの長さがサポートされます)</span><span class="sxs-lookup"><span data-stu-id="65269-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="65269-568">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="65269-569">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-569">**Description**</span></span>

<span data-ttu-id="65269-570">このサービスは *nx_http_server_content_get()* とほぼ同じで、POST または PUT HTTP クライアント要求から指定された量のコンテンツの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="65269-571">ただし、コンテンツの長さがゼロ値の要求 ("空の要求") が有効な要求として処理されます。</span><span class="sxs-lookup"><span data-stu-id="65269-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="65269-572">これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="65269-573">このサービスは *nx_http_server_content_get()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="65269-574">このバージョンでは、呼び出し元が追加の長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="65269-575">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-575">**Input Parameters**</span></span>

- <span data-ttu-id="65269-576">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-577">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="65269-578">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="65269-579">**byte_offset** コンテンツ領域にオフセットするバイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="65269-580">**destination_ptr** コンテンツのコピー先領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="65269-581">**destination_size** コピー先領域の使用可能な最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="65269-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="65269-582">**actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="65269-583">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-583">**Return Values**</span></span>

- <span data-ttu-id="65269-584">**NX_SUCCESS** (0x00) HTTP コンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="65269-585">**NX_HTTP_ERROR** (0xE0) HTTP サーバーの内部エラー</span><span class="sxs-lookup"><span data-stu-id="65269-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="65269-586">**NX_HTTP_DATA_END** (0xE7) 要求コンテンツの終わり</span><span class="sxs-lookup"><span data-stu-id="65269-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="65269-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP サーバーが次のパケットを取得中にタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="65269-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="65269-588">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-589">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-590">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-590">**Allowed From**</span></span>

<span data-ttu-id="65269-591">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-591">Threads</span></span>

<span data-ttu-id="65269-592">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="65269-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="65269-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="65269-594">要求のコンテンツの長さを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-594">Get length of content in the request</span></span>

<span data-ttu-id="65269-595">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="65269-596">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-596">**Description**</span></span>

<span data-ttu-id="65269-597">このサービスは、指定されたパケットの HTTP コンテンツの長さの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="65269-598">HTTP コンテンツがない場合、このルーチンは値 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="65269-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="65269-599">これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="65269-600">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-600">This service is deprecated.</span></span> <span data-ttu-id="65269-601">開発者は nx_http_server_content_length_get_extended() に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="65269-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="65269-602">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-602">**Input Parameters**</span></span>

- <span data-ttu-id="65269-603">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="65269-604">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="65269-605">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-605">**Return Values**</span></span>

- <span data-ttu-id="65269-606">**content length** エラーが発生した場合、値 0 が返されます</span><span class="sxs-lookup"><span data-stu-id="65269-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="65269-607">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-607">**Allowed From**</span></span>

<span data-ttu-id="65269-608">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-608">Threads</span></span>

<span data-ttu-id="65269-609">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="65269-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="65269-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="65269-611">要求のコンテンツの長さを取得する (ゼロ値のコンテンツの長さがサポートされます)</span><span class="sxs-lookup"><span data-stu-id="65269-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="65269-612">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="65269-613">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-613">**Description**</span></span>

<span data-ttu-id="65269-614">このサービスは、*nx_http_server_content_length_get()* に似ており、指定されたパケットの HTTP コンテンツの長さの取得を試行します。</span><span class="sxs-lookup"><span data-stu-id="65269-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="65269-615">ただし、戻り値は正常完了状態を示し、実際の長さの値が入力ポインター content_length で返されます。</span><span class="sxs-lookup"><span data-stu-id="65269-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="65269-616">HTTP コンテンツがない、またはコンテンツの長さが 0 の場合でも、このルーチンは正常完了状態を返し、content_length 入力ポインターは有効な長さ (ゼロ) を指します。</span><span class="sxs-lookup"><span data-stu-id="65269-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="65269-617">これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="65269-618">このサービスは *nx_http_server_content_length_get()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="65269-619">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-619">**Input Parameters**</span></span>

- <span data-ttu-id="65269-620">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="65269-621">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="65269-622">**content_length** Content Length フィールドから取得した値へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="65269-623">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-623">**Return Values**</span></span>

- <span data-ttu-id="65269-624">**NX_SUCCESS** (0x00) HTTP サーバーのコンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="65269-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) HTTP ヘッダーの形式が正しくありません</span><span class="sxs-lookup"><span data-stu-id="65269-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="65269-626">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-627">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-627">**Allowed From**</span></span>

<span data-ttu-id="65269-628">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-628">Threads</span></span>

<span data-ttu-id="65269-629">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="65269-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="65269-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="65269-631">HTTP サーバー インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="65269-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="65269-632">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-632">**Prototype**</span></span>

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
     CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
     VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
     UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, CHAR **name,
     CHAR **password, CHAR **realm),
     UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

<span data-ttu-id="65269-633">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-633">**Description**</span></span>

<span data-ttu-id="65269-634">このサービスは、専用の ThreadX スレッドのコンテキスト内で実行される HTTP サーバー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="65269-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="65269-635">オプションの *authentication_check* および *request_notify* アプリケーション コールバック ルーチンを使うと、アプリケーション ソフトウェアから HTTP サーバーの基本的な操作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="65269-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="65269-636">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-636">**Input Parameters**</span></span>

- <span data-ttu-id="65269-637">**http_server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="65269-638">**http_server_name** HTTP サーバーの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="65269-639">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="65269-640">**media_ptr** 以前に作成された FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="65269-641">**stack_ptr** HTTP サーバーのスレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="65269-642">**stack_size** HTTP サーバーのスレッド スタック サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="65269-643">**authentication_check** アプリケーションの認証確認ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="65269-644">指定した場合、このルーチンは HTTP クライアント要求ごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="65269-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="65269-645">このパラメーターが null 値の場合、認証は実行されません。</span><span class="sxs-lookup"><span data-stu-id="65269-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="65269-646">**request_notify** アプリケーションの要求通知ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="65269-647">指定した場合、このルーチンは要求の HTTP サーバー処理の前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="65269-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="65269-648">これにより、HTTP クライアント要求が完了する前に、リソース名をリダイレクトしたり、リソース内のフィールドを更新したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="65269-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="65269-649">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-649">**Return Values**</span></span>

- <span data-ttu-id="65269-650">**NX_SUCCESS** (0x00) HTTP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="65269-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="65269-651">NX_PTR_ERROR (0x07) HTTP サーバー、IP、メディア、スタック、またはパケット プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="65269-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="65269-652">NX_HTTP_POOL_ERROR (0xE9) プールのパケット ペイロードが HTTP 要求全体を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="65269-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="65269-653">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-653">**Allowed From**</span></span>

<span data-ttu-id="65269-654">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="65269-654">Initialization, Threads</span></span>

<span data-ttu-id="65269-655">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="65269-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="65269-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="65269-657">HTTP サーバー インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="65269-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="65269-658">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="65269-659">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-659">**Description**</span></span>

<span data-ttu-id="65269-660">このサービスは、以前に作成された HTTP サーバー インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="65269-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="65269-661">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-661">**Input Parameters**</span></span>

- <span data-ttu-id="65269-662">**http_server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="65269-663">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-663">**Return Values**</span></span>

- <span data-ttu-id="65269-664">**NX_SUCCESS** (0x00) HTTP サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="65269-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="65269-665">NX_PTR_ERROR (0x07) HTTP サーバー ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="65269-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="65269-666">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-667">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-667">**Allowed From**</span></span>

<span data-ttu-id="65269-668">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-668">Threads</span></span>

<span data-ttu-id="65269-669">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="65269-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="65269-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="65269-671">エンティティ データの場所と長さを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="65269-672">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="65269-673">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-673">**Description**</span></span>

<span data-ttu-id="65269-674">このサービスは、受信したクライアント メッセージの現在のマルチパート エンティティ内にあるデータの開始位置と、境界文字列を除いたデータの長さを特定します。</span><span class="sxs-lookup"><span data-stu-id="65269-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="65269-675">複数のエンティティを含むメッセージの同じクライアント データグラムに対してこの関数を再度呼び出すことができるように、HTTP サーバー自体のオフセットが内部的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="65269-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="65269-676">パケット ポインターは、クライアント メッセージがマルチパケット データグラムである次のパケットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="65269-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="65269-677">このサービスを使用するには NX_HTTP_MULTIPART_ENABLE を有効にする必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="65269-678">詳細については、*nx_http_server_get_entity_header* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65269-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="65269-679">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-679">**Input Parameters**</span></span>

- <span data-ttu-id="65269-680">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="65269-681">**packet_pptr** パケット ポインターの位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="65269-682">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="65269-683">**available_offset** パケットの先頭追加ポインターからのエンティティ データのオフセットへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="65269-684">**available_length** エンティティ データの長さへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="65269-685">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-685">**Return Values**</span></span>

- <span data-ttu-id="65269-686">**NX_SUCCESS** (0x00) エンティティ コンテンツのサイズと場所が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="65269-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) HTTP サーバーの内部マルチパート マーカーのコンテンツが既に存在します</span><span class="sxs-lookup"><span data-stu-id="65269-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="65269-688">NX_HTTP_ERROR (0xE0) HTTP サーバーの内部エラー</span><span class="sxs-lookup"><span data-stu-id="65269-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="65269-689">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-690">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-690">**Allowed From**</span></span>

<span data-ttu-id="65269-691">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-691">Threads</span></span>

<span data-ttu-id="65269-692">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="65269-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="65269-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="65269-694">エンティティ ヘッダーのコンテンツを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="65269-695">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="65269-696">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-696">**Description**</span></span>

<span data-ttu-id="65269-697">このサービスは、エンティティ ヘッダーを取得して、指定されたバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="65269-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="65269-698">複数のエンティティ ヘッダーを含むクライアント データグラム内の次のマルチパート エンティティを見つけるために、HTTP サーバー自体のポインターが内部的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="65269-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="65269-699">パケット ポインターは、クライアント メッセージがマルチパケット データグラムである次のパケットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="65269-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="65269-700">このサービスを使用するには NX_HTTP_MULTIPART_ENABLE を有効にする必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="65269-701">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-701">**Input Parameters**</span></span>

- <span data-ttu-id="65269-702">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="65269-703">**packet_pptr** パケット ポインターの位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="65269-704">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="65269-705">**entity_header_buffer** エンティティ ヘッダーを格納する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="65269-706">**buffer_size** 入力バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="65269-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="65269-707">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-707">**Return Values**</span></span>

- <span data-ttu-id="65269-708">**NX_SUCCESS** (0x00) エンティティ ヘッダーが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="65269-709">**NX_HTTP_NOT_FOUND** (0xE6) エンティティ ヘッダー フィールドが見つかりません</span><span class="sxs-lookup"><span data-stu-id="65269-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="65269-710">**NX_HTTP_TIMEOUT** (0xE1) マルチパケット クライアント メッセージの次のパケットの受信期限が切れました</span><span class="sxs-lookup"><span data-stu-id="65269-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="65269-711">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-712">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="65269-713">NX_HTTP_ERROR (0xE0) 内部 HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="65269-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="65269-714">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-714">**Allowed From**</span></span>

<span data-ttu-id="65269-715">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-715">Threads</span></span>

<span data-ttu-id="65269-716">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

/* Process multipart data. */
if(request_type == NX_HTTP_SERVER_POST_REQUEST)
{

    /* Get the content header. */
    while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                          sizeof(buffer)) == NX_SUCCESS)
    {

        /* Header obtained successfully. Get the content data location. */
        while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                               &length) == NX_SUCCESS)
        {

            /* Write content data to buffer. */
            nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
            buffer[length] = 0;
        }
    }
    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
             &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="65269-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="65269-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="65269-718">GMT の日付と時刻を取得するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="65269-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="65269-719">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="65269-720">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-720">**Description**</span></span>

<span data-ttu-id="65269-721">このサービスは、以前に作成された HTTP サーバーを使用して GMT の日付と時刻を取得するコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="65269-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="65269-722">このサービスは、HTTP サーバーがクライアントに対する HTTP サーバー応答のヘッダーを作成しているときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="65269-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="65269-723">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-723">**Input Parameters**</span></span>

- <span data-ttu-id="65269-724">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="65269-725">**gmt_get** GMT コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="65269-726">**date** 取得した日付へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="65269-727">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-727">**Return Values**</span></span>

- <span data-ttu-id="65269-728">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="65269-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="65269-729">NX_PTR_ERROR (0x07) パケットまたはパラメーター ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="65269-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="65269-730">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-730">**Allowed From**</span></span>

<span data-ttu-id="65269-731">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-731">Threads</span></span>

<span data-ttu-id="65269-732">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="65269-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="65269-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="65269-734">無効なユーザーとパスワードを処理するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="65269-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="65269-735">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="65269-736">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-736">**Description**</span></span>

<span data-ttu-id="65269-737">このサービスは、ダイジェストまたは基本認証のいずれかによって、クライアントの GET、PUT、または DELETE 要求で無効なユーザー名とパスワードを受信したときに呼び出されるコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="65269-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="65269-738">HTTP サーバーを先に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="65269-739">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-739">**Input Parameters**</span></span>

- <span data-ttu-id="65269-740">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="65269-741">**invalid_username_password_callback** 無効なユーザーまたはパス コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="65269-742">**resource** クライアントによって指定されたリソースへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="65269-743">**client_address** クライアント アドレス</span><span class="sxs-lookup"><span data-stu-id="65269-743">**client_address** Client address</span></span>
- <span data-ttu-id="65269-744">**request_type** クライアント要求の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="65269-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="65269-745">次を指定できます。</span><span class="sxs-lookup"><span data-stu-id="65269-745">May be:</span></span>
  - <span data-ttu-id="65269-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="65269-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="65269-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="65269-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="65269-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="65269-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="65269-749">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-749">**Return Values**</span></span>

- <span data-ttu-id="65269-750">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="65269-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="65269-751">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-752">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-752">**Allowed From**</span></span>

<span data-ttu-id="65269-753">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-753">Threads</span></span>

<span data-ttu-id="65269-754">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="65269-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="65269-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="65269-756">HTML 用の追加の MIME マップを設定する</span><span class="sxs-lookup"><span data-stu-id="65269-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="65269-757">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="65269-758">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-758">**Description**</span></span>

<span data-ttu-id="65269-759">このサービスを使用すると、HTTP アプリケーション開発者は、NetX HTTP サーバーによって提供される既定の MIME の種類から MIME の種類をさらに追加できます (定義済みの種類の一覧については、*nx_http_server_get_type* を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="65269-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="65269-760">GET 要求などのクライアント要求を受信すると、HTTP サーバーは、追加の MIME マップ セットを優先的に使用して HTTP ヘッダーから要求されたファイルの種類を解析します。一致するものが見つからない場合は、HTTP サーバーの既定の MIME マップの中で一致するものを検索します。</span><span class="sxs-lookup"><span data-stu-id="65269-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="65269-761">一致するものが見つからない場合、MIME の種類は既定で "text/plain" になります。</span><span class="sxs-lookup"><span data-stu-id="65269-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="65269-762">要求通知関数が HTTP サーバーに登録されている場合、要求通知コールバックから *nx_http_server_type_get* を呼び出して、ファイルの種類を解析できます。</span><span class="sxs-lookup"><span data-stu-id="65269-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="65269-763">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-763">**Input Parameters**</span></span>

- <span data-ttu-id="65269-764">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="65269-765">**mime_maps** MIME マップ配列へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="65269-766">**mime_map_num** 配列内の MIME マップの数</span><span class="sxs-lookup"><span data-stu-id="65269-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="65269-767">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-767">**Return Values**</span></span>

- <span data-ttu-id="65269-768">**NX_SUCCESS** (0x00) HTTP サーバーの MIME マップが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="65269-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="65269-769">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-770">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-770">**Allowed From**</span></span>

<span data-ttu-id="65269-771">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="65269-771">Initialization, Threads</span></span>

<span data-ttu-id="65269-772">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="65269-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="65269-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="65269-774">コンテンツの長さを抽出し、データの先頭にポインターを設定する</span><span class="sxs-lookup"><span data-stu-id="65269-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="65269-775">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="65269-776">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-776">**Description**</span></span>

<span data-ttu-id="65269-777">このサービスは、HTTP ヘッダーからコンテンツの長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="65269-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="65269-778">また、指定されたパケットを次のように更新します。パケットの先頭追加ポインター (書き込み先のパケット バッファーの開始位置) が、HTTP ヘッダーのすぐ先にある HTTP コンテンツ (データ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="65269-779">コンテンツの先頭が現在のパケット内に見つからない場合、この関数では、NX_HTTP_SERVER_TIMEOUT_RECEIVE 待機オプションを使用して、次のパケットを受信するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="65269-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="65269-780">これは、先頭追加ポインターをエンティティ ヘッダーの先に変更するため、*nx_http_server_get_entity_header()* を呼び出す前に呼び出さないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="65269-781">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-781">**Input Parameters**</span></span>

- <span data-ttu-id="65269-782">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="65269-783">**packet_ptr** 先頭追加ポインターが更新されたパケットを返すためのパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="65269-784">**content_length** 抽出された content_length へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="65269-785">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-785">**Return Values**</span></span>

- <span data-ttu-id="65269-786">**NX_SUCCESS** (0x00) HTTP コンテンツの長さが見つかり、パケットが正常に更新されました</span><span class="sxs-lookup"><span data-stu-id="65269-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="65269-787">**NX_HTTP_TIMEOUT** (0xE1) 次のパケットを待っている間に時間切れになりました</span><span class="sxs-lookup"><span data-stu-id="65269-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="65269-788">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-789">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-789">**Allowed From**</span></span>

<span data-ttu-id="65269-790">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-790">Threads</span></span>

<span data-ttu-id="65269-791">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="65269-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="65269-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="65269-793">次の HTTP パケットを受信する</span><span class="sxs-lookup"><span data-stu-id="65269-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="65269-794">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="65269-795">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-795">**Description**</span></span>

<span data-ttu-id="65269-796">このサービスは、HTTP サーバー ソケットで受信した次のパケットを返します。</span><span class="sxs-lookup"><span data-stu-id="65269-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="65269-797">パケットを受信する際の待機オプションは NX_HTTP_SERVER_TIMEOUT_RECEIVE です。</span><span class="sxs-lookup"><span data-stu-id="65269-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="65269-798">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-798">**Input Parameters**</span></span>

- <span data-ttu-id="65269-799">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="65269-800">**packet_ptr** 受信したパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="65269-801">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-801">**Return Values**</span></span>

- <span data-ttu-id="65269-802">**NX_SUCCESS** (0x00) 次の HTTP パケットを正常に受信しました</span><span class="sxs-lookup"><span data-stu-id="65269-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="65269-803">**NX_HTTP_TIMEOUT** (0xE1) 次のパケットを待っている間に時間切れになりました</span><span class="sxs-lookup"><span data-stu-id="65269-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="65269-804">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-805">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-805">**Allowed From**</span></span>

<span data-ttu-id="65269-806">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-806">Threads</span></span>

<span data-ttu-id="65269-807">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="65269-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="65269-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="65269-809">要求からパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-809">Get parameter from the request</span></span>

<span data-ttu-id="65269-810">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="65269-811">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-811">**Description**</span></span>

<span data-ttu-id="65269-812">このサービスは、指定された要求パケット内の指定された HTTP URL パラメーターの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="65269-813">要求された HTTP パラメーターが存在しない場合、このルーチンでは NX_HTTP_NOT_FOUND という状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="65269-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="65269-814">このルーチンは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="65269-815">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-815">**Input Parameters**</span></span>

- <span data-ttu-id="65269-816">**packet_ptr** HTTP クライアントの要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="65269-817">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="65269-818">**param_number** パラメーター リストの左から右に向かって 0 から始まるパラメーターの論理番号。</span><span class="sxs-lookup"><span data-stu-id="65269-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="65269-819">**param_ptr** パラメーターのコピー先領域。</span><span class="sxs-lookup"><span data-stu-id="65269-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="65269-820">**max_param_size** パラメーターのコピー先領域の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="65269-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="65269-821">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-821">**Return Values**</span></span>

- <span data-ttu-id="65269-822">**NX_SUCCESS** (0x00) HTTP サーバーのパラメーターが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="65269-823">**NX_HTTP_NOT_FOUND** (0xE6) 指定されたパラメーターが見つかりません</span><span class="sxs-lookup"><span data-stu-id="65269-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="65269-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) 要求パラメーターが正しく終了していません</span><span class="sxs-lookup"><span data-stu-id="65269-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="65269-825">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-826">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-827">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-827">**Allowed From**</span></span>

<span data-ttu-id="65269-828">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-828">Threads</span></span>

<span data-ttu-id="65269-829">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="65269-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="65269-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="65269-831">要求からクエリを取得する</span><span class="sxs-lookup"><span data-stu-id="65269-831">Get query from the request</span></span>

<span data-ttu-id="65269-832">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="65269-833">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-833">**Description**</span></span>

<span data-ttu-id="65269-834">このサービスは、指定された要求パケット内の指定された HTTP URL クエリの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="65269-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="65269-835">要求された HTTP クエリが存在しない場合、このルーチンでは NX_HTTP_NOT_FOUND という状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="65269-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="65269-836">このルーチンは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="65269-837">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-837">**Input Parameters**</span></span>

- <span data-ttu-id="65269-838">**packet_ptr** HTTP クライアントの要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="65269-839">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="65269-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="65269-840">**query_number** クエリ リストの左から右に向かって 0 から始まるクエリの論理番号。</span><span class="sxs-lookup"><span data-stu-id="65269-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="65269-841">**query_ptr** クエリのコピー先領域。</span><span class="sxs-lookup"><span data-stu-id="65269-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="65269-842">**max_query_size** クエリのコピー先領域の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="65269-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="65269-843">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-843">**Return Values**</span></span>

- <span data-ttu-id="65269-844">**NX_SUCCESS** (0x00) HTTP サーバーのクエリが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="65269-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="65269-845">**NX_HTTP_FAILED** (0xE2) クエリのサイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="65269-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="65269-846">**NX_HTTP_NOT_FOUND** (0xE6) 指定されたクエリが見つかりません</span><span class="sxs-lookup"><span data-stu-id="65269-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="65269-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) クライアント要求内にクエリがありません</span><span class="sxs-lookup"><span data-stu-id="65269-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="65269-848">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-849">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-850">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-850">**Allowed From**</span></span>

<span data-ttu-id="65269-851">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-851">Threads</span></span>

<span data-ttu-id="65269-852">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="65269-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="65269-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="65269-854">HTTP サーバーを起動する</span><span class="sxs-lookup"><span data-stu-id="65269-854">Start the HTTP Server</span></span>

<span data-ttu-id="65269-855">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="65269-856">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-856">**Description**</span></span>

<span data-ttu-id="65269-857">このサービスは、以前に作成された HTTP サーバー インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="65269-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="65269-858">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-858">**Input Parameters**</span></span>

- <span data-ttu-id="65269-859">**http_server_ptr** HTTP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="65269-860">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-860">**Return Values**</span></span>

- <span data-ttu-id="65269-861">**NX_SUCCESS** (0x00) HTTP サーバーが正常に起動しました</span><span class="sxs-lookup"><span data-stu-id="65269-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="65269-862">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-863">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-863">**Allowed From**</span></span>

<span data-ttu-id="65269-864">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="65269-864">Initialization, Threads</span></span>

<span data-ttu-id="65269-865">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="65269-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="65269-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="65269-867">HTTP サーバーを停止する</span><span class="sxs-lookup"><span data-stu-id="65269-867">Stop the HTTP Server</span></span>

<span data-ttu-id="65269-868">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="65269-869">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-869">**Description**</span></span>

<span data-ttu-id="65269-870">このサービスは、以前に作成された HTTP サーバー インスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="65269-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="65269-871">このルーチンは、HTTP サーバー インスタンスを削除する前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65269-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="65269-872">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-872">**Input Parameters**</span></span>

- <span data-ttu-id="65269-873">**http_server_ptr** HTTP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="65269-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="65269-874">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-874">**Return Values**</span></span>

- <span data-ttu-id="65269-875">**NX_SUCCESS** (0x00) HTTP サーバーが正常に停止しました</span><span class="sxs-lookup"><span data-stu-id="65269-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="65269-876">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-877">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="65269-878">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-878">**Allowed From**</span></span>

<span data-ttu-id="65269-879">Threads</span><span class="sxs-lookup"><span data-stu-id="65269-879">Threads</span></span>

<span data-ttu-id="65269-880">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="65269-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="65269-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="65269-882">クライアントの HTTP 要求からファイルの種類を抽出する</span><span class="sxs-lookup"><span data-stu-id="65269-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="65269-883">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="65269-884">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-884">**Description**</span></span>

<span data-ttu-id="65269-885">このサービスは、*http_type_string* バッファー内の HTTP 要求の種類と、入力バッファー *name* からの戻り値 (通常は URL) 内のその長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="65269-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="65269-886">MIME マップが見つからない場合、既定で "text/plain" という種類に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="65269-887">それ以外の場合、抽出された種類を HTTP サーバーの既定の MIME マップと比較して、一致するものを探します。</span><span class="sxs-lookup"><span data-stu-id="65269-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="65269-888">NetX HTTP サーバーの既定の MIME マップは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65269-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="65269-889">html text/html</span><span class="sxs-lookup"><span data-stu-id="65269-889">html text/html</span></span>
- <span data-ttu-id="65269-890">htm text/html</span><span class="sxs-lookup"><span data-stu-id="65269-890">htm text/html</span></span>
- <span data-ttu-id="65269-891">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="65269-891">txt text/plain</span></span>
- <span data-ttu-id="65269-892">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="65269-892">gif image/gif</span></span>
- <span data-ttu-id="65269-893">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="65269-893">jpg image/jpeg</span></span>
- <span data-ttu-id="65269-894">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="65269-894">ico image/x-icon</span></span>

<span data-ttu-id="65269-895">指定した場合は、追加の MIME マップのユーザー定義セットも検索されます。</span><span class="sxs-lookup"><span data-stu-id="65269-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="65269-896">ユーザー定義マップの詳細については、*nx_http_server_mime_maps_addtional_set()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65269-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="65269-897">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="65269-897">This service is deprecated.</span></span> <span data-ttu-id="65269-898">開発者は *nx_http_server_type_get_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="65269-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="65269-899">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-899">**Input Parameters**</span></span>

- <span data-ttu-id="65269-900">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="65269-901">**name** 検索するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="65269-902">**http_type_string** (抽出された HTML の種類へのポインター)</span><span class="sxs-lookup"><span data-stu-id="65269-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="65269-903">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-903">**Return Values**</span></span>

- <span data-ttu-id="65269-904">**文字列の長さ (バイト単位)** 0 以外の値は成功です</span><span class="sxs-lookup"><span data-stu-id="65269-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="65269-905">**0 はエラーを示します**</span><span class="sxs-lookup"><span data-stu-id="65269-905">**Zero indicates error**</span></span>

<span data-ttu-id="65269-906">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-906">**Allowed From**</span></span>

<span data-ttu-id="65269-907">Application</span><span class="sxs-lookup"><span data-stu-id="65269-907">Application</span></span>

<span data-ttu-id="65269-908">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="65269-909">詳細な例については、</span><span class="sxs-lookup"><span data-stu-id="65269-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="65269-910">*nx_http_server_callback_generate_response_header* の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65269-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="65269-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="65269-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="65269-912">クライアントの HTTP 要求からファイルの種類を抽出する</span><span class="sxs-lookup"><span data-stu-id="65269-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="65269-913">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="65269-914">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-914">**Description**</span></span>

<span data-ttu-id="65269-915">このサービスは、*http_type_string* バッファー内の HTTP 要求の種類と、入力バッファー *name* からの戻り値 (通常は URL) 内のその長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="65269-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="65269-916">MIME マップが見つからない場合、既定で "text/plain" という種類に設定されます。</span><span class="sxs-lookup"><span data-stu-id="65269-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="65269-917">それ以外の場合、抽出された種類を HTTP サーバーの既定の MIME マップと比較して、一致するものを探します。</span><span class="sxs-lookup"><span data-stu-id="65269-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="65269-918">NetX Duo HTTP サーバーの既定の MIME マップは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65269-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="65269-919">html text/html</span><span class="sxs-lookup"><span data-stu-id="65269-919">html text/html</span></span>
- <span data-ttu-id="65269-920">htm text/html</span><span class="sxs-lookup"><span data-stu-id="65269-920">htm text/html</span></span>
- <span data-ttu-id="65269-921">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="65269-921">txt text/plain</span></span>
- <span data-ttu-id="65269-922">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="65269-922">gif image/gif</span></span>
- <span data-ttu-id="65269-923">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="65269-923">jpg image/jpeg</span></span>
- <span data-ttu-id="65269-924">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="65269-924">ico image/x-icon</span></span>

<span data-ttu-id="65269-925">指定した場合は、追加の MIME マップのユーザー定義セットも検索されます。</span><span class="sxs-lookup"><span data-stu-id="65269-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="65269-926">ユーザー定義マップの詳細については、*nx_http_server_mime_maps_addtional_set()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65269-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="65269-927">このサービスは *nx_http_server_type_get()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65269-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="65269-928">このバージョンでは、追加の長さの情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="65269-928">This version supplies additional length information.</span></span>

<span data-ttu-id="65269-929">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-929">**Input Parameters**</span></span>

- <span data-ttu-id="65269-930">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="65269-931">**name** 検索するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="65269-932">**name_length** 検索するバッファーの長さ</span><span class="sxs-lookup"><span data-stu-id="65269-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="65269-933">**http_type_string** (抽出された HTML の種類へのポインター)</span><span class="sxs-lookup"><span data-stu-id="65269-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="65269-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="65269-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="65269-935">*http_type_string* バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="65269-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="65269-936">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-936">**Return Values**</span></span>

- <span data-ttu-id="65269-937">**文字列の長さ (バイト単位)** 0 以外の値は成功です</span><span class="sxs-lookup"><span data-stu-id="65269-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="65269-938">0 はエラーを示します</span><span class="sxs-lookup"><span data-stu-id="65269-938">Zero indicates error</span></span>

<span data-ttu-id="65269-939">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-939">**Allowed From**</span></span>

<span data-ttu-id="65269-940">Application</span><span class="sxs-lookup"><span data-stu-id="65269-940">Application</span></span>

<span data-ttu-id="65269-941">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
       my_server.nx_http_server_request_resource, &resource_length,
       sizeof(my_server.nx_http_server_request_resource) - 1))
    {
        return;
    }
/* Extract the HTTP type. */
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="65269-942">詳細な例については、</span><span class="sxs-lookup"><span data-stu-id="65269-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="65269-943">*nx_http_server_callback_generate_response_header* の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65269-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="65269-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="65269-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="65269-945">ダイジェスト認証コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="65269-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="65269-946">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-946">**Prototype**</span></span>

```c
UINT nx_http_server_digest_authenticate_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                         CHAR *name_ptr,
                                         CHAR *realm_ptr,
                                         CHAR *password_ptr,
                                         CHAR *method,
                                         CHAR *authorization_uri,
                                         CHAR *authorization_nc,
                                         CHAR *authorization_cnonce
                                         ));
```

<span data-ttu-id="65269-947">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-947">**Description**</span></span>

<span data-ttu-id="65269-948">このサービスは、ダイジェスト認証の実行時に呼び出されるコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="65269-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="65269-949">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-949">**Input Parameters**</span></span>

- <span data-ttu-id="65269-950">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="65269-951">**digest_authenticate_callback** ダイジェスト認証コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="65269-952">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-952">**Return Values**</span></span>

- <span data-ttu-id="65269-953">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="65269-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="65269-954">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="65269-955">NX_NOT_SUPPORTED (0x4B) ダイジェスト認証が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="65269-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="65269-956">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-956">**Allowed From**</span></span>

<span data-ttu-id="65269-957">Application</span><span class="sxs-lookup"><span data-stu-id="65269-957">Application</span></span>

<span data-ttu-id="65269-958">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="65269-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="65269-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="65269-960">認証確認コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="65269-960">Set authentication checking callback function</span></span>

<span data-ttu-id="65269-961">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="65269-961">**Prototype**</span></span>

```c
UINT nx_http_server_authentication_check_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*authentication_check_extended)(
                                          NX_HTTP_SERVER *server_ptr,
                                          UINT request_type,
                                          CHAR *resource,
                                          CHAR **name,
                                          UINT *name_length,
                                          CHAR **password,
                                          UINT *password_length,
                                          CHAR **realm,
                                          UINT *realm_length
                                          ));
```

<span data-ttu-id="65269-962">**説明**</span><span class="sxs-lookup"><span data-stu-id="65269-962">**Description**</span></span>

<span data-ttu-id="65269-963">このサービスは、認証確認のコールバック関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="65269-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="65269-964">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="65269-964">**Input Parameters**</span></span>

- <span data-ttu-id="65269-965">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="65269-966">**authentication_check_extended** アプリケーションの認証確認へのポインター</span><span class="sxs-lookup"><span data-stu-id="65269-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="65269-967">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="65269-967">**Return Values**</span></span>

- <span data-ttu-id="65269-968">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="65269-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="65269-969">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="65269-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="65269-970">**許可元**</span><span class="sxs-lookup"><span data-stu-id="65269-970">**Allowed From**</span></span>

<span data-ttu-id="65269-971">Application</span><span class="sxs-lookup"><span data-stu-id="65269-971">Application</span></span>

<span data-ttu-id="65269-972">**例**</span><span class="sxs-lookup"><span data-stu-id="65269-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```