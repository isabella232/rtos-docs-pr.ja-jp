---
title: 第 3 章 - Azure RTOS NetX Duo HTTP サービスの説明
description: この章には、すべての Azure RTOS NetX Duo HTTP サービス (以下に記載) の説明がアルファベット順で含まれています。ただし、同じサービスの "NetX" (IPv4 のみ) 版はペアにまとめられています。
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810784"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="38738-103">第 3 章 - Azure RTOS NetX Duo HTTP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="38738-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="38738-104">この章には、すべての Azure RTOS NetX Duo HTTP サービス (以下に記載) の説明がアルファベット順で含まれています。ただし、同じサービスの "NetX" (IPv4 のみ) 版はペアにまとめられています。</span><span class="sxs-lookup"><span data-stu-id="38738-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="38738-105">次の API の説明にある「戻り値」セクションでは、太字の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="38738-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="38738-106">**HTTP クライアントのサービス:**</span><span class="sxs-lookup"><span data-stu-id="38738-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="38738-107">**nx_http_client_create** *HTTP クライアント インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="38738-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="38738-108">**nx_http_client_delete** *HTTP クライアント インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="38738-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="38738-109">**nx_http_client_get_start** *HTTP GET 要求を開始する (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="38738-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="38738-110">**nx_http_client_get_start_extended** *HTTP GET 要求を開始する (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="38738-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="38738-111">**nxd_http_client_get_start** *HTTP GET 要求を開始する (IPv4 または IPv6)*</span><span class="sxs-lookup"><span data-stu-id="38738-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="38738-112">**nxd_http_client_get_start_extended** *HTTP GET 要求を開始する (IPv4 または IPv6)*</span><span class="sxs-lookup"><span data-stu-id="38738-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="38738-113">**nx_http_client_get_packet** *次のリソース データ パケットを取得する*</span><span class="sxs-lookup"><span data-stu-id="38738-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="38738-114">**nx_http_client_put_start** *HTTP PUT 要求を開始する (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="38738-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="38738-115">**nx_http_client_put_start_extended** *HTTP PUT 要求を開始する (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="38738-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="38738-116">**nxd_http_client_put_start** *HTTP PUT 要求を開始する (IPv4 または IPv6)*</span><span class="sxs-lookup"><span data-stu-id="38738-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="38738-117">**nxd_http_client_put_start_extended** *HTTP PUT 要求を開始する (IPv4 または IPv6)*</span><span class="sxs-lookup"><span data-stu-id="38738-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="38738-118">**nx_http_client_put_packet** *次のリソース データ パケットを送信する*</span><span class="sxs-lookup"><span data-stu-id="38738-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="38738-119">**nx_http_client_set_connect_port** *HTTP サーバーに接続するポートを変更する*</span><span class="sxs-lookup"><span data-stu-id="38738-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="38738-120">**HTTP サーバーのサービス:**</span><span class="sxs-lookup"><span data-stu-id="38738-120">**HTTP server services:**</span></span>

- <span data-ttu-id="38738-121">**nx_http_server_cache_info_callback_set** *指定された URL の有効期間と最終更新日を取得するコールバックを設定する*</span><span class="sxs-lookup"><span data-stu-id="38738-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="38738-122">**nx_http_server_callback_data_send** *コールバック関数から HTTP データを送信する*</span><span class="sxs-lookup"><span data-stu-id="38738-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="38738-123">**nx_http_server_callback_generate_response_header** *コールバック関数内で応答ヘッダーを作成する*</span><span class="sxs-lookup"><span data-stu-id="38738-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="38738-124">**nx_http_server_callback_generate_response_header_extended** *コールバック関数内で応答ヘッダーを作成する*</span><span class="sxs-lookup"><span data-stu-id="38738-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="38738-125">**nx_http_server_callback_packet_send** *HTTP コールバックから HTTP パケットを送信する*</span><span class="sxs-lookup"><span data-stu-id="38738-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="38738-126">**nx_http_server_callback_response_send** *コールバック関数から応答を送信する*</span><span class="sxs-lookup"><span data-stu-id="38738-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="38738-127">**nx_http_server_callback_response_send_extended** *コールバック関数から応答を送信する*</span><span class="sxs-lookup"><span data-stu-id="38738-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="38738-128">**nx_http_server_content_get** *要求からコンテンツを取得する*</span><span class="sxs-lookup"><span data-stu-id="38738-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="38738-129">**nx_http_server_content_get_extended** *要求からコンテンツを取得する (空 (コンテンツの長さがゼロ) の要求がサポートされます)*</span><span class="sxs-lookup"><span data-stu-id="38738-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="38738-130">**nx_http_server_content_length_get** *要求のコンテンツの長さを取得する*</span><span class="sxs-lookup"><span data-stu-id="38738-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="38738-131">**nx_http_server_content_length_get_extended** *要求のコンテンツの長さを取得する (空 (コンテンツの長さがゼロ) の要求がサポートされます)*</span><span class="sxs-lookup"><span data-stu-id="38738-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="38738-132">**nx_http_server_create** *HTTP サーバー インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="38738-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="38738-133">**nx_http_server_delete** *HTTP サーバー インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="38738-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="38738-134">**nx_http_server_get_entity_content** *URL のエンティティ コンテンツのサイズと場所を返す*</span><span class="sxs-lookup"><span data-stu-id="38738-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="38738-135">**nx_http_server_get_entity_header** *指定されたバッファーに URL エンティティ ヘッダーを抽出する*</span><span class="sxs-lookup"><span data-stu-id="38738-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="38738-136">**nx_http_server_gmt_callback_set** *GMT の日付と時刻を取得するコールバックを設定する*</span><span class="sxs-lookup"><span data-stu-id="38738-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="38738-137">**nx_http_server_invalid_userpassword_notify_set** *クライアント要求で無効なユーザー名とパスワードを受信した場合のコールバックを設定する*</span><span class="sxs-lookup"><span data-stu-id="38738-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="38738-138">**nx_http_server_mime_maps_additional_set** *HTML 用の追加の MIME マップを定義する*</span><span class="sxs-lookup"><span data-stu-id="38738-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="38738-139">**nx_http_server_packet_content_find** *HTTP ヘッダーからコンテンツの長さを抽出し、コンテンツ データの先頭にポインターを設定する*</span><span class="sxs-lookup"><span data-stu-id="38738-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="38738-140">**nx_http_server_packet_get** *クライアント パケットを直接受信する*</span><span class="sxs-lookup"><span data-stu-id="38738-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="38738-141">**nx_http_server_param_get** *要求からパラメーターを取得する*</span><span class="sxs-lookup"><span data-stu-id="38738-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="38738-142">**nx_http_server_query_get** *要求からクエリを取得する*</span><span class="sxs-lookup"><span data-stu-id="38738-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="38738-143">**nx_http_server_start** *HTTP サーバーを起動する*</span><span class="sxs-lookup"><span data-stu-id="38738-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="38738-144">**nx_http_server_stop** *HTTP サーバーを停止する*</span><span class="sxs-lookup"><span data-stu-id="38738-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="38738-145">**nx_http_server_type_get (非推奨)** *ヘッダーから HTTP の種類 (text/plain など) を抽出する*</span><span class="sxs-lookup"><span data-stu-id="38738-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="38738-146">**nx_http_server_type_get_extended** *ヘッダーから HTTP の種類 (text/plain など) を抽出する*</span><span class="sxs-lookup"><span data-stu-id="38738-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="38738-147">**nx_http_server_digest_authenticate_notify_set** *ダイジェスト認証コールバック関数を設定する*</span><span class="sxs-lookup"><span data-stu-id="38738-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="38738-148">**nx_http_server_authentication_check_set** *認証確認コールバック関数を設定する*</span><span class="sxs-lookup"><span data-stu-id="38738-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="38738-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="38738-149">nx_http_client_create</span></span>

<span data-ttu-id="38738-150">PPPoE クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="38738-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-151">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="38738-152">説明</span><span class="sxs-lookup"><span data-stu-id="38738-152">Description</span></span>

<span data-ttu-id="38738-153">このサービスは、指定された IP インスタンスに HTTP クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="38738-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-154">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-154">Input Parameters</span></span>

 - <span data-ttu-id="38738-155">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-156">**client_name** HTTP クライアント インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="38738-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="38738-157">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="38738-158">**pool_ptr** 既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="38738-159">このプール内のパケットはペイロードが応答ヘッダー全体を処理するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="38738-160">これは *nx_http.h* 内の NX_HTTP_CLIENT_MIN_PACKET_SIZE によって定義されています。</span><span class="sxs-lookup"><span data-stu-id="38738-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="38738-161">**window_size** クライアントの TCP ソケット受信ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="38738-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-162">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-162">Return Values</span></span>

 - <span data-ttu-id="38738-163">**NX_SUCCESS** (0x00) HTTP クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="38738-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="38738-164">NX_PTR_ERROR (0x07) HTTP、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="38738-165">NX_HTTP_POOL_ERROR (0xE9) パケット プールのペイロード サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-166">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-166">Allowed From</span></span>

<span data-ttu-id="38738-167">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="38738-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-168">例</span><span class="sxs-lookup"><span data-stu-id="38738-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="38738-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="38738-169">nx_http_client_delete</span></span>

<span data-ttu-id="38738-170">HTTP クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="38738-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-171">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-172">説明</span><span class="sxs-lookup"><span data-stu-id="38738-172">Description</span></span>

<span data-ttu-id="38738-173">このサービスは、以前に作成された HTTP クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="38738-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-174">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-174">Input Parameters</span></span>

 - <span data-ttu-id="38738-175">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-176">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-176">Return Values</span></span>

 - <span data-ttu-id="38738-177">**NX_SUCCESS** (0x00) HTTP クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="38738-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="38738-178">NX_PTR_ERROR (0x07) HTTP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="38738-179">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-180">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-180">Allowed From</span></span>

<span data-ttu-id="38738-181">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-182">例</span><span class="sxs-lookup"><span data-stu-id="38738-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="38738-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="38738-183">nx_http_client_get_start</span></span>

<span data-ttu-id="38738-184">IPv4 経由で HTTP GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="38738-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-185">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-186">説明</span><span class="sxs-lookup"><span data-stu-id="38738-186">Description</span></span>

<span data-ttu-id="38738-187">このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースに対する GET 要求の作成と送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="38738-188">このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="38738-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-189">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="38738-190">このサービスは、IPv4 ネットワーク経由でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="38738-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="38738-191">IPv6 ネットワークに接続する必要があるアプリケーションの場合は、*nxd_http_client_get_start_extended()* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="38738-192">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-192">This service is deprecated.</span></span> <span data-ttu-id="38738-193">開発者は *nx_http_client_get_start_extended()* または *nxd_http_client_get_start_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-194">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-194">Input Parameters</span></span>

 - <span data-ttu-id="38738-195">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-196">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-197">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-198">**input_ptr** GET 要求の追加データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="38738-199">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="38738-199">This is optional.</span></span> <span data-ttu-id="38738-200">有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="38738-201">**input_size** ```input_ptr``` が指す省略可能な追加入力のバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="38738-202">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-203">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-204">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="38738-205">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="38738-206">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-208">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-209">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-210">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-210">Return Values</span></span>

 - <span data-ttu-id="38738-211">**NX_SUCCESS** (0x00) HTTP クライアントの</span><span class="sxs-lookup"><span data-stu-id="38738-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="38738-212">GET 開始メッセージが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="38738-212">GET start message.</span></span>
 - <span data-ttu-id="38738-213">**NX_HTTP_ERROR** (0xE0) 内部 HTTP クライアント エラー</span><span class="sxs-lookup"><span data-stu-id="38738-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="38738-214">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-215">**NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー。</span><span class="sxs-lookup"><span data-stu-id="38738-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="38738-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="38738-217">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-218">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-219">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-219">Allowed From</span></span>

<span data-ttu-id="38738-220">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-221">例</span><span class="sxs-lookup"><span data-stu-id="38738-221">Example</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="38738-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="38738-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="38738-223">IPv4 経由で HTTP GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="38738-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-224">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-225">説明</span><span class="sxs-lookup"><span data-stu-id="38738-225">Description</span></span>

<span data-ttu-id="38738-226">このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースに対する GET 要求の作成と送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="38738-227">このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="38738-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-228">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="38738-229">このサービスは、IPv4 ネットワーク経由でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="38738-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="38738-230">IPv6 ネットワークに接続する必要があるアプリケーションの場合は、*nxd_http_client_get_start_extended()* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="38738-231">このサービスは *nx_http_client_get_start()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="38738-232">呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-233">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-233">Input Parameters</span></span>

 - <span data-ttu-id="38738-234">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-235">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-236">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-237">**resource_length** 要求されたリソースの URL 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-238">**input_ptr** GET 要求の追加データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="38738-239">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="38738-239">This is optional.</span></span> <span data-ttu-id="38738-240">有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="38738-241">**input_size** ```input_ptr``` が指す省略可能な追加入力のバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="38738-242">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-243">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-244">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-245">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="38738-246">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="38738-247">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-248">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-250">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-251">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-252">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-252">Return Values</span></span>

 - <span data-ttu-id="38738-253">**NX_SUCCESS** (0x00) HTTP クライアントの</span><span class="sxs-lookup"><span data-stu-id="38738-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="38738-254">GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-254">GET start message</span></span>
 - <span data-ttu-id="38738-255">**NX_HTTP_ERROR** (0xE0) 内部 HTTP クライアント エラー</span><span class="sxs-lookup"><span data-stu-id="38738-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="38738-256">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-257">**NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー。</span><span class="sxs-lookup"><span data-stu-id="38738-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="38738-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="38738-259">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-260">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-261">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-261">Allowed From</span></span>

<span data-ttu-id="38738-262">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-263">例</span><span class="sxs-lookup"><span data-stu-id="38738-263">Example</span></span>

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="38738-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="38738-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="38738-265">HTTP GET 要求を送信する (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="38738-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-266">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-267">説明</span><span class="sxs-lookup"><span data-stu-id="38738-267">Description</span></span>

<span data-ttu-id="38738-268">このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースに対する GET 要求の作成と送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="38738-269">IPv4 または IPv6 ネットワークに接続するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="38738-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="38738-270">このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="38738-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="38738-271">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="38738-272">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-272">This service is deprecated.</span></span> <span data-ttu-id="38738-273">開発者は *nxd_http_client_get_start_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-274">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-274">Input Parameters</span></span>

 - <span data-ttu-id="38738-275">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-276">**Server_ip** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-277">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-278">**input_ptr** GET 要求の追加データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="38738-279">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="38738-279">This is optional.</span></span> <span data-ttu-id="38738-280">有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="38738-281">**input_size** ```input_ptr``` が指す省略可能な追加入力のバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="38738-282">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-283">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-284">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-285">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="38738-286">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="38738-287">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-288">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-290">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-291">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-292">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-292">Return Values</span></span>

 - <span data-ttu-id="38738-293">**NX_SUCCESS** (0x00) GET 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="38738-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) パスワードがバッファー サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="38738-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="38738-295">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-296">**NX_HTTP_FAILED** (0xE2) パケット パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="38738-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="38738-298">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-299">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-300">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-300">Allowed From</span></span>

<span data-ttu-id="38738-301">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-302">例</span><span class="sxs-lookup"><span data-stu-id="38738-302">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="38738-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="38738-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="38738-304">HTTP GET 要求を送信する (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="38738-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-305">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-306">説明</span><span class="sxs-lookup"><span data-stu-id="38738-306">Description</span></span>

<span data-ttu-id="38738-307">このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースに対する GET 要求の作成と送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="38738-308">IPv4 または IPv6 ネットワークに接続するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="38738-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="38738-309">このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="38738-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-310">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="38738-311">このサービスは *nxd_http_client_get_start()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="38738-312">呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-313">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-313">Input Parameters</span></span>

 - <span data-ttu-id="38738-314">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-315">**Server_ip** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-316">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-317">**resource_length** 要求されたリソースの URL 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-318">**input_ptr** GET 要求の追加データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="38738-319">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="38738-319">This is optional.</span></span> <span data-ttu-id="38738-320">有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="38738-321">**input_size** ```input_ptr``` が指す省略可能な追加入力のバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="38738-322">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-323">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-324">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-325">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="38738-326">**wait_option** サービスが HTTP クライアントの GET 開始を内部的に処理するのを待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="38738-327">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-328">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-330">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-331">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-332">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-332">Return Values</span></span>

 - <span data-ttu-id="38738-333">**NX_SUCCESS** (0x00) GET 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="38738-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) パスワードがバッファー サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="38738-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="38738-335">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-336">**NX_HTTP_FAILED** (0xE2) パケット パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="38738-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="38738-338">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-339">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-340">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-340">Allowed From</span></span>

<span data-ttu-id="38738-341">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-342">例</span><span class="sxs-lookup"><span data-stu-id="38738-342">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="38738-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="38738-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="38738-344">次のリソース データ パケットを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-345">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-346">説明</span><span class="sxs-lookup"><span data-stu-id="38738-346">Description</span></span>

<span data-ttu-id="38738-347">このサービスは、前の *nx_http_client_get_start* 呼び出しによって要求されたリソースのコンテンツの次のパケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="38738-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="38738-348">NX_HTTP_GET_DONE という戻りステータスを受け取るまで、このルーチンを連続で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-349">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-349">Input Parameters</span></span>

 - <span data-ttu-id="38738-350">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-351">**packet_ptr** 部分的なリソース コンテンツを含むパケット ポインターのコピー先。</span><span class="sxs-lookup"><span data-stu-id="38738-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="38738-352">**wait_option** サービスが HTTP クライアントのパケット取得を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="38738-353">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-354">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-356">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-357">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-358">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-358">Return Values</span></span>

 - <span data-ttu-id="38738-359">**NX_SUCCESS** (0x00) HTTP クライアントのパケット取得が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="38738-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="38738-360">**NX_HTTP_GET_DONE** (0xEC) HTTP クライアントのパケット取得が完了しました</span><span class="sxs-lookup"><span data-stu-id="38738-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="38738-361">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントが GET モードではありません。</span><span class="sxs-lookup"><span data-stu-id="38738-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="38738-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) パケット長が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="38738-363">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-364">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-365">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-365">Allowed From</span></span>

<span data-ttu-id="38738-366">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-367">例</span><span class="sxs-lookup"><span data-stu-id="38738-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="38738-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="38738-368">nx_http_client_put_start</span></span>

<span data-ttu-id="38738-369">IPv4 経由で HTTP PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="38738-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-370">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-371">説明</span><span class="sxs-lookup"><span data-stu-id="38738-371">Description</span></span>

<span data-ttu-id="38738-372">このサービスは、指定された IP アドレスの HTTP サーバーへの、指定されたリソースに対する PUT 要求の送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="38738-373">このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet()* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-374">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="38738-375">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-375">This service is deprecated.</span></span> <span data-ttu-id="38738-376">開発者は *nxd_http_client_put_start_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-377">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-377">Input Parameters</span></span>

 - <span data-ttu-id="38738-378">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-379">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-380">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-381">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-382">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-383">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="38738-384">後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="38738-385">**wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="38738-386">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-387">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-389">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-390">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます</span><span class="sxs-lookup"><span data-stu-id="38738-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-391">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-391">Return Values</span></span>

 - <span data-ttu-id="38738-392">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="38738-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="38738-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="38738-394">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-395">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-396">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="38738-397">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-398">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-398">Allowed From</span></span>

<span data-ttu-id="38738-399">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-400">例</span><span class="sxs-lookup"><span data-stu-id="38738-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="38738-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="38738-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="38738-402">IPv4 経由で HTTP PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="38738-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-403">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-404">説明</span><span class="sxs-lookup"><span data-stu-id="38738-404">Description</span></span>

<span data-ttu-id="38738-405">このサービスは、指定された IP アドレスの HTTP サーバーへの、指定されたリソースに対する PUT 要求の送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="38738-406">このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet()* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-407">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="38738-408">このサービスは *nx_http_client_put_start()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="38738-409">呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-410">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-410">Input Parameters</span></span>

 - <span data-ttu-id="38738-411">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-412">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-413">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-414">**resource_length** サーバーに送信するリソースの URL 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="38738-415">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-416">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-417">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-418">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="38738-419">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="38738-420">後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="38738-421">**wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="38738-422">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-423">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-425">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-426">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-427">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-427">Return Values</span></span>

 - <span data-ttu-id="38738-428">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="38738-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="38738-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="38738-430">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-431">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-432">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="38738-433">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-434">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-434">Allowed From</span></span>

<span data-ttu-id="38738-435">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-436">例</span><span class="sxs-lookup"><span data-stu-id="38738-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="38738-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="38738-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="38738-438">HTTP PUT 要求を開始する (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="38738-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-439">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-440">説明</span><span class="sxs-lookup"><span data-stu-id="38738-440">Description</span></span>

<span data-ttu-id="38738-441">このサービスは、指定された IP アドレスの HTTP サーバーへの IPv6 経由による、指定されたリソースの PUT (送信) を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="38738-442">このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet()* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-443">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="38738-444">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-444">This service is deprecated.</span></span> <span data-ttu-id="38738-445">開発者は *nxd_http_client_put_start_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-446">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-446">Input Parameters</span></span>

 - <span data-ttu-id="38738-447">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-448">**server_ip** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-449">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="38738-450">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-451">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-452">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="38738-453">後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="38738-454">**wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="38738-455">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-456">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-458">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-459">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-460">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-460">Return Values</span></span>

 - <span data-ttu-id="38738-461">**NX_SUCCESS** (0x00) HTTP クライアントの PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="38738-462">**NX_HTTP_ERROR** (0xE0) HTTP クライアントの内部エラー</span><span class="sxs-lookup"><span data-stu-id="38738-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="38738-463">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-464">**NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー</span><span class="sxs-lookup"><span data-stu-id="38738-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="38738-465">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-466">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="38738-467">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-468">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-468">Allowed From</span></span>

<span data-ttu-id="38738-469">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-470">例</span><span class="sxs-lookup"><span data-stu-id="38738-470">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="38738-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="38738-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="38738-472">HTTP PUT 要求を開始する (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="38738-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-473">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-474">説明</span><span class="sxs-lookup"><span data-stu-id="38738-474">Description</span></span>

<span data-ttu-id="38738-475">このサービスは、指定された IP アドレスの HTTP サーバーへの IPv6 経由による、指定されたリソースの PUT (送信) を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="38738-476">このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet()* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-477">リソース文字列では、ローカル ファイルを参照できます (例: ``` “/index.htm” ```)。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: ```http://abc.website.com/index.htm```)。</span><span class="sxs-lookup"><span data-stu-id="38738-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="38738-478">このサービスは *nxd_http_client_put_start()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="38738-479">呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-480">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-480">Input Parameters</span></span>

 - <span data-ttu-id="38738-481">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-482">**ip_address** HTTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="38738-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="38738-483">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="38738-484">**resource_length** サーバーに送信するリソースの URL 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="38738-485">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-486">**username_length** 認証用の省略可能なユーザー名の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="38738-487">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="38738-488">**password_length** 認証用の省略可能なパスワードの長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="38738-489">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="38738-490">後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="38738-491">**wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="38738-492">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-493">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-495">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-496">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-497">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-497">Return Values</span></span>

 - <span data-ttu-id="38738-498">**NX_SUCCESS** (0x00) HTTP クライアントの PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="38738-499">**NX_HTTP_ERROR** (0xE0) HTTP クライアントの内部エラー</span><span class="sxs-lookup"><span data-stu-id="38738-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="38738-500">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-501">NX_HTTP_FAILED (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー</span><span class="sxs-lookup"><span data-stu-id="38738-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="38738-502">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-503">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="38738-504">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-505">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-505">Allowed From</span></span>

<span data-ttu-id="38738-506">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-507">例</span><span class="sxs-lookup"><span data-stu-id="38738-507">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="38738-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="38738-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="38738-509">次のリソース データ パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="38738-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-510">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="38738-511">説明</span><span class="sxs-lookup"><span data-stu-id="38738-511">Description</span></span>

<span data-ttu-id="38738-512">このサービスは、HTTP サーバーへの、リソース コンテンツの次のパケットの送信を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-513">送信されるパケットの合計長が前の *nx_http_client_put_start* 呼び出しで指定された "total_bytes" と等しくなるまで、このルーチンを繰り返し呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-514">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-514">Input Parameters</span></span>

 - <span data-ttu-id="38738-515">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-516">**packet_ptr** HTTP サーバーに送信されるリソースの次のコンテンツへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="38738-517">**wait_option** サービスが HTTP クライアントのパケットの PUT を内部的に処理するのを待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38738-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="38738-518">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="38738-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38738-519">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38738-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="38738-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38738-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="38738-521">TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="38738-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="38738-522">数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-523">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-523">Return Values</span></span>

 - <span data-ttu-id="38738-524">**NX_SUCCESS** (0x00) HTTP クライアントのパケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="38738-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="38738-525">**NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません</span><span class="sxs-lookup"><span data-stu-id="38738-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="38738-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) サーバー エラー コードを受信しました</span><span class="sxs-lookup"><span data-stu-id="38738-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="38738-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) パケット長が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="38738-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="38738-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) PUT が完了する前にサーバーが応答しました</span><span class="sxs-lookup"><span data-stu-id="38738-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="38738-530">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-531">NX_INVALID_PACKET (0x12) パケットが TCP ヘッダーに対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="38738-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="38738-532">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-533">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-533">Allowed From</span></span>

<span data-ttu-id="38738-534">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-535">例</span><span class="sxs-lookup"><span data-stu-id="38738-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="38738-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="38738-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="38738-537">サーバーへの接続ポートを設定する</span><span class="sxs-lookup"><span data-stu-id="38738-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-538">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="38738-539">説明</span><span class="sxs-lookup"><span data-stu-id="38738-539">Description</span></span>

<span data-ttu-id="38738-540">このサービスは、実行時に HTTP サーバーに接続する際の接続ポートを指定されたポートに変更します。</span><span class="sxs-lookup"><span data-stu-id="38738-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="38738-541">それ以外の場合、接続ポートは既定で 80 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="38738-542">これは、*nx_http_client_get_start()* および *nx_http_client_put_start()* (HTTP クライアントがサーバーに接続する場合など) の前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-543">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-543">Input Parameters</span></span>

 - <span data-ttu-id="38738-544">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="38738-545">**port** サーバーに接続するためのポート。</span><span class="sxs-lookup"><span data-stu-id="38738-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-546">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-546">Return Values</span></span>

 - <span data-ttu-id="38738-547">**NX_SUCCESS** (0x00) ポートが正常に変更されました</span><span class="sxs-lookup"><span data-stu-id="38738-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="38738-548">NX_INVALID_PORT (0x46) ポートが最大値 (0xFFFF) を超えているか、0 です</span><span class="sxs-lookup"><span data-stu-id="38738-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="38738-549">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-550">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-550">Allowed From</span></span>

<span data-ttu-id="38738-551">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="38738-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="38738-552">例</span><span class="sxs-lookup"><span data-stu-id="38738-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="38738-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="38738-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="38738-554">URL の最大有効期間と日付を取得するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="38738-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-555">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="38738-556">説明</span><span class="sxs-lookup"><span data-stu-id="38738-556">Description</span></span>

<span data-ttu-id="38738-557">このサービスは、指定されたリソースの最大有効期間と最終更新日を取得するために呼び出されるコールバック サービスを設定します。</span><span class="sxs-lookup"><span data-stu-id="38738-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-558">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-558">Input Parameters</span></span>

 - <span data-ttu-id="38738-559">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-560">**cache_info_get** コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="38738-561">**max_age** リソースの最大有効期間へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="38738-562">**data** 返された最終更新日へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-563">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-563">Return Values</span></span>

 - <span data-ttu-id="38738-564">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="38738-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="38738-565">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-566">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-566">Allowed From</span></span>

<span data-ttu-id="38738-567">初期化</span><span class="sxs-lookup"><span data-stu-id="38738-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="38738-568">例</span><span class="sxs-lookup"><span data-stu-id="38738-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="38738-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="38738-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="38738-570">コールバック関数からデータを送信する</span><span class="sxs-lookup"><span data-stu-id="38738-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-571">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="38738-572">説明</span><span class="sxs-lookup"><span data-stu-id="38738-572">Description</span></span>

<span data-ttu-id="38738-573">このサービスは、アプリケーションのコールバック ルーチンから、指定されたパケット内のデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="38738-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="38738-574">これは通常、GET または POST 要求に関連付けられた動的データを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-575">この関数を使用する場合、コールバック ルーチンから応答全体を適切な形式で送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="38738-576">また、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-577">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-577">Input Parameters</span></span>

 - <span data-ttu-id="38738-578">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-579">**data_ptr** 送信するデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="38738-580">**data_length** 送信するバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-581">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-581">Return Values</span></span>

 - <span data-ttu-id="38738-582">**NX_SUCCESS** (0x00) サーバー データが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="38738-583">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-584">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-584">Allowed From</span></span>

<span data-ttu-id="38738-585">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-586">例</span><span class="sxs-lookup"><span data-stu-id="38738-586">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="38738-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="38738-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="38738-588">コールバック関数内で応答ヘッダーを作成する</span><span class="sxs-lookup"><span data-stu-id="38738-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-589">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="38738-590">説明</span><span class="sxs-lookup"><span data-stu-id="38738-590">Description</span></span>

<span data-ttu-id="38738-591">このサービスは、HTTP サーバーがクライアントの GET、PUT、DELETE 要求に応答するときに、内部関数 *_nx_http_server_generate_response_header* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="38738-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="38738-592">これは、HTTP サーバー アプリケーションがクライアントへのその応答を設計しているときに、HTTP サーバーのコールバック関数内で使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="38738-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="38738-593">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-593">This service is deprecated.</span></span> <span data-ttu-id="38738-594">開発者は *nxd_http_server_callback_generate_response_header_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-595">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-595">Input Parameters</span></span>

 - <span data-ttu-id="38738-596">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-597">**packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="38738-598">**status_code** リソースの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="38738-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="38738-599">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="38738-599">Examples:</span></span>
    - <span data-ttu-id="38738-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="38738-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="38738-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="38738-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="38738-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="38738-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="38738-603">**content_length** コンテンツのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="38738-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="38738-604">**content_type** HTTP の種類 (例: "text/plain")</span><span class="sxs-lookup"><span data-stu-id="38738-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="38738-605">**additional_header** 追加のヘッダー テキストへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-606">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-606">Return Values</span></span>

 - <span data-ttu-id="38738-607">**NX_SUCCESS** (0x00) ヘッダーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="38738-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="38738-608">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-609">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-609">Allowed From</span></span>

<span data-ttu-id="38738-610">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-611">例</span><span class="sxs-lookup"><span data-stu-id="38738-611">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="38738-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="38738-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="38738-613">コールバック関数内で応答ヘッダーを作成する</span><span class="sxs-lookup"><span data-stu-id="38738-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-614">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-614">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="38738-615">説明</span><span class="sxs-lookup"><span data-stu-id="38738-615">Description</span></span>

<span data-ttu-id="38738-616">このサービスは、HTTP サーバーがクライアントの GET、PUT、DELETE 要求に応答するときに、内部関数 *_nx_http_server_generate_response_header()* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="38738-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="38738-617">これは、HTTP サーバー アプリケーションがクライアントへのその応答を設計しているときに、HTTP サーバーのコールバック関数内で使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="38738-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="38738-618">このサービスは *nx_http_server_callback_generate_response_header()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="38738-619">このバージョンでは、コールバック関数に追加の長さの情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="38738-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-620">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-620">Input Parameters</span></span>

 - <span data-ttu-id="38738-621">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-622">**packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="38738-623">**status_code** リソースの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="38738-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="38738-624">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="38738-624">Examples:</span></span>
    - <span data-ttu-id="38738-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="38738-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="38738-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="38738-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="38738-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="38738-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="38738-628">**status_code** 状態コードの長さ</span><span class="sxs-lookup"><span data-stu-id="38738-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="38738-629">**content_length** コンテンツのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="38738-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="38738-630">**content_type** HTTP の種類 (例: "text/plain")</span><span class="sxs-lookup"><span data-stu-id="38738-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="38738-631">**content_type_length** HTTP の種類の長さ</span><span class="sxs-lookup"><span data-stu-id="38738-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="38738-632">**additional_header** 追加のヘッダー テキストへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="38738-633">**additional_header_length** 追加のヘッダー テキストの長さ</span><span class="sxs-lookup"><span data-stu-id="38738-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-634">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-634">Return Values</span></span>

 - <span data-ttu-id="38738-635">**NX_SUCCESS** (0x00) ヘッダーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="38738-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="38738-636">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-637">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-637">Allowed From</span></span>

<span data-ttu-id="38738-638">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-639">例</span><span class="sxs-lookup"><span data-stu-id="38738-639">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
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
                 length,  server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="38738-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="38738-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="38738-641">コールバック関数から HTTP パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="38738-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-642">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-643">説明</span><span class="sxs-lookup"><span data-stu-id="38738-643">Description</span></span>

<span data-ttu-id="38738-644">このサービスは、HTTP コールバックから完全な HTTP サーバー応答を送信します。</span><span class="sxs-lookup"><span data-stu-id="38738-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="38738-645">HTTP サーバーは、NX_HTTP_SERVER _TIMEOUT_SEND を使用してパケットを送信します。</span><span class="sxs-lookup"><span data-stu-id="38738-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="38738-646">HTTP ヘッダーとデータをパケットに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="38738-647">戻りステータスがエラーを示している場合、HTTP アプリケーションはパケットを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="38738-648">このコールバックは NX_HTTP_CALLBACK_COMPLETED を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="38738-649">詳細な例については、*nx_http_server_callback_generate_response_header()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38738-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-650">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-650">Input Parameters</span></span>

 - <span data-ttu-id="38738-651">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-652">**packet_ptr** 送信するパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-653">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-653">Return Values</span></span>

 - <span data-ttu-id="38738-654">**NX_SUCCESS** (0x00) サーバー パケットが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="38738-655">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-656">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-656">Allowed From</span></span>

<span data-ttu-id="38738-657">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-658">例</span><span class="sxs-lookup"><span data-stu-id="38738-658">Example</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="38738-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="38738-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="38738-660">コールバック関数から応答を送信する</span><span class="sxs-lookup"><span data-stu-id="38738-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-661">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="38738-662">説明</span><span class="sxs-lookup"><span data-stu-id="38738-662">Description</span></span>

<span data-ttu-id="38738-663">このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="38738-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="38738-664">これは通常、GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-665">この関数を使用する場合、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="38738-666">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-666">This service is deprecated.</span></span> <span data-ttu-id="38738-667">開発者は *nxd_http_server_callback_response_send_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-668">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-668">Input Parameters</span></span>

 - <span data-ttu-id="38738-669">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-670">**header** 応答ヘッダー文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="38738-671">**information** 情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="38738-672">**additional_info** 追加の情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-673">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-673">Return Values</span></span>

 - <span data-ttu-id="38738-674">**NX_SUCCESS** (0x00) サーバー応答が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-675">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-675">Allowed From</span></span>

<span data-ttu-id="38738-676">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-677">例</span><span class="sxs-lookup"><span data-stu-id="38738-677">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="38738-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="38738-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="38738-679">コールバック関数から応答を送信する</span><span class="sxs-lookup"><span data-stu-id="38738-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-680">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-680">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="38738-681">説明</span><span class="sxs-lookup"><span data-stu-id="38738-681">Description</span></span>

<span data-ttu-id="38738-682">このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="38738-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="38738-683">これは通常、GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="38738-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-684">この関数を使用する場合、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="38738-685">このサービスは *nx_http_server_callback_response_send()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="38738-686">このバージョンでは、引数として追加の長さの情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="38738-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-687">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-687">Input Parameters</span></span>

 - <span data-ttu-id="38738-688">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-689">**header** 応答ヘッダー文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="38738-690">**header_length** 応答ヘッダー文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="38738-691">**information** 情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="38738-692">**information_length** 情報文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="38738-693">**additional_info** 追加の情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="38738-694">**additional_info_length** 追加の情報文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="38738-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-695">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-695">Return Values</span></span>

 - <span data-ttu-id="38738-696">**NX_SUCCESS** (0x00) サーバー応答が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="38738-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-697">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-697">Allowed From</span></span>

<span data-ttu-id="38738-698">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-699">例</span><span class="sxs-lookup"><span data-stu-id="38738-699">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="38738-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="38738-700">nx_http_server_content_get</span></span>

<span data-ttu-id="38738-701">要求からコンテンツを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-702">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="38738-703">説明</span><span class="sxs-lookup"><span data-stu-id="38738-703">Description</span></span>

<span data-ttu-id="38738-704">このサービスは、POST または PUT HTTP クライアント要求から指定された量のコンテンツの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="38738-705">これは、HTTP サーバーの作成時 (*nx_http_server_create*) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="38738-706">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-706">This service is deprecated.</span></span> <span data-ttu-id="38738-707">開発者は *nx_http_server_content_get_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-708">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-708">Input Parameters</span></span>

 - <span data-ttu-id="38738-709">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-710">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="38738-711">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="38738-712">**byte_offset** コンテンツ領域にオフセットするバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="38738-713">**destination_ptr** コンテンツのコピー先領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="38738-714">**destination_size** コピー先領域の使用可能な最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="38738-715">**actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-716">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-716">Return Values</span></span>

 - <span data-ttu-id="38738-717">**NX_SUCCESS** (0x00) HTTP サーバーのコンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="38738-718">**NX_HTTP_ERROR** (0xE0) HTTP サーバーの内部エラー</span><span class="sxs-lookup"><span data-stu-id="38738-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="38738-719">**NX_HTTP_DATA_END** (0xE7) 要求コンテンツの終わり</span><span class="sxs-lookup"><span data-stu-id="38738-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="38738-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP サーバーがコンテンツの次のパケットを取得中にタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="38738-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="38738-721">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-722">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-723">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-723">Allowed From</span></span>

<span data-ttu-id="38738-724">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-725">例</span><span class="sxs-lookup"><span data-stu-id="38738-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="38738-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="38738-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="38738-727">要求からコンテンツを取得する (長さゼロのコンテンツの長さがサポートされます)</span><span class="sxs-lookup"><span data-stu-id="38738-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-728">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="38738-729">説明</span><span class="sxs-lookup"><span data-stu-id="38738-729">Description</span></span>

<span data-ttu-id="38738-730">このサービスは *nx_http_server_content_get()* とほぼ同じで、POST または PUT HTTP クライアント要求から指定された量のコンテンツの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="38738-731">ただし、コンテンツの長さがゼロ値の要求 ("空の要求") が有効な要求として処理されます。</span><span class="sxs-lookup"><span data-stu-id="38738-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="38738-732">これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="38738-733">このサービスは *nx_http_server_content_get()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="38738-734">このバージョンでは、呼び出し元が追加の長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-735">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-735">Input Parameters</span></span>

 - <span data-ttu-id="38738-736">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-737">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="38738-738">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="38738-739">**byte_offset** コンテンツ領域にオフセットするバイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="38738-740">**destination_ptr** コンテンツのコピー先領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="38738-741">**destination_size** コピー先領域の使用可能な最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="38738-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="38738-742">**actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-743">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-743">Return Values</span></span>

 - <span data-ttu-id="38738-744">**NX_SUCCESS** (0x00) HTTP コンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="38738-745">**NX_HTTP_ERROR** (0xE0) HTTP サーバーの内部エラー</span><span class="sxs-lookup"><span data-stu-id="38738-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="38738-746">**NX_HTTP_DATA_END** (0xE7) 要求コンテンツの終わり</span><span class="sxs-lookup"><span data-stu-id="38738-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="38738-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP サーバーが次のパケットを取得中にタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="38738-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="38738-748">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="38738-749">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-750">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-750">Allowed From</span></span>

<span data-ttu-id="38738-751">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-752">例</span><span class="sxs-lookup"><span data-stu-id="38738-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="38738-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="38738-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="38738-754">要求のコンテンツの長さを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-755">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-756">説明</span><span class="sxs-lookup"><span data-stu-id="38738-756">Description</span></span>

<span data-ttu-id="38738-757">このサービスは、指定されたパケットの HTTP コンテンツの長さの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="38738-758">HTTP コンテンツがない場合、このルーチンは値 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="38738-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="38738-759">これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="38738-760">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-760">This service is deprecated.</span></span> <span data-ttu-id="38738-761">開発者は *nx_http_server_content_length_get_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-762">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-762">Input Parameters</span></span>

 - <span data-ttu-id="38738-763">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="38738-764">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-765">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-765">Return Values</span></span>

 - <span data-ttu-id="38738-766">**content length** エラーが発生した場合、値 0 が返されます</span><span class="sxs-lookup"><span data-stu-id="38738-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="38738-767">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-767">Allowed From</span></span>

<span data-ttu-id="38738-768">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-769">例</span><span class="sxs-lookup"><span data-stu-id="38738-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="38738-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="38738-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="38738-771">要求のコンテンツの長さを取得する (ゼロ値のコンテンツの長さがサポートされます)</span><span class="sxs-lookup"><span data-stu-id="38738-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-772">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="38738-773">説明</span><span class="sxs-lookup"><span data-stu-id="38738-773">Description</span></span>

<span data-ttu-id="38738-774">このサービスは、*nx_http_server_content_length_get* に似ており、指定されたパケットの HTTP コンテンツの長さの取得を試行します。</span><span class="sxs-lookup"><span data-stu-id="38738-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="38738-775">ただし、戻り値は正常完了状態を示し、実際の長さの値が入力ポインター ```content_length``` で返されます。</span><span class="sxs-lookup"><span data-stu-id="38738-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="38738-776">HTTP コンテンツがない、またはコンテンツの長さが 0 の場合でも、このルーチンは正常完了状態を返し、content_length 入力ポインターは有効な長さ (ゼロ) を指します。</span><span class="sxs-lookup"><span data-stu-id="38738-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="38738-777">これは、HTTP サーバーの作成時 (*nx_http_server_create*) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="38738-778">このサービスは *nx_http_server_content_length_get()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-779">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-779">Input Parameters</span></span>

 - <span data-ttu-id="38738-780">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="38738-781">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="38738-782">**content_length** Content Length フィールドから取得した値へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-783">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-783">Return Values</span></span>

 - <span data-ttu-id="38738-784">**NX_SUCCESS** (0x00) サーバー コンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="38738-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) HTTP ヘッダーの形式が正しくありません</span><span class="sxs-lookup"><span data-stu-id="38738-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="38738-786">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-787">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-787">Allowed From</span></span>

<span data-ttu-id="38738-788">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-789">例</span><span class="sxs-lookup"><span data-stu-id="38738-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="38738-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="38738-790">nx_http_server_create</span></span>

<span data-ttu-id="38738-791">HTTP サーバー インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="38738-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-792">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-792">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="38738-793">説明</span><span class="sxs-lookup"><span data-stu-id="38738-793">Description</span></span>

<span data-ttu-id="38738-794">このサービスは、専用の ThreadX スレッドのコンテキスト内で実行される HTTP サーバー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="38738-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="38738-795">オプションの *authentication_check* および request_notify アプリケーション コールバック ルーチンを使うと、アプリケーション ソフトウェアから HTTP サーバーの基本的な操作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="38738-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-796">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-796">Input Parameters</span></span>

 - <span data-ttu-id="38738-797">**http_server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="38738-798">**http_server_name** HTTP サーバーの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="38738-799">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="38738-800">**media_ptr** 以前に作成された FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="38738-801">**stack_ptr** HTTP サーバーのスレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="38738-802">**stack_size** HTTP サーバーのスレッド スタック サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="38738-803">**authentication_check** アプリケーションの認証確認ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="38738-804">指定した場合、このルーチンは HTTP クライアント要求ごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="38738-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="38738-805">このパラメーターが null 値の場合、認証は実行されません。</span><span class="sxs-lookup"><span data-stu-id="38738-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="38738-806">**request_notify** アプリケーションの要求通知ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="38738-807">指定した場合、このルーチンは要求の HTTP サーバー処理の前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="38738-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="38738-808">これにより、HTTP クライアント要求が完了する前に、リソース名をリダイレクトしたり、リソース内のフィールドを更新したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="38738-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-809">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-809">Return Values</span></span>

 - <span data-ttu-id="38738-810">**NX_SUCCESS** (0x00) HTTP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="38738-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="38738-811">NX_PTR_ERROR (0x07) HTTP サーバー、IP、メディア、スタック、またはパケット プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="38738-812">NX_HTTP_POOL_ERROR (0xE9) プールのパケット ペイロードが HTTP 要求全体を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="38738-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-813">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-813">Allowed From</span></span>

<span data-ttu-id="38738-814">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="38738-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-815">例</span><span class="sxs-lookup"><span data-stu-id="38738-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="38738-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="38738-816">nx_http_server_delete</span></span>

<span data-ttu-id="38738-817">HTTP サーバー インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="38738-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-818">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-819">説明</span><span class="sxs-lookup"><span data-stu-id="38738-819">Description</span></span>

<span data-ttu-id="38738-820">このサービスは、以前に作成された HTTP サーバー インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="38738-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-821">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-821">Input Parameters</span></span>

 - <span data-ttu-id="38738-822">**http_server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-823">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-823">Return Values</span></span>

 - <span data-ttu-id="38738-824">**NX_SUCCESS** (0x00) HTTP サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="38738-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="38738-825">NX_PTR_ERROR (0x07) HTTP サーバー ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="38738-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="38738-826">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-827">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-827">Allowed From</span></span>

<span data-ttu-id="38738-828">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-829">例</span><span class="sxs-lookup"><span data-stu-id="38738-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="38738-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="38738-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="38738-831">エンティティ データの場所と長さを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-832">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="38738-833">説明</span><span class="sxs-lookup"><span data-stu-id="38738-833">Description</span></span>

<span data-ttu-id="38738-834">このサービスは、受信したクライアント メッセージの現在のマルチパート エンティティ内にあるデータの開始位置と、境界文字列を除いたデータの長さを特定します。</span><span class="sxs-lookup"><span data-stu-id="38738-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="38738-835">複数のエンティティを含むメッセージの同じクライアント データグラムに対してこの関数を再度呼び出すことができるように、HTTP サーバー自体のオフセットが内部的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="38738-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="38738-836">パケット ポインターは、クライアント メッセージがマルチパケット データグラムである次のパケットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="38738-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-837">このサービスを使用するには NX_HTTP_MULTIPART_ENABLE を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="38738-838">詳細については、[*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38738-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-839">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-839">Input Parameters</span></span>

 - <span data-ttu-id="38738-840">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="38738-841">**packet_pptr** パケット ポインターの位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="38738-842">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="38738-843">**available_offset** パケットの先頭追加ポインターからのエンティティ データのオフセットへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="38738-844">**available_length** エンティティ データの長さへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-845">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-845">Return Values</span></span>

 - <span data-ttu-id="38738-846">**NX_SUCCESS** (0x00) エンティティ コンテンツのサイズと場所が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="38738-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) HTTP サーバーの内部マルチパート マーカーのコンテンツが既に存在します</span><span class="sxs-lookup"><span data-stu-id="38738-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="38738-848">NX_HTTP_ERROR (0xE0) 内部 HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="38738-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="38738-849">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-850">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-850">Allowed From</span></span>

<span data-ttu-id="38738-851">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-852">例</span><span class="sxs-lookup"><span data-stu-id="38738-852">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="38738-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="38738-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="38738-854">エンティティ ヘッダーのコンテンツを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-855">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="38738-856">説明</span><span class="sxs-lookup"><span data-stu-id="38738-856">Description</span></span>

<span data-ttu-id="38738-857">このサービスは、エンティティ ヘッダーを取得して、指定されたバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="38738-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="38738-858">複数のエンティティ ヘッダーを含むクライアント データグラム内の次のマルチパート エンティティを見つけるために、HTTP サーバー自体のポインターが内部的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="38738-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="38738-859">パケット ポインターは、クライアント メッセージがマルチパケット データグラムである次のパケットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="38738-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-860">このサービスを使用するには NX_HTTP_MULTIPART_ENABLE を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-861">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-861">Input Parameters</span></span>

 - <span data-ttu-id="38738-862">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="38738-863">**packet_pptr** パケット ポインターの位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="38738-864">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="38738-865">**entity_header_buffer** エンティティ ヘッダーを格納する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="38738-866">**buffer_size** 入力バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="38738-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-867">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-867">Return Values</span></span>

 - <span data-ttu-id="38738-868">**NX_SUCCESS** (0x00) エンティティ ヘッダーが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="38738-869">**NX_HTTP_NOT_FOUND** **(0xE6)** エンティティ ヘッダー フィールドが見つかりません</span><span class="sxs-lookup"><span data-stu-id="38738-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="38738-870">**NX_HTTP_TIMEOUT** **(0xE1)** マルチパケット クライアント メッセージの次のパケットの受信期限が切れました</span><span class="sxs-lookup"><span data-stu-id="38738-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="38738-871">NX_HTTP_ERROR (0xE0) 内部 HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="38738-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="38738-872">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-873">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-874">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-874">Allowed From</span></span>

<span data-ttu-id="38738-875">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-876">例</span><span class="sxs-lookup"><span data-stu-id="38738-876">Example</span></span>

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

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
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
  NX_SUCCESS)
 {
                nx_packet_release(response_pkt);
     }
    }


}
else
{
    /* Indicate we have not processed the response to client yet.*/
    return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="38738-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="38738-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="38738-878">GMT の日付と時刻を取得するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="38738-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-879">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="38738-880">説明</span><span class="sxs-lookup"><span data-stu-id="38738-880">Description</span></span>

<span data-ttu-id="38738-881">このサービスは、以前に作成された HTTP サーバーを使用して GMT の日付と時刻を取得するコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="38738-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="38738-882">このサービスは、HTTP サーバーがクライアントに対する HTTP サーバー応答のヘッダーを作成しているときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="38738-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-883">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-883">Input Parameters</span></span>

 - <span data-ttu-id="38738-884">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="38738-885">**gmt_getv** GMT コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="38738-886">**datev** 取得した日付へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-887">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-887">Return Values</span></span>

 - <span data-ttu-id="38738-888">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="38738-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="38738-889">NX_PTR_ERROR (0x07) パケットまたはパラメーター ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="38738-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-890">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-890">Allowed From</span></span>

<span data-ttu-id="38738-891">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-892">例</span><span class="sxs-lookup"><span data-stu-id="38738-892">Example</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="38738-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="38738-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="38738-894">無効なユーザーとパスワードを処理するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="38738-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-895">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="38738-896">説明</span><span class="sxs-lookup"><span data-stu-id="38738-896">Description</span></span>

<span data-ttu-id="38738-897">このサービスは、ダイジェストまたは基本認証のいずれかによって、クライアントの GET、PUT、または DELETE 要求で無効なユーザー名とパスワードを受信したときに呼び出されるコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="38738-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="38738-898">HTTP サーバーを先に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-899">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-899">Input Parameters</span></span>

 - <span data-ttu-id="38738-900">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="38738-901">**invalid_username_password_callback** 無効なユーザーまたはパス コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="38738-902">**resource** クライアントによって指定されたリソースへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="38738-903">**client_address** クライアントのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="38738-904">IPv4 または IPv6 を指定できます</span><span class="sxs-lookup"><span data-stu-id="38738-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="38738-905">**request_type** クライアント要求の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="38738-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="38738-906">次を指定できます。</span><span class="sxs-lookup"><span data-stu-id="38738-906">May be:</span></span>
    - <span data-ttu-id="38738-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="38738-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="38738-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="38738-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="38738-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="38738-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="38738-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="38738-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="38738-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="38738-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-912">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-912">Return Values</span></span>

 - <span data-ttu-id="38738-913">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="38738-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="38738-914">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-915">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-915">Allowed From</span></span>

<span data-ttu-id="38738-916">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-917">例</span><span class="sxs-lookup"><span data-stu-id="38738-917">Example</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="38738-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="38738-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="38738-919">HTML 用の追加の MIME マップを設定する</span><span class="sxs-lookup"><span data-stu-id="38738-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-920">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="38738-921">説明</span><span class="sxs-lookup"><span data-stu-id="38738-921">Description</span></span>

<span data-ttu-id="38738-922">このサービスを使用すると、HTTP アプリケーション開発者は、NetX Duo HTTP サーバーによって提供される既定の MIME の種類から MIME の種類をさらに追加できます (定義済みの種類の一覧については、*nx_http_server_get_type* を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="38738-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="38738-923">GET 要求などのクライアント要求を受信すると、HTTP サーバーは、追加の MIME マップ セットを優先的に使用して HTTP ヘッダーから要求されたファイルの種類を解析します。一致するものが見つからない場合は、HTTP サーバーの既定の MIME マップの中で一致するものを検索します。</span><span class="sxs-lookup"><span data-stu-id="38738-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="38738-924">一致するものが見つからない場合、MIME の種類は既定で "text/plain" になります。</span><span class="sxs-lookup"><span data-stu-id="38738-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="38738-925">要求通知関数が HTTP サーバーに登録されている場合、要求通知コールバックから *nx_http_server_type_retrieve()* を呼び出して、ファイルの種類を解析できます。</span><span class="sxs-lookup"><span data-stu-id="38738-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-926">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-926">Input Parameters</span></span>

 - <span data-ttu-id="38738-927">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="38738-928">**mime_maps** MIME マップ配列へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="38738-929">**mime_map_num** 配列内の MIME マップの数</span><span class="sxs-lookup"><span data-stu-id="38738-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-930">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-930">Return Values</span></span>

 - <span data-ttu-id="38738-931">**NX_SUCCESS** (0x00) HTTP サーバーの MIME マップが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="38738-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="38738-932">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-933">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-933">Allowed From</span></span>

<span data-ttu-id="38738-934">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="38738-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-935">例</span><span class="sxs-lookup"><span data-stu-id="38738-935">Example</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="38738-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="38738-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="38738-937">コンテンツの長さを抽出し、データの先頭にポインターを設定する</span><span class="sxs-lookup"><span data-stu-id="38738-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-938">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="38738-939">説明</span><span class="sxs-lookup"><span data-stu-id="38738-939">Description</span></span>

<span data-ttu-id="38738-940">このサービスは、HTTP ヘッダーからコンテンツの長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="38738-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="38738-941">また、指定されたパケットを次のように更新します。パケットの先頭追加ポインター (書き込み先のパケット バッファーの開始位置) が、HTTP ヘッダーのすぐ先にある HTTP コンテンツ (データ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="38738-942">コンテンツの先頭が現在のパケット内に見つからない場合、この関数では、NX_HTTP_SERVER_TIMEOUT_RECEIVE 待機オプションを使用して、次のパケットを受信するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="38738-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="38738-943">これは、先頭追加ポインターをエンティティ ヘッダーの先に変更するため、*nx_http_server_get_entity_header* を呼び出す前に呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="38738-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-944">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-944">Input Parameters</span></span>

 - <span data-ttu-id="38738-945">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="38738-946">**packet_ptr** 先頭追加ポインターが更新されたパケットを返すためのパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="38738-947">**content_length** 抽出された ```content_length``` へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-948">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-948">Return Values</span></span>

 - <span data-ttu-id="38738-949">**NX_SUCCESS** (0x00) HTTP コンテンツの長さが見つかり、パケットが正常に更新されました</span><span class="sxs-lookup"><span data-stu-id="38738-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="38738-950">**NX_HTTP_TIMEOUT** (0xE1) 次のパケットを待っている間に時間切れになりました</span><span class="sxs-lookup"><span data-stu-id="38738-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="38738-951">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-952">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-952">Allowed From</span></span>

<span data-ttu-id="38738-953">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-954">例</span><span class="sxs-lookup"><span data-stu-id="38738-954">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="38738-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="38738-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="38738-956">次の HTTP パケットを受信する</span><span class="sxs-lookup"><span data-stu-id="38738-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-957">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-958">説明</span><span class="sxs-lookup"><span data-stu-id="38738-958">Description</span></span>

<span data-ttu-id="38738-959">このサービスは、HTTP サーバー ソケットで受信した次のパケットを返します。</span><span class="sxs-lookup"><span data-stu-id="38738-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="38738-960">パケットを受信する際の待機オプションは NX_HTTP_SERVER_TIMEOUT_RECEIVE です。</span><span class="sxs-lookup"><span data-stu-id="38738-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-961">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-961">Input Parameters</span></span>

 - <span data-ttu-id="38738-962">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="38738-963">**packet_ptr** 受信したパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-964">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-964">Return Values</span></span>

 - <span data-ttu-id="38738-965">**NX_SUCCESS** (0x00) 次のパケットを正常に受信しました</span><span class="sxs-lookup"><span data-stu-id="38738-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="38738-966">**NX_HTTP_TIMEOUT** (0xE1) 次のパケットを待っている間に時間切れになりました</span><span class="sxs-lookup"><span data-stu-id="38738-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="38738-967">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-968">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-968">Allowed From</span></span>

<span data-ttu-id="38738-969">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-970">例</span><span class="sxs-lookup"><span data-stu-id="38738-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="38738-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="38738-971">nx_http_server_param_get</span></span>

<span data-ttu-id="38738-972">要求からパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-973">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="38738-974">説明</span><span class="sxs-lookup"><span data-stu-id="38738-974">Description</span></span>

<span data-ttu-id="38738-975">このサービスは、指定された要求パケット内の指定された HTTP URL パラメーターの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="38738-976">要求された HTTP パラメーターが存在しない場合、このルーチンでは NX_HTTP_NOT_FOUND という状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="38738-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="38738-977">このルーチンは、HTTP サーバーの作成時 (*nx_http_server_create*) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-978">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-978">Input Parameters</span></span>

 - <span data-ttu-id="38738-979">**packet_ptr** HTTP クライアントの要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="38738-980">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="38738-981">**param_number** パラメーター リストの左から右に向かって 0 から始まるパラメーターの論理番号。</span><span class="sxs-lookup"><span data-stu-id="38738-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="38738-982">**param_ptr** パラメーターのコピー先領域。</span><span class="sxs-lookup"><span data-stu-id="38738-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="38738-983">**max_param_size** パラメーターのコピー先領域の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="38738-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-984">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-984">Return Values</span></span>

 - <span data-ttu-id="38738-985">**NX_SUCCESS** (0x00) HTTP サーバーのパラメーターが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="38738-986">**NX_HTTP_NOT_FOUND** (0xE6) 指定されたパラメーターが見つかりません</span><span class="sxs-lookup"><span data-stu-id="38738-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="38738-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) 要求パラメーターが正しく終了していません</span><span class="sxs-lookup"><span data-stu-id="38738-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="38738-988">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-989">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-990">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-990">Allowed From</span></span>

<span data-ttu-id="38738-991">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-992">例</span><span class="sxs-lookup"><span data-stu-id="38738-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="38738-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="38738-993">nx_http_server_query_get</span></span>

<span data-ttu-id="38738-994">要求からクエリを取得する</span><span class="sxs-lookup"><span data-stu-id="38738-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-995">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="38738-996">説明</span><span class="sxs-lookup"><span data-stu-id="38738-996">Description</span></span>

<span data-ttu-id="38738-997">このサービスは、指定された要求パケット内の指定された HTTP URL クエリの取得を試みます。</span><span class="sxs-lookup"><span data-stu-id="38738-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="38738-998">要求された HTTP クエリが存在しない場合、このルーチンでは NX_HTTP_NOT_FOUND という状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="38738-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="38738-999">このルーチンは、HTTP サーバーの作成時 (*nx_http_server_create*) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1000">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1000">Input Parameters</span></span>

 - <span data-ttu-id="38738-1001">**packet_ptr** HTTP クライアントの要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="38738-1002">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="38738-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="38738-1003">**query_number** クエリ リストの左から右に向かって 0 から始まるクエリの論理番号。</span><span class="sxs-lookup"><span data-stu-id="38738-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="38738-1004">**query_ptr** クエリのコピー先領域。</span><span class="sxs-lookup"><span data-stu-id="38738-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="38738-1005">**max_query_size** クエリのコピー先領域の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="38738-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1006">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1006">Return Values</span></span>

 - <span data-ttu-id="38738-1007">**NX_SUCCESS** (0x00) HTTP サーバーのクエリが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="38738-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="38738-1008">**NX_HTTP_FAILED** (0xE2) クエリのサイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="38738-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="38738-1009">**NX_HTTP_NOT_FOUND** (0xE6) 指定されたクエリが見つかりません</span><span class="sxs-lookup"><span data-stu-id="38738-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="38738-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) クライアント要求内にクエリがありません</span><span class="sxs-lookup"><span data-stu-id="38738-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="38738-1011">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-1012">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1013">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1013">Allowed From</span></span>

<span data-ttu-id="38738-1014">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-1015">例</span><span class="sxs-lookup"><span data-stu-id="38738-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="38738-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="38738-1016">nx_http_server_start</span></span>

<span data-ttu-id="38738-1017">HTTP サーバーを起動する</span><span class="sxs-lookup"><span data-stu-id="38738-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-1018">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-1019">説明</span><span class="sxs-lookup"><span data-stu-id="38738-1019">Description</span></span>

<span data-ttu-id="38738-1020">このサービスは、以前に作成された HTTP サーバー インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="38738-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1021">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1021">Input Parameters</span></span>

 - <span data-ttu-id="38738-1022">**http_server_ptr** HTTP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1023">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1023">Return Values</span></span>

 - <span data-ttu-id="38738-1024">**NX_SUCCESS** (0x00) サーバーが正常に起動しました</span><span class="sxs-lookup"><span data-stu-id="38738-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="38738-1025">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1026">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1026">Allowed From</span></span>

<span data-ttu-id="38738-1027">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="38738-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-1028">例</span><span class="sxs-lookup"><span data-stu-id="38738-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="38738-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="38738-1029">nx_http_server_stop</span></span>

<span data-ttu-id="38738-1030">HTTP サーバーを停止する</span><span class="sxs-lookup"><span data-stu-id="38738-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-1031">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="38738-1032">説明</span><span class="sxs-lookup"><span data-stu-id="38738-1032">Description</span></span>

<span data-ttu-id="38738-1033">このサービスは、以前に作成された HTTP サーバー インスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="38738-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="38738-1034">このルーチンは、HTTP サーバー インスタンスを削除する前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38738-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1035">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1035">Input Parameters</span></span>

 - <span data-ttu-id="38738-1036">**http_server_ptr** HTTP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="38738-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1037">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1037">Return Values</span></span>

 - <span data-ttu-id="38738-1038">**NX_SUCCESS** (0x00) サーバーが正常に停止しました</span><span class="sxs-lookup"><span data-stu-id="38738-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="38738-1039">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-1040">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1041">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1041">Allowed From</span></span>

<span data-ttu-id="38738-1042">Threads</span><span class="sxs-lookup"><span data-stu-id="38738-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38738-1043">例</span><span class="sxs-lookup"><span data-stu-id="38738-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="38738-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="38738-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="38738-1045">クライアントの HTTP 要求からファイルの種類を抽出する</span><span class="sxs-lookup"><span data-stu-id="38738-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-1046">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="38738-1047">説明</span><span class="sxs-lookup"><span data-stu-id="38738-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="38738-1048">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-1048">This service is deprecated.</span></span> <span data-ttu-id="38738-1049">ユーザーは *nx_http_server_type_retrieve()* サービスを使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="38738-1050">このサービスは、http_type_string バッファー内の HTTP 要求の種類と、入力バッファー name からの戻り値 (通常は URL) 内のその長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="38738-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="38738-1051">MIME マップが見つからない場合、既定で "text/plain" という種類に設定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="38738-1052">それ以外の場合、抽出された種類を HTTP サーバーの既定の MIME マップと比較して、一致するものを探します。</span><span class="sxs-lookup"><span data-stu-id="38738-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="38738-1053">NetX Duo HTTP サーバーの既定の MIME マップは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="38738-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="38738-1054">**html** text/html</span><span class="sxs-lookup"><span data-stu-id="38738-1054">**html** text/html</span></span>
 - <span data-ttu-id="38738-1055">**htm** text/html</span><span class="sxs-lookup"><span data-stu-id="38738-1055">**htm** text/html</span></span>
 - <span data-ttu-id="38738-1056">**txt** text/plain</span><span class="sxs-lookup"><span data-stu-id="38738-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="38738-1057">**gif** image/gif</span><span class="sxs-lookup"><span data-stu-id="38738-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="38738-1058">**jpg** image/jpeg</span><span class="sxs-lookup"><span data-stu-id="38738-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="38738-1059">**ico** image/x-icon</span><span class="sxs-lookup"><span data-stu-id="38738-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="38738-1060">指定した場合は、追加の MIME マップのユーザー定義セットも検索されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="38738-1061">ユーザー定義マップの詳細については、*nx_http_server_mime_maps_addtional_set()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38738-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="38738-1062">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="38738-1062">This service is deprecated.</span></span> <span data-ttu-id="38738-1063">開発者は *nx_http_server_type_get_extended()* に移行することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1064">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1064">Input Parameters</span></span>

 - <span data-ttu-id="38738-1065">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="38738-1066">**name** 検索するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="38738-1067">**http_type_string** (抽出された HTML の種類へのポインター)</span><span class="sxs-lookup"><span data-stu-id="38738-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1068">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1068">Return Values</span></span>

 - <span data-ttu-id="38738-1069">**文字列の長さ (バイト単位)** 0 以外の値は成功です。</span><span class="sxs-lookup"><span data-stu-id="38738-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="38738-1070">0 はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="38738-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1071">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1071">Allowed From</span></span>

<span data-ttu-id="38738-1072">Application</span><span class="sxs-lookup"><span data-stu-id="38738-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="38738-1073">例</span><span class="sxs-lookup"><span data-stu-id="38738-1073">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="38738-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="38738-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="38738-1075">クライアントの HTTP 要求からファイルの種類を抽出する</span><span class="sxs-lookup"><span data-stu-id="38738-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-1076">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="38738-1077">説明</span><span class="sxs-lookup"><span data-stu-id="38738-1077">Description</span></span>

<span data-ttu-id="38738-1078">このサービスは、*http_type_string* バッファー内の HTTP 要求の種類と、入力バッファー *name* からの戻り値 (通常は URL) 内のその長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="38738-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="38738-1079">MIME マップが見つからない場合、既定で "text/plain" という種類に設定されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="38738-1080">それ以外の場合、抽出された種類を HTTP サーバーの既定の MIME マップと比較して、一致するものを探します。</span><span class="sxs-lookup"><span data-stu-id="38738-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="38738-1081">NetX Duo HTTP サーバーの既定の MIME マップは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="38738-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="38738-1082">**html** text/html</span><span class="sxs-lookup"><span data-stu-id="38738-1082">**html** text/html</span></span>
 - <span data-ttu-id="38738-1083">**htm** text/html</span><span class="sxs-lookup"><span data-stu-id="38738-1083">**htm** text/html</span></span>
 - <span data-ttu-id="38738-1084">**txt** text/plain</span><span class="sxs-lookup"><span data-stu-id="38738-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="38738-1085">**gif** image/gif</span><span class="sxs-lookup"><span data-stu-id="38738-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="38738-1086">**jpg** image/jpeg</span><span class="sxs-lookup"><span data-stu-id="38738-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="38738-1087">**ico** image/x-icon</span><span class="sxs-lookup"><span data-stu-id="38738-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="38738-1088">指定した場合は、追加の MIME マップのユーザー定義セットも検索されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="38738-1089">ユーザー定義マップの詳細については、*nx_http_server_mime_maps_addtional_set()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38738-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="38738-1090">このサービスは *nx_http_server_type_get()* を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="38738-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="38738-1091">このバージョンでは、追加の長さの情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="38738-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1092">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1092">Input Parameters</span></span>

 - <span data-ttu-id="38738-1093">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="38738-1094">**name** 検索するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="38738-1095">**name_length** 検索するバッファーの長さ</span><span class="sxs-lookup"><span data-stu-id="38738-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="38738-1096">**http_type_string** (抽出された HTML の種類へのポインター)</span><span class="sxs-lookup"><span data-stu-id="38738-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="38738-1097">**http_type_string_max_size** http_type_string バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="38738-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1098">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1098">Return Values</span></span>

 - <span data-ttu-id="38738-1099">**文字列の長さ (バイト単位)** 0 以外の値は成功です。</span><span class="sxs-lookup"><span data-stu-id="38738-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="38738-1100">0 はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="38738-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1101">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1101">Allowed From</span></span>

<span data-ttu-id="38738-1102">Application</span><span class="sxs-lookup"><span data-stu-id="38738-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="38738-1103">例</span><span class="sxs-lookup"><span data-stu-id="38738-1103">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

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
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="38738-1104">詳細な例については、[*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header) の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38738-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="38738-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="38738-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="38738-1106">ダイジェスト認証コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="38738-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-1107">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-1107">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="38738-1108">説明</span><span class="sxs-lookup"><span data-stu-id="38738-1108">Description</span></span>

<span data-ttu-id="38738-1109">このサービスは、ダイジェスト認証の実行時に呼び出されるコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="38738-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1110">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1110">Input Parameters</span></span>

 - <span data-ttu-id="38738-1111">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="38738-1112">**digest_authenticate_callback** ダイジェスト認証コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1113">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1113">Return Values</span></span>

 - <span data-ttu-id="38738-1114">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="38738-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="38738-1115">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="38738-1116">NX_NOT_SUPPORTED (0x4B) ダイジェスト認証が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="38738-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1117">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1117">Allowed From</span></span>

<span data-ttu-id="38738-1118">Application</span><span class="sxs-lookup"><span data-stu-id="38738-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="38738-1119">例</span><span class="sxs-lookup"><span data-stu-id="38738-1119">Example</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="38738-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="38738-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="38738-1121">認証確認コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="38738-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="38738-1122">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="38738-1122">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="38738-1123">説明</span><span class="sxs-lookup"><span data-stu-id="38738-1123">Description</span></span>

<span data-ttu-id="38738-1124">このサービスは、認証確認のコールバック関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="38738-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="38738-1125">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="38738-1125">Input Parameters</span></span>

 - <span data-ttu-id="38738-1126">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="38738-1127">**authentication_check_extended** アプリケーションの認証確認へのポインター</span><span class="sxs-lookup"><span data-stu-id="38738-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="38738-1128">戻り値</span><span class="sxs-lookup"><span data-stu-id="38738-1128">Return Values</span></span>

 - <span data-ttu-id="38738-1129">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="38738-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="38738-1130">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="38738-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38738-1131">許可元</span><span class="sxs-lookup"><span data-stu-id="38738-1131">Allowed From</span></span>

<span data-ttu-id="38738-1132">Application</span><span class="sxs-lookup"><span data-stu-id="38738-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="38738-1133">例</span><span class="sxs-lookup"><span data-stu-id="38738-1133">Example</span></span>

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
