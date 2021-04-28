---
title: 第 4 章 - Azure RTOS NetX Duo DHCPv6 クライアント サービス
description: この章では、すべての Azure RTOS NetX Duo DHCPv6 クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810889"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="29a0e-103">第 4 章 - Azure RTOS NetX Duo DHCPv6 クライアント サービス</span><span class="sxs-lookup"><span data-stu-id="29a0e-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="29a0e-104">この章では、すべての Azure RTOS NetX Duo DHCPv6 クライアント サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="29a0e-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="29a0e-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="29a0e-106">**nx_dhcpv6_client_create:** "*DHCPv6 クライアント インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="29a0e-107">**nx_dhcpv6_client_delete:** "*DHCPv6 クライアント インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="29a0e-108">**nx_dhcpv6_create_client_duid:** "*DHCPv6 クライアント DUID を作成する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="29a0e-109">**nx_dhcpv6_add_client_ia:** "*DHCPv6 クライアントの ID アドレス (IA) を追加する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="29a0e-110">**nx_dhcpv6_create_client_ia:** ("*従来の DHCPv6 クライアントの ID アドレス (IA) を追加する*")</span><span class="sxs-lookup"><span data-stu-id="29a0e-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="29a0e-111">**nx_dhcpv6_create_client_iana:** "*DHCPv6 クライアントの非一時アドレス用 ID 関連付け (IANA) を作成する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="29a0e-112">**nx_dhcpv6_get_client_duid_time_id:** "*DHCPv6 クライアント DUID から時刻 ID を取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="29a0e-113">**nx_dhcpv6_client_set_interface:** "*DHCPv6 サーバーと通信するためのクライアント ネットワーク インターフェイスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="29a0e-114">**nx_dhcpv6_get_IP_address:** "*DHCPv6 クライアントに割り当てられたグローバル IPv6 アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="29a0e-115">**nx_dhcpv6_get_lease_time_data:** "*クライアントのグローバル IPv6 アドレスの T1、T2、有効な有効期間、優先有効期間を取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="29a0e-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** "*DHCPv6 クライアントの IPv6 アドレスの T1、T2、有効な有効期間、優先有効期間をアドレス インデックスで取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="29a0e-117">**nx_dhcpv6_get_iana_lease_time:** "*DHCPv6 クライアントにリースされている ID 関連付け (IANA) の T1 と T2 を取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="29a0e-118">**nx_dhcpv6_get_other_option_data:** "*指定されたオプション データ (ドメイン名やタイム ゾーン サーバーなど) を取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="29a0e-119">**nx_dhcpv6_get_DNS_server_address:** "*DHCPv6 クライアントの DNS サーバー リストの指定されたインデックスにある DNS サーバー アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="29a0e-120">**nx_dhcpv6_get_time_accrued:** "*グローバル IPv6 アドレス リースが DHCPv6 クライアントにバインドされている期間を取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="29a0e-121">**nx_dhcpv6_get_time_server_address:** "*DHCPv6 クライアントのタイム サーバー リストの指定されたインデックスにあるタイム サーバー アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="29a0e-122">**nx_dhcpv6_get_valid_ip_address_count:** "*DHCPv6 クライアントに割り当てられた IPv6 アドレスの数を取得する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="29a0e-123">**nx_dhcpv6_reinitialize:** "*DHCPv6 クライアント ステート マシンを再起動し、DHCPv6 プロトコルを再実行するために、DHCPv6 を再初期化する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="29a0e-124">**nx_dhcpv6_request_confirm:** "*CONFIRM 要求をサーバーに送信する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="29a0e-125">**nx_dhcpv6_request_inform_request:** "*INFORM REQUEST メッセージをサーバーに送信する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="29a0e-126">**nx_dhcpv6_request_release:** "*RELEASE 要求をサーバーに送信する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="29a0e-127">**nx_dhcpv6_request_option_DNS_server:** "*サーバーへの要求メッセージのクライアント オプション要求データに DNS サーバー オプションを追加する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="29a0e-128">**nx_dhcpv6_request_option_FQDN:** "*サーバーへの要求メッセージのクライアント オプション要求データに FQDN オプションを追加する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="29a0e-129">**nx_dhcpv6_request_option_domain_name:** "*サーバーへの要求メッセージのクライアント オプション要求データにドメイン名オプションを追加する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="29a0e-130">**nx_dhcpv6_request_option_time_server:** "*サーバーへの要求メッセージのクライアント オプション要求データにタイム サーバー オプションを追加する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="29a0e-131">**nx_dhcpv6_request_option_timezone:** "*サーバーへの要求メッセージのクライアント オプション要求データにタイム ゾーン オプションを追加する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="29a0e-132">**nx_dhcpv6_request_solicit:** "*クライアント ネットワーク上の任意のサーバーに DHCPv6 SOLICIT 要求を送信する (ブロードキャスト)* "</span><span class="sxs-lookup"><span data-stu-id="29a0e-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="29a0e-133">**nx_dhcpv6_request_solicit_rapid:** *Rapid Commit オプションを設定して、クライアント ネットワーク上の任意のサーバーに DHCPv6 SOLICIT 要求を送信する (ブロードキャスト)*</span><span class="sxs-lookup"><span data-stu-id="29a0e-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="29a0e-134">**nx_dhcpv6_resume:** "*DHCPv6 クライアントの処理を再開する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="29a0e-135">**nx_dhcpv6_start:** "*DHCPv6 クライアント スレッド タスクを開始する (これは DHCPv6 ステート マシンの起動と同じではなく、SOLICIT 要求は送信されないことに注意してください)* "</span><span class="sxs-lookup"><span data-stu-id="29a0e-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="29a0e-136">**nx_dhcpv6_stop:** "*DHCPv6 クライアント スレッド タスクを停止する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="29a0e-137">**nx_dhcpv6_suspend:** "*DHCPv6 クライアント スレッド タスクを中断する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="29a0e-138">**nx_dhcpv6_set_time_accrued:** "*クライアント レコードにクライアントのグローバル IPv6 アドレス リースの経過時間を設定する*"</span><span class="sxs-lookup"><span data-stu-id="29a0e-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="29a0e-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="29a0e-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="29a0e-140">DHCPv6 クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="29a0e-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-141">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="29a0e-142">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-142">Description</span></span>

<span data-ttu-id="29a0e-143">このサービスでは、コールバック関数を含む DHCPv6 クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-144">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-144">Input Parameters</span></span>

- <span data-ttu-id="29a0e-145">**dhcpv6_ptr**: DHCPv6 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="29a0e-146">**ip_ptr**: クライアント IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="29a0e-147">**name_ptr**: DHCPv6 インスタンスの名前へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="29a0e-148">**packet_pool_ptr**: クライアントのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="29a0e-149">**stack_ptr**: クライアントのスタック メモリへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="29a0e-150">**stack_ptr**: クライアントのスタック メモリのサイズ</span><span class="sxs-lookup"><span data-stu-id="29a0e-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="29a0e-151">**dhcpv6_state_change_notify**: クライアントがサーバーに対して新しい DHCPv6 要求を開始したときに呼び出されるコールバック関数へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="29a0e-152">**dhcpv6_server_error_handler**: クライアントがサーバーからエラー状態を受信したときに呼び出されるコールバック関数へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-153">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-153">Return Values</span></span>

- <span data-ttu-id="29a0e-154">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="29a0e-155">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-156">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-157">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-157">Allowed From</span></span>

<span data-ttu-id="29a0e-158">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-159">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-160">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-160">See Also</span></span>

- <span data-ttu-id="29a0e-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="29a0e-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="29a0e-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="29a0e-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="29a0e-163">DHCPv6 クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="29a0e-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-164">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-165">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-165">Description</span></span>

<span data-ttu-id="29a0e-166">このサービスでは、以前に作成された DHCPv6 クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-167">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-167">Input Parameters</span></span>

- <span data-ttu-id="29a0e-168">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-169">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-169">Return Values</span></span>

- <span data-ttu-id="29a0e-170">**NX_SUCCESS**: (0x00) DHCPv6 が正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="29a0e-171">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-172">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-173">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-173">Allowed From</span></span>

<span data-ttu-id="29a0e-174">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-175">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-176">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-176">See Also</span></span>

- <span data-ttu-id="29a0e-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="29a0e-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="29a0e-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="29a0e-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="29a0e-179">クライアントの DHCPv6 用ネットワーク インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="29a0e-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-180">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="29a0e-181">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-181">Description</span></span>

<span data-ttu-id="29a0e-182">このサービスでは、DHCPv6 サーバーと通信するためのクライアントのネットワーク インターフェイスを、指定された入力インターフェイス インデックスに設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-183">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-183">Input Parameters</span></span>

- <span data-ttu-id="29a0e-184">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-185">**interface_index**: ネットワーク インターフェイスを示すインデックス</span><span class="sxs-lookup"><span data-stu-id="29a0e-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-186">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-186">Return Values</span></span>

- <span data-ttu-id="29a0e-187">**NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="29a0e-188">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-189">NX_INVALID_INTERFACE: (0x4C) インターフェイス インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-190">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-190">Allowed From</span></span>

<span data-ttu-id="29a0e-191">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-192">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-193">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-193">See Also</span></span>

- <span data-ttu-id="29a0e-194">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="29a0e-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="29a0e-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="29a0e-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="29a0e-197">DHCPv6 メッセージの送信先となる宛先アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="29a0e-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-198">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="29a0e-199">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-199">Description</span></span>

<span data-ttu-id="29a0e-200">このサービスでは、DHCPv6 メッセージの送信先となる宛先アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="29a0e-201">既定値は ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2) です。</span><span class="sxs-lookup"><span data-stu-id="29a0e-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-202">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-202">Input Parameters</span></span>

- <span data-ttu-id="29a0e-203">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-204">**destination_address**: 宛先アドレス</span><span class="sxs-lookup"><span data-stu-id="29a0e-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-205">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-205">Return Values</span></span>

- <span data-ttu-id="29a0e-206">**NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="29a0e-207">NX_PTR_ERROR: (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-208">NX_DHCPV6_PARAM_ERROR: (0xE93) Parament エラー</span><span class="sxs-lookup"><span data-stu-id="29a0e-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-209">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-209">Allowed From</span></span>

<span data-ttu-id="29a0e-210">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-211">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-212">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-212">See Also</span></span>

- <span data-ttu-id="29a0e-213">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="29a0e-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="29a0e-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="29a0e-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="29a0e-216">クライアント DUID オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="29a0e-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-217">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="29a0e-218">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-218">Description</span></span>

<span data-ttu-id="29a0e-219">このサービスでは、入力パラメーターを使用してクライアント DUID を作成します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="29a0e-220">時刻入力が指定されておらず、DUID の種類が "リンク層と時刻" を示している場合、この関数によって、一意性を確保するためのランダム化係数を含む時刻が指定されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="29a0e-221">DUID の種類としてベンダー割り当て (エンタープライズ) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-222">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-222">Input Parameters</span></span>

- <span data-ttu-id="29a0e-223">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-224">**duid_type**: DUID の種類 (ハードウェア、エンタープライズなど)</span><span class="sxs-lookup"><span data-stu-id="29a0e-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="29a0e-225">**hardware_type**: ネットワーク ハードウェア (IEEE 802 など)</span><span class="sxs-lookup"><span data-stu-id="29a0e-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="29a0e-226">**time**: 一意識別子の作成に使用する値</span><span class="sxs-lookup"><span data-stu-id="29a0e-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-227">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-227">Return Values</span></span>

- <span data-ttu-id="29a0e-228">**NX_SUCCESS**: (0x00) クライアント DUID が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="29a0e-229">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-230">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="29a0e-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE: (0xE98) DUID の種類が不明であるか、サポートされていません</span><span class="sxs-lookup"><span data-stu-id="29a0e-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="29a0e-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE: (0xE99) DUID のハードウェアの種類が不明であるか、サポートされていません</span><span class="sxs-lookup"><span data-stu-id="29a0e-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-233">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-233">Allowed From</span></span>

<span data-ttu-id="29a0e-234">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-235">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-236">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-236">See Also</span></span>

- <span data-ttu-id="29a0e-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="29a0e-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="29a0e-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="29a0e-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="29a0e-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="29a0e-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="29a0e-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="29a0e-241">ID 関連付けをクライアントに追加する</span><span class="sxs-lookup"><span data-stu-id="29a0e-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-242">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="29a0e-243">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-243">Description</span></span>

<span data-ttu-id="29a0e-244">このサービスは、*nx_dhcpv6_add_client_ia* サービスと同じです。</span><span class="sxs-lookup"><span data-stu-id="29a0e-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="29a0e-245">指定されたパラメーターをクライアント レコードに入力することによって、クライアントの ID 関連付けを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="29a0e-246">優先有効期間と有効な有効期間の最大値を要求するには、これらのパラメーターを無限大に設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="29a0e-247">DHCPv6 クライアントに複数の IA を追加するには、NX_DHCPV6_MAX_IA_ADDRESS を既定値の 1 より大きい値に設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-248">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-248">Input Parameters</span></span>

- <span data-ttu-id="29a0e-249">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-250">**ipv6_address**: NetX Duo IP アドレス ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="29a0e-251">**preferred_lifetime**: IP アドレスが非推奨になるまでの時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="29a0e-252">**valid_lifetime**: IP アドレスの有効期限が切れるまでの時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-253">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-253">Return Values</span></span>

- <span data-ttu-id="29a0e-254">**NX_SUCCESS**: (0x00) クライアントの IA が正常に追加されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="29a0e-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**: (0xEAF) IA アドレスが重複しています</span><span class="sxs-lookup"><span data-stu-id="29a0e-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="29a0e-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS**: (0xEAE) IA が、クライアントが保存できる IA の最大数を超えています</span><span class="sxs-lookup"><span data-stu-id="29a0e-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="29a0e-257">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-258">NX_DHCPV6_INVALID_IA_ADDRESS: (0xEA4) IA の IA アドレスが無効です (null など)</span><span class="sxs-lookup"><span data-stu-id="29a0e-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="29a0e-259">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="29a0e-260">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-260">Allowed From</span></span>

<span data-ttu-id="29a0e-261">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-262">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-263">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-263">See Also</span></span>

- <span data-ttu-id="29a0e-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="29a0e-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="29a0e-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="29a0e-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="29a0e-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="29a0e-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="29a0e-268">クライアントの ID 関連付け (非一時) を作成する</span><span class="sxs-lookup"><span data-stu-id="29a0e-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-269">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="29a0e-270">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-270">Description</span></span>

<span data-ttu-id="29a0e-271">このサービスでは、指定されたパラメーターからクライアントの非一時 ID 関連付け (IANA) を作成します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="29a0e-272">DHCPv6 クライアント要求で T1 および T2 時間を最大 (無限大) に設定するには、これらのパラメーターを NX_DHCPV6_INFINITE_LEASE に設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="29a0e-273">クライアントには IANA は 1 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-274">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-274">Input Parameters</span></span>

- <span data-ttu-id="29a0e-275">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-276">**IA_ident**: ID 関連付け一意識別子</span><span class="sxs-lookup"><span data-stu-id="29a0e-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="29a0e-277">**T1**: クライアントが IPv6 アドレスの更新を開始する必要がある時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="29a0e-278">**T2**: クライアントが IPv6 アドレスの再バインドを開始する必要がある時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-279">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-279">Return Values</span></span>

- <span data-ttu-id="29a0e-280">**NX_SUCCESS**: (0x00) IANA が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="29a0e-281">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-282">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-283">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-283">Allowed From</span></span>

<span data-ttu-id="29a0e-284">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-285">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-286">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-286">See Also</span></span>

- <span data-ttu-id="29a0e-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="29a0e-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="29a0e-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="29a0e-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="29a0e-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="29a0e-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="29a0e-291">ID 関連付けをクライアントに追加する</span><span class="sxs-lookup"><span data-stu-id="29a0e-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-292">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="29a0e-293">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-293">Description</span></span>

<span data-ttu-id="29a0e-294">このサービスでは、指定されたパラメーターをクライアント レコードに入力することによって、クライアントの ID 関連付けを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="29a0e-295">優先有効期間と有効な有効期間の最大値を要求するには、これらのパラメーターを無限大に設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="29a0e-296">DHCPv6 クライアントに複数の IA を追加するには、NX_DHCPV6_MAX_IA_ADDRESS を既定値の 1 より大きい値に設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-297">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-297">Input Parameters</span></span>

- <span data-ttu-id="29a0e-298">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-299">**ipv6_address**: NetX Duo IP アドレス ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="29a0e-300">**preferred_lifetime**: IP アドレスが非推奨になるまでの時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="29a0e-301">**valid_lifetime**: IP アドレスの有効期限が切れるまでの時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="29a0e-302">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-302">Return Values</span></span>

- <span data-ttu-id="29a0e-303">**NX_SUCCESS**: (0x00) クライアントの IA が正常に追加されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="29a0e-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**: (0xEAF) IA アドレスが重複しています</span><span class="sxs-lookup"><span data-stu-id="29a0e-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="29a0e-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS**: (0xEAE) IA が、クライアントが保存できる IA の最大数を超えています</span><span class="sxs-lookup"><span data-stu-id="29a0e-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="29a0e-306">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-307">NX_DHCPV6_INVALID_IA_ADDRESS: (0xEA4) IA の IA アドレスが無効です (null など)</span><span class="sxs-lookup"><span data-stu-id="29a0e-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="29a0e-308">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="29a0e-309">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-309">Allowed From</span></span>

<span data-ttu-id="29a0e-310">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-311">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-312">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-312">See Also</span></span>

- <span data-ttu-id="29a0e-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="29a0e-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="29a0e-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="29a0e-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="29a0e-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="29a0e-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="29a0e-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="29a0e-317">クライアント DUID から時刻 ID を取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-318">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="29a0e-319">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-319">Description</span></span>

<span data-ttu-id="29a0e-320">このサービスでは、クライアント DUID から時刻 ID フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="29a0e-321">DHCPv6 クライアント インスタンスのクライアント DUID を入力するために、アプリケーションで最初に *nx_dhcpv6_create_client_duid* を呼び出す必要がある場合、このフィールドには null 値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="29a0e-322">これは、アプリケーションがこのデータを保存し、再起動のたびに時刻フィールドを含む同じクライアント DUID をサーバーに提示することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="29a0e-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-323">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-323">Input Parameters</span></span>

- <span data-ttu-id="29a0e-324">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-325">**time_id**: クライアント DUID の時刻フィールドへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-326">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-326">Return Values</span></span>

- <span data-ttu-id="29a0e-327">**NX_SUCCESS**: (0x00) IP リース データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="29a0e-328">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-329">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-330">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-330">Allowed From</span></span>

<span data-ttu-id="29a0e-331">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-332">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-333">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-333">See Also</span></span>

- <span data-ttu-id="29a0e-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="29a0e-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="29a0e-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="29a0e-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="29a0e-339">クライアントのグローバル IPv6 アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-340">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="29a0e-341">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-341">Description</span></span>

<span data-ttu-id="29a0e-342">このサービスでは、クライアントのグローバル IPv6 アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="29a0e-343">クライアントに有効なアドレスがない場合は、エラー状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="29a0e-344">クライアントに複数のグローバル IPv6 アドレスがある場合は、プライマリ IPv6 アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-345">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-345">Input Parameters</span></span>

- <span data-ttu-id="29a0e-346">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-347">**ip_address**: IPv6 アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-348">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-348">Return Values</span></span>

- <span data-ttu-id="29a0e-349">**NX_SUCCESS**: (0x00) IPv6 アドレスが正常に割り当てられました</span><span class="sxs-lookup"><span data-stu-id="29a0e-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="29a0e-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID**: (0xEAD) IPv6 アドレスが無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="29a0e-351">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-352">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-353">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-353">Allowed From</span></span>

<span data-ttu-id="29a0e-354">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-355">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="29a0e-356">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-356">See Also</span></span>

- <span data-ttu-id="29a0e-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="29a0e-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="29a0e-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="29a0e-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="29a0e-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="29a0e-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="29a0e-362">クライアントの IA アドレスのリース時間データを取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-363">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="29a0e-364">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-364">Description</span></span>

<span data-ttu-id="29a0e-365">このサービスでは、クライアントのグローバル IA アドレスの時間データを取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="29a0e-366">クライアントの IA アドレスの状態が無効の場合、時間データは 0 に設定され、正常完了状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="29a0e-367">クライアントに複数のグローバル IPv6 アドレスがある場合は、プライマリ IA アドレス データが返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-368">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-368">Input Parameters</span></span>

- <span data-ttu-id="29a0e-369">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-370">**T1**: IA アドレス更新時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="29a0e-371">**T2**: IA アドレス再バインド時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="29a0e-372">**preferred_lifetime**: IA アドレスが非推奨になる時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="29a0e-373">**valid_lifetime**: IA アドレスの有効期限が切れる時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-374">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-374">Return Values</span></span>

- <span data-ttu-id="29a0e-375">**NX_SUCCESS**: (0x00) IA リース データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="29a0e-376">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-377">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-378">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-378">Allowed From</span></span>

<span data-ttu-id="29a0e-379">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-380">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-381">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-381">See Also</span></span>

- <span data-ttu-id="29a0e-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="29a0e-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="29a0e-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="29a0e-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="29a0e-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="29a0e-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="29a0e-387">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="29a0e-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="29a0e-388">クライアントの IANA のリース時間データを取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-389">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="29a0e-390">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-390">Description</span></span>

<span data-ttu-id="29a0e-391">このサービスでは、クライアントのグローバル IA-NA のリース時間データ (T1 と T2) を取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="29a0e-392">クライアントの IA-NA アドレスの状態が無効の場合、時間データは 0 に設定され、正常完了状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="29a0e-393">クライアントに複数のグローバル IPv6 アドレスがある場合は、プライマリ IA アドレス データが返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-394">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-394">Input Parameters</span></span>

- <span data-ttu-id="29a0e-395">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-396">**T1**: リースの更新を開始する時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="29a0e-397">**T2**: リースの再バインドを開始する時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-398">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-398">Return Values</span></span>

- <span data-ttu-id="29a0e-399">**NX_SUCCESS**: (0x00) IANA リース データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="29a0e-400">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-401">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-402">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-402">Allowed From</span></span>

<span data-ttu-id="29a0e-403">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-404">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-405">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-405">See Also</span></span>

- <span data-ttu-id="29a0e-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="29a0e-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="29a0e-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="29a0e-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="29a0e-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="29a0e-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="29a0e-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="29a0e-412">クライアントの有効な IA アドレスの数を取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-413">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="29a0e-414">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-414">Description</span></span>

<span data-ttu-id="29a0e-415">このサービスでは、クライアントの有効な IPv6 アドレスの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="29a0e-416">有効な IPv6 アドレスがクライアントにバインドされ (割り当てられ)、IP インスタンスに登録されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-417">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-417">Input Parameters</span></span>

- <span data-ttu-id="29a0e-418">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-419">**address_count**: 返されるアドレス数へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-420">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-420">Return Values</span></span>

- <span data-ttu-id="29a0e-421">**NX_SUCCESS**: (0x00) IANA リース データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="29a0e-422">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-423">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-424">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-424">Allowed From</span></span>

<span data-ttu-id="29a0e-425">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-426">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="29a0e-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="29a0e-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="29a0e-428">クライアントの IA データをアドレス インデックスで取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-429">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="29a0e-430">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-430">Description</span></span>

<span data-ttu-id="29a0e-431">このサービスでは、クライアントの IA アドレスとリース データをアドレス インデックスで取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="29a0e-432">無効なインデックスが指定された場合、またはそのインデックスにある IPv6 アドレスが無効な場合は、NX_DHCPV6_IA_ADDRESS_NOT_VALID エラー状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-433">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-433">Input Parameters</span></span>

- <span data-ttu-id="29a0e-434">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-435">**address_index**: DHCPv6 IA テーブルへのインデックス</span><span class="sxs-lookup"><span data-stu-id="29a0e-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="29a0e-436">**ip_address**: 取得する IPv6 アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="29a0e-437">**preferred_lifetime**: IA アドレスが非推奨になる時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="29a0e-438">**valid_lifetime**: IA アドレスの有効期限が切れる時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-439">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-439">Return Values</span></span>

- <span data-ttu-id="29a0e-440">**NX_SUCCESS**: (0x00) IANA データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="29a0e-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID**: (0xEAD) インデックスが無効であるか、指定されたインデックスにある IPv6 アドレスが無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="29a0e-442">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-443">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-444">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-444">Allowed From</span></span>

<span data-ttu-id="29a0e-445">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-446">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-447">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-447">See Also</span></span>

- <span data-ttu-id="29a0e-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="29a0e-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="29a0e-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="29a0e-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="29a0e-452">DNS サーバー アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-453">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="29a0e-454">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-454">Description</span></span>

<span data-ttu-id="29a0e-455">このサービスでは、クライアント リストの指定されたインデックスにある DNS サーバー IPv6 アドレス データを取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="29a0e-456">リストのそのインデックスにサーバー アドレスがない場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="29a0e-457">インデックスは、ユーザーが構成可能な NX_DHCPV6_NUM_DNS_SERVERS オプションで指定された DNS サーバー リストのサイズを超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-458">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-458">Input Parameters</span></span>

- <span data-ttu-id="29a0e-459">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-460">**index**: DNS サーバー リストへのインデックス</span><span class="sxs-lookup"><span data-stu-id="29a0e-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="29a0e-461">**server_address**: サーバー アドレス バッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-462">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-462">Return Values</span></span>

- <span data-ttu-id="29a0e-463">**NX_SUCCESS**: (0x00) アドレスが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="29a0e-464">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-465">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-466">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-466">Allowed From</span></span>

<span data-ttu-id="29a0e-467">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-468">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-469">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-469">See Also</span></span>

- <span data-ttu-id="29a0e-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="29a0e-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="29a0e-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="29a0e-474">DHCPv6 オプション データを取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-475">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="29a0e-476">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-476">Description</span></span>

<span data-ttu-id="29a0e-477">このサービスでは、指定されたオプション コードの DHCPv6 オプション データを DHCPv6 メッセージから取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-478">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-478">Input Parameters</span></span>

- <span data-ttu-id="29a0e-479">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-480">**option_code**: 取得するデータのオプション コード</span><span class="sxs-lookup"><span data-stu-id="29a0e-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="29a0e-481">**buffer**: データのコピー先のバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="29a0e-482">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-482">Return Values</span></span>

- <span data-ttu-id="29a0e-483">**NX_SUCCESS**: (0x00) オプション データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="29a0e-484">**NX_DHCPV6_UNKNOWN_OPTION**: (0xEAB) オプション コードが不明であるか、サポートされていません</span><span class="sxs-lookup"><span data-stu-id="29a0e-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="29a0e-485">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-486">NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="29a0e-487">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-488">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-488">Allowed From</span></span>

<span data-ttu-id="29a0e-489">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-490">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-491">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-491">See Also</span></span>

- <span data-ttu-id="29a0e-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="29a0e-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="29a0e-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="29a0e-496">クライアントの IP アドレス リースの経過時間を取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-497">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="29a0e-498">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-498">Description</span></span>

<span data-ttu-id="29a0e-499">このサービスでは、クライアントの IPv6 アドレス リースの経過時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="29a0e-500">この関数は、クライアントに割り当てられたすべての IPv6 アドレスをチェックして最初の有効なアドレスを探します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="29a0e-501">有効なアドレスが見つからない場合、経過時間の値として 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-502">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-502">Input Parameters</span></span>

- <span data-ttu-id="29a0e-503">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-504">**time_accrued**: IP リースの経過時間へのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-505">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-505">Return Values</span></span>

- <span data-ttu-id="29a0e-506">**NX_SUCCESS**: (0x00) 経過時間が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="29a0e-507">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-508">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-509">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-509">Allowed From</span></span>

<span data-ttu-id="29a0e-510">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-511">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-512">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-512">See Also</span></span>

- <span data-ttu-id="29a0e-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="29a0e-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="29a0e-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="29a0e-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="29a0e-518">タイム サーバー アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="29a0e-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-519">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="29a0e-520">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-520">Description</span></span>

<span data-ttu-id="29a0e-521">このサービスでは、クライアント リストの指定されたインデックスにあるタイム サーバーの IPv6 アドレス データを取得します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="29a0e-522">リストのそのインデックスにサーバー アドレスがない場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="29a0e-523">インデックスは、ユーザーが構成可能な NX_DHCPV6_NUM_TIME_SERVERS オプションで指定されたタイム サーバー リストのサイズを超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-524">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-524">Input Parameters</span></span>

- <span data-ttu-id="29a0e-525">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-526">**index**: タイム サーバー リストへのインデックス</span><span class="sxs-lookup"><span data-stu-id="29a0e-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="29a0e-527">**server_address**: サーバー アドレス バッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-528">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-528">Return Values</span></span>

- <span data-ttu-id="29a0e-529">**NX_SUCCESS**: (0x00) アドレスが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="29a0e-530">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-531">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-532">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-532">Allowed From</span></span>

<span data-ttu-id="29a0e-533">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-534">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-535">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-535">See Also</span></span>

- <span data-ttu-id="29a0e-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="29a0e-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="29a0e-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="29a0e-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="29a0e-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="29a0e-541">IP テーブルからクライアント IP アドレスを削除する</span><span class="sxs-lookup"><span data-stu-id="29a0e-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-542">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-543">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-543">Description</span></span>

<span data-ttu-id="29a0e-544">このサービスでは、DHCPv6 ステート マシンを再起動し、DHCPv6 プロトコルを再実行するために、クライアントを再初期化します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="29a0e-545">クライアントが DHPCv6 ステート マシンをまだ起動していない場合、または IPv6 アドレスが割り当てられていない場合、これは不要です。</span><span class="sxs-lookup"><span data-stu-id="29a0e-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="29a0e-546">DHCPv6 クライアントに保存されているアドレスと、IP インスタンスに登録されているアドレスは、どちらもクリアされます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="29a0e-547">アプリケーションでは、*nx_dhcpv6_start サービス* を使用して DHCPv6 クライアントを起動し、*nx_dhcpv6_request_solicit* を呼び出して IPv6 アドレス割り当ての要求を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29a0e-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-548">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-548">Input Parameters</span></span>

- <span data-ttu-id="29a0e-549">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-550">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-550">Return Values</span></span>

- <span data-ttu-id="29a0e-551">**NX_SUCCESS**: (0x00) アドレスが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="29a0e-552">**NX_DHCPV6_ALREADY_STARTED**: (0xE91) DHCPv6 クライアントは既に実行されています</span><span class="sxs-lookup"><span data-stu-id="29a0e-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="29a0e-553">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-554">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-555">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-555">Allowed From</span></span>

<span data-ttu-id="29a0e-556">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-557">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-558">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-558">See Also</span></span>

- <span data-ttu-id="29a0e-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="29a0e-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="29a0e-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="29a0e-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="29a0e-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="29a0e-562">クライアントの CONFIRM 状態を処理する</span><span class="sxs-lookup"><span data-stu-id="29a0e-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-563">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-564">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-564">Description</span></span>

<span data-ttu-id="29a0e-565">このサービスは、CONFIRM 要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="29a0e-566">サーバーから応答を受信すると、DHCPv6 クライアントは受信したデータでリース パラメーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-567">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-567">Input Parameters</span></span>

- <span data-ttu-id="29a0e-568">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-569">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-569">Return Values</span></span>

- <span data-ttu-id="29a0e-570">**NX_SUCCESS**: (0x00) CONFIRM メッセージが正常に送信され、処理されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="29a0e-571">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-572">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-573">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-573">Allowed From</span></span>

<span data-ttu-id="29a0e-574">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-575">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-576">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-576">See Also</span></span>

- <span data-ttu-id="29a0e-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="29a0e-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="29a0e-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="29a0e-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="29a0e-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="29a0e-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="29a0e-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="29a0e-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="29a0e-581">クライアントの INFORM REQUEST 状態を処理する</span><span class="sxs-lookup"><span data-stu-id="29a0e-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-582">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-583">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-583">Description</span></span>

<span data-ttu-id="29a0e-584">このサービスでは、INFORM REQUEST メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="29a0e-585">応答を受信すると、応答が処理され、それが有効であり、サーバーが要求に応じたことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="29a0e-586">その後、クライアント インスタンスは、必要に応じてサーバー情報で更新されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-587">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-587">Input Parameters</span></span>

- <span data-ttu-id="29a0e-588">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-589">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-589">Return Values</span></span>

- <span data-ttu-id="29a0e-590">**NX_SUCCESS**: (0x00) INFORM REQUEST メッセージが正常に作成され、処理されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="29a0e-591">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-592">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-593">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-593">Allowed From</span></span>

<span data-ttu-id="29a0e-594">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-595">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-596">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-596">See Also</span></span>

- <span data-ttu-id="29a0e-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="29a0e-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="29a0e-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="29a0e-599">DHCPv6 オプション要求に DNS サーバーを追加する</span><span class="sxs-lookup"><span data-stu-id="29a0e-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-600">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-601">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-601">Description</span></span>

<span data-ttu-id="29a0e-602">このサービスでは、DHCPv6 オプション要求に、DNS サーバー情報を要求するためのオプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="29a0e-603">サーバーの応答に DNS サーバー データが含まれている場合、クライアントは DNS サーバーを保存する余地があれば保存します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="29a0e-604">クライアントが保存できる DNS サーバーの数は、構成可能な NX_DHCPV6_NUM_DNS_SERVERS オプションによって決まります。既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="29a0e-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-605">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-605">Input Parameters</span></span>

- <span data-ttu-id="29a0e-606">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-607">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-607">Return Values</span></span>

- <span data-ttu-id="29a0e-608">**NX_SUCCESS**: (0x00) DNS サーバー オプションが含まれています</span><span class="sxs-lookup"><span data-stu-id="29a0e-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="29a0e-609">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-610">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-611">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-611">Allowed From</span></span>

<span data-ttu-id="29a0e-612">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-613">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="29a0e-614">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-614">See Also</span></span>

- <span data-ttu-id="29a0e-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="29a0e-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="29a0e-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="29a0e-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="29a0e-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="29a0e-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="29a0e-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="29a0e-619">オプション要求リストに完全修飾ドメイン名オプションを追加する</span><span class="sxs-lookup"><span data-stu-id="29a0e-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-620">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="29a0e-621">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-621">Description</span></span>

<span data-ttu-id="29a0e-622">このサービスでは、DHCPv6 オプション要求に、クライアントの完全修飾ドメイン名を追加するためのオプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="29a0e-623">FQDN オプションには、3 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="29a0e-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="29a0e-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0: クライアントで使用される FQDN とアドレスについて、FQDN から IPv6 アドレスへのマッピングを更新します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="29a0e-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1: クライアントでサーバーに対して使用される FQDN とアドレスについて、FQDN から IPv6 アドレスへのマッピングを更新します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="29a0e-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2: クライアントに代わって DNS 更新を実行しないようサーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-627">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-627">Input Parameters</span></span>

- <span data-ttu-id="29a0e-628">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-629">**domain_name**: ドメイン名を保持する文字列</span><span class="sxs-lookup"><span data-stu-id="29a0e-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="29a0e-630">**op**: 適用する FQDN オプションの種類 (上記の一覧を参照)</span><span class="sxs-lookup"><span data-stu-id="29a0e-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-631">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-631">Return Values</span></span>

- <span data-ttu-id="29a0e-632">**NX_SUCCESS**: (0x00) FQDN オプションが含まれています</span><span class="sxs-lookup"><span data-stu-id="29a0e-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="29a0e-633">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-634">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-635">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-635">Allowed From</span></span>

<span data-ttu-id="29a0e-636">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-637">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="29a0e-638">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-638">See Also</span></span>

- <span data-ttu-id="29a0e-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="29a0e-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="29a0e-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="29a0e-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="29a0e-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="29a0e-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="29a0e-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="29a0e-643">DHCPv6 オプション要求にドメイン名オプションを追加する</span><span class="sxs-lookup"><span data-stu-id="29a0e-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-644">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-645">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-645">Description</span></span>

<span data-ttu-id="29a0e-646">このサービスでは、クライアント要求メッセージのオプション要求にドメイン名オプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="29a0e-647">サーバーの応答にドメイン名データが含まれている場合、ドメイン名のサイズがドメイン名を保持するためのバッファー サイズ内であれば、クライアントはドメイン名情報を保存します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="29a0e-648">このバッファー サイズは構成可能なオプション (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) であり、既定値は 30 バイトです。</span><span class="sxs-lookup"><span data-stu-id="29a0e-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-649">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-649">Input Parameters</span></span>

- <span data-ttu-id="29a0e-650">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-651">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-651">Return Values</span></span>

- <span data-ttu-id="29a0e-652">**NX_SUCCESS**: (0x00) ドメイン名オプションが設定されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="29a0e-653">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-654">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-655">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-655">Allowed From</span></span>

<span data-ttu-id="29a0e-656">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-657">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="29a0e-658">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-658">See Also</span></span>

- <span data-ttu-id="29a0e-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="29a0e-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="29a0e-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="29a0e-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="29a0e-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="29a0e-663">オプション要求としてタイム サーバー データを設定する</span><span class="sxs-lookup"><span data-stu-id="29a0e-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-664">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-665">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-665">Description</span></span>

<span data-ttu-id="29a0e-666">このサービスでは、クライアント要求メッセージのオプション要求に、タイム サーバー情報のオプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="29a0e-667">サーバーの応答にタイム サーバー データが含まれている場合、クライアントはタイム サーバーを保存する余地があれば保存します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="29a0e-668">クライアントが保存できるタイム サーバーの数は、構成可能な NX_DHCPV6_NUM_TIME _SERVERS オプションによって決まります。既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="29a0e-668">The number of time servers the Client can store is determined by the configurable option</span></span>

NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.

### <a name="input-parameters"></a><span data-ttu-id="29a0e-670">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-670">Input Parameters</span></span>

- <span data-ttu-id="29a0e-671">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-672">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-672">Return Values</span></span>

- <span data-ttu-id="29a0e-673">**NX_SUCCESS**: (0x00) タイム サーバー オプションが追加されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="29a0e-674">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-675">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-676">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-676">Allowed From</span></span>

<span data-ttu-id="29a0e-677">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-678">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="29a0e-679">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-679">See Also</span></span>

- <span data-ttu-id="29a0e-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="29a0e-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="29a0e-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="29a0e-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="29a0e-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="29a0e-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="29a0e-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="29a0e-684">オプション要求としてタイム ゾーン データを設定する</span><span class="sxs-lookup"><span data-stu-id="29a0e-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-685">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-686">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-686">Description</span></span>

<span data-ttu-id="29a0e-687">このサービスでは、クライアント オプション要求に、タイム ゾーン情報を要求するためのオプションを追加します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="29a0e-688">サーバーの応答にタイム ゾーン データが含まれている場合、タイム ゾーンのサイズがタイム ゾーンを保持するためのバッファー サイズ内であれば、クライアントはタイム ゾーン情報を保存します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="29a0e-689">このバッファー サイズは構成可能なオプション (NX_DHCPV6_TIME_ZONE_BUFFER_SIZE) であり、既定値は 10 バイトです。</span><span class="sxs-lookup"><span data-stu-id="29a0e-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-690">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-690">Input Parameters</span></span>

- <span data-ttu-id="29a0e-691">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-692">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-692">Return Values</span></span>

- <span data-ttu-id="29a0e-693">**NX_SUCCESS**: (0x00) タイム ゾーン オプションが追加されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="29a0e-694">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-695">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-696">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-696">Allowed From</span></span>

<span data-ttu-id="29a0e-697">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-698">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="29a0e-699">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-699">See Also</span></span>

- <span data-ttu-id="29a0e-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="29a0e-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="29a0e-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="29a0e-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="29a0e-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="29a0e-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="29a0e-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="29a0e-704">DHCPv6 RELEASE メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="29a0e-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-705">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-706">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-706">Description</span></span>

<span data-ttu-id="29a0e-707">このサービスでは、クライアント ネットワーク上で RELEASE メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="29a0e-708">メッセージが正常に送信されると、成功状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="29a0e-709">正常完了は、クライアントが応答を受信したことや、IPv6 アドレスが既に付与されていることを意味するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="29a0e-710">DHCPv6 クライアント スレッド タスクは、DHCPv6 サーバーからの応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="29a0e-711">応答を受信すると、それが有効であることを確認し、データをクライアント レコードに保存します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-712">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-712">Input Parameters</span></span>

- <span data-ttu-id="29a0e-713">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-714">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-714">Return Values</span></span>

- <span data-ttu-id="29a0e-715">**NX_SUCCESS**: (0x00) RELEASE メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="29a0e-716">**NX_DHCPV6_NOT_STARTED**: (0xE92) DHCPv6 クライアント タスクが開始されていません</span><span class="sxs-lookup"><span data-stu-id="29a0e-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="29a0e-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID**: (0xEAD) クライアントにアドレスがバインドされていません</span><span class="sxs-lookup"><span data-stu-id="29a0e-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="29a0e-718">**NX_INVALID_INTERFACE**: (0x4C) IP アドレス テーブルに見つかりません</span><span class="sxs-lookup"><span data-stu-id="29a0e-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="29a0e-719">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-720">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-721">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-721">Allowed From</span></span>

<span data-ttu-id="29a0e-722">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-723">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-724">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-724">See Also</span></span>

- <span data-ttu-id="29a0e-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="29a0e-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="29a0e-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="29a0e-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="29a0e-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="29a0e-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="29a0e-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="29a0e-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="29a0e-729">SOLICIT メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="29a0e-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-730">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-731">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-731">Description</span></span>

<span data-ttu-id="29a0e-732">このサービスでは、ネットワーク上で SOLICIT メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="29a0e-733">メッセージが正常に送信されると、成功状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="29a0e-734">正常完了は、クライアントが応答を受信したことや、IPv6 アドレスが既に付与されていることを意味するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="29a0e-735">DHCPv6 クライアント スレッド タスクは、DHCPv6 サーバーからの応答 (ADVERTISE メッセージ) を待機します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="29a0e-736">応答を受信すると、それが有効であることを確認し、データをクライアント レコードに保存して、クライアントを REQUEST 状態に昇格させます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="29a0e-737">Rapid Commit オプションを設定した場合、DHCPv6 クライアントは、サーバーの有効な ADVERTISE メッセージを受信すると、BOUND 状態に直接移行します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="29a0e-738">詳細については、*nx_dhcpv6_request_solicit_rapid* のサービスの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29a0e-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-739">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-739">Input Parameters</span></span>

- <span data-ttu-id="29a0e-740">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-741">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-741">Return Values</span></span>

- <span data-ttu-id="29a0e-742">**NX_SUCCESS**: (0x00) SOLICIT メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="29a0e-743">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-744">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-745">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-745">Allowed From</span></span>

<span data-ttu-id="29a0e-746">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-747">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="29a0e-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="29a0e-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="29a0e-749">Rapid Commit オプションを使用して SOLICIT メッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="29a0e-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-750">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-751">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-751">Description</span></span>

<span data-ttu-id="29a0e-752">このサービスでは、Rapid Commit オプションを設定して、ネットワーク上で SOLICIT メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="29a0e-753">メッセージが正常に送信されると、成功状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="29a0e-754">正常完了は、クライアントが応答を受信したことや、IPv6 アドレスが既に付与されていることを意味するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="29a0e-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="29a0e-755">DHCPv6 クライアント スレッド タスクは、DHCPv6 サーバーからの応答 (ADVERTISE メッセージ) を待機します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="29a0e-756">応答を受信すると、それが有効であることを確認し、データをクライアント レコードに保存して、クライアントを BOUND 状態に昇格させます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-757">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-757">Input Parameters</span></span>

- <span data-ttu-id="29a0e-758">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-759">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-759">Return Values</span></span>

- <span data-ttu-id="29a0e-760">**NX_SUCCESS**: (0x00) SOLICIT メッセージが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="29a0e-761">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-762">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-763">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-763">Allowed From</span></span>

<span data-ttu-id="29a0e-764">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-765">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-766">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-766">See Also</span></span>

- <span data-ttu-id="29a0e-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="29a0e-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="29a0e-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="29a0e-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="29a0e-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="29a0e-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="29a0e-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="29a0e-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="29a0e-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="29a0e-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="29a0e-772">DHCPv6 クライアント タスクを再開する</span><span class="sxs-lookup"><span data-stu-id="29a0e-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-773">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-774">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-774">Description</span></span>

<span data-ttu-id="29a0e-775">このサービスでは、DHCPv6 クライアント スレッド タスクを再開します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="29a0e-776">DHCPv6 クライアントの現在の状態 (Bound、Solicit など) が処理されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-777">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-777">Input Parameters</span></span>

- <span data-ttu-id="29a0e-778">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-779">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-779">Return Values</span></span>

- <span data-ttu-id="29a0e-780">**NX_SUCCESS**: (0x00) クライアントが正常に再開されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="29a0e-781">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-782">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-783">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-783">Allowed From</span></span>

<span data-ttu-id="29a0e-784">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-785">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-786">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-786">See Also</span></span>

- <span data-ttu-id="29a0e-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="29a0e-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="29a0e-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="29a0e-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="29a0e-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="29a0e-790">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="29a0e-791">クライアントの IP アドレス リースの経過時間を設定する</span><span class="sxs-lookup"><span data-stu-id="29a0e-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="29a0e-792">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="29a0e-793">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-793">Description</span></span>

<span data-ttu-id="29a0e-794">このサービスでは、クライアントのグローバル IP アドレスがサーバーによって割り当てられてからの経過時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="29a0e-795">これは、割り当てられた IPv6 アドレスにクライアントが現在バインドされている場合にのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29a0e-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-796">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-796">Input Parameters</span></span>

- <span data-ttu-id="29a0e-797">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="29a0e-798">**time_accrued**: IP リースの経過時間</span><span class="sxs-lookup"><span data-stu-id="29a0e-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-799">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-799">Return Values</span></span>

- <span data-ttu-id="29a0e-800">**NX_SUCCESS**: (0x00) 経過時間が正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="29a0e-801">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-802">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-802">Allowed From</span></span>

<span data-ttu-id="29a0e-803">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-804">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-805">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-805">See Also</span></span>

- <span data-ttu-id="29a0e-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="29a0e-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="29a0e-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="29a0e-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="29a0e-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="29a0e-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="29a0e-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="29a0e-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="29a0e-811">DHCPv6 クライアント タスクを開始する</span><span class="sxs-lookup"><span data-stu-id="29a0e-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-812">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-813">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-813">Description</span></span>

<span data-ttu-id="29a0e-814">このサービスでは、DHCPv6 クライアント タスクを開始し、DHCPv6 プロトコルを実行するためにクライアントを準備します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="29a0e-815">クライアント インスタンスに十分な情報 (クライアント DUID など) があることを確認し、DHCPv6 メッセージを送受信するための UDP ソケットを作成してバインドします。また、セッション時間と現在の IPv6 リースの有効期限を追跡するためのタイマーをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="29a0e-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-816">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-816">Input Parameters</span></span>

- <span data-ttu-id="29a0e-817">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-818">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-818">Return Values</span></span>

- <span data-ttu-id="29a0e-819">**NX_SUCCESS**: (0x00) クライアントが正常に起動されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="29a0e-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS**: (0xEA9) クライアントに必要なオプションがありません</span><span class="sxs-lookup"><span data-stu-id="29a0e-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="29a0e-821">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-822">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-823">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-823">Allowed From</span></span>

<span data-ttu-id="29a0e-824">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-825">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-826">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-826">See Also</span></span>

- <span data-ttu-id="29a0e-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="29a0e-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="29a0e-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="29a0e-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="29a0e-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="29a0e-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="29a0e-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="29a0e-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="29a0e-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="29a0e-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="29a0e-832">DHCPv6 クライアント タスクを停止する</span><span class="sxs-lookup"><span data-stu-id="29a0e-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-833">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-834">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-834">Description</span></span>

<span data-ttu-id="29a0e-835">このサービスでは、DHCPv6 クライアント タスクを停止し、再送信回数と最大再送信間隔をクリアします。また、セッションとリースの有効期限のタイマーを非アクティブ化し、DHCPv6 クライアント ソケット ポートのバインドを解除します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="29a0e-836">クライアントを再起動するには、DHCPv6 サーバーとの別のセッションを開始する前に、まずクライアントを停止し、必要に応じて再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29a0e-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="29a0e-837">詳細については、簡単な例のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="29a0e-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-838">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-838">Input Parameters</span></span>

- <span data-ttu-id="29a0e-839">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-840">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-840">Return Values</span></span>

- <span data-ttu-id="29a0e-841">**NX_SUCCESS**: (0x00) クライアントが正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="29a0e-842">**NX_DHCPV6_NOT_STARTED**: (0xE92) クライアント スレッドが開始されていません</span><span class="sxs-lookup"><span data-stu-id="29a0e-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="29a0e-843">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-844">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="29a0e-845">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-845">Allowed From</span></span>

<span data-ttu-id="29a0e-846">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-847">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-848">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-848">See Also</span></span>

- <span data-ttu-id="29a0e-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="29a0e-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="29a0e-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="29a0e-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="29a0e-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="29a0e-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="29a0e-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="29a0e-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="29a0e-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="29a0e-854">DHCPv6 クライアント タスクを中断する</span><span class="sxs-lookup"><span data-stu-id="29a0e-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="29a0e-855">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="29a0e-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="29a0e-856">説明</span><span class="sxs-lookup"><span data-stu-id="29a0e-856">Description</span></span>

<span data-ttu-id="29a0e-857">このサービスでは、DHCPv6 クライアント タスクと処理中のすべての要求を中断します。</span><span class="sxs-lookup"><span data-stu-id="29a0e-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="29a0e-858">タイマーが非アクティブ化され、クライアントの状態が非実行に設定されます。</span><span class="sxs-lookup"><span data-stu-id="29a0e-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="29a0e-859">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="29a0e-859">Input Parameters</span></span>

- <span data-ttu-id="29a0e-860">**dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="29a0e-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="29a0e-861">戻り値</span><span class="sxs-lookup"><span data-stu-id="29a0e-861">Return Values</span></span>

- <span data-ttu-id="29a0e-862">**NX_SUCCESS**: (0x00) クライアントが正常に一時停止されました</span><span class="sxs-lookup"><span data-stu-id="29a0e-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="29a0e-863">**NX_DHCPV6_NOT_STARTED**: (0XE92) クライアントが実行されていないため、一時停止できません</span><span class="sxs-lookup"><span data-stu-id="29a0e-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="29a0e-864">NX_PTR_ERROR: (0x16) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="29a0e-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="29a0e-865">NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります</span><span class="sxs-lookup"><span data-stu-id="29a0e-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="29a0e-866">許可元</span><span class="sxs-lookup"><span data-stu-id="29a0e-866">Allowed From</span></span>

<span data-ttu-id="29a0e-867">Threads</span><span class="sxs-lookup"><span data-stu-id="29a0e-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="29a0e-868">例</span><span class="sxs-lookup"><span data-stu-id="29a0e-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="29a0e-869">参照</span><span class="sxs-lookup"><span data-stu-id="29a0e-869">See Also</span></span>

- <span data-ttu-id="29a0e-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="29a0e-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="29a0e-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="29a0e-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="29a0e-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="29a0e-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="29a0e-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="29a0e-873">nx_dhcpv6_stop</span></span>
