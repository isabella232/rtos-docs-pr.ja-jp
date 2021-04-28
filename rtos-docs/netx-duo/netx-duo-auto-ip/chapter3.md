---
title: 第 3 章 - Azure RTOS NetX Duo AutoIP サービスの説明
description: この章では、すべての Azure RTOS NetX Duo AutoIP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810982"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="2e92f-103">第 3 章 - Azure RTOS NetX Duo AutoIP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="2e92f-104">この章では、すべての Azure RTOS NetX Duo AutoIP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2e92f-105">次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="2e92f-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2e92f-106">**nx_auto_ip_create**: *AutoIP インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="2e92f-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="2e92f-107">**nx_auto_ip_delete**: *AutoIP インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="2e92f-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="2e92f-108">**nx_auto_ip_get_address**: *現在の AutoIP アドレスを取得する*</span><span class="sxs-lookup"><span data-stu-id="2e92f-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="2e92f-109">**nx_auto_ip_set_interface**: *AutoIP アドレスが必要な IP インターフェイスを設定する*</span><span class="sxs-lookup"><span data-stu-id="2e92f-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="2e92f-110">**nx_auto_ip_start**: *AutoIP 処理を開始する*</span><span class="sxs-lookup"><span data-stu-id="2e92f-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="2e92f-111">**nx_auto_ip_stop**: *AutoIP 処理を停止する*</span><span class="sxs-lookup"><span data-stu-id="2e92f-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="2e92f-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="2e92f-112">nx_auto_ip_create</span></span>

<span data-ttu-id="2e92f-113">AutoIP インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="2e92f-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2e92f-114">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2e92f-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="2e92f-115">説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-115">Description</span></span>

<span data-ttu-id="2e92f-116">このサービスでは、指定された IP インスタンス上に AutoIP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e92f-117">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e92f-117">Input Parameters</span></span>

- <span data-ttu-id="2e92f-118">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e92f-119">**name**: AutoIP インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="2e92f-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="2e92f-120">**ip_ptr**: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="2e92f-121">**stack_ptr**: AutoIP スレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="2e92f-122">**stack_size**: AutoIP スレッド スタック領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="2e92f-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="2e92f-123">**priority**: AutoIP スレッドの優先度。</span><span class="sxs-lookup"><span data-stu-id="2e92f-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="2e92f-124">DHCP が使用される場合は、DHCP スレッドの優先度を IP インスタンス スレッドと AutoIP スレッドより高くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e92f-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e92f-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e92f-125">Return Values</span></span>

- <span data-ttu-id="2e92f-126">**NX_SUCCESS**: (0x00) AutoIP の作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2e92f-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="2e92f-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の作成のエラー。</span><span class="sxs-lookup"><span data-stu-id="2e92f-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="2e92f-128">NX_PTR_ERROR: (0x16) AutoIP、ip_ptr、またはスタック ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="2e92f-129">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e92f-130">許可元</span><span class="sxs-lookup"><span data-stu-id="2e92f-130">Allowed From</span></span>

<span data-ttu-id="2e92f-131">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="2e92f-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e92f-132">例</span><span class="sxs-lookup"><span data-stu-id="2e92f-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="2e92f-133">参照</span><span class="sxs-lookup"><span data-stu-id="2e92f-133">See Also</span></span>

<span data-ttu-id="2e92f-134">nx_auto_ip_delete、nx_auto_ip_set_interface、nx_auto_ip_get_address、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e92f-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="2e92f-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="2e92f-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="2e92f-136">AutoIP インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="2e92f-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2e92f-137">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2e92f-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2e92f-138">説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-138">Description</span></span>

<span data-ttu-id="2e92f-139">このサービスでは、指定された IP インスタンス上の以前に作成された AutoIP インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e92f-140">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e92f-140">Input Parameters</span></span>

- <span data-ttu-id="2e92f-141">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e92f-142">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e92f-142">Return Values</span></span>

- <span data-ttu-id="2e92f-143">**NX_SUCCESS**: (0x00) AutoIP の削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2e92f-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="2e92f-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の削除のエラー。</span><span class="sxs-lookup"><span data-stu-id="2e92f-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="2e92f-145">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e92f-146">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e92f-147">許可元</span><span class="sxs-lookup"><span data-stu-id="2e92f-147">Allowed From</span></span>

<span data-ttu-id="2e92f-148">Threads</span><span class="sxs-lookup"><span data-stu-id="2e92f-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e92f-149">例</span><span class="sxs-lookup"><span data-stu-id="2e92f-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="2e92f-150">参照</span><span class="sxs-lookup"><span data-stu-id="2e92f-150">See Also</span></span>

<span data-ttu-id="2e92f-151">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_get_address、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e92f-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="2e92f-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="2e92f-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="2e92f-153">現在の AutoIP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="2e92f-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2e92f-154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2e92f-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="2e92f-155">説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-155">Description</span></span>

<span data-ttu-id="2e92f-156">このサービスでは、現在設定されている AutoIP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="2e92f-157">存在しない場合は、0.0.0.0 の IP アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="2e92f-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e92f-158">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e92f-158">Input Parameters</span></span>

- <span data-ttu-id="2e92f-159">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e92f-160">**local_ip_address**: 戻り IP アドレスの宛先。</span><span class="sxs-lookup"><span data-stu-id="2e92f-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e92f-161">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e92f-161">Return Values</span></span>

- <span data-ttu-id="2e92f-162">**NX_SUCCESS**: (0x00) AutoIP アドレスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2e92f-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="2e92f-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) 有効な AutoIP アドレスがありません。</span><span class="sxs-lookup"><span data-stu-id="2e92f-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="2e92f-164">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e92f-165">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e92f-166">許可元</span><span class="sxs-lookup"><span data-stu-id="2e92f-166">Allowed From</span></span>

<span data-ttu-id="2e92f-167">初期化、タイマー、スレッド、ISR</span><span class="sxs-lookup"><span data-stu-id="2e92f-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2e92f-168">例</span><span class="sxs-lookup"><span data-stu-id="2e92f-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="2e92f-169">参照</span><span class="sxs-lookup"><span data-stu-id="2e92f-169">See Also</span></span>

<span data-ttu-id="2e92f-170">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e92f-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="2e92f-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="2e92f-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="2e92f-172">AutoIP のネットワーク インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="2e92f-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="2e92f-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2e92f-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2e92f-174">説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-174">Description</span></span>

<span data-ttu-id="2e92f-175">このサービスでは、AutoIP でネットワーク IP アドレスをプローブするネットワーク インターフェイスのインデックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="2e92f-176">既定値は 0 (プライマリ ネットワーク インターフェイス) です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="2e92f-177">マルチホーム デバイスにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="2e92f-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e92f-178">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e92f-178">Input Parameters</span></span>

- <span data-ttu-id="2e92f-179">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e92f-180">**interface_index**: IP アドレスをプローブするインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="2e92f-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="2e92f-181">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e92f-181">Return Values</span></span>

- <span data-ttu-id="2e92f-182">**NX_SUCCESS**: (0x00) AutoIP インターフェイスの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2e92f-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="2e92f-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) ネットワーク インターフェイスが無効です NX_PTR_ERROR (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e92f-184">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e92f-185">許可元</span><span class="sxs-lookup"><span data-stu-id="2e92f-185">Allowed From</span></span>

<span data-ttu-id="2e92f-186">初期化、タイマー、スレッド、ISR</span><span class="sxs-lookup"><span data-stu-id="2e92f-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2e92f-187">例</span><span class="sxs-lookup"><span data-stu-id="2e92f-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="2e92f-188">参照</span><span class="sxs-lookup"><span data-stu-id="2e92f-188">See Also</span></span>

<span data-ttu-id="2e92f-189">nx_auto_ip_create、nx_auto_ip_get_address、nx_auto_ip_delete、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e92f-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="2e92f-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2e92f-190">nx_auto_ip_start</span></span>

<span data-ttu-id="2e92f-191">AutoIP 処理を開始する</span><span class="sxs-lookup"><span data-stu-id="2e92f-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2e92f-192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2e92f-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="2e92f-193">説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-193">Description</span></span>

<span data-ttu-id="2e92f-194">このサービスでは、以前に作成された AutoIP インスタンス上で AutoIP プロトコルを開始します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e92f-195">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e92f-195">Input Parameters</span></span>

- <span data-ttu-id="2e92f-196">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e92f-197">**starting_local_address**: 省略可能な AutoIP の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2e92f-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="2e92f-198">IP_ADDRESS(0,0,0,0) の値は、ランダムな AutoIP アドレスを派生させる必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="2e92f-199">それ以外の場合は、有効な AutoIP アドレスが指定されていると、NetX AutoIP ではそのアドレスを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="2e92f-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e92f-200">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e92f-200">Return Values</span></span>

- <span data-ttu-id="2e92f-201">**NX_SUCCESS**: (0x00) AutoIP の開始に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2e92f-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="2e92f-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の開始のエラー。</span><span class="sxs-lookup"><span data-stu-id="2e92f-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="2e92f-203">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e92f-204">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e92f-205">許可元</span><span class="sxs-lookup"><span data-stu-id="2e92f-205">Allowed From</span></span>

<span data-ttu-id="2e92f-206">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="2e92f-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e92f-207">例</span><span class="sxs-lookup"><span data-stu-id="2e92f-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="2e92f-208">参照</span><span class="sxs-lookup"><span data-stu-id="2e92f-208">See Also</span></span>

<span data-ttu-id="2e92f-209">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_get_address、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e92f-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="2e92f-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e92f-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="2e92f-211">AutoIP 処理を停止する</span><span class="sxs-lookup"><span data-stu-id="2e92f-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2e92f-212">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2e92f-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2e92f-213">説明</span><span class="sxs-lookup"><span data-stu-id="2e92f-213">Description</span></span>

<span data-ttu-id="2e92f-214">このサービスでは、以前に作成されて開始された AutoIP インスタンス上の AutoIP プロトコルを停止します。</span><span class="sxs-lookup"><span data-stu-id="2e92f-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="2e92f-215">このサービスは通常、IP アドレスが DHCP 経由または手動で AutoIP 以外のアドレスに変更されているときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e92f-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e92f-216">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e92f-216">Input Parameters</span></span>

- <span data-ttu-id="2e92f-217">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e92f-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e92f-218">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e92f-218">Return Values</span></span>

- <span data-ttu-id="2e92f-219">**NX_SUCCESS**: (0x00) AutoIP の停止に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2e92f-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="2e92f-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の停止のエラー。</span><span class="sxs-lookup"><span data-stu-id="2e92f-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="2e92f-221">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e92f-222">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2e92f-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e92f-223">許可元</span><span class="sxs-lookup"><span data-stu-id="2e92f-223">Allowed From</span></span>

<span data-ttu-id="2e92f-224">Threads</span><span class="sxs-lookup"><span data-stu-id="2e92f-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e92f-225">例</span><span class="sxs-lookup"><span data-stu-id="2e92f-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="2e92f-226">参照</span><span class="sxs-lookup"><span data-stu-id="2e92f-226">See Also</span></span>

<span data-ttu-id="2e92f-227">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_get_address、nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2e92f-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>