---
title: チャプター 3 - Azure RTOS NetX Duo Telnet のサービスの説明
description: このチャプターでは、Azure RTOS NetX Duo Telnet の全サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810529"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="13dd1-103">チャプター 3 - Azure RTOS NetX Duo Telnet のサービスの説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="13dd1-104">このチャプターでは、Azure RTOS NetX Duo Telnet の全サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="13dd1-105">次の API の説明の「戻り値」セクションでは、API のエラー チェックを無効にする **NX_DISABLE_ERROR_CHECKING** の影響を受けない値を **太字** で示します。太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="13dd1-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="13dd1-106">**nx_telnet_client_connect**: *Telnet クライアントを IPv4 アドレスで接続します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="13dd1-107">**nxd_telnet_client_connect**: *IPv6 Telnet クライアントを IPv6 アドレスで接続します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="13dd1-108">**nx_telnet_client_create**: *Telnet クライアントを作成します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="13dd1-109">**nx_telnet_client_delete**: *Telnet クライアントを削除します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="13dd1-110">**nx_telnet_client_disconnect**: *Telnet クライアントの接続を切断します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="13dd1-111">**nx_telnet_client_packet_receive**: *Telnet クライントを通じてパケットを受信します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="13dd1-112">**nx_telnet_client_packet_send**: *Telnet クライアントを通じてパケットを送信します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="13dd1-113">**nx_telnet_server_create**: *Telnet サーバーを作成します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="13dd1-114">**nx_telnet_server_delete**: *Telnet サーバーを削除します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="13dd1-115">**nx_telnet_server_disconnect**: *Telnet クライアントの接続を切断します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="13dd1-116">**nx_telnet_server_get_open_connection_count**: *有効な接続の数を取得します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="13dd1-117">**nx_telnet_server_packet_send**: *クライアント接続を通じてパケットを送信します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="13dd1-118">**nx_telnet_server_packet_pool_set**: *パケット プールを Telnet サーバーのパケット プールに設定します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="13dd1-119">**nx_telnet_server_start**: *Telnet サーバーを起動します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="13dd1-120">**nx_telnet_server_stop**: *Telnet サーバーを停止します*</span><span class="sxs-lookup"><span data-stu-id="13dd1-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="13dd1-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="13dd1-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="13dd1-122">IPv4 アドレスを使用して Telnet クライアントを接続します</span><span class="sxs-lookup"><span data-stu-id="13dd1-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-123">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13dd1-124">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-124">Description</span></span>

<span data-ttu-id="13dd1-125">このサービスでは、作成済みの Telnet クライアント インスタンスを、指定した IPv4 アドレスとポートを使用して、Telnet サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="13dd1-126">このサービスでは、サーバーの IP アドレスを ULONG 型で NXD_ADDRESS 制御ブロックに挿入し、IP のバージョンを IPv4 に設定してから、次に説明する *nxd_telnet_client_connect* サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-127">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-127">Input Parameters</span></span>

- <span data-ttu-id="13dd1-128">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="13dd1-129">**server_ip**: Telnet サーバーの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="13dd1-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="13dd1-130">**server_port**: サーバーの TCP ポート (Telnet サーバーはポート 23)。</span><span class="sxs-lookup"><span data-stu-id="13dd1-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="13dd1-131">**wait_option**: このサービスで、Telnet クライントが接続するのを待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="13dd1-132">待機オプションは次のように定義されています:</span><span class="sxs-lookup"><span data-stu-id="13dd1-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="13dd1-133">**タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="13dd1-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限で一時停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-135">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-135">Return Values</span></span>

- <span data-ttu-id="13dd1-136">**NX_SUCCESS**: (0x00) クライアント接続に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="13dd1-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) クライアントが接続済み。</span><span class="sxs-lookup"><span data-stu-id="13dd1-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="13dd1-138">NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="13dd1-139">NX_IP_ADDRESS_ERROR: (0x21) 無効な IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="13dd1-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="13dd1-140">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-141">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-141">Allowed From</span></span>

<span data-ttu-id="13dd1-142">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-143">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="13dd1-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="13dd1-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="13dd1-145">IPv6 または IPv4 アドレスを使用して Telnet クライアントを接続します</span><span class="sxs-lookup"><span data-stu-id="13dd1-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-146">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13dd1-147">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-147">Description</span></span>

<span data-ttu-id="13dd1-148">このサービスでは、作成済みの Telnet クライアント インスタンスを、指定した IPv6 アドレスとポートを使用して Telnet サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="13dd1-149">このサービスでは、IPv4 または IPv6 アドレスを使用できますが、それが NXD_ADDRESS の *server_ip_address* 変数に入っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="13dd1-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-150">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-150">Input Parameters</span></span>

- <span data-ttu-id="13dd1-151">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="13dd1-152">**server_ip_address**: サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="13dd1-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="13dd1-153">**server_port**: サーバーの TCP ポート (Telnet サーバーはポート 23)。</span><span class="sxs-lookup"><span data-stu-id="13dd1-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="13dd1-154">**wait_option**: このサービスで、Telnet クライントが接続するのを待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="13dd1-155">待機オプションは次のように定義されています:</span><span class="sxs-lookup"><span data-stu-id="13dd1-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="13dd1-156">**タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="13dd1-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-158">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-158">Return Values</span></span>

- <span data-ttu-id="13dd1-159">**NX_SUCCESS**: (0x00) クライアント接続に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="13dd1-160">**NX_TELNET_ERROR**: (0xF0) クライアント接続エラー。</span><span class="sxs-lookup"><span data-stu-id="13dd1-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="13dd1-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) クライアントが接続済み。</span><span class="sxs-lookup"><span data-stu-id="13dd1-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="13dd1-162">NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="13dd1-163">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="13dd1-164">NX_TELNET_INVALID_PARAMETER: (0xF5) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="13dd1-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-165">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-165">Allowed From</span></span>

<span data-ttu-id="13dd1-166">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-167">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="13dd1-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="13dd1-168">nx_telnet_client_create</span></span>

<span data-ttu-id="13dd1-169">Telnet クライアントを作成します</span><span class="sxs-lookup"><span data-stu-id="13dd1-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-170">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="13dd1-171">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-171">Description</span></span>

<span data-ttu-id="13dd1-172">このサービスでは、Telnet クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-173">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-173">Input Parameters</span></span>

- <span data-ttu-id="13dd1-174">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="13dd1-175">**client_name**: クライアント インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="13dd1-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="13dd1-176">**ip_ptr**: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="13dd1-177">**window_size**: このクライアントの TCP 受信ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="13dd1-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-178">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-178">Return Values</span></span>

- <span data-ttu-id="13dd1-179">**NX_SUCCESS**: (0x00) クライアントの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="13dd1-180">**NX_TELNET_ERROR**: (0xF0) ソケット作成エラー。</span><span class="sxs-lookup"><span data-stu-id="13dd1-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="13dd1-181">NX_PTR_ERROR: (0x07) 無効なクライアントまたは IP アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-182">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-182">Allowed From</span></span>

<span data-ttu-id="13dd1-183">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="13dd1-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-184">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="13dd1-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="13dd1-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="13dd1-186">Telnet クライアントを削除します</span><span class="sxs-lookup"><span data-stu-id="13dd1-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-187">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="13dd1-188">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-188">Description</span></span>

<span data-ttu-id="13dd1-189">このサービスでは、作成済みの Telnet クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-190">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-190">Input Parameters</span></span>

- <span data-ttu-id="13dd1-191">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-192">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-192">Return Values</span></span>

- <span data-ttu-id="13dd1-193">**NX_SUCCESS**: (0x00) クライアントの削除に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="13dd1-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) クライアントが接続されたままです。</span><span class="sxs-lookup"><span data-stu-id="13dd1-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="13dd1-195">NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="13dd1-196">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-197">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-197">Allowed From</span></span>

<span data-ttu-id="13dd1-198">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-199">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="13dd1-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="13dd1-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="13dd1-201">Telnet クライアントの接続を切断します</span><span class="sxs-lookup"><span data-stu-id="13dd1-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-202">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13dd1-203">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-203">Description</span></span>

<span data-ttu-id="13dd1-204">このサービスでは、接続済みの Telnet クライアント インスタンスの接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-205">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-205">Input Parameters</span></span>

- <span data-ttu-id="13dd1-206">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="13dd1-207">**wait_option**: このサービスで、Telnet クライアントの接続の切断を待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="13dd1-208">待機オプションは次のように定義されています:</span><span class="sxs-lookup"><span data-stu-id="13dd1-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="13dd1-209">**タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="13dd1-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-211">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-211">Return Values</span></span>

- <span data-ttu-id="13dd1-212">**NX_SUCCESS**: (0x00) クライアント接続切断に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="13dd1-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) クライアントが未接続。</span><span class="sxs-lookup"><span data-stu-id="13dd1-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="13dd1-214">NX_PTR_ERROR: (0x07) クライアントへの無効なポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="13dd1-215">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="13dd1-216">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-216">Allowed From</span></span>

<span data-ttu-id="13dd1-217">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-218">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="13dd1-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="13dd1-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="13dd1-220">Telnet クライアントを通じてパケットを受信します</span><span class="sxs-lookup"><span data-stu-id="13dd1-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-221">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13dd1-222">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-222">Description</span></span>

<span data-ttu-id="13dd1-223">このサービスでは、接続済みの Telnet クライアント インスタンスからパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-224">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-224">Input Parameters</span></span>

- <span data-ttu-id="13dd1-225">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="13dd1-226">**packet_ptr**: 受信パケットの保存先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="13dd1-227">**wait_option**: このサービスで、Telnet クライアントによりパケットを受信するのを待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="13dd1-228">待機オプションは次のように定義されています:</span><span class="sxs-lookup"><span data-stu-id="13dd1-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="13dd1-229">**タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="13dd1-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-231">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-231">Return Values</span></span>

- <span data-ttu-id="13dd1-232">**NX_SUCCESS**: (0x00) クライアントによるパケットの受信に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="13dd1-233">NX_PTR_ERROR: (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="13dd1-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13dd1-234">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-235">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-235">Allowed From</span></span>

<span data-ttu-id="13dd1-236">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-237">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="13dd1-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="13dd1-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="13dd1-239">Telnet クライアントを通じてパケットを送信します</span><span class="sxs-lookup"><span data-stu-id="13dd1-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-240">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13dd1-241">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-241">Description</span></span>

<span data-ttu-id="13dd1-242">このサービスでは、接続済みの Telnet クライアント インスタンスを通じてパケットを送信します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-243">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-243">Input Parameters</span></span>

- <span data-ttu-id="13dd1-244">**client_ptr**: Telnet クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="13dd1-245">**packet_ptr**: 送信するパケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="13dd1-246">**wait_option**: このサービスで、Telnet クライアントからパケットが送信されるのを待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="13dd1-247">待機オプションは次のように定義されています:</span><span class="sxs-lookup"><span data-stu-id="13dd1-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="13dd1-248">**タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="13dd1-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-250">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-250">Return Values</span></span>

- <span data-ttu-id="13dd1-251">**NX_SUCCESS**: (0x00) クライアントパケット送信に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="13dd1-252">**NX_TELNET_ERROR**: (0xF0) パケットの送信に失敗 – 呼び出し元がパケットを解放します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="13dd1-253">NX_PTR_ERROR: (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="13dd1-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13dd1-254">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-255">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-255">Allowed From</span></span>

<span data-ttu-id="13dd1-256">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-257">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="13dd1-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="13dd1-258">nx_telnet_server_create</span></span>

<span data-ttu-id="13dd1-259">Telnet サーバーを作成します</span><span class="sxs-lookup"><span data-stu-id="13dd1-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-260">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="13dd1-261">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-261">Description</span></span>

<span data-ttu-id="13dd1-262">このサービスでは、指定した IP インスタンスに Telnet サーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-263">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-263">Input Parameters</span></span>

- <span data-ttu-id="13dd1-264">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="13dd1-265">**server_name**: Telnet サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="13dd1-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="13dd1-266">**ip_ptr**: 関連付けられた IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="13dd1-267">**stack_ptr**: サーバー内部のスレッド スタックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="13dd1-268">**sack_size**: バイト単位のスタック サイズ。</span><span class="sxs-lookup"><span data-stu-id="13dd1-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="13dd1-269">**new_connection**: アプリケーション コールバック ルーチン関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="13dd1-270">新しい Telnet クライアント接続要求をサーバーで検出するたびに、このルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="13dd1-271">**receive_data**: アプリケーション コールバック ルーチン関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="13dd1-272">新しい Telnet クライアント データが接続に持ち込まれるたびに、このルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="13dd1-273">パケットの解放はこのルーチンによって行います。</span><span class="sxs-lookup"><span data-stu-id="13dd1-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="13dd1-274">**end_connection**: アプリケーション コールバック ルーチン関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="13dd1-275">Telnet クライアントの接続がクライアントによって切断されるたびに、またはクライアント接続がタイムアウトする (“操作タイムアウト” になる) たびに、このルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="13dd1-276">サーバーでは、次に説明する *nx_telnet_server_disconnect* サービスを使用して接続を切断することもできます。</span><span class="sxs-lookup"><span data-stu-id="13dd1-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-277">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-277">Return Values</span></span>

- <span data-ttu-id="13dd1-278">**NX_SUCCESS**: (0x00) サーバーの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="13dd1-279">NX_PTR_ERROR: (0x07) サーバー、IP アドレス、スタック、またはアプリケーション コールバックへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-280">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-280">Allowed From</span></span>

<span data-ttu-id="13dd1-281">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="13dd1-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-282">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="13dd1-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="13dd1-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="13dd1-284">Telnet サーバーを削除します</span><span class="sxs-lookup"><span data-stu-id="13dd1-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-285">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="13dd1-286">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-286">Description</span></span>

<span data-ttu-id="13dd1-287">このサービスでは、作成済みの Telnet サーバー インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-288">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-288">Input Parameters</span></span>

- <span data-ttu-id="13dd1-289">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-290">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-290">Return Values</span></span>

- <span data-ttu-id="13dd1-291">**NX_SUCCESS**: (0x00) サーバーの削除に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="13dd1-292">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="13dd1-293">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-294">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-294">Allowed From</span></span>

<span data-ttu-id="13dd1-295">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-296">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="13dd1-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="13dd1-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="13dd1-298">Telnet クライアントの接続を切断します</span><span class="sxs-lookup"><span data-stu-id="13dd1-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-299">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="13dd1-300">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-300">Description</span></span>

<span data-ttu-id="13dd1-301">このサービスでは、この Telnet サーバー インスタンス上で接続済みのクライアントの接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="13dd1-302">このルーチンは通常、受信したデータで検出された状態へ応答として、アプリケーションの受信データ コールバック関数で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="13dd1-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-303">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-303">Input Parameters</span></span>

- <span data-ttu-id="13dd1-304">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="13dd1-305">**logical_connection**: このサーバー上のクライアント接続に対応する論理接続。</span><span class="sxs-lookup"><span data-stu-id="13dd1-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="13dd1-306">有効な値の範囲は 0 - NX_TELENET_MAX_CLIENTS です。</span><span class="sxs-lookup"><span data-stu-id="13dd1-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-307">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-307">Return Values</span></span>

- <span data-ttu-id="13dd1-308">**NX_SUCCESS**: (0x00) サーバーの接続切断に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="13dd1-309">**NX_TELNET_ERROR**: (0xF0) サーバーの接続切断に失敗。</span><span class="sxs-lookup"><span data-stu-id="13dd1-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="13dd1-310">NX_OPTION_ERROR: (0x0A) 無効な論理接続。</span><span class="sxs-lookup"><span data-stu-id="13dd1-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="13dd1-311">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="13dd1-312">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-313">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-313">Allowed From</span></span>

<span data-ttu-id="13dd1-314">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-315">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="13dd1-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="13dd1-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="13dd1-317">現在有効な接続の数を返します</span><span class="sxs-lookup"><span data-stu-id="13dd1-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-318">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="13dd1-319">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-319">Description</span></span>

<span data-ttu-id="13dd1-320">このサービスでは、接続中の Telnet クライアントの数を返します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-321">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-321">Input Parameters</span></span>

- <span data-ttu-id="13dd1-322">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="13dd1-323">**Connection_count**: 接続数を保存するメモリへのポインター</span><span class="sxs-lookup"><span data-stu-id="13dd1-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-324">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-324">Return Values</span></span>

- <span data-ttu-id="13dd1-325">**NX_SUCCESS**: (0x00) 完了。</span><span class="sxs-lookup"><span data-stu-id="13dd1-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="13dd1-326">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="13dd1-327">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-328">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-328">Allowed From</span></span>

<span data-ttu-id="13dd1-329">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-330">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="13dd1-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="13dd1-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="13dd1-332">クライアント接続を通じてパケットを送信します</span><span class="sxs-lookup"><span data-stu-id="13dd1-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-333">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13dd1-334">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-334">Description</span></span>

<span data-ttu-id="13dd1-335">このサービスでは、この Telnet サーバー インスタンス上のクライアント接続にパケットを送信します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="13dd1-336">このルーチンは通常、受信したデータで検出された状態へ応答として、アプリケーションの受信データ コールバック関数で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="13dd1-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-337">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-337">Input Parameters</span></span>

- <span data-ttu-id="13dd1-338">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="13dd1-339">**logical_connection**: このサーバー上のクライアント接続に対応する論理接続。</span><span class="sxs-lookup"><span data-stu-id="13dd1-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="13dd1-340">有効な値の範囲は 0 - NX_TELENET_MAX_CLIENTS です。</span><span class="sxs-lookup"><span data-stu-id="13dd1-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="13dd1-341">**packet_ptr**: 受信パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="13dd1-342">**wait_option**: このサービスで、Telnet サーバーからパケットが送信されるのを待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="13dd1-343">待機オプションは次のように定義されています:</span><span class="sxs-lookup"><span data-stu-id="13dd1-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="13dd1-344">**タイムアウトの値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択して、Telnet サーバーの応答を待つ間一時停止を続ける最長時間をタイマー刻み単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="13dd1-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、Telnet サーバーが要求に応答するまで、呼び出しスレッドを無期限に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="13dd1-346">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-346">Return Values</span></span>

- <span data-ttu-id="13dd1-347">**NX_SUCCESS**: (0x00) パケットの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="13dd1-348">**NX_TELNET_FAILED**: (0xF2) TCP ソケットによる送信に失敗。</span><span class="sxs-lookup"><span data-stu-id="13dd1-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="13dd1-349">NX_OPTION_ERROR: (0x0A) 無効な論理接続。</span><span class="sxs-lookup"><span data-stu-id="13dd1-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="13dd1-350">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="13dd1-351">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-352">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-352">Allowed From</span></span>

<span data-ttu-id="13dd1-353">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-354">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="13dd1-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="13dd1-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="13dd1-356">作成済みのパケット プールを Telnet サーバーのパケット プールに設定します</span><span class="sxs-lookup"><span data-stu-id="13dd1-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-357">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="13dd1-358">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-358">Description</span></span>

<span data-ttu-id="13dd1-359">このサービスでは、NX_TELNET_SERVER_USER_CREATE_PACKET_POOL が有効である場合、作成済みのパケット プールを Telnet サーバーのパケット プールに設定します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="13dd1-360">また、このサービスを使用するには、X_TELNET_SERVER_OPTION_DISABLE が有効になっておらず、Telnet オプションを Telnet クライアントに送信するためのパケット プールが Telnet サーバーに必要であることも必要です。</span><span class="sxs-lookup"><span data-stu-id="13dd1-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="13dd1-361">このサービスにより、アプリケーションで、Telnet サーバーのスタック以外のメモリ (キャッシュ メモリ以外のメモリなど) にパケット プールを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="13dd1-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="13dd1-362">この関数では、Telnet サーバーのパケット プールが既に設定されていないかどうかを確認しません。</span><span class="sxs-lookup"><span data-stu-id="13dd1-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="13dd1-363">Telnet サーバーのパケット プールへの NULL でないポインターでこれを呼び出した場合、入力したポインターが指し示すパケット プールで既存のパケット プールを置き換えて上書きします。</span><span class="sxs-lookup"><span data-stu-id="13dd1-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-364">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-364">Input Parameters</span></span>

- <span data-ttu-id="13dd1-365">**server_ptr**: Telnet サーバー制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="13dd1-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="13dd1-366">**packet_pool_ptr**: 作成済みパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="13dd1-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-367">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-367">Return Values</span></span>

- <span data-ttu-id="13dd1-368">**NX_SUCCESS**: (0x00) プールの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="13dd1-369">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-370">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-370">Allowed From</span></span>

<span data-ttu-id="13dd1-371">Init、スレッド</span><span class="sxs-lookup"><span data-stu-id="13dd1-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-372">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="13dd1-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="13dd1-373">nx_telnet_server_start</span></span>

<span data-ttu-id="13dd1-374">Telnet サーバーを起動します</span><span class="sxs-lookup"><span data-stu-id="13dd1-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-375">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="13dd1-376">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-376">Description</span></span>

<span data-ttu-id="13dd1-377">このサービスでは、作成済みの Telnet サーバー インスタンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-378">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-378">Input Parameters</span></span>

- <span data-ttu-id="13dd1-379">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-380">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-380">Return Values</span></span>

- <span data-ttu-id="13dd1-381">**NX_SUCCESS**: (0x00) 開始に成功。</span><span class="sxs-lookup"><span data-stu-id="13dd1-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="13dd1-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) パケット プールが実設定</span><span class="sxs-lookup"><span data-stu-id="13dd1-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="13dd1-383">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-384">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-384">Allowed From</span></span>

<span data-ttu-id="13dd1-385">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="13dd1-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-386">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="13dd1-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="13dd1-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="13dd1-388">Telnet サーバーを停止します</span><span class="sxs-lookup"><span data-stu-id="13dd1-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="13dd1-389">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="13dd1-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="13dd1-390">説明</span><span class="sxs-lookup"><span data-stu-id="13dd1-390">Description</span></span>

<span data-ttu-id="13dd1-391">このサービスでは、作成・開始済みの Telnet サーバー インスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="13dd1-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13dd1-392">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="13dd1-392">Input Parameters</span></span>

- <span data-ttu-id="13dd1-393">**server_ptr**: Telnet サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="13dd1-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="13dd1-394">戻り値</span><span class="sxs-lookup"><span data-stu-id="13dd1-394">Return Values</span></span>

- <span data-ttu-id="13dd1-395">**NX_SUCCESS**: (0x00) 停止に成功</span><span class="sxs-lookup"><span data-stu-id="13dd1-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="13dd1-396">NX_PTR_ERROR: (0x07) サーバーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="13dd1-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="13dd1-397">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="13dd1-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13dd1-398">許可元</span><span class="sxs-lookup"><span data-stu-id="13dd1-398">Allowed From</span></span>

<span data-ttu-id="13dd1-399">Threads</span><span class="sxs-lookup"><span data-stu-id="13dd1-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13dd1-400">例</span><span class="sxs-lookup"><span data-stu-id="13dd1-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```