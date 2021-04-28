---
title: 第 3 章 - Azure RTOS NetX Duo DHCP クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX Duo DHCP クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810934"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="6dac4-103">第 3 章 - Azure RTOS NetX Duo DHCP クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="6dac4-104">この章では、すべての Azure RTOS NetX Duo DHCP クライアント サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="6dac4-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="6dac4-106">**nx_dhcp_create**: "*DHCP インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="6dac4-107">**nx_dhcp_clear_broadcast_flag**: "*クライアント メッセージのブロードキャスト フラグをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="6dac4-108">**nx_dhcp_delete**: "*DHCP インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="6dac4-109">**nx_dhcp_force_renew**: "*強制更新メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="6dac4-110">**nx_dhcp_packet_pool_set**: "*DHCP クライアントのパケット プールを設定する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="6dac4-111">**nx_dhcp_decline**: "*サーバーに Decline メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="6dac4-112">**nx_dhcp_release**: "*サーバーに Release メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="6dac4-113">**nx_dhcp_reinitialize**: "*DHCP クライアントのネットワーク パラメーターをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="6dac4-114">**nx_dhcp_request_client_ip**: "*特定の IP アドレスを指定する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="6dac4-115">**nx_dhcp_send_request**: "*サーバーに DHCP メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="6dac4-116">**nx_dhcp_start**: "*DHCP クライアントの処理を開始する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="6dac4-117">**nx_dhcp_start**: "*DHCP クライアントの処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="6dac4-118">**nx_dhcp_set_interface_index**: "*DHCP クライアントを実行するインターフェイスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="6dac4-119">**nx_dhcp_server_address_get**: "*DHCP サーバー IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="6dac4-120">**nx_dhcp_state_change_notify**: "*DHCP の状態が変更されたときのコールバック関数を設定する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="6dac4-121">**nx_dhcp_user_option_retrieve**: "*指定された DHCP オプションを取得する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="6dac4-122">**nx_dhcp_user_option_convert**: "*4 バイトを ULONG に変換する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="6dac4-123">インターフェイス固有の DHCP クライアント サービス:</span><span class="sxs-lookup"><span data-stu-id="6dac4-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="6dac4-124">**nx_dhcp_interface_clear_broadcast_flag**: "*指定されたインターフェイスでクライアント メッセージのブロードキャスト フラグをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="6dac4-125">**nx_dhcp_interface_enable**: "*指定されたインターフェイスで DHCP を実行するためのインターフェイスを有効にする*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="6dac4-126">**nx_dhcp_interface_disable**: "*指定されたインターフェイスで DHCP を実行するためのインターフェイスを無効にする*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="6dac4-127">**nx_dhcp_interface_decline**: "*指定されたインターフェイスでサーバーに Decline メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="6dac4-128">**nx_dhcp_interface_force_renew**: "*指定されたインターフェイスで強制更新メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="6dac4-129">**nx_dhcp_interface_reinitialize**: "*指定されたインターフェイスの DHCP クライアントのネットワーク パラメーターをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="6dac4-130">**nx_dhcp_interface_release**: "*指定されたインターフェイスでサーバーに Release メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="6dac4-131">**nx_dhcp_interface_request_client_ip**: "*指定されたインターフェイスで特定の IP アドレスを指定する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="6dac4-132">**nx_dhcp_interface_send_request**: "*指定されたインターフェイスでサーバーに DHCP メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="6dac4-133">**nx_dhcp_interface_server_address_get**: "*指定されたインターフェイスで DHCP サーバー IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="6dac4-134">**nx_dhcp_interface_start**: "*指定されたインターフェイスで DHCP クライアントの処理を開始する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="6dac4-135">**nx_dhcp_interface_stop**: "*指定されたインターフェイスで DHCP クライアントの処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="6dac4-136">**nx_dhcp_interface_state_change_notify**: "*指定されたインターフェイスで DHCP の状態が変更されたときのコールバック関数を設定する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="6dac4-137">**nx_dhcp_interface_user_option_retrieve**: "*指定されたインターフェイスで指定された DHCP オプションを取得する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="6dac4-138">NX_DHCP_CLIENT_RESORE_STATE が定義されている場合の DHCP クライアント サービス:</span><span class="sxs-lookup"><span data-stu-id="6dac4-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="6dac4-139">**nx_dhcp_resume**: "*以前に確立された DHCP クライアントの状態を再開する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="6dac4-140">**nx_dhcp_suspend**: "*DHCP クライアントの状態の処理を中断する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="6dac4-141">**nx_dhcp_client_get_record**: "*DHCP クライアントの状態のレコードを作成する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="6dac4-142">**nx_dhcp_client_restore_record**: "*以前に保存されたレコードを DHCP クライアントに復元する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="6dac4-143">**nx_dhcp_client_update_time_remaining**: "*DHCP の現在の状態の残り時間を更新する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="6dac4-144">NX_DHCP_CLIENT_RESORE_STATE が定義されている場合のインターフェイス固有の DHCP クライアント サービス:</span><span class="sxs-lookup"><span data-stu-id="6dac4-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="6dac4-145">**nx_dhcp_client_interface_get_record**: "*指定されたインターフェイスで DHCP クライアントの状態のレコードを作成する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="6dac4-146">**nx_dhcp_client_interface_restore_record**: "*以前に保存されたレコードを、指定されたインターフェイスの DHCP クライアントに復元する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="6dac4-147">**nx_dhcp_client_interface_update_time_remaining**: "*指定されたインターフェイスの DHCP の現在の状態の残り時間を更新する*"</span><span class="sxs-lookup"><span data-stu-id="6dac4-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="6dac4-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="6dac4-148">nx_dhcp_create</span></span>

<span data-ttu-id="6dac4-149">DHCP インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="6dac4-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-150">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-151">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-151">Description</span></span>

<span data-ttu-id="6dac4-152">このサービスでは、以前に作成された IP インスタンスの DHCP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="6dac4-153">既定では、DHCP を実行するためのプライマリ インターフェイスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="6dac4-154">DHCP クライアントの NetX Duo 実装では使用されませんが、入力する名前は RFC 1035 のホスト名の基準に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="6dac4-155">全体の長さは 255 文字以下にする必要があります。ドットで区切られたラベルは、文字で始まり、文字または数字で終わる必要があります。また、ハイフンを含めることはできますが、その他の英数字以外の文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="6dac4-156">アプリケーションで、(*nx_ip_interface_attach* を使用して) IP インスタンスに登録された別の DHCP インターフェイスを実行する場合、*nx_dhcp_set_interface_index* を呼び出すと、そのインターフェイスだけで DHCP を実行でき、*nx_dhcp_interface_enable* を呼び出すと、そのインターフェイスでも DHCP を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="6dac4-157">詳細については、これらのサービスの説明をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="6dac4-158">アプリケーションでは、RFC 2131 セクション 2 で指定されている DHCP メッセージの最小サイズ (548 バイトの DHCP メッセージ データに、UDP、IP、物理ネットワーク フレームの各ヘッダーを加えたサイズ) を、DHCP クライアントのパケット プールのペイロードでサポートできることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-159">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-159">Input Parameters</span></span>

- <span data-ttu-id="6dac4-160">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="6dac4-161">**ip_ptr**: 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="6dac4-162">**name_ptr**: DHCP インスタンスのホスト名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-163">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-163">Return Values</span></span>

- <span data-ttu-id="6dac4-164">**NX_SUCCESS**: (0x00) DHCP が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="6dac4-165">**NX_DHCP_INVALID_NAME**: (0xA8) ホスト名が無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="6dac4-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) DHCP メッセージに対してペイロードが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="6dac4-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="6dac4-167">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-168">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-168">Allowed From</span></span>

<span data-ttu-id="6dac4-169">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="6dac4-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-170">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="6dac4-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="6dac4-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="6dac4-172">DHCP を実行するための指定されたインターフェイスを有効にする</span><span class="sxs-lookup"><span data-stu-id="6dac4-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="6dac4-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-174">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-174">Description</span></span>

<span data-ttu-id="6dac4-175">このサービスは、DHCP を実行するための指定されたインターフェイスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="6dac4-176">既定では、DHCP クライアントのプライマリ インターフェイスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="6dac4-177">この時点で、*nx_dhcp_interface_start* を呼び出して、このインターフェイスで DHCP を開始することも、*nx_dhcp_start* を呼び出して、すべての有効なインターフェイスで DHCP を開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="6dac4-178">アプリケーションでは、*nx_ip_interface_attach* を使用して、まずこのインターフェイスを IP インスタンスに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="6dac4-179">さらに、有効なインターフェイスのリストにこのインターフェイスを追加するために、DHCP クライアント インターフェイスの使用可能な "レコード" が必要です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="6dac4-180">既定では、NX_DHCP_CLIENT_MAX_RECORDS は 1 に定義されています。</span><span class="sxs-lookup"><span data-stu-id="6dac4-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="6dac4-181">このオプションを、DHCP クライアントを同時に実行することが予想されるインターフェイスの最大数に設定します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="6dac4-182">通常、NX_DHCP_CLIENT_MAX_RECORDS は NX_MAX_PHYSICAL_INTERFACES と等しくなります。ただし、DHCP クライアントを実行することが予想されるインターフェイスの数よりも多くの物理インターフェイスがデバイスにある場合は、NX_DHCP_CLIENT_MAX_RECORDS をその数よりも小さい値に設定することによって、メモリを節約できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="6dac4-183">物理インターフェイスと DHCP クライアント インターフェイスのレコードのマッピングは 1 対 1 ではありません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="6dac4-184">このサービスと *nx_dhcp_set_interface_index* の違いは、後者では DHCP を実行するためのインターフェイスを 1 つだけ設定するのに対し、このサービスでは、DHCP が有効になっているクライアント インターフェイスのリストに、指定されたインターフェイスを追加するだけであることです。</span><span class="sxs-lookup"><span data-stu-id="6dac4-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="6dac4-185">DHCP 用のインターフェイスを無効にするには、アプリケーションで</span><span class="sxs-lookup"><span data-stu-id="6dac4-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="6dac4-186">*nx_dhcp_interface_disable* サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-187">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-187">Input Parameters</span></span>

- <span data-ttu-id="6dac4-188">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6dac4-189">**interface_index**: DHCP を有効にするインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-190">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-190">Return Values</span></span>

- <span data-ttu-id="6dac4-191">**NX_SUCCESS**: (0x00) DHCP が正常に有効になりました</span><span class="sxs-lookup"><span data-stu-id="6dac4-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="6dac4-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) DHCP を有効にする別のインターフェイスの使用可能なレコードがありません</span><span class="sxs-lookup"><span data-stu-id="6dac4-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) インターフェイスで DHCP が有効になっています</span><span class="sxs-lookup"><span data-stu-id="6dac4-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-194">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="6dac4-195">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-196">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-196">Allowed From</span></span>

<span data-ttu-id="6dac4-197">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="6dac4-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-198">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="6dac4-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="6dac4-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="6dac4-200">DHCP を実行するための指定されたインターフェイスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6dac4-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="6dac4-201">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-202">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-202">Description</span></span>

<span data-ttu-id="6dac4-203">このサービスは、DHCP を実行するための指定されたインターフェイスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="6dac4-204">このインターフェイスの DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="6dac4-205">DHCP クライアントを再起動するには、アプリケーションで *nx_dhcp_interface_enable* を使用してインターフェイスを再度有効にし、*nx_dhcp_interface_start* を呼び出して DHCP を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-206">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-206">Input Parameters</span></span>

- <span data-ttu-id="6dac4-207">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6dac4-208">**interface_index**: DHCP を無効にするインターフェイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="6dac4-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-209">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-209">Return Values</span></span>

- <span data-ttu-id="6dac4-210">**NX_SUCCESS**: (0x00) DHCP が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="6dac4-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-212">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="6dac4-213">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="6dac4-214">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-215">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-215">Allowed From</span></span>

<span data-ttu-id="6dac4-216">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-217">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="6dac4-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="6dac4-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="6dac4-219">DHCP ブロードキャスト フラグを設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-220">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="6dac4-221">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-221">Description</span></span>

<span data-ttu-id="6dac4-222">このサービスは、DHCP が有効になっているすべてのインターフェイスの DHCP メッセージ ヘッダーのブロードキャスト フラグを設定またはクリアします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6dac4-223">一部の DHCP メッセージ (DISCOVER など) では、クライアントに IP アドレスがないため、ブロードキャスト フラグがブロードキャストに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="6dac4-224">clear_flag 値:</span><span class="sxs-lookup"><span data-stu-id="6dac4-224">clear_flag values:</span></span> 

- <span data-ttu-id="6dac4-225">**NX_TRUE**: ブロードキャスト フラグがクリアされます (ユニキャスト応答を要求します)</span><span class="sxs-lookup"><span data-stu-id="6dac4-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="6dac4-226">**NX_FALSE**: ブロードキャスト フラグが設定されます (ブロードキャスト応答を要求します)</span><span class="sxs-lookup"><span data-stu-id="6dac4-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="6dac4-227">このサービスは、ルーター経由で DHCP サーバーにアクセスする必要がある DHCP クライアントを対象としています。そのルーターでブロードキャスト メッセージの転送が拒否されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-228">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-228">Input Parameters</span></span>

- <span data-ttu-id="6dac4-229">**dhcp_ptr**: DHCP 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="6dac4-230">**clear_flag**: ブロードキャスト フラグの設定値</span><span class="sxs-lookup"><span data-stu-id="6dac4-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-231">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-231">Return Values</span></span>

- <span data-ttu-id="6dac4-232">**NX_SUCCESS**: (0x00) フラグが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="6dac4-233">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-234">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-234">Allowed From</span></span>

<span data-ttu-id="6dac4-235">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="6dac4-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-236">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="6dac4-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="6dac4-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="6dac4-238">指定されたインターフェイスでブロードキャスト フラグを設定またはクリアする</span><span class="sxs-lookup"><span data-stu-id="6dac4-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-239">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="6dac4-240">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-240">Description</span></span>

<span data-ttu-id="6dac4-241">このサービスを使用すると、DHCP クライアント ホスト アプリケーションは、指定されたインターフェイスで、DHCP サーバーへの DHCP クライアント メッセージのブロードキャスト フラグを設定またはクリアできます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="6dac4-242">詳細については、「**nx_dhcp_clear_broadcast_flag**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-243">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-243">Input Parameters</span></span>

- <span data-ttu-id="6dac4-244">**dhcp_ptr**: DHCP 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="6dac4-245">**interface_index**: ブロードキャスト フラグを設定するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="6dac4-246">**clear_flag**: ブロードキャスト フラグの設定値</span><span class="sxs-lookup"><span data-stu-id="6dac4-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-247">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-247">Return Values</span></span>

- <span data-ttu-id="6dac4-248">**NX_SUCCESS**: (0x00) フラグが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="6dac4-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-250">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="6dac4-251">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-252">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-252">Allowed From</span></span>

<span data-ttu-id="6dac4-253">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="6dac4-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-254">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="6dac4-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="6dac4-255">nx_dhcp_delete</span></span>

<span data-ttu-id="6dac4-256">DHCP インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="6dac4-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-257">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-258">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-258">Description</span></span>

<span data-ttu-id="6dac4-259">このサービスは、以前に作成された DHCP インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-260">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-260">Input Parameters</span></span>

- <span data-ttu-id="6dac4-261">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-262">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-262">Return Values</span></span>

- <span data-ttu-id="6dac4-263">**NX_SUCCESS**: (0x00) DHCP が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="6dac4-264">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-265">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-266">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-266">Allowed From</span></span>

<span data-ttu-id="6dac4-267">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-268">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="6dac4-269">nx_dhcp_force_renew</span><span class="sxs-lookup"><span data-stu-id="6dac4-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="6dac4-270">強制更新メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="6dac4-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="6dac4-271">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-272">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-272">Description</span></span>

<span data-ttu-id="6dac4-273">このサービスを使用すると、ホスト アプリケーションは、DHCP が有効になっているすべてのインターフェイスで強制更新メッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6dac4-274">DHCP クライアントは、BOUND 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="6dac4-275">この関数によって状態が RENEW に設定され、T1 タイムアウトになる前に DHCP クライアントは更新を試みるようになります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="6dac4-276">複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスで強制更新を送信するには、*nx_dhcp_interface_force_renew* を使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-277">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-277">Input Parameters</span></span>

- <span data-ttu-id="6dac4-278">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-279">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-279">Return Values</span></span>

- <span data-ttu-id="6dac4-280">**NX_SUCCESS**: (0x00) 強制更新が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="6dac4-281">**NX_DHCP_NOT_BOUND**: (0x94) クライアント IP アドレスがバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="6dac4-282">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-283">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-284">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-284">Allowed From</span></span>

<span data-ttu-id="6dac4-285">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-286">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="6dac4-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="6dac4-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="6dac4-288">指定されたインターフェイスで強制更新メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="6dac4-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-289">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-290">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-290">Description</span></span>

<span data-ttu-id="6dac4-291">このサービスを使用すると、ホスト アプリケーションは、入力インターフェイスで DHCP が有効になっていれば (「*nx_dhcp_interface_enable*」を参照)、そのインターフェイスで強制更新メッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="6dac4-292">指定されたインターフェイスの DHCP クライアントは、BOUND 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="6dac4-293">この関数によって状態が RENEW に設定され、T1 タイムアウトになる前に DHCP クライアントは更新を試みるようになります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-294">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-294">Input Parameters</span></span>

- <span data-ttu-id="6dac4-295">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-296">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-296">Return Values</span></span>

- <span data-ttu-id="6dac4-297">**NX_SUCCESS**: (0x00) 強制更新が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="6dac4-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-299">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="6dac4-300">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-301">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-301">Allowed From</span></span>

<span data-ttu-id="6dac4-302">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-303">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="6dac4-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="6dac4-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="6dac4-305">DHCP クライアントのパケット プールを設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-306">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-307">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-307">Description</span></span>

<span data-ttu-id="6dac4-308">このサービスを使用すると、アプリケーションは、以前に作成されたパケット プールへのポインターをこのサービス呼び出しで渡すことによって、DHCP クライアントのパケット プールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="6dac4-309">この機能を使用するには、ホスト アプリケーションで NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="6dac4-310">定義すると、*nx_dhcp_create* サービスでクライアントのパケット プールは作成されなくなります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="6dac4-311">アプリケーションでは、パケット プールを作成するときに、*nxd_dhcp_client.h* で NX_DHCP_PACKET_PAYLOAD として定義されている、DHCP クライアントのパケット プールのペイロードの既定値を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-312">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-312">Input Parameters</span></span>

- <span data-ttu-id="6dac4-313">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6dac4-314">**packet_pool_ptr**: 以前に作成されたパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-315">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-315">Return Values</span></span>

- <span data-ttu-id="6dac4-316">**NX_SUCCESS**: (0x00) DHCP クライアントのパケット プールが設定されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="6dac4-317">**NX_NOT_ENABLED**: (0x14) サービスが有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="6dac4-318">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) ペイロードが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="6dac4-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-320">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-320">Allowed From</span></span>

<span data-ttu-id="6dac4-321">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="6dac4-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-322">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="6dac4-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="6dac4-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="6dac4-324">DHCP インスタンスの要求された IP アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-325">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="6dac4-326">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-326">Description</span></span>

<span data-ttu-id="6dac4-327">このサービスは、DHCP クライアント レコードの DHCP が有効になっている最初のインターフェイスで、DHCP クライアントが DHCP サーバーに要求する IP アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="6dac4-328">*skip_discover_message* フラグが設定されている場合、DHCP クライアントは Discover メッセージをスキップし、Request メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="6dac4-329">特定のインターフェイスで DHCP メッセージに特定の IP の要求を設定するには、*nx_dhcp_interface_request_client_ip* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-330">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-330">Input Parameters</span></span>

- <span data-ttu-id="6dac4-331">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6dac4-332">**client_ip_address**: DHCP サーバーに要求する IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="6dac4-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="6dac4-333">**skip_discover_message**:</span><span class="sxs-lookup"><span data-stu-id="6dac4-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="6dac4-334">true の場合、DHCP クライアントは Request メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="6dac4-335">false の場合、Discover メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-336">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-336">Return Values</span></span>

- <span data-ttu-id="6dac4-337">**NX_SUCCESS**: (0x00) 要求された IP アドレスが設定されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="6dac4-338">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) 要求された IP アドレスが NULL です</span><span class="sxs-lookup"><span data-stu-id="6dac4-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-340">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-340">Allowed From</span></span>

<span data-ttu-id="6dac4-341">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-342">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="6dac4-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="6dac4-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="6dac4-344">指定されたインターフェイスで DHCP インスタンスの要求された IP アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-345">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="6dac4-346">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-346">Description</span></span>

<span data-ttu-id="6dac4-347">このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に (「*nx_dhcp_interface_enable*」を参照)、そのインターフェイスで DHCP クライアントが DHCP サーバーに要求する IP アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="6dac4-348">*skip_discover_message* フラグが設定されている場合、DHCP クライアントは Discover メッセージをスキップし、Request メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-349">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-349">Input Parameters</span></span>

- <span data-ttu-id="6dac4-350">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="6dac4-351">**Interface_index**: IP アドレスを要求するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="6dac4-352">**client_ip_address**: DHCP サーバーに要求する IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="6dac4-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="6dac4-353">**skip_discover_message**: true の場合、DHCP クライアントは Request メッセージを送信します。それ以外の場合は、Discover メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-354">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-354">Return Values</span></span>

- <span data-ttu-id="6dac4-355">**NX_SUCCESS**: (0x00) 要求された IP アドレスが設定されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="6dac4-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-357">NX_PTR_ERROR: (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="6dac4-358">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-359">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-359">Allowed From</span></span>

<span data-ttu-id="6dac4-360">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-361">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="6dac4-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="6dac4-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="6dac4-363">DHCP クライアントのネットワーク パラメーターをクリアする</span><span class="sxs-lookup"><span data-stu-id="6dac4-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="6dac4-364">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-365">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-365">Description</span></span>

<span data-ttu-id="6dac4-366">このサービスは、ホスト アプリケーションのネットワーク パラメーター (IP アドレス、ネットワーク アドレス、ネットワーク マスク) をクリアし、DHCP が有効になっているすべてのインターフェイスの DHCP クライアントの状態をクリアします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6dac4-367">DHCP ステート マシンを "再起動" するために、*nx_dhcp_stop* および *nx_dhcp_start* と組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="6dac4-368">複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスの DHCP クライアントを再初期化するには、*nx_dhcp_interface_reinitialize* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-369">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-369">Input Parameters</span></span>

- <span data-ttu-id="6dac4-370">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-371">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-371">Return Values</span></span>

- <span data-ttu-id="6dac4-372">**NX_SUCCESS**: (0x00) DHCP が正常に再初期化されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="6dac4-373">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-374">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-374">Allowed From</span></span>

<span data-ttu-id="6dac4-375">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-376">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="6dac4-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="6dac4-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="6dac4-378">指定されたインターフェイスの DHCP クライアントのネットワーク パラメーターをクリアする</span><span class="sxs-lookup"><span data-stu-id="6dac4-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="6dac4-379">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-380">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-380">Description</span></span>

<span data-ttu-id="6dac4-381">このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に (「*nx_dhcp_interface_enable*」を参照)、そのインターフェイスのネットワーク パラメーター (IP アドレス、ネットワーク アドレス、ネットワーク マスク) をクリアします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="6dac4-382">詳細については、「*nx_dhcp_reinitialize*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-383">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-383">Input Parameters</span></span>

- <span data-ttu-id="6dac4-384">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="6dac4-385">**interface_index**: 再初期化するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-386">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-386">Return Values</span></span>

- <span data-ttu-id="6dac4-387">**NX_SUCCESS**: (0x00) インターフェイスが正常に再初期化されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="6dac4-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-389">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-390">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="6dac4-391">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-392">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-392">Allowed From</span></span>

<span data-ttu-id="6dac4-393">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-394">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="6dac4-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="6dac4-395">nx_dhcp_release</span></span>

<span data-ttu-id="6dac4-396">リースした IP アドレスを解放する</span><span class="sxs-lookup"><span data-stu-id="6dac4-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-397">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-398">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-398">Description</span></span>

<span data-ttu-id="6dac4-399">このサービスは、DHCP サーバーに RELEASE メッセージを送信することによって、そのサーバーから取得した IP アドレスを解放します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="6dac4-400">その後、DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="6dac4-401">このサービスは、DHCP が有効になっているすべてのインターフェイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="6dac4-402">アプリケーションでは、*nx_dhcp_start* を呼び出すことによって DHCP クライアントを再起動できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="6dac4-403">特定のインターフェイスでアドレスを解放して DHCP サーバーに返却するには、*nx_dhcp_interface_release* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-404">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-404">Input Parameters</span></span>

- <span data-ttu-id="6dac4-405">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-406">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-406">Return Values</span></span>

- <span data-ttu-id="6dac4-407">**NX_SUCCESS**: (0x00) DHCP が正常に解放されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="6dac4-408">**NX_DHCP_NOT_BOUND**: (0x94) IP アドレスがリースされていないため、解放できません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="6dac4-409">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-410">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-411">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-411">Allowed From</span></span>

<span data-ttu-id="6dac4-412">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-413">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="6dac4-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="6dac4-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="6dac4-415">指定されたインターフェイスで IP アドレスを解放する</span><span class="sxs-lookup"><span data-stu-id="6dac4-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-416">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-417">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-417">Description</span></span>

<span data-ttu-id="6dac4-418">このサービスは、指定されたインターフェイスで DHCP サーバーから取得した IP アドレスを解放し、DHCP クライアントを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="6dac4-419">*nx_dhcp_start* を呼び出すことによって、DHCP クライアントを再起動できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-420">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-420">Input Parameters</span></span>

- <span data-ttu-id="6dac4-421">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-422">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-422">Return Values</span></span>

- <span data-ttu-id="6dac4-423">**NX_SUCCESS**: (0x00) DHCP が正常に解放されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="6dac4-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-425">**NX_DHCP_NOT_BOUND**: (0x94) IP アドレスがリースされていないため、解放できません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="6dac4-426">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-427">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="6dac4-428">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-429">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-429">Allowed From</span></span>

<span data-ttu-id="6dac4-430">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-431">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="6dac4-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="6dac4-432">nx_dhcp_decline</span></span>

<span data-ttu-id="6dac4-433">DHCP サーバーからの IP アドレスを拒否する</span><span class="sxs-lookup"><span data-stu-id="6dac4-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-434">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-435">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-435">Description</span></span>

<span data-ttu-id="6dac4-436">このサービスは、DHCP が有効になっているすべてのインターフェイスで、DHCP サーバーからリースされた IP アドレスを拒否します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6dac4-437">NX_DHCP_CLIENT_SEND_ARP_PROBE が定義されている場合、DHCP クライアントはその IP アドレスが既に使用されていることを検出すると、DECLINE メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="6dac4-438">NetX Duo DHCP クライアントでの ARP プローブの構成の詳細については、第 1 章の **ARP プローブ** に関する説明をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="6dac4-439">アプリケーションでは、IP アドレスが他の方法で使用されていることを検出した場合に、このサービスを使用してそのアドレスを拒否できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="6dac4-440">このサービスは、*nx_dhcp_start* を呼び出して再起動できるように、DHCP クライアントを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-441">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-441">Input Parameters</span></span>

- <span data-ttu-id="6dac4-442">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-443">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-443">Return Values</span></span>

- <span data-ttu-id="6dac4-444">**NX_SUCCESS**: (0x00) 拒否が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="6dac4-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP クライアントがバインドされていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="6dac4-446">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-447">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-448">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-448">Allowed From</span></span>

<span data-ttu-id="6dac4-449">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-450">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="6dac4-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="6dac4-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="6dac4-452">指定されたインターフェイスで DHCP サーバーからの IP アドレスを拒否する</span><span class="sxs-lookup"><span data-stu-id="6dac4-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-453">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-454">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-454">Description</span></span>

<span data-ttu-id="6dac4-455">このサービスは、サーバーに DECLINE メッセージを送信して、DHCP サーバーによって割り当てられた IP アドレスを拒否します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="6dac4-456">また、DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="6dac4-457">詳細については、「*nx_dhcp_decline*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-458">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-458">Input Parameters</span></span>

- <span data-ttu-id="6dac4-459">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-460">**Interface_index**: IP アドレスを拒否するインターフェイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="6dac4-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-461">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-461">Return Values</span></span>

- <span data-ttu-id="6dac4-462">**NX_SUCCESS**: (0x00) DHCP 拒否メッセージが送信されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="6dac4-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP クライアントがバインドされていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="6dac4-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-465">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-466">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="6dac4-467">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-468">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-468">Allowed From</span></span>

<span data-ttu-id="6dac4-469">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-470">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="6dac4-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="6dac4-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="6dac4-472">サーバーに DHCP メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="6dac4-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-473">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="6dac4-474">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-474">Description</span></span>

<span data-ttu-id="6dac4-475">このサービスは、DHCP クライアント レコードで最初に見つかった、DHCP が有効になっているインターフェイスで、指定された DHCP メッセージを DHCP サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="6dac4-476">RELEASE または DECLINE メッセージを送信するには、アプリケーションで *nx_dhcp[_interface]_release()* または *nx_dhcp_interface_decline()* サービスをそれぞれ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="6dac4-477">種類が INFORM_REQUEST のメッセージを送信する場合を除き、このサービスを使用するには DHCP クライアントを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="6dac4-478">このサービスは、ホスト アプリケーションで DHCP クライアント ステート マシンを "駆動" するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-479">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-479">Input Parameters</span></span>

- <span data-ttu-id="6dac4-480">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6dac4-481">**dhcp_message_type**: メッセージ要求 (*nxd_dhcp_client.h* で定義)</span><span class="sxs-lookup"><span data-stu-id="6dac4-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-482">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-482">Return Values</span></span>

- <span data-ttu-id="6dac4-483">**NX_SUCCESS**: (0x00) DHCP メッセージが送信されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="6dac4-484">**NX_DHCP_NOT_STARTED**: (0x96) インターフェイス インデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="6dac4-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) 送信するメッセージの種類が無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="6dac4-486">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-487">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-487">Allowed From</span></span>

<span data-ttu-id="6dac4-488">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-489">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="6dac4-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="6dac4-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="6dac4-491">特定のインターフェイスでサーバーに DHCP メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="6dac4-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-492">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="6dac4-493">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-493">Description</span></span>

<span data-ttu-id="6dac4-494">このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP サーバーにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6dac4-495">RELEASE または DECLINE メッセージを送信するには、アプリケーションで *nx_dhcp[_interface]_release()* または *nx_dhcp_interface_decline()* サービスをそれぞれ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="6dac4-496">種類が DHCP INFORM REQUEST のメッセージを送信する場合を除き、このサービスを使用するには DHCP クライアントを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="6dac4-497">このサービスは、ホスト アプリケーションで DHCP クライアント ステート マシンを "駆動" するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-498">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-498">Input Parameters</span></span>

- <span data-ttu-id="6dac4-499">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="6dac4-500">**Interface_index**: メッセージを送信するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="6dac4-501">**dhcp_message_type**: メッセージ要求 (nxd_dhcp_client.h で定義)</span><span class="sxs-lookup"><span data-stu-id="6dac4-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-502">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-502">Return Values</span></span>

- <span data-ttu-id="6dac4-503">**NX_SUCCESS**: (0x00) DHCP メッセージが送信されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="6dac4-504">**NX_DHCP_NOT_STARTED**: (0x96) インターフェイス インデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="6dac4-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) 送信するメッセージの種類が無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="6dac4-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-507">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-508">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="6dac4-509">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-510">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-510">Allowed From</span></span>

<span data-ttu-id="6dac4-511">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-512">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="6dac4-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="6dac4-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="6dac4-514">DHCP クライアントの DHCP サーバー IP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="6dac4-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-515">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="6dac4-516">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-516">Description</span></span>

<span data-ttu-id="6dac4-517">このサービスは、DHCP クライアント レコードで最初に見つかった、DHCP が有効になっているインターフェイスで、DHCP クライアントの DHCP サーバー IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="6dac4-518">DHCP サーバーによって割り当てられた IP アドレスに DHCP クライアントがバインドされた後にのみ、呼び出し元でこのサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="6dac4-519">ホスト アプリケーションでは、*nx_ip_status_check* サービスを使用して、IP アドレスが設定されていることを確認できます。また、*nx_dhcp_state_change_notify* を使用し、DHCP クライアントの状態が NX_DHCP_STATE_BOUND であることを照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="6dac4-520">状態変更コールバック関数の設定の詳細については、「*nx_dhcp_state_change_notify*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="6dac4-521">DHCP クライアントの複数のインターフェイスが有効になっている場合に、特定のインターフェイスで DHCP サーバーを検索するには、*nx_dhcp_interface_server_address_get* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-522">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-522">Input Parameters</span></span>

- <span data-ttu-id="6dac4-523">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="6dac4-524">**server_address**: サーバー IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-525">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-525">Return Values</span></span>

- <span data-ttu-id="6dac4-526">**NX_SUCCESS**: (0x00) DHCP サーバー アドレスが返されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="6dac4-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="6dac4-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-528">NX_PTR_ERROR: (0x16) 入力ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="6dac4-529">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-530">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-530">Allowed From</span></span>

<span data-ttu-id="6dac4-531">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-532">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="6dac4-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="6dac4-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="6dac4-534">指定されたインターフェイスで DHCP クライアントの DHCP サーバー IP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="6dac4-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-535">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="6dac4-536">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-536">Description</span></span>

<span data-ttu-id="6dac4-537">このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP クライアントの DHCP サーバー IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6dac4-538">DHCP クライアントは、BOUND 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="6dac4-539">そのインターフェイスの DHCP クライアントを起動した後に、ホスト アプリケーションでは、*nx_ip_status_check* サービスを使用して、IP アドレスが設定されていることを確認できます。また、DHCP クライアントの状態変更コールバックを使用し、DHCP クライアントの状態が NX_DHCP_STATE_BOUND であることを照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="6dac4-540">状態変更コールバック関数の設定の詳細については、「*nx_dhcp_state_change_notify*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-541">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-541">Input Parameters</span></span>

- <span data-ttu-id="6dac4-542">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="6dac4-543">**Interface_index**: IP アドレスを取得するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="6dac4-544">**server_address**: サーバー IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-545">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-545">Return Values</span></span>

- <span data-ttu-id="6dac4-546">**NX_SUCCESS**: (0x00) DHCP サーバー アドレスが返されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="6dac4-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="6dac4-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP クライアントがバインドされていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="6dac4-549">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="6dac4-550">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="6dac4-551">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-552">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-552">Allowed From</span></span>

<span data-ttu-id="6dac4-553">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-554">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="6dac4-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="6dac4-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="6dac4-556">DHCP インスタンスのネットワーク インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-557">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="6dac4-558">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-558">Description</span></span>

<span data-ttu-id="6dac4-559">このサービスは、単一のネットワーク インターフェイス用に構成された DHCP クライアントを実行する場合に、DHCP サーバーに接続するための DHCP インスタンスのネットワーク インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="6dac4-560">既定では、DHCP クライアントはプライマリ インターフェイスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="6dac4-561">セカンダリ サービスで DHCP を実行するには、このサービスを使用して、セカンダリ インターフェイスを DHCP クライアント インターフェイスとして設定します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="6dac4-562">アプリケーションでは、*nx_ip_interface_attach* サービスを使用して、指定されたインターフェイスを IP インスタンスに事前に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="6dac4-563">このサービスは、1 つのインターフェイスでのみ DHCP クライアントを実行することを目的としたアプリケーションを対象としています。</span><span class="sxs-lookup"><span data-stu-id="6dac4-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="6dac4-564">複数のインターフェイスで DHCP を実行する方法の詳細については、「*nx_dhcp_interface_enable*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-565">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-565">Input Parameters</span></span>

- <span data-ttu-id="6dac4-566">**dhcp_ptr**: DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6dac4-567">**index**: デバイスのネットワーク インターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-568">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-568">Return Values</span></span>

- <span data-ttu-id="6dac4-569">**NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="6dac4-570">**NX_INVALID_INTERFACE**: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="6dac4-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) インターフェイスで DHCP が有効になっています</span><span class="sxs-lookup"><span data-stu-id="6dac4-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) 別のインターフェイスの使用可能なレコードがありません</span><span class="sxs-lookup"><span data-stu-id="6dac4-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="6dac4-573">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-574">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-574">Allowed From</span></span>

<span data-ttu-id="6dac4-575">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-576">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="6dac4-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="6dac4-577">nx_dhcp_start</span></span>

<span data-ttu-id="6dac4-578">DHCP の処理を開始する</span><span class="sxs-lookup"><span data-stu-id="6dac4-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-579">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-580">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-580">Description</span></span>

<span data-ttu-id="6dac4-581">このサービスは、DHCP が有効になっているすべてのインターフェイスで DHCP の処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6dac4-582">既定では、アプリケーションで *nx_dhcp_create* を呼び出すと、DHCP のプライマリ インターフェイスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="6dac4-583">DHCP クライアント インターフェイスで、IP インスタンスが IP アドレスにバインドされていることを確認するには、*nx_ip_status_check* を使用して、IP アドレスが有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="6dac4-584">DHCP が既に実行されている他のインターフェイスがある場合、それらはこのサービスの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="6dac4-585">複数のインターフェイスが有効になっている場合に、特定のインターフェイスで DHCP を開始するには、*nx_dhcp_interface_start* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-586">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-586">Input Parameters</span></span>

- <span data-ttu-id="6dac4-587">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-588">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-588">Return Values</span></span>

- <span data-ttu-id="6dac4-589">**NX_SUCCESS**: (0x00) DHCP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="6dac4-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="6dac4-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="6dac4-591">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-592">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-593">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-593">Allowed From</span></span>

<span data-ttu-id="6dac4-594">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-595">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="6dac4-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="6dac4-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="6dac4-597">指定されたインターフェイスで DHCP の処理を開始する</span><span class="sxs-lookup"><span data-stu-id="6dac4-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-598">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-599">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-599">Description</span></span>

<span data-ttu-id="6dac4-600">このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP の処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6dac4-601">インターフェイスで DHCP を有効にする方法の詳細については、「*nx_dhcp_interface_enable*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="6dac4-602">既定では、アプリケーションで *nx_dhcp_create* を呼び出すと、DHCP のプライマリ インターフェイスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="6dac4-603">DHCP クライアントが実行されている他のインターフェイスがない場合、このサービスは DHCP クライアントのスレッドを開始または再開し、DHCP クライアントのタイマーを (再) アクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="6dac4-604">アプリケーションで *nx_ip_status_check* を使用して、IP アドレスが取得されたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-605">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-605">Input Parameters</span></span>

- <span data-ttu-id="6dac4-606">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-607">**Interface_index**: DHCP クライアントを起動するインデックス</span><span class="sxs-lookup"><span data-stu-id="6dac4-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-608">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-608">Return Values</span></span>

- <span data-ttu-id="6dac4-609">**NX_SUCCESS**: (0x00) DHCP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="6dac4-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="6dac4-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="6dac4-611">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-612">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="6dac4-613">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-614">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-614">Allowed From</span></span>

<span data-ttu-id="6dac4-615">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-616">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="6dac4-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="6dac4-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="6dac4-618">DHCP 状態変更コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-619">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="6dac4-620">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-620">Description</span></span>

<span data-ttu-id="6dac4-621">このサービスは、DHCP の状態変更をアプリケーションに通知するために、指定されたコールバック関数 dhcp_state_change_notify を登録します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="6dac4-622">このコールバック関数では、DHCP クライアントの遷移後の状態が示されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="6dac4-623">DHCP のさまざまな状態に関連付けられている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="6dac4-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="6dac4-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="6dac4-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="6dac4-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="6dac4-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="6dac4-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="6dac4-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="6dac4-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="6dac4-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="6dac4-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="6dac4-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="6dac4-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="6dac4-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="6dac4-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="6dac4-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="6dac4-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="6dac4-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="6dac4-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-633">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-633">Input Parameters</span></span>

- <span data-ttu-id="6dac4-634">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-635">**dhcp_state_change_notify**: 状態変更コールバック関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-636">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-636">Return Values</span></span>

- <span data-ttu-id="6dac4-637">**NX_SUCCESS**: (0x00) コールバックが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="6dac4-638">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-639">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-640">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-640">Allowed From</span></span>

<span data-ttu-id="6dac4-641">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="6dac4-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-642">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="6dac4-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="6dac4-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="6dac4-644">指定されたインターフェイスで DHCP 状態変更コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-645">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="6dac4-646">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-646">Description</span></span>

<span data-ttu-id="6dac4-647">このサービスは、DHCP の状態変更をアプリケーションに通知するために、指定されたコールバック関数を登録します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="6dac4-648">このコールバック関数の入力引数は、インターフェイス インデックスと、そのインターフェイスでの DHCP クライアントの遷移後の状態です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="6dac4-649">状態変更関数の詳細については、「*nx_dhcp_state_change_notify*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-650">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-650">Input Parameters</span></span>

- <span data-ttu-id="6dac4-651">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-652">**dhcp_interface_state_change_notify**: アプリケーションのコールバック関数ポインター</span><span class="sxs-lookup"><span data-stu-id="6dac4-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-653">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-653">Return Values</span></span>

- <span data-ttu-id="6dac4-654">**NX_SUCCESS**: (0x00) コールバックが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="6dac4-655">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-656">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-656">Allowed From</span></span>

<span data-ttu-id="6dac4-657">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="6dac4-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-658">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="6dac4-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="6dac4-659">nx_dhcp_stop</span></span>

<span data-ttu-id="6dac4-660">DHCP の処理を停止する</span><span class="sxs-lookup"><span data-stu-id="6dac4-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-661">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-662">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-662">Description</span></span>

<span data-ttu-id="6dac4-663">このサービスは、DHCP の処理が開始されているすべてのインターフェイスで DHCP の処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="6dac4-664">DHCP を処理しているインターフェイスがない場合、このサービスは DHCP クライアントのスレッドを中断し、DHCP クライアントのタイマーを非アクティブにします。</span><span class="sxs-lookup"><span data-stu-id="6dac4-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="6dac4-665">複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスで DHCP を停止するには、*nx_dhcp_interface_stop* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-666">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-666">Input Parameters</span></span>

- <span data-ttu-id="6dac4-667">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-668">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-668">Return Values</span></span>

- <span data-ttu-id="6dac4-669">**NX_SUCCESS**: (0x00) DHCP が正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="6dac4-670">**NX_DHCP_NOT_STARTED**: (0x96) DHCP インスタンスが開始されていません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="6dac4-671">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-672">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-673">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-673">Allowed From</span></span>

<span data-ttu-id="6dac4-674">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-675">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="6dac4-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="6dac4-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="6dac4-677">指定されたインターフェイスで DHCP の処理を停止する</span><span class="sxs-lookup"><span data-stu-id="6dac4-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-678">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6dac4-679">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-679">Description</span></span>

<span data-ttu-id="6dac4-680">このサービスは、DHCP が既に開始されている場合に、指定されたインターフェイスで DHCP の処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="6dac4-681">DHCP が実行されている他のインターフェイスがない場合は、DHCP のスレッドとタイマーが中断されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-682">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-682">Input Parameters</span></span>

- <span data-ttu-id="6dac4-683">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-684">**Interface_index**: DHCP の処理を停止するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6dac4-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-685">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-685">Return Values</span></span>

- <span data-ttu-id="6dac4-686">**NX_SUCCESS**: (0x00) DHCP が正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="6dac4-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="6dac4-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP が開始されていません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="6dac4-688">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-689">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="6dac4-690">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-691">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-691">Allowed From</span></span>

<span data-ttu-id="6dac4-692">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-693">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="6dac4-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="6dac4-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="6dac4-695">最後のサーバー応答から DHCP オプションを取得する</span><span class="sxs-lookup"><span data-stu-id="6dac4-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-696">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="6dac4-697">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-697">Description</span></span>

<span data-ttu-id="6dac4-698">このサービスは、DHCP クライアント レコードで最初に見つかった、DHCP が有効になっているインターフェイスで、DHCP オプションのバッファーから指定された DHCP オプションを取得します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="6dac4-699">成功すると、そのオプションのデータが指定されたバッファーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-700">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-700">Input Parameters</span></span>

- <span data-ttu-id="6dac4-701">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="6dac4-702">**request_option**: RFC で指定されている DHCP オプション。</span><span class="sxs-lookup"><span data-stu-id="6dac4-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="6dac4-703">*nxd_dhcp_client.h* の NX_DHCP_OPTION オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="6dac4-704">**destination_ptr**: 応答文字列のコピー先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="6dac4-705">**destination_size**: コピー先のサイズへのポインター。戻り時に、返されたバイト数がコピー先に配置されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-706">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-706">Return Values</span></span>

- <span data-ttu-id="6dac4-707">**NX_SUCCESS**: (0x00) オプションが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="6dac4-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP クライアントがバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="6dac4-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="6dac4-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="6dac4-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) コピー先が小さすぎて応答を保持できません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="6dac4-711">**NX_DHCP_PARSE_ERROR**: (0x97) サーバー応答でオプションが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="6dac4-712">NX_PTR_ERROR: (0x16) 入力ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="6dac4-713">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-714">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-714">Allowed From</span></span>

<span data-ttu-id="6dac4-715">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-716">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="6dac4-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="6dac4-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="6dac4-718">指定されたインターフェイスで、最後のサーバー応答から DHCP オプションを取得する</span><span class="sxs-lookup"><span data-stu-id="6dac4-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-719">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="6dac4-720">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-720">Description</span></span>

<span data-ttu-id="6dac4-721">このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで、DHCP オプションのバッファーから指定された DHCP オプションを取得します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6dac4-722">成功すると、そのオプションのデータが指定されたバッファーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-723">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-723">Input Parameters</span></span>

- <span data-ttu-id="6dac4-724">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-725">**Interface_index**: 指定されたオプションを取得するインデックス。</span><span class="sxs-lookup"><span data-stu-id="6dac4-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="6dac4-726">**request_option**: RFC で指定されている DHCP オプション。</span><span class="sxs-lookup"><span data-stu-id="6dac4-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="6dac4-727">*nxd_dhcp_client.h* の NX_DHCP_OPTION オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dac4-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="6dac4-728">**destination_ptr**: 応答文字列のコピー先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="6dac4-729">**destination_size**: コピー先のサイズへのポインター。戻り時に、返されたバイト数がコピー先に配置されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-730">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-730">Return Values</span></span>

- <span data-ttu-id="6dac4-731">**NX_SUCCESS**: (0x00) オプションが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="6dac4-732">**NX_DHCP_NOT_BOUND**: (0x94) IP アドレスが割り当てられていません</span><span class="sxs-lookup"><span data-stu-id="6dac4-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="6dac4-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) バッファーが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="6dac4-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="6dac4-734">**NX_DHCP_PARSE_ERROR**: (0x97) サーバー応答で DHCP オプションが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="6dac4-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="6dac4-735">NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6dac4-736">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="6dac4-737">NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="6dac4-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-738">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-738">Allowed From</span></span>

<span data-ttu-id="6dac4-739">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-740">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="6dac4-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="6dac4-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="6dac4-742">4 バイトを ULONG に変換する</span><span class="sxs-lookup"><span data-stu-id="6dac4-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-743">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="6dac4-744">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-744">Description</span></span>

<span data-ttu-id="6dac4-745">このサービスは、"option_string_ptr" が指す 4 文字を符号なし long 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="6dac4-746">これは、複数の IP アドレスが存在する場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-746">It is especially useful when IP addresses are</span></span>  
present.

### <a name="input-parameters"></a><span data-ttu-id="6dac4-748">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-748">Input Parameters</span></span>

- <span data-ttu-id="6dac4-749">**option_string_ptr**: 以前に取得されたオプション文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-750">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-750">Return Values</span></span>

- <span data-ttu-id="6dac4-751">**Value**: 最初の 4 バイトの値。</span><span class="sxs-lookup"><span data-stu-id="6dac4-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-752">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-752">Allowed From</span></span>

<span data-ttu-id="6dac4-753">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-754">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="6dac4-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="6dac4-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="6dac4-756">ユーザーが指定したオプションを追加するためにコールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="6dac4-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="6dac4-757">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="6dac4-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="6dac4-758">説明</span><span class="sxs-lookup"><span data-stu-id="6dac4-758">Description</span></span>

<span data-ttu-id="6dac4-759">このサービスは、ユーザーが指定したオプションを追加するために、指定されたコールバック関数を登録します。</span><span class="sxs-lookup"><span data-stu-id="6dac4-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="6dac4-760">このコールバック関数が指定されている場合、アプリケーションでは iface_index と message_type を使用して、ユーザーが指定したオプションをパケットに追加できます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="6dac4-761">ユーザーのルーチンで。</span><span class="sxs-lookup"><span data-stu-id="6dac4-761">In user’s routine.</span></span> <span data-ttu-id="6dac4-762">アプリケーションは、ユーザーが指定したオプションを追加するときに、DHCP オプションの形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="6dac4-763">ユーザー オプションの合計サイズは user_option_length 以下である必要があり、user_option_length を実際のオプションの長さで更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dac4-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="6dac4-764">オプションが正常に追加された場合は NX_TRUE が返され、それ以外の場合は NX_FALSE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6dac4-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6dac4-765">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6dac4-765">Input Parameters</span></span>

- <span data-ttu-id="6dac4-766">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="6dac4-767">**dhcp_user_option_add**: ユーザー オプション追加関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6dac4-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="6dac4-768">戻り値</span><span class="sxs-lookup"><span data-stu-id="6dac4-768">Return Values</span></span>

- <span data-ttu-id="6dac4-769">**NX_SUCCESS**: (0x00) コールバックが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="6dac4-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="6dac4-770">NX_PTR_ERROR (0x16): ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="6dac4-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6dac4-771">許可元</span><span class="sxs-lookup"><span data-stu-id="6dac4-771">Allowed From</span></span>

<span data-ttu-id="6dac4-772">Threads</span><span class="sxs-lookup"><span data-stu-id="6dac4-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6dac4-773">例</span><span class="sxs-lookup"><span data-stu-id="6dac4-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

