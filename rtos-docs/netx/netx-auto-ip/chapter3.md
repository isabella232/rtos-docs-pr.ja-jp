---
title: 第 3 章 - Azure RTOS NetX AutoIP サービスの説明
description: この章では、すべての Azure RTOS NetX AutoIP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811663"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a><span data-ttu-id="2632d-103">第 3 章 - Azure RTOS NetX AutoIP サービスの説明</span><span class="sxs-lookup"><span data-stu-id="2632d-103">Chapter 3 - Description of Azure RTOS NetX AutoIP services</span></span>

<span data-ttu-id="2632d-104">この章では、すべての Azure RTOS NetX AutoIP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="2632d-104">This chapter contains a description of all Azure RTOS NetX AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2632d-105">次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="2632d-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2632d-106">**nx_auto_ip_create**: *AutoIP インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="2632d-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="2632d-107">**nx_auto_ip_delete**: *AutoIP インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="2632d-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="2632d-108">**nx_auto_ip_get_address**: *現在の AutoIP アドレスを取得する*</span><span class="sxs-lookup"><span data-stu-id="2632d-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="2632d-109">**nx_auto_ip_set_interface**: *AutoIP アドレスが必要な IP インターフェイスを設定する*</span><span class="sxs-lookup"><span data-stu-id="2632d-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="2632d-110">**nx_auto_ip_start**: *AutoIP 処理を開始する*</span><span class="sxs-lookup"><span data-stu-id="2632d-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="2632d-111">**nx_auto_ip_stop**: *AutoIP 処理を停止する*</span><span class="sxs-lookup"><span data-stu-id="2632d-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="2632d-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="2632d-112">nx_auto_ip_create</span></span>

<span data-ttu-id="2632d-113">AutoIP インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="2632d-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2632d-114">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2632d-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a><span data-ttu-id="2632d-115">説明</span><span class="sxs-lookup"><span data-stu-id="2632d-115">Description</span></span>

<span data-ttu-id="2632d-116">このサービスでは、指定された IP インスタンス上に AutoIP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2632d-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

- <span data-ttu-id="2632d-117">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-117">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2632d-118">**name**: AutoIP インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="2632d-118">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="2632d-119">**ip_ptr**: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-119">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="2632d-120">**stack_ptr**: AutoIP スレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-120">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="2632d-121">**stack_size**: AutoIP スレッド スタック領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="2632d-121">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="2632d-122">**priority**: AutoIP スレッドの優先度。</span><span class="sxs-lookup"><span data-stu-id="2632d-122">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="2632d-123">DHCP が使用される場合は、DHCP スレッドの優先度を IP インスタンス スレッドと AutoIP スレッドより高くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2632d-123">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="2632d-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="2632d-124">Return Values</span></span>

- <span data-ttu-id="2632d-125">**NX_SUCCESS**: (0x00) AutoIP の作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2632d-125">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="2632d-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の作成のエラー。</span><span class="sxs-lookup"><span data-stu-id="2632d-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="2632d-127">NX_PTR_ERROR: (0x16) AutoIP、ip_ptr、またはスタック ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="2632d-128">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-128">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2632d-129">許可元</span><span class="sxs-lookup"><span data-stu-id="2632d-129">Allowed From</span></span>

<span data-ttu-id="2632d-130">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="2632d-130">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2632d-131">例</span><span class="sxs-lookup"><span data-stu-id="2632d-131">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="2632d-132">参照</span><span class="sxs-lookup"><span data-stu-id="2632d-132">See Also</span></span>

<span data-ttu-id="2632d-133">nx_auto_ip_delete、nx_auto_ip_set_interface、nx_auto_ip_get_address、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2632d-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="2632d-134">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="2632d-134">nx_auto_ip_delete</span></span>

<span data-ttu-id="2632d-135">AutoIP インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="2632d-135">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2632d-136">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2632d-136">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2632d-137">説明</span><span class="sxs-lookup"><span data-stu-id="2632d-137">Description</span></span>

<span data-ttu-id="2632d-138">このサービスでは、指定された IP インスタンス上の以前に作成された AutoIP インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="2632d-138">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2632d-139">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2632d-139">Input Parameters</span></span>

- <span data-ttu-id="2632d-140">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-140">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2632d-141">戻り値</span><span class="sxs-lookup"><span data-stu-id="2632d-141">Return Values</span></span>

- <span data-ttu-id="2632d-142">**NX_SUCCESS**: (0x00) AutoIP の削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2632d-142">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="2632d-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の削除のエラー。</span><span class="sxs-lookup"><span data-stu-id="2632d-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="2632d-144">NX_PTR_ERROR (0x16): AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-144">NX_PTR_ERROR (0x16): Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2632d-145">NX_CALLER_ERROR (0x11): このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-145">NX_CALLER_ERROR (0x11): Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2632d-146">許可元</span><span class="sxs-lookup"><span data-stu-id="2632d-146">Allowed From</span></span>

<span data-ttu-id="2632d-147">Threads</span><span class="sxs-lookup"><span data-stu-id="2632d-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2632d-148">例</span><span class="sxs-lookup"><span data-stu-id="2632d-148">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="2632d-149">参照</span><span class="sxs-lookup"><span data-stu-id="2632d-149">See Also</span></span>

<span data-ttu-id="2632d-150">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_get_address、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2632d-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="2632d-151">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="2632d-151">nx_auto_ip_get_address</span></span>

<span data-ttu-id="2632d-152">現在の AutoIP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="2632d-152">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2632d-153">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2632d-153">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="2632d-154">説明</span><span class="sxs-lookup"><span data-stu-id="2632d-154">Description</span></span>

<span data-ttu-id="2632d-155">このサービスでは、現在設定されている AutoIP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2632d-155">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="2632d-156">存在しない場合は、0.0.0.0 の IP アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="2632d-156">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2632d-157">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2632d-157">Input Parameters</span></span>

- <span data-ttu-id="2632d-158">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-158">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2632d-159">**local_ip_address**: 戻り IP アドレスの宛先。</span><span class="sxs-lookup"><span data-stu-id="2632d-159">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2632d-160">戻り値</span><span class="sxs-lookup"><span data-stu-id="2632d-160">Return Values</span></span>

- <span data-ttu-id="2632d-161">**NX_SUCCESS**: (0x00) AutoIP アドレスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2632d-161">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="2632d-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) 有効な AutoIP アドレスがありません。</span><span class="sxs-lookup"><span data-stu-id="2632d-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="2632d-163">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-163">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2632d-164">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-164">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2632d-165">許可元</span><span class="sxs-lookup"><span data-stu-id="2632d-165">Allowed From</span></span>

<span data-ttu-id="2632d-166">初期化、タイマー、スレッド、ISR</span><span class="sxs-lookup"><span data-stu-id="2632d-166">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2632d-167">例</span><span class="sxs-lookup"><span data-stu-id="2632d-167">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="2632d-168">参照</span><span class="sxs-lookup"><span data-stu-id="2632d-168">See Also</span></span>

<span data-ttu-id="2632d-169">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2632d-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="2632d-170">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="2632d-170">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="2632d-171">AutoIP のネットワーク インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="2632d-171">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="2632d-172">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2632d-172">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2632d-173">説明</span><span class="sxs-lookup"><span data-stu-id="2632d-173">Description</span></span>

<span data-ttu-id="2632d-174">このサービスでは、AutoIP でネットワーク IP アドレスをプローブするネットワーク インターフェイスのインデックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="2632d-174">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="2632d-175">既定値は 0 (プライマリ ネットワーク インターフェイス) です。</span><span class="sxs-lookup"><span data-stu-id="2632d-175">The default is zero (the primary network interface).</span></span> <span data-ttu-id="2632d-176">マルチホーム デバイスにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="2632d-176">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2632d-177">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2632d-177">Input Parameters</span></span>

- <span data-ttu-id="2632d-178">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-178">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2632d-179">**interface_index**: IP アドレスをプローブするインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="2632d-179">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="2632d-180">戻り値</span><span class="sxs-lookup"><span data-stu-id="2632d-180">Return Values</span></span>

- <span data-ttu-id="2632d-181">**NX_SUCCESS**: (0x00) AutoIP インターフェイスの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2632d-181">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="2632d-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) ネットワーク インターフェイスが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface</span></span> 
- <span data-ttu-id="2632d-183">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-183">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2632d-184">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2632d-185">許可元</span><span class="sxs-lookup"><span data-stu-id="2632d-185">Allowed From</span></span>

<span data-ttu-id="2632d-186">初期化、タイマー、スレッド、ISR</span><span class="sxs-lookup"><span data-stu-id="2632d-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2632d-187">例</span><span class="sxs-lookup"><span data-stu-id="2632d-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a><span data-ttu-id="2632d-188">参照</span><span class="sxs-lookup"><span data-stu-id="2632d-188">See Also</span></span>

<span data-ttu-id="2632d-189">nx_auto_ip_create、nx_auto_ip_get_address、nx_auto_ip_delete、nx_auto_ip_start、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2632d-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="2632d-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2632d-190">nx_auto_ip_start</span></span>

<span data-ttu-id="2632d-191">AutoIP 処理を開始する</span><span class="sxs-lookup"><span data-stu-id="2632d-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2632d-192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2632d-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="2632d-193">説明</span><span class="sxs-lookup"><span data-stu-id="2632d-193">Description</span></span>

<span data-ttu-id="2632d-194">このサービスでは、以前に作成された AutoIP インスタンス上で AutoIP プロトコルを開始します。</span><span class="sxs-lookup"><span data-stu-id="2632d-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2632d-195">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2632d-195">Input Parameters</span></span>

- <span data-ttu-id="2632d-196">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2632d-197">**starting_local_address**: 省略可能な AutoIP の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2632d-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="2632d-198">IP_ADDRESS(0,0,0,0) の値は、ランダムな AutoIP アドレスを派生させる必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2632d-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="2632d-199">それ以外の場合は、有効な AutoIP アドレスが指定されていると、NetX AutoIP ではそのアドレスを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="2632d-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2632d-200">戻り値</span><span class="sxs-lookup"><span data-stu-id="2632d-200">Return Values</span></span>

- <span data-ttu-id="2632d-201">**NX_SUCCESS**: (0x00) AutoIP の開始に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2632d-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="2632d-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の開始のエラー。</span><span class="sxs-lookup"><span data-stu-id="2632d-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="2632d-203">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2632d-204">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2632d-205">許可元</span><span class="sxs-lookup"><span data-stu-id="2632d-205">Allowed From</span></span>

<span data-ttu-id="2632d-206">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="2632d-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2632d-207">例</span><span class="sxs-lookup"><span data-stu-id="2632d-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="2632d-208">参照</span><span class="sxs-lookup"><span data-stu-id="2632d-208">See Also</span></span>

<span data-ttu-id="2632d-209">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_get_address、nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2632d-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="2632d-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2632d-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="2632d-211">AutoIP 処理を停止する</span><span class="sxs-lookup"><span data-stu-id="2632d-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2632d-212">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="2632d-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2632d-213">説明</span><span class="sxs-lookup"><span data-stu-id="2632d-213">Description</span></span>

<span data-ttu-id="2632d-214">このサービスでは、以前に作成されて開始された AutoIP インスタンス上の AutoIP プロトコルを停止します。</span><span class="sxs-lookup"><span data-stu-id="2632d-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="2632d-215">このサービスは通常、IP アドレスが DHCP 経由または手動で AutoIP 以外のアドレスに変更されているときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="2632d-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2632d-216">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="2632d-216">Input Parameters</span></span>

- <span data-ttu-id="2632d-217">**auto_ip_ptr**: AutoIP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2632d-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2632d-218">戻り値</span><span class="sxs-lookup"><span data-stu-id="2632d-218">Return Values</span></span>

- <span data-ttu-id="2632d-219">**NX_SUCCESS**: (0x00) AutoIP の停止に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2632d-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="2632d-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP の停止のエラー。</span><span class="sxs-lookup"><span data-stu-id="2632d-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="2632d-221">NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2632d-222">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="2632d-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2632d-223">許可元</span><span class="sxs-lookup"><span data-stu-id="2632d-223">Allowed From</span></span>

<span data-ttu-id="2632d-224">Threads</span><span class="sxs-lookup"><span data-stu-id="2632d-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2632d-225">例</span><span class="sxs-lookup"><span data-stu-id="2632d-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="2632d-226">参照</span><span class="sxs-lookup"><span data-stu-id="2632d-226">See Also</span></span>

<span data-ttu-id="2632d-227">nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_get_address、nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2632d-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>