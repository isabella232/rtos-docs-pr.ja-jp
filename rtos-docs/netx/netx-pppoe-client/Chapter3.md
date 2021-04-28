---
title: 第 3 章 - Azure RTOS NetX PPPoE クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX PPPoE クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810406"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="5913e-103">第 3 章 - Azure RTOS NetX PPPoE クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="5913e-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="5913e-104">この章では、すべての Azure RTOS NetX PPPoE クライアント サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="5913e-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="5913e-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="5913e-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="5913e-106">**nx_pppoe_client_create**: "*PPPoE クライアント インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="5913e-107">**nx_pppoe_client_delete**: "*PPPoE クライアント インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="5913e-108">**nx_pppoe_client_host_uniq_set**: "*PPPoE クライアントの Host-Uniq を設定する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="5913e-109">**nx_pppoe_client_host_uniq_set_extended**: "*PPPoE クライアントの Host-Uniq を設定する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="5913e-110">**nx_pppoe_client_service_name_set**: "*PPPoE クライアントのサービス名を設定する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="5913e-111">**nx_pppoe_client_service_name_set_extended**: "*PPPoE クライアントのサービス名を設定する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="5913e-112">**nx_pppoe_client_session_connect**: "*PPPoE クライアント セッションを PPPoE サーバーに接続する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="5913e-113">**nx_pppoe_client_session_packet_send**: "*PPPoE セッション パケットを送信する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="5913e-114">**nx_pppoe_client_session_terminate**: "*PPPoE セッションを終了する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="5913e-115">**nx_pppoe_client_session_get**: "*指定された PPPoE セッション情報を取得する*"</span><span class="sxs-lookup"><span data-stu-id="5913e-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="5913e-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="5913e-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="5913e-117">PPPoE クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="5913e-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-118">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="5913e-119">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-119">Description</span></span>

<span data-ttu-id="5913e-120">このサービスは、指定された NetX IP インスタンスのユーザー指定のリンク ドライバーを使用して、PPPoE クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5913e-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="5913e-121">リンク ドライバーが初期化されておらず、有効になっていない場合は、PPPoE クライアント ソフトウェアがリンク ドライバーを初期化する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="5913e-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="5913e-122">また、アプリケーションでは、PPPoE クライアント インスタンスが内部パケット割り当てに使用するために、以前に作成されたパケット プールを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-123">一般に、PPPoE クライアント スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5913e-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="5913e-124">IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5913e-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-125">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-125">Input Parameters</span></span>

 - <span data-ttu-id="5913e-126">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-127">**name**: この PPPoE クライアント インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="5913e-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="5913e-128">**ip_ptr**: IP インスタンスの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="5913e-129">**interface_index**: インターフェイス インデックス。</span><span class="sxs-lookup"><span data-stu-id="5913e-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="5913e-130">**pool_ptr**: パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="5913e-131">**stack_ptr**: PPPoE クライアント スレッドのスタック領域の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="5913e-132">**stack_size**: スレッドのスタックのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5913e-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="5913e-133">**priority**: 内部 PPPoE クライアント スレッドの優先順位 (1 - 31)。</span><span class="sxs-lookup"><span data-stu-id="5913e-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="5913e-134">**pppoe_link_driver**: ユーザー指定のリンク ドライバー。</span><span class="sxs-lookup"><span data-stu-id="5913e-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="5913e-135">**pppoe_packet_receive**: ユーザー指定のパケット受信関数。</span><span class="sxs-lookup"><span data-stu-id="5913e-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-136">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-136">Return Values</span></span>

 - <span data-ttu-id="5913e-137">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="5913e-138">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント、IP、パケット プール、またはスタック ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="5913e-139">NX_PPPOE_CLIENT_INVALID_INTERFACE: (0xD2) インターフェイスが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="5913e-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR: (0xD3) パケット プールのペイロード サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="5913e-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR: (0xD4) メモリ サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="5913e-142">NX_PPPOE_CLIENT_PRIORITY_ERROR: (0xD5) PPPoE クライアント スレッドの優先順位が無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-143">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-143">Allowed From</span></span>

<span data-ttu-id="5913e-144">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-145">例</span><span class="sxs-lookup"><span data-stu-id="5913e-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="5913e-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="5913e-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="5913e-147">PPPoE クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="5913e-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-148">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="5913e-149">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-149">Description</span></span>

<span data-ttu-id="5913e-150">このサービスは、以前に作成された PPPoE クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="5913e-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-151">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-151">Input Parameters</span></span>

 - <span data-ttu-id="5913e-152">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-153">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-153">Return Values</span></span>

 - <span data-ttu-id="5913e-154">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="5913e-155">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-156">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-156">Allowed From</span></span>

<span data-ttu-id="5913e-157">Threads</span><span class="sxs-lookup"><span data-stu-id="5913e-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-158">例</span><span class="sxs-lookup"><span data-stu-id="5913e-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="5913e-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="5913e-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="5913e-160">PPPoE クライアントの Host-Uniq を設定する</span><span class="sxs-lookup"><span data-stu-id="5913e-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-161">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="5913e-162">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-162">Description</span></span>

<span data-ttu-id="5913e-163">このサービスは、PPPoE クライアントの Host-Uniq を設定します。</span><span class="sxs-lookup"><span data-stu-id="5913e-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="5913e-164">Host-Uniq は、アクセス コンセントレーターを特定のホスト要求に一意に関連付けるためにホストによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="5913e-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="5913e-165">これは、ホストが選択した任意の値と長さのバイナリ データになります。</span><span class="sxs-lookup"><span data-stu-id="5913e-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-166">Host-Uniq は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-167">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5913e-167">This service is deprecated.</span></span> <span data-ttu-id="5913e-168">開発者は、*nx_pppoe_client_host_uniq_set_extended()* に移行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5913e-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-169">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-169">Input Parameters</span></span>

 - <span data-ttu-id="5913e-170">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-171">**host_uniq**: Host-Uniq へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="5913e-172">Host-Uniq は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-173">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-173">Return Values</span></span>

 - <span data-ttu-id="5913e-174">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントの Host-Uniq が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="5913e-175">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-176">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-176">Allowed From</span></span>

<span data-ttu-id="5913e-177">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-178">例</span><span class="sxs-lookup"><span data-stu-id="5913e-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="5913e-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="5913e-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="5913e-180">PPPoE クライアントの Host-Uniq を設定する</span><span class="sxs-lookup"><span data-stu-id="5913e-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-181">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="5913e-182">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-182">Description</span></span>

<span data-ttu-id="5913e-183">このサービスは、PPPoE クライアントの Host-Uniq を設定します。</span><span class="sxs-lookup"><span data-stu-id="5913e-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="5913e-184">Host-Uniq は、アクセス コンセントレーターを特定のホスト要求に一意に関連付けるためにホストによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="5913e-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="5913e-185">これは、ホストが選択した任意の値と長さのバイナリ データになります。</span><span class="sxs-lookup"><span data-stu-id="5913e-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-186">Host-Uniq は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-187">このサービスは、*nx_pppoe_client_host_uniq_set()* に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="5913e-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="5913e-188">このバージョンでは、長さの情報もサービスに提供されます。</span><span class="sxs-lookup"><span data-stu-id="5913e-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-189">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-189">Input Parameters</span></span>

 - <span data-ttu-id="5913e-190">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-191">**host_uniq**: Host-Uniq へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="5913e-192">Host-Uniq は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="5913e-193">**host_uniq_length**: host_uniq の長さ。</span><span class="sxs-lookup"><span data-stu-id="5913e-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-194">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-194">Return Values</span></span>

 - <span data-ttu-id="5913e-195">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントの Host-Uniq が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="5913e-196">**NX_PPPOE_CLIENT_PTR_ERROR**: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="5913e-197">**NX_SIZE_ERROR**: (0x09) host_uniq_length のチェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="5913e-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-198">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-198">Allowed From</span></span>

<span data-ttu-id="5913e-199">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-200">例</span><span class="sxs-lookup"><span data-stu-id="5913e-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="5913e-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="5913e-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="5913e-202">PPPoE クライアント サービス名を設定する</span><span class="sxs-lookup"><span data-stu-id="5913e-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-203">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="5913e-204">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-204">Description</span></span>

<span data-ttu-id="5913e-205">このサービスは、PPPoE クライアント サービス名を設定します。</span><span class="sxs-lookup"><span data-stu-id="5913e-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="5913e-206">Service-Name は、ホストが要求しているサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="5913e-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="5913e-207">Service-Name が設定されていない場合は、ホストが任意の数のサービスを受け入れることを示します。</span><span class="sxs-lookup"><span data-stu-id="5913e-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-208">サービス名は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-209">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5913e-209">This service is deprecated.</span></span> <span data-ttu-id="5913e-210">開発者は、*nx_pppoe_client_service_name_set_extended()* に移行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5913e-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-211">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-211">Input Parameters</span></span>

 - <span data-ttu-id="5913e-212">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-213">**service_name**: サービス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="5913e-214">サービス名は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-215">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-215">Return Values</span></span>

 - <span data-ttu-id="5913e-216">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント サービス名が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="5913e-217">**NX_PPPOE_CLIENT_PTR_ERROR**: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-218">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-218">Allowed From</span></span>

<span data-ttu-id="5913e-219">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-220">例</span><span class="sxs-lookup"><span data-stu-id="5913e-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="5913e-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="5913e-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="5913e-222">PPPoE クライアント サービス名を設定する</span><span class="sxs-lookup"><span data-stu-id="5913e-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-223">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="5913e-224">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-224">Description</span></span>

<span data-ttu-id="5913e-225">このサービスは、PPPoE クライアント サービス名を設定します。</span><span class="sxs-lookup"><span data-stu-id="5913e-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="5913e-226">Service-Name は、ホストが要求しているサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="5913e-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="5913e-227">Service-Name が設定されていない場合は、ホストが任意の数のサービスを受け入れることを示します。</span><span class="sxs-lookup"><span data-stu-id="5913e-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-228">サービス名は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-229">このサービスは、*nx_pppoe_client_service_name_set()* に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="5913e-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="5913e-230">このバージョンでは、サービス名の長さの情報も関数に提供されます。</span><span class="sxs-lookup"><span data-stu-id="5913e-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-231">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-231">Input Parameters</span></span>

 - <span data-ttu-id="5913e-232">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-233">**service_name**: サービス名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="5913e-234">サービス名は Null 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="5913e-235">**service_name_length**: service_name の長さ。</span><span class="sxs-lookup"><span data-stu-id="5913e-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-236">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-236">Return Values</span></span>

 - <span data-ttu-id="5913e-237">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント サービス名が正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="5913e-238">**NX_PPPOE_CLIENT_PTR_ERROR**: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="5913e-239">**NX_SIZE_ERROR**: (0x09) service_name_length のチェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="5913e-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-240">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-240">Allowed From</span></span>

<span data-ttu-id="5913e-241">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-242">例</span><span class="sxs-lookup"><span data-stu-id="5913e-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="5913e-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="5913e-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="5913e-244">PPPoE クライアント セッションを接続する</span><span class="sxs-lookup"><span data-stu-id="5913e-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-245">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5913e-246">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-246">Description</span></span>

<span data-ttu-id="5913e-247">このサービスは、以前に作成された PPPoE クライアントを使用して、指定された PPPoE サーバーへの PPPoE セッション接続を行います。</span><span class="sxs-lookup"><span data-stu-id="5913e-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="5913e-248">この関数は、*nx_pppoe_client_create*、*nx_pppoe_client_host_uniq_set*、*nx_pppoe_client_service_name_set* の後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5913e-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-249">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-249">Input Parameters</span></span>

 - <span data-ttu-id="5913e-250">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-251">**wait_option**: 接続が確立されている間の待機オプション。</span><span class="sxs-lookup"><span data-stu-id="5913e-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-252">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-252">Return Values</span></span>

 - <span data-ttu-id="5913e-253">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント セッションが正常に接続されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="5913e-254">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-255">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-255">Allowed From</span></span>

<span data-ttu-id="5913e-256">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-257">例</span><span class="sxs-lookup"><span data-stu-id="5913e-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="5913e-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="5913e-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="5913e-259">指定されたセッションに PPPoE クライアント パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="5913e-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-260">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="5913e-261">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-261">Description</span></span>

<span data-ttu-id="5913e-262">このサービスでは、指定されたセッション ID を使用して PPPoE パケットを送信します。</span><span class="sxs-lookup"><span data-stu-id="5913e-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-263">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-263">Input Parameters</span></span>

 - <span data-ttu-id="5913e-264">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-265">**packet_ptr**: PPPoE パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-266">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-266">Return Values</span></span>

 - <span data-ttu-id="5913e-267">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント パケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="5913e-268">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="5913e-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR: (0xD3) PPPoE クライアント パケットが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="5913e-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED: (0xD8) PPPoE セッションが確立されていません。</span><span class="sxs-lookup"><span data-stu-id="5913e-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-271">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-271">Allowed From</span></span>

<span data-ttu-id="5913e-272">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-273">例</span><span class="sxs-lookup"><span data-stu-id="5913e-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="5913e-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="5913e-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="5913e-275">PPPoE クライアント セッションを終了する</span><span class="sxs-lookup"><span data-stu-id="5913e-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-276">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="5913e-277">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-277">Description</span></span>

<span data-ttu-id="5913e-278">このサービスは、指定された PPPoE セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="5913e-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-279">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-279">Input Parameters</span></span>

 - <span data-ttu-id="5913e-280">**pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-281">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-281">Return Values</span></span>

 - <span data-ttu-id="5913e-282">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント セッションが正常に終了しました。</span><span class="sxs-lookup"><span data-stu-id="5913e-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="5913e-283">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-284">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-284">Allowed From</span></span>

<span data-ttu-id="5913e-285">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-286">例</span><span class="sxs-lookup"><span data-stu-id="5913e-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="5913e-287">nx_pppoe_client_session_get</span><span class="sxs-lookup"><span data-stu-id="5913e-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="5913e-288">指定された PPPoE セッション情報を取得する</span><span class="sxs-lookup"><span data-stu-id="5913e-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="5913e-289">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5913e-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="5913e-290">説明</span><span class="sxs-lookup"><span data-stu-id="5913e-290">Description</span></span>

<span data-ttu-id="5913e-291">このサービスは、指定された PPPoE セッション情報、サーバーの物理アドレス、セッション ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="5913e-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5913e-292">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="5913e-292">Input Parameters</span></span>

 - <span data-ttu-id="5913e-293">**pppoe_server_ptr**: PPPoE クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="5913e-294">**server_mac_msw**: サーバーの物理アドレス MSW ポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="5913e-295">**server_mac_lsw**: サーバーの物理アドレス LSW ポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="5913e-296">**session_id**: セッション ID ポインター。</span><span class="sxs-lookup"><span data-stu-id="5913e-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5913e-297">戻り値</span><span class="sxs-lookup"><span data-stu-id="5913e-297">Return Values</span></span>

 - <span data-ttu-id="5913e-298">**NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント セッションが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="5913e-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="5913e-299">NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="5913e-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="5913e-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED: (0xD8) PPPoE セッションが確立されていません。</span><span class="sxs-lookup"><span data-stu-id="5913e-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5913e-301">許可元</span><span class="sxs-lookup"><span data-stu-id="5913e-301">Allowed From</span></span>

<span data-ttu-id="5913e-302">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="5913e-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5913e-303">例</span><span class="sxs-lookup"><span data-stu-id="5913e-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
