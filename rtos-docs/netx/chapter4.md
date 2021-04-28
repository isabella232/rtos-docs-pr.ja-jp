---
title: 第 4 章 - Azure RTOS NetX サービスの説明
description: この章は、すべての Azure RTOS NetX サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810457"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="ff631-103">第 4 章 - Azure RTOS NetX サービスの説明</span><span class="sxs-lookup"><span data-stu-id="ff631-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="ff631-104">この章は、すべての Azure RTOS NetX サービスの説明をアルファベット順にまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="ff631-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="ff631-105">サービス名は、類似するすべてのサービスがグループ化されるように命名されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="ff631-106">たとえば、すべての ARP サービスは、この章の最初にあります。</span><span class="sxs-lookup"><span data-stu-id="ff631-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="ff631-107">*BSD-Compatible SOCKET API は、高パフォーマンスの NetX API を最大限に活用できないレガシ アプリケーション コードで使用できます。BSD-Compatible Socket API の詳細については、付録 D を参照してください。*</span><span class="sxs-lookup"><span data-stu-id="ff631-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="ff631-108">各説明の「戻り値」セクションにある **太字** の値は、API エラー チェックを無効にするために使用される NX_DISABLE_ERROR_CHECKING オプションの影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="ff631-109">「許可元」セクションには、各 NetX サービスを呼び出すことのできる呼び出し元が説明されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="ff631-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="ff631-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="ff631-111">ARP キャッシュ内のすべての動的エントリを無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-112">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-113">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-113">Description</span></span>

<span data-ttu-id="ff631-114">このサービスを使用すると、現在 ARP キャッシュにあるすべての動的 ARP エントリが無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-115">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-115">Parameters</span></span>

- <span data-ttu-id="ff631-116">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-117">Return Values</span></span>

- <span data-ttu-id="ff631-118">**NX_SUCCESS** (0x00) ARP キャッシュの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="ff631-119">**NX_NOT_ENABLED** (0x14) ARP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="ff631-120">**NX_PTR_ERROR** (0x07) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-121">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-122">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-122">Allowed From</span></span>

<span data-ttu-id="ff631-123">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-124">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-124">Preemption Possible</span></span>

<span data-ttu-id="ff631-125">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-125">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-126">例</span><span class="sxs-lookup"><span data-stu-id="ff631-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-127">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-127">See Also</span></span>

- <span data-ttu-id="ff631-128">nx_arp_dynamic_entry_set、nx_arp_enable、nx_arp_gratuitous_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="ff631-129">nx_arp_hardware_address_find、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-130">nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-131">nx_arp_static_entry_create、nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="ff631-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="ff631-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="ff631-133">動的 ARP エントリを設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-134">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="ff631-135">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-135">Description</span></span>

<span data-ttu-id="ff631-136">このサービスを使用すると、ARP キャッシュから動的エントリが割り当てられ、指定した IP が物理アドレス マッピングに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="ff631-137">物理アドレスがゼロに指定されている場合は、その物理アドレスを解決するために、実際の ARP 要求がネットワークに送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="ff631-138">別の注意すべき点として、ARP エージングがアクティブである場合や、ARP キャッシュが使い果たされていて、これが最も長く使用されていない ARP エントリである場合は、このエントリは削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-139">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-139">Parameters</span></span>

- <span data-ttu-id="ff631-140">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-141">**ip_address** マップする IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="ff631-142">**physical_msw** 物理アドレスの上位 16 ビット (47-32)。</span><span class="sxs-lookup"><span data-stu-id="ff631-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="ff631-143">**physical_lsw** 物理アドレスの下位 32 ビット (31-0)。</span><span class="sxs-lookup"><span data-stu-id="ff631-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-144">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-144">Return Values</span></span>

- <span data-ttu-id="ff631-145">**NX_SUCCESS** (0x00) ARP の動的エントリの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="ff631-146">**NX_NO_MORE_ENTRIES** (0x17) ARP キャッシュで使用できる ARP エントリがこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="ff631-147">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-148">**NX_PTR_ERROR** (0x07) IP インスタンス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="ff631-149">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-150">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-151">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-151">Allowed From</span></span>

<span data-ttu-id="ff631-152">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-153">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-153">Preemption Possible</span></span>

<span data-ttu-id="ff631-154">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-154">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-155">例</span><span class="sxs-lookup"><span data-stu-id="ff631-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-156">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-156">See Also</span></span>

- <span data-ttu-id="ff631-157">nx_arp_dynamic_entries_invalidate、nx_arp_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="ff631-158">nx_arp_gratuitous_send、nx_arp_hardware_address_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="ff631-159">nx_arp_info_get、nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-160">nx_arp_static_entry_create、nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="ff631-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-161">nx_arp_enable</span></span>

<span data-ttu-id="ff631-162">アドレス解決プロトコル (ARP) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="ff631-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-163">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="ff631-164">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-164">Description</span></span>

<span data-ttu-id="ff631-165">このサービスを使用すると、特定の IP インスタンスの NetX の ARP コンポーネントが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="ff631-166">ARP の初期化には、ARP メッセージの送受信に必要な ARP キャッシュやさまざまな ARP 処理ルーチンの設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff631-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-167">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-167">Parameters</span></span>

- <span data-ttu-id="ff631-168">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-169">**arp_cache_memory** ARP キャッシュを配置するメモリ領域を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="ff631-170">**arp_cache_size** 各 ARP エントリは 52 バイトであるため、ARP の合計数は 52 で割ることのできる数になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-171">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-171">Return Values</span></span>

- <span data-ttu-id="ff631-172">**NX_SUCCESS** (0x00) ARP の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="ff631-173">**NX_PTR_ERROR** (0x07) IP またはキャッシュ メモリ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="ff631-174">**NX_SIZE_ERROR** (0x09) ユーザーが指定した ARP キャッシュ メモリが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="ff631-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="ff631-175">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-176">**NX_ALREADY_ENABLED** (0x15) このコンポーネントは既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ff631-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-177">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-177">Allowed From</span></span>

<span data-ttu-id="ff631-178">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-179">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-179">Preemption Possible</span></span>

<span data-ttu-id="ff631-180">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-180">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-181">例</span><span class="sxs-lookup"><span data-stu-id="ff631-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-182">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-182">See Also</span></span>

- <span data-ttu-id="ff631-183">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-184">nx_arp_gratuitous_send、nx_arp_hardware_address_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="ff631-185">nx_arp_info_get、nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-186">nx_arp_static_entry_create、nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="ff631-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="ff631-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="ff631-188">無償 ARP 要求を送信します</span><span class="sxs-lookup"><span data-stu-id="ff631-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-189">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-190">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-190">Description</span></span>

<span data-ttu-id="ff631-191">このサービスを使用すると、インターフェイスの IP アドレスが有効である限り、すべての物理インターフェイスを経由して、無償 ARP 要求が送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="ff631-192">その後、ARP 応答を受信した場合は、提供された応答ハンドラーが呼び出されて、無償 ARP への応答が処理されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-193">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-193">Parameters</span></span>

- <span data-ttu-id="ff631-194">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-195">**response_handler** 応答処理関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="ff631-196">NX_NULL が指定されている場合、応答は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-197">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-197">Return Values</span></span>

- <span data-ttu-id="ff631-198">**NX_SUCCESS** (0x00) 無償 ARP の送信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="ff631-199">**NX_NO_PACKET** (0x01) 使用可能なパケットがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="ff631-200">**NX_NOT_ENABLED** (0x14) ARP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="ff631-201">**NX_IP_ADDRESS_ERROR** (0x21) 現在の IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="ff631-202">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-203">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-204">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-204">Allowed From</span></span>

<span data-ttu-id="ff631-205">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-206">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-206">Preemption Possible</span></span>

<span data-ttu-id="ff631-207">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-207">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-208">例</span><span class="sxs-lookup"><span data-stu-id="ff631-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-209">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-209">See Also</span></span>

- <span data-ttu-id="ff631-210">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-211">nx_arp_enable、nx_arp_hardware_address_find、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-212">nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-213">nx_arp_static_entry_create、nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="ff631-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="ff631-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="ff631-215">IP アドレスに関連付けられている物理ハードウェア アドレスを特定します</span><span class="sxs-lookup"><span data-stu-id="ff631-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-216">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="ff631-217">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-217">Description</span></span>

<span data-ttu-id="ff631-218">このサービスを使用すると、指定した IP アドレスに関連付けられている ARP キャッシュ内の物理ハードウェア アドレスの検索が試みられます。</span><span class="sxs-lookup"><span data-stu-id="ff631-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-219">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-219">Parameters</span></span>

- <span data-ttu-id="ff631-220">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-221">**ip_address** 検索する IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="ff631-222">**physical_msw** 物理アドレスの上位 16 ビット (47-32) を返すための変数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="ff631-223">**physical_lsw** 物理アドレスの下位 32 ビット (31-0) を返すための変数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-224">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-224">Return Values</span></span>

- <span data-ttu-id="ff631-225">**NX_SUCCESS** (0x00) ARP ハードウェア アドレスの検索に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="ff631-226">**NX_ENTRY_NOT_FOUND** (0x16) マッピングが ARP キャッシュに見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="ff631-227">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-228">**NX_PTR_ERROR** (0x07) IP またはメモリ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="ff631-229">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-230">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-231">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-231">Allowed From</span></span>

<span data-ttu-id="ff631-232">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-233">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-233">Preemption Possible</span></span>

<span data-ttu-id="ff631-234">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-234">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-235">例</span><span class="sxs-lookup"><span data-stu-id="ff631-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-236">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-236">See Also</span></span>

- <span data-ttu-id="ff631-237">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-238">nx_arp_enable、nx_arp_gratuitous_send、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-239">nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-240">nx_arp_static_entry_create、nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="ff631-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-241">nx_arp_info_get</span></span>

<span data-ttu-id="ff631-242">ARP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-243">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="ff631-244">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-244">Description</span></span>

<span data-ttu-id="ff631-245">このサービスを使用すると、関連付けられている IP インスタンスの ARP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="ff631-246">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-247">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-247">Parameters</span></span>

- <span data-ttu-id="ff631-248">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-249">**arp_requests_sent** この IP インスタンスから送信された ARP 要求の合計の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="ff631-250">**arp_requests_received** ネットワークから受信した ARP 要求の合計の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="ff631-251">**arp_responses_sent** この IP インスタンスから送信された ARP 要求の合計の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="ff631-252">**arp_responses_received** ネットワークから受信した ARP 応答の合計の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="ff631-253">**arp_dynamic_entries** 現在の動的 ARP エントリ数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="ff631-254">**arp_static_entries** 現在の静的 ARP エントリ数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="ff631-255">**arp_aged_entries** 期限切れで無効になった ARP エントリの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="ff631-256">**arp_invalid_messages** 受信した無効な ARP メッセージの合計の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-257">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-257">Return Values</span></span>

- <span data-ttu-id="ff631-258">**NX_SUCCESS** (0x00) ARP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="ff631-259">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-260">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-261">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-262">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-262">Allowed From</span></span>

<span data-ttu-id="ff631-263">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-264">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-264">Preemption Possible</span></span>

<span data-ttu-id="ff631-265">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-265">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-266">例</span><span class="sxs-lookup"><span data-stu-id="ff631-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-267">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-267">See Also</span></span>

- <span data-ttu-id="ff631-268">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-269">nx_arp_enable、nx_arp_gratuitous_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="ff631-270">nx_arp_hardware_address_find、nx_arp_ip_address_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="ff631-271">nx_arp_static_entries_delete、nx_arp_static_entry_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="ff631-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="ff631-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="ff631-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="ff631-274">物理アドレスに関連付けられている IP アドレスを特定します</span><span class="sxs-lookup"><span data-stu-id="ff631-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-275">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="ff631-276">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-276">Description</span></span>

<span data-ttu-id="ff631-277">このサービスを使用すると、指定した物理アドレスに関連付けられている ARP キャッシュ内の IP アドレスの検索が試みられます。</span><span class="sxs-lookup"><span data-stu-id="ff631-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-278">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-278">Parameters</span></span>

- <span data-ttu-id="ff631-279">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-280">**ip_address** マップされた IP アドレスが見つかった場合は、それを返すためのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="ff631-281">**physical_msw** 検索対象の物理アドレスの上位 16 ビット (47-32)。</span><span class="sxs-lookup"><span data-stu-id="ff631-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="ff631-282">**physical_lsw** 検索対象の物理アドレスの下位 32 ビット (31-0)。</span><span class="sxs-lookup"><span data-stu-id="ff631-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-283">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-283">Return Values</span></span>

- <span data-ttu-id="ff631-284">**NX_SUCCESS** (0x00) ARP IP アドレスの検索に成功しました</span><span class="sxs-lookup"><span data-stu-id="ff631-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="ff631-285">**NX_ENTRY_NOT_FOUND** (0x16) マッピングが ARP キャッシュに見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="ff631-286">**NX_PTR_ERROR** (0x07) IP またはメモリ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="ff631-287">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-288">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-289">**NX_INVALID_PARAMETERS** (0x4D) physical_msw と physical_lsw がどちらも 0 です。</span><span class="sxs-lookup"><span data-stu-id="ff631-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-290">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-290">Allowed From</span></span>

<span data-ttu-id="ff631-291">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-292">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-292">Preemption Possible</span></span>

<span data-ttu-id="ff631-293">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-293">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-294">例</span><span class="sxs-lookup"><span data-stu-id="ff631-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-295">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-295">See Also</span></span>

- <span data-ttu-id="ff631-296">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-297">nx_arp_enable、nx_arp_gratuitous_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="ff631-298">nx_arp_hardware_address_find、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-299">nx_arp_static_entries_delete、nx_arp_static_entry_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="ff631-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="ff631-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="ff631-302">すべての静的 ARP エントリを削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-303">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-304">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-304">Description</span></span>

<span data-ttu-id="ff631-305">このサービスを使用すると、ARP キャッシュ内のすべての静的エントリが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-306">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-306">Parameters</span></span>

- <span data-ttu-id="ff631-307">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-308">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-308">Return Values</span></span>

- <span data-ttu-id="ff631-309">**NX_SUCCESS** (0x00) 静的エントリが削除されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="ff631-310">**NX_PTR_ERROR** (0x07) ip_ptr ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="ff631-311">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-312">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-313">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-313">Allowed From</span></span>

<span data-ttu-id="ff631-314">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-315">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-315">Preemption Possible</span></span>

<span data-ttu-id="ff631-316">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-316">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-317">例</span><span class="sxs-lookup"><span data-stu-id="ff631-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-318">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-318">See Also</span></span>

- <span data-ttu-id="ff631-319">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-320">nx_arp_enable、nx_arp_gratuitous_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="ff631-321">nx_arp_hardware_address_find、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-322">nx_arp_ip_address_find、nx_arp_static_entry_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="ff631-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="ff631-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="ff631-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="ff631-325">ARP キャッシュにハードウェア マッピングへの静的 IP を作成します</span><span class="sxs-lookup"><span data-stu-id="ff631-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-326">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="ff631-327">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-327">Description</span></span>

<span data-ttu-id="ff631-328">このサービスを使用すると、指定した IP インスタンスの ARP キャッシュに静的 IP から物理アドレスへのマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="ff631-329">静的 ARP エントリは、ARP の定期的な更新の対象にはなりません。</span><span class="sxs-lookup"><span data-stu-id="ff631-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-330">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-330">Parameters</span></span>

- <span data-ttu-id="ff631-331">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-332">**ip_address** マップする IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="ff631-333">**physical_msw** マップする物理アドレスの上位 16 ビット (47-32)。</span><span class="sxs-lookup"><span data-stu-id="ff631-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="ff631-334">**physical_lsw** マップする物理アドレスの下位 32 ビット (31-0)。</span><span class="sxs-lookup"><span data-stu-id="ff631-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-335">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-335">Return Values</span></span>

- <span data-ttu-id="ff631-336">**NX_SUCCESS** (0x00) 静的 ARP エントリの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="ff631-337">**NX_NO_MORE_ENTRIES** (0x17) ARP キャッシュで使用できる ARP エントリがこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="ff631-338">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-339">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-340">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-341">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-342">**NX_INVALID_PARAMETERS** (0x4D) physical_msw と physical_lsw がどちらも 0 です。</span><span class="sxs-lookup"><span data-stu-id="ff631-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-343">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-343">Allowed From</span></span>

<span data-ttu-id="ff631-344">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-345">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-345">Preemption Possible</span></span>

<span data-ttu-id="ff631-346">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-346">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-347">例</span><span class="sxs-lookup"><span data-stu-id="ff631-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-348">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-348">See Also</span></span>

- <span data-ttu-id="ff631-349">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-350">nx_arp_enable、nx_arp_gratuitous_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="ff631-351">nx_arp_hardware_address_find、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-352">nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="ff631-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="ff631-355">ARP キャッシュのハードウェア マッピングへの静的 IP を削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-356">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="ff631-357">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-357">Description</span></span>

<span data-ttu-id="ff631-358">このサービスを使用すると、指定した IP インスタンスの ARP キャッシュに以前に作成された静的 IP から物理アドレスへのマッピングが検索されて削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-359">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-359">Parameters</span></span>

- <span data-ttu-id="ff631-360">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-361">**ip_address** 静的にマップされた IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="ff631-362">**physical_msw** 静的にマップされた物理アドレスの上位 16 ビット (47 - 32)。</span><span class="sxs-lookup"><span data-stu-id="ff631-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="ff631-363">**physical_msw** 静的にマップされた物理アドレスの下位 32 ビット (31 - 0)。</span><span class="sxs-lookup"><span data-stu-id="ff631-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-364">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-364">Return Values</span></span>

- <span data-ttu-id="ff631-365">**NX_SUCCESS** (0x00) 静的 ARP エントリの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="ff631-366">**NX_ENTRY_NOT_FOUND** (0x16) 静的 ARP エントリが ARP キャッシュに見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="ff631-367">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-368">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-369">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-370">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-371">**NX_INVALID_PARAMETERS** (0x4D) physical_msw と physical_lsw がどちらも 0 です。</span><span class="sxs-lookup"><span data-stu-id="ff631-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-372">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-372">Allowed From</span></span>

<span data-ttu-id="ff631-373">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-374">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-374">Preemption Possible</span></span>

<span data-ttu-id="ff631-375">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-375">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-376">例</span><span class="sxs-lookup"><span data-stu-id="ff631-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-377">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-377">See Also</span></span>

- <span data-ttu-id="ff631-378">nx_arp_dynamic_entries_invalidate、nx_arp_dynamic_entry_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="ff631-379">nx_arp_enable、nx_arp_gratuitous_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="ff631-380">nx_arp_hardware_address_find、nx_arp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="ff631-381">nx_arp_ip_address_find、nx_arp_static_entries_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="ff631-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="ff631-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="ff631-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-383">nx_icmp_enable</span></span>

<span data-ttu-id="ff631-384">インターネット制御メッセージ プロトコル (ICMP) を有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-385">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-386">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-386">Description</span></span>

<span data-ttu-id="ff631-387">このサービスを使用すると、指定した IP インスタンスの ICMP コンポーネントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="ff631-388">この ICMP コンポーネントは、インターネット エラー メッセージと ping の要求および応答の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="ff631-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-389">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-389">Parameters</span></span>

- <span data-ttu-id="ff631-390">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-391">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-391">Return Values</span></span>

- <span data-ttu-id="ff631-392">**NX_SUCCESS** (0x00) ICMP の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="ff631-393">**NX_ALREADY_ENABLED** (0x15) ICMP は既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ff631-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="ff631-394">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-395">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-396">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-396">Allowed From</span></span>

<span data-ttu-id="ff631-397">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-398">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-398">Preemption Possible</span></span>

<span data-ttu-id="ff631-399">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-399">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-400">例</span><span class="sxs-lookup"><span data-stu-id="ff631-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-401">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-401">See Also</span></span>

- <span data-ttu-id="ff631-402">nx_icmp_info_get、nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="ff631-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="ff631-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-403">nx_icmp_info_get</span></span>

<span data-ttu-id="ff631-404">ICMP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-405">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="ff631-406">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-406">Description</span></span>

<span data-ttu-id="ff631-407">このサービスを使用すると、指定した IP インスタンスの ICMP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="ff631-408">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-409">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-409">Parameters</span></span>

- <span data-ttu-id="ff631-410">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-411">**pings_sent** 送信された ping の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="ff631-412">**ping_timeouts** ping タイムアウトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="ff631-413">**ping_threads_suspended** ping 要求で中断されているスレッドの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="ff631-414">**ping_responses_received** 受信した ping 応答の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="ff631-415">**icmp_checksum_errors** ICMP チェックサム エラーの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="ff631-416">**icmp_unhandled_messages** 処理されていない ICMP メッセージの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-417">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-417">Return Values</span></span>

- <span data-ttu-id="ff631-418">**NX_SUCCESS** (0x00) ICMP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="ff631-419">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-420">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-421">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-422">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-422">Allowed From</span></span>

<span data-ttu-id="ff631-423">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-424">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-424">Preemption Possible</span></span>

<span data-ttu-id="ff631-425">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-425">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-426">例</span><span class="sxs-lookup"><span data-stu-id="ff631-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-427">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-427">See Also</span></span>

- <span data-ttu-id="ff631-428">nx_icmp_enable、nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="ff631-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="ff631-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="ff631-429">nx_icmp_ping</span></span>

<span data-ttu-id="ff631-430">指定された IP アドレスに ping 要求を送信します</span><span class="sxs-lookup"><span data-stu-id="ff631-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-431">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-432">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-432">Description</span></span>

<span data-ttu-id="ff631-433">このサービスを使用すると、指定した IP アドレスに ping 要求が送信され、ping 応答メッセージを指定した時間だけ待機します。</span><span class="sxs-lookup"><span data-stu-id="ff631-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="ff631-434">応答が受信されない場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="ff631-435">それ以外の場合は、response_ptr によってポイントされた変数で応答メッセージ全体が返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="ff631-436">*NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします。*</span><span class="sxs-lookup"><span data-stu-id="ff631-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-437">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-437">Parameters</span></span>

- <span data-ttu-id="ff631-438">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-439">**ip_address** ping する IP アドレス (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="ff631-440">ping メッセージのデータ領域へのデータ ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="ff631-441">**data_size** ping データ内のバイト数</span><span class="sxs-lookup"><span data-stu-id="ff631-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="ff631-442">**response_ptr** ping 応答メッセージを返すパケット ポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="ff631-443">**wait_option** ping 応答を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="ff631-444">待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="ff631-445">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="ff631-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="ff631-447">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-448">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-448">Return Values</span></span>

- <span data-ttu-id="ff631-449">**NX_SUCCESS** (0x00) ping に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="ff631-450">応答メッセージ ポインターは、response_ptr によってポイントされる変数に配置されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="ff631-451">**NX_NO_PACKET** (0x01) ping 要求パケットを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="ff631-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="ff631-452">**NX_OVERFLOW** (0x03) 指定されたデータ領域が、この IP インスタンスの既定のパケット サイズを超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="ff631-453">**NX_NO_RESPONSE** (0x29) 要求された IP が応答しませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="ff631-454">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-455">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-456">**NX_PTR_ERROR** (0x07) IP または応答ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="ff631-457">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-458">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-459">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-459">Allowed From</span></span>

<span data-ttu-id="ff631-460">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-461">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-461">Preemption Possible</span></span>

<span data-ttu-id="ff631-462">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-462">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-463">例</span><span class="sxs-lookup"><span data-stu-id="ff631-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-464">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-464">See Also</span></span>

- <span data-ttu-id="ff631-465">nx_icmp_enable、nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="ff631-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-466">nx_igmp_enable</span></span>

<span data-ttu-id="ff631-467">インターネット グループ管理プロトコル (IGMP) を有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-468">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-469">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-469">Description</span></span>

<span data-ttu-id="ff631-470">このサービスを使用すると、指定した IP インスタンスの IGMP コンポーネントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="ff631-471">IGMP コンポーネントは、IP マルチキャスト グループ管理操作のサポートを提供する役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="ff631-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-472">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-472">Parameters</span></span>

- <span data-ttu-id="ff631-473">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-474">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-474">Return Values</span></span>

- <span data-ttu-id="ff631-475">**NX_SUCCESS** (0x00) IGMP の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="ff631-476">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-477">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-478">**NX_ALREADY_ENABLED** (0x15) このコンポーネントは既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ff631-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-479">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-479">Allowed From</span></span>

<span data-ttu-id="ff631-480">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-481">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-481">Preemption Possible</span></span>

<span data-ttu-id="ff631-482">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-482">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-483">例</span><span class="sxs-lookup"><span data-stu-id="ff631-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-484">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-484">See Also</span></span>

- <span data-ttu-id="ff631-485">nx_igmp_info_get、nx_igmp_loopback_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="ff631-486">nx_igmp_loopback_enable、nx_igmp_multicast_interface_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="ff631-487">nx_igmp_multicast_join、nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="ff631-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-488">nx_igmp_info_get</span></span>

<span data-ttu-id="ff631-489">IGMP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-490">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="ff631-491">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-491">Description</span></span>

<span data-ttu-id="ff631-492">このサービスを使用すると、指定した IP インスタンスの IGMP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="ff631-493">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-494">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-494">Parameters</span></span>

- <span data-ttu-id="ff631-495">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-496">**igmp_reports_sent** 送信された ICMP レポートの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="ff631-497">**igmp_queries_received** マルチキャスト ルーターによって受信されたクエリの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="ff631-498">**igmp_checksum_errors** 受信パケットの IGMP チェックサム エラーの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="ff631-499">**current_groups_joined** この IP インスタンスを介して参加している現在のグループ数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-500">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-500">Return Values</span></span>

- <span data-ttu-id="ff631-501">**NX_SUCCESS** (0x00) IGMP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="ff631-502">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-503">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-504">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-505">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-505">Allowed From</span></span>

<span data-ttu-id="ff631-506">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-507">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-507">Preemption Possible</span></span>

<span data-ttu-id="ff631-508">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-508">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-509">例</span><span class="sxs-lookup"><span data-stu-id="ff631-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-510">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-510">See Also</span></span>

- <span data-ttu-id="ff631-511">nx_igmp_enable、nx_igmp_loopback_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="ff631-512">nx_igmp_loopback_enable、nx_igmp_multicast_interface_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="ff631-513">nx_igmp_multicast_join、nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="ff631-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="ff631-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="ff631-515">IGMP ループバックを無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-516">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-517">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-517">Description</span></span>

<span data-ttu-id="ff631-518">このサービスを使用すると、以降に参加したすべてのマルチキャスト グループの IGMP ループバックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-519">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-519">Parameters</span></span>

- <span data-ttu-id="ff631-520">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-521">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-521">Return Values</span></span>
- <span data-ttu-id="ff631-522">**NX_SUCCESS** (0x00) IGMP ループバックの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="ff631-523">**NX_NOT_ENABLED** (0x14) IGMP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="ff631-524">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-525">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-526">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-526">Allowed From</span></span>

<span data-ttu-id="ff631-527">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-528">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-528">Preemption Possible</span></span>

<span data-ttu-id="ff631-529">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-529">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-530">例</span><span class="sxs-lookup"><span data-stu-id="ff631-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-531">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-531">See Also</span></span>

- <span data-ttu-id="ff631-532">nx_igmp_enable、nx_igmp_info_get、nx_igmp_loopback_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="ff631-533">nx_igmp_multicast_interface_join、nx_igmp_multicast_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="ff631-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="ff631-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="ff631-536">IGMP ループバックを有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-537">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-538">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-538">Description</span></span>

<span data-ttu-id="ff631-539">このサービスを使用すると、以降に参加したすべてのマルチキャスト グループの IGMP ループバックが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-540">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-540">Parameters</span></span>

- <span data-ttu-id="ff631-541">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-542">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-542">Return Values</span></span>
- <span data-ttu-id="ff631-543">**NX_SUCCESS** (0x00) IGMP ループバックの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="ff631-544">**NX_NOT_ENABLED** (0x14) IGMP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="ff631-545">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-546">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-547">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-547">Allowed From</span></span>

<span data-ttu-id="ff631-548">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-549">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-549">Preemption Possible</span></span>

<span data-ttu-id="ff631-550">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-550">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-551">例</span><span class="sxs-lookup"><span data-stu-id="ff631-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-552">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-552">See Also</span></span>

- <span data-ttu-id="ff631-553">nx_igmp_enable、nx_igmp_info_get、nx_igmp_loopback_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="ff631-554">nx_igmp_multicast_interface_join、nx_igmp_multicast_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="ff631-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="ff631-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="ff631-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="ff631-557">指定されたマルチキャスト グループに IP インスタンスをインターフェイス経由で参加させます</span><span class="sxs-lookup"><span data-stu-id="ff631-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-558">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ff631-559">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-559">Description</span></span>

<span data-ttu-id="ff631-560">このサービスを使用すると、指定したネットワーク インターフェイス経由で、指定したマルチキャスト グループに IP インスタンスを参加できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="ff631-561">内部カウンターは、同じグループに参加した回数を追跡するために保持されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="ff631-562">マルチキャスト グループに参加した後、この IGMP コンポーネントによって、このグループ アドレスを持つ IP パケットを指定されたネットワーク インターフェイス経由で受信することが許可されます。また、この IP がこのマルチキャスト グループのメンバーであることがルーターに報告されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="ff631-563">IGMP メンバーシップの参加、報告、および脱退のメッセージも、指定されたネットワーク インターフェイス経由で送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-564">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-564">Parameters</span></span>

- <span data-ttu-id="ff631-565">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-566">**group_address** 参加するクラス D IP マルチキャスト グループ アドレス (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="ff631-567">**interface_index** NetX インスタンスに接続されているインターフェイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="ff631-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-568">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-568">Return Values</span></span>

- <span data-ttu-id="ff631-569">**NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="ff631-570">**NX_NO_MORE_ENTRIES** (0x17) これ以上、マルチキャスト グループに参加できません。最大値を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="ff631-571">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-572">**NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。</span><span class="sxs-lookup"><span data-stu-id="ff631-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="ff631-573">**NX_IP_ADDRESS_ERROR** (0x21) 指定されたマルチキャスト グループ アドレスは、有効なクラス D アドレスではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="ff631-574">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-575">**NX_NOT_ENABLED** (0x14) IP マルチキャスト サポートが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-576">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-576">Allowed From</span></span>

<span data-ttu-id="ff631-577">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-578">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-578">Preemption Possible</span></span>

<span data-ttu-id="ff631-579">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-579">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-580">例</span><span class="sxs-lookup"><span data-stu-id="ff631-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-581">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-581">See Also</span></span>

- <span data-ttu-id="ff631-582">nx_igmp_enable、nx_igmp_info_get、nx_igmp_loopback_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="ff631-583">nx_igmp_loopback_enable、nx_igmp_multicast_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="ff631-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="ff631-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="ff631-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="ff631-586">指定されたマルチキャスト グループに IP インスタンスを参加させます</span><span class="sxs-lookup"><span data-stu-id="ff631-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-587">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="ff631-588">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-588">Description</span></span>

<span data-ttu-id="ff631-589">このサービスを使用すると、指定したマルチキャスト グループに IP インスタンスを参加できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="ff631-590">内部カウンターは、同じグループに参加した回数を追跡するために保持されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="ff631-591">これが、ホストがグループに参加しようとしていることを示すネットワーク上に送信される最初の参加要求である場合、このドライバーは IGMP レポートを送信するように命令されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="ff631-592">参加後に、この IGMP コンポーネントによってこのグループ アドレスを使用した IP パケットの受信が許可され、その IP がこのマルチキャスト グループのメンバーであることがルーターに報告されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="ff631-593">*非プライマリ デバイスのマルチキャスト グループに参加するには、サービス **nx_igmp_multicast_interface_join** を使用します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="ff631-594">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="ff631-594">**Parameters**</span></span>

- <span data-ttu-id="ff631-595">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-596">**group_address** 参加するクラス D IP マルチキャスト グループ アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-597">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-597">Return Values</span></span>

- <span data-ttu-id="ff631-598">**NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="ff631-599">**NX_NO_MORE_ENTRIES** (0x17) これ以上、マルチキャスト グループに参加できません。最大値を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="ff631-600">**NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。</span><span class="sxs-lookup"><span data-stu-id="ff631-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="ff631-601">**NX_IP_ADDRESS_ERROR** (0x21) IP グループ アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="ff631-602">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-603">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-604">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-605">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-605">Allowed From</span></span>

<span data-ttu-id="ff631-606">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-607">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-607">Preemption Possible</span></span>

<span data-ttu-id="ff631-608">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-608">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-609">例</span><span class="sxs-lookup"><span data-stu-id="ff631-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-610">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-610">See Also</span></span>

- <span data-ttu-id="ff631-611">nx_igmp_enable、nx_igmp_info_get、nx_igmp_loopback_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="ff631-612">nx_igmp_loopback_enable、nx_igmp_multicast_interface_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="ff631-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="ff631-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="ff631-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="ff631-615">指定したマルチキャスト グループから IP インスタンスを脱退させます</span><span class="sxs-lookup"><span data-stu-id="ff631-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-616">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="ff631-617">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-617">Description</span></span>

<span data-ttu-id="ff631-618">このサービスを使用すると、脱退要求の数が参加要求の数と一致する場合、その指定したマルチキャスト グループから IP インスタンスを脱退させます。</span><span class="sxs-lookup"><span data-stu-id="ff631-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="ff631-619">それ以外の場合は、内部の参加カウントが単にデクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-620">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-620">Parameters</span></span>

- <span data-ttu-id="ff631-621">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-622">**group_address** 脱退するマルチキャスト グループ。</span><span class="sxs-lookup"><span data-stu-id="ff631-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-623">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-623">Return Values</span></span>

- <span data-ttu-id="ff631-624">**NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="ff631-625">**NX_ENTRY_NOT_FOUND** (0x16) 前の参加要求が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="ff631-626">**NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。</span><span class="sxs-lookup"><span data-stu-id="ff631-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="ff631-627">**NX_IP_ADDRESS_ERROR** (0x21) IP グループ アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="ff631-628">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-629">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-630">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-631">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-631">Allowed From</span></span>

<span data-ttu-id="ff631-632">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-633">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-633">Preemption Possible</span></span>

<span data-ttu-id="ff631-634">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-634">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-635">例</span><span class="sxs-lookup"><span data-stu-id="ff631-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="ff631-636">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-636">See Also</span></span>

- <span data-ttu-id="ff631-637">nx_igmp_enable、nx_igmp_info_get、nx_igmp_loopback_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="ff631-638">nx_igmp_loopback_enable、nx_igmp_multicast_interface_join、</span><span class="sxs-lookup"><span data-stu-id="ff631-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="ff631-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="ff631-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="ff631-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="ff631-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="ff631-641">IP アドレスが変化した場合、アプリケーションに通知します</span><span class="sxs-lookup"><span data-stu-id="ff631-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-642">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="ff631-643">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-643">Description</span></span>

<span data-ttu-id="ff631-644">このサービスを使用すると、IP アドレスが変更されるたびに呼び出されるアプリケーション通知関数を登録できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-645">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-645">Parameters</span></span>

- <span data-ttu-id="ff631-646">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-647">**change_notify** IP 変更通知関数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="ff631-648">このパラメーターが NX_NULL の場合、IP アドレスの変更通知は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="ff631-649">**additional_info** IP アドレスが変更されたときに通知関数にも提供されるオプションの追加情報を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-650">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-650">Return Values</span></span>

- <span data-ttu-id="ff631-651">**NX_SUCCESS** (0x00) IP アドレスの変更通知に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="ff631-652">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-653">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-654">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-654">Allowed From</span></span>

<span data-ttu-id="ff631-655">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-656">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-656">Preemption Possible</span></span>

<span data-ttu-id="ff631-657">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-657">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-658">例</span><span class="sxs-lookup"><span data-stu-id="ff631-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-659">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-659">See Also</span></span>

- <span data-ttu-id="ff631-660">nx_ip_address_get、nx_ip_address_set、nx_ip_create, nx_ip_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="ff631-661">nx_ip_driver_direct_command、nx_ip_driver_interface_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="ff631-662">nx_ip_forwarding_disable、nx_ip_forwarding_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="ff631-663">nx_ip_fragment_disable、nx_ip_fragment_enable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-664">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="ff631-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="ff631-665">nx_ip_address_get</span></span>

<span data-ttu-id="ff631-666">IP アドレスとネットワーク マスクを取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-667">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="ff631-668">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-668">Description</span></span>

<span data-ttu-id="ff631-669">このサービスを使用すると、プライマリ ネットワーク インターフェイスの IP アドレスとそのサブネット マスクが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="ff631-670">\* セカンダリ デバイスの情報を取得するには、このサービスを使用します</span><span class="sxs-lookup"><span data-stu-id="ff631-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="ff631-671">**nx_ip_interface_address_get**。\*</span><span class="sxs-lookup"><span data-stu-id="ff631-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-672">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-672">Parameters</span></span>

- <span data-ttu-id="ff631-673">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-674">**ip_address** IP アドレスの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="ff631-675">**network_mask** ネットワーク マスクの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-676">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-676">Return Values</span></span>

- <span data-ttu-id="ff631-677">**NX_SUCCESS** (0x00) IP アドレスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="ff631-678">**NX_PTR_ERROR** (0x07) IP または戻り変数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="ff631-679">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-680">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-680">Allowed From</span></span>

<span data-ttu-id="ff631-681">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-682">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-682">Preemption Possible</span></span>

<span data-ttu-id="ff631-683">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-683">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-684">例</span><span class="sxs-lookup"><span data-stu-id="ff631-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-685">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-685">See Also</span></span>

- <span data-ttu-id="ff631-686">nx_ip_address_change_notify、nx_ip_address_set, nx_ip_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="ff631-687">nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-688">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-689">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-690">nx_ip_fragment_enable、nx_ip_info_get, nx_ip_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="ff631-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="ff631-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="ff631-692">nx_ip_address_set</span></span>

<span data-ttu-id="ff631-693">IP アドレスとネットワーク マスクを設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-694">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="ff631-695">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-695">Description</span></span>

<span data-ttu-id="ff631-696">このサービスを使用すると、プライマリ ネットワーク インターフェイスの IP アドレスとネットワーク マスクが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="ff631-697">*セカンダリ デバイスの IP アドレスとネットワーク マスクを設定するには、サービス **nx_ip_interface_address_set** を使用します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-698">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-698">Parameters</span></span>

- <span data-ttu-id="ff631-699">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-700">**ip_address** 新しい IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="ff631-701">**network_mask** 新しいネットワーク マスク。</span><span class="sxs-lookup"><span data-stu-id="ff631-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-702">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-702">Return Values</span></span>

- <span data-ttu-id="ff631-703">**NX_SUCCESS** (0x00) IP アドレスの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="ff631-704">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-705">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-706">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-707">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-707">Allowed From</span></span>

<span data-ttu-id="ff631-708">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-709">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-709">Preemption Possible</span></span>

<span data-ttu-id="ff631-710">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-710">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-711">例</span><span class="sxs-lookup"><span data-stu-id="ff631-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-712">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-712">See Also</span></span>

- <span data-ttu-id="ff631-713">nx_ip_address_change_notify、nx_ip_address_get, nx_ip_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="ff631-714">nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-715">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-716">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-717">nx_ip_fragment_enable、nx_ip_info_get, nx_ip_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="ff631-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="ff631-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="ff631-719">nx_ip_create</span></span>

<span data-ttu-id="ff631-720">IP インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="ff631-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-721">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="ff631-722">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-722">Description</span></span>

<span data-ttu-id="ff631-723">このサービスを使用すると、ユーザーが指定した IP アドレスとネットワーク ドライバーを持つ IP インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="ff631-724">また、このアプリケーションは、その IP インスタンスが内部パケット割り当てに使用するために、以前に作成したパケット プールを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="ff631-725">この IP のスレッドが実行されるまで、指定されたアプリケーション ネットワーク ドライバーは呼び出されないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-726">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-726">Parameters</span></span>

- <span data-ttu-id="ff631-727">**ip_ptr** 新しい IP インスタンスを作成するための制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="ff631-728">**name** この新しい IP インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="ff631-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="ff631-729">**ip_address** この新しい IP インスタンスの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="ff631-730">**network_mask** サブネットまたはスーパーネットで使用する IP アドレスのネットワーク部分を表すマスク。</span><span class="sxs-lookup"><span data-stu-id="ff631-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="ff631-731">**default_pool** 以前に作成した NetX パケット プールの制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="ff631-732">**ip_network_driver** IP パケットを送受信するために使用される、ユーザーが指定したネットワーク ドライバー。</span><span class="sxs-lookup"><span data-stu-id="ff631-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="ff631-733">**memory_ptr** IP ヘルパー スレッドのスタック領域のメモリ領域を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="ff631-734">**memory_size** IP ヘルパー スレッドのスタックのメモリ領域内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="ff631-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="ff631-735">**priority** IP ヘルパー スレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="ff631-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-736">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-736">Return Values</span></span>
- <span data-ttu-id="ff631-737">**NX_SUCCESS** (0x00) IP インスタンスの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="ff631-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX ライブラリが正しく構成されていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="ff631-739">**NX_PTR_ERROR** (0x07) IP、ネットワーク ドライバー関数ポインター、パケット プール、またはメモリ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="ff631-740">**NX_SIZE_ERROR** (0x09) 指定されたスタック サイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="ff631-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="ff631-741">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-742">**NX_IP_ADDRESS_ERROR** (0x21) 指定された IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="ff631-743">**NX_OPTION_ERROR** (0x21) 指定された IP スレッドの優先順位が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-744">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-744">Allowed From</span></span>

<span data-ttu-id="ff631-745">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-746">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-746">Preemption Possible</span></span>

<span data-ttu-id="ff631-747">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-747">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-748">例</span><span class="sxs-lookup"><span data-stu-id="ff631-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-749">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-749">See Also</span></span>

- <span data-ttu-id="ff631-750">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-751">nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-752">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-753">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-754">nx_ip_fragment_enable、nx_ip_info_get, nx_ip_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="ff631-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="ff631-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-756">nx_ip_delete</span></span>

<span data-ttu-id="ff631-757">以前に作成した IP インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-758">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-759">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-759">Description</span></span>

<span data-ttu-id="ff631-760">このサービスを使用すると、以前に作成した IP インスタンスが削除され、その IP インスタンスによって所有されていたすべてのシステム リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-761">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-761">Parameters</span></span>
- <span data-ttu-id="ff631-762">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-763">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-763">Return Values</span></span>

- <span data-ttu-id="ff631-764">**NX_SUCCESS** (0x00) IP アドレスの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="ff631-765">**NX_SOCKETS_BOUND** (0x28) この IP インスタンスには依然として UDP ソケットまたは TCP ソケットがバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="ff631-766">IP インスタンスを削除する前に、すべてのソケットをバインド解除し、削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="ff631-767">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-768">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-769">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-769">Allowed From</span></span>

<span data-ttu-id="ff631-770">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-771">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-771">Preemption Possible</span></span>

<span data-ttu-id="ff631-772">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-773">例</span><span class="sxs-lookup"><span data-stu-id="ff631-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-774">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-774">See Also</span></span>

- <span data-ttu-id="ff631-775">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-776">nx_ip_create、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-777">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-778">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-779">nx_ip_fragment_enable、nx_ip_info_get, nx_ip_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="ff631-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="ff631-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="ff631-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="ff631-782">ネットワーク ドライバーにコマンドを発行します</span><span class="sxs-lookup"><span data-stu-id="ff631-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-783">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-784">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-784">Description</span></span>

<span data-ttu-id="ff631-785">このサービスを使用すると、***nx_ip_create*** の呼び出し時に指定したアプリケーションのプライマリ ネットワーク インターフェイス ドライバーに対する直接インターフェイスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="ff631-786">アプリケーション固有のコマンドは、その数値が NX_LINK_USER_COMMAND 以上である場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="ff631-787">*セカンダリ デバイスに対してコマンドを発行するには、サービス **nx_ip_driver_interface_direct_command** を使用します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-788">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-788">Parameters</span></span>

- <span data-ttu-id="ff631-789">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-790">**command** 数値コマンド コード。</span><span class="sxs-lookup"><span data-stu-id="ff631-790">**command** Numeric command code.</span></span> <span data-ttu-id="ff631-791">標準コマンドは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="ff631-792">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="ff631-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="ff631-793">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="ff631-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="ff631-794">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="ff631-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="ff631-795">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="ff631-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="ff631-796">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="ff631-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="ff631-797">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="ff631-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="ff631-798">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="ff631-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="ff631-799">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="ff631-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="ff631-800">**return_value_ptr** 呼び出し元の戻り変数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-801">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-801">Return Values</span></span>

- <span data-ttu-id="ff631-802">**NX_SUCCESS** (0x00) ネットワーク ドライバーのダイレクト コマンドに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="ff631-803">**NX_UNHANDLED_COMMAND** (0x44) ネットワーク ドライバー コマンドが処理または実装されていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="ff631-804">**NX_PTR_ERROR** (0x07) IP または戻り値ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="ff631-805">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-806">**NX_INVALID_INTERFACE** (0x4C) インターフェイス インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-807">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-807">Allowed From</span></span>

<span data-ttu-id="ff631-808">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-808">Threads</span></span>

- <span data-ttu-id="ff631-809">**プリエンプション可能**</span><span class="sxs-lookup"><span data-stu-id="ff631-809">**Preemption Possible**</span></span>

<span data-ttu-id="ff631-810">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-810">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-811">例</span><span class="sxs-lookup"><span data-stu-id="ff631-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-812">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-812">See Also</span></span>

- <span data-ttu-id="ff631-813">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-814">nx_ip_create, nx_ip_delete、nx_ip_driver_interface_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="ff631-815">nx_ip_forwarding_disable、nx_ip_forwarding_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="ff631-816">nx_ip_fragment_disable、nx_ip_fragment_enable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-817">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="ff631-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="ff631-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="ff631-819">ネットワーク ドライバーにコマンドを発行します</span><span class="sxs-lookup"><span data-stu-id="ff631-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-820">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-821">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-821">Description</span></span>

<span data-ttu-id="ff631-822">このサービスを使用すると、IP インスタンス内のアプリケーションのネットワーク デバイス ドライバーに対する直接コマンドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="ff631-823">アプリケーション固有のコマンドは、その数値が *NX_LINK_USER_COMMAND* 以上である場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-824">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-824">Parameters</span></span>

- <span data-ttu-id="ff631-825">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-826">**command** 数値コマンド コード。</span><span class="sxs-lookup"><span data-stu-id="ff631-826">**command** Numeric command code.</span></span> <span data-ttu-id="ff631-827">標準コマンドは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="ff631-828">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="ff631-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="ff631-829">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="ff631-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="ff631-830">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="ff631-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="ff631-831">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="ff631-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="ff631-832">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="ff631-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="ff631-833">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="ff631-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="ff631-834">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="ff631-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="ff631-835">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="ff631-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="ff631-836">**interface_index** コマンドの送信先となるネットワーク インターフェイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="ff631-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="ff631-837">**return_value_ptr** 呼び出し元の戻り変数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-838">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-838">Return Values</span></span>
- <span data-ttu-id="ff631-839">**NX_SUCCESS** (0x00) ネットワーク ドライバーのダイレクト コマンドに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="ff631-840">**NX_UNHANDLED_COMMAND** (0x44) ネットワーク ドライバー コマンドが処理または実装されていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="ff631-841">**NX_INVALID_INTERFACE** (0x4C) インターフェイス インデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="ff631-842">**NX_PTR_ERROR** (0x07) IP または戻り値ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="ff631-843">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-844">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-844">Allowed From</span></span>

<span data-ttu-id="ff631-845">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-846">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-846">Preemption Possible</span></span>

<span data-ttu-id="ff631-847">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-847">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-848">例</span><span class="sxs-lookup"><span data-stu-id="ff631-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-849">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-849">See Also</span></span>

- <span data-ttu-id="ff631-850">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-851">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-852">nx_ip_forwarding_disable、nx_ip_forwarding_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="ff631-853">nx_ip_fragment_disable、nx_ip_fragment_enable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-854">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="ff631-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="ff631-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="ff631-856">IP パケット転送を無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-857">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-858">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-858">Description</span></span>

<span data-ttu-id="ff631-859">このサービスを使用すると、NetX IP コンポーネント内の IP パケットの転送が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="ff631-860">IP タスクを作成すると、このサービスは自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-861">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-861">Parameters</span></span>

- <span data-ttu-id="ff631-862">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-863">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-863">Return Values</span></span>

- <span data-ttu-id="ff631-864">**NX_SUCCESS** (0x00) IP 転送の無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="ff631-865">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-866">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-867">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-867">Allowed From</span></span>

<span data-ttu-id="ff631-868">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-869">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-869">Preemption Possible</span></span>

<span data-ttu-id="ff631-870">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-870">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-871">例</span><span class="sxs-lookup"><span data-stu-id="ff631-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-872">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-872">See Also</span></span>

- <span data-ttu-id="ff631-873">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-874">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-875">nx_ip_driver_interface_direct_command、nx_ip_forwarding_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="ff631-876">nx_ip_fragment_disable、nx_ip_fragment_enable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-877">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="ff631-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="ff631-879">IP パケット転送を有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-880">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-881">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-881">Description</span></span>

<span data-ttu-id="ff631-882">このサービスを使用すると、NetX IP コンポーネント内の IP パケットの転送が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="ff631-883">IP タスクを作成すると、このサービスは自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-884">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-884">Parameters</span></span>

- <span data-ttu-id="ff631-885">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-886">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-886">Return Values</span></span>
- <span data-ttu-id="ff631-887">**NX_SUCCESS** (0x00) IP 転送の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="ff631-888">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-889">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-890">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-890">Allowed From</span></span>

<span data-ttu-id="ff631-891">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-892">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-892">Preemption Possible</span></span>

<span data-ttu-id="ff631-893">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-893">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-894">例</span><span class="sxs-lookup"><span data-stu-id="ff631-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-895">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-895">See Also</span></span>

- <span data-ttu-id="ff631-896">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-897">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-898">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-899">nx_ip_fragment_disable、nx_ip_fragment_enable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-900">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="ff631-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="ff631-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="ff631-902">IP パケットのフラグメント化を無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-903">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-904">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-904">Description</span></span>

<span data-ttu-id="ff631-905">このサービスを使用すると、IP パケットのフラグメント化と再アセンブル機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="ff631-906">再アセンブル待ちのパケットは、このサービスによって解放されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="ff631-907">IP タスクを作成すると、このサービスは自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-908">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-908">Parameters</span></span>

- <span data-ttu-id="ff631-909">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-910">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-910">Return Values</span></span>
- <span data-ttu-id="ff631-911">**NX_SUCCESS** (0x00) IP フラグメントの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="ff631-912">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-913">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-914">**NX_NOT_ENABLED** (0x14) IP のフラグメント化はこの IP インスタンスで有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-915">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-915">Allowed From</span></span>

<span data-ttu-id="ff631-916">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-917">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-917">Preemption Possible</span></span>

<span data-ttu-id="ff631-918">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-918">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-919">例</span><span class="sxs-lookup"><span data-stu-id="ff631-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-920">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-920">See Also</span></span>

- <span data-ttu-id="ff631-921">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-922">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-923">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-924">nx_ip_forwarding_enable、nx_ip_fragment_enable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-925">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="ff631-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="ff631-927">IP パケットのフラグメント化を有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-928">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-929">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-929">Description</span></span>

<span data-ttu-id="ff631-930">このサービスを使用すると、IP パケットのフラグメント化と再アセンブル機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="ff631-931">IP タスクを作成すると、このサービスは自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-932">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-932">Parameters</span></span>

- <span data-ttu-id="ff631-933">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-934">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-934">Return Values</span></span>

- <span data-ttu-id="ff631-935">**NX_SUCCESS** (0x00) IP フラグメントの有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="ff631-936">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-937">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-938">**NX_NOT_ENABLED** (0x14) IP のフラグメント化機能は NetX にコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-939">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-939">Allowed From</span></span>

<span data-ttu-id="ff631-940">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-941">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-941">Preemption Possible</span></span>

<span data-ttu-id="ff631-942">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-942">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-943">例</span><span class="sxs-lookup"><span data-stu-id="ff631-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-944">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-944">See Also</span></span>

- <span data-ttu-id="ff631-945">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-946">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-947">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-948">nx_ip_forwarding_enable、nx_ip_fragment_disable、nx_ip_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="ff631-949">nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="ff631-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="ff631-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="ff631-951">ゲートウェイ IP アドレスを設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-952">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="ff631-953">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-953">Description</span></span>

<span data-ttu-id="ff631-954">このサービスを使用すると、IP ゲートウェイの IP アドレスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="ff631-955">ネットワーク外に向かうすべてのトラフィックは、送信のためにこのゲートウェイにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="ff631-956">このゲートウェイは、いずれかのネットワーク インターフェイスを介して直接アクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-957">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-957">Parameters</span></span>

- <span data-ttu-id="ff631-958">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-959">**ip_address** ゲートウェイの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-960">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-960">Return Values</span></span>

- <span data-ttu-id="ff631-961">**NX_SUCCESS** (0x00) ゲートウェイ IP アドレスの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="ff631-962">**NX_PTR_ERROR** (0x07) IP インスタンス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="ff631-963">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-964">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-965">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-965">Allowed From</span></span>

<span data-ttu-id="ff631-966">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-967">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-967">Preemption Possible</span></span>

<span data-ttu-id="ff631-968">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-968">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-969">例</span><span class="sxs-lookup"><span data-stu-id="ff631-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="ff631-970">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-970">See Also</span></span>

- <span data-ttu-id="ff631-971">nx_ip_info_get、nx_ip_static_route_add、nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="ff631-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-972">nx_ip_info_get</span></span>

<span data-ttu-id="ff631-973">IP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-974">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="ff631-975">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-975">Description</span></span>

<span data-ttu-id="ff631-976">このサービスを使用すると、指定した IP インスタンスの IP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="ff631-977">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-978">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-978">Parameters</span></span>

- <span data-ttu-id="ff631-979">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-980">**ip_total_packets_sent** 送信された IP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="ff631-981">**ip_total_bytes_sent** 送信された合計バイト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="ff631-982">**ip_total_packets_received** IP 受信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="ff631-983">**ip_total_bytes_received** 受信した IP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="ff631-984">**ip_invalid_packets** 無効な IP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="ff631-985">**ip_receive_packets_dropped** 破棄された受信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="ff631-986">**ip_receive_checksum_errors** 受信パケットのチェックサム エラーの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="ff631-987">**ip_send_packets_dropped** 破棄された送信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="ff631-988">**ip_total_fragments_sent** 送信されたフラグメントの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="ff631-989">**ip_total_fragments_received** 受信したフラグメントの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-990">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-990">Return Values</span></span>

- <span data-ttu-id="ff631-991">**NX_SUCCESS** (0x00) IP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="ff631-992">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-993">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-994">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-994">Allowed From</span></span>

<span data-ttu-id="ff631-995">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-996">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-996">Preemption Possible</span></span>

<span data-ttu-id="ff631-997">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-997">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-998">例</span><span class="sxs-lookup"><span data-stu-id="ff631-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-999">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-999">See Also</span></span>

- <span data-ttu-id="ff631-1000">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-1001">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-1002">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-1003">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-1004">nx_ip_fragment_enable、nx_ip_status_check、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="ff631-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="ff631-1006">インターフェイスの IP アドレスを取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1007">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="ff631-1008">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1008">Description</span></span>

<span data-ttu-id="ff631-1009">このサービスを使用すると、指定したネットワーク インターフェイスの IP アドレスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="ff631-1010">*指定されたデバイスがプライマリ デバイスでない場合は、そのデバイスを先に IP インスタンスに接続しておく必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1011">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1011">Parameters</span></span>

- <span data-ttu-id="ff631-1012">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1013">**interface_index** インターフェイス インデックス。IP インスタンスに接続されているネットワーク インターフェイスのインデックスと同じ値です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="ff631-1014">**ip_address** デバイス インターフェイスの IP アドレスの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="ff631-1015">**network_mask** デバイス インターフェイスのネットワーク マスクの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1016">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1016">Return Values</span></span>

- <span data-ttu-id="ff631-1017">**NX_SUCCESS** (0x00) IP アドレスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="ff631-1018">**NX_INVALID_INTERFACE** (0x4C) 指定されたネットワーク インターフェイスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="ff631-1019">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1020">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1021">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1021">Allowed From</span></span>

<span data-ttu-id="ff631-1022">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1023">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1023">Preemption Possible</span></span>

<span data-ttu-id="ff631-1024">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1025">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1026">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1026">See Also</span></span>

- <span data-ttu-id="ff631-1027">nx_ip_interface_address_set、nx_ip_interface_attach、</span><span class="sxs-lookup"><span data-stu-id="ff631-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="ff631-1028">nx_ip_interface_info_get、nx_ip_interface_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="ff631-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="ff631-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="ff631-1031">インターフェイスの IP アドレスとネットワーク マスクを設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1032">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="ff631-1033">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1033">Description</span></span>

<span data-ttu-id="ff631-1034">このサービスを使用すると、指定した IP インターフェイスの IP アドレスとネットワーク マスクが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="ff631-1035">*指定されたインターフェイスは、先に IP インスタンスに接続されている必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1036">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1036">Parameters</span></span>

- <span data-ttu-id="ff631-1037">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1038">**interface_index** NetX インスタンスに接続されているインターフェイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="ff631-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="ff631-1039">**ip_address** 新しいネットワーク インターフェイスの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="ff631-1040">**network_mask** 新しいインターフェイスのネットワーク マスク。</span><span class="sxs-lookup"><span data-stu-id="ff631-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1041">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1041">Return Values</span></span>

- <span data-ttu-id="ff631-1042">**NX_SUCCESS** (0x00) IP アドレスの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="ff631-1043">**NX_INVALID_INTERFACE** (0x4C) 指定されたネットワーク インターフェイスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="ff631-1044">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1045">**NX_PTR_ERROR** (0x07) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="ff631-1046">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1047">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1047">Allowed From</span></span>

<span data-ttu-id="ff631-1048">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1049">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1049">Preemption Possible</span></span>

<span data-ttu-id="ff631-1050">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1051">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1052">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1052">See Also</span></span>

- <span data-ttu-id="ff631-1053">nx_ip_interface_address_get、nx_ip_interface_attach、</span><span class="sxs-lookup"><span data-stu-id="ff631-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="ff631-1054">nx_ip_interface_info_get、nx_ip_interface_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="ff631-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="ff631-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="ff631-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="ff631-1057">ネットワーク インターフェイスを IP インスタンスに接続します</span><span class="sxs-lookup"><span data-stu-id="ff631-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1058">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="ff631-1059">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1059">Description</span></span>

<span data-ttu-id="ff631-1060">このサービスを使用すると、物理ネットワーク インターフェイスを IP インターフェイスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="ff631-1061">この IP インスタンスはプライマリ インターフェイスを使用して作成されるので、追加の各インターフェイスはプライマリ インターフェイスのセカンダリになります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="ff631-1062">この IP インスタンスに接続されているネットワーク インターフェイスの総数 (プライマリ インターフェイスを含む) は、**NX_MAX_PHYSICAL_INTERFACES** を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="ff631-1063">IP スレッドがまだ実行されていない場合は、すべての物理インターフェイスを初期化する IP スレッド スタートアップ プロセスの一部として、セカンダリ インターフェイスが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="ff631-1064">IP スレッドがまだ実行中でない場合は、このセカンダリ インターフェイスが ***nx_ip_interface_attach*** サービスの一部として初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="ff631-1065">*ip_ptr は、有効な NetX IP 構造体をポイントする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="ff631-1066">***NX_MAX_PHYSICAL_INTERFACES** は、その IP インスタンスのネットワーク インターフェイスの数に対して構成する必要があります。既定値は 1 です。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1067">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1067">Parameters</span></span>

- <span data-ttu-id="ff631-1068">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1069">**interface_name** インターフェイス名の文字列を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="ff631-1070">**ip_address** デバイスの IP アドレス (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="ff631-1071">**network_mask** デバイスのネットワーク マスク (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="ff631-1072">**ip_link_driver** そのインターフェイスのイーサネット ドライバー。</span><span class="sxs-lookup"><span data-stu-id="ff631-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1073">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1073">Return Values</span></span>

- <span data-ttu-id="ff631-1074">**NX_SUCCESS** (0x00) 静的ルーティング テーブルにエントリが追加されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="ff631-1075">**NX_NO_MORE_ENTRIES** (0x17) インターフェイスの最大数。</span><span class="sxs-lookup"><span data-stu-id="ff631-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="ff631-1076">**NX_MAX_PHYSICAL_INTERFACES** を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="ff631-1077">**NX_DUPLICATED_ENTRY** (0x52) 指定された IP アドレスは、この IP インスタンスで既に使用されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="ff631-1078">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1079">**NX_PTR_ERROR** (0x07) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="ff631-1080">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレス入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1081">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1081">Allowed From</span></span>

<span data-ttu-id="ff631-1082">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1083">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1083">Preemption Possible</span></span>

<span data-ttu-id="ff631-1084">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1085">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1086">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1086">See Also</span></span>

- <span data-ttu-id="ff631-1087">nx_ip_interface_address_get、nx_ip_interface_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="ff631-1088">nx_ip_interface_info_get、nx_ip_interface_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="ff631-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="ff631-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="ff631-1091">ネットワーク インターフェイス パラメーターを取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-1092">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="ff631-1093">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1093">Description</span></span>

<span data-ttu-id="ff631-1094">このサービスを使用すると、指定したネットワーク インターフェイスのネットワーク パラメーターに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="ff631-1095">すべてのデータは、ホストのバイト順に取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="ff631-1096">*ip_ptr は、有効な NetX IP 構造体を指す必要があります。指定されたインターフェイスがプライマリ インターフェイスでない場合は、そのインターフェイスを先に IP インスタンスに接続しておく必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1097">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1097">Parameters</span></span>

- <span data-ttu-id="ff631-1098">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1099">**interface_index** ネットワーク インターフェイスを指定するインデックス。</span><span class="sxs-lookup"><span data-stu-id="ff631-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="ff631-1100">**interface_name** ネットワーク インターフェイスの名前を保持するバッファーを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="ff631-1101">**ip_address** インターフェイスの IP アドレスの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="ff631-1102">**network_mask** ネットワーク マスクの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="ff631-1103">**mtu_size** このインターフェイスの最大転送単位の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="ff631-1104">**physical_address_msw** デバイスの MAC アドレスの上位 16 ビットの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="ff631-1105">**physical_address_lsw** デバイスの MAC アドレスの下位 32 ビットの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-1106">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1106">Return Values</span></span>
- <span data-ttu-id="ff631-1107">**NX_SUCCESS** (0x00) インターフェイス情報が取得されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="ff631-1108">**NX_PTR_ERROR** (0x07) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="ff631-1109">**NX_INVALID_INTERFACE** (0x4C) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1110">**NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1111">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1111">Allowed From</span></span>

<span data-ttu-id="ff631-1112">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1113">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1113">Preemption Possible</span></span>

<span data-ttu-id="ff631-1114">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1115">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1116">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1116">See Also</span></span>

- <span data-ttu-id="ff631-1117">nx_ip_interface_address_get、nx_ip_interface_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="ff631-1118">nx_ip_interface_attach、nx_ip_interface_status_check、</span><span class="sxs-lookup"><span data-stu-id="ff631-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="ff631-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="ff631-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="ff631-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="ff631-1121">IP インスタンスの状態を確認します</span><span class="sxs-lookup"><span data-stu-id="ff631-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-1122">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1123">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1123">Description</span></span>

<span data-ttu-id="ff631-1124">このサービスを使用すると、以前に作成された IP インスタンスのネットワーク インターフェイスの指定した状態を確認し、必要に応じて待機します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1125">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1125">Parameters</span></span>

- <span data-ttu-id="ff631-1126">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1127">**interface_index** インターフェイスのインデックス番号</span><span class="sxs-lookup"><span data-stu-id="ff631-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="ff631-1128">**needed_status** 要求された IP 状態。ビットマップ形式で次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="ff631-1129">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="ff631-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="ff631-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="ff631-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="ff631-1131">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="ff631-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="ff631-1132">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="ff631-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="ff631-1133">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="ff631-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="ff631-1134">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="ff631-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="ff631-1135">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="ff631-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="ff631-1136">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="ff631-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="ff631-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="ff631-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="ff631-1138">**actual_status** 設定された実際のビットの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="ff631-1139">**wait_option** 要求されたステータス ビットが使用できない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="ff631-1140">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="ff631-1141">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="ff631-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="ff631-1143">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1144">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1144">Return Values</span></span>

- <span data-ttu-id="ff631-1145">**NX_SUCCESS** (0x00) IP 状態の確認に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="ff631-1146">**NX_NOT_SUCCESSFUL** (0x43) 状態要求が、指定されたタイムアウト時間内に満たされませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="ff631-1147">**NX_PTR_ERROR** (0x07) IP ポインターが無効であるか、無効になったか、または実際の状態ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="ff631-1148">**NX_OPTION_ERROR** (0x0a) 必要な状態オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="ff631-1149">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index が範囲外です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="ff631-1151">または、インターフェイスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1152">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1152">Allowed From</span></span>

<span data-ttu-id="ff631-1153">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1154">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1154">Preemption Possible</span></span>

<span data-ttu-id="ff631-1155">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1156">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1157">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1157">See Also</span></span>

- <span data-ttu-id="ff631-1158">nx_ip_interface_address_get、nx_ip_interface_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="ff631-1159">nx_ip_interface_attach、nx_ip_interface_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="ff631-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="ff631-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="ff631-1162">リンク状態の変更通知コールバック関数を設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1163">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="ff631-1164">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1164">Description</span></span>

<span data-ttu-id="ff631-1165">このサービスを使用すると、リンク状態の変更通知コールバック関数を構成できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="ff631-1166">ユーザーが指定した *link_status_change_notify* ルーチンは、プライマリかセカンダリのいずれかのインターフェイスの状態が変更されたとき (IP アドレスの変更など) に呼び出されます。*link_status_change_notify* が null 値の場合、リンク状態の変更通知コールバック関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1167">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1167">Parameters</span></span>

- <span data-ttu-id="ff631-1168">**ip_ptr** IP 制御ブロック ポインター</span><span class="sxs-lookup"><span data-stu-id="ff631-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="ff631-1169">**link_status_change_notify** 物理インターフェイスの変更時に呼び出されるユーザー指定のコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="ff631-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-1170">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1170">Return Values</span></span>

- <span data-ttu-id="ff631-1171">**NX_SUCCESS** (0x00) 設定に成功しました</span><span class="sxs-lookup"><span data-stu-id="ff631-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="ff631-1172">**NX_PTR_ERROR** (0x07) IP 制御ブロック ポインターまたは新しい物理アドレス ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="ff631-1173">**NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ff631-1174">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1174">Allowed From</span></span>

<span data-ttu-id="ff631-1175">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1176">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1176">Preemption Possible</span></span>

<span data-ttu-id="ff631-1177">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1178">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1179">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1179">See Also</span></span>

- <span data-ttu-id="ff631-1180">nx_ip_interface_address_get、nx_ip_interface_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="ff631-1181">nx_ip_interface_attach、nx_ip_interface_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="ff631-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="ff631-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="ff631-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="ff631-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="ff631-1184">生パケットの送受信を無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-1185">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1186">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1186">Description</span></span>

<span data-ttu-id="ff631-1187">このサービスを使用すると、この IP インスタンスの生 IP パケットの送信と受信が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="ff631-1188">生パケットのサービスが以前に有効になっていて、生パケットが受信キューに存在する場合、受信済みの生パケットはすべてこのサービスによって解放されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1189">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1189">Parameters</span></span>

- <span data-ttu-id="ff631-1190">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1191">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1191">Return Values</span></span>

- <span data-ttu-id="ff631-1192">**NX_SUCCESS** (0x00) IP 生パケットの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="ff631-1193">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1194">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1195">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1195">Allowed From</span></span>

<span data-ttu-id="ff631-1196">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1197">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1197">Preemption Possible</span></span>

<span data-ttu-id="ff631-1198">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1199">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1200">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1200">See Also</span></span>

- <span data-ttu-id="ff631-1201">nx_ip_raw_packet_enable、nx_ip_raw_packet_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="ff631-1202">nx_ip_raw_packet_send、nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="ff631-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="ff631-1204">生パケットの処理を有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-1205">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1206">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1206">Description</span></span>

<span data-ttu-id="ff631-1207">このサービスを使用すると、この IP インスタンスの生 IP パケットの送信と受信が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="ff631-1208">着信 TCP、UDP、ICMP、および IGMP パケットは引き続き NetX によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="ff631-1209">上位層プロトコルの種類が不明なパケットは、生パケット受信ルーチンによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1210">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1210">Parameters</span></span>

- <span data-ttu-id="ff631-1211">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1212">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1212">Return Values</span></span>

- <span data-ttu-id="ff631-1213">**NX_SUCCESS** (0x00) IP 生パケットの有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="ff631-1214">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1215">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1216">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1216">Allowed From</span></span>

<span data-ttu-id="ff631-1217">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1218">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1218">Preemption Possible</span></span>

<span data-ttu-id="ff631-1219">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1220">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1221">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1221">See Also</span></span>

- <span data-ttu-id="ff631-1222">nx_ip_raw_packet_disable、nx_ip_raw_packet_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="ff631-1223">nx_ip_raw_packet_send、nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="ff631-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="ff631-1225">指定されたネットワーク インターフェイスを経由して生 IP パケットを送信します</span><span class="sxs-lookup"><span data-stu-id="ff631-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1226">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="ff631-1227">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1227">Description</span></span>

<span data-ttu-id="ff631-1228">このサービスを使用すると、指定したローカル IP アドレスが発信元アドレスとして使用され、関連付けられているネットワーク インターフェイスを経由して、宛先 IP アドレスに生 IP パケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="ff631-1229">このルーチンはすぐに戻るため、IP パケットが実際に送信されたかどうかはわからないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="ff631-1230">このネットワーク ドライバーは、送信が完了したときにパケットを開放する役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="ff631-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="ff631-1231">このサービスは、パケットが実際に送信されたかどうかを知る方法がないという点で、他のサービスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="ff631-1232">パケットはインターネット上で失われている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="ff631-1233">*生 IP 処理を有効にする必要があることにご注意ください。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="ff631-1234">*このサービスは、アプリケーションが生の IP パケットを指定した物理インターフェイスから送信することを許可する点を除けば、\*\*nx_ip_raw_packet_send*\* と似ています。\*</span><span class="sxs-lookup"><span data-stu-id="ff631-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1235">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1235">Parameters</span></span>

- <span data-ttu-id="ff631-1236">**ip_ptr** 以前に作成された IP タスクを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="ff631-1237">**packet_ptr** 送信するパケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="ff631-1238">**destination_ip** パケットを送信する IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="ff631-1239">**address_index** パケットを送信するインターフェイスのアドレスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="ff631-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="ff631-1240">**type_of_service** パケットのサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="ff631-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1241">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1241">Return Values</span></span>

- <span data-ttu-id="ff631-1242">**NX_SUCCESS** (0x00) パケットが正常に転送されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="ff631-1243">**NX_IP_ADDRESS_ERROR** (0x21) 使用可能な適切な送信インターフェイスがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="ff631-1244">**NX_NOT_ENABLED** (0x14) 生 IP パケット処理が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="ff631-1245">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1246">**NX_PTR_ERROR** (0x07) ポインター入力が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="ff631-1247">**NX_OPTION_ERROR** (0x0A) 指定されたサービスの種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="ff631-1248">**NX_OVERFLOW** (0x03) パケットのプリペンド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="ff631-1249">**NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="ff631-1250">**NX_INVALID_INTERFACE** (0x4C) 指定されたインターフェイス インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1251">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1251">Allowed From</span></span>

<span data-ttu-id="ff631-1252">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1253">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1253">Preemption Possible</span></span>

<span data-ttu-id="ff631-1254">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1255">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1256">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1256">See Also</span></span>

- <span data-ttu-id="ff631-1257">nx_ip_raw_packet_disable、nx_ip_raw_packet_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="ff631-1258">nx_ip_raw_packet_receive、nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="ff631-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="ff631-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="ff631-1260">生 IP パケットを受信します</span><span class="sxs-lookup"><span data-stu-id="ff631-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1261">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1262">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1262">Description</span></span>

<span data-ttu-id="ff631-1263">このサービスを使用すると、指定した IP インスタンスから生 IP パケットを受信できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="ff631-1264">生パケット受信キューに IP パケットがある場合、最初の (最も古い) パケットが呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="ff631-1265">それ以外の場合、使用可能なパケットがない場合は、待機オプションの指定に従って呼び出し元が中断される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="ff631-1266">*NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1267">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1267">Parameters</span></span>

- <span data-ttu-id="ff631-1268">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1269">**packet_ptr** 受信した生 IP パケットを格納するポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="ff631-1270">**wait_option** 使用可能な生 IP パケットがない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="ff631-1271">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1272">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1274">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1275">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1275">Return Values</span></span>

- <span data-ttu-id="ff631-1276">**NX_SUCCESS** (0x00) IP 生パケットの受信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="ff631-1277">**NX_NO_PACKET** (0x01) 使用可能なパケットがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="ff631-1278">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-1279">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-1280">**NX_PTR_ERROR** (0x07) IP またはパケットの戻りポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="ff631-1281">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1282">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1282">Allowed From</span></span>

<span data-ttu-id="ff631-1283">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1284">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1284">Preemption Possible</span></span>

<span data-ttu-id="ff631-1285">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1286">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1287">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1287">See Also</span></span>

- <span data-ttu-id="ff631-1288">nx_ip_raw_packet_disable、nx_ip_raw_packet_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="ff631-1289">nx_ip_raw_packet_send、nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="ff631-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="ff631-1291">生 IP パケットを送信します</span><span class="sxs-lookup"><span data-stu-id="ff631-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1292">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="ff631-1293">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1293">Description</span></span>

<span data-ttu-id="ff631-1294">このサービスを使用すると、宛先 IP アドレスに生の IP パケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="ff631-1295">このルーチンはすぐに戻るため、IP パケットが実際に送信されたかどうかはわからないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="ff631-1296">このネットワーク ドライバーは、送信が完了したときにパケットを開放する役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="ff631-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="ff631-1297">マルチホーム システムの場合、NetX はこの宛先 IP アドレスを使用して適切なネットワーク インターフェイスを検索し、発信元アドレスとしてこのインターフェイスの IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="ff631-1298">宛先 IP アドレスがブロードキャストまたはマルチキャストの場合は、最初の有効なインターフェイスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="ff631-1299">この場合、アプリケーションでは ***nx_ip_raw_packet_interface_send*** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="ff631-1300">*エラーが返されない限り、アプリケーションでこの呼び出しの後にパケットを開放することはできません。これを行うと、送信後にネットワーク ドライバーがパケットを解放するため、予期しない結果が発生します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1301">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1301">Parameters</span></span>

- <span data-ttu-id="ff631-1302">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1303">**packet_ptr** 送信する生 IP パケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="ff631-1304">**destination_ip** 宛先 IP アドレス。特定のホスト IP アドレス、ネットワーク ブロードキャスト、内部ループバック、またはマルチキャスト アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="ff631-1305">**type_of_service** 送信のためのサービスの種類を定義します。有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ff631-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="ff631-1306">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="ff631-1307">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="ff631-1308">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="ff631-1309">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="ff631-1310">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-1311">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1311">Return Values</span></span>

- <span data-ttu-id="ff631-1312">**NX_SUCCESS** (0x00) IP 生パケットの送信開始に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="ff631-1313">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-1314">**NX_NOT_ENABLED** (0x14) 生 IP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="ff631-1315">**NX_OPTION_ERROR** (0x0A) サービスの種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="ff631-1316">**NX_UNDERFLOW** (0x02) パケットの先頭に IP ヘッダーを付加するのに十分な空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="ff631-1317">**NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="ff631-1318">**NX_PTR_ERROR** (0x07) IP またはパケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="ff631-1319">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1320">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1320">Allowed From</span></span>

<span data-ttu-id="ff631-1321">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1322">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1322">Preemption Possible</span></span>

<span data-ttu-id="ff631-1323">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1324">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1325">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1325">See Also</span></span>

- <span data-ttu-id="ff631-1326">nx_ip_raw_packet_disable、nx_ip_raw_packet_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="ff631-1327">nx_ip_raw_packet_receive、nx_ip_raw_packet_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="ff631-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="ff631-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="ff631-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="ff631-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="ff631-1330">ルーティング テーブルに静的ルートを追加します</span><span class="sxs-lookup"><span data-stu-id="ff631-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1331">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="ff631-1332">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1332">Description</span></span>

<span data-ttu-id="ff631-1333">このサービスを使用すると、静的ルーティング テーブルにエントリが追加されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="ff631-1334">*next_hop* アドレスは、いずれかのローカル ネットワーク デバイスから直接アクセスできる必要があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="ff631-1335">*次の点にご注意ください。ip_ptr は、有効な NetX IP 構造体をポイントする必要があります。また、NetX ライブラリは、このサービスを使用するために NX_ENABLE_IP_STATIC_ROUTING を定義して構築される必要があります。既定で NetX は、NX_ENABLE_IP_STATIC_ROUTING が定義されていない状態で構築されます*。</span><span class="sxs-lookup"><span data-stu-id="ff631-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1336">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1336">Parameters</span></span>

- <span data-ttu-id="ff631-1337">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1338">**network_address** ターゲット ネットワーク アドレス (ホストのバイト順)</span><span class="sxs-lookup"><span data-stu-id="ff631-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="ff631-1339">**net_mask** ターゲット ネットワーク マスク (ホストのバイト順)</span><span class="sxs-lookup"><span data-stu-id="ff631-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="ff631-1340">**next_hop** ターゲット ネットワークのネクスト ホップ アドレス (ホストのバイト順)</span><span class="sxs-lookup"><span data-stu-id="ff631-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1341">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1341">Return Values</span></span>

- <span data-ttu-id="ff631-1342">**NX_SUCCESS** (0x00) 静的ルーティング テーブルにエントリが追加されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="ff631-1343">**NX_OVERFLOW** (0x03) 静的ルーティング テーブルがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="ff631-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="ff631-1344">**NX_NOT_SUPPORTED** (0x4B) この機能はコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="ff631-1345">**NX_IP_ADDRESS_ERROR** (0x21) ネクスト ホップにローカル インターフェイス経由で直接アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="ff631-1346">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1347">**NX_PTR_ERROR** (0x07) ip_ptr ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1348">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1348">Allowed From</span></span>

<span data-ttu-id="ff631-1349">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1350">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1350">Preemption Possible</span></span>

<span data-ttu-id="ff631-1351">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1352">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1353">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1353">See Also</span></span>

- <span data-ttu-id="ff631-1354">nx_ip_gateway_address_set、nx_ip_info_get、nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="ff631-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="ff631-1356">静的ルートをルーティング テーブルから削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1357">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="ff631-1358">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1358">Description</span></span>

<span data-ttu-id="ff631-1359">このサービスを使用すると、静的ルーティング テーブルからエントリが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="ff631-1360">*次の点にご注意ください。ip_ptr は、有効な NetX IP 構造体をポイントする必要があります。また、NetX ライブラリは、このサービスを使用するために NX_ENABLE_IP_STATIC_ROUTING を定義して構築される必要があります。既定で NetX は、NX_ENABLE_IP_STATIC_ROUTING が定義されていない状態で構築されます*。</span><span class="sxs-lookup"><span data-stu-id="ff631-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1361">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1361">Parameters</span></span>

- <span data-ttu-id="ff631-1362">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1363">**network_address** ターゲット ネットワーク アドレス (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="ff631-1364">**net_mask** ターゲット ネットワーク マスク (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1365">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1365">Allowed From</span></span>

<span data-ttu-id="ff631-1366">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1367">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1367">Preemption Possible</span></span>

<span data-ttu-id="ff631-1368">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1369">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1370">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1370">See Also</span></span>

- <span data-ttu-id="ff631-1371">nx_ip_gateway_address_set、nx_ip_info_get、nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="ff631-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="ff631-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="ff631-1372">nx_ip_status_check</span></span>

<span data-ttu-id="ff631-1373">IP インスタンスの状態を確認します</span><span class="sxs-lookup"><span data-stu-id="ff631-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1374">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1375">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1375">Description</span></span>

<span data-ttu-id="ff631-1376">このサービスを使用すると、以前に作成された IP インスタンスのプライマリ ネットワーク インターフェイスの指定した状態の確認が行われ、必要に応じて待機します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="ff631-1377">セカンダリ インターフェイスの状態を取得するには、アプリケーションでサービス ***nx_ip_interface_status_check*** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1378">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1378">Parameters</span></span>

- <span data-ttu-id="ff631-1379">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1380">**needed_status** 要求された IP 状態。ビットマップ形式で次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="ff631-1381">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="ff631-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="ff631-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="ff631-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="ff631-1383">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="ff631-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="ff631-1384">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="ff631-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="ff631-1385">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="ff631-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="ff631-1386">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="ff631-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="ff631-1387">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="ff631-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="ff631-1388">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="ff631-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="ff631-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="ff631-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="ff631-1390">**actual_status** 設定された実際のビットの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="ff631-1391">**wait_option** 要求されたステータス ビットが使用できない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="ff631-1392">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1393">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1395">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1396">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1396">Return Values</span></span>

- <span data-ttu-id="ff631-1397">**NX_SUCCESS** (0x00) IP 状態の確認に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="ff631-1398">**NX_NOT_SUCCESSFUL** (0x43) 状態要求が、指定されたタイムアウト時間内に満たされませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="ff631-1399">**NX_PTR_ERROR** (0x07) IP ポインターが無効であるか、無効になったか、または実際の状態ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="ff631-1400">**NX_OPTION_ERROR** (0x0a) 必要な状態オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="ff631-1401">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1402">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1402">Allowed From</span></span>

<span data-ttu-id="ff631-1403">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1404">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1404">Preemption Possible</span></span>

<span data-ttu-id="ff631-1405">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1406">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1407">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1407">See Also</span></span>

- <span data-ttu-id="ff631-1408">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-1409">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-1410">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-1411">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-1412">nx_ip_fragment_enable、nx_ip_info_get、nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="ff631-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="ff631-1413">nx_packet_allocate</span></span>

<span data-ttu-id="ff631-1414">指定されたプールからパケットを割り当てます</span><span class="sxs-lookup"><span data-stu-id="ff631-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1415">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1416">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1416">Description</span></span>

<span data-ttu-id="ff631-1417">このサービスを使用すると、指定したプールからパケットが割り当てられ、指定したパケットの種類に従ってパケット内のプリペンド ポインターが調整されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="ff631-1418">使用可能なパケットがない場合は、指定された待機オプションに従ってサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1419">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1419">Parameters</span></span>

- <span data-ttu-id="ff631-1420">**pool_ptr** 以前に作成されたパケット プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="ff631-1421">**packet_ptr** 割り当てられたパケット ポインターのポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="ff631-1422">**packet_type** 要求されたパケットの種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="ff631-1423">サポートされているパケットの種類の一覧については、第 3 章の 49 ページにある「パケット プール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff631-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="ff631-1424">**wait_option** パケット プールに使用可能なパケットがない場合の待機時間をティックで定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="ff631-1425">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1426">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1428">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1429">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1429">Return Values</span></span>

- <span data-ttu-id="ff631-1430">**NX_SUCCESS** (0x00) パケットの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="ff631-1431">**NX_NO_PACKET** (0x01) 使用可能なパケットがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="ff631-1432">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-1433">**NX_INVALID_PARAMETERS** (0x4D) パケット サイズはプロトコルをサポートできません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="ff631-1434">**NX_OPTION_ERROR** (0x0A) パケットの種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="ff631-1435">**NX_PTR_ERROR** (0x07) プールまたはパケットの戻りポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="ff631-1436">**NX_CALLER_ERROR** (0x11) スレッド以外からの待機オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1437">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1437">Allowed From</span></span>

<span data-ttu-id="ff631-1438">初期化、スレッド、タイマー、ISR (アプリケーション ネットワーク ドライバー)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="ff631-1439">ISR またはタイマー コンテキストで使用する場合、待機オプションは NX_NO_WAIT である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1440">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1440">Preemption Possible</span></span>

<span data-ttu-id="ff631-1441">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1442">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1443">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1443">See Also</span></span>

- <span data-ttu-id="ff631-1444">nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1445">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1446">nx_packet_length_get、nx_packet_pool_create、nx_packet_pool_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="ff631-1447">nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="ff631-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="ff631-1449">nx_packet_copy</span></span>

<span data-ttu-id="ff631-1450">パケットをコピーします</span><span class="sxs-lookup"><span data-stu-id="ff631-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1451">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1452">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1452">Description</span></span>

<span data-ttu-id="ff631-1453">このサービスを使用すると、指定したパケットの情報が、指定したパケット プールから割り当てられている 1 つ以上の新しいパケットにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="ff631-1454">成功した場合、新しいパケットを指すポインターが、**new_packet_ptr** よってポイントされている宛先に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1455">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1455">Parameters</span></span>

- <span data-ttu-id="ff631-1456">**packet_ptr** 発信元パケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="ff631-1457">**new_packet_ptr** パケットの新しいコピーを指すポインターを返すべき宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="ff631-1458">**pool_ptr** そのコピーのために 1 つ以上のパケットを割り当てるのに使用される、以前に作成されたパケット プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="ff631-1459">**wait_option** 使用可能なパケットがない場合にサービスが待機する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="ff631-1460">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1461">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1463">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1464">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1464">Return Values</span></span>
- <span data-ttu-id="ff631-1465">**NX_SUCCESS** (0x00) パケットのコピーに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="ff631-1466">**NX_NO_PACKET** (0x01) コピーに使用できるパケットがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="ff631-1467">**NX_INVALID_PACKET** (0x12) 発信元パケットが空であるか、コピーに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="ff631-1468">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-1469">**NX_INVALID_PARAMETERS** (0x4D) パケット サイズはプロトコルをサポートできません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="ff631-1470">**NX_PTR_ERROR** (0x07) プール、パケット、または宛先のポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="ff631-1471">**NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="ff631-1472">**NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="ff631-1473">**NX_CALLER_ERROR** (0x11) 待機オプションが初期化または ISR で指定されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1474">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1474">Allowed From</span></span>

<span data-ttu-id="ff631-1475">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1476">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1476">Preemption Possible</span></span>

<span data-ttu-id="ff631-1477">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1478">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1479">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1479">See Also</span></span>

- <span data-ttu-id="ff631-1480">nx_packet_allocate、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1481">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1482">nx_packet_length_get、nx_packet_pool_create、nx_packet_pool_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="ff631-1483">nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="ff631-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="ff631-1485">nx_packet_data_append</span></span>

<span data-ttu-id="ff631-1486">パケットの末尾にデータを追加します</span><span class="sxs-lookup"><span data-stu-id="ff631-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1487">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1488">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1488">Description</span></span>

<span data-ttu-id="ff631-1489">このサービスを使用すると、指定したパケットの末尾にデータが追加されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="ff631-1490">指定されたデータ領域がパケットにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="ff631-1491">使用可能なメモリが不足していて、チェーン化されたパケット機能が有効になっている場合、要求を満たすために 1 つ以上のパケットが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="ff631-1492">チェーン化されたパケット機能が有効になっていない場合は、*NX_SIZE_ERROR* が返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1493">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1493">Parameters</span></span>

- <span data-ttu-id="ff631-1494">**packet_ptr** パケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="ff631-1495">**data_start** パケットに追加するユーザーのデータ領域の先頭を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="ff631-1496">**data_size** ユーザーのデータ領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ff631-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="ff631-1497">**pool_ptr** 現在のパケットに十分な空き領域がない場合に、別のパケットの割り当て元となるパケット プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="ff631-1498">**wait_option** 使用可能なパケットがない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="ff631-1499">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1500">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1502">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1503">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1503">Return Values</span></span>

- <span data-ttu-id="ff631-1504">**NX_SUCCESS** (0x00) パケットの追加に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="ff631-1505">**NX_NO_PACKET** (0x01) 使用可能なパケットがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="ff631-1506">**NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="ff631-1507">**NX_INVALID_PARAMETERS** (0x4D) パケット サイズはプロトコルをサポートできません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="ff631-1508">**NX_UNDERFLOW** (0x02) プリペンド ポインターがペイロードの先頭未満です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="ff631-1509">**NX_OVERFLOW** (0x03) 追加ポインターがペイロードの末尾を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="ff631-1510">**NX_PTR_ERROR** (0x07) プール、パケット、またはデータ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="ff631-1511">**NX_SIZE_ERROR** (0x09) データ サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="ff631-1512">**NX_CALLER_ERROR** (0x11) スレッド以外からの待機オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1513">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1513">Allowed From</span></span>

<span data-ttu-id="ff631-1514">初期化、スレッド、タイマー、ISR (アプリケーション ネットワーク ドライバー)</span><span class="sxs-lookup"><span data-stu-id="ff631-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1515">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1515">Preemption Possible</span></span>

<span data-ttu-id="ff631-1516">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1517">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="ff631-1518">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1518">See Also</span></span>

- <span data-ttu-id="ff631-1519">nx_packet_allocate、nx_packet_copy、nx_packet_data_extract_offset、</span><span class="sxs-lookup"><span data-stu-id="ff631-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="ff631-1520">nx_packet_data_retrieve、nx_packet_length_get、nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="ff631-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="ff631-1521">nx_packet_pool_delete、nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="ff631-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="ff631-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="ff631-1524">オフセット経由でパケットからデータを抽出します</span><span class="sxs-lookup"><span data-stu-id="ff631-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1525">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="ff631-1526">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1526">Description</span></span>

<span data-ttu-id="ff631-1527">このサービスを使用すると、指定したサイズ (バイト単位) のパケット プリペンド ポインターからの指定したオフセットを開始位置とする NetX パケット (またはパケット チェーン) から、指定したバッファーにデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="ff631-1528">実際にコピーされたバイト数が *bytes_copied* に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="ff631-1529">このサービスでは、パケットからデータは削除されません。また、プリペンド ポインターやその他の内部状態情報も調整されません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1530">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1530">Parameters</span></span>

- <span data-ttu-id="ff631-1531">**packet_ptr** 抽出するパケットを指すポインター</span><span class="sxs-lookup"><span data-stu-id="ff631-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="ff631-1532">**offset** 現在のプリペンド ポインターからのオフセット。</span><span class="sxs-lookup"><span data-stu-id="ff631-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="ff631-1533">**buffer_start** 保存バッファーの先頭を指すポインター</span><span class="sxs-lookup"><span data-stu-id="ff631-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="ff631-1534">**buffer_length** コピーするバイト数</span><span class="sxs-lookup"><span data-stu-id="ff631-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="ff631-1535">**bytes_copied** 実際にコピーされたバイト数</span><span class="sxs-lookup"><span data-stu-id="ff631-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1536">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1536">Return Values</span></span>

- <span data-ttu-id="ff631-1537">**NX_SUCCESS** (0x00) パケットのコピーに成功しました</span><span class="sxs-lookup"><span data-stu-id="ff631-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="ff631-1538">**NX_PACKET_OFFSET_ERROR** (0x53) 無効なオフセット値が指定されました</span><span class="sxs-lookup"><span data-stu-id="ff631-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="ff631-1539">**NX_PTR_ERROR** (0x07) パケット ポインターまたはバッファー ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1540">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1540">Allowed From</span></span>

<span data-ttu-id="ff631-1541">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1542">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1542">Preemption Possible</span></span>

<span data-ttu-id="ff631-1543">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1544">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1545">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1545">See Also</span></span>

- <span data-ttu-id="ff631-1546">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1547">nx_packet_data_retrieve、nx_packet_length_get、nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="ff631-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="ff631-1548">nx_packet_pool_delete、nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="ff631-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="ff631-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="ff631-1551">パケットからデータを取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1552">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="ff631-1553">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1553">Description</span></span>

<span data-ttu-id="ff631-1554">このサービスを使用すると、指定したパケットから指定したバッファーにデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="ff631-1555">コピーされた実際のバイト数は、**bytes_copied** から指されている宛先に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="ff631-1556">このサービスでは、パケットの内部状態は変更されないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="ff631-1557">取得されるデータは、パケットで引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="ff631-1558">*コピー先のバッファーは、パケットの内容を保持するのに十分な大きさである必要があります。十分でない場合、メモリが破損し、予期しない結果が発生します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1559">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1559">Parameters</span></span>

- <span data-ttu-id="ff631-1560">**packet_ptr** 発信元パケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="ff631-1561">**buffer_start** バッファー領域の先頭を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="ff631-1562">**bytes_copied** コピーされたバイト数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1563">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1563">Return Values</span></span>

- <span data-ttu-id="ff631-1564">**NX_SUCCESS** (0x00) パケット データの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="ff631-1565">**NX_INVALID_PACKET** (0x12) パケットが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="ff631-1566">**NX_PTR_ERROR** (0x07) パケット、バッファーの先頭、またはコピーされたバイト数のポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1567">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1567">Allowed From</span></span>

<span data-ttu-id="ff631-1568">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1569">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1569">Preemption Possible</span></span>

<span data-ttu-id="ff631-1570">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1571">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1572">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1572">See Also</span></span>

- <span data-ttu-id="ff631-1573">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1574">nx_packet_data_extract_offset、nx_packet_length_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="ff631-1575">nx_packet_pool_create、nx_packet_pool_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="ff631-1576">nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="ff631-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1578">nx_packet_length_get</span></span>

<span data-ttu-id="ff631-1579">パケット データの長さを取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1580">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="ff631-1581">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1581">Description</span></span>

<span data-ttu-id="ff631-1582">このサービスを使用すると、指定したパケット内のデータの長さが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1583">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1583">Parameters</span></span>

- <span data-ttu-id="ff631-1584">**packet_ptr** パケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="ff631-1585">**length** パケットの長さの宛先。</span><span class="sxs-lookup"><span data-stu-id="ff631-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1586">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1586">Allowed From</span></span>

<span data-ttu-id="ff631-1587">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1588">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1588">Preemption Possible</span></span>

<span data-ttu-id="ff631-1589">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1590">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1591">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1591">See Also</span></span>

- <span data-ttu-id="ff631-1592">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1593">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1594">nx_packet_pool_create、nx_packet_pool_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="ff631-1595">nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="ff631-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="ff631-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="ff631-1598">指定されたメモリ領域にパケット プールを作成します</span><span class="sxs-lookup"><span data-stu-id="ff631-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1599">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="ff631-1600">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1600">Description</span></span>

<span data-ttu-id="ff631-1601">このサービスを使用すると、ユーザーが指定したメモリ領域に、指定したパケット サイズのパケット プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1602">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1602">Parameters</span></span>

- <span data-ttu-id="ff631-1603">**pool_ptr** パケット プール制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="ff631-1604">**name** パケット プールのアプリケーションの名前を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="ff631-1605">**payload_size** プール内の各パケットのバイト数。</span><span class="sxs-lookup"><span data-stu-id="ff631-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="ff631-1606">この値は、40 バイト以上である必要があり、4 で割り切れなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="ff631-1607">**memory_ptr** パケット プールを配置するメモリ領域を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="ff631-1608">このポインターは、ULONG 境界上に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="ff631-1609">**memory_size** プールのメモリ領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ff631-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1610">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1610">Return Values</span></span>

- <span data-ttu-id="ff631-1611">**NX_SUCCESS** (0x00) パケット プールの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="ff631-1612">**NX_PTR_ERROR** (0x07) プールまたはメモリ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="ff631-1613">**NX_SIZE_ERROR** (0x09) ブロックまたはメモリのサイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="ff631-1614">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1615">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1615">Allowed From</span></span>

<span data-ttu-id="ff631-1616">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1617">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1617">Preemption Possible</span></span>

<span data-ttu-id="ff631-1618">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1619">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1620">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1620">See Also</span></span>

- <span data-ttu-id="ff631-1621">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1622">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1623">nx_packet_length_get、nx_packet_pool_delete、nx_packet_pool_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="ff631-1624">nx_packet_release、nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="ff631-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="ff631-1626">以前に作成されたパケット プールを削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1627">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1628">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1628">Description</span></span>

<span data-ttu-id="ff631-1629">このサービスを使用すると、以前に作成されたパケット プールが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="ff631-1630">NetX は、パケット プール内のパケットで現在中断されているすべてのスレッドを確認し、その中断をクリアします。</span><span class="sxs-lookup"><span data-stu-id="ff631-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1631">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1631">Parameters</span></span>

- <span data-ttu-id="ff631-1632">**pool_ptr** パケット プール制御ブロック ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1633">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1633">Return Values</span></span>

- <span data-ttu-id="ff631-1634">**NX_SUCCESS** (0x00) パケット プールの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="ff631-1635">**NX_PTR_ERROR** (0x07) プール ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="ff631-1636">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1637">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1637">Allowed From</span></span>

<span data-ttu-id="ff631-1638">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1639">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1639">Preemption Possible</span></span>

<span data-ttu-id="ff631-1640">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1641">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1642">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1642">See Also</span></span>

- <span data-ttu-id="ff631-1643">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1644">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1645">nx_packet_length_get、nx_packet_pool_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="ff631-1646">nx_packet_pool_info_get、nx_packet_release、</span><span class="sxs-lookup"><span data-stu-id="ff631-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="ff631-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="ff631-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="ff631-1649">パケット プールに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1650">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="ff631-1651">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1651">Description</span></span>

<span data-ttu-id="ff631-1652">このサービスを使用すると、指定したパケット プールに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="ff631-1653">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1654">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1654">Parameters</span></span>

- <span data-ttu-id="ff631-1655">**pool_ptr** 以前に作成されたパケット プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="ff631-1656">**total_packets** プール内のパケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="ff631-1657">**free_packets** 現在解放されているパケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="ff631-1658">**empty_pool_requests** プールが空だった場合の割り当て要求の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="ff631-1659">**empty_pool_suspensions** 空のプールによる中断の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="ff631-1660">**invalid_packet_releases** 無効なパケット リリースの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1661">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1661">Return Values</span></span>

- <span data-ttu-id="ff631-1662">**NX_SUCCESS** (0x00) パケット プール情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="ff631-1663">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1664">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1665">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1665">Allowed From</span></span>

<span data-ttu-id="ff631-1666">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1667">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1667">Preemption Possible</span></span>

<span data-ttu-id="ff631-1668">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1669">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1670">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1670">See Also</span></span>

- <span data-ttu-id="ff631-1671">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1672">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1673">nx_packet_length_get、nx_packet_pool_create、nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="ff631-1674">nx_packet_release、nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="ff631-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1675">nx_packet_release</span></span>

<span data-ttu-id="ff631-1676">以前に割り当てられたパケットを解放します</span><span class="sxs-lookup"><span data-stu-id="ff631-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1677">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1678">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1678">Description</span></span>

<span data-ttu-id="ff631-1679">このサービスを使用すると、パケットが解放されます。これには、指定したパケットにチェーンされている追加のパケットも含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="ff631-1680">パケット割り当てで別のスレッドがブロックされている場合は、そのスレッドにこのパケットが与えられて、再開されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="ff631-1681">*このアプリケーションでは、パケットが複数回解放されないようにする必要があります。パケットが複数回解放されると、予期しない結果が発生します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1682">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1682">Parameters</span></span>

- <span data-ttu-id="ff631-1683">**packet_ptr** パケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-1684">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1684">Return Values</span></span>
- <span data-ttu-id="ff631-1685">**NX_SUCCESS** (0x00) パケットの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="ff631-1686">**NX_PTR_ERROR** (0x07) パケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="ff631-1687">**NX_UNDERFLOW** (0x02) プリペンド ポインターがペイロードの先頭未満です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="ff631-1688">**NX_OVERFLOW** (0x03) 追加ポインターがペイロードの末尾を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1689">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1689">Allowed From</span></span>

<span data-ttu-id="ff631-1690">初期化、スレッド、タイマー、ISR (アプリケーション ネットワーク ドライバー)</span><span class="sxs-lookup"><span data-stu-id="ff631-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1691">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1691">Preemption Possible</span></span>

<span data-ttu-id="ff631-1692">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1693">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1694">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1694">See Also</span></span>

- <span data-ttu-id="ff631-1695">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1696">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1697">nx_packet_length_get、nx_packet_pool_create、nx_packet_pool_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="ff631-1698">nx_packet_pool_info_get、nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="ff631-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="ff631-1700">送信済みパケットを解放します</span><span class="sxs-lookup"><span data-stu-id="ff631-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1701">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1702">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1702">Description</span></span>

<span data-ttu-id="ff631-1703">TCP 以外のパケットの場合、このサービスによって送信済みパケットが解放されます。これには、指定されたパケットにチェーンされている追加のパケットも含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="ff631-1704">パケット割り当てで別のスレッドがブロックされている場合は、そのスレッドにこのパケットが与えられて、再開されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="ff631-1705">送信済みの TCP パケットの場合、パケットは送信中としてマークされますが、パケットの受信が確認されるまでは解放されません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="ff631-1706">通常、このサービスはパケットが送信された後にアプリケーションのネットワーク ドライバーから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="ff631-1707">*ネットワーク ドライバーは、このサービスを呼び出す前に、物理メディア ヘッダーを削除し、パケットの長さを調整する必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1708">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1708">Parameters</span></span>

- <span data-ttu-id="ff631-1709">**packet_ptr** パケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1710">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1710">Return Values</span></span>

- <span data-ttu-id="ff631-1711">**NX_SUCCESS** (0x00) 送信パケットの解放に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="ff631-1712">**NX_PTR_ERROR** (0x07) パケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="ff631-1713">**NX_UNDERFLOW** (0x02) プリペンド ポインターがペイロードの先頭未満です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="ff631-1714">**NX_OVERFLOW** (0x03) 追加ポインターがペイロードの末尾を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1715">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1715">Allowed From</span></span>

<span data-ttu-id="ff631-1716">初期化、スレッド、タイマー、アプリケーション ネットワーク ドライバー (ISR を含む)</span><span class="sxs-lookup"><span data-stu-id="ff631-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1717">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1717">Preemption Possible</span></span>

<span data-ttu-id="ff631-1718">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1719">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1720">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1720">See Also</span></span>

- <span data-ttu-id="ff631-1721">nx_packet_allocate、nx_packet_copy、nx_packet_data_append、</span><span class="sxs-lookup"><span data-stu-id="ff631-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="ff631-1722">nx_packet_data_extract_offset、nx_packet_data_retrieve、</span><span class="sxs-lookup"><span data-stu-id="ff631-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="ff631-1723">nx_packet_length_get、nx_packet_pool_create、nx_packet_pool_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="ff631-1724">nx_packet_pool_info_get、nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="ff631-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="ff631-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="ff631-1725">nx_rarp_disable</span></span>

<span data-ttu-id="ff631-1726">逆アドレス解決プロトコル (RARP) を無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1727">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1728">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1728">Description</span></span>

<span data-ttu-id="ff631-1729">このサービスを使用すると、特定の IP インスタンスの NetX の RARP コンポーネントが無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="ff631-1730">マルチホーム システムの場合、このサービスはすべてのインターフェイスで RARP を無効にします。</span><span class="sxs-lookup"><span data-stu-id="ff631-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1731">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1731">Parameters</span></span>

- <span data-ttu-id="ff631-1732">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1733">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1733">Return Values</span></span>

- <span data-ttu-id="ff631-1734">**NX_SUCCESS** (0x00) RARP の無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="ff631-1735">**NX_NOT_ENABLED** (0x14) RARP が有効になっていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="ff631-1736">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1737">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1738">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1738">Allowed From</span></span>

<span data-ttu-id="ff631-1739">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1740">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1740">Preemption Possible</span></span>

<span data-ttu-id="ff631-1741">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1742">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1743">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1743">See Also</span></span>

- <span data-ttu-id="ff631-1744">nx_rarp_enable、nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="ff631-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-1745">nx_rarp_enable</span></span>

<span data-ttu-id="ff631-1746">逆アドレス解決プロトコル (RARP) を有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1747">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1748">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1748">Description</span></span>

<span data-ttu-id="ff631-1749">このサービスを使用すると、特定の IP インスタンスの NetX の RARP コンポーネントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="ff631-1750">RARP コンポーネントは、接続されているすべてのネットワーク インターフェイスから IP アドレスがゼロであるものを検索します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="ff631-1751">IP アドレスがゼロであることは、そのインターフェイスに IP アドレスがまだ割り当てられていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="ff631-1752">RARP は、そのインターフェイスで RARP プロセスを有効にすることにより、IP アドレスの解決を試みます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1753">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1753">Parameters</span></span>

- <span data-ttu-id="ff631-1754">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1755">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1755">Return Values</span></span>

- <span data-ttu-id="ff631-1756">**NX_SUCCESS** (0x00) RARP の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="ff631-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスは既に有効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="ff631-1758">**NX_ALREADY_ENABLED** (0x15) RARP は既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="ff631-1759">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1760">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1761">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1761">Allowed From</span></span>

<span data-ttu-id="ff631-1762">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1763">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1763">Preemption Possible</span></span>

<span data-ttu-id="ff631-1764">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1765">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1766">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1766">See Also</span></span>

- <span data-ttu-id="ff631-1767">nx_rarp_disable、nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="ff631-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="ff631-1769">RARP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1770">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="ff631-1771">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1771">Description</span></span>

<span data-ttu-id="ff631-1772">このサービスを使用すると、指定した IP インスタンスの RARP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="ff631-1773">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1774">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1774">Parameters</span></span>

- <span data-ttu-id="ff631-1775">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1776">**rarp_requests_sent** 送信された RARP 要求の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="ff631-1777">**rarp_responses_received** 受信した RARP 応答の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="ff631-1778">**rarp_invalid_messages** 無効なメッセージの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-1779">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1779">Return Values</span></span>
- <span data-ttu-id="ff631-1780">**NX_SUCCESS** (0x00) RARP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="ff631-1781">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1782">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-1783">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1784">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1784">Allowed From</span></span>

<span data-ttu-id="ff631-1785">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1786">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1786">Preemption Possible</span></span>

<span data-ttu-id="ff631-1787">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1788">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1789">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1789">See Also</span></span>

- <span data-ttu-id="ff631-1790">nx_rarp_disable、nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="ff631-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="ff631-1791">nx_system_initialize</span></span>

<span data-ttu-id="ff631-1792">NetX システムを初期化します</span><span class="sxs-lookup"><span data-stu-id="ff631-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1793">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="ff631-1794">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1794">Description</span></span>

<span data-ttu-id="ff631-1795">このサービスを使用すると、使用に備えて基本的な NetX システム リソースが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="ff631-1796">このサービスは、初期化の実行中に、他のどの NetX 呼び出しが実行されるよりも前にアプリケーションによって呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1797">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1797">Parameters</span></span>

<span data-ttu-id="ff631-1798">None</span><span class="sxs-lookup"><span data-stu-id="ff631-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1799">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1799">Return Values</span></span>

<span data-ttu-id="ff631-1800">None</span><span class="sxs-lookup"><span data-stu-id="ff631-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1801">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1801">Allowed From</span></span>

<span data-ttu-id="ff631-1802">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1803">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1803">Preemption Possible</span></span>

<span data-ttu-id="ff631-1804">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1805">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1806">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1806">See Also</span></span>

- <span data-ttu-id="ff631-1807">nx_ip_address_change_notify、nx_ip_address_get、nx_ip_address_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="ff631-1808">nx_ip_create, nx_ip_delete、nx_ip_driver_direct_command、</span><span class="sxs-lookup"><span data-stu-id="ff631-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="ff631-1809">nx_ip_driver_interface_direct_command、nx_ip_forwarding_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="ff631-1810">nx_ip_forwarding_enable、nx_ip_fragment_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="ff631-1811">nx_ip_fragment_enable、nx_ip_info_get、nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="ff631-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="ff631-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="ff631-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="ff631-1813">TCP ポートにクライアントの TCP ソケットをバインドします</span><span class="sxs-lookup"><span data-stu-id="ff631-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1814">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1815">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1815">Description</span></span>

<span data-ttu-id="ff631-1816">このサービスを使用すると、以前に作成された TCP クライアント ソケットが、指定した TCP ポートにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="ff631-1817">有効な TCP ソケットの範囲は 0 から 0xFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="ff631-1818">指定された TCP ポートが使用できない場合は、指定された待機オプションに従ってサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1819">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1819">Parameters</span></span>

- <span data-ttu-id="ff631-1820">**socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="ff631-1821">**port** バインドするポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="ff631-1822">ポート番号が NX_ANY_PORT (0x0000) の場合、IP インスタンスは次の空きポートを検索し、そのポートをバインドに使用します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="ff631-1823">**wait_option** ポートが既に別のソケットにバインドされている場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="ff631-1824">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1825">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1827">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1828">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1828">Return Values</span></span>

- <span data-ttu-id="ff631-1829">**NX_SUCCESS** (0x00) ソケットのバインドに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="ff631-1830">**NX_ALREADY_BOUND** (0x22) このソケットは既に別の TCP ポートにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="ff631-1831">**NX_PORT_UNAVAILABLE** (0x23) ポートは既に別のソケットにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="ff631-1832">**NX_NO_FREE_PORTS** (0x45) 空きポートがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="ff631-1833">**NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="ff631-1834">**NX_INVALID_PORT** (0x46) ポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="ff631-1835">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-1836">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1837">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1838">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1838">Allowed From</span></span>

<span data-ttu-id="ff631-1839">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1840">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1840">Preemption Possible</span></span>

<span data-ttu-id="ff631-1841">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1842">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1843">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1843">See Also</span></span>

- <span data-ttu-id="ff631-1844">nx_tcp_client_socket_connect、nx_tcp_client_socket_port_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="ff631-1845">nx_tcp_client_socket_unbind、nx_tcp_enable、nx_tcp_free_port_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="ff631-1846">nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-1847">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-1848">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-1849">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-1850">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-1851">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-1852">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="ff631-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="ff631-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="ff631-1855">クライアントの TCP ソケットを接続します</span><span class="sxs-lookup"><span data-stu-id="ff631-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1856">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-1857">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1857">Description</span></span>

<span data-ttu-id="ff631-1858">このサービスを使用すると、以前に作成され、バインドされた TCP クライアント ソケットが、指定したサーバーのポートに接続されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="ff631-1859">有効な TCP サーバー ポートの範囲は 0 から 0xFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="ff631-1860">接続がすぐに完了しない場合、指定された待機オプションに従ってサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1861">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1861">Parameters</span></span>

- <span data-ttu-id="ff631-1862">**socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="ff631-1863">**server_ip** サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="ff631-1864">**server_port** 接続先のサーバー ポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="ff631-1865">**wait_option** 接続を確立している最中のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="ff631-1866">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-1867">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-1869">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1870">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1870">Return Values</span></span>

- <span data-ttu-id="ff631-1871">**NX_SUCCESS** (0x00) ソケットの接続に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="ff631-1872">**NX_NOT_BOUND** (0x24) ソケットがバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="ff631-1873">**NX_NOT_CLOSED** (0x35) ソケットが CLOSED 状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="ff631-1874">**NX_IN_PROGRESS** (0x37) 待機が指定されていないため、接続の試行を実行中です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="ff631-1875">**NX_INVALID_INTERFACE** (0x4C) 指定されたインターフェイスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="ff631-1876">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-1877">**NX_IP_ADDRESS_ERROR** (0x21) サーバー IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="ff631-1878">**NX_INVALID_PORT** (0x46) ポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="ff631-1879">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-1880">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1881">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1882">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1882">Allowed From</span></span>

<span data-ttu-id="ff631-1883">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1884">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1884">Preemption Possible</span></span>

<span data-ttu-id="ff631-1885">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1886">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1887">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1887">See Also</span></span>

- <span data-ttu-id="ff631-1888">nx_tcp_client_socket_bind、nx_tcp_client_socket_port_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="ff631-1889">nx_tcp_client_socket_unbind、nx_tcp_enable、nx_tcp_free_port_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="ff631-1890">nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-1891">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-1892">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-1893">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-1894">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-1895">nx_tcp_socket_info_get、nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ff631-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="ff631-1896">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="ff631-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="ff631-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="ff631-1899">クライアントの TCP ソケットにバインドされているポート番号を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1900">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1901">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1901">Description</span></span>

<span data-ttu-id="ff631-1902">このサービスを使用すると、ソケットに関連付けられているポート番号が取得されます。これは、ソケットのバインド時に NX_ANY_PORT が指定された場合に NetX によって割り当てられたポートを見つけるのに便利です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1903">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1903">Parameters</span></span>

- <span data-ttu-id="ff631-1904">**socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="ff631-1905">**port_ptr** 戻りポート番号の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="ff631-1906">有効なポート番号は、1 から 0xFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1907">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1907">Return Values</span></span>

- <span data-ttu-id="ff631-1908">**NX_SUCCESS** (0x00) ソケットのバインドに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="ff631-1909">**NX_NOT_BOUND** (0x24) このソケットはポートにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="ff631-1910">**NX_PTR_ERROR** (0x07) ソケット ポインターまたはポートの戻りポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="ff631-1911">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1912">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1913">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1913">Allowed From</span></span>

<span data-ttu-id="ff631-1914">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1915">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1915">Preemption Possible</span></span>

<span data-ttu-id="ff631-1916">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1917">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1918">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1918">See Also</span></span>

- <span data-ttu-id="ff631-1919">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-1920">nx_tcp_client_socket_unbind、nx_tcp_enable、nx_tcp_free_port_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="ff631-1921">nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-1922">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-1923">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-1924">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-1925">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-1926">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-1927">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="ff631-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="ff631-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="ff631-1930">TCP クライアント ソケットを TCP ポートからバインド解除します</span><span class="sxs-lookup"><span data-stu-id="ff631-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1931">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1932">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1932">Description</span></span>

<span data-ttu-id="ff631-1933">このサービスを使用すると、TCP クライアント ソケットと TCP ポートとの間のバインドが解放されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="ff631-1934">他のスレッドが同じポート番号に別のソケットをバインドするために待機している場合は、中断されている最初のスレッドがこのポートにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1935">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1935">Parameters</span></span>

- <span data-ttu-id="ff631-1936">**socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1937">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1937">Return Values</span></span>

- <span data-ttu-id="ff631-1938">**NX_SUCCESS** (0x00) ソケットのバインド解除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="ff631-1939">**NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="ff631-1940">**NX_NOT_CLOSED** (0x35) ソケットが切断されていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="ff631-1941">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-1942">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-1943">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1944">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1944">Allowed From</span></span>

<span data-ttu-id="ff631-1945">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1946">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1946">Preemption Possible</span></span>

<span data-ttu-id="ff631-1947">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1948">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1949">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1949">See Also</span></span>

- <span data-ttu-id="ff631-1950">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-1951">nx_tcp_client_socket_port_get、nx_tcp_enable、nx_tcp_free_port_find、</span><span class="sxs-lookup"><span data-stu-id="ff631-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="ff631-1952">nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-1953">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-1954">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-1955">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-1956">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-1957">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-1958">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="ff631-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-1960">nx_tcp_enable</span></span>

<span data-ttu-id="ff631-1961">NetX の TCP コンポーネントを有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1962">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1963">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1963">Description</span></span>

<span data-ttu-id="ff631-1964">このサービスを使用すると、NetX の伝送制御プロトコル (TCP) コンポーネントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="ff631-1965">有効にすると、このアプリケーションで TCP 接続を確立できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff631-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1966">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1966">Parameters</span></span>

- <span data-ttu-id="ff631-1967">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-1968">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-1968">Return Values</span></span>

- <span data-ttu-id="ff631-1969">**NX_SUCCESS** (0x00) TCP の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="ff631-1970">**NX_ALREADY_ENABLED** (0x15) TCP は既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ff631-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="ff631-1971">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-1972">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-1973">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-1973">Allowed From</span></span>

<span data-ttu-id="ff631-1974">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-1975">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-1975">Preemption Possible</span></span>

<span data-ttu-id="ff631-1976">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-1977">例</span><span class="sxs-lookup"><span data-stu-id="ff631-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-1978">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-1978">See Also</span></span>

- <span data-ttu-id="ff631-1979">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-1980">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-1981">nx_tcp_free_port_find、nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-1982">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-1983">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-1984">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-1985">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-1986">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-1987">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="ff631-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="ff631-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="ff631-1990">使用可能な次の TCP ポートを検索します</span><span class="sxs-lookup"><span data-stu-id="ff631-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-1991">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-1992">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-1992">Description</span></span>

<span data-ttu-id="ff631-1993">このサービスを使用すると、アプリケーションで指定されているポートを起点として、空いている TCP ポート (バインドされていない) の検索が試みられます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="ff631-1994">この検索ロジックは、検索が最大ポート値の 0xFFFF に到達すると、ラップアラウンドします。</span><span class="sxs-lookup"><span data-stu-id="ff631-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="ff631-1995">検索が成功すると、*free_port_ptr* によってポイントされている変数に空きポートが返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="ff631-1996">*このサービスが別のスレッドから呼び出されて、同じポートが返される場合があります。このような競合状態を回避するには、アプリケーションでこのサービスと実際のクライアント ソケット バインドをミューテックスの保護下に置くことが必要になる場合があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-1997">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-1997">Parameters</span></span>

- <span data-ttu-id="ff631-1998">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-1999">**port** 検索を開始するポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="ff631-2000">**free_port_ptr** 宛先の空きポートの戻り値を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2001">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2001">Return Values</span></span>

- <span data-ttu-id="ff631-2002">**NX_SUCCESS** (0x00) 空きポートの検索に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="ff631-2003">**NX_NO_FREE_PORTS** (0x45) 空きポートが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="ff631-2004">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-2005">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2006">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-2007">**NX_INVALID_PORT** (0x46) 指定されたポート番号が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2008">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2008">Allowed From</span></span>

<span data-ttu-id="ff631-2009">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2010">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2010">Preemption Possible</span></span>

<span data-ttu-id="ff631-2011">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2012">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2013">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2013">See Also</span></span>

- <span data-ttu-id="ff631-2014">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2015">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2016">nx_tcp_enable、nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-2017">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-2018">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-2019">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2020">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2021">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2022">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="ff631-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="ff631-2025">TCP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2026">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="ff631-2027">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2027">Description</span></span>

<span data-ttu-id="ff631-2028">このサービスを使用すると、指定した IP インスタンスの TCP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="ff631-2029">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2030">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2030">Parameters</span></span>

- <span data-ttu-id="ff631-2031">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2032">**tcp_packets_sent** 送信された TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="ff631-2033">**tcp_bytes_sent** 送信された TCP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="ff631-2034">**tcp_packets_received** 受信した TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="ff631-2035">**tcp_bytes_received** 受信した TCP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="ff631-2036">**tcp_invalid_packets** 無効な TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="ff631-2037">**tcp_receive_packets_dropped** 破棄された TCP 受信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="ff631-2038">**tcp_checksum_errors** チェックサム エラーが発生している TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="ff631-2039">**tcp_connections** TCP 接続の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="ff631-2040">**tcp_disconnections** TCP 切断の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="ff631-2041">**tcp_connections_dropped** 破棄された TCP 接続の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="ff631-2042">**tcp_retransmit_packets** 再送信された TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2043">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2043">Return Values</span></span>

- <span data-ttu-id="ff631-2044">**NX_SUCCESS** (0x00) TCP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="ff631-2045">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-2046">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2047">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2048">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2048">Allowed From</span></span>

<span data-ttu-id="ff631-2049">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2050">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2050">Preemption Possible</span></span>

<span data-ttu-id="ff631-2051">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2052">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2053">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2053">See Also</span></span>

- <span data-ttu-id="ff631-2054">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2055">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2056">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-2057">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-2058">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-2059">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2060">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2061">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2062">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="ff631-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="ff631-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="ff631-2065">TCP 接続を受け入れます</span><span class="sxs-lookup"><span data-stu-id="ff631-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2066">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-2067">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2067">Description</span></span>

<span data-ttu-id="ff631-2068">このサービスを使用すると、以前にリッスン用に設定されたポートに対する、TCP クライアント ソケット接続要求が受け入れられます (または受け入れる準備が行われます)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="ff631-2069">このサービスは、アプリケーションがリッスン サービスや再リッスン サービスを呼び出した直後、またはクライアント接続が実際に存在する場合は、リッスン コールバック ルーチンが呼び出された後に呼び出されることがあります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="ff631-2070">接続をすぐに確立できない場合は、指定された待機オプションに従ってサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="ff631-2071">*サーバー ポートへのサーバー ソケットのバインドを削除するためにその接続が必要ではなくなった後、アプリケーションで **nx_tcp_server_socket_unaccept** を呼び出す必要があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="ff631-2072">*アプリケーション コールバック ルーチンは、IP のヘルパー スレッド内から呼び出されます。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2073">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2073">Parameters</span></span>

- <span data-ttu-id="ff631-2074">**socket_ptr** TCP サーバー ソケット制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="ff631-2075">**wait_option** 接続を確立している最中のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="ff631-2076">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-2077">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-2079">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-2080">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2080">Return Values</span></span>
- <span data-ttu-id="ff631-2081">**NX_SUCCESS** (0x00) TCP サーバー ソケットの受け入れに成功しました (パッシブ接続)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="ff631-2082">**NX_NOT_LISTEN_STATE** (0x36) 指定されたサーバー ソケットはリッスン状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="ff631-2083">**NX_IN_PROGRESS** (0x37) 待機が指定されていないため、接続の試行を実行中です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="ff631-2084">**NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="ff631-2085">**NX_PTR_ERROR** (0x07) ソケット ポインター エラー。</span><span class="sxs-lookup"><span data-stu-id="ff631-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="ff631-2086">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2087">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2088">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2088">Allowed From</span></span>

<span data-ttu-id="ff631-2089">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2090">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2090">Preemption Possible</span></span>

<span data-ttu-id="ff631-2091">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2092">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="ff631-2093">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2093">See Also</span></span>

- <span data-ttu-id="ff631-2094">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2095">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2096">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2097">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-2098">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-2099">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2100">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2101">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2102">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="ff631-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="ff631-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="ff631-2105">TCP ポートでのクライアント接続のリッスンを有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2106">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="ff631-2107">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2107">Description</span></span>

<span data-ttu-id="ff631-2108">このサービスを使用すると、指定した TCP ポートでクライアント接続要求をリッスンできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="ff631-2109">クライアント接続要求を受信すると、指定されたサーバー ソケットが指定されたポートにバインドされ、指定されたリッスン コールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="ff631-2110">リッスン コールバック ルーチンの処理は、アプリケーションによって決まります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="ff631-2111">アプリケーションによっては、後から受け入れ操作を実行するアプリケーション スレッドをウェイクアップするロジックが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="ff631-2112">アプリケーションによるこのソケットの受け入れ処理でスレッドが既に中断されている場合、リッスン コールバック ルーチンは必要ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="ff631-2113">同じポート上の追加のクライアント接続をそのアプリケーションで処理する場合は、次の接続のために使用可能なソケット (CLOSED 状態のソケット) を使用して ***nx_tcp_server_socket_relisten*** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="ff631-2114">再リッスン サービスが呼び出されるまで、追加のクライアント接続はキューに入れられます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="ff631-2115">キューの最大深度を超えた場合は、新しい接続要求をキューできるようにするため、最も古い接続要求が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="ff631-2116">キューの最大深度は、このサービスによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="ff631-2117">*アプリケーション コールバック ルーチンは、内部の IP ヘルパー スレッドから呼び出されます。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2118">Parameters</span></span>

- <span data-ttu-id="ff631-2119">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2120">**port** リッスンするポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="ff631-2121">**socket_ptr** 接続に使用するソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="ff631-2122">**listen_queue_size** キューに入れることができるクライアント接続要求の数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="ff631-2123">**listen_callback** 接続を受信したときに呼び出すアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="ff631-2124">NULL 値が指定されている場合、リッスン コールバック機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2125">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2125">Return Values</span></span>

- <span data-ttu-id="ff631-2126">**NX_SUCCESS** (0x00) TCP ポートのリッスンの有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="ff631-2127">**NX_MAX_LISTEN** (0x33) 使用できるリッスン要求構造体がこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="ff631-2128">nx_api.h の定数 NX_MAX_LISTEN_REQUESTS で、許可されるアクティブなリッスン要求の数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="ff631-2129">**NX_NOT_CLOSED** (0x35) 指定されたサーバー ソケットが CLOSED 状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="ff631-2130">**NX_ALREADY_BOUND** (0x22) 指定されたサーバー ソケットは既にポートにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="ff631-2131">**NX_DUPLICATE_LISTEN** (0x34) このポートに対するアクティブなリッスン要求が既に存在します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="ff631-2132">**NX_INVALID_PORT** (0x46) 指定されたポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="ff631-2133">**NX_PTR_ERROR** (0x07) IP またはソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="ff631-2134">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2135">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2136">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2136">Allowed From</span></span>

<span data-ttu-id="ff631-2137">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2138">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2138">Preemption Possible</span></span>

<span data-ttu-id="ff631-2139">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2140">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="ff631-2141">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2141">See Also</span></span>

- <span data-ttu-id="ff631-2142">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2143">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2144">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2145">nx_tcp_server_socket_accept、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-2146">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-2147">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2148">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2149">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2150">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="ff631-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="ff631-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="ff631-2153">TCP ポートでクライアント接続を再リッスンします</span><span class="sxs-lookup"><span data-stu-id="ff631-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-2155">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2155">Description</span></span>

<span data-ttu-id="ff631-2156">このサービスは、以前にリッスン用に設定されたポートで接続を受信した後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="ff631-2157">このサービスの主な目的は、次のクライアント接続に新しいサーバー ソケットを提供することです。</span><span class="sxs-lookup"><span data-stu-id="ff631-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="ff631-2158">接続要求がキューに入れられている場合、接続はこのサービス呼び出し中に直ちに処理されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="ff631-2159">*元のリッスン要求によって指定されたのと同じコールバック ルーチンが、この新しいサーバー ソケットのための接続が存在する場合にも呼び出されます。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2160">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2160">Parameters</span></span>

- <span data-ttu-id="ff631-2161">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2162">**port** 再リッスンするポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="ff631-2163">**socket_ptr** 次のクライアント接続に使用するソケット。</span><span class="sxs-lookup"><span data-stu-id="ff631-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2164">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2164">Return Values</span></span>
- <span data-ttu-id="ff631-2165">**NX_SUCCESS** (0x00) TCP ポートの再リッスンに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="ff631-2166">**NX_NOT_CLOSED** (0x35) 指定されたサーバー ソケットが CLOSED 状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="ff631-2167">**NX_ALREADY_BOUND** (0x22) 指定されたサーバー ソケットは既にポートにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="ff631-2168">**NX_INVALID_RELISTEN** (0x47) このポートには有効なソケット ポインターが既に存在するか、指定されたポートでリッスン要求がアクティブになっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="ff631-2169">**NX_CONNECTION_PENDING** (0x48) キューに入れられた接続要求が既に存在しており、この呼び出し中にその要求が処理されたこと以外は、NX_SUCCESS と同じです。</span><span class="sxs-lookup"><span data-stu-id="ff631-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="ff631-2170">**NX_INVALID_PORT** (0x46) 指定されたポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="ff631-2171">**NX_PTR_ERROR** (0x07) IP またはリッスン コールバック ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="ff631-2172">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2173">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2174">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2174">Allowed From</span></span>

<span data-ttu-id="ff631-2175">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2176">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2176">Preemption Possible</span></span>

<span data-ttu-id="ff631-2177">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2178">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="ff631-2179">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2179">See Also</span></span>

- <span data-ttu-id="ff631-2180">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2181">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2182">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2183">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2184">nx_tcp_server_socket_unaccept、nx_tcp_server_socket_unlisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="ff631-2185">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2186">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2187">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2188">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="ff631-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="ff631-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="ff631-2191">リッスン ポートとのソケットの関連付けを削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-2193">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2193">Description</span></span>

<span data-ttu-id="ff631-2194">このサービスを使用すると、このサーバー ソケットと指定したサーバー ポートとの間の関連付けが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="ff631-2195">アプリケーションは、切断の後か、着信の応答に失敗した後、このサービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2196">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2196">Parameters</span></span>

- <span data-ttu-id="ff631-2197">**socket_ptr** 以前にセットアップされたサーバーのソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2198">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2198">Return Values</span></span>

- <span data-ttu-id="ff631-2199">**NX_SUCCESS** (0x00) サーバー ソケットの受け入れ解除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="ff631-2200">**NX_NOT_LISTEN_STATE** (0x36) サーバー ソケットが不適切な状態のため、切断されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="ff631-2201">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2202">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2203">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2204">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2204">Allowed From</span></span>

<span data-ttu-id="ff631-2205">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2206">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2206">Preemption Possible</span></span>

<span data-ttu-id="ff631-2207">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2208">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="ff631-2209">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2209">See Also</span></span>

- <span data-ttu-id="ff631-2210">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2211">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、nx_tcp_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="ff631-2212">nx_tcp_free_port_find、nx_tcp_info_get、nx_tcp_server_socket_accept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="ff631-2213">nx_tcp_server_socket_listen、nx_tcp_server_socket_relisten、</span><span class="sxs-lookup"><span data-stu-id="ff631-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="ff631-2214">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2215">nx_tcp_socket_create、nx_tcp_socket_delete、nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="ff631-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2216">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2217">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="ff631-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="ff631-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="ff631-2220">TCP ポートでのクライアント接続のリッスンを無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2221">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="ff631-2222">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2222">Description</span></span>

<span data-ttu-id="ff631-2223">このサービスを使用すると、指定した TCP ポートでのクライアント接続要求のリッスンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2224">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2224">Parameters</span></span>

- <span data-ttu-id="ff631-2225">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2226">**port** リッスンを無効にするポートの数 (0 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2227">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2227">Return Values</span></span>

- <span data-ttu-id="ff631-2228">**NX_SUCCESS** (0x00) TCP のリッスンの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="ff631-2229">**NX_ENTRY_NOT_FOUND** (0x16) 指定されたポートに対してリッスンが有効になっていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="ff631-2230">**NX_INVALID_PORT** (0x46) 指定されたポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="ff631-2231">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-2232">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2233">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2234">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2234">Allowed From</span></span>

<span data-ttu-id="ff631-2235">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2236">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2236">Preemption Possible</span></span>

<span data-ttu-id="ff631-2237">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2238">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="ff631-2239">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2239">See Also</span></span>

- <span data-ttu-id="ff631-2240">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2241">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2242">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2243">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2244">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2245">nx_tcp_socket_bytes_available、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2246">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2247">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2248">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="ff631-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="ff631-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="ff631-2251">取得可能なバイト数を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2252">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="ff631-2253">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2253">Description</span></span>

<span data-ttu-id="ff631-2254">このサービスを使用すると、指定した TCP ソケットで取得可能なバイト数が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="ff631-2255">TCP ソケットが既に接続されている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff631-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2256">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2256">Parameters</span></span>

- <span data-ttu-id="ff631-2257">**socket_ptr** 以前に作成され、接続されている TCP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="ff631-2258">**bytes_available** 使用可能なバイトの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2259">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2259">Return Values</span></span>

- <span data-ttu-id="ff631-2260">**NX_SUCCESS** (0x00) サービスが正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="ff631-2261">読み取り可能なバイト数が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="ff631-2262">**NX_NOT_CONNECTED** (0x38) ソケットが接続状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="ff631-2263">**NX_PTR_ERROR** (0x07) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="ff631-2264">**NX_NOT_ENABLED** (0x14) TCP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="ff631-2265">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2266">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2266">Allowed From</span></span>

<span data-ttu-id="ff631-2267">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2268">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2268">Preemption Possible</span></span>

<span data-ttu-id="ff631-2269">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2270">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2271">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2271">See Also</span></span>

- <span data-ttu-id="ff631-2272">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2273">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2274">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2275">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2276">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2277">nx_tcp_server_socket_unlisten、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2278">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2279">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2280">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="ff631-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="ff631-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="ff631-2283">TCP クライアントまたはサーバー ソケットを作成します</span><span class="sxs-lookup"><span data-stu-id="ff631-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2284">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-2285">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2285">Description</span></span>

<span data-ttu-id="ff631-2286">このサービスを使用すると、指定した IP インスタンスの TCP クライアントまたはサーバー ソケットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="ff631-2287">*アプリケーション コールバック ルーチンは、この IP インスタンスに関連付けられているスレッドから呼び出されます。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2288">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2288">Parameters</span></span>

- <span data-ttu-id="ff631-2289">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2290">**socket_ptr** 新しい TCP ソケット制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="ff631-2291">**name** この TCP ソケットのアプリケーション名。</span><span class="sxs-lookup"><span data-stu-id="ff631-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="ff631-2292">**type_of_service** 送信のためのサービスの種類を定義します。有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ff631-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="ff631-2293">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="ff631-2294">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="ff631-2295">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="ff631-2296">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="ff631-2297">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="ff631-2298">**fragment**  IP のフラグメント化を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="ff631-2299">NX_FRAGMENT_OKAY (0x0) が指定されている場合は、IP のフラグメント化が許可されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="ff631-2300">NX_DONT_FRAGMENT (0x4000) が指定されている場合は、IP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="ff631-2301">**time_to_live** このパケットが破棄されるまでに通過できるルーターの数を定義する 8 ビットの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="ff631-2302">既定値は NX_IP_TIME_TO_LIVE によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="ff631-2303">**window_size** このソケットの受信キューで許可される最大バイト数を定義します</span><span class="sxs-lookup"><span data-stu-id="ff631-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="ff631-2304">**urgent_data_callback** 受信ストリームで緊急データが検出されるたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="ff631-2305">この値が NX_NULL 場合は、緊急データが無視されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="ff631-2306">**disconnect_callback** 接続の反対側のソケットによって切断が発行されるたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="ff631-2307">この値が NX_NULL の場合は、切断コールバック関数が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2308">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2308">Return Values</span></span>
- <span data-ttu-id="ff631-2309">**NX_SUCCESS** (0x00) TCP クライアント ソケットの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="ff631-2310">**NX_OPTION_ERROR** (0x0A) サービスの種類、フラグメント、ウィンドウ サイズ、または有効期限オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="ff631-2311">**NX_PTR_ERROR** (0x07) IP またはソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="ff631-2312">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2313">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2314">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2314">Allowed From</span></span>

<span data-ttu-id="ff631-2315">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2316">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2316">Preemption Possible</span></span>

<span data-ttu-id="ff631-2317">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2318">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2319">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2319">See Also</span></span>

- <span data-ttu-id="ff631-2320">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2321">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2322">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2323">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2324">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2325">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2326">nx_tcp_socket_delete、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2327">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2328">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="ff631-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="ff631-2331">TCP ソケットを削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-2333">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2333">Description</span></span>

<span data-ttu-id="ff631-2334">このサービスを使用すると、以前作成した TCP ソケットが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="ff631-2335">そのソケットがまだバインドされているか接続されている場合、サービスはエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2336">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2336">Parameters</span></span>

- <span data-ttu-id="ff631-2337">**socket_ptr** 以前に作成された TCP ソケット</span><span class="sxs-lookup"><span data-stu-id="ff631-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2338">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2338">Return Values</span></span>

- <span data-ttu-id="ff631-2339">**NX_SUCCESS** (0x00) ソケットの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="ff631-2340">**NX_NOT_CREATED** (0x27) ソケットが作成されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="ff631-2341">**NX_STILL_BOUND** (0x42) ソケットはまだバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="ff631-2342">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2343">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2344">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2345">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2345">Allowed From</span></span>

<span data-ttu-id="ff631-2346">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2347">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2347">Preemption Possible</span></span>

<span data-ttu-id="ff631-2348">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2349">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2350">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2350">See Also</span></span>

- <span data-ttu-id="ff631-2351">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2352">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2353">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2354">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2355">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2356">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2357">nx_tcp_socket_create、nx_tcp_socket_disconnect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2358">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2359">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="ff631-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="ff631-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="ff631-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="ff631-2362">クライアントとサーバーのソケット接続を切断します</span><span class="sxs-lookup"><span data-stu-id="ff631-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2363">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-2364">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2364">Description</span></span>

<span data-ttu-id="ff631-2365">このサービスを使用すると、確立されたクライアントまたはサーバーのソケット接続が切断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="ff631-2366">サーバー ソケットを切断した場合、その後に受け入れ解除要求が発行される必要がありますが、切断されているクライアント ソケットは別の接続要求を受け入れられる状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="ff631-2367">切断プロセスをすぐに完了できない場合、指定された待機オプションに従ってサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2368">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2368">Parameters</span></span>

- <span data-ttu-id="ff631-2369">**socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="ff631-2370">**wait_option** 切断を実行中のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="ff631-2371">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-2372">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-2374">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2375">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2375">Return Values</span></span>

- <span data-ttu-id="ff631-2376">**NX_SUCCESS** (0x00) ソケットの切断に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="ff631-2377">**NX_NOT_CONNECTED** (0x38) 指定されたソケットは接続されていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="ff631-2378">**NX_IN_PROGRESS** (0x37) 切断を実行中です。待機は指定されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="ff631-2379">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-2380">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2381">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2382">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2383">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2383">Allowed From</span></span>

<span data-ttu-id="ff631-2384">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2385">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2385">Preemption Possible</span></span>

<span data-ttu-id="ff631-2386">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2387">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2388">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2388">See Also</span></span>

- <span data-ttu-id="ff631-2389">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2390">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2391">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2392">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2393">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2394">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2395">nx_tcp_socket_create、nx_tcp_socket_delete、nx_tcp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-2396">nx_tcp_socket_receive、nx_tcp_socket_receive_queue_max_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="ff631-2397">nx_tcp_socket_send、nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="ff631-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="ff631-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="ff631-2399">TCP 切断完了通知コールバック関数をインストールします</span><span class="sxs-lookup"><span data-stu-id="ff631-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2400">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-2401">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2401">Description</span></span>

<span data-ttu-id="ff631-2402">このサービスを使用すると、ソケットの切断操作の完了後に呼び出されるコールバック関数を登録できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="ff631-2403">TCP ソケット切断完了コールバック関数は、オプションの</span><span class="sxs-lookup"><span data-stu-id="ff631-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="ff631-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** を定義して NetX が構築されている場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2405">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2405">Parameters</span></span>

- <span data-ttu-id="ff631-2406">**socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="ff631-2407">**tcp_disconnect_complete_notify** インストールされるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2408">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2408">Return Values</span></span>
- <span data-ttu-id="ff631-2409">**NX_SUCCESS** (0x00) コールバック関数が正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="ff631-2410">**NX_NOT_SUPPORTED** (0x4B) この拡張通知機能は NetX ライブラリに組み込まれていません</span><span class="sxs-lookup"><span data-stu-id="ff631-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="ff631-2411">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2412">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2413">**NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2414">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2414">Allowed From</span></span>

<span data-ttu-id="ff631-2415">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2416">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2416">Preemption Possible</span></span>

<span data-ttu-id="ff631-2417">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2418">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="ff631-2419">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2419">See Also</span></span>

- <span data-ttu-id="ff631-2420">nx_tcp_enable、nx_tcp_socket_create、nx_tcp_socket_establish_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="ff631-2421">nx_tcp_socket_mss_get、nx_tcp_socket_mss_peer_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="ff631-2422">nx_tcp_socket_mss_set、nx_tcp_socket_peer_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="ff631-2423">nx_tcp_socket_receive_notify、nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2424">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="ff631-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="ff631-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="ff631-2427">TCP 確立通知コールバック関数を設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2428">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-2429">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2429">Description</span></span>

<span data-ttu-id="ff631-2430">このサービスを使用すると、TCP ソケットが接続を確立した後に呼び出されるコールバック関数を登録できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="ff631-2431">TCP ソケット確立コールバック関数は、オプションの ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** を定義して NetX が構築されている場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2432">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2432">Parameters</span></span>

- <span data-ttu-id="ff631-2433">**socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="ff631-2434">**tcp_establish_notify** TCP 接続が確立された後に呼び出されるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2435">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2435">Return Values</span></span>

- <span data-ttu-id="ff631-2436">**NX_SUCCESS** (0x00) 通知関数が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="ff631-2437">**NX_NOT_SUPPORTED** (0x4B) この拡張通知機能は NetX ライブラリに組み込まれていません</span><span class="sxs-lookup"><span data-stu-id="ff631-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="ff631-2438">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2439">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2440">**NX_NOT_ENABLED** (0x14) TCP は、このアプリケーションで有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2441">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2441">Allowed From</span></span>

<span data-ttu-id="ff631-2442">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2443">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2443">Preemption Possible</span></span>

<span data-ttu-id="ff631-2444">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2445">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="ff631-2446">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2446">See Also</span></span>

- <span data-ttu-id="ff631-2447">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2448">nx_tcp_socket_disconnect_complete_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2449">nx_tcp_socket_mss_peer_get、nx_tcp_socket_mss_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="ff631-2450">nx_tcp_socket_peer_info_get、nx_tcp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-2451">nx_tcp_socket_timed_wait_callback、nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="ff631-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="ff631-2454">TCP ソケット アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2455">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="ff631-2456">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2456">Description</span></span>

<span data-ttu-id="ff631-2457">このサービスを使用すると、指定した TCP ソケット インスタンスの TCP ソケット アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="ff631-2458">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2459">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2459">Parameters</span></span>

- <span data-ttu-id="ff631-2460">**socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="ff631-2461">**tcp_packets_sent** ソケットで送信された TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="ff631-2462">**tcp_bytes_sent** ソケットで送信された TCP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="ff631-2463">**tcp_packets_received** ソケットで受信した TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="ff631-2464">**tcp_bytes_received** ソケットで受信した TCP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="ff631-2465">**tcp_retransmit_packets** TCP パケット再送信の合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="ff631-2466">**tcp_packets_queued** ソケットでキューに入れられた TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="ff631-2467">**tcp_checksum_errors** ソケットでチェックサム エラーが発生している TCP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="ff631-2468">**tcp_socket_state** ソケットの現在の状態の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="ff631-2469">**tcp_transmit_queue_depth** ACK を待機してキューに入れられたままになっている送信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="ff631-2470">**tcp_transmit_window** 現在の送信ウィンドウ サイズの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="ff631-2471">**tcp_receive_window** 現在の受信ウィンドウ サイズの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2472">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2472">Return Values</span></span>

- <span data-ttu-id="ff631-2473">**NX_SUCCESS** (0x00) TCP ソケット情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="ff631-2474">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2475">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2476">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2477">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="ff631-2478">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2478">Allowed From</span></span>

<span data-ttu-id="ff631-2479">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2480">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2480">Preemption Possible</span></span>

<span data-ttu-id="ff631-2481">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2482">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2483">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2483">See Also</span></span>

- <span data-ttu-id="ff631-2484">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2485">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2486">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2487">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2488">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2489">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2490">nx_tcp_socket_create、nx_tcp_socket_delete、nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="ff631-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2491">nx_tcp_socket_receive、nx_tcp_socket_receive_queue_max_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="ff631-2492">nx_tcp_socket_send、nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="ff631-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="ff631-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="ff631-2494">ソケットの MSS を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2495">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="ff631-2496">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2496">Description</span></span>

<span data-ttu-id="ff631-2497">このサービスを使用すると、指定したソケットのローカルの最大セグメント サイズ (MSS) が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2498">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2498">Parameters</span></span>

- <span data-ttu-id="ff631-2499">**socket_ptr** 以前に作成されたソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="ff631-2500">**mss** MSS を返す宛先。</span><span class="sxs-lookup"><span data-stu-id="ff631-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2501">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2501">Return Values</span></span>

- <span data-ttu-id="ff631-2502">**NX_SUCCESS** (0x00) MSS の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="ff631-2503">**NX_PTR_ERROR** (0x07) ソケットまたは MSS 宛先ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="ff631-2504">**NX_NOT_ENABLED** (0x14) TCP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="ff631-2505">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2506">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2506">Allowed From</span></span>

<span data-ttu-id="ff631-2507">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2508">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2508">Preemption Possible</span></span>

<span data-ttu-id="ff631-2509">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2510">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2511">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2511">See Also</span></span>

- <span data-ttu-id="ff631-2512">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2513">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2514">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_peer_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="ff631-2515">nx_tcp_socket_mss_set、nx_tcp_socket_peer_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="ff631-2516">nx_tcp_socket_receive_notify、nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2517">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="ff631-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="ff631-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="ff631-2520">ピア TCP ソケットの MSS を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2521">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="ff631-2522">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2522">Description</span></span>

<span data-ttu-id="ff631-2523">このサービスを使用すると、ピア ソケットによってアドバタイズされた最大セグメント サイズ (MSS) が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2524">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2524">Parameters</span></span>

- <span data-ttu-id="ff631-2525">**socket_ptr** 以前に作成され、接続されているソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="ff631-2526">**mss** MSS を返す宛先。</span><span class="sxs-lookup"><span data-stu-id="ff631-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-2527">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2527">Return Values</span></span>

- <span data-ttu-id="ff631-2528">**NX_SUCCESS** (0x00) ピア MSS の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="ff631-2529">**NX_PTR_ERROR** (0x07) ソケットまたは MSS 宛先ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="ff631-2530">**NX_NOT_ENABLED** (0x14) TCP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="ff631-2531">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2532">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2532">Allowed From</span></span>

<span data-ttu-id="ff631-2533">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2534">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2534">Preemption Possible</span></span>

<span data-ttu-id="ff631-2535">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2536">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2537">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2537">See Also</span></span>

- <span data-ttu-id="ff631-2538">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2539">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2540">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2541">nx_tcp_socket_mss_set、nx_tcp_socket_peer_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="ff631-2542">nx_tcp_socket_receive_notify、nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2543">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="ff631-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="ff631-2546">ソケットの MSS を設定します</span><span class="sxs-lookup"><span data-stu-id="ff631-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2547">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="ff631-2548">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2548">Description</span></span>

<span data-ttu-id="ff631-2549">このサービスを使用すると、指定したソケットの最大セグメント サイズ (MSS) が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="ff631-2550">MSS 値は、ネットワーク インターフェイスの IP MTU の範囲内で指定して、IP ヘッダーと TCP ヘッダーのための余地を残す必要があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="ff631-2551">このサービスは、TCP ソケットで接続プロセスが開始される前に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="ff631-2552">TCP 接続が確立された後にこのサービスを使用した場合、新しい値は接続に影響しません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2553">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2553">Parameters</span></span>

- <span data-ttu-id="ff631-2554">**socket_ptr** 以前に作成されたソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="ff631-2555">**mss** 設定する MSS の値。</span><span class="sxs-lookup"><span data-stu-id="ff631-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2556">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2556">Return Values</span></span>

- <span data-ttu-id="ff631-2557">**NX_SUCCESS** (0x00) MSS の設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="ff631-2558">**NX_SIZE_ERROR** (0x09) 指定された MSS 値が大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="ff631-2559">**NX_NOT_CONNECTED** (0x38) TCP 接続が確立されていません</span><span class="sxs-lookup"><span data-stu-id="ff631-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="ff631-2560">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2561">**NX_NOT_ENABLED** (0x14) TCP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="ff631-2562">**NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2563">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2563">Allowed From</span></span>

<span data-ttu-id="ff631-2564">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2565">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2565">Preemption Possible</span></span>

<span data-ttu-id="ff631-2566">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2567">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2568">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2568">See Also</span></span>

- <span data-ttu-id="ff631-2569">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2570">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2571">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2572">nx_tcp_socket_mss_peer_get、nx_tcp_socket_peer_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="ff631-2573">nx_tcp_socket_receive_notify、nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2574">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="ff631-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="ff631-2577">ピア TCP ソケットに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2578">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="ff631-2579">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2579">Description</span></span>

<span data-ttu-id="ff631-2580">このサービスを使用すると、IP ネットワーク経由で接続されている TCP ソケットのピア IP アドレスとポート情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2581">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2581">Parameters</span></span>

- <span data-ttu-id="ff631-2582">**socket_ptr** 以前に作成された TCP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="ff631-2583">**peer_ip_address** ピア IP アドレスの宛先を指すポインター (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="ff631-2584">**peer_port** ピア ポート番号の宛先を指すポインター (ホストのバイト順)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2585">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2585">Return Values</span></span>

- <span data-ttu-id="ff631-2586">**NX_SUCCESS** (0x00) サービスが正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="ff631-2587">ピア IP アドレスとポート番号が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="ff631-2588">**NX_NOT_CONNECTED** (0x38) ソケットが接続状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="ff631-2589">**NX_PTR_ERROR** (0x07) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="ff631-2590">**NX_NOT_ENABLED** (0x14) TCP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="ff631-2591">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2592">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2592">Allowed From</span></span>

<span data-ttu-id="ff631-2593">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2594">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2594">Preemption Possible</span></span>

<span data-ttu-id="ff631-2595">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2596">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2597">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2597">See Also</span></span>

- <span data-ttu-id="ff631-2598">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2599">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2600">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2601">nx_tcp_socket_mss_peer_get、nx_tcp_socket_mss_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="ff631-2602">nx_tcp_socket_receive_notify、nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2603">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="ff631-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ff631-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="ff631-2606">TCP ソケットからデータを受信します</span><span class="sxs-lookup"><span data-stu-id="ff631-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2607">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-2608">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2608">Description</span></span>

<span data-ttu-id="ff631-2609">このサービスを使用すると、指定したソケットから TCP データを受信できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="ff631-2610">指定したソケットでデータがキューに格納されていない場合は、指定された待機オプションに基づいて呼び出し元が中断します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="ff631-2611">*NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2612">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2612">Parameters</span></span>

- <span data-ttu-id="ff631-2613">**socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="ff631-2614">**packet_ptr** TCP パケット ポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="ff631-2615">**wait_option** このソケットでデータが現在キューに格納されていない場合に、サービスがどのように動作するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="ff631-2616">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-2617">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-2619">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2620">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2620">Return Values</span></span>
- <span data-ttu-id="ff631-2621">**NX_SUCCESS** (0x00) ソケットのデータの受信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="ff631-2622">**NX_NOT_BOUND** (0x24) ソケットがまだバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="ff631-2623">**NX_NO_PACKET** (0x01) 受信したデータはありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="ff631-2624">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-2625">**NX_NOT_CONNECTED** (0x38) ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="ff631-2626">**NX_PTR_ERROR** (0x07) ソケットまたはパケットの戻りポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="ff631-2627">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2628">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2629">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2629">Allowed From</span></span>

<span data-ttu-id="ff631-2630">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2631">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2631">Preemption Possible</span></span>

<span data-ttu-id="ff631-2632">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2633">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2633">Example</span></span>

<span data-ttu-id="ff631-2634">/\* 以前に作成され、接続されている TCP クライアントソケットからパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="ff631-2635">使用できるパケットがない場合は、中断する前に、タイマーのティック数が 200 に達するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="ff631-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span><span class="sxs-lookup"><span data-stu-id="ff631-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="ff631-2637">/\* 状態が NX_SUCCESS の場合、受信パケットは "packet_ptr" によって示されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="ff631-2638">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2638">See Also</span></span>

- <span data-ttu-id="ff631-2639">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2640">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2641">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2642">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2643">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2644">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2645">nx_tcp_socket_create、nx_tcp_socket_delete、nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="ff631-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2646">nx_tcp_socket_info_get、nx_tcp_socket_receive_queue_max_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="ff631-2647">nx_tcp_socket_send、nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="ff631-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="ff631-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="ff631-2649">受信したパケットをアプリケーションに通知します</span><span class="sxs-lookup"><span data-stu-id="ff631-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="ff631-2650">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-2651">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2651">Description</span></span>

<span data-ttu-id="ff631-2652">このサービスを使用すると、アプリケーションによって指定されたコールバック関数を使用して、受信通知関数ポインターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="ff631-2653">このコールバック関数は、ソケットで 1 つ以上のパケットを受信するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="ff631-2654">NX_NULL ポインターが指定されている場合、通知関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2655">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2655">Parameters</span></span>

- <span data-ttu-id="ff631-2656">**socket_ptr** TCP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="ff631-2657">**tcp_receive_notify** ソケットで 1 つ以上のパケットを受信したときに呼び出されるアプリケーション コールバック関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2658">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2658">Return Values</span></span>

- <span data-ttu-id="ff631-2659">**NX_SUCCESS** (0x00) ソケットの受信の通知に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="ff631-2660">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2661">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2662">**NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2663">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2663">Allowed From</span></span>

<span data-ttu-id="ff631-2664">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2665">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2665">Preemption Possible</span></span>

<span data-ttu-id="ff631-2666">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2667">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2668">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2668">See Also</span></span>

- <span data-ttu-id="ff631-2669">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2670">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2671">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2672">nx_tcp_socket_mss_peer_get、nx_tcp_socket_mss_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="ff631-2673">nx_tcp_socket_peer_info_get、nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2674">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="ff631-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="ff631-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="ff631-2677">TCP ソケットを介してデータを送信します</span><span class="sxs-lookup"><span data-stu-id="ff631-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2678">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-2679">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2679">Description</span></span>

<span data-ttu-id="ff631-2680">このサービスを使用すると、以前に接続された TCP ソケットを介して TCP データが送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="ff631-2681">受信側の最後に公開されたウィンドウのサイズがこの要求よりも小さい場合、サービスは、指定された待機オプションに基づいて、必要に応じて中断します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="ff631-2682">このサービスでは、MSS より大きいパケット データは IP レイヤーに送信されません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="ff631-2683">*エラーが返されない限り、アプリケーションは、この呼び出しの後にパケットを解放することはできません。送信後、ネットワーク ドライバーがパケットの解放も試行するため、これを行うと予期しない結果が発生します。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2684">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2684">Parameters</span></span>

- <span data-ttu-id="ff631-2685">**socket_ptr** 以前に接続された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="ff631-2686">**packet_ptr** TCP データ パケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="ff631-2687">**wait_option** 要求が受信側のウィンドウ サイズより大きい場合に、サービスがどのように動作するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="ff631-2688">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-2689">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-2691">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2692">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2692">Return Values</span></span>

- <span data-ttu-id="ff631-2693">**NX_SUCCESS** (0x00) ソケットの送信に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="ff631-2694">**NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="ff631-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="ff631-2696">**NX_NOT_CONNECTED** (0x38) ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="ff631-2697">**NX_WINDOW_OVERFLOW** (0x39) 要求が、受信側の公開されたウィンドウ サイズ (バイト単位) を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="ff631-2698">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-2699">**NX_INVALID_PACKET** (0x12) パケットが割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="ff631-2700">**NX_TX_QUEUE_DEPTH** (0x49) 最大転送キューの深さに達しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="ff631-2701">**NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="ff631-2702">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2703">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2704">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-2705">**NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2706">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2706">Allowed From</span></span>

<span data-ttu-id="ff631-2707">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2708">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2708">Preemption Possible</span></span>

<span data-ttu-id="ff631-2709">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2710">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2711">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2711">See Also</span></span>

- <span data-ttu-id="ff631-2712">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2713">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2714">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2715">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2716">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2717">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2718">nx_tcp_socket_create、nx_tcp_socket_delete、nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="ff631-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2719">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2720">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="ff631-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="ff631-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="ff631-2722">TCP ソケットが特定の状態になるのを待機します</span><span class="sxs-lookup"><span data-stu-id="ff631-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2723">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="ff631-2724">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2724">Description</span></span>

<span data-ttu-id="ff631-2725">このサービスは、ソケットが目的の状態になるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="ff631-2726">ソケットが目的の状態でない場合、指定された待機オプションに従ってサービスが中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2727">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2727">Parameters</span></span>

- <span data-ttu-id="ff631-2728">**socket_ptr** 以前に接続された TCP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="ff631-2729">**desired_state** 目的の TCP 状態。</span><span class="sxs-lookup"><span data-stu-id="ff631-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="ff631-2730">有効な TCP ソケットの状態は、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="ff631-2731">NX_TCP_CLOSED (0x01)</span><span class="sxs-lookup"><span data-stu-id="ff631-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="ff631-2732">NX_TCP_LISTEN_STATE (0x02)</span><span class="sxs-lookup"><span data-stu-id="ff631-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="ff631-2733">NX_TCP_SYN_SENT (0x03)</span><span class="sxs-lookup"><span data-stu-id="ff631-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="ff631-2734">NX_TCP_SYN_RECEIVED (0x04)</span><span class="sxs-lookup"><span data-stu-id="ff631-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="ff631-2735">NX_TCP_ESTABLISHED (0x05)</span><span class="sxs-lookup"><span data-stu-id="ff631-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="ff631-2736">NX_TCP_CLOSE_WAIT (0x06)</span><span class="sxs-lookup"><span data-stu-id="ff631-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="ff631-2737">NX_TCP_FIN_WAIT_1 (0x07)</span><span class="sxs-lookup"><span data-stu-id="ff631-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="ff631-2738">NX_TCP_FIN_WAIT_2 (0x08)</span><span class="sxs-lookup"><span data-stu-id="ff631-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="ff631-2739">NX_TCP_CLOSING (0x09)</span><span class="sxs-lookup"><span data-stu-id="ff631-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="ff631-2740">NX_TCP_TIMED_WAIT (0x0A)</span><span class="sxs-lookup"><span data-stu-id="ff631-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="ff631-2741">NX_TCP_LAST_ACK (0x0B)</span><span class="sxs-lookup"><span data-stu-id="ff631-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="ff631-2742">**wait_option** 要求された状態が存在しない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="ff631-2743">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-2744">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-2746">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2747">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2747">Return Values</span></span>
- <span data-ttu-id="ff631-2748">**NX_SUCCESS** (0x00) 状態の待機に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="ff631-2749">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2750">**NX_NOT_SUCCESSFUL** (0x43) 指定された待機時間内に状態が存在しませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="ff631-2751">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-2752">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2753">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-2754">**NX_OPTION_ERROR** (0x0A) 目的のソケットの状態が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2755">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2755">Allowed From</span></span>

<span data-ttu-id="ff631-2756">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2757">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2757">Preemption Possible</span></span>

<span data-ttu-id="ff631-2758">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2759">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2760">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2760">See Also</span></span>

- <span data-ttu-id="ff631-2761">nx_tcp_client_socket_bind、nx_tcp_client_socket_connect、</span><span class="sxs-lookup"><span data-stu-id="ff631-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="ff631-2762">nx_tcp_client_socket_port_get、nx_tcp_client_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2763">nx_tcp_enable、nx_tcp_free_port_find、nx_tcp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="ff631-2764">nx_tcp_server_socket_accept、nx_tcp_server_socket_listen、</span><span class="sxs-lookup"><span data-stu-id="ff631-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="ff631-2765">nx_tcp_server_socket_relisten、nx_tcp_server_socket_unaccept、</span><span class="sxs-lookup"><span data-stu-id="ff631-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="ff631-2766">nx_tcp_server_socket_unlisten、nx_tcp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2767">nx_tcp_socket_create、nx_tcp_socket_delete、nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="ff631-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="ff631-2768">nx_tcp_socket_info_get、nx_tcp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2769">nx_tcp_socket_receive_queue_max_set、nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="ff631-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="ff631-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="ff631-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="ff631-2771">時間指定された待機状態のコールバックをインストールします</span><span class="sxs-lookup"><span data-stu-id="ff631-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2772">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-2773">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2773">Description</span></span>

<span data-ttu-id="ff631-2774">このサービスを使用すると、TCP ソケットが時間指定した待機状態になったときに呼び出されるコールバック関数を登録できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="ff631-2775">このサービスを使用するには、オプションの ***NX_ENABLE_EXTENDED_NOTIFY*** を定義して NetX ライブラリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2776">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2776">Parameters</span></span>

- <span data-ttu-id="ff631-2777">**socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="ff631-2778">**tcp_timed_wait_callback** 時間指定された待機コールバック関数</span><span class="sxs-lookup"><span data-stu-id="ff631-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2779">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2779">Return Values</span></span>

- <span data-ttu-id="ff631-2780">**NX_SUCCESS** (0x00) コールバック関数ソケットが正常に登録されました</span><span class="sxs-lookup"><span data-stu-id="ff631-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="ff631-2781">**NX_NOT_SUPPORTED** (0x4B) この拡張通知機能を有効にせずに NetX ライブラリが構築されています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="ff631-2782">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2783">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2784">**NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2785">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2785">Allowed From</span></span>

<span data-ttu-id="ff631-2786">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2787">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2787">Preemption Possible</span></span>

<span data-ttu-id="ff631-2788">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2789">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="ff631-2790">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2790">See Also</span></span>

- <span data-ttu-id="ff631-2791">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2792">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2793">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2794">nx_tcp_socket_mss_peer_get、nx_tcp_socket_mss_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="ff631-2795">nx_tcp_socket_peer_info_get、nx_tcp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-2796">nx_tcp_socket_transmit_configure、</span><span class="sxs-lookup"><span data-stu-id="ff631-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="ff631-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="ff631-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="ff631-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="ff631-2799">ソケットの送信パラメーターを構成します</span><span class="sxs-lookup"><span data-stu-id="ff631-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2800">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="ff631-2801">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2801">Description</span></span>

<span data-ttu-id="ff631-2802">このサービスを使用すると、指定した TCP ソケットのさまざまな送信パラメーターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2803">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2803">Parameters</span></span>

- <span data-ttu-id="ff631-2804">**socket_ptr** TCP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="ff631-2805">**max_queue_depth** 送信するためにキューに入れることができるパケットの最大数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="ff631-2806">**timeout** パケットが再度送信される前に ACK が待機する ThreadX タイマー ティック数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="ff631-2807">**max_retries** 許可される最大再試行回数。</span><span class="sxs-lookup"><span data-stu-id="ff631-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="ff631-2808">**timeout_shift** 再試行のたびにタイムアウトをシフトする値。</span><span class="sxs-lookup"><span data-stu-id="ff631-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="ff631-2809">値が 0 の場合は、次の再試行との間のタイムアウトは同じになります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="ff631-2810">値が 1 の場合は、再試行の間のタイムアウトは 2 倍になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2811">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2811">Return Values</span></span>
- <span data-ttu-id="ff631-2812">**NX_SUCCESS** (0x00) 送信ソケットの構成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="ff631-2813">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-2814">**NX_OPTION_ERROR** (0x0a) キューの深度オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="ff631-2815">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2816">**NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2817">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2817">Allowed From</span></span>

<span data-ttu-id="ff631-2818">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2819">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2819">Preemption Possible</span></span>

<span data-ttu-id="ff631-2820">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2821">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2822">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2822">See Also</span></span>

- <span data-ttu-id="ff631-2823">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2824">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2825">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2826">nx_tcp_socket_mss_peer_get、nx_tcp_socket_mss_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="ff631-2827">nx_tcp_socket_peer_info_get、nx_tcp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-2828">nx_tcp_socket_timed_wait_callback、</span><span class="sxs-lookup"><span data-stu-id="ff631-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="ff631-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="ff631-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="ff631-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="ff631-2831">アプリケーションにウィンドウ サイズの更新を通知します</span><span class="sxs-lookup"><span data-stu-id="ff631-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2832">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-2833">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2833">Description</span></span>

<span data-ttu-id="ff631-2834">このサービスを使用すると、ソケット ウィンドウ更新コールバック ルーチンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="ff631-2835">このルーチンは、指定されたソケットがリモート ホストのウィンドウ サイズが増加したことを示すパケットを受信するたびに自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2836">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2836">Parameters</span></span>

- <span data-ttu-id="ff631-2837">**socket_ptr** 以前に作成された TCP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="ff631-2838">**tcp_window_update_notify** ウィンドウ サイズが変更されたときに呼び出されるコールバック ルーチン。</span><span class="sxs-lookup"><span data-stu-id="ff631-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="ff631-2839">NULL 値を指定すると、ウィンドウの変更更新は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2840">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2840">Return Values</span></span>
- <span data-ttu-id="ff631-2841">**NX_SUCCESS** (0x00) コールバック ルーチンがソケットにインストールされました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="ff631-2842">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2843">**NX_PTR_ERROR** (0x07) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="ff631-2844">**NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ff631-2845">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2845">Allowed From</span></span>

<span data-ttu-id="ff631-2846">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2847">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2847">Preemption Possible</span></span>

<span data-ttu-id="ff631-2848">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2849">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="ff631-2850">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2850">See Also</span></span>

- <span data-ttu-id="ff631-2851">nx_tcp_enable、nx_tcp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="ff631-2852">nx_tcp_socket_disconnect_complete_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="ff631-2853">nx_tcp_socket_establish_notify、nx_tcp_socket_mss_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="ff631-2854">nx_tcp_socket_mss_peer_get、nx_tcp_socket_mss_set、</span><span class="sxs-lookup"><span data-stu-id="ff631-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="ff631-2855">nx_tcp_socket_peer_info_get、nx_tcp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-2856">nx_tcp_socket_timed_wait_callback、nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="ff631-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="ff631-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-2857">nx_udp_enable</span></span>

<span data-ttu-id="ff631-2858">NetX の UDP コンポーネントを有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2859">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-2860">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2860">Description</span></span>

<span data-ttu-id="ff631-2861">このサービスを使用すると、NetX のユーザー データグラム プロトコル (UDP) コンポーネントが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="ff631-2862">有効にすると、アプリケーションで UDP データグラムを送受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff631-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2863">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2863">Parameters</span></span>

- <span data-ttu-id="ff631-2864">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2865">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2865">Return Values</span></span>

- <span data-ttu-id="ff631-2866">**NX_SUCCESS** (0x00) UDP の有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="ff631-2867">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-2868">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2869">**NX_ALREADY_ENABLED** (0x15) このコンポーネントは既に有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2870">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2870">Allowed From</span></span>

<span data-ttu-id="ff631-2871">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2872">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2872">Preemption Possible</span></span>

<span data-ttu-id="ff631-2873">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2874">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2875">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2875">See Also</span></span>

- <span data-ttu-id="ff631-2876">nx_udp_free_port_find、nx_udp_info_get、nx_udp_packet_info_extract、</span><span class="sxs-lookup"><span data-stu-id="ff631-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="ff631-2877">nx_udp_socket_bind、nx_udp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2878">nx_udp_socket_checksum_disable、nx_udp_socket_checksum_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="ff631-2879">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-2880">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2881">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-2882">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="ff631-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="ff631-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="ff631-2885">使用可能な次の UDP ポートを検索します</span><span class="sxs-lookup"><span data-stu-id="ff631-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2886">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-2887">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2887">Description</span></span>

<span data-ttu-id="ff631-2888">このサービスを使用すると、アプリケーションで指定されているポート番号を起点として、空いている UDP ポート (バインドされていない) の検索が行われます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="ff631-2889">この検索ロジックは、検索が最大ポート値の 0xFFFF に到達すると、ラップアラウンドします。</span><span class="sxs-lookup"><span data-stu-id="ff631-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="ff631-2890">検索が成功すると、*free_port_ptr* によってポイントされている変数に空きポートが返されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="ff631-2891">*このサービスが別のスレッドから呼び出されて、同じポートが返される場合があります。このような競合状態を回避するには、アプリケーションでこのサービスと実際のソケット バインドをミューテックスの保護下に置くことが必要になる場合があります。*</span><span class="sxs-lookup"><span data-stu-id="ff631-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2892">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2892">Parameters</span></span>

- <span data-ttu-id="ff631-2893">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2894">**port** 検索を開始するポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="ff631-2895">**free_port_ptr** 宛先の空きポートの戻り変数を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="ff631-2896">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2896">Return Values</span></span>

- <span data-ttu-id="ff631-2897">**NX_SUCCESS** (0x00) 空きポートの検索に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="ff631-2898">**NX_NO_FREE_PORTS** (0x45) 空きポートが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="ff631-2899">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-2900">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2901">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="ff631-2902">**NX_INVALID_PORT** (0x46) 指定されたポート番号が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2903">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2903">Allowed From</span></span>

<span data-ttu-id="ff631-2904">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2905">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2905">Preemption Possible</span></span>

<span data-ttu-id="ff631-2906">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2907">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2908">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2908">See Also</span></span>

- <span data-ttu-id="ff631-2909">nx_udp_enable、nx_udp_info_get、nx_udp_packet_info_extract、</span><span class="sxs-lookup"><span data-stu-id="ff631-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="ff631-2910">nx_udp_socket_bind、nx_udp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2911">nx_udp_socket_checksum_disable、nx_udp_socket_checksum_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="ff631-2912">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-2913">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2914">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-2915">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="ff631-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-2917">nx_udp_info_get</span></span>

<span data-ttu-id="ff631-2918">UDP アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2919">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="ff631-2920">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2920">Description</span></span>

<span data-ttu-id="ff631-2921">このサービスを使用すると、指定した IP インスタンスの UDP アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="ff631-2922">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2923">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2923">Parameters</span></span>

- <span data-ttu-id="ff631-2924">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-2925">**udp_packets_sent** 送信された UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="ff631-2926">**udp_bytes_sent** 送信された UDP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="ff631-2927">**udp_packets_received** 受信した UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="ff631-2928">**udp_bytes_received** 受信した UDP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="ff631-2929">**udp_invalid_packets** 無効な UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="ff631-2930">**udp_receive_packets_dropped** 破棄された UDP 受信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="ff631-2931">**udp_checksum_errors** チェックサム エラーが発生している UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2932">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2932">Return Values</span></span>

- <span data-ttu-id="ff631-2933">**NX_SUCCESS** (0x00) UDP 情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="ff631-2934">**NX_PTR_ERROR** (0x07) IP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="ff631-2935">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-2936">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ff631-2937">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2937">Allowed From</span></span>

<span data-ttu-id="ff631-2938">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2939">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2939">Preemption Possible</span></span>

<span data-ttu-id="ff631-2940">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2941">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2942">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2942">See Also</span></span>

- <span data-ttu-id="ff631-2943">nx_udp_enable、nx_udp_free_port_find、nx_udp_packet_info_extract、</span><span class="sxs-lookup"><span data-stu-id="ff631-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="ff631-2944">nx_udp_socket_bind、nx_udp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2945">nx_udp_socket_checksum_disable、nx_udp_socket_checksum_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="ff631-2946">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-2947">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2948">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-2949">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="ff631-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="ff631-2952">UDP パケットからネットワーク パラメーターを抽出します</span><span class="sxs-lookup"><span data-stu-id="ff631-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2953">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="ff631-2954">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2954">Description</span></span>

<span data-ttu-id="ff631-2955">このサービスを使用すると、IP アドレス、ピア ポート番号、プロトコルの種類 (このサービスでは常に UDP の種類が返されます) などのネットワーク パラメーターを、受信インターフェイスで受信したパケットから抽出できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2956">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2956">Parameters</span></span>

- <span data-ttu-id="ff631-2957">**packet_ptr** パケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="ff631-2958">**ip_address** 送信元 IP アドレスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="ff631-2959">**protocol** プロトコル (UDP) を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="ff631-2960">**port** 送信者のポート番号を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="ff631-2961">**interface_index** 受信インターフェイス インデックスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2962">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2962">Return Values</span></span>

- <span data-ttu-id="ff631-2963">**NX_SUCCESS** (0x00) パケット インターフェイス データが正常に抽出されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="ff631-2964">**NX_INVALID_PACKET** (0x12) パケットに IP フレームが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="ff631-2965">**NX_PTR_ERROR** (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ff631-2966">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-2967">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-2967">Allowed From</span></span>

<span data-ttu-id="ff631-2968">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-2969">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-2969">Preemption Possible</span></span>

<span data-ttu-id="ff631-2970">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-2971">例</span><span class="sxs-lookup"><span data-stu-id="ff631-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-2972">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-2972">See Also</span></span>

- <span data-ttu-id="ff631-2973">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-2974">nx_udp_socket_bind、nx_udp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-2975">nx_udp_socket_checksum_disable、nx_udp_socket_checksum_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="ff631-2976">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-2977">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-2978">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-2979">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="ff631-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="ff631-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="ff631-2982">UDP ソケットを UDP ポートにバインドします</span><span class="sxs-lookup"><span data-stu-id="ff631-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-2983">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-2984">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-2984">Description</span></span>

<span data-ttu-id="ff631-2985">このサービスを使用すると、以前作成した UDP ソケットが、指定した UDP ポートにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="ff631-2986">有効な UDP ソケットの範囲は 0 から 0xFFFF です。</span><span class="sxs-lookup"><span data-stu-id="ff631-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="ff631-2987">要求されたポート番号が別のソケットにバインドされている場合、このサービスは、そのポート番号からソケットがバインド解除されるまで、指定された時間待機します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-2988">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-2988">Parameters</span></span>

- <span data-ttu-id="ff631-2989">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="ff631-2990">**port** バインド先のポート番号 (1 から 0xFFFF)。</span><span class="sxs-lookup"><span data-stu-id="ff631-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="ff631-2991">ポート番号が NX_ANY_PORT (0x0000) の場合、IP インスタンスは次の空きポートを検索し、そのポートをバインドに使用します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="ff631-2992">**wait_option** ポートが既に別のソケットにバインドされている場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="ff631-2993">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-2994">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-2996">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-2997">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-2997">Return Values</span></span>

- <span data-ttu-id="ff631-2998">**NX_SUCCESS** (0x00) ソケットのバインドに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="ff631-2999">**NX_ALREADY_BOUND** (0x22) このソケットは既に別のポートにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="ff631-3000">**NX_PORT_UNAVAILABLE** (0x23) ポートは既に別のソケットにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="ff631-3001">**NX_NO_FREE_PORTS** (0x45) 空きポートがありません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="ff631-3002">**NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="ff631-3003">**NX_INVALID_PORT** (0x46) 指定されたポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="ff631-3004">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-3005">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3006">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3007">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3007">Allowed From</span></span>

<span data-ttu-id="ff631-3008">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3009">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3009">Preemption Possible</span></span>

<span data-ttu-id="ff631-3010">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3011">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-3012">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3012">See Also</span></span>

- <span data-ttu-id="ff631-3013">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3014">nx_udp_packet_info_extract、nx_udp_socket_bytes_available、</span><span class="sxs-lookup"><span data-stu-id="ff631-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="ff631-3015">nx_udp_socket_checksum_disable、nx_udp_socket_checksum_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="ff631-3016">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3017">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3018">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3019">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="ff631-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="ff631-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="ff631-3022">取得可能なバイト数を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3023">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="ff631-3024">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3024">Description</span></span>

<span data-ttu-id="ff631-3025">このサービスを使用すると、指定した UDP ソケットでの受信に使用可能なバイト数が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3026">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3026">Parameters</span></span>

- <span data-ttu-id="ff631-3027">**socket_ptr** 以前に作成された UDP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="ff631-3028">**bytes_available** 使用可能なバイトの宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3029">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3029">Return Values</span></span>

- <span data-ttu-id="ff631-3030">**NX_SUCCESS** (0x00) 使用可能なバイト数の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="ff631-3031">**NX_NOT_SUCCESSFUL** (0x43) ソケットがポートにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="ff631-3032">**NX_PTR_ERROR** (0x07) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="ff631-3033">**NX_NOT_ENABLED** (0x14) UDP 機能が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="ff631-3034">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3035">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3035">Allowed From</span></span>

<span data-ttu-id="ff631-3036">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3037">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3037">Preemption Possible</span></span>

<span data-ttu-id="ff631-3038">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3039">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-3040">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3040">See Also</span></span>

- <span data-ttu-id="ff631-3041">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3042">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3043">nx_udp_socket_checksum_disable、nx_udp_socket_checksum_enable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="ff631-3044">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3045">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3046">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3047">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="ff631-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="ff631-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="ff631-3050">UDP ソケットのチェックサムを無効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3051">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-3052">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3052">Description</span></span>

<span data-ttu-id="ff631-3053">このサービスを使用すると、指定した UDP ソケットでパケットを送受信するためのチェックサム ロジックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="ff631-3054">チェックサム ロジックが無効になっている場合、このソケットを介して送信されるすべてのパケットの UDP ヘッダーのチェックサム フィールドに値 0 が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="ff631-3055">UDP ヘッダーのゼロ値のチェックサム値は、このパケットのチェックサムが計算されていないことを受信者に示す働きをします。</span><span class="sxs-lookup"><span data-stu-id="ff631-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="ff631-3056">また、UDP パケットの受信と送信で、それぞれ ***NX_DISABLE_UDP_RX_CHECKSUM** _ および _ *_NX_DISABLE_UDP_TX_CHECKSUM_** が定義されている場合は、このサービスに効果はないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3057">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3057">Parameters</span></span>

- <span data-ttu-id="ff631-3058">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3059">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3059">Return Values</span></span>

- <span data-ttu-id="ff631-3060">**NX_SUCCESS** (0x00) ソケットのチェックサムの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="ff631-3061">**NX_NOT_BOUND** (0x24) ソケットがバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="ff631-3062">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-3063">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3064">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3065">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3065">Allowed From</span></span>

<span data-ttu-id="ff631-3066">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3067">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3067">Preemption Possible</span></span>

<span data-ttu-id="ff631-3068">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3069">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3070">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3070">See Also</span></span>

- <span data-ttu-id="ff631-3071">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3072">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3073">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3074">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3075">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3076">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3077">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="ff631-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="ff631-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="ff631-3080">UDP ソケットのチェックサムを有効にします</span><span class="sxs-lookup"><span data-stu-id="ff631-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3081">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-3082">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3082">Description</span></span>

<span data-ttu-id="ff631-3083">このサービスを使用すると、指定した UDP ソケットでパケットを送受信するためのチェックサム ロジックが有効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="ff631-3084">このチェックサムでは、UDP データ領域全体と擬似 IP ヘッダーが対象になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="ff631-3085">また、UDP パケットの受信と送信で、それぞれ **NX_DISABLE_UDP_RX_CHECKSUM** および **NX_DISABLE_UDP_TX_CHECKSUM** が定義されている場合は、このサービスに効果はないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ff631-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3086">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3086">Parameters</span></span>

- <span data-ttu-id="ff631-3087">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3088">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3088">Return Values</span></span>

- <span data-ttu-id="ff631-3089">**NX_SUCCESS** (0x00) ソケットのチェックサムの有効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="ff631-3090">**NX_NOT_BOUND** (0x24) ソケットがバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="ff631-3091">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-3092">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3093">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3094">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3094">Allowed From</span></span>

<span data-ttu-id="ff631-3095">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3096">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3096">Preemption Possible</span></span>

<span data-ttu-id="ff631-3097">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3098">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3099">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3099">See Also</span></span>

- <span data-ttu-id="ff631-3100">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3101">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3102">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3103">nx_udp_socket_create、nx_udp_socket_delete、nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="ff631-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3104">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3105">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3106">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="ff631-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="ff631-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="ff631-3109">UDP ソケットを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3110">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="ff631-3111">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3111">Description</span></span>

<span data-ttu-id="ff631-3112">このサービスを使用すると、指定した IP インスタンスの UDP ソケットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3113">Parameters</span></span>

- <span data-ttu-id="ff631-3114">**ip_ptr** 以前に作成された IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ff631-3115">**socket_ptr** 新しい UDP ソケット制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="ff631-3116">**name** この UDP ソケットのアプリケーション名。</span><span class="sxs-lookup"><span data-stu-id="ff631-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="ff631-3117">**type_of_service** 送信のためのサービスの種類を定義します。有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ff631-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="ff631-3118">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="ff631-3119">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="ff631-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="ff631-3120">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="ff631-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="ff631-3121">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="ff631-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="ff631-3122">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="ff631-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="ff631-3123">**fragment** IP のフラグメント化を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="ff631-3124">NX_FRAGMENT_OKAY (0x0) が指定されている場合は、IP のフラグメント化が許可されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="ff631-3125">NX_DONT_FRAGMENT (0x4000) が指定されている場合は、IP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="ff631-3126">**time_to_live** このパケットが破棄されるまでに通過できるルーターの数を定義する 8 ビットの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="ff631-3127">既定値は NX_IP_TIME_TO_LIVE によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="ff631-3128">**queue_maximum** このソケットのキューに入れることができる UDP データグラムの最大数を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="ff631-3129">キューの上限に達すると、新しいパケットを受信するたびに、最も古い UDP パケットが解放されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3130">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3130">Return Values</span></span>

- <span data-ttu-id="ff631-3131">**NX_SUCCESS** (0x00) UDP ソケットの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="ff631-3132">**NX_OPTION_ERROR** (0x0A) サービスの種類、フラグメント、または有効期限オプションが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="ff631-3133">**NX_PTR_ERROR** (0x07) IP またはソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="ff631-3134">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3135">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3136">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3136">Allowed From</span></span>

<span data-ttu-id="ff631-3137">初期化およびスレッド</span><span class="sxs-lookup"><span data-stu-id="ff631-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3138">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3138">Preemption Possible</span></span>

<span data-ttu-id="ff631-3139">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3140">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3141">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3141">See Also</span></span>

- <span data-ttu-id="ff631-3142">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3143">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3144">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3145">nx_udp_socket_checksum_enable、nx_udp_socket_delete、</span><span class="sxs-lookup"><span data-stu-id="ff631-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="ff631-3146">nx_udp_socket_info_get、nx_udp_socket_port_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="ff631-3147">nx_udp_socket_receive、nx_udp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-3148">nx_udp_socket_send、nx_udp_socket_interface_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="ff631-3149">nx_udp_socket_unbind、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="ff631-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="ff631-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="ff631-3151">UDP ソケットを削除します</span><span class="sxs-lookup"><span data-stu-id="ff631-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3152">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-3153">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3153">Description</span></span>

<span data-ttu-id="ff631-3154">このサービスを使用すると、以前に作成された UDP ソケットが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="ff631-3155">ソケットがポートにバインドされている場合は、最初にソケットをバインド解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3156">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3156">Parameters</span></span>

- <span data-ttu-id="ff631-3157">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3158">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3158">Return Values</span></span>

- <span data-ttu-id="ff631-3159">**NX_SUCCESS** (0x00) ソケットの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="ff631-3160">**NX_STILL_BOUND** (0x42) ソケットはまだバインドされています。</span><span class="sxs-lookup"><span data-stu-id="ff631-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="ff631-3161">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-3162">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3163">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3164">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3164">Allowed From</span></span>

<span data-ttu-id="ff631-3165">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3166">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3166">Preemption Possible</span></span>

<span data-ttu-id="ff631-3167">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3168">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3169">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3169">See Also</span></span>

- <span data-ttu-id="ff631-3170">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3171">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3172">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3173">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3174">nx_udp_socket_info_get、nx_udp_socket_port_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="ff631-3175">nx_udp_socket_receive、nx_udp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-3176">nx_udp_socket_send、nx_udp_socket_interface_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="ff631-3177">nx_udp_socket_unbind、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="ff631-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="ff631-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="ff631-3179">UDP ソケット アクティビティに関する情報を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3180">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="ff631-3181">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3181">Description</span></span>

<span data-ttu-id="ff631-3182">このサービスを使用すると、指定した UDP ソケット インスタンスの UDP ソケット アクティビティに関する情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="ff631-3183">*宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。</span><span class="sxs-lookup"><span data-stu-id="ff631-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3184">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3184">Parameters</span></span>

- <span data-ttu-id="ff631-3185">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="ff631-3186">**udp_packets_sent** ソケットで送信された UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="ff631-3187">**udp_bytes_sent** ソケットで送信された UDP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="ff631-3188">**udp_packets_received** ソケットで受信した UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="ff631-3189">**udp_bytes_received** ソケットで受信した UDP バイトの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="ff631-3190">**udp_packets_queued** ソケットでキューに入れられた UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="ff631-3191">**udp_receive_packets_dropped** キューのサイズを超えたため、ソケットに対して破棄された UDP 受信パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="ff631-3192">**tcp_checksum_errors** ソケットでチェックサム エラーが発生している UDP パケットの合計数の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3193">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3193">Return Values</span></span>

- <span data-ttu-id="ff631-3194">**NX_SUCCESS** (0x00) UDP ソケット情報の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="ff631-3195">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-3196">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3197">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3198">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3198">Allowed From</span></span>

<span data-ttu-id="ff631-3199">初期化、スレッド、タイマー</span><span class="sxs-lookup"><span data-stu-id="ff631-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3200">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3200">Preemption Possible</span></span>

<span data-ttu-id="ff631-3201">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3202">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-3203">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3203">See Also</span></span>

- <span data-ttu-id="ff631-3204">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3205">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3206">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3207">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3208">nx_udp_socket_delete、nx_udp_socket_port_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="ff631-3209">nx_udp_socket_receive、nx_udp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-3210">nx_udp_socket_send、nx_udp_socket_interface_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="ff631-3211">nx_udp_socket_unbind、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="ff631-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="ff631-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="ff631-3213">UDP ソケットにバインドされているポート番号を取得します</span><span class="sxs-lookup"><span data-stu-id="ff631-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3214">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-3215">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3215">Description</span></span>

<span data-ttu-id="ff631-3216">このサービスを使用すると、ソケットに関連付けられているポート番号が取得されます。これは、ソケットのバインド時に NX_ANY_PORT が指定された場合に NetX によって割り当てられたポートを見つけるのに便利です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3217">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3217">Parameters</span></span>

- <span data-ttu-id="ff631-3218">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="ff631-3219">**port_ptr** 戻りポート番号の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="ff631-3220">有効なポート番号は (1 から 0xFFFF) です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3221">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3221">Return Values</span></span>

- <span data-ttu-id="ff631-3222">**NX_SUCCESS** (0x00) ソケットのバインドに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="ff631-3223">**NX_NOT_BOUND** (0x24) このソケットはポートにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="ff631-3224">**NX_PTR_ERROR** (0x07) ソケット ポインターまたはポートの戻りポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="ff631-3225">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3226">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3227">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3227">Allowed From</span></span>

<span data-ttu-id="ff631-3228">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3229">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3229">Preemption Possible</span></span>

<span data-ttu-id="ff631-3230">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3231">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3232">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3232">See Also</span></span>

- <span data-ttu-id="ff631-3233">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3234">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3235">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3236">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3237">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3238">nx_udp_socket_receive、nx_udp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-3239">nx_udp_socket_send、nx_udp_socket_interface_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="ff631-3240">nx_udp_socket_unbind、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="ff631-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="ff631-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="ff631-3242">UDP ソケットからデータグラムを受信します</span><span class="sxs-lookup"><span data-stu-id="ff631-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3243">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ff631-3244">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3244">Description</span></span>

<span data-ttu-id="ff631-3245">このサービスを使用すると、指定したソケットから UDP データグラムを受信できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="ff631-3246">指定されたソケットでキューに入れられたデータグラムが存在しない場合は、指定された待機オプションに基づいて呼び出し元が中断されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="ff631-3247">*NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします。*</span><span class="sxs-lookup"><span data-stu-id="ff631-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3248">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3248">Parameters</span></span>

- <span data-ttu-id="ff631-3249">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="ff631-3250">**packet_ptr** UDP データグラム パケット ポインターを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="ff631-3251">**wait_option** このソケットで現在キューに入れられたデータグラムが存在しない場合のサービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="ff631-3252">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="ff631-3253">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="ff631-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="ff631-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="ff631-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="ff631-3255">タイムアウト値 (ティック数) (0x00000001 から 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="ff631-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3256">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3256">Allowed From</span></span>

<span data-ttu-id="ff631-3257">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3258">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3258">Preemption Possible</span></span>

<span data-ttu-id="ff631-3259">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3260">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3261">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3261">See Also</span></span>

- <span data-ttu-id="ff631-3262">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3263">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3264">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3265">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3266">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3267">nx_udp_socket_port_get、nx_udp_socket_receive_notify、</span><span class="sxs-lookup"><span data-stu-id="ff631-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="ff631-3268">nx_udp_socket_send、nx_udp_socket_interface_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="ff631-3269">nx_udp_socket_unbind、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="ff631-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="ff631-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="ff631-3271">受信した各パケットをアプリケーションに通知します</span><span class="sxs-lookup"><span data-stu-id="ff631-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3272">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="ff631-3273">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3273">Description</span></span>

<span data-ttu-id="ff631-3274">このサービスを使用すると、受信通知関数ポインターが、アプリケーションによって指定されたコールバック関数に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="ff631-3275">このコールバック関数は、ソケットでパケットが受信されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="ff631-3276">NX_NULL ポインターが指定されている場合、この受信通知関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3277">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3277">Parameters</span></span>

- <span data-ttu-id="ff631-3278">**socket_ptr** UDP ソケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="ff631-3279">**udp_receive_notify** ソケットでパケットを受信したときに呼び出されるアプリケーション コールバック関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3280">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3280">Allowed From</span></span>

<span data-ttu-id="ff631-3281">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3282">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3282">Preemption Possible</span></span>

<span data-ttu-id="ff631-3283">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3284">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3285">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3285">See Also</span></span>

- <span data-ttu-id="ff631-3286">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3287">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3288">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3289">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3290">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3291">nx_udp_socket_port_get、nx_udp_socket_receive、nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="ff631-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3292">nx_udp_socket_interface_send、nx_udp_socket_unbind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="ff631-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="ff631-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="ff631-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="ff631-3295">UDP データグラムを送信します</span><span class="sxs-lookup"><span data-stu-id="ff631-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3296">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="ff631-3297">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3297">Description</span></span>

<span data-ttu-id="ff631-3298">このサービスを使用すると、以前に作成され、バインドされた UDP ソケットを介して UDP データグラムが送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="ff631-3299">NetX は、宛先 IP アドレスに基づいて、適切なローカル IP アドレスをソース アドレスとして検索します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="ff631-3300">特定のインターフェイスと発信元 IP アドレスを指定するには、アプリケーションでは **nx_udp_socket_interface_send** サービスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="ff631-3301">このサービスは、UDP データグラムが正常に送信されたかどうかに関係なく、直ちに返されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff631-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="ff631-3302">ソケットはローカル ポートにバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff631-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3303">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3303">Parameters</span></span>

- <span data-ttu-id="ff631-3304">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター</span><span class="sxs-lookup"><span data-stu-id="ff631-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="ff631-3305">**packet_ptr** UDP データグラム パケット ポインター</span><span class="sxs-lookup"><span data-stu-id="ff631-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="ff631-3306">**ip_address** 宛先 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="ff631-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="ff631-3307">**port** 1 から 0xFFFF の範囲の有効な宛先ポート番号 (ホストのバイト順)</span><span class="sxs-lookup"><span data-stu-id="ff631-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3308">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3308">Return Values</span></span>

- <span data-ttu-id="ff631-3309">**NX_SUCCESS** (0x00) UDP ソケットの送信に成功しました</span><span class="sxs-lookup"><span data-stu-id="ff631-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="ff631-3310">**NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていません</span><span class="sxs-lookup"><span data-stu-id="ff631-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="ff631-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="ff631-3312">**NX_IP_ADDRESS_ERROR** (0x21) サーバー IP アドレスが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="ff631-3313">**NX_UNDERFLOW** (0x02) パケット内の UDP ヘッダーに十分な領域がありません</span><span class="sxs-lookup"><span data-stu-id="ff631-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="ff631-3314">**NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="ff631-3315">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="ff631-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="ff631-3316">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ff631-3317">**NX_NOT_ENABLED** (0x14) UDP が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="ff631-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="ff631-3318">**NX_INVALID_PORT** (0x46) ポート番号が有効な範囲内ではありません</span><span class="sxs-lookup"><span data-stu-id="ff631-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3319">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3319">Allowed From</span></span>

<span data-ttu-id="ff631-3320">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3321">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3321">Preemption Possible</span></span>

<span data-ttu-id="ff631-3322">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3323">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3324">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3324">See Also</span></span>

- <span data-ttu-id="ff631-3325">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3326">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3327">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3328">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3329">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3330">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3331">nx_udp_socket_receive_notify、nx_udp_socket_interface_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="ff631-3332">nx_udp_socket_unbind、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="ff631-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="ff631-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="ff631-3334">UDP ソケット経由でデータグラムを送信します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3335">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="ff631-3336">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3336">Description</span></span>

<span data-ttu-id="ff631-3337">このサービスを使用すると、指定した IP アドレスを発信元アドレスとするネットワーク インターフェイスを経由して、以前に作成され、バインドされた UDP ソケットを介して UDP データグラムが送信されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="ff631-3338">このサービスは、UDP データグラムが正常に送信されたかどうかに関係なく、直ちに返されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ff631-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3339">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3339">Parameters</span></span>

- <span data-ttu-id="ff631-3340">**socket_ptr** パケットを送信するソケット。</span><span class="sxs-lookup"><span data-stu-id="ff631-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="ff631-3341">**packet_ptr** 送信するパケットを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="ff631-3342">**ip_address** パケットを送信する宛先 IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ff631-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="ff631-3343">**port** 宛先ポート。</span><span class="sxs-lookup"><span data-stu-id="ff631-3343">**port** Destination port.</span></span>
- <span data-ttu-id="ff631-3344">**address_index** パケットを送信するインターフェイスに関連付けられているアドレスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="ff631-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3345">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3345">Return Values</span></span>

- <span data-ttu-id="ff631-3346">**NX_SUCCESS** (0x00) パケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="ff631-3347">**NX_NOT_BOUND** (0x24) ソケットがポートにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="ff631-3348">**NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="ff631-3349">**NX_NOT_ENABLED** (0x14) UDP 処理が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="ff631-3350">**NX_PTR_ERROR** (0x07) ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="ff631-3351">**NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="ff631-3352">**NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="ff631-3353">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3354">**NX_INVALID_INTERFACE** (0x4C) アドレス インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="ff631-3355">**NX_INVALID_PORT** (0x46) ポート番号がポート番号の最大値を超えています。</span><span class="sxs-lookup"><span data-stu-id="ff631-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3356">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3356">Allowed From</span></span>

<span data-ttu-id="ff631-3357">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3358">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3358">Preemption Possible</span></span>

<span data-ttu-id="ff631-3359">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3360">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3361">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3361">See Also</span></span>

- <span data-ttu-id="ff631-3362">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3363">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3364">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3365">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3366">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3367">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3368">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="ff631-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="ff631-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="ff631-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="ff631-3371">UDP ポートから UDP ソケットをバインド解除します。</span><span class="sxs-lookup"><span data-stu-id="ff631-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3372">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="ff631-3373">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3373">Description</span></span>

<span data-ttu-id="ff631-3374">このサービスを使用すると、UDP ソケットと UDP ポート間のバインドが解除されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="ff631-3375">受信キューに格納されている受信パケットは、バインド解除操作の一部として解放されます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="ff631-3376">他のスレッドが非バインド ポートに別のソケットをバインドするために待機している場合は、中断されている最初のスレッドが新しい非バインド ポートにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3377">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3377">Parameters</span></span>

- <span data-ttu-id="ff631-3378">**socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3379">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3379">Return Values</span></span>

- <span data-ttu-id="ff631-3380">**NX_SUCCESS** (0x00) ソケットのバインド解除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="ff631-3381">**NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ff631-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="ff631-3382">**NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="ff631-3383">**NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ff631-3384">**NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="ff631-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3385">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3385">Allowed From</span></span>

<span data-ttu-id="ff631-3386">Threads</span><span class="sxs-lookup"><span data-stu-id="ff631-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3387">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3387">Preemption Possible</span></span>

<span data-ttu-id="ff631-3388">はい</span><span class="sxs-lookup"><span data-stu-id="ff631-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3389">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="ff631-3390">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3390">See Also</span></span>

- <span data-ttu-id="ff631-3391">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3392">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3393">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3394">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3395">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3396">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3397">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3398">nx_udp_socket_interface_send、nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="ff631-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="ff631-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="ff631-3400">UDP データグラムから IP と送信ポートを抽出します</span><span class="sxs-lookup"><span data-stu-id="ff631-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="ff631-3401">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="ff631-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="ff631-3402">説明</span><span class="sxs-lookup"><span data-stu-id="ff631-3402">Description</span></span>

<span data-ttu-id="ff631-3403">このサービスを使用すると、指定した UDP データグラムの IP および UDP ヘッダーから送信者の IP とポート番号を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="ff631-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="ff631-3404">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff631-3404">Parameters</span></span>

- <span data-ttu-id="ff631-3405">**packet_ptr** UDP データグラム パケット ポインター。</span><span class="sxs-lookup"><span data-stu-id="ff631-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="ff631-3406">**ip_address** 戻り IP アドレス変数への有効なポインターです。</span><span class="sxs-lookup"><span data-stu-id="ff631-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="ff631-3407">**port** 戻りポート変数への有効なポインターです。</span><span class="sxs-lookup"><span data-stu-id="ff631-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="ff631-3408">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff631-3408">Return Values</span></span>

- <span data-ttu-id="ff631-3409">**NX_SUCCESS** (0x00) 送信元 IP またはポートの抽出が成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff631-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="ff631-3410">**NX_INVALID_PACKET** (0x12) 指定されたパケットが無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="ff631-3411">**NX_PTR_ERROR** (0x07) パケット、IP、またはポートの宛先が無効です。</span><span class="sxs-lookup"><span data-stu-id="ff631-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff631-3412">許可元</span><span class="sxs-lookup"><span data-stu-id="ff631-3412">Allowed From</span></span>

<span data-ttu-id="ff631-3413">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="ff631-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="ff631-3414">プリエンプション可能</span><span class="sxs-lookup"><span data-stu-id="ff631-3414">Preemption Possible</span></span>

<span data-ttu-id="ff631-3415">いいえ</span><span class="sxs-lookup"><span data-stu-id="ff631-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="ff631-3416">例</span><span class="sxs-lookup"><span data-stu-id="ff631-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="ff631-3417">参照</span><span class="sxs-lookup"><span data-stu-id="ff631-3417">See Also</span></span>

- <span data-ttu-id="ff631-3418">nx_udp_enable、nx_udp_free_port_find、nx_udp_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="ff631-3419">nx_udp_packet_info_extract、nx_udp_socket_bind、</span><span class="sxs-lookup"><span data-stu-id="ff631-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="ff631-3420">nx_udp_socket_bytes_available、nx_udp_socket_checksum_disable、</span><span class="sxs-lookup"><span data-stu-id="ff631-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="ff631-3421">nx_udp_socket_checksum_enable、nx_udp_socket_create、</span><span class="sxs-lookup"><span data-stu-id="ff631-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="ff631-3422">nx_udp_socket_delete、nx_udp_socket_info_get、</span><span class="sxs-lookup"><span data-stu-id="ff631-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="ff631-3423">nx_udp_socket_port_get、nx_udp_socket_receive、</span><span class="sxs-lookup"><span data-stu-id="ff631-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="ff631-3424">nx_udp_socket_receive_notify、nx_udp_socket_send、</span><span class="sxs-lookup"><span data-stu-id="ff631-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="ff631-3425">nx_udp_socket_interface_send、nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="ff631-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>