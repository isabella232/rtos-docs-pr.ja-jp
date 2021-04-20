---
title: 第 2 章 - USBX デバイス クラスに関する考慮事項
description: USB デバイス RNDIS クラスにより、USB ホスト システムが、イーサネット デバイスとしてデバイスと通信できるようになります。 このクラスは Microsoft 独自の実装に基づいており、Windows プラットフォームに固有です。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082219"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="eebb2-104">第 2 章 - USBX デバイス クラスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="eebb2-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="eebb2-105">USB デバイス RNDIS クラス</span><span class="sxs-lookup"><span data-stu-id="eebb2-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="eebb2-106">USB デバイス RNDIS クラスにより、USB ホスト システムが、イーサネット デバイスとしてデバイスと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="eebb2-107">このクラスは Microsoft 独自の実装に基づいており、Windows プラットフォームに固有です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="eebb2-108">RNDIS 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="eebb2-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="eebb2-110">RNDIS クラスは、CDC-ACM および CDC-ECM とよく似たデバイス記述子アプローチを採用しており、IAD 記述子も必要とします。</span><span class="sxs-lookup"><span data-stu-id="eebb2-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="eebb2-111">デバイス記述子の定義と要件については、「CDC-ACM クラス」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eebb2-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="eebb2-112">RNDIS クラスのアクティブ化は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="eebb2-113">CDC-ECM の場合、RNDIS クラスにはローカルとリモートの 2 つのノードが必要ですが、リモート ノードを記述する文字列記述子は必要はありません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="eebb2-114">ただし、Microsoft 独自のメッセージング メカニズムにより、追加パラメーターがいくつか必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="eebb2-115">まず、ベンダー ID を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="eebb2-116">同様に、RNDIS のドライバー バージョンも必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="eebb2-117">ベンダー文字列を指定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-117">A vendor string must also be given.</span></span>

<span data-ttu-id="eebb2-118">RNDIS クラスには、両方の方法でデータを転送するための組み込み API が用意されていますが、ユーザー アプリケーションは NetX 経由で USB イーサネット デバイスと通信するため、アプリケーションには表示されません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="eebb2-119">USBX RNDIS クラスは、Azure RTOS NetX ネットワーク スタックに緊密に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="eebb2-120">NetX と USBX の両方の RNDIS クラスを使用するアプリケーションは、通常の方法で NetX ネットワークスタックを起動しますが、それに加えて次のように USB ネットワーク スタックをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="eebb2-121">USB ネットワーク スタックは 1 回だけアクティブにする必要があり、RNDIS に固有ではありませんが、NetX サービスを必要とするすべての USB クラスで必要になります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="eebb2-122">RNDIS クラスは、Microsoft オペレーティング システムに固有であるため、MAC OS や Linux ホストによって認識されません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="eebb2-123">Windows プラットフォーム上で、.inf ファイルが、デバイス記述子と一致するホスト上に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="eebb2-124">Microsoft は RNDIS クラスのテンプレートを提供しており、これは usbx_windows_host_files ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="eebb2-125">新しいバージョンの Windows の場合は、RNDIS_Template ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="eebb2-126">このファイルを変更して、デバイスによって使用される PID/VID を反映させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="eebb2-127">この PID/VID は、会社と製品が USB-IF に登録されたときに、最終的な顧客に固有のものになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="eebb2-128">inf ファイル内の変更対象のフィールドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="eebb2-129">RNDIS デバイスのデバイス フレームワーク内で、PID/VID はデバイス記述子に格納されます (上記の宣言されたデバイス記述子を参照)</span><span class="sxs-lookup"><span data-stu-id="eebb2-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="eebb2-130">USB ホスト システムによって USB RNDIS デバイスが検出されると、ネットワーク インターフェイスがマウントされ、デバイスは、ネットワーク プロトコル スタックと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="eebb2-131">詳細については、「ホスト オペレーティング システム」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eebb2-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="eebb2-132">USB デバイス DFU クラス</span><span class="sxs-lookup"><span data-stu-id="eebb2-132">USB Device DFU Class</span></span>

<span data-ttu-id="eebb2-133">USB デバイス DFU クラスにより、USB ホスト システムが、ホスト アプリケーションに基づいてデバイス ファームウェアを更新できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="eebb2-134">DFU クラスは、USB-IF 標準クラスです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="eebb2-135">USBX DFU クラスは比較的シンプルです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="eebb2-136">そのデバイス記述子には、コントロール エンドポイント以外は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="eebb2-137">ほとんどの場合、このクラスは USB 複合デバイスに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="eebb2-138">デバイスは、ストレージ デバイスや通信デバイスなど何でも構いません。また、追加された DFU インターフェイスは、デバイスが即座にファームウェアを更新できることをホストに通知できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="eebb2-139">DFU クラスは 3 つの手順で動作します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="eebb2-140">まず、エクスポートされたクラスを使用して、デバイスが通常どおりにマウントされます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="eebb2-141">ホスト (Windows または Linux) 上のアプリケーションが、DFU クラスを実行し、デバイスを DFU モードにリセットするように要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="eebb2-142">デバイスは、短時間 (ホストとデバイスが RESET シーケンスを検出できるだけの時間) だけバスから非表示になります。そして再起動時にデバイスは排他的に DFU モードになり、ホスト アプリケーションがファームウェアのアップグレードを送信するのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="eebb2-143">ファームウェアのアップグレードが完了すると、デバイスはホスト アプリケーションによってリセットされ、再列挙時に新しいファームウェアで通常の動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="eebb2-144">DFU デバイス フレームワークは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="eebb2-145">この例では、DFU 記述子は他のクラスには関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="eebb2-146">単純なインターフェイス記述子があり、その他のエンドポイントはアタッチされていません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="eebb2-147">デバイスの DFU 機能の詳細について説明する機能記述子があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="eebb2-148">DFU 機能の説明は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="eebb2-149">名前</span><span class="sxs-lookup"><span data-stu-id="eebb2-149">Name</span></span>             | <span data-ttu-id="eebb2-150">Offset</span><span class="sxs-lookup"><span data-stu-id="eebb2-150">Offset</span></span>  | <span data-ttu-id="eebb2-151">サイズ</span><span class="sxs-lookup"><span data-stu-id="eebb2-151">Size</span></span> | <span data-ttu-id="eebb2-152">type</span><span class="sxs-lookup"><span data-stu-id="eebb2-152">type</span></span>      | <span data-ttu-id="eebb2-153">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="eebb2-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="eebb2-154">bmAttributes</span></span>  | <span data-ttu-id="eebb2-155">2</span><span class="sxs-lookup"><span data-stu-id="eebb2-155">2</span></span>     | <span data-ttu-id="eebb2-156">1</span><span class="sxs-lookup"><span data-stu-id="eebb2-156">1</span></span>   | <span data-ttu-id="eebb2-157">ビット フィールド</span><span class="sxs-lookup"><span data-stu-id="eebb2-157">Bit field</span></span> | <span data-ttu-id="eebb2-158">ビット 3: デバイスは、DFU_DETACH 要求を受信すると、バス デタッチ-アタッチ シーケンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="eebb2-159">ホストは、USB リセットを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="eebb2-160">(bitWillDetach) 0 = いいえ 1 = はい ビット 2: デバイスは明示フェーズ後に USB 経由で通信できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="eebb2-161">(bitManifestationTolerant) 0 = いいえ、バス リセット確認要 1 = はい ビット 1: アップロード対応 (bitCanUpload) 0 = いいえ 1 = はい ビット 0: ダウンロード対応 (bitCanDnload) 0 = いいえ 1 = はい</span><span class="sxs-lookup"><span data-stu-id="eebb2-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="eebb2-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="eebb2-162">wDetachTimeOut</span></span>  | <span data-ttu-id="eebb2-163">3</span><span class="sxs-lookup"><span data-stu-id="eebb2-163">3</span></span>      | <span data-ttu-id="eebb2-164">2</span><span class="sxs-lookup"><span data-stu-id="eebb2-164">2</span></span>  | <span data-ttu-id="eebb2-165">number</span><span class="sxs-lookup"><span data-stu-id="eebb2-165">number</span></span>    | <span data-ttu-id="eebb2-166">DFU_DETACH 要求の受信後にデバイスが待機する時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="eebb2-167">USB リセットせずにこの時間が経過すると、デバイスは再構成フェーズを終了し、通常の操作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="eebb2-168">これは、デバイスが待機できる最大時間を表します (タイマーなどによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="eebb2-169">この値は、USBX によって 1000 ミリ秒に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="eebb2-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="eebb2-170">wTransferSize</span></span>  | <span data-ttu-id="eebb2-171">5</span><span class="sxs-lookup"><span data-stu-id="eebb2-171">5</span></span>      | <span data-ttu-id="eebb2-172">2</span><span class="sxs-lookup"><span data-stu-id="eebb2-172">2</span></span>  | <span data-ttu-id="eebb2-173">number</span><span class="sxs-lookup"><span data-stu-id="eebb2-173">number</span></span>    | <span data-ttu-id="eebb2-174">デバイスが受け入れることができる制御\-書き込み操作あたりの最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="eebb2-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="eebb2-175">この値は、USBX によって 64 バイトに設定されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="eebb2-176">DFU クラスの宣言は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="eebb2-177">DFU クラスは、ターゲットに固有のデバイス ファームウェア アプリケーションを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="eebb2-178">このため、ファームウェアのブロックの読み取りおよび書き込みを行い、ファームウェア更新アプリケーションから状態を取得するために、コールバックがいくつか定義されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="eebb2-179">また、DFU クラスには、ファームウェアの転送の開始と終了が発生したときにアプリケーションに通知する、通知コールバック関数もあります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="eebb2-180">一般的な DFU アプリケーション フローの説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-180">Following is the description of a typical DFU application flow.</span></span>

![DFU アプリケーション フロー](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="eebb2-182">DFU クラスの主な課題は、ファームウェアのダウンロードを実行するための適切なアプリケーションをホスト上で取得することです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="eebb2-183">Microsoft または USB-IF によって提供されるアプリケーションはありません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="eebb2-184">シェアウェアがいくつか存在し、それらは Linux 上では適切に動作し、Windows 上でも程度の差はありますが、それなりに機能します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="eebb2-185">Linux 上では、[https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) にある dfu-utils を使用できます。また、次のリンクには dfu utils に関する情報が多数記載されています: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span><span class="sxs-lookup"><span data-stu-id="eebb2-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="eebb2-186">ホストとデバイスの間のリセット シーケンスは、DFU の Linux 実装によって正しく実行されます。したがって、デバイスは、この処理を実行する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="eebb2-187">Linuxは、bmAttributes *bitWillDetach* 0 を受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="eebb2-188">一方、Window の場合は、デバイスがリセットを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="eebb2-189">Windows 上で、USB レジストリは、USB デバイスと、その PID/VID、および DFU アプリケーションによって使用される USB ライブラリを関連付けられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="eebb2-190">これは、[https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) にある無料のユーティリティ Zadig を使って簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="eebb2-191">Zadig を初めて実行すると、次のスクリーンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-191">Running Zadig for the first time will show this screen:</span></span>

![Zadig の初回の実行](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="eebb2-193">デバイスの一覧からデバイスを見つけて、libusb Windows ドライバーに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="eebb2-194">これにより、デバイスの PID/VID が DFU ユーティリティによって使用される Windows USB ライブラリにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="eebb2-195">DFU コマンドを操作するには、zip 圧縮された dfu ユーティリティをディレクトリに展開するだけです。また、libusb dll が、その同じディレクトリに存在することも確認します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="eebb2-196">DFU ユーティリティは、コマンド ラインを使用して DOS ボックスから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="eebb2-197">まず、**dfu-util –l** コマンドを入力して、デバイスが一覧に表示されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="eebb2-198">表示されていない場合は、Zadig を実行して、デバイスが一覧表示され、USB ライブラリに関連付けられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="eebb2-199">次のスクリーンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="eebb2-200">次の手順で、ダウンロードするファイルを準備します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="eebb2-201">USBX DFU クラスは、このファイルに対して何の検証も実行せず、その内部形式には依存していません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="eebb2-202">このファームウェア ファイルはターゲットに対して非常に限定的なものですが、DFU または USBX 固有ではありません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="eebb2-203">その後、次のコマンドを入力すると、ファイルを送信するように dfu-util に指示できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="eebb2-204">dfu-util により、ファームウェアが完全にダウンロードされるまでのファイルのダウンロード プロセスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="eebb2-205">USB デバイス PIMA クラス (PTP レスポンダー)</span><span class="sxs-lookup"><span data-stu-id="eebb2-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="eebb2-206">USB デバイス PIMA クラスにより、USB ホスト システム (イニシエーター) が、</span><span class="sxs-lookup"><span data-stu-id="eebb2-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="eebb2-207">メディア ファイルを転送するための PIMA デバイス (レスポンダー) に接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="eebb2-208">USBX Pima クラスは、PTP (画像転送プロトコル) クラスとも呼ばれる USB-IF PIMA 15740 クラスに準拠しています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="eebb2-209">USBX デバイス側の PIMA クラスは、次の操作をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="eebb2-210">操作コード</span><span class="sxs-lookup"><span data-stu-id="eebb2-210">Operation code</span></span>                                    | <span data-ttu-id="eebb2-211">値</span><span class="sxs-lookup"><span data-stu-id="eebb2-211">Value</span></span> | <span data-ttu-id="eebb2-212">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="eebb2-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="eebb2-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="eebb2-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="eebb2-214">0x1001</span></span>  | <span data-ttu-id="eebb2-215">デバイスでサポートされている操作とイベントを取得します</span><span class="sxs-lookup"><span data-stu-id="eebb2-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="eebb2-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="eebb2-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="eebb2-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="eebb2-217">0x1002</span></span>  | <span data-ttu-id="eebb2-218">ホストとデバイスの間のセッションを開きます</span><span class="sxs-lookup"><span data-stu-id="eebb2-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="eebb2-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="eebb2-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="eebb2-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="eebb2-220">0x1003</span></span>  | <span data-ttu-id="eebb2-221">ホストとデバイスの間のセッションを閉じます</span><span class="sxs-lookup"><span data-stu-id="eebb2-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="eebb2-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="eebb2-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="eebb2-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="eebb2-223">0x1004</span></span>  | <span data-ttu-id="eebb2-224">デバイスのストレージ ID を返します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="eebb2-225">USBX PIMA は 1 つのストレージ ID のみを使用します</span><span class="sxs-lookup"><span data-stu-id="eebb2-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="eebb2-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="eebb2-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="eebb2-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="eebb2-227">0x1005</span></span>  | <span data-ttu-id="eebb2-228">最大容量および空き領域などのストレージ オブジェクトに関する情報を返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="eebb2-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="eebb2-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="eebb2-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="eebb2-230">0x1006</span></span>  | <span data-ttu-id="eebb2-231">ストレージ デバイス内に含まれるオブジェクトの数を返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="eebb2-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="eebb2-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="eebb2-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="eebb2-233">0x1007</span></span>  | <span data-ttu-id="eebb2-234">ストレージ デバイス上のオブジェクトのハンドルの配列を返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="eebb2-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="eebb2-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="eebb2-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="eebb2-236">0x1008</span></span>  | <span data-ttu-id="eebb2-237">オブジェクトの名前、その作成日、変更日などのオブジェクトに関する情報を返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="eebb2-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="eebb2-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="eebb2-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="eebb2-239">0x1009</span></span>  | <span data-ttu-id="eebb2-240">特定のオブジェクトに関連するデータを返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="eebb2-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="eebb2-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="eebb2-242">0x100A</span><span class="sxs-lookup"><span data-stu-id="eebb2-242">0x100A</span></span>  | <span data-ttu-id="eebb2-243">オブジェクトに関するサムネイル (使用できる場合) を送信します</span><span class="sxs-lookup"><span data-stu-id="eebb2-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="eebb2-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="eebb2-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="eebb2-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="eebb2-245">0x100B</span></span>  | <span data-ttu-id="eebb2-246">メディア上のオブジェクトを削除します</span><span class="sxs-lookup"><span data-stu-id="eebb2-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="eebb2-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="eebb2-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="eebb2-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="eebb2-248">0x100C</span></span>  | <span data-ttu-id="eebb2-249">メディア上にオブジェクトを作成するためのオブジェクト情報をデバイスに送信します</span><span class="sxs-lookup"><span data-stu-id="eebb2-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="eebb2-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="eebb2-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="eebb2-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="eebb2-251">0x100D</span></span>  | <span data-ttu-id="eebb2-252">オブジェクトのデータをデバイスに送信します</span><span class="sxs-lookup"><span data-stu-id="eebb2-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="eebb2-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="eebb2-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="eebb2-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="eebb2-254">0x100F</span></span>  | <span data-ttu-id="eebb2-255">デバイス メディアをクリーンします</span><span class="sxs-lookup"><span data-stu-id="eebb2-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="eebb2-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="eebb2-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="eebb2-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="eebb2-257">0x0110</span></span>  | <span data-ttu-id="eebb2-258">ターゲット デバイスをリセットします</span><span class="sxs-lookup"><span data-stu-id="eebb2-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="eebb2-259">操作コード</span><span class="sxs-lookup"><span data-stu-id="eebb2-259">Operation Code</span></span>                                         | <span data-ttu-id="eebb2-260">値</span><span class="sxs-lookup"><span data-stu-id="eebb2-260">Value</span></span> | <span data-ttu-id="eebb2-261">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="eebb2-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="eebb2-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="eebb2-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="eebb2-263">0x4001</span></span>  | <span data-ttu-id="eebb2-264">現在のトランザクションを取り消します</span><span class="sxs-lookup"><span data-stu-id="eebb2-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="eebb2-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="eebb2-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="eebb2-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="eebb2-266">0x4002</span></span>  | <span data-ttu-id="eebb2-267">オブジェクトがデバイス メディアに追加されました。これはホストによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="eebb2-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="eebb2-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="eebb2-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="eebb2-269">0x4003</span></span>  | <span data-ttu-id="eebb2-270">オブジェクトがデバイス メディアから削除されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="eebb2-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="eebb2-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="eebb2-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="eebb2-272">0x4004</span></span>  | <span data-ttu-id="eebb2-273">メディアがデバイスに追加されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="eebb2-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="eebb2-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="eebb2-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="eebb2-275">0x4005</span></span>  | <span data-ttu-id="eebb2-276">メディアがデバイスから削除されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="eebb2-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="eebb2-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="eebb2-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="eebb2-278">0x4006</span></span>  | <span data-ttu-id="eebb2-279">デバイスのプロパティが変更されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="eebb2-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="eebb2-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="eebb2-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="eebb2-281">0x4007</span></span>  | <span data-ttu-id="eebb2-282">オブジェクト情報が変更されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="eebb2-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="eebb2-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="eebb2-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="eebb2-284">0x4008</span></span>  | <span data-ttu-id="eebb2-285">デバイスが変更されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="eebb2-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="eebb2-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="eebb2-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="eebb2-287">0x4009</span></span>  | <span data-ttu-id="eebb2-288">デバイスはオブジェクトの転送をホストに要求します</span><span class="sxs-lookup"><span data-stu-id="eebb2-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="eebb2-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="eebb2-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="eebb2-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="eebb2-290">0x400A</span></span>  | <span data-ttu-id="eebb2-291">デバイスはメディアがいっぱいであることを報告します</span><span class="sxs-lookup"><span data-stu-id="eebb2-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="eebb2-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="eebb2-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="eebb2-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="eebb2-293">0x400B</span></span>  | <span data-ttu-id="eebb2-294">デバイスは自身がリセットされたことを報告します</span><span class="sxs-lookup"><span data-stu-id="eebb2-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="eebb2-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="eebb2-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="eebb2-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="eebb2-296">0x400C</span></span>  | <span data-ttu-id="eebb2-297">デバイス上でストレージ情報が変更されました</span><span class="sxs-lookup"><span data-stu-id="eebb2-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="eebb2-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="eebb2-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="eebb2-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="eebb2-299">0x400D</span></span>  | <span data-ttu-id="eebb2-300">キャプチャが完了しました</span><span class="sxs-lookup"><span data-stu-id="eebb2-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="eebb2-301">USBX PIMA デバイス クラスは、TX スレッドを使用して、ホストからの PIMA コマンドをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="eebb2-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="eebb2-302">PIMA コマンドは、コマンド ブロック、データ ブロック、および状態フェーズで構成されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="eebb2-303">関数 ux_device_class_pima_thread は、要求をスタックにポストして、ホスト側から PIMA コマンドを受信します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="eebb2-304">PIMA コマンドがデコードされ、コンテンツに対して検証されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="eebb2-305">コマンド ブロックが有効な場合は、適切なコマンド ハンドラーに分岐します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="eebb2-306">PIMA コマンドのほとんどは、セッションがホストによって開かれた場合にのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="eebb2-307">唯一の例外は、**UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO** コマンドです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="eebb2-308">USBX PIMA 実装を使用する場合、イニシエーターとレスポンダーの間で開くことができるセッションはいつでも 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="eebb2-309">1 つのセッション内のすべてのトランザクションがブロックとなり、前のトランザクションが完了するまで、新しいトランザクションを開始することはできません。</span><span class="sxs-lookup"><span data-stu-id="eebb2-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="eebb2-310">PIMA トランザクションは、コマンド フェーズ、オプションのデータ フェーズと応答フェーズの 3 つのフェーズで構成されています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="eebb2-311">データ フェーズが存在する場合は、一方向のみになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="eebb2-312">PIMA 操作のフローを決定するのは常にイニシエーターですが、レスポンダーはセッション中に発生した状態の変更を通知するために、イニシエーターに対するイベントを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="eebb2-313">次の図は、ホストと PIMA デバイス クラスの間のデータ オブジェクトの転送を示しています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![PIMA トランザクション](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="eebb2-315">PIMA デバイス クラスの初期化</span><span class="sxs-lookup"><span data-stu-id="eebb2-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="eebb2-316">PIMA デバイス クラスには、初期化中、アプリケーションによって提供されたパラメーターがいくつか必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="eebb2-317">次のパラメーターは、デバイスとストレージの情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="eebb2-318">また、PIMA クラスにはアプリケーションへのコールバック登録が必要で、これによって特定のイベントをアプリケーションに通知したり、ローカル メディアとの間でデータを取得/保存したりします。</span><span class="sxs-lookup"><span data-stu-id="eebb2-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="eebb2-319">コールバックを次に示します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="eebb2-320">次の例は、PIMA のクライアント側を初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="eebb2-321">この例は、PIMA に対するクライアントとして Pictbridge を使用します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="eebb2-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="eebb2-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="eebb2-323">オブジェクトの追加と、ホストへのイベントの送信</span><span class="sxs-lookup"><span data-stu-id="eebb2-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-324">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="eebb2-325">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-325">Description</span></span>

<span data-ttu-id="eebb2-326">この関数は、PIMA クラスがオブジェクトを追加し、ホストに通知する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-327">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-327">Parameters</span></span>

- <span data-ttu-id="eebb2-328">**pima**: pima クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="eebb2-329">**object_handle**: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="eebb2-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-330">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="eebb2-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="eebb2-332">アプリケーションからのオブジェクト番号の取得</span><span class="sxs-lookup"><span data-stu-id="eebb2-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-333">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="eebb2-334">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-334">Description</span></span>

<span data-ttu-id="eebb2-335">この関数は、PIMA クラスがローカル システム内のオブジェクト数を取得し、ホストに送り返す必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-336">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-336">Parameters</span></span>

- <span data-ttu-id="eebb2-337">**pima**: pima クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="eebb2-338">**object_number**: 返されるオブジェクト数のアドレス</span><span class="sxs-lookup"><span data-stu-id="eebb2-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-339">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="eebb2-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="eebb2-341">オブジェクト ハンドル配列を返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-342">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="eebb2-343">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-343">Description</span></span>

<span data-ttu-id="eebb2-344">この関数は、PIMA クラスがローカル システム内のオブジェクト ハンドル配列を取得し、ホストに送り返す必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-345">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-345">Parameters</span></span>

- <span data-ttu-id="eebb2-346">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="eebb2-347">**object_handles_format_code**: ハンドルの表示形式コード</span><span class="sxs-lookup"><span data-stu-id="eebb2-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="eebb2-348">**object_handles_association**: オブジェクトの関連付けコード</span><span class="sxs-lookup"><span data-stu-id="eebb2-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="eebb2-349">**object_handle_array**: ハンドルを格納する場所のアドレス</span><span class="sxs-lookup"><span data-stu-id="eebb2-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="eebb2-350">**object_handles_max_number**: 配列内のハンドルの最大数</span><span class="sxs-lookup"><span data-stu-id="eebb2-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-351">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="eebb2-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="eebb2-353">オブジェクト情報を返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-354">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="eebb2-355">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-355">Description</span></span>

<span data-ttu-id="eebb2-356">この関数は、PIMA クラスがローカル システム内のオブジェクト ハンドル配列を取得し、ホストに送り返す必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-357">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-357">Parameters</span></span>

- <span data-ttu-id="eebb2-358">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="eebb2-359">**object_handles**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="eebb2-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="eebb2-360">**object**: オブジェクト ポインターのアドレス</span><span class="sxs-lookup"><span data-stu-id="eebb2-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-361">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="eebb2-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="eebb2-363">オブジェクト データを返します</span><span class="sxs-lookup"><span data-stu-id="eebb2-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-364">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="eebb2-365">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-365">Description</span></span>

<span data-ttu-id="eebb2-366">この関数は、PIMA クラスがローカル システム内のオブジェクト データを取得し、ホストに送り返す必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-367">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-367">Parameters</span></span>

- <span data-ttu-id="eebb2-368">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="eebb2-369">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="eebb2-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="eebb2-370">**object_buffer**: オブジェクト バッファー アドレス</span><span class="sxs-lookup"><span data-stu-id="eebb2-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="eebb2-371">**object_length_requested**: クライアントからアプリケーションに対して要求されたオブジェク トデータの長さ</span><span class="sxs-lookup"><span data-stu-id="eebb2-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="eebb2-372">**object_actual_length**: アプリケーションによって返されたオブジェクト データの長さ</span><span class="sxs-lookup"><span data-stu-id="eebb2-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-373">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="eebb2-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="eebb2-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="eebb2-375">ホストがオブジェクト情報を送信します</span><span class="sxs-lookup"><span data-stu-id="eebb2-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-376">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="eebb2-377">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-377">Description</span></span>

<span data-ttu-id="eebb2-378">この関数は、PIMA クラスが、今後のストレージ用にローカル システム内のオブジェクト情報を受け取る必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-379">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-379">Parameters</span></span>

- <span data-ttu-id="eebb2-380">**pima**: pima クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="eebb2-381">**object**: オブジェクトへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="eebb2-382">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="eebb2-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-383">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="eebb2-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="eebb2-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="eebb2-385">ホストがオブジェクト データを送信します</span><span class="sxs-lookup"><span data-stu-id="eebb2-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-386">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="eebb2-387">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-387">Description</span></span>

<span data-ttu-id="eebb2-388">この関数は、PIMA クラスが、ストレージ用にローカル システム内のオブジェクト データを受け取る必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-389">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-389">Parameters</span></span>

- <span data-ttu-id="eebb2-390">**pima**: pima クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="eebb2-391">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="eebb2-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="eebb2-392">**phase**: 転送のフェーズ (アクティブまたは完了)</span><span class="sxs-lookup"><span data-stu-id="eebb2-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="eebb2-393">**object_buffer**: オブジェクト バッファー アドレス</span><span class="sxs-lookup"><span data-stu-id="eebb2-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="eebb2-394">**object_offset**: データのアドレス</span><span class="sxs-lookup"><span data-stu-id="eebb2-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="eebb2-395">**object_length**: アプリケーションによって送信されたオブジェクト データの長さ</span><span class="sxs-lookup"><span data-stu-id="eebb2-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-396">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="eebb2-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="eebb2-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="eebb2-398">ローカル オブジェクトを削除します</span><span class="sxs-lookup"><span data-stu-id="eebb2-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-399">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="eebb2-400">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-400">Description</span></span>

<span data-ttu-id="eebb2-401">この関数は、PIMA クラスがローカル ストレージ上のオブジェクトを削除する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-402">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-402">Parameters</span></span>

- <span data-ttu-id="eebb2-403">**pima**: pima クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="eebb2-404">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="eebb2-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-405">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="eebb2-406">USB デバイス Audio クラス</span><span class="sxs-lookup"><span data-stu-id="eebb2-406">USB Device Audio Class</span></span>

<span data-ttu-id="eebb2-407">USB デバイス Audio クラスにより、USB ホスト システムが、オーディオ デバイスとしてデバイスと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="eebb2-408">このクラスは、USB 標準および USB Audio クラス 1.0 または2.0 標準に基づいています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="eebb2-409">USB Audio 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="eebb2-410">Audio 2.0 スピーカーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="eebb2-411">Audio クラスは、複合デバイス フレームワークを使用して、インターフェイス (コントロールとストリーミング) をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="eebb2-412">そのため、デバイス記述子を定義するときは注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="eebb2-413">USBX は IAD 記述子を使用して、インターフェイスのバインド方法を内部で認識します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="eebb2-414">IAD 記述子は、インターフェイスの前に宣言する必要があり (AudioControl インターフェイスの後に 1 つ以上の AudioStreaming インターフェイスが続きます)、Audio クラスの最初のインターフェイス (AudioControl インターフェイス) と、アタッチされているインターフェイスの数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="eebb2-415">Audio クラスの動作は、デバイスがオーディオを送信するか受信するかによって異なりますが、どちらの場合も、オーディオ フレーム バッファーの格納に FIFO が使用されます。デバイスがホストにオーディオを送信している場合は、アプリケーションが、オーディオ フレーム バッファーを FIFO に追加し、これが後で USBX によってホストに送信されます。デバイスがホストからオーディオを受信している場合は、USBX が、ホストから受信したオーディオ フレーム バッファーを FIFO に追加し、これが後でアプリケーションによって読み取られます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="eebb2-416">各オーディオ ストリームには独自の FIFO があり、各オーディオ フレーム バッファーは複数のサンプルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="eebb2-417">Audio クラスの初期化には、次の部分が必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="eebb2-418">Audio クラスには、次のストリーミング パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="eebb2-419">Audio クラスには、次の関数パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="eebb2-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="eebb2-420">アプリケーションで定義された制御要求コールバック (前の例で設定された ***ux_device_class_audio_control_process***) は、スタックがホストから制御要求を受け取ったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="eebb2-421">要求が受け入れられ、処理 (確認または停止) された場合、コールバックは成功を返す必要があります。それ以外の場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="eebb2-422">クラス固有の制御要求プロセスは、アプリケーション定義のコールバックとして定義されます。これは、制御要求が USB Audio バージョンによって大きく異なり、要求プロセスの大部分がデバイス フレームワークに関連するためです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="eebb2-423">アプリケーションは、デバイスを動作させるために、要求を正しく処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="eebb2-424">オーディオ デバイスの場合、ボリューム、ミュート、およびサンプリング頻度は一般的な制御要求であるため、さまざまな USB オーディオ バージョン用の内部定義されたシンプルなコールバックが、アプリケーションの後のセクション内で使用されるように導入されています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="eebb2-425">詳細については、***ux_device_class_audio10_control_process** _ および _ *_ux_device_class_audio_control_request_** をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eebb2-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="eebb2-426">Audio デバイスのデバイス フレームワーク内で、PID/VID はデバイス記述子に格納されます (上記の宣言されたデバイス記述子を参照)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="eebb2-427">USB ホスト システムによって USB Audio デバイスが検出され、Audio クラスがマウントされている場合、デバイスは、任意のオーディオ プレーヤーまたはレコーダー (フレームワークによって異なります) と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="eebb2-428">詳細については、「ホスト オペレーティング システム」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eebb2-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="eebb2-429">Audio クラス API は以下のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="eebb2-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="eebb2-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="eebb2-431">Audio 関数のデータを読み取るためのスレッド エントリ。</span><span class="sxs-lookup"><span data-stu-id="eebb2-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-432">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="eebb2-433">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-433">Description</span></span>

<span data-ttu-id="eebb2-434">この関数は、ホストからのオーディオの読み取りが必要な場合に、オーディオ ストリーム初期化パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="eebb2-435">内部的には、スレッドがこの関数によってエントリ関数として作成され、スレッド自体は、Audio 関数内のアイソクロナス OUT エンドポイントを介してオーディオ データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-436">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-436">Parameters</span></span>

- <span data-ttu-id="eebb2-437">**audio_stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-438">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="eebb2-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="eebb2-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="eebb2-440">Audio 関数のデータ書き込むためのスレッド エントリ</span><span class="sxs-lookup"><span data-stu-id="eebb2-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-441">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="eebb2-442">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-442">Description</span></span>

<span data-ttu-id="eebb2-443">この関数は、ホストへのオーディオの書き込みが必要な場合に、オーディオ ストリーム初期化パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="eebb2-444">内部的には、スレッドがこの関数によってエントリ関数として作成され、スレッド自体は、Audio 関数内のアイソクロナス IN エンドポイントを介してオーディオ データを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-445">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-445">Parameters</span></span>

- <span data-ttu-id="eebb2-446">**audio_stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-447">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="eebb2-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="eebb2-449">Audio 関数の特定のストリーム インスタンスを取得します</span><span class="sxs-lookup"><span data-stu-id="eebb2-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-450">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="eebb2-451">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-451">Description</span></span>

<span data-ttu-id="eebb2-452">この関数は、Audio クラスのストリームインスタンスを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-453">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-453">Parameters</span></span>

- <span data-ttu-id="eebb2-454">**audio**: オーディオ インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="eebb2-455">**stream_index**: 0 に基づくストリーム インスタンス インデックス</span><span class="sxs-lookup"><span data-stu-id="eebb2-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="eebb2-456">**stream**: オーディオ ストリーム インスタンス ポインターを格納するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="eebb2-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-457">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-457">Return Value</span></span>

- <span data-ttu-id="eebb2-458">**UX_SUCCESS** (0x00) この操作は成功しました</span><span class="sxs-lookup"><span data-stu-id="eebb2-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="eebb2-459">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-460">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="eebb2-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="eebb2-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="eebb2-462">オーディオ ストリームのオーディオ データの受信を開始します</span><span class="sxs-lookup"><span data-stu-id="eebb2-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-463">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="eebb2-464">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-464">Description</span></span>

<span data-ttu-id="eebb2-465">この関数は、オーディオ ストリーム内でのオーディオ データの読み取りを開始するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-466">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-466">Parameters</span></span>

- <span data-ttu-id="eebb2-467">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-468">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-468">Return Value</span></span>

- <span data-ttu-id="eebb2-469">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="eebb2-472">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-473">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="eebb2-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="eebb2-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="eebb2-475">オーディオ ストリームから 8 ビットのサンプルを読み取ります</span><span class="sxs-lookup"><span data-stu-id="eebb2-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-476">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="eebb2-477">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-477">Description</span></span>

<span data-ttu-id="eebb2-478">この関数は、指定したストリームから 8 ビットのオーディオ サンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="eebb2-479">具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="eebb2-480">オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-481">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-481">Parameters</span></span>

- <span data-ttu-id="eebb2-482">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-483">**buffer**: サンプル バイトが保存されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-484">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-484">Return Value</span></span>

- <span data-ttu-id="eebb2-485">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-488">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-489">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="eebb2-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="eebb2-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="eebb2-491">オーディオ ストリームから 16 ビットのサンプルを読み取ります</span><span class="sxs-lookup"><span data-stu-id="eebb2-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-492">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="eebb2-493">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-493">Description</span></span>

<span data-ttu-id="eebb2-494">この関数は、指定したストリームから 16 ビットのオーディオ サンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="eebb2-495">具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="eebb2-496">オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-497">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-497">Parameters</span></span>

- <span data-ttu-id="eebb2-498">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-499">**buffer**: 16 ビットのサンプルが保存されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-500">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-500">Return Value</span></span>

- <span data-ttu-id="eebb2-501">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-504">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-505">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="eebb2-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="eebb2-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="eebb2-507">オーディオ ストリームから 24 ビットのサンプルを読み取ります</span><span class="sxs-lookup"><span data-stu-id="eebb2-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-508">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="eebb2-509">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-509">Description</span></span>

<span data-ttu-id="eebb2-510">この関数は、指定したストリームから 24 ビットのオーディオ サンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="eebb2-511">具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="eebb2-512">オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-513">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-513">Parameters</span></span>

- <span data-ttu-id="eebb2-514">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-515">**buffer**: 3 バイトのサンプルが保存されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-516">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-516">Return Value</span></span>

- <span data-ttu-id="eebb2-517">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-520">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-521">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="eebb2-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="eebb2-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="eebb2-523">オーディオ ストリームから 32 ビットのサンプルを読み取ります</span><span class="sxs-lookup"><span data-stu-id="eebb2-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-524">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="eebb2-525">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-525">Description</span></span>

<span data-ttu-id="eebb2-526">この関数は、指定したストリームから 32 ビットのオーディオ サンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="eebb2-527">具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="eebb2-528">オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-529">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-529">Parameters</span></span>

- <span data-ttu-id="eebb2-530">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-531">**buffer**: 4 バイトのデータが保存されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-532">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-532">Return Value</span></span>

- <span data-ttu-id="eebb2-533">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-536">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-537">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="eebb2-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="eebb2-539">オーディオ ストリーム内のオーディオ フレームにアクセスします</span><span class="sxs-lookup"><span data-stu-id="eebb2-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-540">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="eebb2-541">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-541">Description</span></span>

<span data-ttu-id="eebb2-542">この関数は、指定したストリームの FIFO 内の最初のオーディオ フレーム バッファーとその長さを返します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="eebb2-543">アプリケーションによるデータの処理が完了したら、ux_device_class_audio_read_frame_free を使用して、FIFO 内のフレーム バッファーを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-544">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-544">Parameters</span></span>

- <span data-ttu-id="eebb2-545">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-546">**frame_data**: データ ポインターを返すデータ ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="eebb2-547">**frame_length**: フレームの長さがバイト単位で保存されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-548">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-548">Return Value</span></span>

- <span data-ttu-id="eebb2-549">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-552">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-553">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="eebb2-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="eebb2-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="eebb2-555">オーディオ ストリーム内のオーディオ フレーム バッファーを解放します</span><span class="sxs-lookup"><span data-stu-id="eebb2-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-556">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="eebb2-557">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-557">Description</span></span>

<span data-ttu-id="eebb2-558">この関数は、ホストからデータを受信できるように、指定したストリームの FIFO の前にあるオーディオ フレーム バッファーを解放します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-559">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-559">Parameters</span></span>

- <span data-ttu-id="eebb2-560">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-561">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-561">Return Value</span></span>

- <span data-ttu-id="eebb2-562">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-565">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-566">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="eebb2-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="eebb2-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="eebb2-568">オーディオ ストリームのオーディオ データ転送を開始します</span><span class="sxs-lookup"><span data-stu-id="eebb2-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-569">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="eebb2-570">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-570">Description</span></span>

<span data-ttu-id="eebb2-571">この関数は、Audio クラス内での FIFO に書き込まれたオーディオ データの送信を開始するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-572">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-572">Parameters</span></span>

- <span data-ttu-id="eebb2-573">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-574">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-574">Return Value</span></span>

- <span data-ttu-id="eebb2-575">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="eebb2-578">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-579">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="eebb2-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="eebb2-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="eebb2-581">オーディオ フレームをオーディオ ストリームに書き込みます</span><span class="sxs-lookup"><span data-stu-id="eebb2-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-582">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="eebb2-583">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-583">Description</span></span>

<span data-ttu-id="eebb2-584">この関数は、フレームをオーディオ ストリームの FIFO に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="eebb2-585">フレーム データは、ホストに送信できるように、FIFO 内の使用可能なバッファーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-586">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-586">Parameters</span></span>

- <span data-ttu-id="eebb2-587">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-588">**frame**: フレーム データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="eebb2-589">**frame_length**: フレームの長さ (バイト数)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-590">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-590">Return Value</span></span>

- <span data-ttu-id="eebb2-591">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="eebb2-594">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-595">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="eebb2-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="eebb2-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="eebb2-597">オーディオ ストリーム内のオーディオ フレームにアクセスします</span><span class="sxs-lookup"><span data-stu-id="eebb2-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-598">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="eebb2-599">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-599">Description</span></span>

<span data-ttu-id="eebb2-600">この関数は、FIFO の最後のオーディオ フレーム バッファーのアドレスを取得します。また、オーディオ フレーム バッファーの長さも取得します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="eebb2-601">アプリケーションによるオーディオ フレーム バッファーへの必要なデータ入力が完了したら、***ux_device_class_audio_write_frame_commit*** を使用して、フレーム バッファーを FIFO に追加/コミットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eebb2-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-602">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-602">Parameters</span></span>

- <span data-ttu-id="eebb2-603">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-604">**frame_data**: フレーム データ ポインターを返すフレーム データ ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="eebb2-605">**frame_length**: フレームの長さがバイト単位で保存されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-606">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-606">Return Value</span></span>

- <span data-ttu-id="eebb2-607">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="eebb2-610">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-611">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="eebb2-612">ux_device_class_audio_write_frame_commit</span><span class="sxs-lookup"><span data-stu-id="eebb2-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="eebb2-613">オーディオ ストリーム内のオーディオ フレーム バッファーをコミットします。</span><span class="sxs-lookup"><span data-stu-id="eebb2-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-614">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="eebb2-615">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-615">Description</span></span>

<span data-ttu-id="eebb2-616">この関数は、最後のオーディオ フレーム バッファーを FIFO に追加/コミットし、バッファーをホストに転送できるようにします。最後のオーディオ フレーム バッファーは、ux_device_class_write_frame_get によって入力されている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="eebb2-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-617">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-617">Parameters</span></span>

- <span data-ttu-id="eebb2-618">**stream**: オーディオ ストリーム インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="eebb2-619">**length**: バッファー内で準備ができているバイト数。</span><span class="sxs-lookup"><span data-stu-id="eebb2-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-620">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-620">Return Value</span></span>

- <span data-ttu-id="eebb2-621">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。</span><span class="sxs-lookup"><span data-stu-id="eebb2-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="eebb2-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="eebb2-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="eebb2-624">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-625">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="eebb2-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="eebb2-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="eebb2-627">USB Audio 1.0 制御要求を処理します</span><span class="sxs-lookup"><span data-stu-id="eebb2-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-628">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="eebb2-629">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-629">Description</span></span>

<span data-ttu-id="eebb2-630">この関数は、USB Audio 1.0 固有の種類を使用して、制御エンドポイント上のホストによって送信された基本要求を管理します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="eebb2-631">音量およびミュート要求の Audio 1.0 機能が、関数内で処理されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="eebb2-632">要求の処理中、最後のパラメーター (group) によって渡された事前定義済みデータが、要求に応答し、制御の変更を格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-633">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-633">Parameters</span></span>

- <span data-ttu-id="eebb2-634">**audio**: オーディオ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="eebb2-635">**transfer**: 転送要求インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="eebb2-636">**group**: 要求プロセスのデータ グループ。</span><span class="sxs-lookup"><span data-stu-id="eebb2-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-637">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-637">Return Value</span></span>

- <span data-ttu-id="eebb2-638">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-639">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-640">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="eebb2-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="eebb2-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="eebb2-642">USB Audio 1.0 制御要求を処理します</span><span class="sxs-lookup"><span data-stu-id="eebb2-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="eebb2-643">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="eebb2-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="eebb2-644">説明</span><span class="sxs-lookup"><span data-stu-id="eebb2-644">Description</span></span>

<span data-ttu-id="eebb2-645">この関数は、USB Audio 2.0 固有の種類を使用して、制御エンドポイント上のホストによって送信された基本要求を管理します。</span><span class="sxs-lookup"><span data-stu-id="eebb2-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="eebb2-646">Audio 2.0 サンプリング レート (単一の固定周波数を想定) と、音量およびミュート要求の機能が、関数内で処理されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="eebb2-647">要求の処理中、最後のパラメーター (group) によって渡された事前定義済みデータが、要求に応答し、制御の変更を格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eebb2-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="eebb2-648">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eebb2-648">Parameters</span></span>

- <span data-ttu-id="eebb2-649">**audio**: オーディオ インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="eebb2-650">**transfer**: 転送要求インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eebb2-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="eebb2-651">**group**: 要求プロセスのデータ グループ。</span><span class="sxs-lookup"><span data-stu-id="eebb2-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="eebb2-652">戻り値</span><span class="sxs-lookup"><span data-stu-id="eebb2-652">Return Value</span></span>

- <span data-ttu-id="eebb2-653">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="eebb2-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eebb2-654">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="eebb2-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="eebb2-655">例</span><span class="sxs-lookup"><span data-stu-id="eebb2-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
