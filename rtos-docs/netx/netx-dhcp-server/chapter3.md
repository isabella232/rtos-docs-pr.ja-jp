---
title: 第 3 章 - Azure RTOS NetX DHCP サーバー サービスの説明
description: この章では、Azure RTOS NetX DHCP サーバーのすべてのサービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811600"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="99ecc-103">第 3 章 - Azure RTOS NetX DHCP サーバー サービスの説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="99ecc-104">この章では、NetX DHCP サーバーのすべてのサービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="99ecc-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="99ecc-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="99ecc-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="99ecc-106">**nx_dhcp_server_create**: "*DHCP サーバー インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="99ecc-107">**nx_dhcp_set_interface_network_parameters**: "*指定されたインターフェイス用の重要なネットワーク パラメーターの DHCP サーバー オプションを設定する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="99ecc-108">**nx_dhcp_create_server_ip_address_list**: "*DHCP クライアント インターフェイスに割り当てる使用可能な IP アドレスのプールを作成する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="99ecc-109">**nx_dhcp_clear_client_record**: "*サーバー データベース内のクライアント レコードを削除する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="99ecc-110">**nx_dhcp_server_delete**: "*DHCP サーバー インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="99ecc-111">**nx_dhcp_server_start**: "*DHCP サーバーの処理を開始または再開する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="99ecc-112">**nx_dhcp_server_stop**: "*DHCP サーバーの処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="99ecc-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="99ecc-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="99ecc-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="99ecc-114">DHCP サーバー インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="99ecc-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-115">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="99ecc-116">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-116">Description</span></span>

<span data-ttu-id="99ecc-117">このサービスにより、以前に作成された IP インスタンスを使用して DHCP サーバー インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99ecc-118">アプリケーションでは、IP 作成サービス用に作成されたパケット プールに、UDP、IP、およびイーサネット ヘッダーを含まない最小 548 バイトのペイロードがあることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99ecc-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-119">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-119">Input Parameters</span></span>

- <span data-ttu-id="99ecc-120">**dhcp_ptr**: DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="99ecc-121">**ip_ptr**: DHCP サーバーの IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="99ecc-122">**stack_ptr**: DHCP サーバー スタックの場所を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="99ecc-123">**stack_size**: DHCP サーバー スタックのサイズ</span><span class="sxs-lookup"><span data-stu-id="99ecc-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="99ecc-124">**input_address_list**: サーバーの IP アドレスのリストへのポインター</span><span class="sxs-lookup"><span data-stu-id="99ecc-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="99ecc-125">**name_ptr**: DHCP サーバー名へのポインター</span><span class="sxs-lookup"><span data-stu-id="99ecc-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="99ecc-126">**packet_pool_ptr**: DHCP サーバーのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="99ecc-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-127">Return Values</span></span>

- <span data-ttu-id="99ecc-128">**NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="99ecc-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) パケット ペイロードが小さすぎるというエラー</span><span class="sxs-lookup"><span data-stu-id="99ecc-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="99ecc-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) サーバー オプション リストが空です</span><span class="sxs-lookup"><span data-stu-id="99ecc-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="99ecc-131">NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力</span><span class="sxs-lookup"><span data-stu-id="99ecc-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="99ecc-132">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="99ecc-133">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-134">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-134">Allowed From</span></span>

<span data-ttu-id="99ecc-135">Application</span><span class="sxs-lookup"><span data-stu-id="99ecc-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-136">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="99ecc-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="99ecc-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="99ecc-138">IP アドレス プールを作成します</span><span class="sxs-lookup"><span data-stu-id="99ecc-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-139">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="99ecc-140">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-140">Description</span></span>

<span data-ttu-id="99ecc-141">このサービスにより、指定された DHCP サーバーによって割り当てられる、使用可能な IP アドレスのネットワーク インターフェイス固有のプールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="99ecc-142">開始および終了 IP アドレスは、指定されたネットワーク インターフェイスと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="99ecc-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="99ecc-143">IP アドレス リストのサイズが十分でない場合 (ユーザーが構成可能な *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* パラメーターで設定されています)、実際に追加される IP アドレスの数は、アドレスの総数よりも少なくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99ecc-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-144">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-144">Input Parameters</span></span>

- <span data-ttu-id="99ecc-145">**dhcp_ptr** DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="99ecc-146">**iface_index**: ネットワーク インターフェイスに対応するインデックス</span><span class="sxs-lookup"><span data-stu-id="99ecc-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="99ecc-147">**start_ip_address**: 使用可能な最初の IP アドレス</span><span class="sxs-lookup"><span data-stu-id="99ecc-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="99ecc-148">**end_ip_address**: 使用可能な最後の IP アドレス</span><span class="sxs-lookup"><span data-stu-id="99ecc-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="99ecc-149">**addresses_added**: リストに追加された IP アドレスの数</span><span class="sxs-lookup"><span data-stu-id="99ecc-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-150">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-150">Return Values</span></span>

- <span data-ttu-id="99ecc-151">**NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="99ecc-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) インデックスがアドレスと一致しません</span><span class="sxs-lookup"><span data-stu-id="99ecc-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="99ecc-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) アドレス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="99ecc-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="99ecc-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) 非論理的な開始/終了アドレス</span><span class="sxs-lookup"><span data-stu-id="99ecc-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="99ecc-155">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-156">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-156">Allowed From</span></span>

<span data-ttu-id="99ecc-157">Application</span><span class="sxs-lookup"><span data-stu-id="99ecc-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-158">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="99ecc-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="99ecc-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="99ecc-160">サーバー データベースからクライアント レコードを削除します</span><span class="sxs-lookup"><span data-stu-id="99ecc-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-161">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="99ecc-162">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-162">Description</span></span>

<span data-ttu-id="99ecc-163">このサービスにより、サーバー データベースからクライアント レコードがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-164">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-164">Input Parameters</span></span>

- <span data-ttu-id="99ecc-165">**dhcp_ptr**: DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="99ecc-166">**dhcp_client_ptr**: 削除する DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="99ecc-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-167">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-167">Return Values</span></span>

- <span data-ttu-id="99ecc-168">**NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="99ecc-169">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="99ecc-170">NX_CALLER_ERROR: (0x11) サービスの呼び出し元がスレッドではありません</span><span class="sxs-lookup"><span data-stu-id="99ecc-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-171">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-171">Allowed From</span></span>

<span data-ttu-id="99ecc-172">Application</span><span class="sxs-lookup"><span data-stu-id="99ecc-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-173">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="99ecc-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="99ecc-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="99ecc-175">DHCP オプションのネットワーク パラメーターを設定します</span><span class="sxs-lookup"><span data-stu-id="99ecc-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-176">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="99ecc-177">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-177">Description</span></span>

<span data-ttu-id="99ecc-178">このサービスにより、指定されたインターフェイスのネットワーク クリティカルなパラメーターの既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="99ecc-179">DHCP サーバーによって、これらのオプションが DHCP クライアントへの OFFER および ACK 応答に含められます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="99ecc-180">DHCP サーバーが実行されているホストによってインターフェイス パラメーターが設定された場合、パラメーターの既定値は次のようになります: ルーターは DHCP サーバー自体のプライマリ インターフェイス ゲートウェイに設定され、DNS サーバー アドレスは DHCP サーバー自体で、サブネット マスクは DHCP サーバー インターフェイスで構成されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="99ecc-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-181">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-181">Input Parameters</span></span>

- <span data-ttu-id="99ecc-182">**dhcp_ptr**: DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="99ecc-183">**iface_index**: ネットワーク インターフェイスに対応するインデックス</span><span class="sxs-lookup"><span data-stu-id="99ecc-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="99ecc-184">**subnet_mask**: クライアント ネットワークのサブネット マスク</span><span class="sxs-lookup"><span data-stu-id="99ecc-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="99ecc-185">**default_gateway_address**: クライアントのルーター IP アドレス</span><span class="sxs-lookup"><span data-stu-id="99ecc-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="99ecc-186">**dns_server_address**: クライアントのネットワーク用の DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="99ecc-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-187">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-187">Return Values</span></span>

- <span data-ttu-id="99ecc-188">**NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="99ecc-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) インデックスがアドレスと一致しません</span><span class="sxs-lookup"><span data-stu-id="99ecc-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="99ecc-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) ネットワーク パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="99ecc-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="99ecc-191">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-192">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-192">Allowed From</span></span>

<span data-ttu-id="99ecc-193">Application</span><span class="sxs-lookup"><span data-stu-id="99ecc-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-194">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="99ecc-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="99ecc-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="99ecc-196">DHCP サーバー インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="99ecc-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-197">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="99ecc-198">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-198">Description</span></span>

<span data-ttu-id="99ecc-199">このサービスにより、以前に作成された DHCP サーバー インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-200">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-200">Input Parameters</span></span>

- <span data-ttu-id="99ecc-201">**dhcp_ptr**: DHCP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-202">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-202">Return Values</span></span>

- <span data-ttu-id="99ecc-203">**NX_SUCCESS**: (0x00) DHCP サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="99ecc-204">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="99ecc-205">NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力</span><span class="sxs-lookup"><span data-stu-id="99ecc-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="99ecc-206">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-207">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-207">Allowed From</span></span>

<span data-ttu-id="99ecc-208">Threads</span><span class="sxs-lookup"><span data-stu-id="99ecc-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-209">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="99ecc-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="99ecc-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="99ecc-211">DHCP サーバー処理を開始します</span><span class="sxs-lookup"><span data-stu-id="99ecc-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-212">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="99ecc-213">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-213">Description</span></span>

<span data-ttu-id="99ecc-214">このサービスにより、DHCP サーバーの処理が開始されます。これには、サーバー UDP ソケットの作成、DHCP ポートのバインド、およびクライアント DHCP 要求の受信の待機が含まれます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-215">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-215">Input Parameters</span></span>

- <span data-ttu-id="99ecc-216">**dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-217">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-217">Return Values</span></span>

- <span data-ttu-id="99ecc-218">**NX_SUCCESS**: (0x00) サーバーが正常に起動しました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="99ecc-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="99ecc-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="99ecc-220">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="99ecc-221">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="99ecc-222">NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力</span><span class="sxs-lookup"><span data-stu-id="99ecc-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-223">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-223">Allowed From</span></span>

<span data-ttu-id="99ecc-224">Threads</span><span class="sxs-lookup"><span data-stu-id="99ecc-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-225">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="99ecc-226">参照</span><span class="sxs-lookup"><span data-stu-id="99ecc-226">See Also</span></span>

<span data-ttu-id="99ecc-227">nx_dhcp_create、nx_dhcp_delete、nx_dhcp_release、nx_dhcp_state_change_notify、nx_dhcp_stop、nx_dhcp_user_option_retrieve、nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="99ecc-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="99ecc-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="99ecc-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="99ecc-229">DHCP サーバー処理を停止します</span><span class="sxs-lookup"><span data-stu-id="99ecc-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="99ecc-230">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="99ecc-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="99ecc-231">説明</span><span class="sxs-lookup"><span data-stu-id="99ecc-231">Description</span></span>

<span data-ttu-id="99ecc-232">このサービスにより、DHCP クライアント要求の受信を含む DHCP サーバーの処理が停止されます。</span><span class="sxs-lookup"><span data-stu-id="99ecc-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="99ecc-233">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="99ecc-233">Input Parameters</span></span>

- <span data-ttu-id="99ecc-234">**dhcp_ptr**: DHCP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99ecc-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="99ecc-235">戻り値</span><span class="sxs-lookup"><span data-stu-id="99ecc-235">Return Values</span></span>

- <span data-ttu-id="99ecc-236">**NX_SUCCESS**: (0x00) DHCP が正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="99ecc-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="99ecc-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="99ecc-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="99ecc-238">NX_PTR_ERROR: (0x16) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="99ecc-239">NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="99ecc-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="99ecc-240">NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力。</span><span class="sxs-lookup"><span data-stu-id="99ecc-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="99ecc-241">許可元</span><span class="sxs-lookup"><span data-stu-id="99ecc-241">Allowed From</span></span>

<span data-ttu-id="99ecc-242">Threads</span><span class="sxs-lookup"><span data-stu-id="99ecc-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="99ecc-243">例</span><span class="sxs-lookup"><span data-stu-id="99ecc-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
