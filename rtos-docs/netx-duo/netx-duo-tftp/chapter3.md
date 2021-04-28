---
title: 第 3 章 - Azure RTOS NetX Duo TFTP サービスの説明
description: この章では、すべての NetX Duo TFTP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810523"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="60e0e-103">第 3 章 - Azure RTOS NetX Duo TFTP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="60e0e-104">この章では、すべての NetX Duo TFTP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="60e0e-105">特に指定がない限り、すべてのサービスで IPv6 および IPv4 の通信がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="60e0e-106">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="60e0e-107">**nxd_tftp_client_file_open**: "*TFTP クライアント ファイルを開く*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="60e0e-108">**nxd_tftp_client_create**: "*TFTP クライアント インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="60e0e-109">**nxd_tftp_client_delete**: "*TFTP クライアント インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="60e0e-110">**nxd_tftp_client_error_info_get**: "*クライアントのエラー情報を取得する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="60e0e-111">**nxd_tftp_client_file_close**: "*クライアント ファイルを閉じる*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="60e0e-112">**nxd_tftp_client_file_open**: "*クライアント ファイルを開く*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="60e0e-113">**nxd_tftp_client_file_read**: "*クライアント ファイルからブロックを読み取る*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="60e0e-114">**nxd_tftp_client_file_write**: "*クライアント ファイルにブロックを書き込む*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="60e0e-115">**nxd_tftp_client_packet_allocate**: "*クライアント ファイル書き込み用にパケットを割り当てる*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="60e0e-116">**nxd_tftp_client_set_interface**: "*TFTP 要求の物理インターフェイスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="60e0e-117">**nxd_tftp_server_create**: "*TFTP サーバーを作成する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="60e0e-118">**nxd_tftp_server_delete**: "*TFTP サーバーを削除する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="60e0e-119">**nxd_tftp_server_start**: "*TFTP サーバーを起動する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="60e0e-120">**nxd_tftp_server_stop**: "*TFTP サーバーを停止する*"</span><span class="sxs-lookup"><span data-stu-id="60e0e-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="60e0e-121">上記のすべてのサービスの IPv4 に相当するものは、NetX Duo TFTP クライアントとサーバー (*nx_tftp_server_create* や *nx_tftp_client_file_open* など) で利用できます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="60e0e-122">以下のページでは、"Duo" API の説明 (*nxd_* で始まるサービスなど) のみを提供しています。</span><span class="sxs-lookup"><span data-stu-id="60e0e-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="60e0e-123">NXD_ADDRESS \* 入力が指定されている場合、IPv4 に相当する API は ULONG 入力を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="60e0e-124">それ以外の場合、API の使用に違いはありません。</span><span class="sxs-lookup"><span data-stu-id="60e0e-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="60e0e-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="60e0e-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="60e0e-126">TFTP クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="60e0e-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-127">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="60e0e-128">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-128">Description</span></span>

<span data-ttu-id="60e0e-129">このサービスでは、以前に作成された IP インスタンスの TFTP クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60e0e-130">アプリケーションでは、指定された IP およびパケット プールが既に作成されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="60e0e-131">さらに、このサービスを呼び出す前に、IP インスタンスに対して UDP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-132">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-132">Input Parameters</span></span>

- <span data-ttu-id="60e0e-133">**tftp_client_ptr** TFTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="60e0e-134">**tftp_client_name** この TFTP クライアント インスタンスの名前</span><span class="sxs-lookup"><span data-stu-id="60e0e-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="60e0e-135">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="60e0e-136">**pool_ptr** パケット プール TFTP クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-137">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-137">Return Values</span></span>

- <span data-ttu-id="60e0e-138">**NX_SUCCESS** (0x00) TFTP が正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="60e0e-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="60e0e-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効またはサポートされていません</span><span class="sxs-lookup"><span data-stu-id="60e0e-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="60e0e-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 無効なサーバー IP アドレスを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="60e0e-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバー ACK を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="60e0e-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="60e0e-142">NX_PTR_ERROR (0x16) IP、プール、または TFTP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="60e0e-143">NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="60e0e-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="60e0e-144">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-145">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-145">Allowed From</span></span>

<span data-ttu-id="60e0e-146">初期化とスレッド</span><span class="sxs-lookup"><span data-stu-id="60e0e-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-147">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="60e0e-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="60e0e-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="60e0e-149">TFTP クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="60e0e-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-150">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="60e0e-151">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-151">Description</span></span>

<span data-ttu-id="60e0e-152">このサービスでは、以前に作成された TFTP クライアント インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-153">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-153">Input Parameters</span></span>

- <span data-ttu-id="60e0e-154">**tftp_client_ptr** 以前に作成した TFTP クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-155">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-155">Return Values</span></span>

- <span data-ttu-id="60e0e-156">**NX_SUCCESS** (0x00) TFTP クライアントが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="60e0e-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="60e0e-157">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-158">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-159">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-159">Allowed From</span></span>

<span data-ttu-id="60e0e-160">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-161">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="60e0e-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="60e0e-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="60e0e-163">クライアントのエラー情報を取得する</span><span class="sxs-lookup"><span data-stu-id="60e0e-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-164">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="60e0e-165">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-165">Description</span></span>

<span data-ttu-id="60e0e-166">このサービスでは、最後のエラー コードを返し、クライアントの内部エラー文字列へのポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="60e0e-167">エラー状態では、ユーザーはサーバーによって最後に送信されたエラーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="60e0e-168">null 値のエラー文字列は、エラーが存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-169">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-169">Input Parameters</span></span>

- <span data-ttu-id="60e0e-170">**tftp_client_ptr** 以前に作成した TFTP クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="60e0e-171">**error_code** エラー コードの送信先領域へのポインター</span><span class="sxs-lookup"><span data-stu-id="60e0e-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="60e0e-172">**error_string** エラー文字列の送信先へのポインター</span><span class="sxs-lookup"><span data-stu-id="60e0e-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-173">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-173">Return Values</span></span>

- <span data-ttu-id="60e0e-174">**NX_SUCCESS** (0x00) TFTP エラー情報を正常に取得しました。</span><span class="sxs-lookup"><span data-stu-id="60e0e-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="60e0e-175">NX_PTR_ERROR (0x16) TFTP クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="60e0e-176">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-177">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-177">Allowed From</span></span>

<span data-ttu-id="60e0e-178">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-179">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="60e0e-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="60e0e-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="60e0e-181">クライアント ファイルを閉じる</span><span class="sxs-lookup"><span data-stu-id="60e0e-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-182">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="60e0e-183">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-183">Description</span></span>

<span data-ttu-id="60e0e-184">このサービスにより、この TFTP クライアント インスタンスによって以前に開かれたファイルが閉じます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="60e0e-185">TFTP クライアント インスタンスで一度に開くことができるファイルは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="60e0e-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-186">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-186">Input Parameters</span></span>

- <span data-ttu-id="60e0e-187">**tftp_client_ptr** 以前に作成した TFTP クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="60e0e-188">**ip_type** 使用する IP プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="60e0e-189">有効なオプションは、IPv4 (4) または IPv6 (6) です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-190">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-190">Return Values</span></span>

- <span data-ttu-id="60e0e-191">**FX_SUCCESS** (0x00) TFTP ファイルが閉じられました。</span><span class="sxs-lookup"><span data-stu-id="60e0e-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="60e0e-192">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-193">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="60e0e-194">NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-195">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-195">Allowed From</span></span>

<span data-ttu-id="60e0e-196">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-197">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="60e0e-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="60e0e-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="60e0e-199">TFTP クライアント ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="60e0e-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="60e0e-201">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-201">Description</span></span>

<span data-ttu-id="60e0e-202">このサービスでは、指定された IP アドレスで、TFTP サーバー上の指定されたファイルを開こうとします。</span><span class="sxs-lookup"><span data-stu-id="60e0e-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="60e0e-203">読み取りまたは書き込みのいずれかでファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="60e0e-204">これは IPv4 パケットに限定され、NetX TFTP アプリケーションのサポートを目的としています。</span><span class="sxs-lookup"><span data-stu-id="60e0e-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="60e0e-205">開発者は、同等の "duo" サービス *nxd_tftp_client_file_open* を使用するようにアプリケーションを移植することをお勧め します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-206">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-206">Input Parameters</span></span>

- <span data-ttu-id="60e0e-207">**tftp_client_ptr** TFTP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="60e0e-208">**file_name** ASCII ファイル名で、NULL で終了し、かつ適切なパス情報を持ちます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="60e0e-209">**server_ip_address** サーバーの TFTP アドレス。</span><span class="sxs-lookup"><span data-stu-id="60e0e-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="60e0e-210">**open_type** オープン要求の種類。次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="60e0e-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="60e0e-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="60e0e-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="60e0e-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="60e0e-213">**wait_option** サービスで、TFTP クライアントのファイルが開くまで待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="60e0e-214">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="60e0e-215">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="60e0e-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="60e0e-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="60e0e-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="60e0e-217">TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="60e0e-218">数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="60e0e-219">**ip_type** 使用する IP プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="60e0e-220">有効なオプションは、IPv4 (4) または IPv6 (6) です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-221">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-221">Return Values</span></span>

- <span data-ttu-id="60e0e-222">**NX_SUCCESS** (0x00) クライアント ファイルのオープンに成功しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="60e0e-223">**NX_TFTP_NOT_CLOSED** (0xC3) クライアントで既にファイルが開かれています</span><span class="sxs-lookup"><span data-stu-id="60e0e-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="60e0e-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="60e0e-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません</span><span class="sxs-lookup"><span data-stu-id="60e0e-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="60e0e-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 無効なサーバー IP を受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="60e0e-227">**NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="60e0e-228">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-229">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="60e0e-230">NX_IP_ADDRESS_ERROR (0x21) サーバー IP アドレスが無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="60e0e-231">NX_OPTION_ERROR (0x0A) オープン型が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-232">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-232">Allowed From</span></span>

<span data-ttu-id="60e0e-233">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-234">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="60e0e-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="60e0e-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="60e0e-236">TFTP クライアント ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="60e0e-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-237">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="60e0e-238">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-238">Description</span></span>

<span data-ttu-id="60e0e-239">このサービスでは、指定された IPv6 アドレスで、TFTP サーバー上の指定されたファイルを開こうとします。</span><span class="sxs-lookup"><span data-stu-id="60e0e-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="60e0e-240">読み取りまたは書き込みのいずれかでファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-241">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-241">Input Parameters</span></span>

- <span data-ttu-id="60e0e-242">**tftp_client_ptr** TFTP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="60e0e-243">**file_name** ASCII ファイル名で、NULL で終了し、かつ適切なパス情報を持ちます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="60e0e-244">**server_ip_address** サーバーの TFTP アドレス。</span><span class="sxs-lookup"><span data-stu-id="60e0e-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="60e0e-245">**open_type** オープン要求の種類。次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="60e0e-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="60e0e-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="60e0e-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="60e0e-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="60e0e-248">**wait_option** サービスで、TFTP クライアントのファイルが開くまで待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="60e0e-249">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="60e0e-250">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="60e0e-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="60e0e-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="60e0e-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="60e0e-252">TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="60e0e-253">数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="60e0e-254">**ip_type** 使用する IP プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="60e0e-255">有効なオプションは、IPv4 (4) または IPv6 (6) です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-256">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-256">Return Values</span></span>

- <span data-ttu-id="60e0e-257">**NX_SUCCESS** (0x00) クライアント ファイルのオープンに成功しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="60e0e-258">**NX_TFTP_NOT_CLOSED** (0xC3) クライアントで既にファイルが開かれています</span><span class="sxs-lookup"><span data-stu-id="60e0e-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="60e0e-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="60e0e-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません</span><span class="sxs-lookup"><span data-stu-id="60e0e-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="60e0e-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="60e0e-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 無効なサーバー IP を受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="60e0e-263">**NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="60e0e-264">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-265">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="60e0e-266">NX_IP_ADDRESS_ERROR (0x21) サーバー IP アドレスが無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="60e0e-267">NX_OPTION_ERROR (0x0A) オープン型が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="60e0e-268">NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="60e0e-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-269">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-269">Allowed From</span></span>

<span data-ttu-id="60e0e-270">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-271">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="60e0e-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="60e0e-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="60e0e-273">クライアント ファイルからブロックを読み取る</span><span class="sxs-lookup"><span data-stu-id="60e0e-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-274">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="60e0e-275">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-275">Description</span></span>

<span data-ttu-id="60e0e-276">このサービスでは、以前に開いた TFTP クライアント ファイルから 512 バイトのブロックを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="60e0e-277">512 バイト未満のブロックではファイルの終わりの合図があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-278">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-278">Input Parameters</span></span>

- <span data-ttu-id="60e0e-279">**tftp_client_ptr** TFTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="60e0e-280">**packet_ptr** ファイルから読み取られたブロックを格納しているパケットの宛先。</span><span class="sxs-lookup"><span data-stu-id="60e0e-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="60e0e-281">**wait_option** サービスで読み取りの完了を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="60e0e-282">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="60e0e-283">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="60e0e-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="60e0e-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="60e0e-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="60e0e-285">TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="60e0e-286">数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーによるファイルのブロックの送信を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="60e0e-287">**ip_type** 使用する IP プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="60e0e-288">有効なオプションは、IPv4 (4) または IPv6 (6) です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-289">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-289">Return Values</span></span>

- <span data-ttu-id="60e0e-290">**NX_SUCCESS** (0x00) クライアント ブロックが正常に読み取られました</span><span class="sxs-lookup"><span data-stu-id="60e0e-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="60e0e-291">**NX_TFTP_NOT_OPEN** (0xC3) 指定されたクライアント ファイルは読み取り用に開かれていません</span><span class="sxs-lookup"><span data-stu-id="60e0e-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="60e0e-292">**NX_NO_PACKET** (0x01) サーバーからパケットを受信していません。</span><span class="sxs-lookup"><span data-stu-id="60e0e-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="60e0e-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="60e0e-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません</span><span class="sxs-lookup"><span data-stu-id="60e0e-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="60e0e-295">**NX_TFTP_END_OF_FILE** (0xC5) ファイルの終わりが検出されました (エラーではありません)。</span><span class="sxs-lookup"><span data-stu-id="60e0e-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="60e0e-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="60e0e-297">**NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="60e0e-298">**NX_TFTP_FAILED** (0xC2) 不明な TFTP コードを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="60e0e-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) 無効なブロック番号を受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="60e0e-300">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-301">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="60e0e-302">NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="60e0e-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-303">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-303">Allowed From</span></span>

<span data-ttu-id="60e0e-304">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-305">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="60e0e-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="60e0e-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="60e0e-307">クライアント ファイルにブロックを書き込む</span><span class="sxs-lookup"><span data-stu-id="60e0e-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-308">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="60e0e-309">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-309">Description</span></span>

<span data-ttu-id="60e0e-310">このサービスでは、前に開いていた TFTP クライアント ファイルに 512 バイトのブロックを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="60e0e-311">512 バイト未満のブロックを指定すると、ファイルの終わりの合図があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-312">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-312">Input Parameters</span></span>

- <span data-ttu-id="60e0e-313">**tftp_client_ptr** TFTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="60e0e-314">**packet_ptr** ファイルに書き込むブロックを格納しているパケット。</span><span class="sxs-lookup"><span data-stu-id="60e0e-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="60e0e-315">**wait_option** サービスで書き込みの完了を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="60e0e-316">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="60e0e-317">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="60e0e-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="60e0e-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="60e0e-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="60e0e-319">TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="60e0e-320">数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーで書き込み要求に対する ACK の送信を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="60e0e-321">**ip_type** 使用する IP プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="60e0e-322">有効なオプションは、IPv4 (4) または IPv6 (6) です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-323">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-323">Return Values</span></span>

- <span data-ttu-id="60e0e-324">**NX_SUCCESS** (0x00) クライアント ブロックが正常に書き込まれました</span><span class="sxs-lookup"><span data-stu-id="60e0e-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="60e0e-325">**NX_TFTP_NOT_OPEN** (0xC3) 指定されたクライアント ファイルは書き込み用に開かれていません</span><span class="sxs-lookup"><span data-stu-id="60e0e-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="60e0e-326">**NX_TFTP_TIMEOUT** (0xC1) サーバーの ACK を待機中にタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="60e0e-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="60e0e-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="60e0e-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません</span><span class="sxs-lookup"><span data-stu-id="60e0e-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="60e0e-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="60e0e-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="60e0e-331">**NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="60e0e-332">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-333">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="60e0e-334">NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="60e0e-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-335">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-335">Allowed From</span></span>

<span data-ttu-id="60e0e-336">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-337">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="60e0e-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="60e0e-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="60e0e-339">クライアント ファイル書き込み用のパケットを割り当てる</span><span class="sxs-lookup"><span data-stu-id="60e0e-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-340">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="60e0e-341">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-341">Description</span></span>

<span data-ttu-id="60e0e-342">このサービスでは、指定されたパケット プールから UDP パケットを割り当て、パケットが呼び出し元に返される前に 4 バイトの TFTP ヘッダー用の領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="60e0e-343">その後、呼び出し元では、クライアント ファイルに書き込むためのバッファーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-344">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-344">Input Parameters</span></span>

- <span data-ttu-id="60e0e-345">**pool_ptr** パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="60e0e-346">**packet_ptr** 割り当てられたパケットへのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="60e0e-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="60e0e-347">**wait_option** パケットの割り当てが完了するまでサービスが待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="60e0e-348">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="60e0e-349">**タイムアウト値** (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="60e0e-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="60e0e-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="60e0e-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="60e0e-351">TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、割り当てが完了するまで無期限に一時停止になります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="60e0e-352">数値 (1 から 0xFFFFFFFE) を選択すると、パケットの割り当てを待機している間に一時停止を続けるタイマーティックの最大数が指定されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="60e0e-353">**ip_type** 使用する IP プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="60e0e-354">有効なオプションは、IPv4 (4) または IPv6 (6) です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-355">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-355">Return Values</span></span>

- <span data-ttu-id="60e0e-356">**NX_SUCCESS** (0x00) パケットが正常に割り当てられました</span><span class="sxs-lookup"><span data-stu-id="60e0e-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="60e0e-357">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-358">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="60e0e-359">NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="60e0e-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-360">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-360">Allowed From</span></span>

<span data-ttu-id="60e0e-361">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-362">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="60e0e-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="60e0e-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="60e0e-364">TFTP 要求の物理インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="60e0e-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-365">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="60e0e-366">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-366">Description</span></span>

<span data-ttu-id="60e0e-367">このサービスでは、入力インターフェイス インデックスを使用して、TFTP パケットを送受信する TFTP クライアントの物理インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="60e0e-368">プライマリ インターフェイスの既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="60e0e-369">NetX Duo では、このサービスを使用するために、マルチホーム アドレス指定 (v5.6 以降) をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-370">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-370">Input Parameters</span></span>

- <span data-ttu-id="60e0e-371">**tftp_client_ptr** TFTP クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="60e0e-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="60e0e-372">**if_index** 使用する物理インターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="60e0e-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-373">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-373">Return Values</span></span>

- <span data-ttu-id="60e0e-374">**NX_SUCCESS** (0x00) インターフェイスが正常に設定されました (0x0B) インターフェイス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="60e0e-375">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-376">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="60e0e-377">NX_TFTP_INVALID_INTERFACE (0x0B) インターフェイス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-378">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-378">Allowed From</span></span>

<span data-ttu-id="60e0e-379">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-380">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="60e0e-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="60e0e-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="60e0e-382">TFTP サーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="60e0e-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-383">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="60e0e-384">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-384">Description</span></span>

<span data-ttu-id="60e0e-385">このサービスでは、ポート 69 で TFTP クライアント要求に応答する TFTP サーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="60e0e-386">サーバーは、*nxd_tftp_server_start* の後続の呼び出しによって開始される必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60e0e-387">アプリケーションでは、指定された IP インスタンス、パケット プール、および FileX メディア インスタンスが既に作成されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="60e0e-388">さらに、このサービスを呼び出す前に、IP インスタンスに対して UDP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-389">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-389">Input Parameters</span></span>

- <span data-ttu-id="60e0e-390">**tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="60e0e-391">**tftp_server_name** この TFTP サーバー インスタンスの名前</span><span class="sxs-lookup"><span data-stu-id="60e0e-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="60e0e-392">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="60e0e-393">**media_ptr** FileX メディア インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="60e0e-394">**stack_ptr** TFTP サーバーのスタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="60e0e-395">**stack_size** TFTP サーバー スタック内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="60e0e-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="60e0e-396">**pool_ptr** TFTP パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="60e0e-397">指定されたプールには、サイズが 580 バイト以上のパケット ペイロードが必要です。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="60e0e-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="60e0e-398"><sup>1</sup> パケットのデータ部分はちょうど 512 バイトですが、パケット ペイロードのサイズは 572 バイト以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e0e-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="60e0e-399">残りのバイト数は、UDP、IPv6、イーサネット ヘッダー、およびドライバーがアラインメントに必要とする可能性のある後続バイトに使用されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-400">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-400">Return Values</span></span>

- <span data-ttu-id="60e0e-401">**NX_SUCCESS** (0x00) サーバーが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="60e0e-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="60e0e-402">**NX_TFTP_POOL_ERROR** (0xC6) パケット プールのパケット サイズが 560 バイト未満です</span><span class="sxs-lookup"><span data-stu-id="60e0e-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="60e0e-403">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-404">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-404">Allowed From</span></span>

<span data-ttu-id="60e0e-405">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="60e0e-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-406">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="60e0e-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="60e0e-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="60e0e-408">TFTP サーバーを削除する</span><span class="sxs-lookup"><span data-stu-id="60e0e-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-409">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="60e0e-410">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-410">Description</span></span>

<span data-ttu-id="60e0e-411">このサービスでは、以前に作成された TFTP サーバーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="60e0e-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-412">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-412">Input Parameters</span></span>

- <span data-ttu-id="60e0e-413">**tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-414">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-414">Return Values</span></span>

- <span data-ttu-id="60e0e-415">**NX_SUCCESS** (0x00) サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="60e0e-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="60e0e-416">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-417">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-418">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-418">Allowed From</span></span>

<span data-ttu-id="60e0e-419">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-420">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="60e0e-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="60e0e-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="60e0e-422">TFTP サーバーを起動する</span><span class="sxs-lookup"><span data-stu-id="60e0e-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-423">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="60e0e-424">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-424">Description</span></span>

<span data-ttu-id="60e0e-425">このサービスでは、以前に作成した TFTP サーバーを起動します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-426">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-426">Input Parameters</span></span>

- <span data-ttu-id="60e0e-427">**tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-428">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-428">Return Values</span></span>

- <span data-ttu-id="60e0e-429">**NX_SUCCESS** (0x00) サーバーが正常に起動しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="60e0e-430">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="60e0e-431">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-431">Allowed From</span></span>

<span data-ttu-id="60e0e-432">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="60e0e-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-433">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="60e0e-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="60e0e-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="60e0e-435">TFTP サーバーを停止する</span><span class="sxs-lookup"><span data-stu-id="60e0e-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="60e0e-436">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60e0e-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="60e0e-437">説明</span><span class="sxs-lookup"><span data-stu-id="60e0e-437">Description</span></span>

<span data-ttu-id="60e0e-438">このサービスでは、以前に作成した TFTP サーバーを停止します。</span><span class="sxs-lookup"><span data-stu-id="60e0e-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="60e0e-439">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60e0e-439">Input Parameters</span></span>

- <span data-ttu-id="60e0e-440">**tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60e0e-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="60e0e-441">戻り値</span><span class="sxs-lookup"><span data-stu-id="60e0e-441">Return Values</span></span>

- <span data-ttu-id="60e0e-442">**NX_SUCCESS** (0x00) サーバーが正常に停止しました</span><span class="sxs-lookup"><span data-stu-id="60e0e-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="60e0e-443">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="60e0e-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="60e0e-444">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="60e0e-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="60e0e-445">許可元</span><span class="sxs-lookup"><span data-stu-id="60e0e-445">Allowed From</span></span>

<span data-ttu-id="60e0e-446">Threads</span><span class="sxs-lookup"><span data-stu-id="60e0e-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="60e0e-447">例</span><span class="sxs-lookup"><span data-stu-id="60e0e-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```