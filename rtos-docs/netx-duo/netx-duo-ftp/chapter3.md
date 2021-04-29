---
title: 章 3 章 - FTP サービスの説明
description: この章では、NetX FTP のすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810796"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="91c98-103">章 3 章 - FTP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="91c98-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="91c98-104">この章では、NetX FTP のすべてのサービス (下記参照) をアルファベット順に示します (ただし、同じサービスの IPv4 と IPv6 に対応するものがペアになっている場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="91c98-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="91c98-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="91c98-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="91c98-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="91c98-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="91c98-107">IPv4 経由で FTP サーバーに接続します</span><span class="sxs-lookup"><span data-stu-id="91c98-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-109">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-109">Description</span></span>

<span data-ttu-id="91c98-110">このサービスを使用すると、以前に作成した NetX FTP クライアント インスタンスが、指定した IP アドレスの FTP サーバーに接続されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-111">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-111">Input Parameters</span></span>

- <span data-ttu-id="91c98-112">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-113">**server_ip** FTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="91c98-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="91c98-114">**username** 認証用のクライアント ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="91c98-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="91c98-115">**password** 認証用のクライアント パスワード。</span><span class="sxs-lookup"><span data-stu-id="91c98-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="91c98-116">**wait_option** FTP クライント接続をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="91c98-117">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-118">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-120">Return Values</span></span>

- <span data-ttu-id="91c98-121">**NX_SUCCESS** (0x00) FTP 接続に成功しました。</span><span class="sxs-lookup"><span data-stu-id="91c98-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="91c98-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) 22X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="91c98-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) 23X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="91c98-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) 33X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="91c98-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) クライアントは既に接続されています。</span><span class="sxs-lookup"><span data-stu-id="91c98-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="91c98-126">NX_PTR_ERROR (0x07) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="91c98-127">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="91c98-128">NX_IP_ADDRESS_ERROR (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-129">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-129">Allowed From</span></span>

<span data-ttu-id="91c98-130">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-131">例</span><span class="sxs-lookup"><span data-stu-id="91c98-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="91c98-132">参照</span><span class="sxs-lookup"><span data-stu-id="91c98-132">See Also</span></span>

<span data-ttu-id="91c98-133">nx_ftp_client_create、nx_ftp_client_delete、nx_ftp_client_directory_create、nx_ftp_client_disconnect、nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="91c98-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="91c98-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="91c98-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="91c98-135">IPv6 のサポートを使用して FTP サーバーに接続します</span><span class="sxs-lookup"><span data-stu-id="91c98-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-136">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-137">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-137">Description</span></span>

<span data-ttu-id="91c98-138">このサービスを使用すると、以前に作成した NetX Duo FTP クライアント インスタンスが、指定した IP アドレスの FTP サーバーに接続されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="91c98-139">IPv4 と IPv6 の両方のネットワークがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="91c98-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-140">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-140">Input Parameters</span></span>

- <span data-ttu-id="91c98-141">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-142">**server_ipduo** FTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="91c98-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="91c98-143">**username** 認証用のクライアント ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="91c98-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="91c98-144">**password** 認証用のクライアント パスワード。</span><span class="sxs-lookup"><span data-stu-id="91c98-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="91c98-145">**wait_option** FTP クライント接続をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="91c98-146">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-147">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-149">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-149">Return Values</span></span>

- <span data-ttu-id="91c98-150">**NX_SUCCESS** (0x00) FTP 接続に成功しました。</span><span class="sxs-lookup"><span data-stu-id="91c98-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="91c98-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) 22X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="91c98-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) 23X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="91c98-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) 33X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="91c98-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) クライアントは既に接続されています</span><span class="sxs-lookup"><span data-stu-id="91c98-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="91c98-155">NX_PTR_ERROR (0x07) ポインター入出力が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="91c98-156">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="91c98-157">NX_IP_ADDRESS_ERROR (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-158">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-158">Allowed From</span></span>

<span data-ttu-id="91c98-159">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-160">例</span><span class="sxs-lookup"><span data-stu-id="91c98-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="91c98-161">参照</span><span class="sxs-lookup"><span data-stu-id="91c98-161">See Also</span></span>

<span data-ttu-id="91c98-162">nx_ftp_client_create、nx_ftp_client_delete、nx_ftp_client_directory_create、nx_ftp_client_disconnect、nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="91c98-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="91c98-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="91c98-163">nx_ftp_client_create</span></span>

<span data-ttu-id="91c98-164">FTP クライアント インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="91c98-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-165">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="91c98-166">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-166">Description</span></span>

<span data-ttu-id="91c98-167">このサービスを使用すると、FTP クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-168">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-168">Input Parameters</span></span>

- <span data-ttu-id="91c98-169">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-170">**ftp_client_name** FTP クライアントの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="91c98-171">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="91c98-172">**window_size** この FTP クライアントの TCP ソケットのアドバタイズされたウィンドウ サイズ。</span><span class="sxs-lookup"><span data-stu-id="91c98-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="91c98-173">**pool_ptr** この FTP クライアントの既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="91c98-174">最小パケット ペイロードは、完全なパスとファイルまたはディレクトリ名を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-175">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-175">Return Values</span></span>

- <span data-ttu-id="91c98-176">**NX_SUCCESS** (0x00) FTP クライアントが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="91c98-177">NX_PTR_ERROR (0x07) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-178">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-178">Allowed From</span></span>

<span data-ttu-id="91c98-179">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="91c98-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-180">例</span><span class="sxs-lookup"><span data-stu-id="91c98-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="91c98-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="91c98-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="91c98-182">FTP クライアント インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="91c98-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-183">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="91c98-184">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-184">Description</span></span>

<span data-ttu-id="91c98-185">このサービスを使用すると、FTP クライアント インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-186">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-186">Input Parameters</span></span>

- <span data-ttu-id="91c98-187">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-188">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-188">Return Values</span></span>

- <span data-ttu-id="91c98-189">**NX_SUCCESS** (0x00) FTP クライアントが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="91c98-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP クライアントが切断されていません</span><span class="sxs-lookup"><span data-stu-id="91c98-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="91c98-191">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-192">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-193">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-193">Allowed From</span></span>

<span data-ttu-id="91c98-194">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-195">例</span><span class="sxs-lookup"><span data-stu-id="91c98-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="91c98-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="91c98-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="91c98-197">FTP サーバーにディレクトリを作成します</span><span class="sxs-lookup"><span data-stu-id="91c98-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-198">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-199">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-199">Description</span></span>

<span data-ttu-id="91c98-200">このサービスを使用すると、指定した FTP クライアントに接続されている FTP サーバー上に、指定したディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-201">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-201">Input Parameters</span></span>

- <span data-ttu-id="91c98-202">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-203">**directory_name** 作成するディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="91c98-204">**wait_option** FTP ディレクトリの作成をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="91c98-205">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-206">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-208">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-208">Return Values</span></span>

- <span data-ttu-id="91c98-209">**NX_SUCCESS** (0x00) FTP ディレクトリトが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="91c98-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-212">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-213">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-214">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-214">Allowed From</span></span>

<span data-ttu-id="91c98-215">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-216">例</span><span class="sxs-lookup"><span data-stu-id="91c98-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="91c98-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="91c98-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="91c98-218">FTP サーバーに既定のディレクトリを設定します</span><span class="sxs-lookup"><span data-stu-id="91c98-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-219">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-220">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-220">Description</span></span>

<span data-ttu-id="91c98-221">このサービスを使用すると、指定した FTP クライアントに接続されている FTP サーバーに、既定のディレクトリが設定されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="91c98-222">この既定のディレクトリは、このクライアントの接続にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-223">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-223">Input Parameters</span></span>

- <span data-ttu-id="91c98-224">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-225">**directory_path** 設定するディレクトリ パスの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="91c98-226">**wait_option** FTP の既定のディレクトリの設定をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="91c98-227">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-228">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-230">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-230">Return Values</span></span>

- <span data-ttu-id="91c98-231">**NX_SUCCESS** (0x00) FTP の既定の設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="91c98-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="91c98-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-234">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-235">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-236">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-236">Allowed From</span></span>

<span data-ttu-id="91c98-237">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-238">例</span><span class="sxs-lookup"><span data-stu-id="91c98-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="91c98-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="91c98-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="91c98-240">FTP サーバー上のディレクトリを削除します</span><span class="sxs-lookup"><span data-stu-id="91c98-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-241">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-242">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-242">Description</span></span>

<span data-ttu-id="91c98-243">このサービスを使用すると、指定した FTP クライアントに接続されている FTP サーバー上の指定したディレクトリが削除されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-244">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-244">Input Parameters</span></span>

- <span data-ttu-id="91c98-245">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-246">**directory_name** 削除するディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="91c98-247">**wait_option** FTP ディレクトリの削除をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="91c98-248">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-249">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-251">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-251">Return Values</span></span>

- <span data-ttu-id="91c98-252">**NX_SUCCESS** (0x00) FTP ディレクトリトが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="91c98-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-255">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-256">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-257">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-257">Allowed From</span></span>

<span data-ttu-id="91c98-258">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-259">例</span><span class="sxs-lookup"><span data-stu-id="91c98-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="91c98-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="91c98-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="91c98-261">FTP サーバーからディレクトリの一覧を取得します</span><span class="sxs-lookup"><span data-stu-id="91c98-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-262">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-263">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-263">Description</span></span>

<span data-ttu-id="91c98-264">このサービスを使用すると、指定した FTP クライアントに接続されている FTP サーバー上の指定したディレクトリのコンテンツが取得されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="91c98-265">指定したパケット ポインターには、1 つ以上のディレクトリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="91c98-266">各エントリは、\<cr/lf\> の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="91c98-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="91c98-267">ディレクトリの取得操作を完了するには、***nx_ftp_client_directory_listing_continue*** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c98-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-268">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-268">Input Parameters</span></span>

- <span data-ttu-id="91c98-269">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-270">**directory_name** コンテンツを取得するディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="91c98-271">**packet_ptr** 格納先パケット ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="91c98-272">成功した場合、パケット ペイロードには 1 つ以上のディレクトリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="91c98-273">**wait_option** FTP ディレクトリの一覧をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="91c98-274">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-275">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-277">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-277">Return Values</span></span>

- <span data-ttu-id="91c98-278">**NX_SUCCESS** (0x00) FTP ディレクトリトが正常に一覧されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="91c98-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-280">**NX_NOT_ENABLED** (0x14) サービス (IPv6) が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="91c98-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="91c98-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) 1XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="91c98-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-283">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-284">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-285">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-285">Allowed From</span></span>

<span data-ttu-id="91c98-286">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-287">例</span><span class="sxs-lookup"><span data-stu-id="91c98-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="91c98-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="91c98-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="91c98-289">FTP サーバーからのディレクトリの一覧取得を続行します</span><span class="sxs-lookup"><span data-stu-id="91c98-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-290">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-291">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-291">Description</span></span>

<span data-ttu-id="91c98-292">このサービスを使用すると、指定した FTP クライアントに接続されている FTP サーバー上の指定したディレクトリのコンテンツの取得が続行されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="91c98-293">直前に ***nx_ftp_client_directory_listing_get*** の呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="91c98-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="91c98-294">成功した場合、指定したパケット ポインターに、1 つ以上のディレクトリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="91c98-295">NX_FTP_END_OF_LISTING の状態を受け取るまで、このルーチンを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c98-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-296">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-296">Input Parameters</span></span>

- <span data-ttu-id="91c98-297">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-298">**packet_ptr** 格納先パケット ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="91c98-299">成功した場合、パケット ペイロードには、<cr/lf> で区切られた 1 つ以上のディレクトリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="91c98-300">**wait_option** FTP ディレクトリの一覧をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="91c98-301">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-302">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-304">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-304">Return Values</span></span>

- <span data-ttu-id="91c98-305">**NX_SUCCESS** (0x00) FTP ディレクトリトが正常に一覧されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="91c98-306">**NX_FTP_END_OF_LISTING** (0xD8) このディレクトリにはこれ以上エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="91c98-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="91c98-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-309">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-310">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-311">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-311">Allowed From</span></span>

<span data-ttu-id="91c98-312">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-313">例</span><span class="sxs-lookup"><span data-stu-id="91c98-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="91c98-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="91c98-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="91c98-315">FTP サーバーから切断します</span><span class="sxs-lookup"><span data-stu-id="91c98-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-316">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-317">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-317">Description</span></span>

<span data-ttu-id="91c98-318">このサービスを使用すると、指定した FTP クライアントとの間に以前に確立された FTP サーバー接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-319">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-319">Input Parameters</span></span>

- <span data-ttu-id="91c98-320">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-321">**wait_option** FTP クライントの切断をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="91c98-322">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-323">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-325">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-325">Return Values</span></span>

- <span data-ttu-id="91c98-326">**NX_SUCCESS** (0x00) FTP の切断に成功しました。</span><span class="sxs-lookup"><span data-stu-id="91c98-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="91c98-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-329">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-330">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-331">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-331">Allowed From</span></span>

<span data-ttu-id="91c98-332">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-333">例</span><span class="sxs-lookup"><span data-stu-id="91c98-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="91c98-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="91c98-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="91c98-335">クライアント ファイルを閉じます</span><span class="sxs-lookup"><span data-stu-id="91c98-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-336">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-337">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-337">Description</span></span>

<span data-ttu-id="91c98-338">このサービスを使用すると、FTP サーバーで前に開いたファイルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="91c98-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-339">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-339">Input Parameters</span></span>

- <span data-ttu-id="91c98-340">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-341">**wait_option** FTP クライントのファイルが閉じられるをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="91c98-342">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-343">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-345">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-345">Return Values</span></span>

- <span data-ttu-id="91c98-346">**NX_SUCCESS** (0x00) FTP ファイルが正常に閉じられました。</span><span class="sxs-lookup"><span data-stu-id="91c98-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="91c98-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-348">**NX_FTP_NOT_OPEN (0xD5)** ファイルが開かれていません。閉じることができません</span><span class="sxs-lookup"><span data-stu-id="91c98-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="91c98-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-350">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-351">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-352">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-352">Allowed From</span></span>

<span data-ttu-id="91c98-353">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-354">例</span><span class="sxs-lookup"><span data-stu-id="91c98-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="91c98-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="91c98-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="91c98-356">FTP サーバー上のファイルを削除します</span><span class="sxs-lookup"><span data-stu-id="91c98-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-357">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-358">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-358">Description</span></span>

<span data-ttu-id="91c98-359">このサービスを使用すると、FTP サーバー上の指定したファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-360">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-360">Input Parameters</span></span>

- <span data-ttu-id="91c98-361">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-362">**file_name** 削除するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="91c98-363">**wait_option** FTP クライントのファイルの削除をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="91c98-364">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-365">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-367">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-367">Return Values</span></span>

- <span data-ttu-id="91c98-368">**NX_SUCCESS** (0x00) FTP ファイルが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="91c98-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-371">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-372">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-373">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-373">Allowed From</span></span>

<span data-ttu-id="91c98-374">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-375">例</span><span class="sxs-lookup"><span data-stu-id="91c98-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="91c98-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="91c98-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="91c98-377">FTP サーバー上のファイルを開きます</span><span class="sxs-lookup"><span data-stu-id="91c98-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-378">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-379">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-379">Description</span></span>

<span data-ttu-id="91c98-380">このサービスを使用すると、指定したクライアント インスタンスに以前に接続された FTP サーバー上の指定したファイルが (読み取りまたは書き込み用に) 開かれます。</span><span class="sxs-lookup"><span data-stu-id="91c98-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-381">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-381">Input Parameters</span></span>

- <span data-ttu-id="91c98-382">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-383">**file_name** 開くファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="91c98-384">**open_type** **NX_FTP_OPEN_FOR_READ** または **NX_FTP_OPEN_FOR_WRITE**。</span><span class="sxs-lookup"><span data-stu-id="91c98-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="91c98-385">**wait_option** FTP クライントのファイルが開かれるのをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="91c98-386">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-387">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-389">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-389">Return Values</span></span>

- <span data-ttu-id="91c98-390">**NX_SUCCESS** (0x00) FTP ファイルが正常に開かれました。</span><span class="sxs-lookup"><span data-stu-id="91c98-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="91c98-391">**NX_OPTION_ERROR**  (0x0A) オープンの種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="91c98-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP クライアントは既に開かれています。</span><span class="sxs-lookup"><span data-stu-id="91c98-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="91c98-394">**NX_NO_FREE_PORTS** (0x45) 割り当てることのできる TCP ポートがありません</span><span class="sxs-lookup"><span data-stu-id="91c98-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="91c98-395">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-396">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-397">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-397">Allowed From</span></span>

<span data-ttu-id="91c98-398">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-399">例</span><span class="sxs-lookup"><span data-stu-id="91c98-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="91c98-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="91c98-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="91c98-401">ファイルから読み取ります</span><span class="sxs-lookup"><span data-stu-id="91c98-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-402">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-403">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-403">Description</span></span>

<span data-ttu-id="91c98-404">このサービスを使用すると、前に開いたファイルからパケットが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="91c98-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="91c98-405">NX_FTP_END_OF_FILE の状態が受信されるまで繰り返し呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c98-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="91c98-406">このサービスのパケットは、呼び出し元で割り当てるのではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="91c98-407">指定する必要があるのはパケット ポインターへのポインターだけです。</span><span class="sxs-lookup"><span data-stu-id="91c98-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="91c98-408">このサービスにより、ソケット受信キューから取得されたパケットを指すようにそのパケット ポインターが更新されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="91c98-409">正常状態が返された場合は、パケットが使用可能であったことを意味します。また、終了時にパケットを解放するのは呼び出し元の責任です。</span><span class="sxs-lookup"><span data-stu-id="91c98-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="91c98-410">0 以外の状態 (エラー状態または NX_FTP_END_OF_FILE) が返された場合は、パケットの解放は呼び出し元では行いません。</span><span class="sxs-lookup"><span data-stu-id="91c98-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="91c98-411">それ以外の場合は、パケット ポインターが NULL の場合にエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-412">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-412">Input Parameters</span></span>

- <span data-ttu-id="91c98-413">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-414">**packet_ptr** 格納されるデータ パケット ポインターの格納先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="91c98-415">成功した場合、パケットには一部または全部のファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="91c98-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="91c98-416">**wait_option** FTP クライントのファイルの読み取りをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="91c98-417">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-418">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-420">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-420">Return Values</span></span>

- <span data-ttu-id="91c98-421">**NX_SUCCESS** (0x00) FTP ファイルが正常に読み取られました。</span><span class="sxs-lookup"><span data-stu-id="91c98-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="91c98-422">**NX_FTP_NOT_OPEN** (0xD5) FTP クライアントが開かれていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="91c98-423">**NX_FTP_END_OF_FILE** (0xD7) ファイルの終わりの状態。</span><span class="sxs-lookup"><span data-stu-id="91c98-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="91c98-424">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-425">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-426">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-426">Allowed From</span></span>

<span data-ttu-id="91c98-427">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-428">例</span><span class="sxs-lookup"><span data-stu-id="91c98-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="91c98-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="91c98-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="91c98-430">FTP サーバー上のファイルの名前を変更します</span><span class="sxs-lookup"><span data-stu-id="91c98-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-431">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-432">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-432">Description</span></span>

<span data-ttu-id="91c98-433">このサービスを使用すると、FTP サーバー上のファイルの名前が変更されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-434">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-434">Input Parameters</span></span>

- <span data-ttu-id="91c98-435">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-436">**filename** ファイルの現在の名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="91c98-437">**new_filename** ファイルの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="91c98-438">**wait_option** FTP クライントのファイル名の変更をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="91c98-439">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-440">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-442">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-442">Return Values</span></span>

- <span data-ttu-id="91c98-443">**NX_SUCCESS** (0x00) FTP ファイルの名前が正常に変更されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="91c98-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="91c98-445">**NX_FTP_EXPECTED_3XX_CODE** (0xDD) 3XX (ok) 応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="91c98-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="91c98-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="91c98-447">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-448">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-449">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-449">Allowed From</span></span>

<span data-ttu-id="91c98-450">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-451">例</span><span class="sxs-lookup"><span data-stu-id="91c98-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="91c98-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="91c98-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="91c98-453">ファイルに書き込みます</span><span class="sxs-lookup"><span data-stu-id="91c98-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-454">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="91c98-455">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-455">Description</span></span>

<span data-ttu-id="91c98-456">このサービスを使用すると、FTP サーバーで前に開いたファイルにデータのパケットが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="91c98-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-457">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-457">Input Parameters</span></span>

- <span data-ttu-id="91c98-458">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-459">**packet_ptr** 書き込むデータが格納されているパケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="91c98-460">**wait_option** FTP クライントのファイルの書き込みをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="91c98-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="91c98-461">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="91c98-462">**タイムアウトの値** (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、FTP サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="91c98-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="91c98-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-464">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-464">Return Values</span></span>

- <span data-ttu-id="91c98-465">**NX_SUCCESS** (0x00) FTP ファイルが正常に書き込まれました。</span><span class="sxs-lookup"><span data-stu-id="91c98-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="91c98-466">**NX_FTP_NOT_OPEN** (0xD5) FTP クライアントが開かれていません。</span><span class="sxs-lookup"><span data-stu-id="91c98-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="91c98-467">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-468">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-469">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-469">Allowed From</span></span>

<span data-ttu-id="91c98-470">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-471">例</span><span class="sxs-lookup"><span data-stu-id="91c98-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="91c98-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="91c98-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="91c98-473">パッシブ転送モードを有効または無効にします</span><span class="sxs-lookup"><span data-stu-id="91c98-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-474">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="91c98-475">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-475">Description</span></span>

<span data-ttu-id="91c98-476">このサービスを使用すると、以前に作成した FTP クライアント インスタンスで passive_mode_enabled 入力が NX_TRUE に設定されている場合、パッシブ転送モードが有効になります。これにより、ファイルの読み取りや書き込み (RETR、STOR) またはディレクトリ一覧のダウンロード (NLST) に対する後続の呼び出しは、転送モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="91c98-477">パッシブ モードの転送を無効にして、アクティブ転送モードの既定の動作に戻すには、passive_mode_enabled 入力を NX_FALSE に設定して、この関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="91c98-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-478">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-478">Input Parameters</span></span>

- <span data-ttu-id="91c98-479">**ftp_client_ptr** FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="91c98-480">**passive_mode_enabled** NX_TRUE に設定すると、パッシブ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="91c98-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="91c98-481">NX_FALSE に設定すると、パッシブ モードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="91c98-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-482">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-482">Return Values</span></span>

- <span data-ttu-id="91c98-483">**NX_SUCCESS** (0x00) パッシブ モードの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="91c98-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="91c98-484">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-485">NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="91c98-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-486">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-486">Allowed From</span></span>

<span data-ttu-id="91c98-487">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-488">例</span><span class="sxs-lookup"><span data-stu-id="91c98-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="91c98-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="91c98-489">nx_ftp_server_create</span></span>

<span data-ttu-id="91c98-490">FTP サーバーを作成します</span><span class="sxs-lookup"><span data-stu-id="91c98-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-491">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="91c98-492">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-492">Description</span></span>

<span data-ttu-id="91c98-493">このサービスを使用すると、指定した、以前に作成した NetX IP インスタンス上に、FTP サーバー インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="91c98-494">操作を開始するには、***nx_ftp_server_start*** の呼び出しを使用して FTP サーバーを開始する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-495">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-495">Input Parameters</span></span>

- <span data-ttu-id="91c98-496">**ftp_server_ptr** FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="91c98-497">**ftp_server_name** FTP サーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="91c98-498">**ip_ptr** 関連付けられた NetX IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="91c98-499">1 つの IP インスタンスにつき 1 つの FTP サーバーしか存在できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="91c98-500">**media_ptr** 関連付けられた FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="91c98-501">**stack_ptr** 内部 FTP サーバー スレッドのスタック領域のメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="91c98-502">**stack_size** *stack_ptr* によって指定されたスタック領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="91c98-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="91c98-503">**pool_ptr** 既定の NetX パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="91c98-504">プール内のパケットのペイロード サイズは、最大のファイル名またはパスを格納するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="91c98-505">**ftp_login** アプリケーションのログイン関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="91c98-506">この関数には、接続を要求するクライアントからユーザー名とパスワード、および ULONG データ型のクライアント アドレスを提供します。</span><span class="sxs-lookup"><span data-stu-id="91c98-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="91c98-507">これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="91c98-508">**ftp_logout** アプリケーションのログアウト関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="91c98-509">この関数には、切断を要求するクライアントからユーザー名とパスワード、および ULONG データ型のクライアント アドレスを提供します。</span><span class="sxs-lookup"><span data-stu-id="91c98-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="91c98-510">これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-511">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-511">Return Values</span></span>

- <span data-ttu-id="91c98-512">**NX_SUCCESS** (0x00) FTP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="91c98-513">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-514">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-514">Allowed From</span></span>

<span data-ttu-id="91c98-515">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="91c98-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-516">例</span><span class="sxs-lookup"><span data-stu-id="91c98-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="91c98-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="91c98-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="91c98-518">IPv4 と IPv6 がサポートされる FTP サーバーを作成します</span><span class="sxs-lookup"><span data-stu-id="91c98-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-519">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="91c98-520">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-520">Description</span></span>

<span data-ttu-id="91c98-521">このサービスを使用すると、指定した、以前に作成した NetX IP インスタンス上に、FTP サーバー インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="91c98-522">サーバーが作成された後で操作を開始するには、***nx_ftp_server_start*** を呼び出して FTP サーバーを開始する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-523">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-523">Input Parameters</span></span>

- <span data-ttu-id="91c98-524">**ftp_server_ptr** FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="91c98-525">**ftp_server_name** FTP サーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="91c98-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="91c98-526">**ip_ptr** 関連付けられた NetX IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="91c98-527">1 つの IP インスタンスにつき 1 つの FTP サーバーしか存在できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="91c98-528">**media_ptr** 関連付けられた FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="91c98-529">**stack_ptr** 内部 FTP サーバー スレッドのスタック領域のメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="91c98-530">**stack_size** *stack_ptr* によって指定されたスタック領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="91c98-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="91c98-531">**pool_ptr** 既定の NetX パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="91c98-532">プール内のパケットのペイロード サイズは、最大のファイル名またはパスを格納するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c98-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="91c98-533">**ftp_login_duo** アプリケーションのログイン関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="91c98-534">この関数には、接続を要求するクライアントからユーザー名とパスワード、および NXD_ADDRESS データ型のクライアント アドレスへのポインターを提供します。</span><span class="sxs-lookup"><span data-stu-id="91c98-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="91c98-535">これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="91c98-536">**ftp_logout_duo** アプリケーションのログアウト関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="91c98-537">この関数には、切断を要求するクライアントからユーザー名とパスワード、および NXD_ADDRESS データ型のクライアント アドレスへのポインターを提供します。</span><span class="sxs-lookup"><span data-stu-id="91c98-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="91c98-538">これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-539">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-539">Return Values</span></span>

- <span data-ttu-id="91c98-540">**NX_SUCCESS** (0x00) FTP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="91c98-541">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-542">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-543">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-543">Allowed From</span></span>

<span data-ttu-id="91c98-544">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="91c98-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-545">例</span><span class="sxs-lookup"><span data-stu-id="91c98-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="91c98-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="91c98-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="91c98-547">FTP サーバーを削除します</span><span class="sxs-lookup"><span data-stu-id="91c98-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-548">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="91c98-549">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-549">Description</span></span>

<span data-ttu-id="91c98-550">このサービスを使用すると、以前に作成した FTP サーバー インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-551">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-551">Input Parameters</span></span>

- <span data-ttu-id="91c98-552">**ftp_server_ptr** FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-553">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-553">Return Values</span></span>

- <span data-ttu-id="91c98-554">**NX_SUCCESS** (0x00) FTP サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="91c98-555">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-556">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-557">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-557">Allowed From</span></span>

<span data-ttu-id="91c98-558">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-559">例</span><span class="sxs-lookup"><span data-stu-id="91c98-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="91c98-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="91c98-560">nx_ftp_server_start</span></span>

<span data-ttu-id="91c98-561">FTP サーバーを開始します</span><span class="sxs-lookup"><span data-stu-id="91c98-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-562">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="91c98-563">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-563">Description</span></span>

<span data-ttu-id="91c98-564">このサービスを使用すると、以前に作成した FTP サーバー インスタンスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-565">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-565">Input Parameters</span></span>

- <span data-ttu-id="91c98-566">**ftp_server_ptr** FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-567">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-567">Return Values</span></span>

- <span data-ttu-id="91c98-568">**NX_SUCCESS** (0x00) FTP サーバーが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="91c98-569">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-570">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-570">Allowed From</span></span>

<span data-ttu-id="91c98-571">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-572">例</span><span class="sxs-lookup"><span data-stu-id="91c98-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="91c98-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="91c98-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="91c98-574">FTP サーバーを停止します</span><span class="sxs-lookup"><span data-stu-id="91c98-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="91c98-575">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="91c98-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="91c98-576">説明</span><span class="sxs-lookup"><span data-stu-id="91c98-576">Description</span></span>

<span data-ttu-id="91c98-577">このサービスを使用すると、以前に作成して開始した FTP サーバー インスタンスが停止されます。</span><span class="sxs-lookup"><span data-stu-id="91c98-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="91c98-578">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c98-578">Input Parameters</span></span>

- <span data-ttu-id="91c98-579">**ftp_server_ptr** FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91c98-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="91c98-580">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c98-580">Return Values</span></span>

- <span data-ttu-id="91c98-581">**NX_SUCCESS** (0x00) FTP サーバーが正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="91c98-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="91c98-582">NX_PTR_ERROR (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="91c98-583">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="91c98-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="91c98-584">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="91c98-584">Allowed From</span></span>

<span data-ttu-id="91c98-585">Threads</span><span class="sxs-lookup"><span data-stu-id="91c98-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="91c98-586">例</span><span class="sxs-lookup"><span data-stu-id="91c98-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
