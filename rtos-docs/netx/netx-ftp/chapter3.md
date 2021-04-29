---
title: 第 3 章 - Azure RTOS NetX FTP サービスの説明
description: この章では、すべての Azure RTOS NetX FTP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811537"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="1ecd0-103">第 3 章 - Azure RTOS NetX FTP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="1ecd0-104">この章では、すべての Azure RTOS NetX FTP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="1ecd0-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="1ecd0-106">**nx_ftp_client_connect**: "*FTP サーバーに接続する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="1ecd0-107">**nx_ftp_client_create**: "*FTP クライアント インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="1ecd0-108">**nx_ftp_client_delete**: "*FTP クライアント インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="1ecd0-109">**nx_ftp_client_directory_create**: "*サーバーにディレクトリを作成する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="1ecd0-110">**nx_ftp_client_directory_default_set**: "*サーバーに既定のディレクトリを設定する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="1ecd0-111">**nx_ftp_client_directory_delete**: "*サーバー上のディレクトリを削除する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="1ecd0-112">**nx_ftp_client_directory_listing_get**: "*サーバーからディレクトリの一覧を取得する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="1ecd0-113">**nx_ftp_client_directory_listing_continue**: "*サーバーからのディレクトリの一覧を続行する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="1ecd0-114">**nx_ftp_client_disconnect**: "*FTP サーバーから切断する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="1ecd0-115">**nx_ftp_client_file_close**: "*クライアント ファイルを閉じる*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="1ecd0-116">**nx_ftp_client_file_delete**: "*サーバー上のファイルを削除する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="1ecd0-117">**nx_ftp_client_file_open**: "*クライアント ファイルを開く*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="1ecd0-118">**nx_ftp_client_file_read**: "*ファイルから読み取る*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="1ecd0-119">**nx_ftp_client_file_rename**: "*サーバー上のファイルの名前を変更する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="1ecd0-120">**nx_ftp_client_file_write**: "*ファイルに書き込む*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="1ecd0-121">**nx_ftp_server_create**: "*FTP サーバーを作成する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="1ecd0-122">**nx_ftp_server_delete**: "*FTP サーバーを削除する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="1ecd0-123">**nx_ftp_server_start**: "*FTP サーバーを開始する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="1ecd0-124">**nx_ftp_server_stop**: "*FTP サーバーを停止する*"</span><span class="sxs-lookup"><span data-stu-id="1ecd0-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="1ecd0-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="1ecd0-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="1ecd0-126">FTP サーバーに接続します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-127">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-128">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-128">Description</span></span>

<span data-ttu-id="1ecd0-129">このサービスにより、以前に作成された FTP クライアント インスタンスが、指定された IP アドレスの FTP サーバーに接続されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-130">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-130">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-131">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-132">**server_ip**: FTP サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="1ecd0-133">**username**: 認証用のクライアント ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="1ecd0-134">**password**: 認証用のクライアント パスワード。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="1ecd0-135">**wait_option**: FTP クライント接続をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="1ecd0-136">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-137">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-139">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-140">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-140">Return Values</span></span>

- <span data-ttu-id="1ecd0-141">**NX_SUCCESS**: (0x00) FTP 接続に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="1ecd0-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) 22X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="1ecd0-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) 23X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="1ecd0-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) 33X (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="1ecd0-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) クライアントは既に接続されています。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="1ecd0-146">NX_PTR_ERROR: (0x07) ポインター入出力が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="1ecd0-147">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="1ecd0-148">NX_IP_ADDRESS_ERROR: (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-149">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-149">Allowed From</span></span>

<span data-ttu-id="1ecd0-150">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-151">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="1ecd0-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="1ecd0-152">nx_ftp_client_create</span></span>

<span data-ttu-id="1ecd0-153">FTP クライアント インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="1ecd0-155">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-155">Description</span></span>

<span data-ttu-id="1ecd0-156">このサービスにより、FTP クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-157">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-157">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-158">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-159">**ftp_client_name**: FTP クライアントの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="1ecd0-160">**ip_ptr**: 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="1ecd0-161">**window_size**: この FTP クライアントの TCP ソケットのアドバタイズされたウィンドウ サイズ。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="1ecd0-162">**pool_ptr**: この FTP クライアントの既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="1ecd0-163">最小パケット ペイロードは、完全なパスとファイルまたはディレクトリ名を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-164">Return Values</span></span>

- <span data-ttu-id="1ecd0-165">**NX_SUCCESS**: (0x00) FTP クライアントが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="1ecd0-166">NX_PTR_ERROR: (0x16) FTP、IP ポインター、またはパケット プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="1ecd0-167">パスワード ポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-168">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-168">Allowed From</span></span>

<span data-ttu-id="1ecd0-169">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="1ecd0-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-170">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="1ecd0-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="1ecd0-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="1ecd0-172">FTP クライアント インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="1ecd0-174">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-174">Description</span></span>

<span data-ttu-id="1ecd0-175">このサービスにより、FTP クライアント インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-176">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-176">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-177">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-178">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-178">Return Values</span></span>

- <span data-ttu-id="1ecd0-179">**NX_SUCCESS**: (0x00) FTP クライアントが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="1ecd0-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP クライアントの削除エラー。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="1ecd0-181">NX_PTR_ERROR: (0x16) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-182">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-183">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-183">Allowed From</span></span>

<span data-ttu-id="1ecd0-184">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-185">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="1ecd0-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="1ecd0-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="1ecd0-187">FTP サーバーにディレクトリを作成します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-188">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-189">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-189">Description</span></span>

<span data-ttu-id="1ecd0-190">このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上に、指定されたディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-191">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-191">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-192">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-193">**directory_name**: 作成するディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="1ecd0-194">**wait_option**: FTP ディレクトリの作成をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="1ecd0-195">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-196">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-198">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-199">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-199">Return Values</span></span>

- <span data-ttu-id="1ecd0-200">**NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="1ecd0-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="1ecd0-203">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="1ecd0-204">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-205">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-205">Allowed From</span></span>

<span data-ttu-id="1ecd0-206">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-207">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="1ecd0-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="1ecd0-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="1ecd0-209">FTP サーバーに既定のディレクトリを設定します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-210">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-211">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-211">Description</span></span>

<span data-ttu-id="1ecd0-212">このサービスにより、指定された FTP クライアントに接続されている FTP サーバーに既定のディレクトリが設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="1ecd0-213">この既定のディレクトリは、このクライアントの接続にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-214">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-214">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-215">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-216">**directory_path**: 設定するディレクトリ パスの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="1ecd0-217">**wait_option**: FTP の既定のディレクトリの設定をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="1ecd0-218">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-219">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-221">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-222">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-222">Return Values</span></span>

- <span data-ttu-id="1ecd0-223">**NX_SUCCESS**: (0x00) FTP の既定の設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="1ecd0-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="1ecd0-226">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="1ecd0-227">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-228">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-228">Allowed From</span></span>

<span data-ttu-id="1ecd0-229">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-230">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="1ecd0-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="1ecd0-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="1ecd0-232">FTP サーバー上のディレクトリを削除します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-233">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-234">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-234">Description</span></span>

<span data-ttu-id="1ecd0-235">このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上の指定されたディレクトリが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-236">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-236">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-237">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-238">**directory_name**: 削除するディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="1ecd0-239">**wait_option**: FTP ディレクトリの削除をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="1ecd0-240">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-241">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-243">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-244">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-244">Return Values</span></span>

- <span data-ttu-id="1ecd0-245">**NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="1ecd0-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="1ecd0-248">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="1ecd0-249">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-250">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-250">Allowed From</span></span>

<span data-ttu-id="1ecd0-251">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-252">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="1ecd0-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="1ecd0-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="1ecd0-254">FTP サーバーからディレクトリの一覧を取得します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-255">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-256">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-256">Description</span></span>

<span data-ttu-id="1ecd0-257">このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上の指定されたディレクトリのコンテンツが取得されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="1ecd0-258">指定されたパケット ポインターには、1 つ以上のディレクトリ エントリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="1ecd0-259">それぞれのエントリは、&lt;cr/lf\ の組み合わせで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="1ecd0-260">ディレクトリの取得操作を完了するには、***nx_ftp_client_directory_listing_continue*** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-261">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-261">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-262">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-263">**directory_name**: コンテンツを取得するディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="1ecd0-264">**packet_ptr**: 宛先パケット ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="1ecd0-265">成功した場合、パケット ペイロードには 1 つ以上のディレクトリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="1ecd0-266">**wait_option**: FTP ディレクトリの一覧をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="1ecd0-267">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-268">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-270">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-271">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-271">Return Values</span></span>

- <span data-ttu-id="1ecd0-272">**NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に一覧されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="1ecd0-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-274">**NX_NOT_ENABLED**: (0x14) サービス (IPv6) が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="1ecd0-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="1ecd0-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) 1XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-277">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-278">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-279">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-279">Allowed From</span></span>

<span data-ttu-id="1ecd0-280">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-281">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="1ecd0-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="1ecd0-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="1ecd0-283">FTP サーバーからのディレクトリの一覧取得を続行します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-284">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-285">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-285">Description</span></span>

<span data-ttu-id="1ecd0-286">このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上の指定されたディレクトリのコンテンツの取得が続行されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="1ecd0-287">直前に ***nx_ftp_client_directory_listing_get*** の呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="1ecd0-288">成功した場合、指定されたパケット ポインターには、1 つ以上のディレクトリ エントリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="1ecd0-289">このルーチンは、NX_FTP_END_OF_LISTING の状態を受信するまで呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-290">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-290">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-291">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-292">**packet_ptr**: 宛先パケット ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="1ecd0-293">成功した場合、パケット ペイロードには、&lt;cr/lf&gt; で区切られた 1 つ以上のディレクトリ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="1ecd0-294">**wait_option**: FTP ディレクトリの一覧をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="1ecd0-295">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-296">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-298">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-299">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-299">Return Values</span></span>

- <span data-ttu-id="1ecd0-300">**NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に一覧されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="1ecd0-301">**NX_FTP_END_OF_LISTING**: (0xD8) このディレクトリにはこれ以上エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="1ecd0-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-304">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-305">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-306">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-306">Allowed From</span></span>

<span data-ttu-id="1ecd0-307">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-308">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="1ecd0-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="1ecd0-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="1ecd0-310">FTP サーバーから切断します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-311">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-312">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-312">Description</span></span>

<span data-ttu-id="1ecd0-313">このサービスにより、指定された FTP クライアントとの間に以前に確立された FTP サーバー接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-314">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-314">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-315">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-316">**wait_option**: FTP クライントの切断をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="1ecd0-317">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-318">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-320">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-321">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-321">Return Values</span></span>

- <span data-ttu-id="1ecd0-322">**NX_SUCCESS**: (0x00) FTP の切断に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="1ecd0-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-325">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-326">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-327">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-327">Allowed From</span></span>

<span data-ttu-id="1ecd0-328">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-329">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="1ecd0-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="1ecd0-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="1ecd0-331">クライアント ファイルを閉じます</span><span class="sxs-lookup"><span data-stu-id="1ecd0-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-333">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-333">Description</span></span>

<span data-ttu-id="1ecd0-334">このサービスにより、FTP サーバー上で既に開いているファイルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-335">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-335">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-336">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-337">**wait_option**: FTP クライントのファイルが閉じられるのをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="1ecd0-338">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-339">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-341">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-342">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-342">Return Values</span></span>

- <span data-ttu-id="1ecd0-343">**NX_SUCCESS**: (0x00) FTP ファイルが正常に閉じられました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="1ecd0-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-345">**NX_FTP_NOT_OPEN (0xD5)** : ファイルが開かれていません。閉じることができません</span><span class="sxs-lookup"><span data-stu-id="1ecd0-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="1ecd0-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-347">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-348">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-349">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-349">Allowed From</span></span>

<span data-ttu-id="1ecd0-350">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-351">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="1ecd0-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="1ecd0-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="1ecd0-353">FTP サーバー上のファイルを削除します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-354">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-355">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-355">Description</span></span>

<span data-ttu-id="1ecd0-356">このサービスにより、FTP サーバー上の指定したファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-357">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-357">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-358">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-359">**file_name**: 削除するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="1ecd0-360">**wait_option**: FTP クライントのファイルの削除をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="1ecd0-361">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-362">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-364">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-365">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-365">Return Values</span></span>

- <span data-ttu-id="1ecd0-366">**NX_SUCCESS**: (0x00) FTP ファイルが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="1ecd0-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-369">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-370">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-371">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-371">Allowed From</span></span>

<span data-ttu-id="1ecd0-372">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-373">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="1ecd0-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="1ecd0-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="1ecd0-375">FTP サーバー上のファイルを開きます</span><span class="sxs-lookup"><span data-stu-id="1ecd0-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-376">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-377">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-377">Description</span></span>

<span data-ttu-id="1ecd0-378">このサービスにより、指定したクライアント インスタンスに接続済みの FTP サーバー上の指定したファイルが (読み取りまたは書き込み用に) 開かれます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-379">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-379">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-380">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-381">**file_name**: 開くファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="1ecd0-382">**open_type**: **NX_FTP_OPEN_FOR_READ** または **NX_FTP_OPEN_FOR_WRITE**。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="1ecd0-383">**wait_option**: FTP クライントのファイルが開かれるのをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="1ecd0-384">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-385">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-387">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-388">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-388">Return Values</span></span>

- <span data-ttu-id="1ecd0-389">**NX_SUCCESS**: (0x00) FTP ファイルが正常に開かれました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="1ecd0-390">**NX_OPTION_ERROR** :(0x0A) オープン型が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="1ecd0-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP クライアントは既に開かれています。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="1ecd0-393">**NX_NO_FREE_PORTS**: (0x45) 割り当てることのできる TCP ポートがありません</span><span class="sxs-lookup"><span data-stu-id="1ecd0-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="1ecd0-394">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-395">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-396">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-396">Allowed From</span></span>

<span data-ttu-id="1ecd0-397">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-398">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="1ecd0-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="1ecd0-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="1ecd0-400">ファイルから読み取ります</span><span class="sxs-lookup"><span data-stu-id="1ecd0-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-401">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-402">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-402">Description</span></span>

<span data-ttu-id="1ecd0-403">このサービスにより、以前に開かれたファイルからパケットが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="1ecd0-404">NX_FTP_END_OF_FILE の状態が受信されるまで繰り返し呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="1ecd0-405">このサービスのパケットは呼び出し元によって割り当てられないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="1ecd0-406">指定する必要があるのはパケット ポインターへのポインターだけです。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="1ecd0-407">このサービスにより、ソケット受信キューから取得されたパケットを指すようにそのパケット ポインターが更新されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="1ecd0-408">正常状態が返された場合は、パケットが使用可能であったことを意味します。また、終了時にパケットを解放するのは呼び出し元の責任です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="1ecd0-409">0 以外の状態 (エラー状態または NX_FTP_END_OF_FILE) が返された場合、パケットは呼び出し元によって解放されません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="1ecd0-410">それ以外の場合は、パケット ポインターが NULL の場合にエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-411">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-411">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-412">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-413">**packet_ptr**: キューから取得したデータ パケット ポインターの宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="1ecd0-414">成功した場合、パケット データにはファイルの一部またはすべてが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="1ecd0-415">**wait_option**: FTP クライントのファイルの読み取りをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="1ecd0-416">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-417">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-419">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-420">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-420">Return Values</span></span>

- <span data-ttu-id="1ecd0-421">**NX_SUCCESS**: (0x00) FTP ファイルが正常に読み取られました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="1ecd0-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP クライアントが開かれていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="1ecd0-423">**NX_FTP_END_OF_FILE**: (0xD7) ファイルの終わりの条件。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="1ecd0-424">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-425">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-426">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-426">Allowed From</span></span>

<span data-ttu-id="1ecd0-427">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-428">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

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

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="1ecd0-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="1ecd0-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="1ecd0-430">FTP サーバー上のファイルの名前を変更します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-431">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-432">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-432">Description</span></span>

<span data-ttu-id="1ecd0-433">このサービスにより、FTP サーバー上のファイルの名前が変更されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-434">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-434">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-435">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-436">**filename**: ファイルの現在の名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="1ecd0-437">**new_filename**: ファイルの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="1ecd0-438">**wait_option**: FTP クライントのファイル名の変更をこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="1ecd0-439">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-440">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-442">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-443">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-443">Return Values</span></span>

- <span data-ttu-id="1ecd0-444">**NX_SUCCESS**: (0x00) FTP ファイルの名前が正常に変更されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="1ecd0-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="1ecd0-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) 3XX (ok) 応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした</span><span class="sxs-lookup"><span data-stu-id="1ecd0-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="1ecd0-448">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-449">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-450">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-450">Allowed From</span></span>

<span data-ttu-id="1ecd0-451">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-452">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="1ecd0-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="1ecd0-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="1ecd0-454">ファイルに書き込みます</span><span class="sxs-lookup"><span data-stu-id="1ecd0-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-455">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="1ecd0-456">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-456">Description</span></span>

<span data-ttu-id="1ecd0-457">このサービスにより、FTP サーバー上の以前に開かれたファイルにデータのパケットが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-458">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-458">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-459">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-460">**packet_ptr**: 書き込むデータが格納されているパケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="1ecd0-461">**wait_option**: FTP クライントのファイルの書き込みをこのサービスで待機する時間の長さを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="1ecd0-462">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1ecd0-463">**timeout value**: (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1ecd0-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1ecd0-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="1ecd0-465">数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-466">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-466">Return Values</span></span>

- <span data-ttu-id="1ecd0-467">**NX_SUCCESS**: (0x00) FTP ファイルが正常に書き込まれました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="1ecd0-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP クライアントが開かれていません。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="1ecd0-469">NX_PTR_ERROR: (0x07) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-470">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-471">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-471">Allowed From</span></span>

<span data-ttu-id="1ecd0-472">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-473">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="1ecd0-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="1ecd0-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="1ecd0-475">パッシブ転送モードを有効または無効にします</span><span class="sxs-lookup"><span data-stu-id="1ecd0-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-476">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="1ecd0-477">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-477">Description</span></span>

<span data-ttu-id="1ecd0-478">このサービスにより、以前に作成された FTP クライアント インスタンス上で passive_mode_enabled 入力が NX_TRUE に設定されている場合にパッシブ転送モードが有効化されます。これにより、ファイルの読み取りや書き込み (RETR、STOR) またはディレクトリ一覧のダウンロード (NLST) に対する後続の呼び出しは、転送モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="1ecd0-479">パッシブ モードの転送を無効にして、アクティブ転送モードの既定の動作に戻すには、passive_mode_enabled 入力を NX_FALSE に設定して、この関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-480">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-480">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-481">**ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="1ecd0-482">**passive_mode_enabled**:</span><span class="sxs-lookup"><span data-stu-id="1ecd0-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="1ecd0-483">NX_TRUE に設定すると、パッシブ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="1ecd0-484">NX_FALSE に設定すると、パッシブ モードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-485">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-485">Return Values</span></span>

- <span data-ttu-id="1ecd0-486">**NX_SUCCESS**: (0x00) パッシブ モードの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="1ecd0-487">NX_PTR_ERROR: (0x16) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-488">NX_INVALID_PARAMETERS: (0x4D) ポインターではない無効な入力</span><span class="sxs-lookup"><span data-stu-id="1ecd0-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-489">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-489">Allowed From</span></span>

<span data-ttu-id="1ecd0-490">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-491">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="1ecd0-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="1ecd0-492">nx_ftp_server_create</span></span>

<span data-ttu-id="1ecd0-493">FTP サーバーを作成します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-494">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="1ecd0-495">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-495">Description</span></span>

<span data-ttu-id="1ecd0-496">このサービスにより、指定した作成済みの NetX IP インスタンス上に FTP サーバー インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="1ecd0-497">操作を開始するには、***nx_ftp_server_start*** の呼び出しを使用して FTP サーバーを開始する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-498">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-498">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-499">**ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="1ecd0-500">**ftp_server_name**: FTP サーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="1ecd0-501">**ip_ptr**: 関連付けられた NetX IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="1ecd0-502">1 つの IP インスタンスにつき 1 つの FTP サーバーしか存在できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="1ecd0-503">**media_ptr**: 関連付けられた FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="1ecd0-504">**stack_ptr**: 内部 FTP サーバー スレッドのスタック領域のメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="1ecd0-505">**stack_size**: *stack_ptr* によって指定されたスタック領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="1ecd0-506">**pool_ptr**: 既定の NetX パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="1ecd0-507">プール内のパケットのペイロード サイズは、最大のファイル名またはパスを格納するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="1ecd0-508">**ftp_login**: アプリケーションのログイン関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="1ecd0-509">この関数には、接続を要求しているクライアントからのユーザー名とパスワードが指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="1ecd0-510">これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="1ecd0-511">**ftp_logout**: アプリケーションのログアウト関数への関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="1ecd0-512">この関数には、切断を要求しているクライアントからのユーザー名とパスワードが指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="1ecd0-513">これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-514">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-514">Return Values</span></span>

- <span data-ttu-id="1ecd0-515">**NX_SUCCESS**: (0x00) FTP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="1ecd0-516">NX_PTR_ERROR: (0x16) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-517">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-517">Allowed From</span></span>

<span data-ttu-id="1ecd0-518">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="1ecd0-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-519">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="1ecd0-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ecd0-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="1ecd0-521">FTP サーバーを削除します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-522">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="1ecd0-523">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-523">Description</span></span>

<span data-ttu-id="1ecd0-524">このサービスにより、以前に作成された FTP サーバー インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-525">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-525">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-526">**ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-527">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-527">Return Values</span></span>

- <span data-ttu-id="1ecd0-528">**NX_SUCCESS**: (0x00) FTP サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="1ecd0-529">NX_PTR_ERROR: (0x16) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-530">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-531">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-531">Allowed From</span></span>

<span data-ttu-id="1ecd0-532">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-533">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="1ecd0-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="1ecd0-534">nx_ftp_server_start</span></span>

<span data-ttu-id="1ecd0-535">FTP サーバーを開始します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-536">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="1ecd0-537">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-537">Description</span></span>

<span data-ttu-id="1ecd0-538">このサービスにより、作成済みの FTP サーバー インスタンスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-539">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-539">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-540">**ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-541">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-541">Return Values</span></span>

- <span data-ttu-id="1ecd0-542">**NX_SUCCESS**: (0x00) FTP サーバーが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="1ecd0-543">NX_PTR_ERROR: (0x16) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-544">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-544">Allowed From</span></span>

<span data-ttu-id="1ecd0-545">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="1ecd0-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-546">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="1ecd0-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="1ecd0-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="1ecd0-548">FTP サーバーを停止します</span><span class="sxs-lookup"><span data-stu-id="1ecd0-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ecd0-549">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1ecd0-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="1ecd0-550">説明</span><span class="sxs-lookup"><span data-stu-id="1ecd0-550">Description</span></span>

<span data-ttu-id="1ecd0-551">このサービスにより、以前に作成され、開始された FTP サーバー インスタンスが停止されます。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1ecd0-552">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ecd0-552">Input Parameters</span></span>

- <span data-ttu-id="1ecd0-553">**ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ecd0-554">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ecd0-554">Return Values</span></span>

- <span data-ttu-id="1ecd0-555">**NX_SUCCESS**: (0x00) FTP サーバーが正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="1ecd0-556">NX_PTR_ERROR: (0x16) FTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="1ecd0-557">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="1ecd0-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ecd0-558">許可元</span><span class="sxs-lookup"><span data-stu-id="1ecd0-558">Allowed From</span></span>

<span data-ttu-id="1ecd0-559">Threads</span><span class="sxs-lookup"><span data-stu-id="1ecd0-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ecd0-560">例</span><span class="sxs-lookup"><span data-stu-id="1ecd0-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
