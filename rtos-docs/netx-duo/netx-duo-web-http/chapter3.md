---
title: 章 3 章 - HTTP サービスの説明
description: この章では、すべての NetX Web HTTP サービス (以下に記載) をアルファベット順で説明します。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bb2743f05c5b56331d1c0e948601ad23bf340d1
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875274"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="58df1-103">章 3 章 - HTTP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="58df1-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="58df1-104">この章では、すべての NetX Web HTTP サービス (以下に記載) をアルファベット順で説明します。</span><span class="sxs-lookup"><span data-stu-id="58df1-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-105">次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="58df1-106">HTTP および HTTPS Client の API</span><span class="sxs-lookup"><span data-stu-id="58df1-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="58df1-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="58df1-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="58df1-108">カスタム要求のために HTTP Server へのプレーンテキスト ソケットを開く</span><span class="sxs-lookup"><span data-stu-id="58df1-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-109">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-110">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-110">Description</span></span>

<span data-ttu-id="58df1-111">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-112">このサービスでは、HTTP Server に対してプレーンテキストの TCP ソケットが開かれますが、要求は送信されません。</span><span class="sxs-lookup"><span data-stu-id="58df1-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="58df1-113">要求は、*nx_web_http_client_request_initialize()* を使用して作成され、*nx_web_http_client_request_send()* を使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="58df1-114">カスタム HTTP ヘッダーを要求に追加するには、*nx_web_http_client_request_header_add()* を使用します。</span><span class="sxs-lookup"><span data-stu-id="58df1-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="58df1-115">このサービスを使用すると、アプリケーションで任意の数のカスタム ヘッダーを要求に追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="58df1-116">**これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。**</span><span class="sxs-lookup"><span data-stu-id="58df1-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-117">nx_web_http_client_*_start メソッドは、利便性のために用意されており (*nx_web_http_client_get_start\*() など)、要求の生成とソケットの接続が処理されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="58df1-118">要求にカスタム HTTP ヘッダーが不要な場合は、*nx_web_http_client_connect()* や関連するルーチンの代わりに、これらのサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-119">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-119">Input Parameters</span></span>

- <span data-ttu-id="58df1-120">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-121">**server_ip** リモート HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="58df1-122">**server_port** リモート HTTP Server のポート (HTTP の場合は 80 など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="58df1-123">**wait_option** 基になるネットワーク操作をサービスで待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="58df1-124">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-125">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-127">Return Values</span></span>

- <span data-ttu-id="58df1-128">**NX_SUCCESS** (0x00) TCP ソケットが正常に接続されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="58df1-129">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-130">NX_WEB_HTTP_NOT_READY (0x3000A) 別の要求が既に進行中です。</span><span class="sxs-lookup"><span data-stu-id="58df1-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-131">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-131">Allowed From</span></span>

<span data-ttu-id="58df1-132">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-133">例</span><span class="sxs-lookup"><span data-stu-id="58df1-133">Example</span></span>

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="58df1-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="58df1-134">nx_web_http_client_create</span></span>

<span data-ttu-id="58df1-135">HTTP Client インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="58df1-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-136">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="58df1-137">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-137">Description</span></span>

<span data-ttu-id="58df1-138">このサービスでは、指定された IP インスタンスに HTTP Client インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="58df1-139">このクライアント インスタンスは、HTTP または HTTPS のいずれかに使用できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="58df1-140">HTTP または HTTPS インスタンスの開始の詳細については、サービス *nx_web_http_client_connect()* および *nx_web_http_client_secure_connect()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="58df1-141">また、GET、PUT、POST メソッドの単純な呼び出しについては、*nx_web_http_client_get_\*\*、*nx_web_http_client_put_**、\*nx_web_http_client_post_** の API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-142">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-142">Input Parameters</span></span>

- <span data-ttu-id="58df1-143">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-144">**client_name** HTTP クライアント インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="58df1-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="58df1-145">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="58df1-146">**pool_ptr** 既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="58df1-147">このプール内のパケットはペイロードが応答ヘッダー全体を処理するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="58df1-148">これは *nx_web_http_client.h* の *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="58df1-149">**window_size** クライアントの TCP ソケット受信ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="58df1-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-150">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-150">Return Values</span></span>

- <span data-ttu-id="58df1-151">**NX_SUCCESS** (0x00) HTTP クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="58df1-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="58df1-152">NX_PTR_ERROR (0x16) HTTP、ip_ptr、またはパケット プール ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="58df1-153">NX_WEB_HTTP_POOL_ERROR (0x30009) パケット プールのペイロードのサイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-154">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-154">Allowed From</span></span>

<span data-ttu-id="58df1-155">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="58df1-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-156">例</span><span class="sxs-lookup"><span data-stu-id="58df1-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="58df1-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="58df1-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="58df1-158">HTTP Client インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="58df1-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-159">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-160">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-160">Description</span></span>

<span data-ttu-id="58df1-161">このサービスは、以前に作成された HTTP クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="58df1-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-162">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-162">Input Parameters</span></span>

- <span data-ttu-id="58df1-163">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-164">Return Values</span></span>

- <span data-ttu-id="58df1-165">**NX_SUCCESS** (0x00) HTTP クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="58df1-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="58df1-166">NX_PTR_ERROR (0x16) HTTP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="58df1-167">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-168">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-168">Allowed From</span></span>

<span data-ttu-id="58df1-169">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-170">例</span><span class="sxs-lookup"><span data-stu-id="58df1-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="58df1-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="58df1-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="58df1-172">プレーンテキストの HTTP DELETE 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-174">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-174">Description</span></span>

<span data-ttu-id="58df1-175">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-176">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-177">このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="58df1-178">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-179">この API は非推奨です。</span><span class="sxs-lookup"><span data-stu-id="58df1-179">This API is deprecated.</span></span> <span data-ttu-id="58df1-180">開発者には、*nx_web_http_client_delete_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-181">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-181">Input Parameters</span></span>

- <span data-ttu-id="58df1-182">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-183">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-184">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-185">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-186">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-187">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-188">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-189">**username** 認証用の省略可能なユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-190">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-191">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-192">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-193">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-195">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-195">Return Values</span></span>

- <span data-ttu-id="58df1-196">**NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="58df1-197">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-201">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-202">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-203">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-203">Allowed From</span></span>

<span data-ttu-id="58df1-204">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-205">例</span><span class="sxs-lookup"><span data-stu-id="58df1-205">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="58df1-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="58df1-207">プレーンテキストの HTTP DELETE 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-208">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-209">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-209">Description</span></span>

<span data-ttu-id="58df1-210">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-211">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-212">このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="58df1-213">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-214">resource、host、username、password の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-215">このサービスによって *nx_web_http_client_delete_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="58df1-216">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-217">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-217">Input Parameters</span></span>

- <span data-ttu-id="58df1-218">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-219">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-220">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-221">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-222">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-223">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-224">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-225">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-226">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-227">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-228">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-229">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-230">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-231">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-232">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-233">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-235">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-235">Return Values</span></span>

- <span data-ttu-id="58df1-236">**NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="58df1-237">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-241">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-242">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-243">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-243">Allowed From</span></span>

<span data-ttu-id="58df1-244">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-245">例</span><span class="sxs-lookup"><span data-stu-id="58df1-245">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="58df1-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="58df1-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="58df1-247">暗号化された HTTPS DELETE 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-248">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-249">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-249">Description</span></span>

<span data-ttu-id="58df1-250">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-251">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-252">このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="58df1-253">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-254">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-254">This service is deprecated.</span></span> <span data-ttu-id="58df1-255">開発者には、*nx_web_http_client_delete_secure_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-256">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-256">Input Parameters</span></span>

- <span data-ttu-id="58df1-257">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-258">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-259">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-260">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="58df1-261">リソースは NULL 終端である必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="58df1-262">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-263">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-264">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-265">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-266">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-267">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-268">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-269">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-270">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-271">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-273">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-273">Return Values</span></span>

- <span data-ttu-id="58df1-274">**NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="58df1-275">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-279">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-280">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-281">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-281">Allowed From</span></span>

<span data-ttu-id="58df1-282">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-283">例</span><span class="sxs-lookup"><span data-stu-id="58df1-283">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="58df1-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="58df1-285">暗号化された HTTPS DELETE 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-286">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-286">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-287">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-287">Description</span></span>

<span data-ttu-id="58df1-288">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-289">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-290">このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="58df1-291">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-292">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-293">このサービスによって *nx_web_http_client_delete_secure_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="58df1-294">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-295">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-295">Input Parameters</span></span>

- <span data-ttu-id="58df1-296">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-297">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-298">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-299">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="58df1-300">リソースは NULL 終端である必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="58df1-301">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-302">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-303">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-304">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-305">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-306">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-307">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-308">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-309">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-310">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-311">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-312">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-313">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-314">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-316">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-316">Return Values</span></span>

- <span data-ttu-id="58df1-317">**NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="58df1-318">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-322">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-323">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="58df1-324">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-324">Allowed From</span></span>

<span data-ttu-id="58df1-325">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-326">例</span><span class="sxs-lookup"><span data-stu-id="58df1-326">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="58df1-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="58df1-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="58df1-328">プレーンテキストの HTTP GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-329">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-330">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-330">Description</span></span>

<span data-ttu-id="58df1-331">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-332">このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-333">このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="58df1-334">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-335">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-335">This service is deprecated.</span></span> <span data-ttu-id="58df1-336">開発者には、*nx_web_http_client_get_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-337">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-337">Input Parameters</span></span>

- <span data-ttu-id="58df1-338">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-339">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-340">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-341">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-342">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-343">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-344">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-345">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-346">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-347">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-348">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-349">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-351">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-351">Return Values</span></span>

- <span data-ttu-id="58df1-352">**NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="58df1-353">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-357">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-358">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-359">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-359">Allowed From</span></span>

<span data-ttu-id="58df1-360">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-361">例</span><span class="sxs-lookup"><span data-stu-id="58df1-361">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="58df1-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="58df1-363">プレーンテキストの HTTP GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-364">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-365">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-365">Description</span></span>

<span data-ttu-id="58df1-366">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-367">このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-368">このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="58df1-369">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-370">resource、host、username、password の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-371">このサービスによって *nx_web_http_client_get_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="58df1-372">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-373">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-373">Input Parameters</span></span>

- <span data-ttu-id="58df1-374">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-375">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-376">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-377">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-378">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-379">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-380">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-381">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-382">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-383">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-384">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-385">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-386">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-387">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-388">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-389">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-391">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-391">Return Values</span></span>

- <span data-ttu-id="58df1-392">**NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="58df1-393">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-397">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-398">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-399">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-399">Allowed From</span></span>

<span data-ttu-id="58df1-400">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-401">例</span><span class="sxs-lookup"><span data-stu-id="58df1-401">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="58df1-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="58df1-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="58df1-403">暗号化された HTTPS GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-404">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-405">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-405">Description</span></span>

<span data-ttu-id="58df1-406">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-407">このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-408">このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="58df1-409">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-410">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-410">This service is deprecated.</span></span> <span data-ttu-id="58df1-411">開発者には、*nx_web_http_client_get_secure_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-412">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-412">Input Parameters</span></span>

- <span data-ttu-id="58df1-413">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-414">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-415">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-416">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-417">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-418">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-419">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-420">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-421">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-422">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-423">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-424">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-425">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-426">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-428">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-428">Return Values</span></span>

- <span data-ttu-id="58df1-429">**NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="58df1-430">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-434">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-435">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-436">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-436">Allowed From</span></span>

<span data-ttu-id="58df1-437">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-438">例</span><span class="sxs-lookup"><span data-stu-id="58df1-438">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="58df1-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="58df1-440">暗号化された HTTPS GET 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-441">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-441">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-442">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-442">Description</span></span>

<span data-ttu-id="58df1-443">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-444">このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-445">このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="58df1-446">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-447">resource、host、username、password の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-448">このサービスによって *nx_web_http_client_secure_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="58df1-449">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-450">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-450">Input Parameters</span></span>

- <span data-ttu-id="58df1-451">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-452">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-453">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-454">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-455">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-456">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-457">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-458">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-459">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-460">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-461">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-462">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-463">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-464">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-465">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-466">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-467">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-468">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-470">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-470">Return Values</span></span>

- <span data-ttu-id="58df1-471">**NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="58df1-472">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-476">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-477">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-478">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-478">Allowed From</span></span>

<span data-ttu-id="58df1-479">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-480">例</span><span class="sxs-lookup"><span data-stu-id="58df1-480">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="58df1-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="58df1-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="58df1-482">プレーンテキストの HTTP HEAD 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-483">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-484">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-484">Description</span></span>

<span data-ttu-id="58df1-485">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-486">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-487">このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、応答を取得できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="58df1-488">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-489">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-489">This service is deprecated.</span></span> <span data-ttu-id="58df1-490">開発者には、*nx_web_http_client_head_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-491">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-491">Input Parameters</span></span>

- <span data-ttu-id="58df1-492">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-493">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-494">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-495">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-496">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-497">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-498">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-499">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-500">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-501">**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-502">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-503">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-505">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-505">Return Values</span></span>

- <span data-ttu-id="58df1-506">**NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="58df1-507">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-511">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-512">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-513">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-513">Allowed From</span></span>

<span data-ttu-id="58df1-514">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-515">例</span><span class="sxs-lookup"><span data-stu-id="58df1-515">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="58df1-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="58df1-517">プレーンテキストの HTTP HEAD 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-518">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-519">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-519">Description</span></span>

<span data-ttu-id="58df1-520">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-521">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-522">このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、応答を取得できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="58df1-523">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-524">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-525">このサービスによって *nx_web_http_client_head_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="58df1-526">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-527">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-527">Input Parameters</span></span>

- <span data-ttu-id="58df1-528">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-529">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-530">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-531">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-532">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-533">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-534">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-535">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-536">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-537">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-538">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-539">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-540">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-541">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-542">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-543">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-545">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-545">Return Values</span></span>

- <span data-ttu-id="58df1-546">**NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="58df1-547">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-551">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-552">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-553">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-553">Allowed From</span></span>

<span data-ttu-id="58df1-554">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-555">例</span><span class="sxs-lookup"><span data-stu-id="58df1-555">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="58df1-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="58df1-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="58df1-557">暗号化された HTTPS HEAD 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-558">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-559">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-559">Description</span></span>

<span data-ttu-id="58df1-560">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-561">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-562">このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、要求されたリソース コンテンツに対応するサーバーの応答を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="58df1-563">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-564">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-564">This service is deprecated.</span></span> <span data-ttu-id="58df1-565">開発者には、*nx_web_http_client_head_secure_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-566">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-566">Input Parameters</span></span>

- <span data-ttu-id="58df1-567">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-568">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-569">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-570">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-571">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-572">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-573">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-574">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-575">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-576">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-577">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-578">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-579">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-580">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-582">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-582">Return Values</span></span>

- <span data-ttu-id="58df1-583">**NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="58df1-584">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-588">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-589">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-590">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-590">Allowed From</span></span>

<span data-ttu-id="58df1-591">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-592">例</span><span class="sxs-lookup"><span data-stu-id="58df1-592">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="58df1-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="58df1-594">暗号化された HTTPS HEAD 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-595">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-595">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-596">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-596">Description</span></span>

<span data-ttu-id="58df1-597">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-598">このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="58df1-599">このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、要求されたリソース コンテンツに対応するサーバーの応答を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="58df1-600">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="58df1-601">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-602">このサービスによって *nx_web_http_client_head_secure_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="58df1-603">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-604">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-604">Input Parameters</span></span>

- <span data-ttu-id="58df1-605">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-606">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-607">**server_port** リモート HTTP Server のポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-608">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-609">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-610">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-611">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-612">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-613">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-614">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-615">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-616">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-617">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-618">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-619">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-620">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-621">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-622">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-624">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-624">Return Values</span></span>

- <span data-ttu-id="58df1-625">**NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="58df1-626">**NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="58df1-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="58df1-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="58df1-630">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-631">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-632">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-632">Allowed From</span></span>

<span data-ttu-id="58df1-633">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-634">例</span><span class="sxs-lookup"><span data-stu-id="58df1-634">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="58df1-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="58df1-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="58df1-636">HTTP(S) パケットを割り当てる</span><span class="sxs-lookup"><span data-stu-id="58df1-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-637">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-638">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-638">Description</span></span>

<span data-ttu-id="58df1-639">このサービスでは、クライアントの HTTP(S) にパケットを割り当てることが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-640">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-640">Input Parameters</span></span>

- <span data-ttu-id="58df1-641">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-642">**packet_ptr** 割り当てられるパケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="58df1-643">**wait_option** パケット プールに使用可能なパケットがない場合の待機時間をティックで定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="58df1-644">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="58df1-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="58df1-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="58df1-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="58df1-647">**タイムアウト (ティック数)** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="58df1-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-648">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-648">Return Values</span></span>

- <span data-ttu-id="58df1-649">**NX_SUCCESS** (0x00) パケットが正常に割り当てられました</span><span class="sxs-lookup"><span data-stu-id="58df1-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="58df1-650">**NX_NO_PACKET** (0x01) 使用可能なパケットがありません</span><span class="sxs-lookup"><span data-stu-id="58df1-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="58df1-651">**NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="58df1-652">**NX_INVALID_PARAMETERS** (0x4D) プロトコルをサポートできないパケット サイズです。</span><span class="sxs-lookup"><span data-stu-id="58df1-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="58df1-653">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-654">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-655">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-655">Allowed From</span></span>

<span data-ttu-id="58df1-656">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-657">例</span><span class="sxs-lookup"><span data-stu-id="58df1-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="58df1-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="58df1-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="58df1-659">HTTP POST 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-660">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-661">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-661">Description</span></span>

<span data-ttu-id="58df1-662">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-663">このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する POST 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-664">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-665">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-666">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-666">This service is deprecated.</span></span> <span data-ttu-id="58df1-667">開発者には、*nx_web_http_client_post_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-668">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-668">Input Parameters</span></span>

- <span data-ttu-id="58df1-669">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-670">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-671">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-672">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="58df1-673">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-674">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-675">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-676">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-677">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-678">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-679">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-680">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-681">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-682">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-684">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-684">Return Values</span></span>

- <span data-ttu-id="58df1-685">**NX_SUCCESS** (0x00) POST 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="58df1-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-688">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-689">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-690">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-691">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-691">Allowed From</span></span>

<span data-ttu-id="58df1-692">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-693">例</span><span class="sxs-lookup"><span data-stu-id="58df1-693">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="58df1-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="58df1-695">HTTP POST 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-696">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-697">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-697">Description</span></span>

<span data-ttu-id="58df1-698">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-699">このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する POST 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-700">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-701">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-702">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-703">このサービスによって *nx_web_http_client_post_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="58df1-704">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-705">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-705">Input Parameters</span></span>

- <span data-ttu-id="58df1-706">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-707">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-708">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-709">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-710">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-711">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-712">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-713">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-714">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-715">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-716">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-717">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-718">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-719">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-720">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-721">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-722">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-723">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-725">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-725">Return Values</span></span>

- <span data-ttu-id="58df1-726">**NX_SUCCESS** (0x00) POST 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="58df1-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-729">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-730">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-731">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-732">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-732">Allowed From</span></span>

<span data-ttu-id="58df1-733">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-734">例</span><span class="sxs-lookup"><span data-stu-id="58df1-734">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="58df1-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="58df1-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="58df1-736">暗号化された HTTPS POST 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-737">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-737">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-738">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-738">Description</span></span>

<span data-ttu-id="58df1-739">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-740">このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する POST 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-741">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-742">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-743">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-743">This service is deprecated.</span></span> <span data-ttu-id="58df1-744">開発者には、*nx_web_http_client_post_secure_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-745">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-745">Input Parameters</span></span>

- <span data-ttu-id="58df1-746">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-747">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-748">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-749">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="58df1-750">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-751">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-752">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-753">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-754">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-755">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-756">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-757">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-758">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-759">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-760">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-761">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-763">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-763">Return Values</span></span>

- <span data-ttu-id="58df1-764">**NX_SUCCESS** (0x00) POST 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="58df1-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-767">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-768">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-769">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-770">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-770">Allowed From</span></span>

<span data-ttu-id="58df1-771">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-772">例</span><span class="sxs-lookup"><span data-stu-id="58df1-772">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="58df1-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="58df1-774">暗号化された HTTPS POST 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-775">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-775">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-776">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-776">Description</span></span>

<span data-ttu-id="58df1-777">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-778">このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する POST 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-779">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-780">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-781">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-782">このサービスによって *nx_web_http_client_post_secure_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="58df1-783">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-784">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-784">Input Parameters</span></span>

- <span data-ttu-id="58df1-785">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-786">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-787">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-788">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-789">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-790">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-791">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-792">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-793">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-794">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-795">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-796">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-797">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-798">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-799">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-800">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-801">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-802">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-803">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-804">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-806">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-806">Return Values</span></span>

- <span data-ttu-id="58df1-807">**NX_SUCCESS** (0x00) POST 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="58df1-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-810">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-811">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-812">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-813">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-813">Allowed From</span></span>

<span data-ttu-id="58df1-814">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-815">例</span><span class="sxs-lookup"><span data-stu-id="58df1-815">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="58df1-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="58df1-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="58df1-817">HTTP PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-818">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-819">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-819">Description</span></span>

<span data-ttu-id="58df1-820">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-821">このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する PUT 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-822">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-823">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-824">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-824">This service is deprecated.</span></span> <span data-ttu-id="58df1-825">開発者には、*nx_web_http_client_put_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-826">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-826">Input Parameters</span></span>

- <span data-ttu-id="58df1-827">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-828">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-829">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-830">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="58df1-831">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-832">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-833">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-834">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-835">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-836">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-837">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-838">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-839">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-840">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-842">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-842">Return Values</span></span>

- <span data-ttu-id="58df1-843">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="58df1-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-846">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-847">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-848">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-849">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-849">Allowed From</span></span>

<span data-ttu-id="58df1-850">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-851">例</span><span class="sxs-lookup"><span data-stu-id="58df1-851">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="58df1-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="58df1-853">HTTP PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-854">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-855">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-855">Description</span></span>

<span data-ttu-id="58df1-856">このメソッドは、**プレーンテキスト** の HTTP 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="58df1-857">このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する PUT 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-858">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-859">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-860">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-861">このサービスによって *nx_web_http_client_put_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="58df1-862">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-863">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-863">Input Parameters</span></span>

- <span data-ttu-id="58df1-864">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-865">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-866">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-867">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-868">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-869">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-870">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-871">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-872">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-873">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-874">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-875">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-876">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-877">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-878">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-879">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-880">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-881">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-883">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-883">Return Values</span></span>

- <span data-ttu-id="58df1-884">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="58df1-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-887">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-888">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-889">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-890">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-890">Allowed From</span></span>

<span data-ttu-id="58df1-891">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-892">例</span><span class="sxs-lookup"><span data-stu-id="58df1-892">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="58df1-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="58df1-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="58df1-894">暗号化された HTTPS PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-895">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-895">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-896">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-896">Description</span></span>

<span data-ttu-id="58df1-897">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-898">このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する PUT 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-899">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-900">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-901">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-901">This service is deprecated.</span></span> <span data-ttu-id="58df1-902">開発者には、*nx_web_http_client_put_secure_start_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-903">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-903">Input Parameters</span></span>

- <span data-ttu-id="58df1-904">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-905">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-906">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-907">**resource** サーバーに送信するリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="58df1-908">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-909">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-910">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-911">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-912">**password** 認証用の省略可能なパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-913">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-914">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-915">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-916">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-917">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-918">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-919">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-921">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-921">Return Values</span></span>

- <span data-ttu-id="58df1-922">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="58df1-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-925">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-926">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-927">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-928">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-928">Allowed From</span></span>

<span data-ttu-id="58df1-929">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-930">例</span><span class="sxs-lookup"><span data-stu-id="58df1-930">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="58df1-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="58df1-932">暗号化された HTTPS PUT 要求を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-933">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-933">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-934">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-934">Description</span></span>

<span data-ttu-id="58df1-935">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-936">このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する PUT 要求の送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="58df1-937">このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="58df1-938">リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="58df1-939">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-940">このサービスによって *nx_web_http_client_put_secure_start*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="58df1-941">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-942">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-942">Input Parameters</span></span>

- <span data-ttu-id="58df1-943">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-944">**ip_address** HTTP Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="58df1-945">**server_port** リモート HTTP Server 上の TCP ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="58df1-946">**resource** 要求されたリソースの URL 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="58df1-947">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-948">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-949">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-950">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-951">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-952">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-953">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-954">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-955">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-956">**total_bytes** 送信されるリソースの合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="58df1-957">後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="58df1-958">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-959">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-960">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-961">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-962">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-964">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-964">Return Values</span></span>

- <span data-ttu-id="58df1-965">**NX_SUCCESS** (0x00) PUT 要求が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="58df1-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="58df1-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-968">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-969">NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="58df1-970">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-971">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-971">Allowed From</span></span>

<span data-ttu-id="58df1-972">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-973">例</span><span class="sxs-lookup"><span data-stu-id="58df1-973">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="58df1-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="58df1-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="58df1-975">次のリソース データ パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-976">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-977">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-977">Description</span></span>

<span data-ttu-id="58df1-978">このサービスでは、PUT 操作と POST 操作でリソース コンテンツの次のパケットを HTTP Server に送信することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="58df1-979">このルーチンは、送信されたパケットの合計長が先行する *nx_web_http_client_put_start()* または *nx_web_http_client_post_start()* の呼び出し (または対応するセキュリティで保護されたバージョン) で指定された "total_bytes" と同じになるまで、繰り返し呼び出す必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="58df1-980">また、このサービスでは、HTTP (または HTTPS) 接続の確立で問題が発生した場合のために、サーバーからの応答がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="58df1-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-981">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-981">Input Parameters</span></span>

- <span data-ttu-id="58df1-982">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-983">**packet_ptr** HTTP Server に送信されるリソースの次のコンテンツへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="58df1-984">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-985">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-986">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-988">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-988">Return Values</span></span>

- <span data-ttu-id="58df1-989">**NX_SUCCESS** (0x00) HTTP Client のパケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="58df1-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません</span><span class="sxs-lookup"><span data-stu-id="58df1-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="58df1-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) サーバー エラー コードを受信しました\*\*</span><span class="sxs-lookup"><span data-stu-id="58df1-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="58df1-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) パケットの長さが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="58df1-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="58df1-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) PUT が完了する前にサーバーが応答しました</span><span class="sxs-lookup"><span data-stu-id="58df1-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="58df1-995">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-996">NX_INVALID_PACKET (0x12) パケットが TCP ヘッダーに対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="58df1-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="58df1-997">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-998">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-998">Allowed From</span></span>

<span data-ttu-id="58df1-999">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1000">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="58df1-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="58df1-1002">HTTP(S) 要求にチャンク転送を設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1003">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1004">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1004">Description</span></span>

<span data-ttu-id="58df1-1005">このサービスでは、リモート ホストへのソケット接続をあらかじめ確立した *nx_web_http_client_connect()* または *nx_web_http_client_secure_connect()* 呼び出しで指定されたサーバーに、チャンク転送コーディングを使用してカスタム HTTP(S) 要求が送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1006">アプリケーションでチャンク転送コーディングを使用して要求データ パケットを送信する場合は、*nx_web_http_client_request_packet_allocate*() を呼び出した後にこのサービスを呼び出し、その後、*nx_web_http_client_reqeust_packet_send*() を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1007">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1007">Input Parameters</span></span>

- <span data-ttu-id="58df1-1008">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1009">**chunk_size** チャンクデータのサイズ (オクテット単位)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="58df1-1010">**packet_ptr** HTTP(S) 要求データ パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1011">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1011">Return Values</span></span>

- <span data-ttu-id="58df1-1012">**NX_SUCCESS** (0x00) チャンクが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="58df1-1013">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1014">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1014">Allowed From</span></span>

<span data-ttu-id="58df1-1015">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1016">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="58df1-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="58df1-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="58df1-1018">カスタム HTTP 要求にカスタム ヘッダーを追加する</span><span class="sxs-lookup"><span data-stu-id="58df1-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1019">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1020">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1020">Description</span></span>

<span data-ttu-id="58df1-1021">このサービスでは、*nx_web_http_client_request_initialize()* で作成されたカスタム HTTP 要求に (フィールド名と値の形式で) カスタム ヘッダーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="58df1-1022">このサービスを使用すると、アプリケーションで任意の数のカスタム ヘッダーを要求に追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="58df1-1023">**これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。**</span><span class="sxs-lookup"><span data-stu-id="58df1-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1024">nx_web_http_client_\*_start メソッドは、利便性のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="58df1-1025">これらのすべての関数では、このルーチンを (*nx_web_http_client_request_initialize()* と共に) 内部で使用し、HTTP 要求を作成して送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1026">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1026">Input Parameters</span></span>

- <span data-ttu-id="58df1-1027">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1028">**field_name** フィールド名の文字列 ("Content-type" など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="58df1-1029">**name_length** フィールド名文字列の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="58df1-1030">**field_value** フィールド値の文字列 ("application/octet-stream" など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="58df1-1031">**value_length** 値の文字列の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="58df1-1032">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1033">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1034">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1036">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1036">Return Values</span></span>

- <span data-ttu-id="58df1-1037">**NX_SUCCESS** (0x00) 要求にヘッダーが正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="58df1-1038">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1039">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1039">Allowed From</span></span>

<span data-ttu-id="58df1-1040">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1041">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="58df1-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="58df1-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="58df1-1043">カスタム HTTP 要求を初期化する</span><span class="sxs-lookup"><span data-stu-id="58df1-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1044">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1045">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1045">Description</span></span>

<span data-ttu-id="58df1-1046">このサービスでは、カスタム HTTP 要求が作成され、HTTP Client インスタンスに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="58df1-1047">より単純な *nx_web_http_client_get_start()* (および PUT、POST とそれらの API に関連付けられたセキュリティで保護されたバージョンのメソッド) とは異なり、カスタム要求は、*nx_web_http_client_request_send()* サービスが呼び出されるまで送信されません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="58df1-1048">このサービスを使用すると、アプリケーションでは、***nx_web_http_client_request_header_add()*** サービスを使用して、要求に任意の数のカスタム ヘッダーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="58df1-1049">これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1050">nx_web_http_client_\*_start メソッドは、利便性のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="58df1-1051">これらのすべての関数では、このルーチンを (*nx_web_http_client_request_send()* と共に) 内部で使用し、HTTP 要求を作成して送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="58df1-1052">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1052">This service is deprecated.</span></span> <span data-ttu-id="58df1-1053">開発者には、*nx_web_http_client_request_initialize_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1054">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1054">Input Parameters</span></span>

- <span data-ttu-id="58df1-1055">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1056">**method** 使用する HTTP 要求メソッド。</span><span class="sxs-lookup"><span data-stu-id="58df1-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="58df1-1057">オプションは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="58df1-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="58df1-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="58df1-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="58df1-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="58df1-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="58df1-1064">**resource** 転送されるリソースの名前。</span><span class="sxs-lookup"><span data-stu-id="58df1-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="58df1-1065">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-1066">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-1067">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-1068">**input_size** PUT および POST の入力データのサイズ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="58df1-1069">他の操作の場合は 0 を渡します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="58df1-1070">**transfer_encoding_trunked** 将来のトランク転送のサポートのために予約されているパラメーター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="58df1-1071">**username** 保護されたリソースのユーザー名。</span><span class="sxs-lookup"><span data-stu-id="58df1-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="58df1-1072">**password** 保護されたリソースのパスワード。</span><span class="sxs-lookup"><span data-stu-id="58df1-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="58df1-1073">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1074">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1075">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1077">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1077">Return Values</span></span>

- <span data-ttu-id="58df1-1078">**NX_SUCCESS** (0x00) 要求が正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="58df1-1079">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) 一部の必須の情報がありませんでした (PUT または POST の input_size など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1081">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1081">Allowed From</span></span>

<span data-ttu-id="58df1-1082">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1083">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1083">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="58df1-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="58df1-1085">カスタム HTTP 要求を初期化する</span><span class="sxs-lookup"><span data-stu-id="58df1-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1086">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1087">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1087">Description</span></span>

<span data-ttu-id="58df1-1088">このサービスでは、カスタム HTTP 要求が作成され、HTTP Client インスタンスに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="58df1-1089">より単純な *nx_web_http_client_get_start()* (および PUT、POST とそれらの API に関連付けられたセキュリティで保護されたバージョンのメソッド) とは異なり、カスタム要求は、*nx_web_http_client_request_send()* サービスが呼び出されるまで送信されません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="58df1-1090">このサービスを使用すると、アプリケーションでは、***nx_web_http_client_request_header_add()*** サービスを使用して、要求に任意の数のカスタム ヘッダーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="58df1-1091">これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1092">nx_web_http_client_\*_start メソッドは、利便性のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="58df1-1093">これらのすべての関数では、このルーチンを (*nx_web_http_client_request_send()* と共に) 内部で使用し、HTTP 要求を作成して送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="58df1-1094">resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-1095">このサービスによって *nx_web_http_client_request_initialize*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="58df1-1096">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1097">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1097">Input Parameters</span></span>

- <span data-ttu-id="58df1-1098">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1099">**method** 使用する HTTP 要求メソッド。</span><span class="sxs-lookup"><span data-stu-id="58df1-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="58df1-1100">オプションは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="58df1-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="58df1-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="58df1-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="58df1-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="58df1-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="58df1-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="58df1-1107">**resource** 転送されるリソースの名前。</span><span class="sxs-lookup"><span data-stu-id="58df1-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="58df1-1108">**resource_length** 要求されたリソースの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="58df1-1109">**host** サーバーのドメイン名の Null 終端の文字列。</span><span class="sxs-lookup"><span data-stu-id="58df1-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="58df1-1110">この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="58df1-1111">ホスト文字列を NULL にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="58df1-1112">**host_length** ホストの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="58df1-1113">**input_size** PUT および POST の入力データのサイズ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="58df1-1114">他の操作の場合は 0 を渡します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="58df1-1115">**transfer_encoding_trunked** 将来のトランク転送のサポートのために予約されているパラメーター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="58df1-1116">**username** 省略可能な認証用のユーザー名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="58df1-1117">**username_length** 認証用のユーザー名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="58df1-1118">**password** 省略可能な認証用のパスワードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="58df1-1119">**password_length** 認証用のパスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="58df1-1120">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1121">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1122">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1124">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1124">Return Values</span></span>

- <span data-ttu-id="58df1-1125">**NX_SUCCESS** (0x00) 要求が正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="58df1-1126">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) 一部の必須の情報がありませんでした (PUT または POST の input_size など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1128">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1128">Allowed From</span></span>

<span data-ttu-id="58df1-1129">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1130">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1130">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="58df1-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="58df1-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="58df1-1132">HTTP(S) 要求データ パケットをリモート サーバーに送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1133">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1134">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1134">Description</span></span>

<span data-ttu-id="58df1-1135">このサービスでは、リモート ホストへのソケット接続をあらかじめ確立した *nx_web_http_client_connect()* または *nx_web_http_client_secure_connect()* 呼び出しで指定されたサーバーに、*nx_web_http_client_request_packet_allocate*() で作成されたカスタム HTTP(S) 要求データ パケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1136">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1136">Input Parameters</span></span>

- <span data-ttu-id="58df1-1137">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1138">**packet_ptr** HTTP(S) 要求データ パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="58df1-1139">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1140">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1141">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1143">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1143">Return Values</span></span>

- <span data-ttu-id="58df1-1144">**NX_SUCCESS** (0x00) 要求データ パケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="58df1-1145">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1146">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1146">Allowed From</span></span>

<span data-ttu-id="58df1-1147">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1148">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="58df1-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="58df1-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="58df1-1150">カスタム HTTP 要求を送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1151">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1152">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1152">Description</span></span>

<span data-ttu-id="58df1-1153">このサービスでは、リモート ホストへのソケット接続をあらかじめ確立した *nx_web_http_client_connect()* または *nx_web_http_client_secure_connect()* で指定されたサーバーに、*nx_web_http_client_request_initialize*() で作成されたカスタム HTTP 要求が送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="58df1-1154">このサービスを使用すると、アプリケーションでは、***nx_web_http_client_request_header_add()*** サービスを使用して、要求に任意の数のカスタム ヘッダーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="58df1-1155">これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1156">nx_web_http_client_\*_start メソッドは、利便性のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="58df1-1157">これらのすべての関数では、このルーチンを (*nx_web_http_client_request_initialize()* と共に) 内部で使用し、HTTP 要求を作成して送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1158">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1158">Input Parameters</span></span>

- <span data-ttu-id="58df1-1159">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1160">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1161">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1162">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1164">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1164">Return Values</span></span>

- <span data-ttu-id="58df1-1165">**NX_SUCCESS** (0x00) 要求が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="58df1-1166">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1167">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1167">Allowed From</span></span>

<span data-ttu-id="58df1-1168">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1169">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="58df1-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="58df1-1171">次のリソース データ パケットを取得する</span><span class="sxs-lookup"><span data-stu-id="58df1-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1172">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1173">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1173">Description</span></span>

<span data-ttu-id="58df1-1174">このサービスでは、先行する *nx_web_http_client_get_start()* または *nx_web_http_client_get_secure_start()* 呼び出しによって要求されたリソースのコンテンツの次のパケットが取得されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="58df1-1175">NX_WEB_HTTP_GET_DONE という戻りステータスを受け取るまで、このルーチンを連続して呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1176">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1176">Input Parameters</span></span>

- <span data-ttu-id="58df1-1177">**client_ptr** HTTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1178">**packet_ptr** 部分的なリソース コンテンツを含むパケット ポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="58df1-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="58df1-1179">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1180">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1181">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1183">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1183">Return Values</span></span>

- <span data-ttu-id="58df1-1184">**NX_SUCCESS** (0x00) HTTP Client パケットが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="58df1-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client のパケット取得が完了しました</span><span class="sxs-lookup"><span data-stu-id="58df1-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="58df1-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client が GET モードではありません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="58df1-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) パケットの長さが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="58df1-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP 状態コード 100 - 継続</span><span class="sxs-lookup"><span data-stu-id="58df1-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="58df1-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP 状態コード 101 - プロトコルの切り替え</span><span class="sxs-lookup"><span data-stu-id="58df1-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="58df1-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP 状態コード 201 - 作成</span><span class="sxs-lookup"><span data-stu-id="58df1-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="58df1-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP 状態コード 202 - 受理</span><span class="sxs-lookup"><span data-stu-id="58df1-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="58df1-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP 状態コード 203 - 信頼できない情報</span><span class="sxs-lookup"><span data-stu-id="58df1-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="58df1-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP 状態コード 204 - 内容なし</span><span class="sxs-lookup"><span data-stu-id="58df1-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="58df1-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP 状態コード 205 - 内容のリセット</span><span class="sxs-lookup"><span data-stu-id="58df1-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="58df1-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP 状態コード 206 - 部分的内容</span><span class="sxs-lookup"><span data-stu-id="58df1-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="58df1-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP 状態コード 300 - 複数の選択</span><span class="sxs-lookup"><span data-stu-id="58df1-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="58df1-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP 状態コード 301 - 恒久的に移動</span><span class="sxs-lookup"><span data-stu-id="58df1-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="58df1-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP 状態コード 302 - 発見</span><span class="sxs-lookup"><span data-stu-id="58df1-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="58df1-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP 状態コード 303 - 他を参照せよ</span><span class="sxs-lookup"><span data-stu-id="58df1-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="58df1-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP 状態コード 304 - 未更新</span><span class="sxs-lookup"><span data-stu-id="58df1-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="58df1-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP 状態コード 305 - プロキシを使用せよ</span><span class="sxs-lookup"><span data-stu-id="58df1-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="58df1-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP 状態コード 307 - 一時的リダイレクト</span><span class="sxs-lookup"><span data-stu-id="58df1-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="58df1-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP 状態コード 400 - 不正な要求</span><span class="sxs-lookup"><span data-stu-id="58df1-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="58df1-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP 状態コード 401 - 認証が必要</span><span class="sxs-lookup"><span data-stu-id="58df1-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="58df1-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP 状態コード 402 - 支払いが必要</span><span class="sxs-lookup"><span data-stu-id="58df1-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="58df1-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP 状態コード 403 - 拒否</span><span class="sxs-lookup"><span data-stu-id="58df1-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="58df1-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP 状態コード 404 - 未検出</span><span class="sxs-lookup"><span data-stu-id="58df1-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="58df1-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP 状態コード 405 - 未許可のメソッド</span><span class="sxs-lookup"><span data-stu-id="58df1-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="58df1-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP 状態コード 406 - 受理不可</span><span class="sxs-lookup"><span data-stu-id="58df1-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="58df1-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP 状態コード 407 - プロキシ認証が必要</span><span class="sxs-lookup"><span data-stu-id="58df1-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="58df1-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP 状態コード 408 - タイムアウト</span><span class="sxs-lookup"><span data-stu-id="58df1-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="58df1-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP 状態コード 409 - 競合</span><span class="sxs-lookup"><span data-stu-id="58df1-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="58df1-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP 状態コード 410 - 消滅</span><span class="sxs-lookup"><span data-stu-id="58df1-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="58df1-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP 状態コード 411 - 長さが必要</span><span class="sxs-lookup"><span data-stu-id="58df1-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="58df1-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP 状態コード 412 - 前提条件が失敗</span><span class="sxs-lookup"><span data-stu-id="58df1-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="58df1-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP 状態コード 413 - リクエスト エンティティが膨大</span><span class="sxs-lookup"><span data-stu-id="58df1-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="58df1-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP 状態コード 414 - 要求 URL が長すぎる</span><span class="sxs-lookup"><span data-stu-id="58df1-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="58df1-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP 状態コード 415 - サポートされていないメディア タイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="58df1-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP 状態コード 416 - 要求したレンジが範囲外</span><span class="sxs-lookup"><span data-stu-id="58df1-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="58df1-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP 状態コード 417 - Expect ヘッダーによる拡張が失敗</span><span class="sxs-lookup"><span data-stu-id="58df1-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="58df1-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP 状態コード 500 - 内部サーバー エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="58df1-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP 状態コード 501 - 実装されていない</span><span class="sxs-lookup"><span data-stu-id="58df1-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="58df1-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP 状態コード 502 - 不正なゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="58df1-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="58df1-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP 状態コード 503 - サービス利用不可</span><span class="sxs-lookup"><span data-stu-id="58df1-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="58df1-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP 状態コード 504 - ゲートウェイ タイムアウト</span><span class="sxs-lookup"><span data-stu-id="58df1-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="58df1-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP 状態コード 505 - サポートされていない HTTP バージョン</span><span class="sxs-lookup"><span data-stu-id="58df1-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="58df1-1227">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1228">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1229">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1229">Allowed From</span></span>

<span data-ttu-id="58df1-1230">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1231">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="58df1-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="58df1-1233">HTTP ヘッダーが処理されるときに呼び出されるコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1234">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="58df1-1235">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1235">Description</span></span>

<span data-ttu-id="58df1-1236">このサービスでは、リモート HTTP Server からの受信応答の HTTP ヘッダーが NetX Web HTTP Client で処理されるたびに呼び出されるコールバックが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="58df1-1237">このコールバックは、応答が処理されるときに応答の各ヘッダーに対して 1 回ずつ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="58df1-1238">このコールバックを使用すると、HTTP Client アプリケーションでは HTTP Server の応答の各ヘッダーにアクセスし、NetX Web HTTP Client によって行われる基本的な処理以外の必要なアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1239">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1239">Input Parameters</span></span>

<span data-ttu-id="58df1-1240">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="58df1-1241">**callback_function** 応答ヘッダーの処理中に呼び出すコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="58df1-1242">このコールバックは、フィールドの名前と値の文字列 (およびその長さ) を使用して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="58df1-1243">たとえば、ヘッダー "Content-Length: 100" を指定すると、*field_name* に "Content-Length"、*field_value* に文字列 "100" が指定されて関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1244">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1244">Return Values</span></span>

- <span data-ttu-id="58df1-1245">**NX_SUCCESS** (0x00) コールバックが正常に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="58df1-1246">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1247">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1247">Allowed From</span></span>

<span data-ttu-id="58df1-1248">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1249">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1249">Example</span></span>

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="58df1-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="58df1-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="58df1-1251">カスタム要求のために HTTPS Server への TLS セッションを開く</span><span class="sxs-lookup"><span data-stu-id="58df1-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1252">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1253">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1253">Description</span></span>

<span data-ttu-id="58df1-1254">このメソッドは **TLS で保護された** HTTPS 用です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="58df1-1255">このサービスでは、HTTPS Server へのセキュリティで保護された TLS セッションが開かれますが、要求は送信されません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="58df1-1256">要求は、*nx_web_http_client_request_initialize()* を使用して作成され、*nx_web_http_client_request_send()* を使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="58df1-1257">カスタム HTTP ヘッダーを要求に追加するには、*nx_web_http_client_request_header_add()* を使用します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="58df1-1258">このサービスを使用すると、アプリケーションで任意の数のカスタム ヘッダーを要求に追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="58df1-1259">**これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。**</span><span class="sxs-lookup"><span data-stu-id="58df1-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1260">nx_web_http_client_\*_start メソッドは、利便性のために提供されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="58df1-1261">これらのすべての関数では、このルーチンを (*nx_web_http_client_request_initialize()* と共に) 内部で使用し、HTTP 要求を作成して送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1262">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1262">Input Parameters</span></span>

- <span data-ttu-id="58df1-1263">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1264">**server_ip** リモート HTTPS Server の IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="58df1-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="58df1-1265">**server_port** リモート HTTPS Server のポート (HTTPS の場合は 443 など)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="58df1-1266">**tls_setup** TLS 構成を設定するために使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="58df1-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="58df1-1267">アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="58df1-1268">**wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="58df1-1269">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1270">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="58df1-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1272">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1272">Return Values</span></span>

- <span data-ttu-id="58df1-1273">**NX_SUCCESS** (0x00) TLS セッションが正常に接続されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="58df1-1274">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1275">NX_WEB_HTTP_NOT_READY (0x3000A) 別の要求が既に進行中です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1276">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1276">Allowed From</span></span>

<span data-ttu-id="58df1-1277">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1278">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1278">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="58df1-1279">HTTP および HTTPS Server の API</span><span class="sxs-lookup"><span data-stu-id="58df1-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="58df1-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="58df1-1281">URL の最大有効期間と日付を取得するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1282">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="58df1-1283">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1283">Description</span></span>

<span data-ttu-id="58df1-1284">このサービスは、指定されたリソースの最大有効期間と最終更新日を取得するために呼び出されるコールバック サービスを設定します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1285">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1285">Input Parameters</span></span>

- <span data-ttu-id="58df1-1286">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1287">**cache_info_get** コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="58df1-1288">**max_age** リソースの最大有効期間へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="58df1-1289">**data** 返された最終更新日へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1290">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1290">Return Values</span></span>

- <span data-ttu-id="58df1-1291">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="58df1-1292">**NX_PTR_ERROR** (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1293">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1293">Allowed From</span></span>

<span data-ttu-id="58df1-1294">初期化</span><span class="sxs-lookup"><span data-stu-id="58df1-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1295">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="58df1-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="58df1-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="58df1-1297">コールバック関数からデータを送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1298">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="58df1-1299">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1299">Description</span></span>

<span data-ttu-id="58df1-1300">このサービスは、アプリケーションのコールバック ルーチンから、指定されたパケット内のデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="58df1-1301">これは通常、GET または POST 要求に関連付けられた動的データを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="58df1-1302">この関数を使用する場合、応答全体を適切な形式で送信するのはコールバック ルーチンの責任であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="58df1-1303">また、コールバック ルーチンによって NX_WEB_HTTP_CALLBACK_COMPLETED という状態が返される必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1304">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1304">Input Parameters</span></span>

- <span data-ttu-id="58df1-1305">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1306">**data_ptr** 送信するデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="58df1-1307">**data_length** 送信するバイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1308">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1308">Return Values</span></span>

- <span data-ttu-id="58df1-1309">**NX_SUCCESS** (0x00) サーバー データが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="58df1-1310">**NX_PTR_ERROR** (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1311">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1311">Allowed From</span></span>

<span data-ttu-id="58df1-1312">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1313">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1313">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="58df1-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="58df1-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="58df1-1315">コールバック関数で応答ヘッダーを作成する</span><span class="sxs-lookup"><span data-stu-id="58df1-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1316">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="58df1-1317">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1317">Description</span></span>

<span data-ttu-id="58df1-1318">このサービスは、HTTP 応答ヘッダーを生成するために、HTTP(S) サーバー コールバック ルーチン (アプリケーションで定義します) で使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="58df1-1319">サーバー コールバック ルーチンは、HTTP 応答を必要とするクライアントの GET、PUT、DELETE 要求に対して HTTP Server が応答するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="58df1-1320">この関数では、アプリケーションから応答情報を受け取り、適切な応答ヘッダーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="58df1-1321">サーバー要求コールバック ルーチンの詳細については、サービス *nx_web_http_server_create()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="58df1-1322">この API は非推奨です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1322">This API is deprecated.</span></span> <span data-ttu-id="58df1-1323">開発者には、*nx_web_http_server_callback_generate_response_header_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1324">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1324">Input Parameters</span></span>

- <span data-ttu-id="58df1-1325">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1326">**packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="58df1-1327">**status_code** リソースの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="58df1-1328">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1328">Examples:</span></span>
  - <span data-ttu-id="58df1-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="58df1-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="58df1-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="58df1-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="58df1-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="58df1-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="58df1-1332">**content_length** コンテンツのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="58df1-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="58df1-1333">**content_type** HTTP の種類 ("text/plain" など)</span><span class="sxs-lookup"><span data-stu-id="58df1-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="58df1-1334">**additional_header** 追加のヘッダー テキストへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1335">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1335">Return Values</span></span>

- <span data-ttu-id="58df1-1336">**NX_SUCCESS** (0x00) HTML ヘッダーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="58df1-1337">**NX_PTR_ERROR** (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1338">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1338">Allowed From</span></span>

<span data-ttu-id="58df1-1339">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1340">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1340">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="58df1-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="58df1-1342">コールバック関数で応答ヘッダーを作成する</span><span class="sxs-lookup"><span data-stu-id="58df1-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1343">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1343">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="58df1-1344">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1344">Description</span></span>

<span data-ttu-id="58df1-1345">このサービスは、HTTP 応答ヘッダーを生成するために、HTTP(S) サーバー コールバック ルーチン (アプリケーションで定義します) で使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="58df1-1346">サーバー コールバック ルーチンは、HTTP 応答を必要とするクライアントの GET、PUT、DELETE 要求に対して HTTP Server が応答するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="58df1-1347">この関数では、アプリケーションから応答情報を受け取り、適切な応答ヘッダーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="58df1-1348">サーバー要求コールバック ルーチンの詳細については、サービス *nx_web_http_server_create()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1349">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1349">Input Parameters</span></span>

- <span data-ttu-id="58df1-1350">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1351">**packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="58df1-1352">**status_code** リソースの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="58df1-1353">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1353">Examples:</span></span>
  - <span data-ttu-id="58df1-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="58df1-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="58df1-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="58df1-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="58df1-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="58df1-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="58df1-1357">**status_code_length** 状態コードの文字列の長さ</span><span class="sxs-lookup"><span data-stu-id="58df1-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="58df1-1358">**content_length** コンテンツのサイズ (バイト単位)</span><span class="sxs-lookup"><span data-stu-id="58df1-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="58df1-1359">**content_type** HTTP の種類 ("text/plain" など)</span><span class="sxs-lookup"><span data-stu-id="58df1-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="58df1-1360">**content_type_length** コンテンツの種類の文字列の長さ</span><span class="sxs-lookup"><span data-stu-id="58df1-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="58df1-1361">**additional_header** 追加のヘッダー テキストへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="58df1-1362">**additional_header_length** 追加のヘッダー テキストの長さ</span><span class="sxs-lookup"><span data-stu-id="58df1-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1363">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1363">Return Values</span></span>

- <span data-ttu-id="58df1-1364">**NX_SUCCESS** (0x00) HTML ヘッダーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="58df1-1365">**NX_PTR_ERROR** (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1366">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1366">Allowed From</span></span>

<span data-ttu-id="58df1-1367">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1368">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1368">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="58df1-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="58df1-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="58df1-1370">コールバック関数から HTTP パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1371">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1372">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1372">Description</span></span>

<span data-ttu-id="58df1-1373">このサービスでは、HTTP コールバックから完全な HTTP Server の応答が送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="58df1-1374">HTTP Server では、NX_WEB_HTTP_SERVER _TIMEOUT_SEND を使用してパケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="58df1-1375">HTTP のヘッダーとデータをパケットに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="58df1-1376">戻りステータスがエラーを示している場合、HTTP アプリケーションでパケットを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="58df1-1377">このコールバックによって NX_WEB_HTTP_CALLBACK_COMPLETED が返される必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="58df1-1378">詳細な例については、*nx_web_http_server_callback_generate_response_header()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1379">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1379">Input Parameters</span></span>

- <span data-ttu-id="58df1-1380">**server_ptr** HTTP Server の制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="58df1-1381">**packet_ptr** 送信するパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1382">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1382">Return Values</span></span>

- <span data-ttu-id="58df1-1383">**NX_SUCCESS** (0x00) HTTP Server のパケットが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="58df1-1384">**NX_PTR_ERROR** (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1385">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1385">Allowed From</span></span>

<span data-ttu-id="58df1-1386">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1387">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1387">Example</span></span>

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="58df1-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="58df1-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="58df1-1389">コールバック関数から応答を送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1390">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="58df1-1391">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1391">Description</span></span>

<span data-ttu-id="58df1-1392">このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="58df1-1393">通常、これは GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="58df1-1394">この関数を使用する場合、コールバック ルーチンによって NX_WEB_HTTP_CALLBACK_COMPLETED という状態が返される必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="58df1-1395">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1395">This service is deprecated.</span></span> <span data-ttu-id="58df1-1396">開発者には、*nx_web_http_server_callback_response_send_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1397">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1397">Input Parameters</span></span>

- <span data-ttu-id="58df1-1398">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1399">**header** 応答ヘッダー文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="58df1-1400">**information** 情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="58df1-1401">**additional_info** 追加の情報文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1402">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1402">Return Values</span></span>

- <span data-ttu-id="58df1-1403">**NX_SUCCESS** (0x00) HTTP Server の応答が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1404">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1404">Allowed From</span></span>

<span data-ttu-id="58df1-1405">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1406">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1406">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="58df1-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="58df1-1408">コールバック関数から応答を送信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1409">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="58df1-1410">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1410">Description</span></span>

<span data-ttu-id="58df1-1411">このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="58df1-1412">通常、これは GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="58df1-1413">この関数を使用する場合、コールバック ルーチンによって NX_WEB_HTTP_CALLBACK_COMPLETED という状態が返される必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="58df1-1414">header、information、additional_info の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="58df1-1415">このサービスによって *nx_web_http_server_callback_response_send*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="58df1-1416">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1417">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1417">Input Parameters</span></span>

- <span data-ttu-id="58df1-1418">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1419">**header** 応答ヘッダー文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="58df1-1420">**header_length** 応答ヘッダー文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="58df1-1421">**information** 情報の文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="58df1-1422">**information_length** 情報の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="58df1-1423">**additional_info** 追加の情報の文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="58df1-1424">**additional_info_length** 追加の情報文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1425">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1425">Return Values</span></span>

- <span data-ttu-id="58df1-1426">**NX_SUCCESS** (0x00) HTTP Server の応答が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1427">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1427">Allowed From</span></span>

<span data-ttu-id="58df1-1428">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1429">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1429">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="58df1-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="58df1-1431">要求からコンテンツを取得する</span><span class="sxs-lookup"><span data-stu-id="58df1-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1432">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1433">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1433">Description</span></span>

<span data-ttu-id="58df1-1434">このサービスでは、POST または PUT の HTTP Client 要求から指定された量のコンテンツを取得することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="58df1-1435">これは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1436">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1436">Input Parameters</span></span>

- <span data-ttu-id="58df1-1437">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1438">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="58df1-1439">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="58df1-1440">**byte_offset** コンテンツ領域にオフセットするバイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="58df1-1441">**destination_ptr** コンテンツのコピー先領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="58df1-1442">**destination_size** コピー先領域の使用可能な最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="58df1-1443">**actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1444">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1444">Return Values</span></span>

- <span data-ttu-id="58df1-1445">**NX_SUCCESS** (0x00) HTTP Server のコンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="58df1-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server の内部エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="58df1-1447">**NX_WEB_HTTP_DATA_END** (0x30007) 要求コンテンツの終わり</span><span class="sxs-lookup"><span data-stu-id="58df1-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="58df1-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) コンテンツの次のパケットを取得しているときに HTTP Server がタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="58df1-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="58df1-1449">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1450">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1451">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1451">Allowed From</span></span>

<span data-ttu-id="58df1-1452">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1453">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="58df1-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="58df1-1455">要求からコンテンツを取得する (長さゼロのコンテンツの長さがサポートされます)</span><span class="sxs-lookup"><span data-stu-id="58df1-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1456">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1457">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1457">Description</span></span>

<span data-ttu-id="58df1-1458">このサービスは *nx_web_http_server_content_get()* とほぼ同じで、POST または PUT の HTTP Client 要求から指定された量のコンテンツを取得することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="58df1-1459">ただし、コンテンツの長さがゼロ値の要求 ("空の要求") が有効な要求として処理されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="58df1-1460">これは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="58df1-1461">このサービスによって *nx_web_http_server_content_get*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="58df1-1462">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1463">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1463">Input Parameters</span></span>

- <span data-ttu-id="58df1-1464">**server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1465">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="58df1-1466">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="58df1-1467">**byte_offset** コンテンツ領域にオフセットするバイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="58df1-1468">**destination_ptr** コンテンツのコピー先領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="58df1-1469">**destination_size** コピー先領域の使用可能な最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="58df1-1470">**actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1471">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1471">Return Values</span></span>

- <span data-ttu-id="58df1-1472">**NX_SUCCESS** (0x00) HTTP コンテンツが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="58df1-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server の内部エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="58df1-1474">**NX_WEB_HTTP_DATA_END** (0x30007) 要求コンテンツの終わり</span><span class="sxs-lookup"><span data-stu-id="58df1-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="58df1-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) 次のパケットを取得しているときに HTTP Server がタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="58df1-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="58df1-1476">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1477">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1478">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1478">Allowed From</span></span>

<span data-ttu-id="58df1-1479">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1480">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="58df1-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="58df1-1482">要求のコンテンツの長さを取得する (ゼロ値のコンテンツの長さがサポートされます)</span><span class="sxs-lookup"><span data-stu-id="58df1-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1483">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="58df1-1484">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1484">Description</span></span>

<span data-ttu-id="58df1-1485">このサービスでは、指定されたパケットの HTTP コンテンツの長さの取得が試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="58df1-1486">戻り値では正常な完了状態が示され、実際の長さの値が入力ポインター content_length で返されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="58df1-1487">HTTP コンテンツがないか、コンテンツの長さが 0 の場合でも、このルーチンでは正常な完了状態が返され、content_length 入力ポインターは有効な長さ (ゼロ) を指します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="58df1-1488">これは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1489">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1489">Input Parameters</span></span>

- <span data-ttu-id="58df1-1490">**packet_ptr** HTTP クライアント要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="58df1-1491">このパケットは要求通知コールバックで解放してはならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="58df1-1492">**content_length** Content Length フィールドから取得した値へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1493">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1493">Return Values</span></span>

- <span data-ttu-id="58df1-1494">**NX_SUCCESS** (0x00) HTTP Server のコンテンツの長さが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="58df1-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) HTTP ヘッダーの形式が正しくありません</span><span class="sxs-lookup"><span data-stu-id="58df1-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="58df1-1496">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1497">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1497">Allowed From</span></span>

<span data-ttu-id="58df1-1498">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1499">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="58df1-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="58df1-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="58df1-1501">HTTP Server インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="58df1-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1502">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1502">Prototype</span></span>

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="58df1-1503">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1503">Description</span></span>

<span data-ttu-id="58df1-1504">このサービスは、専用の ThreadX スレッドのコンテキスト内で実行される HTTP サーバー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="58df1-1505">オプションの *authentication_check* および *request_notify* アプリケーション コールバック ルーチンを使用すると、アプリケーション ソフトウェアから HTTP Server の基本的な操作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="58df1-1506">このサービスは、プレーンテキストの HTTP Server と TLS で保護された HTTPS Server の両方を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="58df1-1507">TLS を使用して HTTPS を有効にする方法については、サービス *nx_web_http_server_secure_configure()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1508">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1508">Input Parameters</span></span>

- <span data-ttu-id="58df1-1509">**http_server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1510">**http_server_name** HTTP サーバーの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="58df1-1511">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="58df1-1512">**server_port** サーバー インスタンスの TCP リスニング ポート。</span><span class="sxs-lookup"><span data-stu-id="58df1-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="58df1-1513">**media_ptr** 以前に作成された FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="58df1-1514">**stack_ptr** HTTP サーバーのスレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="58df1-1515">**stack_size** HTTP サーバーのスレッド スタック サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="58df1-1516">**authentication_check** アプリケーションの認証確認ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="58df1-1517">指定した場合、このルーチンは HTTP クライアント要求ごとに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="58df1-1518">このパラメーターが null 値の場合、認証は実行されません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="58df1-1519">このパラメーターは非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1519">This parameter is deprecated.</span></span> <span data-ttu-id="58df1-1520">代わりに *nx_web_http_server_authenticate_check_set*() を呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="58df1-1521">**request_notify** アプリケーションの要求通知ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="58df1-1522">指定した場合、このルーチンは要求の HTTP サーバー処理の前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="58df1-1523">これにより、HTTP クライアント要求が完了する前に、リソース名をリダイレクトしたり、リソース内のフィールドを更新したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1524">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1524">Return Values</span></span>

- <span data-ttu-id="58df1-1525">**NX_SUCCESS** (0x00) HTTP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="58df1-1526">NX_PTR_ERROR (0x07) HTTP Server、IP、メディア、スタック、またはパケット プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="58df1-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) プールのパケット ペイロードが HTTP 要求全体を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1528">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1528">Allowed From</span></span>

<span data-ttu-id="58df1-1529">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="58df1-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1530">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="58df1-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="58df1-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="58df1-1532">HTTP Server インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="58df1-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1533">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1534">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1534">Description</span></span>

<span data-ttu-id="58df1-1535">このサービスは、以前に作成された HTTP サーバー インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1536">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1536">Input Parameters</span></span>

- <span data-ttu-id="58df1-1537">**http_server_ptr** HTTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1538">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1538">Return Values</span></span>

- <span data-ttu-id="58df1-1539">**NX_SUCCESS** (0x00) HTTP サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="58df1-1540">NX_PTR_ERROR (0x07) HTTP サーバー ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="58df1-1541">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1542">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1542">Allowed From</span></span>

<span data-ttu-id="58df1-1543">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1544">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="58df1-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="58df1-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="58df1-1546">エンティティ データの場所と長さを取得する</span><span class="sxs-lookup"><span data-stu-id="58df1-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1547">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="58df1-1548">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1548">Description</span></span>

<span data-ttu-id="58df1-1549">このサービスでは、受信したクライアント メッセージの現在のマルチパート エンティティ内にあるデータの開始位置と、境界文字列を除いたデータの長さが判別されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="58df1-1550">複数のエンティティを含むメッセージの同じクライアント データグラムに対してこの関数を再度呼び出すことができるように、HTTP Server 自体のオフセットが内部的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="58df1-1551">クライアント メッセージはマルチパケット データグラムであり、パケット ポインターが次のパケットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="58df1-1552">このサービスを使用するには NX_WEB_HTTP_MULTIPART_ENABLE を有効にする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="58df1-1553">また、packet_pptr が指しているパケットをアプリケーションで解放しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="58df1-1554">これは、HTTP Server によって内部的に行われます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="58df1-1555">詳細については、*nx_web_http_server_get_entity_header()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1556">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1556">Input Parameters</span></span>

- <span data-ttu-id="58df1-1557">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="58df1-1558">**packet_pptr** パケット ポインターの位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="58df1-1559">アプリケーションでこのパケットを解放しないように注意してください</span><span class="sxs-lookup"><span data-stu-id="58df1-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="58df1-1560">**available_offset** パケットのプリペンド ポインターからのエンティティ データのオフセットへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="58df1-1561">**available_length** エンティティ データの長さへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1562">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1562">Return Values</span></span>

- <span data-ttu-id="58df1-1563">**NX_SUCCESS** (0x00) エンティティ コンテンツのサイズと場所が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="58df1-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) HTTP Server の内部マルチパート マーカーのコンテンツが既に存在します</span><span class="sxs-lookup"><span data-stu-id="58df1-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="58df1-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server の内部エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="58df1-1566">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1567">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1567">Allowed From</span></span>

<span data-ttu-id="58df1-1568">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1569">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1569">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="58df1-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="58df1-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="58df1-1571">エンティティ ヘッダーのコンテンツを取得する</span><span class="sxs-lookup"><span data-stu-id="58df1-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1572">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1573">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1573">Description</span></span>

<span data-ttu-id="58df1-1574">このサービスは、エンティティ ヘッダーを取得して、指定されたバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="58df1-1575">複数のエンティティ ヘッダーを含むクライアント データグラム内の次のマルチパート エンティティを見つけるために、HTTP サーバー自体のポインターが内部的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="58df1-1576">クライアント メッセージはマルチパケット データグラムであり、パケット ポインターが次のパケットに更新されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="58df1-1577">このサービスを使用するには NX_WEB_HTTP_MULTIPART_ENABLE を有効にする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="58df1-1578">また、packet_pptr が指しているパケットをアプリケーションで解放しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1579">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1579">Input Parameters</span></span>

- <span data-ttu-id="58df1-1580">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="58df1-1581">**packet_pptr** パケット ポインターの位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="58df1-1582">アプリケーションでこのパケットを解放しないように注意してください</span><span class="sxs-lookup"><span data-stu-id="58df1-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="58df1-1583">**entity_header_buffer** エンティティ ヘッダーを格納する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="58df1-1584">**buffer_size** 入力バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="58df1-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1585">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1585">Return Values</span></span>

- <span data-ttu-id="58df1-1586">**NX_SUCCESS** (0x00) エンティティ ヘッダーが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="58df1-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) エンティティ ヘッダー フィールドが見つかりません</span><span class="sxs-lookup"><span data-stu-id="58df1-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="58df1-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) マルチパケット クライアント メッセージの次のパケットの受信期限が切れました</span><span class="sxs-lookup"><span data-stu-id="58df1-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="58df1-1589">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1590">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="58df1-1591">NX_WEB_HTTP_ERROR (0x30000) 内部 HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="58df1-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1592">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1592">Allowed From</span></span>

<span data-ttu-id="58df1-1593">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1594">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1594">Example</span></span>

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="58df1-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="58df1-1596">GMT の日付と時刻を取得するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1597">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="58df1-1598">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1598">Description</span></span>

<span data-ttu-id="58df1-1599">このサービスは、以前に作成された HTTP サーバーを使用して GMT の日付と時刻を取得するコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="58df1-1600">このサービスは、HTTP サーバーがクライアントに対する HTTP サーバー応答のヘッダーを作成しているときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1601">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1601">Input Parameters</span></span>

- <span data-ttu-id="58df1-1602">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="58df1-1603">**gmt_get** GMT コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="58df1-1604">**date** 取得される日付へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1605">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1605">Return Values</span></span>

- <span data-ttu-id="58df1-1606">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="58df1-1607">NX_PTR_ERROR (0x07) パケットまたはパラメーター ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1608">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1608">Allowed From</span></span>

<span data-ttu-id="58df1-1609">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1610">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1610">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="58df1-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="58df1-1612">無効なユーザー/パスワードを処理するコールバックを設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1613">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="58df1-1614">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1614">Description</span></span>

<span data-ttu-id="58df1-1615">このサービスは、ダイジェストまたは基本認証のいずれかによって、クライアントの GET、PUT、または DELETE 要求で無効なユーザー名とパスワードを受信したときに呼び出されるコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="58df1-1616">HTTP サーバーを先に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1617">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1617">Input Parameters</span></span>

- <span data-ttu-id="58df1-1618">**server_ptr** HTTP サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="58df1-1619">**invalid_username_password_callback** 無効なユーザーまたはパス コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="58df1-1620">**resource** クライアントによって指定されたリソースへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="58df1-1621">**client_address** クライアント アドレス</span><span class="sxs-lookup"><span data-stu-id="58df1-1621">**client_address** Client address</span></span>
- <span data-ttu-id="58df1-1622">**request_type** クライアント要求の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="58df1-1623">次を指定できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1623">May be:</span></span>
  - <span data-ttu-id="58df1-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="58df1-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="58df1-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="58df1-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="58df1-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="58df1-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1627">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1627">Return Values</span></span>

- <span data-ttu-id="58df1-1628">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="58df1-1629">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1630">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1630">Allowed From</span></span>

<span data-ttu-id="58df1-1631">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1632">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1632">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="58df1-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="58df1-1634">HTML 用の追加の MIME マップを設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1635">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="58df1-1636">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1636">Description</span></span>

<span data-ttu-id="58df1-1637">このサービスを使用すると、HTTP アプリケーション開発者は、NetX Web HTTP Server によって提供される既定の MIME の種類から MIME の種類を追加できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="58df1-1638">定義されている種類の一覧については、*nx_web_http_server_get_type()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="58df1-1639">GET 要求などのクライアント要求を受信すると、HTTP Server では、追加の MIME マップ セットを優先的に使用して HTTP ヘッダーから要求されたファイルの種類が解析されます。一致するものが見つからない場合は、HTTP Server の既定の MIME マップの中で一致するものが検索されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="58df1-1640">一致するものが見つからない場合、MIME の種類は既定で "text/plain" になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="58df1-1641">要求通知関数が HTTP Server に登録されている場合、要求通知コールバックから *nx_web_http_server_type_get_extended()* を呼び出して、ファイルの種類を解析できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1642">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1642">Input Parameters</span></span>

- <span data-ttu-id="58df1-1643">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="58df1-1644">**mime_maps** MIME マップ配列へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="58df1-1645">**mime_map_num** 配列内の MIME マップの数</span><span class="sxs-lookup"><span data-stu-id="58df1-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1646">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1646">Return Values</span></span>

- <span data-ttu-id="58df1-1647">**NX_SUCCESS** (0x00) HTTP サーバーの MIME マップが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="58df1-1648">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1649">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1649">Allowed From</span></span>

<span data-ttu-id="58df1-1650">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="58df1-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1651">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1651">Example</span></span>

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="58df1-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="58df1-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="58df1-1653">HTTP(S) パケットを割り当てる</span><span class="sxs-lookup"><span data-stu-id="58df1-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1654">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="58df1-1655">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1655">Description</span></span>

<span data-ttu-id="58df1-1656">このサービスでは、HTTP(S) サーバーにパケットを割り当てることが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="58df1-1657">このパケットを入力として使用する以降の NetX または HTTP Server API (nx_packet_data_append や \*\*nx_web_http_server_callback_packet_send など) が **失敗** した場合、パケットを解放するのはアプリケーションの責任であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="58df1-1658">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1658">Input Parameters</span></span>

- <span data-ttu-id="58df1-1659">**server_ptr** HTTP Server の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="58df1-1660">**packet_ptr** 割り当てられるパケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="58df1-1661">**wait_option** パケット プールに使用可能なパケットがない場合の待機時間をティックで定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="58df1-1662">この待機オプションは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="58df1-1663">**NX_NO_WAIT** (0x00000000) NX_NO_WAIT を選択すると、要求が履行されない場合、呼び出し元のスレッドによって直ちに制御が戻されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="58df1-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="58df1-1665">**timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1666">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1666">Return Values</span></span>

- <span data-ttu-id="58df1-1667">**NX_SUCCESS** (0x00) パケットが正常に割り当てられました</span><span class="sxs-lookup"><span data-stu-id="58df1-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="58df1-1668">**NX_NO_PACKET** (0x01) 使用可能なパケットがありません</span><span class="sxs-lookup"><span data-stu-id="58df1-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="58df1-1669">**NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="58df1-1670">**NX_INVALID_PARAMETERS** (0x4D) プロトコルをサポートできないパケット サイズです。</span><span class="sxs-lookup"><span data-stu-id="58df1-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="58df1-1671">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1672">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1673">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1673">Allowed From</span></span>

<span data-ttu-id="58df1-1674">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1675">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="58df1-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="58df1-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="58df1-1677">コンテンツの長さを抽出し、データの先頭にポインターを設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1678">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="58df1-1679">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1679">Description</span></span>

<span data-ttu-id="58df1-1680">このサービスは、HTTP ヘッダーからコンテンツの長さを抽出します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="58df1-1681">また、指定されたパケットを次のように更新します。パケットのプリペンド ポインター (書き込み先のパケット バッファーの開始位置) が、HTTP ヘッダーのすぐ先にある HTTP コンテンツ (データ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="58df1-1682">コンテンツの先頭が現在のパケット内に見つからない場合、この関数では、NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE 待機オプションを使用して、次のパケットを受信するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="58df1-1683">これにより、パケットのプリペンド ポインターがエンティティ ヘッダーの先に変更されるため、*nx_web_http_server_get_entity_header()* を呼び出す前に呼び出さないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1684">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1684">Input Parameters</span></span>

- <span data-ttu-id="58df1-1685">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="58df1-1686">**packet_ptr** 先頭追加ポインターが更新されたパケットを返すためのパケット ポインターへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="58df1-1687">**content_length** 抽出される content_length へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1688">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1688">Return Values</span></span>

- <span data-ttu-id="58df1-1689">**NX_SUCCESS** (0x00) HTTP コンテンツの長さが見つかり、パケットが正常に更新されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="58df1-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) 次のパケットを待機している間に時間切れになりました</span><span class="sxs-lookup"><span data-stu-id="58df1-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="58df1-1691">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1692">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1692">Allowed From</span></span>

<span data-ttu-id="58df1-1693">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1694">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1694">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="58df1-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="58df1-1696">次の HTTP パケットを受信する</span><span class="sxs-lookup"><span data-stu-id="58df1-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1697">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1698">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1698">Description</span></span>

<span data-ttu-id="58df1-1699">このサービスでは、HTTP Server のソケットで受信された次のパケットが返されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="58df1-1700">パケットを受信する際の待機オプションは NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE です。</span><span class="sxs-lookup"><span data-stu-id="58df1-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="58df1-1701">正常に実行された場合、パケットを解放するのはアプリケーションの責任であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1702">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1702">Input Parameters</span></span>

- <span data-ttu-id="58df1-1703">**server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="58df1-1704">**packet_ptr** 受信したパケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1705">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1705">Return Values</span></span>

- <span data-ttu-id="58df1-1706">**NX_SUCCESS** (0x00) 次の HTTP パケットを正常に受信しました</span><span class="sxs-lookup"><span data-stu-id="58df1-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="58df1-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) 次のパケットを待機している間に時間切れになりました</span><span class="sxs-lookup"><span data-stu-id="58df1-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="58df1-1708">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1709">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1709">Allowed From</span></span>

<span data-ttu-id="58df1-1710">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1711">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="58df1-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="58df1-1713">要求からパラメーターを取得する</span><span class="sxs-lookup"><span data-stu-id="58df1-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1714">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1715">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1715">Description</span></span>

<span data-ttu-id="58df1-1716">このサービスでは、指定された要求パケット内の指定された HTTP URL パラメーターを取得することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="58df1-1717">要求された HTTP パラメーターが存在しない場合、このルーチンでは NX_WEB_HTTP_NOT_FOUND という状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="58df1-1718">このルーチンは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1719">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1719">Input Parameters</span></span>

- <span data-ttu-id="58df1-1720">**packet_ptr** HTTP クライアントの要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="58df1-1721">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="58df1-1722">**param_number** パラメーター リストの左から右に向かって 0 から始まるパラメーターの論理番号。</span><span class="sxs-lookup"><span data-stu-id="58df1-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="58df1-1723">**param_ptr** パラメーターのコピー先領域。</span><span class="sxs-lookup"><span data-stu-id="58df1-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="58df1-1724">**param_size** パラメーター データの合計長 (バイト単位) が返されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="58df1-1725">**max_param_size** パラメーターのコピー先領域の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1726">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1726">Return Values</span></span>

- <span data-ttu-id="58df1-1727">**NX_SUCCESS** (0x00) HTTP Server のパラメーターが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="58df1-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) 指定されたパラメーターが見つかりません</span><span class="sxs-lookup"><span data-stu-id="58df1-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="58df1-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) 要求パラメーターが正しく終了されていません</span><span class="sxs-lookup"><span data-stu-id="58df1-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="58df1-1730">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1731">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1732">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1732">Allowed From</span></span>

<span data-ttu-id="58df1-1733">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1734">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="58df1-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="58df1-1736">要求からクエリを取得する</span><span class="sxs-lookup"><span data-stu-id="58df1-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1737">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1738">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1738">Description</span></span>

<span data-ttu-id="58df1-1739">このサービスでは、指定された要求パケット内の指定された HTTP URL クエリを取得することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="58df1-1740">要求された HTTP クエリが存在しない場合、このルーチンでは NX_WEB_HTTP_NOT_FOUND という状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="58df1-1741">このルーチンは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1742">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1742">Input Parameters</span></span>

- <span data-ttu-id="58df1-1743">**packet_ptr** HTTP クライアントの要求パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="58df1-1744">アプリケーションでこのパケットを解放しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="58df1-1745">**query_number** クエリ リストの左から右に向かって 0 から始まるクエリの論理番号。</span><span class="sxs-lookup"><span data-stu-id="58df1-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="58df1-1746">**query_ptr** クエリのコピー先領域。</span><span class="sxs-lookup"><span data-stu-id="58df1-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="58df1-1747">**query_size** クエリ データのサイズ (バイト単位) が返されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="58df1-1748">**max_query_size** クエリのコピー先の最大サイズ</span><span class="sxs-lookup"><span data-stu-id="58df1-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="58df1-1749">できます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1750">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1750">Return Values</span></span>

- <span data-ttu-id="58df1-1751">**NX_SUCCESS** (0x00) HTTP Server のクエリが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="58df1-1752">**NX_WEB_HTTP_FAILED** (0x30002) クエリのサイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="58df1-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) 指定されたクエリが見つかりません</span><span class="sxs-lookup"><span data-stu-id="58df1-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="58df1-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) クライアント要求内にクエリがありません</span><span class="sxs-lookup"><span data-stu-id="58df1-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="58df1-1755">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1756">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1757">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1757">Allowed From</span></span>

<span data-ttu-id="58df1-1758">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1759">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="58df1-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="58df1-1761">HTTP(S) 応答にチャンク転送を設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1762">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1763">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1763">Description</span></span>

<span data-ttu-id="58df1-1764">このサービスでは、*nx_web_http_server_response_packet_allocate*() で作成されたカスタム HTTP(S) 応答データ パケットが、チャンク転送コーディングを使用してクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1765">アプリケーションでチャンク転送コーディングを使用して応答データ パケットを送信する場合は、*nx_web_http_server_response_packet_allocate*() を呼び出した後にこのサービスを呼び出し、その後、*nx_web_http_server_callback_packet_send*() を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1766">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1766">Input Parameters</span></span>

- <span data-ttu-id="58df1-1767">**client_ptr** HTTP Client の制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="58df1-1768">**chunk_size** チャンクデータのサイズ (オクテット単位)。</span><span class="sxs-lookup"><span data-stu-id="58df1-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="58df1-1769">**packet_ptr** HTTP(S) 要求データ パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1770">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1770">Return Values</span></span>

- <span data-ttu-id="58df1-1771">**NX_SUCCESS** (0x00) チャンクが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="58df1-1772">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1773">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1773">Allowed From</span></span>

<span data-ttu-id="58df1-1774">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1775">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="58df1-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="58df1-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="58df1-1777">HTTPS をセキュリティで保護するために TLS を使用するように HTTP Server を構成する</span><span class="sxs-lookup"><span data-stu-id="58df1-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1778">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1778">Prototype</span></span>

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1779">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1779">Description</span></span>

<span data-ttu-id="58df1-1780">このサービスでは、セキュリティで保護された HTTPS 通信にするために TLS を使用するように、以前に作成された NetX Web HTTP Server インスタンスが構成されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="58df1-1781">使用されるすべての TLS セッションを同じ状態に構成するためにパラメーターが使用され、各受信 HTTPS Client が一貫した動作で実行されるようになります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="58df1-1782">TLS セッションの数は、マクロ NX_WEB_HTTP_SESSION_MAX を使用して制御されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="58df1-1783">暗号化ルーチン テーブル (暗号スイート テーブル) は、関数ポインターが含まれているだけなので、すべての TLS セッション間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="58df1-1784">メタデータ バッファーとパケット再構築バッファーはそれぞれ、すべての TLS セッション間で均等に分割されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="58df1-1785">バッファー サイズがセッション数で均等に割り切れない場合、残りは使用されません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="58df1-1786">渡された ID 証明書は、すべてのセッションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="58df1-1787">TLS 操作中は、サーバー ID 証明書のみが読み取られるため、セッションごとにコピーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="58df1-1788">信頼された証明書は、HTTPS Server の各 TLS セッションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="58df1-1789">これらは、リモート証明書の領域が提供されている場合に自動的に有効になるクライアント証明書の認証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="58df1-1790">リモート証明書の配列とバッファーは、既定ですべての TLS セッション間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="58df1-1791">リモート証明書は、クライアント証明書の認証に使用されます。これは、リモート証明書の数が 0 以外の場合に自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="58df1-1792">バッファーは共有されているため、証明書の検証中に一部のセッションがブロックされることがあります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="58df1-1793">クライアント証明書の認証を無効にするには、remote_certificates パラメーターに NX_NULL、remote_certs_num パラメーターに値 0 を渡します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="58df1-1794">戻り値には、TLS セッションの構成で発生した問題の結果として得られる TLS エラー コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1795">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1795">Input Parameters</span></span>

- <span data-ttu-id="58df1-1796">**http_server_ptr** HTTP Server インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="58df1-1797">**crypto_table** TLS 暗号スイート テーブルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="58df1-1798">**metadata_buffer** 暗号化メタデータ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="58df1-1799">**metadata_size** 暗号化メタデータ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="58df1-1800">**packet_buffer** TLS パケット再構築バッファー。</span><span class="sxs-lookup"><span data-stu-id="58df1-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="58df1-1801">**packet_buffer** TLS パケット バッファーのサイズ – (<必要な TLS バッファーのサイズ \* NX_WEB_HTTP_SESSION_MAX) と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="58df1-1802">**identity_certificate** TLS サーバー ID 証明書 – すべての HTTPS Server セッションに使用されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="58df1-1803">**trusted_certificates** *Remote_certs_num* パラメーターに 0 以外の値を渡すことによってクライアント証明書の認証が有効になっている場合に、受信クライアント証明書を検証するために使用される NX_SECURE_X509_CERT オブジェクトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="58df1-1804">**trusted_certs_num** *Trusted_certificates* 配列内の信頼された証明書の数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="58df1-1805">**remote_certificates** 受信クライアント証明書に使用される NX_SECURE_X509_CERT オブジェクトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="58df1-1806">**remote_certs_num** リモート証明書の数。</span><span class="sxs-lookup"><span data-stu-id="58df1-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="58df1-1807">クライアントからの予想される証明書の最大数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="58df1-1808">この値が 0 以外の場合、クライアント証明書の認証が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="58df1-1809">**remote_certificate_buffer** クライアント証明書の認証が有効になっている場合に、クライアントからの受信リモート証明書が格納されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="58df1-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="58df1-1810">remote_cert_buffer_size リモート証明書のバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="58df1-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="58df1-1811">(<予想される証明書の最大サイズ \* remote_certs_num) と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="58df1-1812">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1812">Return Values</span></span>

- <span data-ttu-id="58df1-1813">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="58df1-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="58df1-1814">**NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="58df1-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** （0x102） 受信した TLS メッセージの種類が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="58df1-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** （0x106） リモート ホストによって提供された暗号はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="58df1-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS ハンドシェイク中のメッセージの処理に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="58df1-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 受信メッセージのハッシュ MAC チェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="58df1-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) 基になる TCP ソケットの送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="58df1-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 受信メッセージに無効な長さのフィールドがありました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="58df1-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) 受信 ChangeCipherSpec メッセージが正しくありませんでした。</span><span class="sxs-lookup"><span data-stu-id="58df1-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="58df1-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) 受信 TLS 証明書を、リモート TLS サーバーの識別に使用できません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="58df1-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) リモート ホストによって提供された公開キー暗号はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="58df1-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="58df1-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** （0x10E） リモート ホストは、NetX Secure TLS スタックによってサポートされている暗号スイートがないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="58df1-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="58df1-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信した TLS メッセージのヘッダーに不明な TLS バージョンがありました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="58df1-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** （0x110） 受信した TLS メッセージのヘッダーに既知だがサポートされていない TLS バージョンがありました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="58df1-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 内部 TLS パケットの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="58df1-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） リモート ホストが無効な証明書を提供しました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="58df1-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) リモート ホストによって、エラーを通知して TLS セッションを終了するアラートが送信されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="58df1-1830">**NX_PTR_ERROR** (0x07) 無効なポインターを使用することが試みられました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1831">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1831">Allowed From</span></span>

<span data-ttu-id="58df1-1832">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="58df1-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1833">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1833">Example</span></span>

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a><span data-ttu-id="58df1-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="58df1-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="58df1-1835">HTTP Server を開始する</span><span class="sxs-lookup"><span data-stu-id="58df1-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1836">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1837">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1837">Description</span></span>

<span data-ttu-id="58df1-1838">このサービスでは、以前に作成された HTTP または HTTPS Server インスタンスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="58df1-1839">HTTPS Server では、HTTP と同じ API が共有されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="58df1-1840">HTTP Server で TLS を使用して HTTPS を有効にする方法については、サービス *nx_web_http_server_secure_configure()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1841">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1841">Input Parameters</span></span>

- <span data-ttu-id="58df1-1842">**http_server_ptr** HTTP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1843">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1843">Return Values</span></span>

- <span data-ttu-id="58df1-1844">**NX_SUCCESS** (0x00) HTTP Server が正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="58df1-1845">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1846">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1846">Allowed From</span></span>

<span data-ttu-id="58df1-1847">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="58df1-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1848">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="58df1-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="58df1-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="58df1-1850">HTTP Server を停止する</span><span class="sxs-lookup"><span data-stu-id="58df1-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1851">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="58df1-1852">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1852">Description</span></span>

<span data-ttu-id="58df1-1853">このサービスは、以前に作成された HTTP サーバー インスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="58df1-1854">このルーチンは、HTTP サーバー インスタンスを削除する前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1855">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1855">Input Parameters</span></span>

- <span data-ttu-id="58df1-1856">**http_server_ptr** HTTP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1857">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1857">Return Values</span></span>

- <span data-ttu-id="58df1-1858">**NX_SUCCESS** (0x00) HTTP Server が正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="58df1-1859">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1860">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1861">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1861">Allowed From</span></span>

<span data-ttu-id="58df1-1862">Threads</span><span class="sxs-lookup"><span data-stu-id="58df1-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1863">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="58df1-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="58df1-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="58df1-1865">クライアントの HTTP 要求からファイルの種類を抽出する</span><span class="sxs-lookup"><span data-stu-id="58df1-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1866">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1867">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="58df1-1868">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1868">This service is deprecated.</span></span> <span data-ttu-id="58df1-1869">ユーザーには、サービス *nx_web_http_server_type_get_extended()* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58df1-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="58df1-1870">このサービスでは、入力バッファー *name* (通常は URL) から HTTP 要求の種類がバッファー *http_type_string* に、その長さが *string_size* に抽出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="58df1-1871">MIME マップが見つからない場合、既定では種類に "text/plain" が設定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="58df1-1872">それ以外の場合、抽出された種類を HTTP Server の既定の MIME マップと比較して、一致するものが見つけられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="58df1-1873">NetX Web HTTP Server の既定の MIME マップは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="58df1-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="58df1-1874">html text/html</span><span class="sxs-lookup"><span data-stu-id="58df1-1874">html text/html</span></span>
- <span data-ttu-id="58df1-1875">htm text/html</span><span class="sxs-lookup"><span data-stu-id="58df1-1875">htm text/html</span></span>
- <span data-ttu-id="58df1-1876">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="58df1-1876">txt text/plain</span></span>
- <span data-ttu-id="58df1-1877">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="58df1-1877">gif image/gif</span></span>
- <span data-ttu-id="58df1-1878">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="58df1-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="58df1-1879">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="58df1-1879">ico image/x-icon</span></span>

<span data-ttu-id="58df1-1880">指定した場合は、ユーザーが定義した一連の追加の MIME マップも検索されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="58df1-1881">ユーザー定義マップの詳細については、*nx_web_http_server_mime_maps_addtional_set()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1882">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1882">Input Parameters</span></span>

- <span data-ttu-id="58df1-1883">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="58df1-1884">**name** 検索するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="58df1-1885">**http_type_string** 抽出される HTML の種類の文字列へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="58df1-1886">**string_size** 抽出された HTML の種類の文字列長を返すためのポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1887">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1887">Return Values</span></span>

- <span data-ttu-id="58df1-1888">**NX_SUCCESS** (0x00) 種類が正常に抽出されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="58df1-1889">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 既定の "text/plain" が返されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1891">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1891">Allowed From</span></span>

<span data-ttu-id="58df1-1892">Application</span><span class="sxs-lookup"><span data-stu-id="58df1-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1893">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1893">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="58df1-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="58df1-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="58df1-1895">クライアントの HTTP 要求からファイルの種類を抽出する</span><span class="sxs-lookup"><span data-stu-id="58df1-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1896">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="58df1-1897">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1897">Description</span></span>

<span data-ttu-id="58df1-1898">このサービスでは、入力バッファー *name* (通常は URL) から HTTP 要求の種類がバッファー *http_type_string* に、その長さが *string_size* に抽出されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="58df1-1899">MIME マップが見つからない場合、既定では種類に "text/plain" が設定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="58df1-1900">それ以外の場合、抽出された種類を HTTP Server の既定の MIME マップと比較して、一致するものが見つけられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="58df1-1901">NetX Web HTTP Server の既定の MIME マップは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="58df1-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="58df1-1902">html text/html</span><span class="sxs-lookup"><span data-stu-id="58df1-1902">html text/html</span></span>
- <span data-ttu-id="58df1-1903">htm text/html</span><span class="sxs-lookup"><span data-stu-id="58df1-1903">htm text/html</span></span>
- <span data-ttu-id="58df1-1904">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="58df1-1904">txt text/plain</span></span>
- <span data-ttu-id="58df1-1905">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="58df1-1905">gif image/gif</span></span>
- <span data-ttu-id="58df1-1906">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="58df1-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="58df1-1907">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="58df1-1907">ico image/x-icon</span></span>

<span data-ttu-id="58df1-1908">指定した場合は、ユーザーが定義した一連の追加の MIME マップも検索されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="58df1-1909">ユーザー定義マップの詳細については、*nx_web_http_server_mime_maps_addtional_set()* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58df1-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="58df1-1910">このサービスによって *nx_web_http_server_type_get*() が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="58df1-1911">このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58df1-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1912">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1912">Input Parameters</span></span>

- <span data-ttu-id="58df1-1913">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="58df1-1914">**name** 検索するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="58df1-1915">**name_length** 名前の長さ</span><span class="sxs-lookup"><span data-stu-id="58df1-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="58df1-1916">**http_type_string** 抽出される HTML の種類の文字列へのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="58df1-1917">**http_type_string_max_size** http_type_string バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="58df1-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="58df1-1918">**string_size** 抽出される HTML の種類の文字列長を返すための</span><span class="sxs-lookup"><span data-stu-id="58df1-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="58df1-1919">ポインター。</span><span class="sxs-lookup"><span data-stu-id="58df1-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1920">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1920">Return Values</span></span>

- <span data-ttu-id="58df1-1921">**NX_SUCCESS** (0x00) 種類が正常に抽出されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="58df1-1922">NX_PTR_ERROR: (0x07) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 既定の "text/plain" が返されました。</span><span class="sxs-lookup"><span data-stu-id="58df1-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1924">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1924">Allowed From</span></span>

<span data-ttu-id="58df1-1925">Application</span><span class="sxs-lookup"><span data-stu-id="58df1-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1926">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1926">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="58df1-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="58df1-1928">ダイジェスト認証のコールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1929">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1929">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a><span data-ttu-id="58df1-1930">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1930">Description</span></span>

<span data-ttu-id="58df1-1931">このサービスは、ダイジェスト認証の実行時に呼び出されるコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="58df1-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1932">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1932">Input Parameters</span></span>

- <span data-ttu-id="58df1-1933">**http_server_ptr** HTTP サーバー インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="58df1-1934">**digest_authenticate_callback** ダイジェスト認証コールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1935">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1935">Return Values</span></span>

- <span data-ttu-id="58df1-1936">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="58df1-1937">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="58df1-1938">NX_NOT_SUPPORTED (0x4B) ダイジェスト認証が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="58df1-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1939">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1939">Allowed From</span></span>

<span data-ttu-id="58df1-1940">Application</span><span class="sxs-lookup"><span data-stu-id="58df1-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1941">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1941">Example</span></span>

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="58df1-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="58df1-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="58df1-1943">ダイジェスト認証のコールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="58df1-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="58df1-1944">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="58df1-1944">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a><span data-ttu-id="58df1-1945">説明</span><span class="sxs-lookup"><span data-stu-id="58df1-1945">Description</span></span>

<span data-ttu-id="58df1-1946">このサービスでは、認証チェックの実行時に呼び出されるコールバックが設定されます。</span><span class="sxs-lookup"><span data-stu-id="58df1-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="58df1-1947">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="58df1-1947">Input Parameters</span></span>

- <span data-ttu-id="58df1-1948">**http_server_ptr** HTTP Server インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="58df1-1949">**authenticate_check_externded** 認証チェックのコールバックへのポインター</span><span class="sxs-lookup"><span data-stu-id="58df1-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="58df1-1950">戻り値</span><span class="sxs-lookup"><span data-stu-id="58df1-1950">Return Values</span></span>

- <span data-ttu-id="58df1-1951">**NX_SUCCESS** (0x00) コールバックが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="58df1-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="58df1-1952">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="58df1-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="58df1-1953">許可元</span><span class="sxs-lookup"><span data-stu-id="58df1-1953">Allowed From</span></span>

<span data-ttu-id="58df1-1954">Application</span><span class="sxs-lookup"><span data-stu-id="58df1-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="58df1-1955">例</span><span class="sxs-lookup"><span data-stu-id="58df1-1955">Example</span></span>

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
