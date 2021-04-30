---
title: '第 5 章: USBX OTG'
description: OTG 対応 USB コントローラーをハードウェア設計に使用できる場合、USBX で USB の OTG 機能がどのようにサポートされるかを説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 64a3c44f84b9ffca31d9e616d14d3d5d87c56bd7
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550322"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="8898d-103">第 5 章: USBX OTG</span><span class="sxs-lookup"><span data-stu-id="8898d-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="8898d-104">OTG 対応 USB コントローラーをハードウェア設計に使用できる場合、USBX が USB の OTG 機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8898d-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="8898d-105">USBX では、コア USB スタック内で OTG をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8898d-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="8898d-106">しかし、OTG が機能するには、特定の USB コントローラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="8898d-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="8898d-107">USBX OTG コントローラー関数は、usbx_otg ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="8898d-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="8898d-108">現在の USBX バージョンでは、完全な OTG 機能を備える NXP LPC3131 のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8898d-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="8898d-109">通常のコントローラー ドライバー関数 (ホストまたはデバイス) は従来どおりに標準の USBX usbx_device_controllers と usbx_host_controllers にありますが、usbx_otg ディレクトリには、USB コントローラーに関連付けられている特定の OTG 関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8898d-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="8898d-110">通常のホスト/デバイスの関数に加えて、OTG コントローラー対応関数には次の 4 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="8898d-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="8898d-111">VBUS 固有関数</span><span class="sxs-lookup"><span data-stu-id="8898d-111">VBUS specific functions</span></span>
- <span data-ttu-id="8898d-112">コントローラーの起動と停止</span><span class="sxs-lookup"><span data-stu-id="8898d-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="8898d-113">USB ロール マネージャー</span><span class="sxs-lookup"><span data-stu-id="8898d-113">USB role manager</span></span>
- <span data-ttu-id="8898d-114">割り込みハンドラー</span><span class="sxs-lookup"><span data-stu-id="8898d-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="8898d-115">VBUS 関数</span><span class="sxs-lookup"><span data-stu-id="8898d-115">VBUS functions</span></span>

<span data-ttu-id="8898d-116">各コントローラーには、電力管理要件に基づいて VBUS の状態を変更する VBUS マネージャーを搭載する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8898d-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="8898d-117">通常、この関数は VBUS のオン/オフの切り替えのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="8898d-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="8898d-118">コントローラーの起動と停止</span><span class="sxs-lookup"><span data-stu-id="8898d-118">Start and Stop the controller</span></span>

<span data-ttu-id="8898d-119">通常の USB 実装とは異なり、OTG では、ロールを変更するときにホストやデバイス スタック (またはそのいずれか) をアクティブ化/非アクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8898d-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="8898d-120">USB ロール マネージャー</span><span class="sxs-lookup"><span data-stu-id="8898d-120">USB role Manager</span></span>

<span data-ttu-id="8898d-121">USB ロール マネージャーは、USB の状態を変更するコマンドを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8898d-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="8898d-122">遷移を必要とする状態はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="8898d-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="8898d-123">州</span><span class="sxs-lookup"><span data-stu-id="8898d-123">State</span></span>                    | <span data-ttu-id="8898d-124">値</span><span class="sxs-lookup"><span data-stu-id="8898d-124">Value</span></span> | <span data-ttu-id="8898d-125">説明</span><span class="sxs-lookup"><span data-stu-id="8898d-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="8898d-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="8898d-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="8898d-127">0</span><span class="sxs-lookup"><span data-stu-id="8898d-127">0</span></span>     | <span data-ttu-id="8898d-128">デバイスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="8898d-128">The device is Idle.</span></span> <span data-ttu-id="8898d-129">何にも接続していません</span><span class="sxs-lookup"><span data-stu-id="8898d-129">Not connected to anything</span></span> |
| <span data-ttu-id="8898d-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="8898d-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="8898d-131">1</span><span class="sxs-lookup"><span data-stu-id="8898d-131">1</span></span>     | <span data-ttu-id="8898d-132">デバイスはタイプ A コネクタに接続しています</span><span class="sxs-lookup"><span data-stu-id="8898d-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="8898d-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="8898d-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="8898d-134">2</span><span class="sxs-lookup"><span data-stu-id="8898d-134">2</span></span>     | <span data-ttu-id="8898d-135">デバイスはタイプ B コネクタに接続しています</span><span class="sxs-lookup"><span data-stu-id="8898d-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="8898d-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="8898d-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="8898d-137">3</span><span class="sxs-lookup"><span data-stu-id="8898d-137">3</span></span>     | <span data-ttu-id="8898d-138">ホスト デバイスが切断されました</span><span class="sxs-lookup"><span data-stu-id="8898d-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="8898d-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="8898d-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="8898d-140">4</span><span class="sxs-lookup"><span data-stu-id="8898d-140">4</span></span>     | <span data-ttu-id="8898d-141">ホストからスレーブにロールが切り替えられます</span><span class="sxs-lookup"><span data-stu-id="8898d-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="8898d-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="8898d-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="8898d-143">5</span><span class="sxs-lookup"><span data-stu-id="8898d-143">5</span></span>     | <span data-ttu-id="8898d-144">スレーブ デバイスが切断しています</span><span class="sxs-lookup"><span data-stu-id="8898d-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="8898d-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="8898d-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="8898d-146">6</span><span class="sxs-lookup"><span data-stu-id="8898d-146">6</span></span>     | <span data-ttu-id="8898d-147">スレーブからホストにロールが切り替えられます</span><span class="sxs-lookup"><span data-stu-id="8898d-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="8898d-148">割り込みハンドラー</span><span class="sxs-lookup"><span data-stu-id="8898d-148">Interrupt handlers</span></span>

<span data-ttu-id="8898d-149">OTG 用のホストとデバイスのコントローラー ドライバーには、従来の USB 割り込みを超える信号 (特に SRP や VBUS による信号) を監視するために、別の割り込みハンドラーが必要です。</span><span class="sxs-lookup"><span data-stu-id="8898d-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="8898d-150">ここでは、USB OTG コントローラーを初期化する方法の例として、</span><span class="sxs-lookup"><span data-stu-id="8898d-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="8898d-151">NXP LPC3131 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8898d-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="8898d-152">この例では、VBUS 関数とモード変更のコールバック (ホストからスレーブ、またはその逆) を渡すことによって、LPC3131 を OTG モードで初期化します。</span><span class="sxs-lookup"><span data-stu-id="8898d-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="8898d-153">コールバック関数は、新しいモードを記録し、保留中のスレッドを新しい状態でウェイクアップするだけです。</span><span class="sxs-lookup"><span data-stu-id="8898d-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="8898d-154">渡されるモード値には、次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8898d-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="8898d-155">**UX_OTG_MODE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="8898d-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="8898d-156">**UX_OTG_MODE_SLAVE**</span><span class="sxs-lookup"><span data-stu-id="8898d-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="8898d-157">**UX_OTG_MODE_HOST**</span><span class="sxs-lookup"><span data-stu-id="8898d-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="8898d-158">アプリケーションでは、次の変数を調べることで、常にデバイスの種類を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8898d-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="8898d-159">値は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8898d-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="8898d-160">**UX_OTG_DEVICE_A**</span><span class="sxs-lookup"><span data-stu-id="8898d-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="8898d-161">**UX_OTG_DEVICE_B**</span><span class="sxs-lookup"><span data-stu-id="8898d-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="8898d-162">**UX_OTG_DEVICE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="8898d-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="8898d-163">USB OTG ホストデバイスは、次のコマンドを発行することによって、常にロール スワップを要求できます。</span><span class="sxs-lookup"><span data-stu-id="8898d-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="8898d-164">スレーブ デバイスの場合、発行するコマンドはありませんが、ロールを変更する状態を設定できます。ホストが **GET_STATUS** を発行したときに、この状態がホストによって取得されて、スワップが開始されます。</span><span class="sxs-lookup"><span data-stu-id="8898d-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
