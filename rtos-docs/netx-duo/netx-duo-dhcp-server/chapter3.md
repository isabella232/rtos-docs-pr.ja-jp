---
title: 第 3 章 - Azure RTOS NetX Duo DHCP サーバーのサービスの説明
description: この章では、すべての NetX Duo DHCP サーバーのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810922"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a><span data-ttu-id="f16f5-103">第 3 章 - Azure RTOS NetX Duo DHCP サーバーのサービスの説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Server Services</span></span>

<span data-ttu-id="f16f5-104">この章では、すべての NetX Duo DHCP サーバーのサービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="f16f5-104">This chapter contains a description of all NetX Duo DHCP Server services (listed below) in alphabetic order.</span></span>

> [!NOTE]
> <span data-ttu-id="f16f5-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="f16f5-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_dhcp_server-create"></a><span data-ttu-id="f16f5-106">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="f16f5-106">nx_dhcp_server create</span></span>

<span data-ttu-id="f16f5-107">DHCP サーバー インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="f16f5-107">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-108">Prototype</span></span>

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="f16f5-109">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-109">Description</span></span>

<span data-ttu-id="f16f5-110">このサービスを使用すると、以前に作成された IP インスタンスを使用して DHCP サーバー インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-110">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f16f5-111">IP 作成サービス用に作成されたパケット プールに、UDP、IP、イーサネットのヘッダーを除いて、少なくとも 548 バイトのペイロードがあることを、アプリケーションで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f16f5-111">The application must make sure the packet pool created for the IP create service has a minimum 548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-112">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-112">Input Parameters</span></span>

- <span data-ttu-id="f16f5-113">**dhcp_ptr** DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-113">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="f16f5-114">**ip_ptr** DHCP サーバーの IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-114">**ip_ptr** Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="f16f5-115">**stack_ptr** DHCP サーバー スタックの場所を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-115">**stack_ptr** Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="f16f5-116">**stack_size** DHCP サーバー スタックのサイズ input_address_list サーバーの IP アドレスのリストへのポインター</span><span class="sxs-lookup"><span data-stu-id="f16f5-116">**stack_size Size of DHCP Server stack** input_address_list Pointer to Server’s list of IP addresses</span></span>
- <span data-ttu-id="f16f5-117">**name_ptr** DHCP サーバー名へのポインター packet_pool_ptr DHCP サーバーのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="f16f5-117">**name_ptr Pointer to DHCP Server name** packet_pool_ptr Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-118">Return Values</span></span>

- <span data-ttu-id="f16f5-119">**NX_SUCCESS** (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-119">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="f16f5-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) パケット ペイロードが小さすぎるというエラー</span><span class="sxs-lookup"><span data-stu-id="f16f5-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="f16f5-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) サーバー オプション リストが空です</span><span class="sxs-lookup"><span data-stu-id="f16f5-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Server option list is empty</span></span>
- <span data-ttu-id="f16f5-122">NX_DHCP_PARAMETER_ERROR (0x92) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="f16f5-122">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="f16f5-123">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-123">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="f16f5-124">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-124">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-125">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-125">Allowed From</span></span>

<span data-ttu-id="f16f5-126">Application</span><span class="sxs-lookup"><span data-stu-id="f16f5-126">Application</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-127">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-127">Example</span></span>

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="f16f5-128">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="f16f5-128">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="f16f5-129">IP アドレス プールを作成します</span><span class="sxs-lookup"><span data-stu-id="f16f5-129">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-130">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-130">Prototype</span></span>

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="f16f5-131">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-131">Description</span></span>

<span data-ttu-id="f16f5-132">このサービスを使用すると、指定した DHCP サーバーによって割り当てられる、使用可能な IP アドレスのネットワーク インターフェイス固有のプールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-132">This service creates a network interface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="f16f5-133">開始および終了 IP アドレスは、指定したネットワーク インターフェイスと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f16f5-133">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="f16f5-134">IP アドレス リストのサイズが十分でない場合 (ユーザーが構成可能な *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* パラメーターで設定されています)、実際に追加される IP アドレスの数は、アドレスの総数よりも少なくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f16f5-134">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-135">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-135">Input Parameters</span></span>

- <span data-ttu-id="f16f5-136">**dhcp_ptr** DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-136">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="f16f5-137">**iface_index** ネットワーク インターフェイスに対応するインデックス</span><span class="sxs-lookup"><span data-stu-id="f16f5-137">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="f16f5-138">**start_ip_address** 使用可能な最初の IP アドレス</span><span class="sxs-lookup"><span data-stu-id="f16f5-138">**start_ip_address** First available IP address</span></span>
- <span data-ttu-id="f16f5-139">**end_ip_address** 使用可能な最後の IP アドレス</span><span class="sxs-lookup"><span data-stu-id="f16f5-139">**end_ip_address** Last of the available IP address</span></span>
- <span data-ttu-id="f16f5-140">**addresses_added** リストに追加された IP アドレスの数</span><span class="sxs-lookup"><span data-stu-id="f16f5-140">**addresses_added** Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-141">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-141">Return Values</span></span>

- <span data-ttu-id="f16f5-142">**NX_SUCCESS** (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-142">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="f16f5-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) インデックスがアドレスと一致しません</span><span class="sxs-lookup"><span data-stu-id="f16f5-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="f16f5-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) アドレス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="f16f5-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Invalid address input</span></span>
- <span data-ttu-id="f16f5-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) 非論理的な開始および終了アドレス</span><span class="sxs-lookup"><span data-stu-id="f16f5-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="f16f5-146">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-146">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-147">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-147">Allowed From</span></span>

<span data-ttu-id="f16f5-148">Application</span><span class="sxs-lookup"><span data-stu-id="f16f5-148">Application</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-149">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-149">Example</span></span>

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="f16f5-150">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="f16f5-150">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="f16f5-151">サーバー データベースからクライアント レコードを削除します</span><span class="sxs-lookup"><span data-stu-id="f16f5-151">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-152">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-152">Prototype</span></span>

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="f16f5-153">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-153">Description</span></span>

<span data-ttu-id="f16f5-154">このサービスを使用すると、サーバー データベースからクライアント レコードがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-154">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-155">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-155">Input Parameters</span></span>

- <span data-ttu-id="f16f5-156">**dhcp_ptr** DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-156">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="f16f5-157">**dhcp_client_ptr** 削除する DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="f16f5-157">**dhcp_client_ptr Pointer to DHCP Client to remove**</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-158">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-158">Return Values</span></span>

- <span data-ttu-id="f16f5-159">**NX_SUCCESS** (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-159">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="f16f5-160">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-160">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="f16f5-161">NX_CALLER_ERROR (0x11) サービスの呼び出し元がスレッドではありません</span><span class="sxs-lookup"><span data-stu-id="f16f5-161">NX_CALLER_ERROR (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-162">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-162">Allowed From</span></span>

<span data-ttu-id="f16f5-163">Application</span><span class="sxs-lookup"><span data-stu-id="f16f5-163">Application</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-164">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-164">Example</span></span>

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="f16f5-165">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="f16f5-165">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="f16f5-166">DHCP オプションのネットワーク パラメーターを設定します</span><span class="sxs-lookup"><span data-stu-id="f16f5-166">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-167">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-167">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="f16f5-168">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-168">Description</span></span>

<span data-ttu-id="f16f5-169">このサービスを使用すると、指定したインターフェイスのネットワーク クリティカルなパラメーターに既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-169">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="f16f5-170">DHCP サーバーによって、これらのオプションが DHCP クライアントへの OFFER および ACK 応答に含められます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-170">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="f16f5-171">DHCP サーバーが実行されているホストによってインターフェイス パラメーターが設定された場合、パラメーターの既定値は次のようになります: ルーターは DHCP サーバー自体のプライマリ インターフェイス ゲートウェイに設定され、DNS サーバー アドレスは DHCP サーバー自体で、サブネット マスクは DHCP サーバー インターフェイスで構成されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="f16f5-171">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-172">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-172">Input Parameters</span></span>

- <span data-ttu-id="f16f5-173">**dhcp_ptr** DHCP サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-173">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="f16f5-174">**iface_index** ネットワーク インターフェイスに対応するインデックス</span><span class="sxs-lookup"><span data-stu-id="f16f5-174">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="f16f5-175">**subnet_mask** クライアント ネットワークのサブネット マスク</span><span class="sxs-lookup"><span data-stu-id="f16f5-175">**subnet_mask** Subnet mask for Client network</span></span>
- <span data-ttu-id="f16f5-176">**default_gateway_address** クライアントのルーター IP アドレス</span><span class="sxs-lookup"><span data-stu-id="f16f5-176">**default_gateway_address** Client’s router IP address</span></span>
- <span data-ttu-id="f16f5-177">**dns_server_address** クライアントのネットワーク用の DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="f16f5-177">**dns_server_address** DNS server for Client’s network</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-178">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-178">Return Values</span></span>

- <span data-ttu-id="f16f5-179">**NX_SUCCESS** (0x00) DHCP サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-179">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="f16f5-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) インデックスがアドレスと一致しません</span><span class="sxs-lookup"><span data-stu-id="f16f5-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="f16f5-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) ネットワーク パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="f16f5-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="f16f5-182">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-182">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-183">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-183">Allowed From</span></span>

<span data-ttu-id="f16f5-184">Application</span><span class="sxs-lookup"><span data-stu-id="f16f5-184">Application</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-185">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-185">Example</span></span>

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="f16f5-186">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="f16f5-186">nx_dhcp_server_delete</span></span>

<span data-ttu-id="f16f5-187">DHCP サーバー インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="f16f5-187">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-188">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-188">Prototype</span></span>

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="f16f5-189">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-189">Description</span></span>

<span data-ttu-id="f16f5-190">このサービスを使用すると、以前に作成した DHCP サーバー インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-190">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-191">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-191">Input Parameters</span></span>

- <span data-ttu-id="f16f5-192">**dhcp_ptr** DHCP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-192">**dhcp_ptr** Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-193">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-193">Return Values</span></span>

- <span data-ttu-id="f16f5-194">**NX_SUCCESS** (0x00) DHCP サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-194">**NX_SUCCESS** (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="f16f5-195">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-195">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="f16f5-196">NX_DHCP_PARAMETER_ERROR (0x92) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="f16f5-196">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="f16f5-197">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-197">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-198">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-198">Allowed From</span></span>

<span data-ttu-id="f16f5-199">Threads</span><span class="sxs-lookup"><span data-stu-id="f16f5-199">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-200">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-200">Example</span></span>

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="f16f5-201">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="f16f5-201">nx_dhcp_server_start</span></span>

<span data-ttu-id="f16f5-202">DHCP サーバーの処理を開始します</span><span class="sxs-lookup"><span data-stu-id="f16f5-202">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-203">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-203">Prototype</span></span>

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="f16f5-204">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-204">Description</span></span>

<span data-ttu-id="f16f5-205">このサービスを使用すると、DHCP サーバーの処理が開始されます。これには、サーバー UDP ソケットの作成、DHCP ポートのバインド、クライアント DHCP 要求の受信の待機が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-205">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-206">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-206">Input Parameters</span></span>

- <span data-ttu-id="f16f5-207">**dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-207">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-208">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-208">Return Values</span></span>

- <span data-ttu-id="f16f5-209">**NX_SUCCESS** (0x00) サーバーが正常に起動しました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-209">**NX_SUCCESS** (0x00) Successful Server start.</span></span>
- <span data-ttu-id="f16f5-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="f16f5-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="f16f5-211">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-211">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="f16f5-212">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-212">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="f16f5-213">NX_DHCP_PARAMETER_ERROR (0x92) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="f16f5-213">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-214">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-214">Allowed From</span></span>

<span data-ttu-id="f16f5-215">Threads</span><span class="sxs-lookup"><span data-stu-id="f16f5-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-216">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-216">Example</span></span>

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="f16f5-217">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="f16f5-217">nx_dhcp_server_stop</span></span>

<span data-ttu-id="f16f5-218">DHCP サーバーの処理を停止します</span><span class="sxs-lookup"><span data-stu-id="f16f5-218">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="f16f5-219">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f16f5-219">Prototype</span></span>

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="f16f5-220">説明</span><span class="sxs-lookup"><span data-stu-id="f16f5-220">Description</span></span>

<span data-ttu-id="f16f5-221">このサービスを使用すると、DHCP クライアント要求の受信など、DHCP サーバーの処理が停止されます。</span><span class="sxs-lookup"><span data-stu-id="f16f5-221">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f16f5-222">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16f5-222">Input Parameters</span></span>

- <span data-ttu-id="f16f5-223">**dhcp_ptr** DHCP サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16f5-223">**dhcp_ptr** Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f16f5-224">戻り値</span><span class="sxs-lookup"><span data-stu-id="f16f5-224">Return Values</span></span>

- <span data-ttu-id="f16f5-225">**NX_SUCCESS** (0x00) DHCP が正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="f16f5-225">**NX_SUCCESS** (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="f16f5-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="f16f5-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="f16f5-227">NX_PTR_ERROR (0x16) ポインターの入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-227">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="f16f5-228">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="f16f5-228">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="f16f5-229">NX_DHCP_PARAMETER_ERROR (0x92) 無効な非ポインター入力です</span><span class="sxs-lookup"><span data-stu-id="f16f5-229">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f16f5-230">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="f16f5-230">Allowed From</span></span>

<span data-ttu-id="f16f5-231">Threads</span><span class="sxs-lookup"><span data-stu-id="f16f5-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f16f5-232">例</span><span class="sxs-lookup"><span data-stu-id="f16f5-232">Example</span></span>

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
