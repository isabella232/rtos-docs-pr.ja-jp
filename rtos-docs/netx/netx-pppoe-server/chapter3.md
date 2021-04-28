---
title: 第 3 章 - Azure RTOS NetX PPPoE サーバー サービスの説明
description: この章では、すべての Azure RTOS NetX PPPoE サーバー サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811417"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="dad34-103">第 3 章 - Azure RTOS NetX PPPoE サーバー サービスの説明</span><span class="sxs-lookup"><span data-stu-id="dad34-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="dad34-104">この章では、すべての Azure RTOS NetX PPPoE サーバー サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="dad34-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="dad34-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="dad34-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="dad34-106">**nx_pppoe_server_create**: "*PPPoE サーバー インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="dad34-107">**nx_pppoe_server_ac_name_set**: "*アクセス コンセントレーター名を設定する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="dad34-108">**nx_pppoe_server_delete**: "*PPPoE サーバー インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="dad34-109">**nx_pppoe_server_enable**: "*PPPoE サーバー サービスを有効にする*"</span><span class="sxs-lookup"><span data-stu-id="dad34-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="dad34-110">**nx_pppoe_server_disable**: "*PPPoE サーバー サービスを無効にする*"</span><span class="sxs-lookup"><span data-stu-id="dad34-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="dad34-111">**nx_pppoe_server_callback_notify_set**: "*PPPoE サーバーのコールバック通知関数を設定する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="dad34-112">**nx_pppoe_server_service_name_set**: "*PPPoE サーバー サービス名を設定する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="dad34-113">**nx_pppoe_server_session_send**: "*指定されたセッションに PPPoE サーバー データを送信する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="dad34-114">**nx_pppoe_server_session_packet_send**: "*指定されたセッションに PPPoE サーバー パケットを送信する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="dad34-115">**nx_pppoe_server_session_terminate**: "*指定された PPPoE セッションを終了する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="dad34-116">**nx_pppoe_server_session_get**: "*指定されたセッション情報を取得する*"</span><span class="sxs-lookup"><span data-stu-id="dad34-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="dad34-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="dad34-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="dad34-118">PPPoE サーバー インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="dad34-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-119">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="dad34-120">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-120">Description</span></span>

<span data-ttu-id="dad34-121">このサービスでは、指定された NetX IP インスタンスのユーザー指定のリンク ドライバーを使用して、PPPoE サーバー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dad34-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="dad34-122">リンク ドライバーが初期化されておらず、有効になっていない場合は、PPPoE サーバー ソフトウェアがリンク ドライバーを初期化する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="dad34-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="dad34-123">また、PPPoE サーバー インスタンスで内部パケット割り当てに使用できるように、以前に作成されたパケット プールがアプリケーションによって提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="dad34-124">一般に、PPPoE サーバー スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dad34-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="dad34-125">IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dad34-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-126">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-126">Input Parameters</span></span>

- <span data-ttu-id="dad34-127">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-128">**name**: この PPPoE サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="dad34-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="dad34-129">**ip_ptr**: IP インスタンスの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="dad34-130">**interface_index**: インターフェイス インデックス。</span><span class="sxs-lookup"><span data-stu-id="dad34-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="dad34-131">**pppoe_link_driver**: ユーザー指定のリンク ドライバー。</span><span class="sxs-lookup"><span data-stu-id="dad34-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="dad34-132">**pool_ptr**: パケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="dad34-133">**stack_ptr**: PPPoE サーバー スレッドのスタック領域の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="dad34-134">**stack_size**: スレッドのスタックのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="dad34-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="dad34-135">**priority**: 内部 PPPoE サーバー スレッドの優先順位 (1 から 31)。</span><span class="sxs-lookup"><span data-stu-id="dad34-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-136">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-136">Return Values</span></span>

- <span data-ttu-id="dad34-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="dad34-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー、IP、パケット プール、またはスタック ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="dad34-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) インターフェイスが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="dad34-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) パケット プールのペイロード サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="dad34-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) メモリ サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="dad34-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) PPPoE サーバー スレッドの優先順位が無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-143">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-143">Allowed From</span></span>

<span data-ttu-id="dad34-144">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-145">例</span><span class="sxs-lookup"><span data-stu-id="dad34-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="dad34-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="dad34-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="dad34-147">PPPoE サーバー インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="dad34-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-148">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="dad34-149">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-149">Description</span></span>

<span data-ttu-id="dad34-150">このサービスは、以前に作成された PPPoE サーバー インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="dad34-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-151">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-151">Input Parameters</span></span>

- <span data-ttu-id="dad34-152">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-153">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-153">Return Values</span></span>

- <span data-ttu-id="dad34-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-156">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-156">Allowed From</span></span>

<span data-ttu-id="dad34-157">Threads</span><span class="sxs-lookup"><span data-stu-id="dad34-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-158">例</span><span class="sxs-lookup"><span data-stu-id="dad34-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="dad34-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="dad34-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="dad34-160">PPPoE サーバー サービスを有効にする</span><span class="sxs-lookup"><span data-stu-id="dad34-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-161">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="dad34-162">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-162">Description</span></span>

<span data-ttu-id="dad34-163">このサービスは、PPPoE サーバー サービスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="dad34-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="dad34-164">この関数は、*nx_pppoe_server_create* および *nx_pppoe_server_callback_notify_set* の後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-165">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-165">Input Parameters</span></span>

- <span data-ttu-id="dad34-166">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-167">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-167">Return Values</span></span>

- <span data-ttu-id="dad34-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-170">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-170">Allowed From</span></span>

<span data-ttu-id="dad34-171">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-172">例</span><span class="sxs-lookup"><span data-stu-id="dad34-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="dad34-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="dad34-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="dad34-174">PPPoE サーバー サービスを無効にする</span><span class="sxs-lookup"><span data-stu-id="dad34-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-175">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="dad34-176">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-176">Description</span></span>

<span data-ttu-id="dad34-177">このサービスは、PPPoE サーバー サービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="dad34-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-178">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-178">Input Parameters</span></span>

- <span data-ttu-id="dad34-179">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-180">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-180">Return Values</span></span>

- <span data-ttu-id="dad34-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-183">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-183">Allowed From</span></span>

<span data-ttu-id="dad34-184">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-185">例</span><span class="sxs-lookup"><span data-stu-id="dad34-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="dad34-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="dad34-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="dad34-187">PPPoE サーバーのコールバック通知関数を設定する</span><span class="sxs-lookup"><span data-stu-id="dad34-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="dad34-188">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="dad34-189">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-189">Description</span></span>

<span data-ttu-id="dad34-190">このサービスは、PPPoE サーバーのコールバック通知関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="dad34-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="dad34-191">この関数は *nx_pppoe_server_enable* の前に呼び出す必要があり、pppoe_data_receive_notify 関数ポインターを設定する必要があります。そうしないと、*nx_pppoe_server_enable* は失敗します。</span><span class="sxs-lookup"><span data-stu-id="dad34-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-192">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-192">Input Parameters</span></span>

- <span data-ttu-id="dad34-193">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-194">**pppoe_discover_initiation_notify**: PPPoE 検出開始メッセージを受信するたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="dad34-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="dad34-195">この値が NULL の場合、検出開始コールバック関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="dad34-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="dad34-196">**pppoe_discover_request_notify**: PPPoE 検出要求メッセージを受信するたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="dad34-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="dad34-197">この値が NULL の場合、検出要求コールバック関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="dad34-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="dad34-198">**pppoe_discover_terminate_notify**: PPPoE 検出終了メッセージを受信するたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="dad34-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="dad34-199">この値が NULL の場合、検出終了コールバック関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="dad34-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="dad34-200">**pppoe_discover_terminate_confirm**: PPPoE 検出終了メッセージを送信するたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="dad34-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="dad34-201">この値が NULL の場合、検出終了コールバック関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="dad34-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="dad34-202">**pppoe_data_receive_notify**: PPPoE データ メッセージを受信するたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="dad34-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="dad34-203">この値を 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="dad34-203">This value must not be zero.</span></span>
- <span data-ttu-id="dad34-204">**pppoe_data_send_notify**: PPPoE データ メッセージを送信するたびに呼び出されるアプリケーション関数。</span><span class="sxs-lookup"><span data-stu-id="dad34-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="dad34-205">この値が NULL の場合、データ送信コールバック関数は無効になります。</span><span class="sxs-lookup"><span data-stu-id="dad34-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-206">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-206">Return Values</span></span>

- <span data-ttu-id="dad34-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターまたは関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-209">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-209">Allowed From</span></span>

<span data-ttu-id="dad34-210">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-211">例</span><span class="sxs-lookup"><span data-stu-id="dad34-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="dad34-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="dad34-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="dad34-213">アクセス コンセントレーター名を設定する</span><span class="sxs-lookup"><span data-stu-id="dad34-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-214">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="dad34-215">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-215">Description</span></span>

<span data-ttu-id="dad34-216">この関数は、アクセス コンセントレーター名関数呼び出しを設定します。</span><span class="sxs-lookup"><span data-stu-id="dad34-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="dad34-217">ac_name の文字列は NULL で終わる必要があり、ac_name の長さは引数リストで指定された長さと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-218">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-218">Input Parameters</span></span>

- <span data-ttu-id="dad34-219">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-220">**ac_name**: アクセス コンセントレーター名。</span><span class="sxs-lookup"><span data-stu-id="dad34-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="dad34-221">**ac_name_length**: ac_name の長さ。</span><span class="sxs-lookup"><span data-stu-id="dad34-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-222">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-222">Return Values</span></span>

- <span data-ttu-id="dad34-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="dad34-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) PPPoE サーバー、IP、パケット プール、またはスタック ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="dad34-225">**NX_SIZE_ERROR**: (0x09) name_length のチェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="dad34-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-226">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-226">Allowed From</span></span>

<span data-ttu-id="dad34-227">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-228">例</span><span class="sxs-lookup"><span data-stu-id="dad34-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="dad34-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="dad34-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="dad34-230">PPPoE サーバー サービス名を設定する</span><span class="sxs-lookup"><span data-stu-id="dad34-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-231">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="dad34-232">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-232">Description</span></span>

<span data-ttu-id="dad34-233">このサービスは、PPPoE サーバー サービス名を設定します。</span><span class="sxs-lookup"><span data-stu-id="dad34-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-234">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-234">Input Parameters</span></span>

- <span data-ttu-id="dad34-235">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-236">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-236">Return Values</span></span>

- <span data-ttu-id="dad34-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-239">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-239">Allowed From</span></span>

<span data-ttu-id="dad34-240">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-241">例</span><span class="sxs-lookup"><span data-stu-id="dad34-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="dad34-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="dad34-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="dad34-243">指定されたセッションに PPPoE サーバー データを送信する</span><span class="sxs-lookup"><span data-stu-id="dad34-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-244">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="dad34-245">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-245">Description</span></span>

<span data-ttu-id="dad34-246">このサービスでは、指定されたセッション ID を使用して PPPoE フレームを送信します。</span><span class="sxs-lookup"><span data-stu-id="dad34-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-247">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-247">Input Parameters</span></span>

- <span data-ttu-id="dad34-248">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-249">**session_index**: セッションのインデックス。</span><span class="sxs-lookup"><span data-stu-id="dad34-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="dad34-250">**data_ptr**: PPPoE サーバー データ フレームの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="dad34-251">**data_length**: PPPoE サーバー データ フレームの長さ。</span><span class="sxs-lookup"><span data-stu-id="dad34-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-252">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-252">Return Values</span></span>

- <span data-ttu-id="dad34-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="dad34-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE サーバー サービスが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="dad34-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="dad34-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-258">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-258">Allowed From</span></span>

<span data-ttu-id="dad34-259">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-260">例</span><span class="sxs-lookup"><span data-stu-id="dad34-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="dad34-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="dad34-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="dad34-262">指定されたセッションに PPPoE サーバー パケットを送信する</span><span class="sxs-lookup"><span data-stu-id="dad34-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-263">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="dad34-264">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-264">Description</span></span>

<span data-ttu-id="dad34-265">このサービスでは、指定されたセッション ID を使用して PPPoE パケットを送信します。</span><span class="sxs-lookup"><span data-stu-id="dad34-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-266">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-266">Input Parameters</span></span>

- <span data-ttu-id="dad34-267">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-268">**session_index**: セッションのインデックス。</span><span class="sxs-lookup"><span data-stu-id="dad34-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="dad34-269">**packet_ptr**: PPPoE パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-270">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-270">Return Values</span></span>

- <span data-ttu-id="dad34-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="dad34-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) PPPoE サーバー パケットが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="dad34-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE サーバー サービスが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="dad34-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="dad34-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-277">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-277">Allowed From</span></span>

<span data-ttu-id="dad34-278">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-279">例</span><span class="sxs-lookup"><span data-stu-id="dad34-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="dad34-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="dad34-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="dad34-281">指定された PPPoE セッションを終了する</span><span class="sxs-lookup"><span data-stu-id="dad34-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-282">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="dad34-283">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-283">Description</span></span>

<span data-ttu-id="dad34-284">このサービスは、指定された PPPoE セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="dad34-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-285">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-285">Input Parameters</span></span>

- <span data-ttu-id="dad34-286">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-287">**session_index**: セッションのインデックス。</span><span class="sxs-lookup"><span data-stu-id="dad34-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-288">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-288">Return Values</span></span>

- <span data-ttu-id="dad34-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="dad34-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE サーバー サービスが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="dad34-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="dad34-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-294">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-294">Allowed From</span></span>

<span data-ttu-id="dad34-295">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-296">例</span><span class="sxs-lookup"><span data-stu-id="dad34-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="dad34-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="dad34-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="dad34-298">指定された PPPoE セッション情報を取得する</span><span class="sxs-lookup"><span data-stu-id="dad34-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-299">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="dad34-300">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-300">Description</span></span>

<span data-ttu-id="dad34-301">このサービスは、指定された PPPoE セッション情報、クライアントの物理アドレス、セッション ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="dad34-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-302">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-302">Input Parameters</span></span>

- <span data-ttu-id="dad34-303">**pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="dad34-304">**session_index**: セッションのインデックス。</span><span class="sxs-lookup"><span data-stu-id="dad34-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="dad34-305">**client_mac_msw**: クライアントの物理アドレス MSW ポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="dad34-306">**client_mac_lsw**: クライアントの物理アドレス LSW ポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="dad34-307">**session_id**: セッション ID ポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-308">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-308">Return Values</span></span>

- <span data-ttu-id="dad34-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad34-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="dad34-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="dad34-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。</span><span class="sxs-lookup"><span data-stu-id="dad34-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="dad34-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。</span><span class="sxs-lookup"><span data-stu-id="dad34-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-313">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-313">Allowed From</span></span>

<span data-ttu-id="dad34-314">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-315">例</span><span class="sxs-lookup"><span data-stu-id="dad34-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="dad34-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="dad34-316">PppInitInd</span></span>

<span data-ttu-id="dad34-317">既定のサービス名を構成する</span><span class="sxs-lookup"><span data-stu-id="dad34-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-318">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="dad34-319">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-319">Description</span></span>

<span data-ttu-id="dad34-320">受信 PADI 要求をフィルター処理するために PPPoE で使用される "既定のサービス名" を TTP のソフトウェアが構成できるように、PPPoE ソフトウェアはこの関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="dad34-321">PPPoE ソフトウェアはこの情報を記憶しておく必要があり、一致するサービス名を含む PADI パケットを受信した場合に、PppDiscoverReq を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-322">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-322">Input Parameters</span></span>

- <span data-ttu-id="dad34-323">**length**: 既定のサービス名の長さ。</span><span class="sxs-lookup"><span data-stu-id="dad34-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="dad34-324">**aData**: 既定のサービス名。</span><span class="sxs-lookup"><span data-stu-id="dad34-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-325">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-325">Return Values</span></span>

<span data-ttu-id="dad34-326">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-327">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-327">Allowed From</span></span>

<span data-ttu-id="dad34-328">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-329">例</span><span class="sxs-lookup"><span data-stu-id="dad34-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="dad34-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="dad34-330">PppDiscoverCnf</span></span>

<span data-ttu-id="dad34-331">PADO パケットの Service Name フィールドを定義する</span><span class="sxs-lookup"><span data-stu-id="dad34-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="dad34-333">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-333">Description</span></span>

<span data-ttu-id="dad34-334">PPPoE ソフトウェアは、TTP のソフトウェアが PADO パケットの Service Name フィールドを定義できるように、この関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="dad34-335">PPPoE ソフトウェアは、PppDiscoverCnf が呼び出されるまで PADO を送信しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="dad34-336">PADO パケットには、PPPoE ソフトウェアの初期化時に定義されたアクセス コンセントレーター名 (RFC 2516 で定義されているタグ ID 0x0102 を使用) が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="dad34-337">複数のサービス名を aData に渡すことができます。各名前は null で終了します。</span><span class="sxs-lookup"><span data-stu-id="dad34-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="dad34-338">サービス名の一部として他のコマンドを渡す必要がある場合に最大限の柔軟性を提供するために、null 文字は区切り文字として使用されます。</span><span class="sxs-lookup"><span data-stu-id="dad34-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-339">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-339">Input Parameters</span></span>

- <span data-ttu-id="dad34-340">**length**: 既定のサービス名の長さ。</span><span class="sxs-lookup"><span data-stu-id="dad34-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="dad34-341">**aData**: 既定のサービス名。</span><span class="sxs-lookup"><span data-stu-id="dad34-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="dad34-342">**interfaceHandle**: インターフェイス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="dad34-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-343">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-343">Return Values</span></span>

<span data-ttu-id="dad34-344">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-345">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-345">Allowed From</span></span>

<span data-ttu-id="dad34-346">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-347">例</span><span class="sxs-lookup"><span data-stu-id="dad34-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="dad34-348">PppOpenCnf</span><span class="sxs-lookup"><span data-stu-id="dad34-348">PppOpenCnf</span></span>

<span data-ttu-id="dad34-349">PPPoE セッションを受け入れるか拒否する</span><span class="sxs-lookup"><span data-stu-id="dad34-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-350">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="dad34-351">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-351">Description</span></span>

<span data-ttu-id="dad34-352">PPPoE ソフトウェアは、TTP のソフトウェアが PPPoE セッションを受け入れるか拒否できるように、この関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="dad34-353">これに応じて、PPPoE スタックは接続を受け入れ、interfaceHandle に関連付けられた一意の PPPoE Session_ID 番号を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad34-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-354">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-354">Input Parameters</span></span>

- <span data-ttu-id="dad34-355">**accept**: 接続を受け入れる場合は NX_TRUE。</span><span class="sxs-lookup"><span data-stu-id="dad34-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="dad34-356">**interfaceHandle**: インターフェイス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="dad34-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-357">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-357">Return Values</span></span>

<span data-ttu-id="dad34-358">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-359">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-359">Allowed From</span></span>

<span data-ttu-id="dad34-360">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-361">例</span><span class="sxs-lookup"><span data-stu-id="dad34-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="dad34-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="dad34-362">PppCloseInd</span></span>

<span data-ttu-id="dad34-363">PPPoE セッションを閉じる</span><span class="sxs-lookup"><span data-stu-id="dad34-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-364">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="dad34-365">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-365">Description</span></span>

<span data-ttu-id="dad34-366">PPPoE ソフトウェアは、TTP のソフトウェアが PPPoE セッションを閉じることができるように、この関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="dad34-367">PPPoE ソフトウェアは、PADT メッセージの Generic-Error タグ (0x0203) に原因コード文字列を示します。</span><span class="sxs-lookup"><span data-stu-id="dad34-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-368">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-368">Input Parameters</span></span>

- <span data-ttu-id="dad34-369">**interfaceHandle**: インターフェイス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="dad34-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="dad34-370">**causeCode**: PPPoE サーバーからの接続を閉じる理由に関する情報を送信するための null 終端文字列。</span><span class="sxs-lookup"><span data-stu-id="dad34-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-371">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-371">Return Values</span></span>

<span data-ttu-id="dad34-372">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-373">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-373">Allowed From</span></span>

<span data-ttu-id="dad34-374">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-375">例</span><span class="sxs-lookup"><span data-stu-id="dad34-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="dad34-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="dad34-376">PppCloseCnf</span></span>

<span data-ttu-id="dad34-377">ハンドルが解放されたことを確認する</span><span class="sxs-lookup"><span data-stu-id="dad34-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-378">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="dad34-379">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-379">Description</span></span>

<span data-ttu-id="dad34-380">PPPoE ソフトウェアは、ハンドルが解放されたことを TTP のソフトウェアが確認できるように、この関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-381">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-381">Input Parameters</span></span>

- <span data-ttu-id="dad34-382">**interfaceHandle**: インターフェイス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="dad34-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-383">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-383">Return Values</span></span>

<span data-ttu-id="dad34-384">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-385">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-385">Allowed From</span></span>

<span data-ttu-id="dad34-386">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-387">例</span><span class="sxs-lookup"><span data-stu-id="dad34-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="dad34-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="dad34-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="dad34-389">先行する PPP データの受信確認を可能にする</span><span class="sxs-lookup"><span data-stu-id="dad34-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-390">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="dad34-391">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-391">Description</span></span>

<span data-ttu-id="dad34-392">PPPoE ソフトウェアは、先行する PppTransmitDataReq の受信確認を可能にするために、この関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="dad34-393">これは、TTP のソフトウェアが PPPoE から新しい PPP フレームを受け入れる準備ができていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="dad34-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-394">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-394">Input Parameters</span></span>

- <span data-ttu-id="dad34-395">**interfaceHandle**: インターフェイス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="dad34-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="dad34-396">**aData**: 受け入れられた PPP データ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dad34-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="dad34-397">**Packet_id**: パケット識別子。</span><span class="sxs-lookup"><span data-stu-id="dad34-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-398">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-398">Return Values</span></span>

<span data-ttu-id="dad34-399">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-400">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-400">Allowed From</span></span>

<span data-ttu-id="dad34-401">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-402">例</span><span class="sxs-lookup"><span data-stu-id="dad34-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="dad34-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="dad34-403">PppReceiveDataInd</span></span>

<span data-ttu-id="dad34-404">イーサネット経由で送信されたデータを受信する</span><span class="sxs-lookup"><span data-stu-id="dad34-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="dad34-405">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="dad34-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="dad34-406">説明</span><span class="sxs-lookup"><span data-stu-id="dad34-406">Description</span></span>

<span data-ttu-id="dad34-407">PPPoE ソフトウェアは、イーサネット経由で送信されたデータを受信するために、この関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="dad34-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dad34-408">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad34-408">Input Parameters</span></span>

- <span data-ttu-id="dad34-409">**interfaceHandle**: インターフェイス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="dad34-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="dad34-410">**length**: aData のバイト数。</span><span class="sxs-lookup"><span data-stu-id="dad34-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="dad34-411">**aData**: PPP データのフレームを格納するデータ バッファー。</span><span class="sxs-lookup"><span data-stu-id="dad34-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="dad34-412">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad34-412">Return Values</span></span>

<span data-ttu-id="dad34-413">**なし**</span><span class="sxs-lookup"><span data-stu-id="dad34-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dad34-414">許可元</span><span class="sxs-lookup"><span data-stu-id="dad34-414">Allowed From</span></span>

<span data-ttu-id="dad34-415">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="dad34-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="dad34-416">例</span><span class="sxs-lookup"><span data-stu-id="dad34-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```