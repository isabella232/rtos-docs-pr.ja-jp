---
title: 第 3 章 - Azure RTOS NetX DHCP クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX DHCP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811612"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="8d5e0-103">第 3 章 - Azure RTOS NetX DHCP クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="8d5e0-104">この章では、すべての Azure RTOS NetX DHCP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="8d5e0-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にする際に使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="8d5e0-106">**nx_dhcp_create**: "*DHCP インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="8d5e0-107">**nx_dhcp_clear_broadcast_flag**: クライアント メッセージのブロードキャスト フラグをクリアする</span><span class="sxs-lookup"><span data-stu-id="8d5e0-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="8d5e0-108">**nx_dhcp_delete**: "*DHCP インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="8d5e0-109">**nx_dhcp_decline**: "*サーバーに拒否メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="8d5e0-110">**nx_dhcp_force_renew**: "*強制更新メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="8d5e0-111">**nx_dhcp_packet_pool_set**: "*DHCP クライアントのパケット プールを設定する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="8d5e0-112">**nx_dhcp_release**: "*リリース メッセージをサーバーに送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="8d5e0-113">**nx_dhcp_reinitialize**: "*DHCP クライアントのネットワーク パラメーターをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="8d5e0-114">**nx_dhcp_request_client_ip**: "*特定の IP アドレスを指定する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="8d5e0-115">**nx_dhcp_send_request**: "*DHCP メッセージをサーバーに送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="8d5e0-116">**nx_dhcp_server_address_get**: "*DHCP クライアントの DHCP サーバー アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="8d5e0-117">**nx_dhcp_set_interface_index**: "*クライアントのネットワーク インターフェイスを指定する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="8d5e0-118">**nx_dhcp_start**: "*DHCP 処理を開始する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="8d5e0-119">**nx_dhcp_state_change_notify**: "*DHCP の状態の変更をアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="8d5e0-120">**nx_dhcp_stop**: "*DHCP の処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="8d5e0-121">**nx_dhcp_user_option_retrieve**: "*DHCP のオプションを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="8d5e0-122">**nx_dhcp_user_option_convert**: "*4 バイトを ULONG に変換する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="8d5e0-123">インターフェイス固有の DHCP クライアント サービス:</span><span class="sxs-lookup"><span data-stu-id="8d5e0-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="8d5e0-124">**nx_dhcp_interface_clear_broadcast_flag**: "*指定されたインターフェイスのクライアント メッセージのブロードキャスト フラグをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="8d5e0-125">**nx_dhcp_interface_enable**: "*指定されたインターフェイスで DHCP を実行するためのインターフェイスを有効にする*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-126">**nx_dhcp_interface_disable**: "*指定されたインターフェイスで DHCP を実行するためのインターフェイスを無効にする*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-127">**nx_dhcp_interface_decline**: "*指定されたインターフェイスでサーバーに拒否メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-128">**nx_dhcp_interface_force_renew**: "*指定されたインターフェイスに強制更新メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-129">**nx_dhcp_interface_reinitialize**: "*指定されたインターフェイスで DHCP クライアントのネットワーク パラメーターをクリアする*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-130">**nx_dhcp_interface_release**: "*指定されたインターフェイスでサーバーにリリース メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-131">**nx_dhcp_interface_request_client_ip**: "*指定されたインターフェイスに特定の IP アドレスを指定する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-132">**nx_dhcp_interface_release**: "*指定されたインターフェイスでサーバーに DHCP メッセージを送信する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-133">**nx_dhcp_interface_server_address_get**: "*指定されたインターフェイスで DHCP サーバーの IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-134">**nx_dhcp_interface_start**: "*指定されたインターフェイスで DHCP クライアント処理を開始する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-135">**nx_dhcp_interface_stop**: "*指定されたインターフェイスで DHCP クライアント処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-136">**nx_dhcp_interface_state_change_notify**: "*DHCP の状態が変更されたときのコールバック関数を指定されたインターフェイスに設定する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-137">**nx_dhcp_interface_user_option_retrieve**: "*指定されたインターフェイスで指定された DHCP オプションを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="8d5e0-138">NX_DHCP_CLIENT_RESORE_STATE が定義されている場合の DHCP クライアント サービス:</span><span class="sxs-lookup"><span data-stu-id="8d5e0-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="8d5e0-139">**nx_dhcp_resume**: "*以前に確立された DHCP クライアントの状態を再開する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="8d5e0-140">**nx_dhcp_suspend**: "*DHCP クライアントの状態の処理を中断する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="8d5e0-141">**nx_dhcp_client_get_record**: "*DHCP クライアントの状態のレコードを作成する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="8d5e0-142">**nx_dhcp_client_restore_record**: "*以前に保存されたレコードを DHCP クライアントに復元する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="8d5e0-143">**nx_dhcp_client_update_time_remaining**: "*現在の DHCP の状態の残り時間を更新する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="8d5e0-144">NX_DHCP_CLIENT_RESORE_STATE が定義されている場合のインターフェイス固有の DHCP クライアント サービス:</span><span class="sxs-lookup"><span data-stu-id="8d5e0-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="8d5e0-145">**nx_dhcp_client_interface_get_record**: "*指定されたインターフェイスで DHCP クライアントの状態のレコードを作成する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-146">**nx_dhcp_client_interface_restore_record**: "*以前に保存されたレコードを指定されたインターフェイスの DHCP クライアントに復元する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="8d5e0-147">**nx_dhcp_client_interface_update_time_remaining**: "*指定されたインターフェイスの現在の DHCP の状態の残り時間を更新する*"</span><span class="sxs-lookup"><span data-stu-id="8d5e0-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="8d5e0-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="8d5e0-148">nx_dhcp_create</span></span>

<span data-ttu-id="8d5e0-149">DHCP インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-150">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-151">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-151">Description</span></span>

<span data-ttu-id="8d5e0-152">このサービスでは、以前に作成された IP インスタンスの DHCP インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="8d5e0-153">既定では、DHCP の実行にはプライマリ インターフェイスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="8d5e0-154">DHCP クライアントの NetX 実装では使用されませんが、入力する名前は、RFC 1035 のホスト名の規定に従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="8d5e0-155">合計長は 255 文字以下にする必要があります。ドットで区切られたラベルは、文字で始まり、文字または数字で終わる必要があります。また、ハイフンを含めることはできますが、その他の英数字以外の文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="8d5e0-156">IP インスタンスに登録された DHCP の別のインターフェイス (*nx_ip_interface_attach* を使用して) をアプリケーションで実行する場合、アプリケーションでは *nx_dhcp_set_interface_index* を呼び出してそのインターフェイスだけで DHCP を実行するか、*nx_dhcp_interface_enable* を呼び出してそのインターフェイスでも DHCP を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="8d5e0-157">詳細については、これらのサービスの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="8d5e0-158">アプリケーションでは、RFC 2131 セクション 2 によって指定されている DHCP メッセージの最小サイズ (DHCP メッセージ データ の 548 バイトと UDP、IP、および物理ネットワーク フレームのヘッダー) を DHCP クライアントのパケット プールのペイロードでサポートできることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-159">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-159">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-160">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="8d5e0-161">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="8d5e0-162">**name_ptr** DHCP インスタンスのホスト名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-163">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-163">Return Values</span></span>

- <span data-ttu-id="8d5e0-164">**NX_SUCCESS** (0x00) DHCP が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="8d5e0-165">**NX_DHCP_INVALID_NAME** (0xA8) ホスト名が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="8d5e0-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) DHCP メッセージに対してペイロードが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="8d5e0-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="8d5e0-167">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-168">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-168">Allowed From</span></span>

<span data-ttu-id="8d5e0-169">**スレッド**、初期化</span><span class="sxs-lookup"><span data-stu-id="8d5e0-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-170">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="8d5e0-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="8d5e0-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="8d5e0-172">DHCP を実行するために指定されたインターフェイスを有効にする</span><span class="sxs-lookup"><span data-stu-id="8d5e0-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="8d5e0-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-174">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-174">Description</span></span>

<span data-ttu-id="8d5e0-175">このサービスでは、DHCP を実行するために指定されたインターフェイスが有効にされます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="8d5e0-176">既定では、プライマリ インターフェイスで DHCP クライアントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="8d5e0-177">この時点で、*nx_dhcp_interface_start* を呼び出すとこのインターフェイスで DHCP を開始でき、*nx_dhcp_start* を呼び出すとすべての有効なインターフェイスで DHCP を開始できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="8d5e0-178">アプリケーションでは、*nx_ip_interface_attach* を使用して、まずこのインターフェイスを IP インスタンスに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="8d5e0-179">さらに、有効なインターフェイスの一覧にこのインターフェイスを追加する、使用可能な DHCP クライアント インターフェイスの "レコード" が必要です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="8d5e0-180">既定では NX_DHCP_CLIENT_MAX_RECORDS は 1 に定義されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="8d5e0-181">このオプションには、DHCP クライアントを同時に実行することが予想されるインターフェイスの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="8d5e0-182">通常、NX_DHCP_CLIENT_MAX_RECORDS は NX_MAX_PHYSICAL_INTERFACES と等しくなります。ただし、DHCP クライアントの実行に想定されるよりも多くの物理インターフェイスがデバイスにある場合は、NX_DHCP_CLIENT_MAX_RECORDS をその数値よりも小さい値に設定することによって、メモリを節約できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="8d5e0-183">物理インターフェイスと DHCP クライアント インターフェイス レコードのマッピングは 1 対 1 ではありません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="8d5e0-184">このサービスと *nx_dhcp_set_interface_index* の違いは、後者が DHCP を実行するためのインターフェイスを 1 つだけ設定するのに対し、このサービスでは、DHCP が有効になっているクライアント インターフェイスの一覧に指定されたインターフェイスが単純に追加されることです。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="8d5e0-185">DHCP 用のインターフェイスを無効にするには、アプリケーションで *nx_dhcp_interface_disable* サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-186">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-186">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-187">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="8d5e0-188">**interface_index** DHCP を有効にするインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-189">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-189">Return Values</span></span>

- <span data-ttu-id="8d5e0-190">**NX_SUCCESS** (0x00) DHCP が正常に有効にされました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="8d5e0-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) DHCP を有効にする別のインターフェイスのレコードがありません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP が有効になっているインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-193">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-194">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-195">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-195">Allowed From</span></span>

<span data-ttu-id="8d5e0-196">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="8d5e0-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-197">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="8d5e0-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="8d5e0-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="8d5e0-199">DHCP を実行するために指定されたインターフェイスを無効にする</span><span class="sxs-lookup"><span data-stu-id="8d5e0-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="8d5e0-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-201">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-201">Description</span></span>

<span data-ttu-id="8d5e0-202">このサービスでは、DHCP を実行するために指定されたインターフェイスが無効にされます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="8d5e0-203">このインターフェイスの DHCP クライアント が再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="8d5e0-204">DHCP クライアントを再起動するには、アプリケーションで *nx_dhcp_interface_enable* を使用してインターフェイスを再度有効にし、*nx_dhcp_interface_start* を呼び出して DHCP を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-205">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-205">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-206">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="8d5e0-207">**interface_index** DHCP を無効にするインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-208">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-208">Return Values</span></span>

- <span data-ttu-id="8d5e0-209">**NX_SUCCESS** (0x00) DHCP が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="8d5e0-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-211">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-212">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="8d5e0-213">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-214">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-214">Allowed From</span></span>

<span data-ttu-id="8d5e0-215">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-216">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="8d5e0-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="8d5e0-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="8d5e0-218">DHCP ブロードキャスト フラグを設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-219">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="8d5e0-220">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-220">Description</span></span>

<span data-ttu-id="8d5e0-221">このサービスでは、DHCP が有効になっているすべてのインターフェイスの DHCP メッセージ ヘッダーのブロードキャスト フラグが設定または解除されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-222">一部の DHCP メッセージ (DISCOVER など) の場合、クライアントに IP アドレスがないため、ブロードキャスト フラグがブロードキャストに設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="8d5e0-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="8d5e0-223">__clear_flag__</span></span>


- <span data-ttu-id="8d5e0-224">**NX_TRUE** ブロードキャスト フラグがクリアされました (ユニキャスト応答を要求します)</span><span class="sxs-lookup"><span data-stu-id="8d5e0-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="8d5e0-225">**NX_FALSE** ブロードキャスト フラグが設定されました (ブロードキャスト応答を要求します)</span><span class="sxs-lookup"><span data-stu-id="8d5e0-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="8d5e0-226">このサービスは、ブロードキャスト メッセージの転送が拒否されるルーターを経由して DHCP サーバーにアクセスする必要がある DHCP クライアントを対象としています。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-227">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-227">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-228">**dhcp_ptr** DHCP 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="8d5e0-229">**clear_flag** ブロードキャスト フラグに設定する値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-230">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-230">Return Values</span></span>

- <span data-ttu-id="8d5e0-231">**NX_SUCCESS** (0x00) ブロードキャスト フラグが正常に更新されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="8d5e0-232">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-233">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-234">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-234">Allowed From</span></span>

<span data-ttu-id="8d5e0-235">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="8d5e0-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-236">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="8d5e0-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="8d5e0-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="8d5e0-238">指定したインターフェイスでブロードキャスト フラグを設定または解除する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-239">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="8d5e0-240">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-240">Description</span></span>

<span data-ttu-id="8d5e0-241">このサービスを使用すると、DHCP クライアントのホスト アプリケーションでは、DHCP クライアント メッセージのブロードキャスト フラグを、指定されたインターフェイスの DHCP サーバーに設定するか、クリアすることができます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="8d5e0-242">詳細については、**nx_dhcp_clear_broadcast_flag** を参照してください</span><span class="sxs-lookup"><span data-stu-id="8d5e0-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-243">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-243">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-244">**dhcp_ptr** DHCP 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="8d5e0-245">**interface_index** ブロードキャスト フラグを設定するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="8d5e0-246">**clear_flag** ブロードキャスト フラグに設定する値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-247">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-247">Return Values</span></span>

- <span data-ttu-id="8d5e0-248">**NX_SUCCESS** (0x00) ブロードキャスト フラグが正常に更新されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="8d5e0-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-250">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-251">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-252">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-252">Allowed From</span></span>

<span data-ttu-id="8d5e0-253">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="8d5e0-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-254">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="8d5e0-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="8d5e0-255">nx_dhcp_delete</span></span>

<span data-ttu-id="8d5e0-256">DHCP インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-257">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-258">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-258">Description</span></span>

<span data-ttu-id="8d5e0-259">このサービスでは、以前に作成された DHCP インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-260">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-260">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-261">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-262">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-262">Return Values</span></span>

- <span data-ttu-id="8d5e0-263">**NX_SUCCESS** (0x00) DHCP が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="8d5e0-264">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-265">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-266">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-266">Allowed From</span></span>

<span data-ttu-id="8d5e0-267">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-268">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="8d5e0-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="8d5e0-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="8d5e0-270">強制更新メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="8d5e0-271">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-272">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-272">Description</span></span>

<span data-ttu-id="8d5e0-273">このサービスにより、ホスト アプリケーションでは、DHCP が有効になっているすべてのインターフェイスに対して強制更新メッセージを送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-274">DHCP クライアントは、BOUND 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="8d5e0-275">この関数によって状態が RENEW に設定され、T1 タイムアウトの期限切れになる前に DHCP クライアントで更新が試みられるようになります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="8d5e0-276">複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスに強制更新を送信するには、*nx_dhcp_interface_force_renew* を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-277">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-277">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-278">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-279">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-279">Return Values</span></span>

- <span data-ttu-id="8d5e0-280">**NX_SUCCESS** (0x00) 強制更新が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="8d5e0-281">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-282">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-283">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-283">Allowed From</span></span>

<span data-ttu-id="8d5e0-284">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-285">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="8d5e0-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="8d5e0-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="8d5e0-287">指定されたインターフェイスに強制更新メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-288">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-289">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-289">Description</span></span>

<span data-ttu-id="8d5e0-290">このサービスを使用すると、ホスト アプリケーションでは、入力インターフェイスで DHCP が有効になっている限り (*nx_dhcp_interface_enable* を参照してください)、そのインターフェイスに強制更新のメッセージを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="8d5e0-291">指定されたインターフェイスの DHCP クライアントは、BOUND 状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="8d5e0-292">この関数によって状態が RENEW に設定され、T1 タイムアウトの期限切れになる前に DHCP クライアントで更新が試みられるようになります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-293">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-293">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-294">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-295">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-295">Return Values</span></span>

- <span data-ttu-id="8d5e0-296">**NX_SUCCESS** (0x00) 強制更新が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="8d5e0-297">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-298">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-299">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-300">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-300">Allowed From</span></span>

<span data-ttu-id="8d5e0-301">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-302">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="8d5e0-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="8d5e0-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="8d5e0-304">DHCP クライアントのパケット プールを設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-305">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-306">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-306">Description</span></span>

<span data-ttu-id="8d5e0-307">このサービスを使用すると、アプリケーションでは、以前に作成したパケット プールへのポインターをこのサービス呼び出しに渡すことによって、DHCP クライアントのパケット プールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="8d5e0-308">この機能を使用するには、ホスト アプリケーションで NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="8d5e0-309">定義した場合、*nx_dhcp_create* サービスによってクライアントのパケット プールが作成されません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="8d5e0-310">パケット プールを作成するときには、*nx_dhcp.h* で NX_DHCP_PACKET_PAYLOAD として定義されている、DHCP クライアントのパケット プールのペイロードの既定値をアプリケーションで使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-311">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-311">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-312">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="8d5e0-313">**packet_pool_ptr** 以前に作成されたパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-314">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-314">Return Values</span></span>

- <span data-ttu-id="8d5e0-315">**NX_SUCCESS** (0x00) DHCP クライアントのパケット プールが設定されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="8d5e0-316">**NX_NOT_ENABLED** (0x14) サービスが有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="8d5e0-317">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-318">NX_DHCP_INVALID_PAYLOAD (0x9C) ペイロードが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="8d5e0-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-319">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-319">Allowed From</span></span>

<span data-ttu-id="8d5e0-320">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="8d5e0-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-321">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="8d5e0-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="8d5e0-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="8d5e0-323">DHCP インスタンスの要求された IP アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-324">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="8d5e0-325">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-325">Description</span></span>

<span data-ttu-id="8d5e0-326">このサービスでは、DHCP クライアント レコードの DHCP が有効になっている最初のインターフェイスに、DHCP サーバーに要求した DHCP クライアントの IP アドレスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="8d5e0-327">*skip_discover_message* フラグが設定されている場合、DHCP クライアントでは Discover メッセージをスキップして、Request メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="8d5e0-328">DHCP メッセージの特定の IP に対する要求を特定のインターフェイスに設定するには、*nx_dhcp_interface_request_client_ip* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-329">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-329">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-330">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="8d5e0-331">**client_ip_address** DHCP サーバーに要求する IP アドレス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="8d5e0-332">**skip_discover_message** True の場合、DHCP クライアントでは Request メッセージが送信されます</span><span class="sxs-lookup"><span data-stu-id="8d5e0-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="8d5e0-333">False の場合は、Discover メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-334">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-334">Return Values</span></span>

- <span data-ttu-id="8d5e0-335">**NX_SUCCESS** (0x00) 要求された IP アドレスが設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="8d5e0-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-337">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-338">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="8d5e0-339">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-339">Allowed From</span></span>

<span data-ttu-id="8d5e0-340">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-341">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="8d5e0-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="8d5e0-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="8d5e0-343">指定されたインターフェイスに DHCP インスタンスの要求された IP アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-344">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="8d5e0-345">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-345">Description</span></span>

<span data-ttu-id="8d5e0-346">このサービスでは、指定されたインターフェイスで DHCP が有効になっている (*nx_dhcp_interface_enable* を参照してください) 場合に、DHCP サーバーに要求した DHCP クライアントの IP アドレスがそのインターフェイスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="8d5e0-347">*skip_discover_message* フラグが設定されている場合、DHCP クライアントでは Discover メッセージをスキップして、Request メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-348">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-348">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-349">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="8d5e0-350">**Interface_index** IP アドレスを要求するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="8d5e0-351">**client_ip_address** DHCP サーバーに要求する IP アドレス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="8d5e0-352">**skip_discover_message** True の場合、DHCP クライアントによって Request メッセージが送信されます。それ以外の場合は、Discover メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-353">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-353">Return Values</span></span>

- <span data-ttu-id="8d5e0-354">**NX_SUCCESS** (0x00) 要求された IP アドレスが設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="8d5e0-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-356">NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-357">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="8d5e0-358">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-358">Allowed From</span></span>

<span data-ttu-id="8d5e0-359">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-360">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="8d5e0-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="8d5e0-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="8d5e0-362">DHCP クライアントのネットワーク パラメーターをクリアする</span><span class="sxs-lookup"><span data-stu-id="8d5e0-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="8d5e0-363">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-364">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-364">Description</span></span>

<span data-ttu-id="8d5e0-365">このサービスでは、ホスト アプリケーションのネットワーク パラメーター (IP アドレス、ネットワーク アドレス、ネットワーク マスク) がクリアされ、DHCP が有効になっているすべてのインターフェイスの DHCP クライアントの状態がクリアされます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-366">これは *nx_dhcp_stop* および *nx_dhcp_start* と組み合わせて使用され、DHCP ステート マシンが "再起動" されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="8d5e0-367">nx_dhcp_stop(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="8d5e0-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="8d5e0-368">nx_dhcp_reinitialize(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="8d5e0-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="8d5e0-369">nx_dhcp_start(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="8d5e0-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="8d5e0-370">複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスの DHCP クライアントを再初期化するには、*nx_dhcp_interface_reinitialize* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-371">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-371">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-372">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-373">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-373">Return Values</span></span>

- <span data-ttu-id="8d5e0-374">**NX_SUCCESS** (0x00) DHCP が正常に再初期化されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="8d5e0-375">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-376">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-376">Allowed From</span></span>

<span data-ttu-id="8d5e0-377">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-378">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="8d5e0-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="8d5e0-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="8d5e0-380">指定したインターフェイスの DHCP クライアントのネットワーク パラメーターをクリアする</span><span class="sxs-lookup"><span data-stu-id="8d5e0-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="8d5e0-381">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-382">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-382">Description</span></span>

<span data-ttu-id="8d5e0-383">このサービスでは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスのネットワーク パラメーター (IP アドレス、ネットワーク アドレス、ネットワーク マスク) がクリアされます (*nx_dhcp_interface_enable* を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="8d5e0-384">詳細については、*nx_dhcp_reinitialize* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-385">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-385">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-386">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="8d5e0-387">**interface_index** 再初期化するインターフェイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-388">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-388">Return Values</span></span>

- <span data-ttu-id="8d5e0-389">**NX_SUCCESS**: (0x00) インターフェイスが正常に再初期化されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="8d5e0-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-391">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-392">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="8d5e0-393">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-394">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-394">Allowed From</span></span>

<span data-ttu-id="8d5e0-395">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-396">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="8d5e0-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="8d5e0-397">nx_dhcp_release</span></span>

<span data-ttu-id="8d5e0-398">リースした IP アドレスを解放する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-399">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-400">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-400">Description</span></span>

<span data-ttu-id="8d5e0-401">このサービスは、DHCP サーバーに RELEASE メッセージを送信することによって、そのサーバーから取得した IP アドレスを解放します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="8d5e0-402">その後、DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="8d5e0-403">このサービスは、DHCP が有効になっているすべてのインターフェイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="8d5e0-404">アプリケーションでは、*nx_dhcp_start* を呼び出すことによって DHCP クライアントを再起動できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="8d5e0-405">特定のインターフェイスのアドレスを DHCP サーバーに解放するには、*nx_dhcp_interface_release* サービスを使用します</span><span class="sxs-lookup"><span data-stu-id="8d5e0-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-406">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-406">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-407">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-408">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-408">Return Values</span></span>

- <span data-ttu-id="8d5e0-409">**NX_SUCCESS** (0x00) DHCP が正常に解放されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="8d5e0-410">**NX_DHCP_NOT_BOUND** (0x94) IP アドレスがリースされていないため、解放できません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="8d5e0-411">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-412">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-413">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-413">Allowed From</span></span>

<span data-ttu-id="8d5e0-414">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-415">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="8d5e0-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="8d5e0-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="8d5e0-417">指定されたインターフェイスの IP アドレスを解放する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-418">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-419">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-419">Description</span></span>

<span data-ttu-id="8d5e0-420">このサービスでは、指定されたインターフェイスで DHCP サーバーから取得した IP アドレスが解放され、DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="8d5e0-421">DHCP クライアントを再起動するには、*nx_dhcp_start* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-422">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-422">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-423">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-424">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-424">Return Values</span></span>

- <span data-ttu-id="8d5e0-425">**NX_SUCCESS** (0x00) DHCP が正常に解放されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="8d5e0-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-427">**NX_DHCP_NOT_BOUND** (0x94) IP アドレスがリースされていないため、解放できません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="8d5e0-428">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-429">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="8d5e0-430">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-431">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-431">Allowed From</span></span>

<span data-ttu-id="8d5e0-432">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-433">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="8d5e0-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="8d5e0-434">nx_dhcp_decline</span></span>

<span data-ttu-id="8d5e0-435">DHCP サーバーからの IP アドレスを拒否する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-436">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-437">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-437">Description</span></span>

<span data-ttu-id="8d5e0-438">このサービスでは、DHCP が有効になっているすべてのインターフェイスで、DHCP サーバーからリースされた IP アドレスが拒否されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-439">NX_DHCP_CLIENT_ SEND_ ARP_PROBE が定義されていて、その IP アドレスが既に使用されていることが DHCP クライアントで検出された場合、DECLINE メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="8d5e0-440">NetX DHCP クライアントでの ARP プローブの構成の詳細については、第 1 章の **ARP プローブ** に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="8d5e0-441">アプリケーションでは、このサービスを使用して、IP アドレスが他で使用されていることが検出された場合に、その IP アドレスを拒否することができます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="8d5e0-442">このサービスでは、*nx_dhcp_start* を呼び出すことによって再起動できるように、DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-443">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-443">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-444">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-445">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-445">Return Values</span></span>

- <span data-ttu-id="8d5e0-446">**NX_SUCCESS** (0x00) 拒否が正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="8d5e0-447">**NX_DHCP_NOT_STARTED** (0x96) DHCP インスタンスが開始されていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="8d5e0-448">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-449">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-450">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-450">Allowed From</span></span>

<span data-ttu-id="8d5e0-451">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-452">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="8d5e0-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="8d5e0-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="8d5e0-454">指定されたインターフェイスで DHCP サーバーからの IP アドレスを拒否する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-455">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-456">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-456">Description</span></span>

<span data-ttu-id="8d5e0-457">このサービスでは、DHCP サーバーによって割り当てられた IP アドレスを拒否するために、DECLINE メッセージがサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="8d5e0-458">また、DHCP クライアントが再初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="8d5e0-459">詳細については、*nx_dhcp_decline* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-460">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-460">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-461">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-462">**Interface_index** IP アドレスを拒否するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-463">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-463">Return Values</span></span>

- <span data-ttu-id="8d5e0-464">**NX_SUCCESS** (0x00) DHCP 拒否メッセージが送信されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="8d5e0-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP クライアントがバインドされていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="8d5e0-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-467">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-468">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="8d5e0-469">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-470">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-470">Allowed From</span></span>

<span data-ttu-id="8d5e0-471">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-472">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="8d5e0-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="8d5e0-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="8d5e0-474">DHCP メッセージをサーバーに送信する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-475">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="8d5e0-476">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-476">Description</span></span>

<span data-ttu-id="8d5e0-477">このサービスでは、DHCP クライアント レコードで見つかった DHCP が有効になっている最初のインターフェイスで、指定された DHCP メッセージが DHCP サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="8d5e0-478">RELEASE または DECLINE メッセージを送信するには、アプリケーションで *nx_dhcp[_interface]_release()* または *nx_dhcp_interface_decline()* サービスをそれぞれ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="8d5e0-479">INFORM_REQUEST メッセージの種類を送信する場合を除き、このサービスを使用するには DHCP クライアントを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="8d5e0-480">このサービスは、ホスト アプリケーションで DHCP クライアントのステート マシンを "操作" するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-481">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-481">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-482">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="8d5e0-483">**dhcp_message_type** メッセージ要求 (*nx_dhcp.h* で定義されます)</span><span class="sxs-lookup"><span data-stu-id="8d5e0-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-484">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-484">Return Values</span></span>

- <span data-ttu-id="8d5e0-485">**NX_SUCCESS** (0x00) DHCP メッセージが送信されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="8d5e0-486">**NX_DHCP_NOT_STARTED** (0x96) インターフェイスのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="8d5e0-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) 送信するメッセージの種類が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="8d5e0-488">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-489">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-489">Allowed From</span></span>

<span data-ttu-id="8d5e0-490">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-491">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="8d5e0-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="8d5e0-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="8d5e0-493">特定のインターフェイスでサーバーに DHCP メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-494">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="8d5e0-495">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-495">Description</span></span>

<span data-ttu-id="8d5e0-496">このサービスでは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP サーバーにメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-497">RELEASE または DECLINE メッセージを送信するには、アプリケーションで *nx_dhcp[_interface]_release()* または *nx_dhcp_interface_decline()* サービスをそれぞれ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="8d5e0-498">DHCP INFORM REQUEST メッセージの種類を送信する場合を除き、このサービスを使用するには DHCP クライアントを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="8d5e0-499">このサービスは、ホスト アプリケーションで DHCP クライアントのステート マシンを "操作" するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-500">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-500">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-501">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="8d5e0-502">**Interface_index** メッセージを送信するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="8d5e0-503">**dhcp_message_type** メッセージ要求 (*nx_dhcp.h* で定義されます)</span><span class="sxs-lookup"><span data-stu-id="8d5e0-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-504">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-504">Return Values</span></span>

- <span data-ttu-id="8d5e0-505">**NX_SUCCESS** (0x00) DHCP メッセージが送信されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="8d5e0-506">**NX_DHCP_NOT_STARTED** (0x96) インターフェイスのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="8d5e0-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) 送信するメッセージの種類が無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="8d5e0-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-509">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-510">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="8d5e0-511">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-512">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-512">Allowed From</span></span>

<span data-ttu-id="8d5e0-513">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-514">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="8d5e0-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="8d5e0-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="8d5e0-516">DHCP クライアントの DHCP サーバーの IP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-517">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="8d5e0-518">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-518">Description</span></span>

<span data-ttu-id="8d5e0-519">このサービスでは、DHCP クライアント レコードで見つかった DHCP が有効になっている最初のインターフェイスで、DHCP クライアントの DHCP サーバーの IP アドレスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="8d5e0-520">DHCP クライアントが DHCP サーバーによって割り当てられた IP アドレスにバインドされた後にのみ、呼び出し元はこのサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="8d5e0-521">ホスト アプリケーションでは、*nx_ip_status_check* サービスを使用して IP アドレスが設定されていることを確認できます。または、*nx_dhcp_state_change_notify* を使用して、DHCP クライアントの状態が NX_DHCP_STATE_BOUND であることを照会できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="8d5e0-522">状態変更コールバック関数の設定の詳細については、*nx_dhcp_state_change_notify* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="8d5e0-523">複数のインターフェイスが DHCP クライアントに対して有効になっている場合に、特定のインターフェイスで DHCP サーバーを検索するには、*nx_dhcp_interface_server_address_get* サービスを使用します</span><span class="sxs-lookup"><span data-stu-id="8d5e0-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-524">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-524">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-525">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="8d5e0-526">**server_address** サーバーの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-527">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-527">Return Values</span></span>

- <span data-ttu-id="8d5e0-528">**NX_SUCCESS** (0x00) DHCP サーバー アドレスが返されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="8d5e0-529">NX_PTR_ERROR (0x16) 入力されたポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="8d5e0-530">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-531">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-531">Allowed From</span></span>

<span data-ttu-id="8d5e0-532">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-533">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="8d5e0-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="8d5e0-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="8d5e0-535">指定されたインターフェイスで DHCP クライアントの DHCP サーバーの IP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-536">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="8d5e0-537">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-537">Description</span></span>

<span data-ttu-id="8d5e0-538">このサービスでは、指定されたインターフェイスで DHCP が有効になっている場合に、DHCP クライアントの DHCP サーバーの IP アドレスがそのインターフェイスで取得されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-539">DHCP クライアントは、バインドされた状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="8d5e0-540">このインターフェイスで DHCP クライアントを起動した後に、ホスト アプリケーションでは、*nx_ip_status_check* サービスを使用して、IP アドレスが設定されていることを確認できます。また、DHCP クライアントの状態変更コールバックを使用して、DHCP クライアントの状態が NX_DHCP_STATE_BOUND であることを照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="8d5e0-541">状態変更コールバック関数の設定の詳細については、*nx_dhcp_state_change_notify* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-542">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-542">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-543">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="8d5e0-544">**Interface_index** IP アドレスを取得するインターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="8d5e0-545">**server_address** サーバーの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-546">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-546">Return Values</span></span>

- <span data-ttu-id="8d5e0-547">**NX_SUCCESS** (0x00) DHCP サーバー アドレスが返されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="8d5e0-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP クライアントがバインドされていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="8d5e0-550">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="8d5e0-551">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="8d5e0-552">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-553">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-553">Allowed From</span></span>

<span data-ttu-id="8d5e0-554">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-555">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="8d5e0-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="8d5e0-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="8d5e0-557">DHCP インスタンスのネットワーク インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-558">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-559">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-559">Description</span></span>

<span data-ttu-id="8d5e0-560">このサービスでは、単一のネットワーク インターフェイス用に構成された DHCP クライアントを実行する場合に、DHCP サーバーに接続するための DHCP インスタンスのネットワーク インターフェイスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="8d5e0-561">既定では、DHCP クライアントはプライマリ インターフェイスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="8d5e0-562">セカンダリ サービスで DHCP を実行するには、このサービスを使用して、セカンダリ インターフェイスを DHCP クライアント インターフェイスとして設定します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="8d5e0-563">アプリケーションでは、*nx_ip_interface_attach* サービスを使用して、指定されたインターフェイスを IP インスタンスに事前に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="8d5e0-564">このサービスは、1 つのインターフェイスでのみ DHCP クライアントを実行するアプリケーションを対象としています。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="8d5e0-565">複数のインターフェイスで DHCP を実行する方法の詳細については、*nx_dhcp_interface_enable* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-566">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-566">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-567">**dhcp_ptr** DHCP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="8d5e0-568">**index** デバイスのネットワーク インターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-569">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-569">Return Values</span></span>

- <span data-ttu-id="8d5e0-570">**NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="8d5e0-571">**NX_INVALID_INTERFACE** (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="8d5e0-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP が有効になっているインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) 別のインターフェイスのレコードがありません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="8d5e0-574">NX_PTR_ERROR (0x16) DHCP ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-575">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-575">Allowed From</span></span>

<span data-ttu-id="8d5e0-576">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-577">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="8d5e0-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="8d5e0-578">nx_dhcp_start</span></span>

<span data-ttu-id="8d5e0-579">DHCP の処理の開始する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-580">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-581">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-581">Description</span></span>

<span data-ttu-id="8d5e0-582">このサービスでは、DHCP が有効になっているすべてのインターフェイスで DHCP の処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-583">既定では、アプリケーションで *nx_dhcp_create* を呼び出されると、プライマリ インターフェイスが DHCP に対して有効になります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="8d5e0-584">IP インスタンスが DHCP クライアント インターフェイスの IP アドレスにバインドされていることを確認するには、*nx_ip_status_check* を使用して、IP アドレスが有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="8d5e0-585">DHCP が既に実行されている他のインターフェイスがある場合、それらはこのサービスの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="8d5e0-586">複数のインターフェイスが有効になっている場合に、特定のインターフェイスで DHCP を開始するには、*nx_dhcp_interface_start* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-587">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-587">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-588">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-589">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-589">Return Values</span></span>

- <span data-ttu-id="8d5e0-590">**NX_SUCCESS** (0x00) DHCP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="8d5e0-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="8d5e0-592">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-593">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-594">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-594">Allowed From</span></span>

<span data-ttu-id="8d5e0-595">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-596">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="8d5e0-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="8d5e0-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="8d5e0-598">指定されたインターフェイスで DHCP 処理を開始する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-599">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-600">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-600">Description</span></span>

<span data-ttu-id="8d5e0-601">このサービスでは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP の処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-602">インターフェイスで DHCP を有効にする方法の詳細については、*nx_dhcp_interface_enable*() を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="8d5e0-603">既定では、アプリケーションで *nx_dhcp_create* を呼び出されると、プライマリ インターフェイスが DHCP に対して有効になります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="8d5e0-604">DHCP クライアントが実行されている他のインターフェイスがない場合、このサービスでは DHCP クライアントのスレッドが開始または再開され、DHCP クライアントのタイマーが (再) アクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="8d5e0-605">アプリケーションで、IP アドレスが取得されたかどうかを確認するには、*nx_ip_status_check* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-606">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-606">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-607">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-608">**Interface_index** DHCP クライアントを開始するインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-609">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-609">Return Values</span></span>

- <span data-ttu-id="8d5e0-610">**NX_SUCCESS** (0x00) DHCP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="8d5e0-611">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP インスタンスは既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="8d5e0-612">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-613">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="8d5e0-614">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-615">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-615">Allowed From</span></span>

<span data-ttu-id="8d5e0-616">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-617">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="8d5e0-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="8d5e0-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="8d5e0-619">DHCP 状態変更コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-620">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="8d5e0-621">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-621">Description</span></span>

<span data-ttu-id="8d5e0-622">このサービスでは、DHCP の状態変更をアプリケーションに通知するために、指定されたコールバック関数 dhcp_state_change_notify が登録されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="8d5e0-623">このコールバック関数では、DHCP クライアントが遷移した状態が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="8d5e0-624">さまざまな DHCP の状態に関連付けられている値を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="8d5e0-625">State</span><span class="sxs-lookup"><span data-stu-id="8d5e0-625">State</span></span>                             | <span data-ttu-id="8d5e0-626">値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="8d5e0-627">NX\_DHCP\_STATE\_BOOT</span><span class="sxs-lookup"><span data-stu-id="8d5e0-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="8d5e0-628">1</span><span class="sxs-lookup"><span data-stu-id="8d5e0-628">1</span></span>     |
| <span data-ttu-id="8d5e0-629">NX\_DHCP\_STATE\_INIT</span><span class="sxs-lookup"><span data-stu-id="8d5e0-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="8d5e0-630">2</span><span class="sxs-lookup"><span data-stu-id="8d5e0-630">2</span></span>     |
| <span data-ttu-id="8d5e0-631">NX\_DHCP\_STATE\_SELECTING</span><span class="sxs-lookup"><span data-stu-id="8d5e0-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="8d5e0-632">3</span><span class="sxs-lookup"><span data-stu-id="8d5e0-632">3</span></span>     |
| <span data-ttu-id="8d5e0-633">NX\_DHCP\_STATE\_REQUESTING</span><span class="sxs-lookup"><span data-stu-id="8d5e0-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="8d5e0-634">4</span><span class="sxs-lookup"><span data-stu-id="8d5e0-634">4</span></span>     |
| <span data-ttu-id="8d5e0-635">NX\_DHCP\_STATE\_BOUND</span><span class="sxs-lookup"><span data-stu-id="8d5e0-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="8d5e0-636">5</span><span class="sxs-lookup"><span data-stu-id="8d5e0-636">5</span></span>     |
| <span data-ttu-id="8d5e0-637">NX\_DHCP\_STATE\_RENEWING</span><span class="sxs-lookup"><span data-stu-id="8d5e0-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="8d5e0-638">6</span><span class="sxs-lookup"><span data-stu-id="8d5e0-638">6</span></span>     |
| <span data-ttu-id="8d5e0-639">NX\_DHCP\_STATE\_REBINDING</span><span class="sxs-lookup"><span data-stu-id="8d5e0-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="8d5e0-640">7</span><span class="sxs-lookup"><span data-stu-id="8d5e0-640">7</span></span>     |
| <span data-ttu-id="8d5e0-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="8d5e0-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="8d5e0-642">8</span><span class="sxs-lookup"><span data-stu-id="8d5e0-642">8</span></span>     |
| <span data-ttu-id="8d5e0-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span><span class="sxs-lookup"><span data-stu-id="8d5e0-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="8d5e0-644">9</span><span class="sxs-lookup"><span data-stu-id="8d5e0-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="8d5e0-645">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-645">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-646">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-647">**dhcp_state_change_notify** 状態変更コールバック関数のポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-648">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-648">Return Values</span></span>

- <span data-ttu-id="8d5e0-649">**NX_SUCCESS** (0x00) コールバックが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="8d5e0-650">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-651">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-652">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-652">Allowed From</span></span>

<span data-ttu-id="8d5e0-653">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="8d5e0-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-654">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="8d5e0-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="8d5e0-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="8d5e0-656">指定されたインターフェイスに DHCP 状態変更コールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-657">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="8d5e0-658">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-658">Description</span></span>

<span data-ttu-id="8d5e0-659">このサービスでは、DHCP の状態変更をアプリケーションに通知するために、指定されたコールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="8d5e0-660">このコールバック関数の入力引数は、インターフェイスのインデックスと、そのインターフェイスで DHCP クライアントが遷移した状態です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="8d5e0-661">状態変更関数の詳細については、*nx_dhcp_state_change_notify*() を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-662">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-662">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-663">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-664">**dhcp_interface_state_change_notify** アプリケーションのコールバック関数のポインター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-665">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-665">Return Values</span></span>

- <span data-ttu-id="8d5e0-666">**NX_SUCCESS** (0x00) コールバックが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="8d5e0-667">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-668">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-668">Allowed From</span></span>

<span data-ttu-id="8d5e0-669">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="8d5e0-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-670">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="8d5e0-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="8d5e0-671">nx_dhcp_stop</span></span>

<span data-ttu-id="8d5e0-672">DHCP の処理の停止する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-673">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-674">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-674">Description</span></span>

<span data-ttu-id="8d5e0-675">このサービスでは、DHCP の処理が開始されたすべてのインターフェイスで DHCP の処理が停止されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="8d5e0-676">DHCP が処理されているインターフェイスがない場合、このサービスによって、DHCP クライアントのスレッドが中断され、DHCP クライアントのタイマーが非アクティブにされます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="8d5e0-677">複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスで DHCP を停止するには、*nx_dhcp_interface_stop* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-678">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-678">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-679">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-680">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-680">Return Values</span></span>

- <span data-ttu-id="8d5e0-681">**NX_SUCCESS** (0x00) DHCP が正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="8d5e0-682">**NX_DHCP_NOT_STARTED** (0x96) DHCP インスタンスが開始されていません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="8d5e0-683">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-684">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-685">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-685">Allowed From</span></span>

<span data-ttu-id="8d5e0-686">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-687">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="8d5e0-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="8d5e0-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="8d5e0-689">指定されたインターフェイスで DHCP 処理を停止する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-690">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="8d5e0-691">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-691">Description</span></span>

<span data-ttu-id="8d5e0-692">このサービスでは、DHCP が既に開始されている場合に、指定されたインターフェイスで DHCP の処理が停止されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="8d5e0-693">DHCP が実行されている他のインターフェイスがない場合は、DHCP のスレッドとタイマーが中断されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-694">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-694">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-695">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-696">**Interface_index** DHCP の処理を停止するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-697">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-697">Return Values</span></span>

- <span data-ttu-id="8d5e0-698">**NX_SUCCESS** (0x00) DHCP が正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="8d5e0-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="8d5e0-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP が開始されていません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="8d5e0-700">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-701">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="8d5e0-702">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-703">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-703">Allowed From</span></span>

<span data-ttu-id="8d5e0-704">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-705">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="8d5e0-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="8d5e0-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="8d5e0-707">最後のサーバーの応答から DHCP のオプションを取得する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-708">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="8d5e0-709">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-709">Description</span></span>

<span data-ttu-id="8d5e0-710">このサービスでは、DHCP クライアント レコードで検出された DHCP が有効になっている最初のインターフェイスで、DHCP オプションのバッファーから指定された DHCP オプションが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="8d5e0-711">正常に実行された場合、オプションのデータは指定されたバッファーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-712">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-712">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-713">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="8d5e0-714">**request_option** RFC で指定されている DHCP のオプション。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="8d5e0-715">*nx_dhcp.h* の NX_DHCP_OPTION オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="8d5e0-716">**destination_ptr** 応答文字列のコピー先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="8d5e0-717">**destination_size** コピー先のサイズへのポインター。戻り値では、返されたバイト数が保持されているコピー先。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-718">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-718">Return Values</span></span>

- <span data-ttu-id="8d5e0-719">**NX_SUCCESS** (0x00) オプションの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="8d5e0-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP クライアントがバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="8d5e0-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="8d5e0-722">**NX_DHCP_DEST_TO_SMALL** (0x95) コピー先が小さすぎて応答を保持できません。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="8d5e0-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP オプションがサーバー応答で見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="8d5e0-724">NX_PTR_ERROR (0x16) 入力されたポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="8d5e0-725">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-726">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-726">Allowed From</span></span>

<span data-ttu-id="8d5e0-727">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-728">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="8d5e0-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="8d5e0-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="8d5e0-730">指定されたインターフェイスで、最後のサーバーの応答から DHCP オプションを取得する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-731">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="8d5e0-732">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-732">Description</span></span>

<span data-ttu-id="8d5e0-733">このサービスでは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスの DHCP オプションのバッファーから指定された DHCP オプションが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="8d5e0-734">正常に実行された場合、オプションのデータは指定されたバッファーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-735">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-735">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-736">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-737">**Interface_index** 指定されたオプションを取得するインデックス</span><span class="sxs-lookup"><span data-stu-id="8d5e0-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="8d5e0-738">**request_option** RFC で指定されている DHCP のオプション。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="8d5e0-739">*nx_dhcp.h* の NX_DHCP_OPTION オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="8d5e0-740">**destination_ptr** 応答文字列のコピー先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="8d5e0-741">**destination_size** コピー先のサイズへのポインター。戻り値では、返されたバイト数が保持されているコピー先。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-742">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-742">Return Values</span></span>

- <span data-ttu-id="8d5e0-743">**NX_SUCCESS** (0x00) オプションの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="8d5e0-744">**NX_DHCP_NOT_BOUND** (0x94) IP アドレスが割り当てられていません</span><span class="sxs-lookup"><span data-stu-id="8d5e0-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="8d5e0-745">**NX_DHCP_DEST_TO_SMALL** (0x95) バッファーが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="8d5e0-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="8d5e0-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP オプションがサーバー応答で見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="8d5e0-747">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="8d5e0-748">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="8d5e0-749">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8d5e0-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-750">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-750">Allowed From</span></span>

<span data-ttu-id="8d5e0-751">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-752">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="8d5e0-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="8d5e0-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="8d5e0-754">4 バイトを ULONG に変換する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-755">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="8d5e0-756">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-756">Description</span></span>

<span data-ttu-id="8d5e0-757">このサービスでは、"option_string_ptr" が指している 4 文字が符号なしの long 値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="8d5e0-758">これは、IP アドレスが存在する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-759">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-759">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-760">**option_string_ptr** 以前に取得されたオプションの文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-761">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-761">Return Values</span></span>

- <span data-ttu-id="8d5e0-762">**Value** 最初の 4 バイトの値。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-763">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-763">Allowed From</span></span>

<span data-ttu-id="8d5e0-764">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-765">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="8d5e0-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="8d5e0-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="8d5e0-767">ユーザーが指定したオプションを追加するためにコールバック関数を設定する</span><span class="sxs-lookup"><span data-stu-id="8d5e0-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="8d5e0-768">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8d5e0-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="8d5e0-769">説明</span><span class="sxs-lookup"><span data-stu-id="8d5e0-769">Description</span></span>

<span data-ttu-id="8d5e0-770">このサービスでは、ユーザーが指定したオプションを追加するために、指定されたコールバック関数が登録されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="8d5e0-771">このコールバック関数を指定した場合、アプリケーションでは iface_index と message_type を使用して、ユーザーが指定したオプションをパケットに追加できます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="8d5e0-772">ユーザーのルーチンで。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-772">In user’s routine.</span></span> <span data-ttu-id="8d5e0-773">アプリケーションでは、ユーザーが指定したオプションを追加するときに、DHCP オプションの形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="8d5e0-774">ユーザー オプションの合計サイズが user_option_length 以下になるようにして、user_option_length を実際のオプションの長さで更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="8d5e0-775">オプションが正常に追加された場合は NX_TRUE が返され、それ以外の場合は NX_FALSE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d5e0-776">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d5e0-776">Input Parameters</span></span>

- <span data-ttu-id="8d5e0-777">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="8d5e0-778">**dhcp_user_option_add** ユーザー オプション追加関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d5e0-779">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d5e0-779">Return Values</span></span>

- <span data-ttu-id="8d5e0-780">**NX_SUCCESS** (0x00) コールバックが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="8d5e0-781">NX_PTR_ERROR (0x16) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8d5e0-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d5e0-782">許可元</span><span class="sxs-lookup"><span data-stu-id="8d5e0-782">Allowed From</span></span>

<span data-ttu-id="8d5e0-783">Threads</span><span class="sxs-lookup"><span data-stu-id="8d5e0-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d5e0-784">例</span><span class="sxs-lookup"><span data-stu-id="8d5e0-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
