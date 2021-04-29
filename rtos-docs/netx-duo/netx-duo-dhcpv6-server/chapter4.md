---
title: 第 4 章 - Azure RTOS NetX Duo DHCPv6 サーバーのサービス
description: この章では、NetX Duo DHCPv6Server のすべてのサービスについて説明します
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810844"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="2c9e3-103">第 4 章 - Azure RTOS NetX Duo DHCPv6 サーバーのサービス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="2c9e3-104">この章では、NetX Duo DHCPv6Server のすべてのサービスについて説明します (以下の一覧を参照)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="2c9e3-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2c9e3-106">nx_dhcpv6_server_create *DHCPv6 サーバー インスタンスを作成します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="2c9e3-107">nx_dhcpv6_server_delete *DHCPv6 サーバー インスタンスを削除します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="2c9e3-108">nx_dhcpv6_server_start *DHCPv6 サーバー タスクを開始します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="2c9e3-109">nx_dhcpv6_server_suspend *DHCPv6 サーバー タスクを一時停止します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="2c9e3-110">nx_dhcpv6_server_resume *DHCPv6 クライアントの処理を再開します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="2c9e3-111">nx_dhcpv6_server_suspend *DHCPv6 クライアントの処理を一時停止します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="2c9e3-112">nx_dhcpv6_create_dns_address *DNS サーバーをオプション要求用に設定します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="2c9e3-113">nx_dhcpv6_create_ip_address_range *リースする IP アドレスの範囲を作成します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="2c9e3-114">nx_dhcpv6_reserve_ip_address_range *サーバー リストで IP アドレスの範囲を予約します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="2c9e3-115">nx_dhcpv6_set_server_duid *DHCPv6 パケット用のサーバー DUID を設定します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="2c9e3-116">nx_dhcpv6_add_ip_address_lease *DHCPv6 サーバー テーブルにリース レコードを追加します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="2c9e3-117">Nx_dhcpv6_retrieve_ip_address_lease *サーバー テーブルから IP リース レコードを取得します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="2c9e3-118">nx_dhcpv6_add_client_record *サーバー テーブルに DHCPv6 クライアント レコードを追加します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="2c9e3-119">nx_dhcpv6_retrieve_client_record *サーバー テーブルからクライアント レコードを取得します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="2c9e3-120">nx_dhcpv6_server_interface_set *サーバー DHCPv6 サービス用の インターフェイス インデックスを設定します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="2c9e3-121">nx_dhcpv6_server_option_request_handler_set *オプション要求ハンドラーを設定します*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="2c9e3-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="2c9e3-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="2c9e3-123">ネットワーク DNS サーバーを設定する</span><span class="sxs-lookup"><span data-stu-id="2c9e3-123">Set the network DNS server</span></span>

<span data-ttu-id="2c9e3-124">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="2c9e3-125">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-125">**Description**</span></span>

<span data-ttu-id="2c9e3-126">このサービスを使用すると、サーバー DHCPv6 ネットワーク インターフェイス用の DNS サーバー アドレスが DHCPv6 サーバーに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="2c9e3-127">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-127">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-128">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-129">**dns_ipv6_address** DNS サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="2c9e3-130">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-130">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-131">**NX_SUCCESS** (0x00) DNS サーバーが DHCPv6 サーバー インスタンスに保存されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="2c9e3-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 無効なアドレスが指定されています</span><span class="sxs-lookup"><span data-stu-id="2c9e3-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="2c9e3-133">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-134">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-134">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-135">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-135">Application Code</span></span>

<span data-ttu-id="2c9e3-136">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="2c9e3-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="2c9e3-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="2c9e3-138">サーバーの IP アドレス リストを作成します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-138">Create the Server IP address list</span></span>

<span data-ttu-id="2c9e3-139">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="2c9e3-140">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-140">**Description**</span></span>

<span data-ttu-id="2c9e3-141">このサービスを使用すると、サーバーの割り当て可能なアドレス範囲の開始アドレスと終了アドレスによって指定された IP アドレス リストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="2c9e3-142">開始アドレスと終了アドレスは、サーバー インターフェイスのアドレス プレフィックスと一致している必要があります (サーバー DHCPv6 インターフェイスと同じリンク上にある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="2c9e3-143">実際に追加されたアドレスの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="2c9e3-144">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-144">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-145">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-146">**start_ipv6_address** 追加するアドレスの先頭</span><span class="sxs-lookup"><span data-stu-id="2c9e3-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="2c9e3-147">**end_ipv6_address** 追加するアドレスの末尾</span><span class="sxs-lookup"><span data-stu-id="2c9e3-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="2c9e3-148">\***addresses_added** 追加されたアドレスの出力</span><span class="sxs-lookup"><span data-stu-id="2c9e3-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="2c9e3-149">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-149">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-150">**NX_SUCCESS** (0x00) IP アドレス リストが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="2c9e3-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 無効なアドレスが指定されています</span><span class="sxs-lookup"><span data-stu-id="2c9e3-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="2c9e3-152">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-153">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-153">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-154">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-154">Application Code</span></span>

<span data-ttu-id="2c9e3-155">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="2c9e3-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="2c9e3-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="2c9e3-157">指定した IP アドレスの範囲を予約します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="2c9e3-158">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="2c9e3-159">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-159">**Description**</span></span>

<span data-ttu-id="2c9e3-160">このサービスを使用すると、開始アドレスと終了アドレスによって指定した IP アドレスの範囲が予約されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="2c9e3-161">これらのアドレスは、前に作成したサーバーの IP アドレス範囲内に含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="2c9e3-162">これらのアドレスは、DHCPv6 サーバーによってクライアントに割り当てられなくなります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="2c9e3-163">開始アドレスと終了アドレスは、サーバー インターフェイスのアドレス プレフィックスと一致している必要があります (サーバー DHCPv6 ネットワーク インターフェイスと同じリンク上にある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="2c9e3-164">実際に予約されたアドレスの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="2c9e3-165">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-165">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-166">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-167">**start_ipv6_address** 予約するアドレスの先頭</span><span class="sxs-lookup"><span data-stu-id="2c9e3-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="2c9e3-168">**end_ipv6_address** 予約するアドレスの末尾</span><span class="sxs-lookup"><span data-stu-id="2c9e3-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="2c9e3-169">\***addresses_reserved** 予約されたアドレスの数</span><span class="sxs-lookup"><span data-stu-id="2c9e3-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="2c9e3-170">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-170">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-171">**NX_SUCCESS** (0x00) RELEASE メッセージが正常に作成され、処理されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="2c9e3-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 無効なアドレスが指定されています</span><span class="sxs-lookup"><span data-stu-id="2c9e3-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="2c9e3-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) サーバー アドレス リストに開始アドレスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="2c9e3-174">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-175">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-175">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-176">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-176">Application Code</span></span>

<span data-ttu-id="2c9e3-177">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="2c9e3-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="2c9e3-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="2c9e3-179">DHCPv6 サーバー インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="2c9e3-180">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="2c9e3-181">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-181">**Description**</span></span>

<span data-ttu-id="2c9e3-182">このサービスを使用すると、指定した入力を使用して DHCPv6 サーバー タスクが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="2c9e3-183">コールバック ハンドラーは、省略可能な入力です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-183">The callback handlers are optional input.</span></span> <span data-ttu-id="2c9e3-184">スタック ポインター、IP インスタンス、パケット プールの入力は必須です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="2c9e3-185">IP インスタンスとパケット プールは、既に作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="2c9e3-186">ユーザーには、nx_dhcpv6_server_option_request_handler_set を呼び出して、オプション要求ハンドラーを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="2c9e3-187">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-187">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-188">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-189">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="2c9e3-190">**name_str** サーバー名へのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="2c9e3-191">**packet_pool_ptr** サーバーのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="2c9e3-192">**stack_ptr** サーバーのスタック メモリへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="2c9e3-193">**stack_size** サーバーのスタック メモリのサイズ</span><span class="sxs-lookup"><span data-stu-id="2c9e3-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="2c9e3-194">**dhcpv6_address_declined_handler** クライアントの拒否または解放メッセージ ハンドラーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="2c9e3-195">**dhcpv6_option_request_handler** オプション要求オプション ハンドラーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="2c9e3-196">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-196">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-197">**NX_SUCCESS** (0x00) サーバーが正常に再開されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="2c9e3-198">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="2c9e3-199">NX_DHCPV6_PARAM_ERROR 無効なポインターではない入力です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="2c9e3-200">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-200">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-201">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-201">Application Code</span></span>

<span data-ttu-id="2c9e3-202">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="2c9e3-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="2c9e3-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="2c9e3-204">DHCPv6 サーバーを削除します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-205">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="2c9e3-206">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-206">**Description**</span></span>

<span data-ttu-id="2c9e3-207">このサービスを使用すると、DHCPv6 サーバー タスクと、サーバーによって処理されていたすべての要求が削除されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="2c9e3-208">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-208">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-209">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-210">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-210">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-211">**NX_SUCCESS** (0x00) サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="2c9e3-212">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-213">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-213">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-214">Threads</span><span class="sxs-lookup"><span data-stu-id="2c9e3-214">Threads</span></span>

<span data-ttu-id="2c9e3-215">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="2c9e3-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="2c9e3-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="2c9e3-217">DHCPv6 サーバー タスクを再開します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="2c9e3-218">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="2c9e3-219">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-219">**Description**</span></span>

<span data-ttu-id="2c9e3-220">このサービスを使用すると、DHCPv6 サーバー タスクと、サーバーによって処理されていたすべての要求が再開されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="2c9e3-221">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-221">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-222">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-223">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-223">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-224">**NX_SUCCESS** (0x00) サーバーが正常に再開されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="2c9e3-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) サーバーは既に実行されています</span><span class="sxs-lookup"><span data-stu-id="2c9e3-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="2c9e3-226">**状態** (可変) ThreadX と NetX Duo のエラー ステータス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="2c9e3-227">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-228">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-228">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-229">Threads</span><span class="sxs-lookup"><span data-stu-id="2c9e3-229">Threads</span></span>

<span data-ttu-id="2c9e3-230">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="2c9e3-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="2c9e3-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="2c9e3-232">DHCPv6 サーバー タスクを一時停止します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="2c9e3-233">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="2c9e3-234">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-234">**Description**</span></span>

<span data-ttu-id="2c9e3-235">このサービスを使用すると、DHCPv6 サーバー タスクと、サーバーによって処理されていたすべての要求が一時停止されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="2c9e3-236">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-236">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-237">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-238">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-238">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-239">**NX_SUCCESS** (0x00) サーバーが正常に再開されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="2c9e3-240">**NX_DHCPV6_NOT_STARTED** (0xE92) サーバーが開始されていません</span><span class="sxs-lookup"><span data-stu-id="2c9e3-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="2c9e3-241">**状態** (可変) ThreadX と Netx Duo のエラー ステータス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="2c9e3-242">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-243">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-243">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-244">Threads</span><span class="sxs-lookup"><span data-stu-id="2c9e3-244">Threads</span></span>

<span data-ttu-id="2c9e3-245">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="2c9e3-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="2c9e3-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="2c9e3-247">DHCPv6 サーバー タスクを開始します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="2c9e3-248">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="2c9e3-249">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-249">**Description**</span></span>

<span data-ttu-id="2c9e3-250">このサービスを使用すると、DHCPv6 サーバー タスクが開始され、DHCPv6 クライアント メッセージを受信するためのアプリケーション要求を処理するようにサーバーが準備されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="2c9e3-251">サーバー インスタンスに十分な情報 (サーバーの DUID) があることが確認され、DHCPv6 メッセージを送受信するための UDP ソケットが作成されてバインドされます。また、セッション時間と IP リースの有効期限を追跡するためのタイマーがアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-252">DHCPv6 サーバーを実行する前に、ホスト アプリケーションで、サーバーが IP アドレスを割り当てることができる IP アドレス範囲を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="2c9e3-253">また、サーバーの DUID と DHCPv6 インターフェイスを設定する必要もあります (それぞれ、*nx_dhcpv6_server_duid_set* と *nx_dhcpv6_server_interface_set* を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="2c9e3-254">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-254">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-255">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-256">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-256">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-257">**NX_SUCCESS** (0x00) サーバーが正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="2c9e3-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) サーバーは既に実行されています</span><span class="sxs-lookup"><span data-stu-id="2c9e3-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="2c9e3-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) リースのための割り当て可能なアドレスがサーバーにありません</span><span class="sxs-lookup"><span data-stu-id="2c9e3-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="2c9e3-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) グローバル アドレス インデックスが設定されていません</span><span class="sxs-lookup"><span data-stu-id="2c9e3-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="2c9e3-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) サーバーの DUID が作成されていません</span><span class="sxs-lookup"><span data-stu-id="2c9e3-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="2c9e3-262">**状態** (可変) ThreadX と NetX Duo のエラー ステータス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="2c9e3-263">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-264">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-264">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-265">Threads</span><span class="sxs-lookup"><span data-stu-id="2c9e3-265">Threads</span></span>

<span data-ttu-id="2c9e3-266">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="2c9e3-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="2c9e3-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="2c9e3-268">サーバー テーブルから IP アドレスのリースを取得します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="2c9e3-269">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="2c9e3-270">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-270">**Description**</span></span>

<span data-ttu-id="2c9e3-271">このサービスを使用すると、サーバー テーブルの指定したテーブル インデックス位置にある IP アドレス リース レコードが取得されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="2c9e3-272">これは、クライアント レコード データを取得する前でも後でも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="2c9e3-273">DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="2c9e3-274">IP リース データとクライアント レコード データを不揮発性メモリに保存する順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-275">サーバー テーブルに、またはサーバー テーブルからデータをコピーするときは、最初に DHCPv6 サーバーを停止または一時停止することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="2c9e3-276">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-276">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-277">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-278">**table_index** リースを格納するテーブル インデックス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="2c9e3-279">**lease_IP_address** クライアントにリースする IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="2c9e3-280">**T1** クライアントが要求した更新時間</span><span class="sxs-lookup"><span data-stu-id="2c9e3-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="2c9e3-281">**T2** クライアントが要求した再バインド時間</span><span class="sxs-lookup"><span data-stu-id="2c9e3-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="2c9e3-282">**valid_lifetime** クライアント リースが非推奨になります</span><span class="sxs-lookup"><span data-stu-id="2c9e3-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="2c9e3-283">**preferred_lifetime** クライアント リースが無効になります</span><span class="sxs-lookup"><span data-stu-id="2c9e3-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="2c9e3-284">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-284">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-285">**NX_SUCCESS** (0x00) サーバーが正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="2c9e3-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) 無効な IP リース データ入力</span><span class="sxs-lookup"><span data-stu-id="2c9e3-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="2c9e3-287">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-288">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-288">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-289">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-289">Application code</span></span>

<span data-ttu-id="2c9e3-290">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="2c9e3-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="2c9e3-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="2c9e3-292">サーバー テーブルに IP アドレスのリースを追加します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="2c9e3-293">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="2c9e3-294">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-294">**Description**</span></span>

<span data-ttu-id="2c9e3-295">このサービスを使用すると、前の DHCPv6 サーバー セッションの IP リース データが、不揮発性メモリからサーバー リース テーブルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="2c9e3-296">サーバーが初めて実行され、以前のリース データがない場合、これは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="2c9e3-297">ホスト アプリケーションで IP アドレスを割り当てるための IP アドレス範囲を作成する必要がある場合は、*nx_dhcpv6_create_ip_address_range* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="2c9e3-298">データは、DHCPv6 リース レコードを再構築するのに十分です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="2c9e3-299">テーブル インデックスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-299">The table index need not be specified.</span></span> <span data-ttu-id="2c9e3-300">0xFFFFFFFF (無限大) に設定すると、データのコピー先として使用可能な次のスロットが DHCPv6 サーバーによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-301">クライアント レコードをアップロードする前に、IP リース データをアップロードする必要があります。どちらも、DHCPv6 サーバーを開始または再開する前に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="2c9e3-302">DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="2c9e3-303">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-303">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-304">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-305">**table_index** リースを格納するテーブル インデックス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="2c9e3-306">**lease_IP_address** クライアントにリースする IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="2c9e3-307">**T1** クライアントが要求した更新時間</span><span class="sxs-lookup"><span data-stu-id="2c9e3-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="2c9e3-308">**T2** クライアントが要求した再バインド時間</span><span class="sxs-lookup"><span data-stu-id="2c9e3-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="2c9e3-309">**valid_lifetime** クライアント リースが非推奨になります</span><span class="sxs-lookup"><span data-stu-id="2c9e3-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="2c9e3-310">**preferred_lifetime** クライアント リースが無効になります</span><span class="sxs-lookup"><span data-stu-id="2c9e3-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="2c9e3-311">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-311">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-312">**NX_SUCCESS** (0x00) サーバーが正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="2c9e3-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) リース データを増やすための空き領域がありません\*\*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="2c9e3-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) リース データがサーバー DHCPV6 インターフェイスとのリンク上にないようです</span><span class="sxs-lookup"><span data-stu-id="2c9e3-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="2c9e3-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) 無効な IP リース データ入力</span><span class="sxs-lookup"><span data-stu-id="2c9e3-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="2c9e3-316">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-317">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-317">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-318">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-318">Application code</span></span>

<span data-ttu-id="2c9e3-319">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="2c9e3-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="2c9e3-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="2c9e3-321">クライアント レコードをサーバー テーブルに追加します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="2c9e3-322">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="2c9e3-323">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-323">**Description**</span></span>

<span data-ttu-id="2c9e3-324">このサービスを使用すると、不揮発性メモリからサーバー テーブルに、クライアント データが一度に 1 レコードずつコピーされます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="2c9e3-325">これは、サーバーが再起動されていて、前のセッションのクライアント データをメモリから復元する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="2c9e3-326">サーバーに前のデータがない場合、クライアント テーブルはクライアント レコードを追加できるように DHCPv6 サーバーによって初期化されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="2c9e3-327">テーブル インデックスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="2c9e3-328">0xFFFFFFFF (無限大) に設定すると、次に使用可能なスロットが DHCPv6 サーバーによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="2c9e3-329">DHCPv6 サーバーにより、このデータからクライアント レコードを再構築できます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-330">ホスト アプリケーションでは、クライアント レコード データの前に、IP リース データをアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="2c9e3-331">これは、各クライアント レコードがそれぞれのテーブルの対応する IP リース レコードと結合されるように、DHCPv6 サーバーで内部的にテーブルをクロスリンクできるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="2c9e3-332">メモリから IP リース データをアップロードする方法の詳細については、*nx_dhcpv6_add_ip_address_lease* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-333">DUID の種類によっては、すべてのデータを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="2c9e3-334">たとえば、ベンダーによって割り当てられた DUID の種類がクライアントにある場合、DUID リンク レイヤー パラメーターに対して 0 を送信できます (MAC アドレス、ハードウェアの種類、DUID 時間)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="2c9e3-335">DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="2c9e3-336">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-336">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-337">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-338">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-338">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-339">**NX_SUCCESS** (0x00) サーバーが正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="2c9e3-340">**NX_INVALID_PARAMETERS** (0x4D) ポインターではない無効な値の入力\*\*</span><span class="sxs-lookup"><span data-stu-id="2c9e3-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="2c9e3-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) 別のクライアント レコードを追加するための空のスロットが残っていません</span><span class="sxs-lookup"><span data-stu-id="2c9e3-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="2c9e3-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) クライアントによって割り当てられたアドレスがサーバー リース テーブルに見つかりません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="2c9e3-343">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-344">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-344">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-345">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-345">Application code</span></span>

<span data-ttu-id="2c9e3-346">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="2c9e3-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="2c9e3-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="2c9e3-348">サーバー テーブルからクライアント レコードを取得します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="2c9e3-349">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="2c9e3-350">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-350">**Description**</span></span>

<span data-ttu-id="2c9e3-351">このサービスを使用すると、記憶域用のサーバーのクライアント レコード テーブルから不揮発性メモリに重要なデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="2c9e3-352">サーバーで、逆のプロセスでこのようなデータから適切なクライアント レコードを再構築できます(サーバー テーブルにデータをアップロードする)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="2c9e3-353">DUID の種類に関係なく、ポインターを NULL ポインターにすることはできません。すべてのパラメーターについて、データは 0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="2c9e3-354">たとえば、クライアントの DUID の種類がリンク レイヤー + 時間の場合、ベンダー番号はゼロとして返され、プライベート ID は空の文字列になります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="2c9e3-355">DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="2c9e3-356">IP リース データとクライアント レコード データを不揮発性メモリに保存する順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-357">サーバー テーブルに、またはサーバー テーブルからデータをコピーするときは、最初に DHCPv6 サーバーを停止または一時停止することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="2c9e3-358">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-358">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-359">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-360">**table_index** サーバーのクライアント テーブルへのインデックス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="2c9e3-361">**message_xid** クライアント サーバーのトランザクション ID</span><span class="sxs-lookup"><span data-stu-id="2c9e3-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="2c9e3-362">**client_address** クライアントにリースされた IPv6 アドレス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="2c9e3-363">**client_state** クライアントの DHCPv6 の状態 (例: バインド)</span><span class="sxs-lookup"><span data-stu-id="2c9e3-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="2c9e3-364">**IP_lease_time_accrued** リースで既に切れている有効期限 **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-365">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="2c9e3-366">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-366">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-367">**NX_SUCCESS** (0x00) サーバーが正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="2c9e3-368">**NX_DHCPV6_INVALID_DUID** (0xECC) 無効または矛盾する DUID データ</span><span class="sxs-lookup"><span data-stu-id="2c9e3-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="2c9e3-369">**NX_PTR_ERROR** (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="2c9e3-370">NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="2c9e3-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="2c9e3-371">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-371">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-372">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-372">Application code</span></span>

<span data-ttu-id="2c9e3-373">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="2c9e3-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="2c9e3-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="2c9e3-375">サーバー DHCPv6 インターフェイスのインターフェイス インデックスを設定します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="2c9e3-376">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="2c9e3-377">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-377">**Description**</span></span>

<span data-ttu-id="2c9e3-378">このサービスを使用すると、DHCPv6 サーバーによって DHCPv6 クライアント要求が処理されるネットワーク インターフェイスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="2c9e3-379">マルチホームがサポートされていない NetX Duo のバージョンでは、インターフェイスの値は既定で 0 になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="2c9e3-380">DHCPv6 インターフェイスでサーバー グローバル アドレスを取得するには、グローバル アドレス インデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="2c9e3-381">これは、リース アドレスと他の DHCPv6 データが DHCPv6 サーバーとのリンク上にあることを確認するるために、DHCPv6 のロジックによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="2c9e3-382">シングルホーム デバイス上のアプリケーションや、マルチホームのサポートがないアプリケーションでも、DHCPv6 サーバーが開始される前に、これを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="2c9e3-383">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-383">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-384">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-385">**iface_index** サーバーの DHCPv6 サーバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="2c9e3-386">**ga_address_index** サーバーの IP インスタンス アドレス テーブル内のサーバー グローバル アドレスのインデックス</span><span class="sxs-lookup"><span data-stu-id="2c9e3-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="2c9e3-387">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-387">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-388">**NX_SUCCESS** (0x00) サーバーが正常に開始されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="2c9e3-389">**NX_INVALID_INTERFACE** (0x4C) インターフェイスが存在しません</span><span class="sxs-lookup"><span data-stu-id="2c9e3-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="2c9e3-390">NX_NO_INTERFACE_ADDRESS (0x50) グローバル インデックスが、IP インスタンスの最大 IPv6 アドレス (NX_MAX_IPV6_ADDRESSES) を超えています</span><span class="sxs-lookup"><span data-stu-id="2c9e3-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="2c9e3-391">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-392">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-392">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-393">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-393">Application code</span></span>

<span data-ttu-id="2c9e3-394">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="2c9e3-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="2c9e3-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="2c9e3-396">DHCPv6 パケットのサーバー DUID を設定します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="2c9e3-397">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="2c9e3-398">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-398">**Description**</span></span>

<span data-ttu-id="2c9e3-399">このサービスを使用すると、サーバーの DUID が設定されます。ホスト アプリケーションによってサーバーが起動される前に、このサービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="2c9e3-400">リンク レイヤーとリンク レイヤー時間の DUID の種類の場合、ホスト アプリケーションでハードウェアの種類と MAC アドレスのデータを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="2c9e3-401">リンク レイヤー時間の DUID の場合、時刻ポインターは有効な時間を指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="2c9e3-402">2000 年 1 月 1 日からの秒数が、一般的なシード値です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="2c9e3-403">サーバーの DUID の種類がエンタープライズまたはベンダーによる割り当ての種類の場合、DUID はユーザーが構成可能なオプション NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID と NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID から作成され、時間と MAC アドレスの値は NULL に設定できます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="2c9e3-404">再起動の前後で、同じ DUID がクライアントへのメッセージで使用されように、サーバーの DUID パラメーターを不揮発性メモリに保存するのは、ホスト アプリケーションの責任です。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="2c9e3-405">これは、DHCPv6 プロトコルの要件です (RFC 3315)。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="2c9e3-406">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-406">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-407">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-408">**duid_type** DHCPv6 サーバーの DUID の種類</span><span class="sxs-lookup"><span data-stu-id="2c9e3-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="2c9e3-409">**hardware_type** ハードウェアの種類 (例: イーサネット)</span><span class="sxs-lookup"><span data-stu-id="2c9e3-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="2c9e3-410">**mac_address_msw** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-411">**mac_address_lsw** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-412">**time** DUID の時刻値</span><span class="sxs-lookup"><span data-stu-id="2c9e3-412">**time** Time value for DUID</span></span>

<span data-ttu-id="2c9e3-413">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-413">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-414">**NX_SUCCESS** (0x00) サーバーは正常に一時停止されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="2c9e3-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) 不明またはサポートされていない DUID の種類</span><span class="sxs-lookup"><span data-stu-id="2c9e3-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="2c9e3-416">**NX_INVALID_PARAMETERS** (0x4D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="2c9e3-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="2c9e3-417">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-418">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-418">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-419">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-419">Application code</span></span>

<span data-ttu-id="2c9e3-420">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="2c9e3-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="2c9e3-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="2c9e3-422">DHCPv6 サーバー インスタンスのオプション要求ハンドラーを設定します</span><span class="sxs-lookup"><span data-stu-id="2c9e3-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="2c9e3-423">**プロトタイプ**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="2c9e3-424">**説明**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-424">**Description**</span></span>

<span data-ttu-id="2c9e3-425">このサービスを使用すると、DHCPv6 サーバー拡張オプション要求ハンドラーが設定されます。</span><span class="sxs-lookup"><span data-stu-id="2c9e3-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="2c9e3-426">**入力パラメーター**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-426">**Input Parameters**</span></span>

- <span data-ttu-id="2c9e3-427">**dhcpv6_server_ptr** DHCPv6 サーバーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="2c9e3-428">**dhcpv6_option_request_handler_extended** 拡張オプション要求ハンドラーへのポインター</span><span class="sxs-lookup"><span data-stu-id="2c9e3-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="2c9e3-429">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-429">**Return Values**</span></span>

- <span data-ttu-id="2c9e3-430">**NX_SUCCESS** (0x00) サーバーが正常に再開されました</span><span class="sxs-lookup"><span data-stu-id="2c9e3-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="2c9e3-431">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="2c9e3-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="2c9e3-432">**使用可能な場所**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-432">**Allowed From**</span></span>

<span data-ttu-id="2c9e3-433">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="2c9e3-433">Application Code</span></span>

<span data-ttu-id="2c9e3-434">**例**</span><span class="sxs-lookup"><span data-stu-id="2c9e3-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```