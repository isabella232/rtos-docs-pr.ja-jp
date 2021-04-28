---
title: 第 4 章 - mDNS サービスの説明
description: この章では、すべての NetX mDNS サービスについて説明します
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810733"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="758f4-103">第 4 章 - mDNS サービスの説明</span><span class="sxs-lookup"><span data-stu-id="758f4-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="758f4-104">この章では、すべての NetX mDNS サービスについて説明します (以下の一覧を参照)。</span><span class="sxs-lookup"><span data-stu-id="758f4-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="758f4-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="758f4-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="758f4-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="758f4-106">nx_mdns_create</span></span>

<span data-ttu-id="758f4-107">mDNS インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="758f4-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="758f4-109">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-109">Description</span></span>

<span data-ttu-id="758f4-110">このサービスは、特定の IP インスタンスとその関連リソース上に mDNS インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="758f4-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="758f4-111">受信した mDNS メッセージを処理し、クエリに応答して、定期的にクエリ メッセージを送信するためのスレッドも作成されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-112">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-112">Input Parameters</span></span>

- <span data-ttu-id="758f4-113">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-114">**ip_ptr**: 関連付けられている IP インスタンスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="758f4-115">**packet_pool**: 有効なパケット プールを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="758f4-116">**priority**: mDNS スレッドの優先度。</span><span class="sxs-lookup"><span data-stu-id="758f4-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="758f4-117">**stack_ptr**: mDNS スレッドのスタック領域を指すポインター</span><span class="sxs-lookup"><span data-stu-id="758f4-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="758f4-118">**stack_size**: スタック領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="758f4-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="758f4-119">**host_name**: このノードに割り当てられたホスト名。</span><span class="sxs-lookup"><span data-stu-id="758f4-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="758f4-120">**local_service_cache**: ローカルに登録されているサービス用の記憶領域。</span><span class="sxs-lookup"><span data-stu-id="758f4-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="758f4-121">**local_service_cache_size**: ローカル サービス キャッシュのサイズ。</span><span class="sxs-lookup"><span data-stu-id="758f4-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="758f4-122">**peer_service_cache**: 受信したサービス情報用の記憶領域</span><span class="sxs-lookup"><span data-stu-id="758f4-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="758f4-123">**peer_service_cache_size**: ピア サービス キャッシュのサイズ</span><span class="sxs-lookup"><span data-stu-id="758f4-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="758f4-124">**probing_notify**: プローブ操作の最後に呼び出される省略可能なコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="758f4-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="758f4-125">ホスト名 (ローカル インターフェイスで mDNS を有効にする場合) またはサービス名 (サービスの登録後) が一意であるかどうかをアプリケーションに通知します。</span><span class="sxs-lookup"><span data-stu-id="758f4-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-126">Return Values</span></span>

- <span data-ttu-id="758f4-127">**NX_SUCCESS** (0x00): mDNS インスタンスが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-128">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-128">Allowed From</span></span>

<span data-ttu-id="758f4-129">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-130">例</span><span class="sxs-lookup"><span data-stu-id="758f4-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="758f4-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="758f4-131">nx_mdns_delete</span></span>

<span data-ttu-id="758f4-132">mDNS インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="758f4-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-133">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="758f4-134">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-134">Description</span></span>

<span data-ttu-id="758f4-135">このサービスは、mDNS インスタンスを削除し、そのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="758f4-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-136">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-136">Input Parameters</span></span>

- <span data-ttu-id="758f4-137">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-138">Return Values</span></span>

- <span data-ttu-id="758f4-139">**NX_SUCCESS** (0x00): mDNS インスタンスが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-140">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-140">Allowed From</span></span>

<span data-ttu-id="758f4-141">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-142">例</span><span class="sxs-lookup"><span data-stu-id="758f4-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="758f4-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="758f4-143">nx_mdns_enable</span></span>

<span data-ttu-id="758f4-144">mDNS サービスを開始します</span><span class="sxs-lookup"><span data-stu-id="758f4-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-145">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="758f4-146">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-146">Description</span></span>

<span data-ttu-id="758f4-147">この API は、特定の物理インターフェイスで mDNS サービスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="758f4-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="758f4-148">サービスが有効になると、mDNS モジュールは、まず、ネットワーク上のそのすべての一意のサービス名をプローブしてから、インターフェイスで受信したクエリに応答します。</span><span class="sxs-lookup"><span data-stu-id="758f4-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-149">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-149">Input Parameters</span></span>

- <span data-ttu-id="758f4-150">**mdns_ptr**: mDNS インスタンス制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="758f4-151">**interface_index**: サービスを有効にするインターフェイスへのインデックス</span><span class="sxs-lookup"><span data-stu-id="758f4-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-152">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-152">Return Values</span></span>

- <span data-ttu-id="758f4-153">**NX_SUCCESS** (0x00): サービスが正常に有効になりました。</span><span class="sxs-lookup"><span data-stu-id="758f4-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-154">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-154">Allowed From</span></span>

<span data-ttu-id="758f4-155">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-156">例</span><span class="sxs-lookup"><span data-stu-id="758f4-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="758f4-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="758f4-157">nx_mdns_disable</span></span>

<span data-ttu-id="758f4-158">mDNS サービスを無効にします</span><span class="sxs-lookup"><span data-stu-id="758f4-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-159">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="758f4-160">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-160">Description</span></span>

<span data-ttu-id="758f4-161">この API は、特定の物理インターフェイスで mDNS サービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="758f4-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="758f4-162">サービスが無効になると、mDNS は、インターフェイスに接続されているネットワークに対してすべてのローカル サービスの "goodbye" メッセージを送信するため、隣接ノードに通知されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-163">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-163">Input Parameters</span></span>

- <span data-ttu-id="758f4-164">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-165">**interface_index**: サービスを無効にするインターフェイスへのインデックス</span><span class="sxs-lookup"><span data-stu-id="758f4-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-166">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-166">Return Values</span></span>

- <span data-ttu-id="758f4-167">**NX_SUCCESS** (0x00): サービスが正常に無効になりました。</span><span class="sxs-lookup"><span data-stu-id="758f4-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-168">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-168">Allowed From</span></span>

<span data-ttu-id="758f4-169">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-170">例</span><span class="sxs-lookup"><span data-stu-id="758f4-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="758f4-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="758f4-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="758f4-172">mDNS のキャッシュ満杯通知関数をインストールします</span><span class="sxs-lookup"><span data-stu-id="758f4-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="758f4-174">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-174">Description</span></span>

<span data-ttu-id="758f4-175">このサービスは、ローカル サービス キャッシュまたはピア サービス キャッシュのいずれかがいっぱいになったときに呼び出される、ユーザー指定のコールバック関数をインストールします。</span><span class="sxs-lookup"><span data-stu-id="758f4-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="758f4-176">サービス キャッシュがいっぱいになると、mDNS リソース レコードをそれ以上追加できなくなります。</span><span class="sxs-lookup"><span data-stu-id="758f4-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="758f4-177">さまざまな文字列長のサービスが追加されたり削除されたりすると、内部断片化の結果としてサービス キャッシュがいっぱいになる可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="758f4-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="758f4-178">アプリケーションは、ピア サービス キャッシュのキャッシュがいっぱいという通知を受信すると、サービス "*nx_mdns_service_cache_clear*" を使用して、ピア サービス キャッシュ内のすべてのエントリを消去できます。</span><span class="sxs-lookup"><span data-stu-id="758f4-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-179">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-179">Input Parameters</span></span>

- <span data-ttu-id="758f4-180">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-181">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-181">Return Values</span></span>

- <span data-ttu-id="758f4-182">**NX_SUCCESS** (0x00): mDNS のキャッシュ通知コールバック関数が正常にインストールされました。</span><span class="sxs-lookup"><span data-stu-id="758f4-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-183">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-183">Allowed From</span></span>

<span data-ttu-id="758f4-184">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-185">例</span><span class="sxs-lookup"><span data-stu-id="758f4-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="758f4-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="758f4-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="758f4-187">mDNS のサービス キャッシュ満杯通知関数をクリアします</span><span class="sxs-lookup"><span data-stu-id="758f4-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-188">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="758f4-189">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-189">Description</span></span>

<span data-ttu-id="758f4-190">このサービスは、ユーザー指定のサービス キャッシュ通知コールバック関数をクリアします。</span><span class="sxs-lookup"><span data-stu-id="758f4-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-191">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-191">Input Parameters</span></span>

- <span data-ttu-id="758f4-192">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-193">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-193">Return Values</span></span>

- <span data-ttu-id="758f4-194">**NX_SUCCESS** (0x00): mDNS のサービス キャッシュ通知コールバック関数が正常にクリアされました。</span><span class="sxs-lookup"><span data-stu-id="758f4-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-195">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-195">Allowed From</span></span>

<span data-ttu-id="758f4-196">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-197">例</span><span class="sxs-lookup"><span data-stu-id="758f4-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="758f4-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="758f4-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="758f4-199">ドメイン名を設定します</span><span class="sxs-lookup"><span data-stu-id="758f4-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="758f4-201">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-201">Description</span></span>

<span data-ttu-id="758f4-202">このサービスは、既定のローカル ドメイン名を設定します。</span><span class="sxs-lookup"><span data-stu-id="758f4-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="758f4-203">mDNS インスタンスが作成されると、既定のローカル ドメイン名が ".local" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="758f4-204">この API を使用すると、アプリケーションは既定のローカル ドメイン名を上書きできます。</span><span class="sxs-lookup"><span data-stu-id="758f4-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-205">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-205">Input Parameters</span></span>

- <span data-ttu-id="758f4-206">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-207">**domain_name**: 使用するドメイン名。</span><span class="sxs-lookup"><span data-stu-id="758f4-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-208">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-208">Return Values</span></span>

- <span data-ttu-id="758f4-209">**NX_SUCCESS** (0x00): ローカル ドメインが正常に構成されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-210">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-210">Allowed From</span></span>

<span data-ttu-id="758f4-211">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-212">例</span><span class="sxs-lookup"><span data-stu-id="758f4-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="758f4-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="758f4-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="758f4-214">サービス アナウンス メッセージのタイミング パラメーターを設定します</span><span class="sxs-lookup"><span data-stu-id="758f4-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-215">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="758f4-216">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-216">Description</span></span>

<span data-ttu-id="758f4-217">このサービスは、サービス アナウンスの送信時に mDNS によって使用されるタイミング パラメーターを再構成します。</span><span class="sxs-lookup"><span data-stu-id="758f4-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="758f4-218">公開期間は、ティック数 *t* から始まり、2 の *k* 乗で自在に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="758f4-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="758f4-219">公開通知あたりの繰り返し回数は *p*、繰り返される各公開通知の間隔は *interval* のティック数、アナウンス期間の数値は max_time です。</span><span class="sxs-lookup"><span data-stu-id="758f4-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="758f4-220">既定では、最初の期間は 1 秒に設定されており、k = 1 (期間は毎回 2 倍になります)、*p = 1* (繰り返しなし)、retrans_interval = 0 (間隔なし)、period_interval = 0xFFFFFFFF (最大期間間隔)、および max_time = 3 (公開通知の数) となっています。</span><span class="sxs-lookup"><span data-stu-id="758f4-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-221">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-221">Input Parameters</span></span>

- <span data-ttu-id="758f4-222">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-223">**t**: 最初の期間のティック数。</span><span class="sxs-lookup"><span data-stu-id="758f4-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="758f4-224">既定値は 100 ティック (1 秒) です。</span><span class="sxs-lookup"><span data-stu-id="758f4-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="758f4-225">**p**: 繰り返しの数。</span><span class="sxs-lookup"><span data-stu-id="758f4-225">**p** Number of repetitions.</span></span> <span data-ttu-id="758f4-226">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="758f4-226">Default value is 1.</span></span>
- <span data-ttu-id="758f4-227">**k**: テレスコープ係数。</span><span class="sxs-lookup"><span data-stu-id="758f4-227">**k** Telescopic factor.</span></span> <span data-ttu-id="758f4-228">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="758f4-228">Default value is 1.</span></span>
- <span data-ttu-id="758f4-229">**retrans_interval**: 繰り返しされるアナウンス メッセージを送信する前に待機するティック数。</span><span class="sxs-lookup"><span data-stu-id="758f4-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="758f4-230">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="758f4-230">Default value is 0.</span></span>
- <span data-ttu-id="758f4-231">**period_interval**: 2 つのアナウンス期間の間のティック数。</span><span class="sxs-lookup"><span data-stu-id="758f4-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="758f4-232">既定値は 0xFFFFFFFF です。</span><span class="sxs-lookup"><span data-stu-id="758f4-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="758f4-233">**max_time**: 公開通知に使用するアナウンス期間の数値。</span><span class="sxs-lookup"><span data-stu-id="758f4-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="758f4-234">*max_time* のアナウンス期間が過ぎると、アナウンス メッセージはそれ以上送信されません。</span><span class="sxs-lookup"><span data-stu-id="758f4-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="758f4-235">既定値は 3 です。</span><span class="sxs-lookup"><span data-stu-id="758f4-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-236">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-236">Return Values</span></span>

- <span data-ttu-id="758f4-237">**NX_SUCCESS** (0x00): タイミングの値が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-238">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-238">Allowed From</span></span>

<span data-ttu-id="758f4-239">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-240">例</span><span class="sxs-lookup"><span data-stu-id="758f4-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="758f4-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="758f4-241">nx_mdns_service_add</span></span>

<span data-ttu-id="758f4-242">ローカル サービスを追加します</span><span class="sxs-lookup"><span data-stu-id="758f4-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-243">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="758f4-244">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-244">Description</span></span>

<span data-ttu-id="758f4-245">この API は、アプリケーションが提供するサービスを登録します。</span><span class="sxs-lookup"><span data-stu-id="758f4-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="758f4-246">フラグ *is_unique* が設定されている場合、mDNS は、ネットワーク上でサービスのアナウンスを開始する前に、サービス名をプローブして、それがローカル ネットワーク上で一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="758f4-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="758f4-247">*instance* は、サービス名のインスタンス部分です。</span><span class="sxs-lookup"><span data-stu-id="758f4-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="758f4-248">*service* は、サービス名のサービス部分です。</span><span class="sxs-lookup"><span data-stu-id="758f4-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="758f4-249">たとえば、"_http._tcp" はサービスです。</span><span class="sxs-lookup"><span data-stu-id="758f4-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="758f4-250">サブタイプを使用してサービスを記述するには、呼び出し元で *subtype* パラメーターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="758f4-251">たとえば、目的のサービスが "_printer._sub._http._tcp" の場合、サービス フィールドは "_http._tcp:"、サブタイプ フィールドは "_printer" です。</span><span class="sxs-lookup"><span data-stu-id="758f4-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-252">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-252">Input Parameters</span></span>

- <span data-ttu-id="758f4-253">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-254">**instance**: サービスのインスタンス名を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="758f4-255">**service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="758f4-256">**subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="758f4-257">**priority**: サービスの優先度</span><span class="sxs-lookup"><span data-stu-id="758f4-257">**priority** Service priority</span></span>
- <span data-ttu-id="758f4-258">**weight**: サービスの重み</span><span class="sxs-lookup"><span data-stu-id="758f4-258">**weight** Service weight</span></span>
- <span data-ttu-id="758f4-259">**port**: サービスが使用する TCP または UDP ポート番号</span><span class="sxs-lookup"><span data-stu-id="758f4-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="758f4-260">**text**: 追加のテキスト情報</span><span class="sxs-lookup"><span data-stu-id="758f4-260">**text** Additional text information</span></span>
- <span data-ttu-id="758f4-261">**is_unique**: サービスが共有されているか一意であるかを示すブール型のフラグ。</span><span class="sxs-lookup"><span data-stu-id="758f4-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="758f4-262">一意として登録されるサービスの場合、mDNS は、ネットワーク上のサービスをプローブしてから、その提供を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="758f4-263">**Interface_index**: サービスが提供される際に使用される物理インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="758f4-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="758f4-264">接続型サービスのいずれかを介して提供されるサービスの場合、値 *NX_MDNS_ALL_INTERFACES* が使用されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-265">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-265">Return Values</span></span>

- <span data-ttu-id="758f4-266">**NX_SUCCESS** (0x00): サービスが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-267">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-267">Allowed From</span></span>

<span data-ttu-id="758f4-268">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-269">例</span><span class="sxs-lookup"><span data-stu-id="758f4-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="758f4-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="758f4-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="758f4-271">以前に登録されたサービスを削除します</span><span class="sxs-lookup"><span data-stu-id="758f4-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-272">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="758f4-273">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-273">Description</span></span>

<span data-ttu-id="758f4-274">この API は、以前に登録されたサービスを削除します。</span><span class="sxs-lookup"><span data-stu-id="758f4-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="758f4-275">サービスが削除されると、"goodbye" メッセージがローカル ネットワークに送信されるため、隣接ノードに通知されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-276">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-276">Input Parameters</span></span>

- <span data-ttu-id="758f4-277">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-278">**instance**: サービスのインスタンス名を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="758f4-279">**service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="758f4-280">**subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-281">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-281">Return Values</span></span>

- <span data-ttu-id="758f4-282">**NX_SUCCESS** (0x00): サービスが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-283">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-283">Allowed From</span></span>

<span data-ttu-id="758f4-284">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-285">例</span><span class="sxs-lookup"><span data-stu-id="758f4-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="758f4-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="758f4-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="758f4-287">ワンショット サービス検出を開始します</span><span class="sxs-lookup"><span data-stu-id="758f4-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-288">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="758f4-289">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-289">Description</span></span>

<span data-ttu-id="758f4-290">このサービスは、ワンショット mDNS クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="758f4-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="758f4-291">指定したサービスがピア サービス キャッシュ内に見つかった場合は、最初のインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="758f4-292">ローカル ピア サービス キャッシュ内にサービスが見つからない場合、mDNS モジュールは、クエリ コマンドを発行し、応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="758f4-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="758f4-293">このサービスは、最初の回答を受信するか、クエリがタイムアウトするまで、ブロックされます。</span><span class="sxs-lookup"><span data-stu-id="758f4-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-294">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-294">Input Parameters</span></span>

- <span data-ttu-id="758f4-295">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-296">**instance**: サービスのインスタンス名を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="758f4-297">**service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="758f4-298">アプリケーションでは、サービスの種類を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-298">the application must specify the service type.</span></span>
- <span data-ttu-id="758f4-299">**subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="758f4-300">**service_ptr**: クエリ結果を格納する NX_MDNS_SERVICE 構造体を指すユーザー指定のポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="758f4-301">**wait_option**: 応答を待機する時間 (ティック数)。</span><span class="sxs-lookup"><span data-stu-id="758f4-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-302">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-302">Return Values</span></span>

- <span data-ttu-id="758f4-303">**NX_SUCCESS** (0x00): サービス情報が正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-304">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-304">Allowed From</span></span>

<span data-ttu-id="758f4-305">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-306">例</span><span class="sxs-lookup"><span data-stu-id="758f4-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="758f4-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="758f4-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="758f4-308">連続サービス検出を開始します</span><span class="sxs-lookup"><span data-stu-id="758f4-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-309">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="758f4-310">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-310">Description</span></span>

<span data-ttu-id="758f4-311">このサービスは、連続クエリを開始します。</span><span class="sxs-lookup"><span data-stu-id="758f4-311">This service starts a continuous query.</span></span> <span data-ttu-id="758f4-312">サービスから即座に制御が返されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="758f4-312">Note that the service returns immediately.</span></span> <span data-ttu-id="758f4-313">連続クエリを発行した後、アプリケーションは、API *nx_mdns_service_lookup* を使用してサービス レコードを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="758f4-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="758f4-314">連続クエリを停止するために、アプリケーションは、API *nx_mdns_service_query_stop* を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="758f4-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-315">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-315">Input Parameters</span></span>

- <span data-ttu-id="758f4-316">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-317">**instance**: サービスのインスタンス名を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="758f4-318">**service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="758f4-319">**subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-320">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-320">Return Values</span></span>

- <span data-ttu-id="758f4-321">**NX_SUCCESS** (0x00): 連続クエリが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-322">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-322">Allowed From</span></span>

<span data-ttu-id="758f4-323">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-324">例</span><span class="sxs-lookup"><span data-stu-id="758f4-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="758f4-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="758f4-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="758f4-326">以前に発行された連続サービス検出を停止します</span><span class="sxs-lookup"><span data-stu-id="758f4-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-327">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="758f4-328">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-328">Description</span></span>

<span data-ttu-id="758f4-329">この API は、以前に発行された連続サービス検出を終了します。</span><span class="sxs-lookup"><span data-stu-id="758f4-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-330">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-330">Input Parameters</span></span>

- <span data-ttu-id="758f4-331">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-332">**instance**: サービスのインスタンス名を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="758f4-333">**service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="758f4-334">**subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-335">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-335">Return Values</span></span>

- <span data-ttu-id="758f4-336">**NX_SUCCESS** (0x00): 連続クエリが正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-337">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-337">Allowed From</span></span>

<span data-ttu-id="758f4-338">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-339">例</span><span class="sxs-lookup"><span data-stu-id="758f4-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="758f4-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="758f4-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="758f4-341">ローカル ピア サービス キャッシュからサービスを取得します</span><span class="sxs-lookup"><span data-stu-id="758f4-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-342">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="758f4-343">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-343">Description</span></span>

<span data-ttu-id="758f4-344">このサービスは、インスタンス名 (指定されている場合) とサービスの種類が一致するサービスをローカル ピア サービス キャッシュ内で検索します。</span><span class="sxs-lookup"><span data-stu-id="758f4-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="758f4-345">アプリケーションは、記述に一致するキャッシュ内の最初のサービスの *instance_index* を 0 に設定して、サービスの検索を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="758f4-346">アプリケーションは、キャッシュの末尾を示す *NX_NO_MORE_ENTRIES* がサービスから返されるまで、キャッシュ内で追加のサービスが見つかるたびに *instance_index* 値を引き上げながらこのサービスを使用し続ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-347">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-347">Input Parameters</span></span>

- <span data-ttu-id="758f4-348">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-349">**instance**: サービスのインスタンス名を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="758f4-350">**service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="758f4-351">**subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="758f4-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="758f4-352">**Instance_index**: 返されるインスタンスのインデックス番号。</span><span class="sxs-lookup"><span data-stu-id="758f4-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="758f4-353">**service_ptr**: 検索結果を格納する NX_MDNS_SERVICE 構造体を指すユーザー指定のポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-354">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-354">Return Values</span></span>

- <span data-ttu-id="758f4-355">**NX_SUCCESS** (0x00): サービスが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="758f4-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="758f4-356">**NX_NO_MORE_ENTRIES** (0x17): 指定されたインデックス番号にサービス エントリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="758f4-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="758f4-357">このエラー コードは、検索の終了を示します。</span><span class="sxs-lookup"><span data-stu-id="758f4-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-358">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-358">Allowed From</span></span>

<span data-ttu-id="758f4-359">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-360">例</span><span class="sxs-lookup"><span data-stu-id="758f4-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="758f4-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="758f4-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="758f4-362">サービス無視セットを構成します</span><span class="sxs-lookup"><span data-stu-id="758f4-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-363">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="758f4-364">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-364">Description</span></span>

<span data-ttu-id="758f4-365">この API は、*service_mask* ビットマスクで指定されたサービスを無視するようマスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="758f4-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="758f4-366">ユーザーは、必要に応じて service_mask を使用して、キャッシュしないサービスの種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="758f4-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="758f4-367">サービスの一覧は、*nxd_mdns.c* 内のテーブル *nx_mdns_service_types* で定義されています。</span><span class="sxs-lookup"><span data-stu-id="758f4-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="758f4-368">nx_mdns_service_types[] 内の最初のサービスの種類に対応するマスクは 0x00000001、2 番目のサービスの種類のマスクは 0x00000002 のようになります。</span><span class="sxs-lookup"><span data-stu-id="758f4-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-369">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-369">Input Parameters</span></span>

- <span data-ttu-id="758f4-370">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-371">**service_mask**: 無視するユーザー定義のサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="758f4-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="758f4-372">マスクは、32 ビットの ULONG 型です。</span><span class="sxs-lookup"><span data-stu-id="758f4-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="758f4-373">各ビットは、ユーザー定義の *nx_mdns_service_types* 配列内のエントリを表します。</span><span class="sxs-lookup"><span data-stu-id="758f4-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="758f4-374">ビットが設定されている場合、*nx_mdns_service_type* 配列で指定された対応するサービスの種類はピア サービス キャッシュに格納されません。</span><span class="sxs-lookup"><span data-stu-id="758f4-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-375">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-375">Return Values</span></span>

- <span data-ttu-id="758f4-376">**NX_SUCCESS** (0x00): サービス無視マスクが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-377">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-377">Allowed From</span></span>

<span data-ttu-id="758f4-378">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-379">例</span><span class="sxs-lookup"><span data-stu-id="758f4-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="758f4-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="758f4-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="758f4-381">サービス変更通知コールバック関数を構成します</span><span class="sxs-lookup"><span data-stu-id="758f4-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-382">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="758f4-383">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-383">Description</span></span>

<span data-ttu-id="758f4-384">この API は、サービス変更通知コールバック関数を構成します。</span><span class="sxs-lookup"><span data-stu-id="758f4-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="758f4-385">このコールバック関数は、ネットワーク上の他のノードによって提供されるサービスが追加または変更されたとき、あるいは使用できなくなったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="758f4-386">ユーザーは、必要に応じて service_mask を使用して、監視するサービスの種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="758f4-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="758f4-387">監視対象のサービスのリストは、*nxd_mdns.c* 内のテーブル *nx_mdns_service_types* にハードコーディングされています。</span><span class="sxs-lookup"><span data-stu-id="758f4-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="758f4-388">nx_mdns_service_types[] 内の最初のサービスの種類に対応するマスクは 0x00000001、2 番目のサービスの種類のマスクは 0x00000002 のようになります。</span><span class="sxs-lookup"><span data-stu-id="758f4-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-389">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-389">Input Parameters</span></span>

- <span data-ttu-id="758f4-390">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-391">**service_mask**: 監視するユーザー定義のサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="758f4-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="758f4-392">マスクは、32 ビットの ULONG 型です。</span><span class="sxs-lookup"><span data-stu-id="758f4-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="758f4-393">各ビットは、*nx_mdns_service_types* 配列内のエントリを表します。</span><span class="sxs-lookup"><span data-stu-id="758f4-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="758f4-394">**service_change_notify**: 指定されたサービスが変更されたときに呼び出されるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="758f4-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="758f4-395">詳細なサービス情報は、*service_ptr* が指すメモリに返されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="758f4-396">コールバック通知関数から制御が返された後はメモリ内のコンテンツが無効であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="758f4-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-397">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-397">Return Values</span></span>

- <span data-ttu-id="758f4-398">**NX_SUCCESS** (0x00): コールバック関数が正常にインストールされました。</span><span class="sxs-lookup"><span data-stu-id="758f4-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-399">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-399">Allowed From</span></span>

<span data-ttu-id="758f4-400">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-401">例</span><span class="sxs-lookup"><span data-stu-id="758f4-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="758f4-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="758f4-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="758f4-403">サービス変更通知コールバック関数をクリアします</span><span class="sxs-lookup"><span data-stu-id="758f4-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-404">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="758f4-405">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-405">Description</span></span>

<span data-ttu-id="758f4-406">この API は、サービス変更通知コールバック関数をクリアします。</span><span class="sxs-lookup"><span data-stu-id="758f4-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-407">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-407">Input Parameters</span></span>

- <span data-ttu-id="758f4-408">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-409">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-409">Return Values</span></span>

- <span data-ttu-id="758f4-410">**NX_SUCCESS** (0x00): コールバック関数が正常にクリアされました。</span><span class="sxs-lookup"><span data-stu-id="758f4-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-411">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-411">Allowed From</span></span>

<span data-ttu-id="758f4-412">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-413">例</span><span class="sxs-lookup"><span data-stu-id="758f4-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="758f4-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="758f4-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="758f4-415">ホスト アドレスを取得します</span><span class="sxs-lookup"><span data-stu-id="758f4-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-416">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="758f4-417">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-417">Description</span></span>

<span data-ttu-id="758f4-418">このサービスは、ホスト IPv4 および IPv6 アドレスに対する mDNS クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="758f4-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="758f4-419">指定されたホスト名のアドレスがピア サービス キャッシュ内に見つかった場合は、そのアドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="758f4-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="758f4-420">アドレスがピア サービス キャッシュ内に見つからない場合、mDNS モジュールは、A および AAAA 型のクエリを発行し、応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="758f4-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="758f4-421">この API は、回答が受信されるかクエリがタイムアウトするまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="758f4-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-422">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-422">Input Parameters</span></span>

- <span data-ttu-id="758f4-423">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="758f4-424">**host_name**: ホスト名を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="758f4-425">**ipv4_address**: IPv4 アドレスの記憶領域用に 4 バイトでアラインされたアドレスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="758f4-426">ユーザーは、IPv4 アドレス用に 4 バイトの領域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="758f4-427">アプリケーションが IPv4 アドレスを取得する必要がない場合は、NX_NULL アドレスをこの API に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="758f4-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="758f4-428">**ipv6_address**: IPv6 アドレスの記憶領域用に 4 バイトでアラインされたアドレスを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="758f4-429">ユーザーは、IPv6 アドレス用に 16 バイトの領域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="758f4-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="758f4-430">アプリケーションが IPv6 アドレスを取得する必要がない場合は、NX_NULL アドレスをこの API に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="758f4-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="758f4-431">**wait_option**: 応答を待機する時間 (ティック数)。</span><span class="sxs-lookup"><span data-stu-id="758f4-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-432">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-432">Return Values</span></span>

- <span data-ttu-id="758f4-433">**NX_SUCCESS** (0x00): ホスト アドレスが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-434">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-434">Allowed From</span></span>

<span data-ttu-id="758f4-435">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-436">例</span><span class="sxs-lookup"><span data-stu-id="758f4-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="758f4-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="758f4-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="758f4-438">すべてのローカル サービスを消去します</span><span class="sxs-lookup"><span data-stu-id="758f4-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-439">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="758f4-440">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-440">Description</span></span>

<span data-ttu-id="758f4-441">このサービスは、Goodbye メッセージを送信した後、ローカル サービス キャッシュ内のすべてのエントリをクリアします。</span><span class="sxs-lookup"><span data-stu-id="758f4-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-442">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-442">Input Parameters</span></span>

- <span data-ttu-id="758f4-443">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-444">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-444">Return Values</span></span>

- <span data-ttu-id="758f4-445">**NX_SUCCESS** (0x00): キャッシュ内のすべてのエントリが正常に消去されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-446">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-446">Allowed From</span></span>

<span data-ttu-id="758f4-447">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-448">例</span><span class="sxs-lookup"><span data-stu-id="758f4-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="758f4-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="758f4-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="758f4-450">検出されたすべてのサービスを消去します</span><span class="sxs-lookup"><span data-stu-id="758f4-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="758f4-451">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="758f4-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="758f4-452">説明</span><span class="sxs-lookup"><span data-stu-id="758f4-452">Description</span></span>

<span data-ttu-id="758f4-453">このサービスは、ピア サービス キャッシュ内のすべてのエントリをクリアします。</span><span class="sxs-lookup"><span data-stu-id="758f4-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="758f4-454">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="758f4-454">Input Parameters</span></span>

- <span data-ttu-id="758f4-455">**mdns_ptr**: mDNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="758f4-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="758f4-456">戻り値</span><span class="sxs-lookup"><span data-stu-id="758f4-456">Return Values</span></span>

- <span data-ttu-id="758f4-457">**NX_SUCCESS** (0x00): キャッシュ内のすべてのエントリが正常に消去されました。</span><span class="sxs-lookup"><span data-stu-id="758f4-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="758f4-458">許可元</span><span class="sxs-lookup"><span data-stu-id="758f4-458">Allowed From</span></span>

<span data-ttu-id="758f4-459">Threads</span><span class="sxs-lookup"><span data-stu-id="758f4-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="758f4-460">例</span><span class="sxs-lookup"><span data-stu-id="758f4-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
