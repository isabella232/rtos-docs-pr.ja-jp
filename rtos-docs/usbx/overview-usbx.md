---
title: Azure RTOS USBX を理解する
description: Azure RTOS USBX は、ハイパフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。Azure RTOS USBX は Azure RTOS ThreadX と完全に統合されており、すべての Azure RTOS ThreadX でサポートされているプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3c214a49f7dd1af20c20f07412fb072dd785b16f
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754830"
---
# <a name="overview-of-azure-rtos-usbx"></a><span data-ttu-id="b7956-103">Azure RTOS USBX の概要</span><span class="sxs-lookup"><span data-stu-id="b7956-103">Overview of Azure RTOS USBX</span></span>

<span data-ttu-id="b7956-104">Azure RTOS USBXは、ハイ パフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。</span><span class="sxs-lookup"><span data-stu-id="b7956-104">Azure RTOS USBX is a high-performance USB host, device, and on-the-go (OTG) embedded stack.</span></span> <span data-ttu-id="b7956-105">Azure RTOS USBX は Azure RTOS ThreadX と完全に統合されており、ThreadX でサポートされているすべてのプロセッサで利用できます。</span><span class="sxs-lookup"><span data-stu-id="b7956-105">Azure RTOS USBX is fully integrated with Azure RTOS ThreadX and available for all ThreadX–supported processors.</span></span> <span data-ttu-id="b7956-106">ThreadX と同様に、Azure RTOS USBX は、小さいフットプリントでハイパフォーマンスを実現するように設計されているため、USB デバイスとのインターフェイスを必要とする深い埋め込み型のアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="b7956-106">Like ThreadX, Azure RTOS USBX is designed to have a small footprint and high performance, making it ideal for deeply embedded applications that require an interface with USB devices.</span></span>

## <a name="host-device-otg--extensive-class-support"></a><span data-ttu-id="b7956-107">ホスト、デバイス、OTG、および広範なクラスのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-107">Host, Device, OTG & Extensive Class Support</span></span>

<span data-ttu-id="b7956-108">Azure RTOS USBX ホストまたはデバイス埋め込み USB プロトコル スタックは、リアルタイムの深い埋め込み型 IoT アプリケーション用に設計された産業用埋め込み USB ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="b7956-108">Azure RTOS USBX Host/Device embedded USB protocol stack is an Industrial Grade embedded USB solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="b7956-109">Azure RTOS USBX は、ホスト、デバイス、および OTG のサポートに加えて、広範なクラスのサポートを提供しています。</span><span class="sxs-lookup"><span data-stu-id="b7956-109">Azure RTOS USBX provides host, device, and OTG support, as well as extensive class support.</span></span> <span data-ttu-id="b7956-110">Azure RTOS USBX は、ThreadX Real-Time オペレーティング システム、Azure RTOS FileX 埋め込み FAT 互換ファイル システム、Azure RTOS NetX、および Azure RTOS NetX Duo 埋め込み TCP/IP スタックと完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="b7956-110">Azure RTOS USBX is fully integrated with ThreadX Real-Time Operating System, Azure RTOS FileX embedded FAT-compatible file system, Azure RTOS NetX, and Azure RTOS NetX Duo embedded TCP/IP stacks.</span></span> <span data-ttu-id="b7956-111">これらすべてを非常に小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS USBX は、USB 接続を必要とする最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="b7956-111">All of this, combined with an extremely small footprint, fast execution and superior ease-of-use, make Azure RTOS USBX the ideal choice for the most demanding embedded IoT applications requiring USB connectivity.</span></span>

### <a name="usbx-memory-footprint"></a><span data-ttu-id="b7956-112">USBX のメモリ占有領域</span><span class="sxs-lookup"><span data-stu-id="b7956-112">USBX memory footprint</span></span>

<span data-ttu-id="b7956-113">Azure RTOS USBX では、Azure RTOS USBX デバイスの CDC/ACM サポートのために、10.5 KB のフラッシュと 5.1 KB の RAM という非常に小さなフットプリントを実現しています。</span><span class="sxs-lookup"><span data-stu-id="b7956-113">Azure RTOS USBX has a remarkably small minimal footprint of 10.5 KB of FLASH and 5.1 KB RAM for Azure RTOS USBX Device CDC/ACM support.</span></span> <span data-ttu-id="b7956-114">Azure RTOS USBX ホストには、CDC/ACM のサポートのために最低 18 KB のフラッシュと 25 KB の RAM が必要です。</span><span class="sxs-lookup"><span data-stu-id="b7956-114">Azure RTOS USBX Host requires a minimum of 18 KB of FLASH and 25 KB of RAM for CDC/ACM support.</span></span>

<span data-ttu-id="b7956-115">TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7956-115">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="b7956-116">Azure RTOS USBX の RAM の使用率は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた分になります。</span><span class="sxs-lookup"><span data-stu-id="b7956-116">Azure RTOS USBX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span>

<span data-ttu-id="b7956-117">ThreadX と同様に、Azure RTOS USBX のサイズは、アプリケーションで実際に使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="b7956-117">Like ThreadX, the size of Azure RTOS USBX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="b7956-118">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="b7956-118">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="usb-interoperability-verification"></a><span data-ttu-id="b7956-119">USB 相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="b7956-119">USB Interoperability verification</span></span>

<span data-ttu-id="b7956-120">Azure RTOS USBX デバイス スタックは、USB IF 標準テスト ツール USBCV で厳格にテストされ、USB 仕様に完全に準拠し、さまざまなホスト システムと相互運用性があることが確認されています。</span><span class="sxs-lookup"><span data-stu-id="b7956-120">Azure RTOS USBX Device Stack has been rigorously tested with the USB IF standard testing tool USBCV to ensure full compliance with the USB specifications and interoperability with different host systems.</span></span>
<span data-ttu-id="b7956-121">さらに、Azure RTOS USBX OTG スタックは、台湾の独立テスト ラボ Allion によって検証および認定されています。</span><span class="sxs-lookup"><span data-stu-id="b7956-121">In addition, Azure RTOS USBX OTG stack has been verified and certified by the independent test lab Allion in Taiwan.</span></span>

### <a name="usb-host-controller-support"></a><span data-ttu-id="b7956-122">USB ホスト コントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-122">USB Host controller support</span></span>

<span data-ttu-id="b7956-123">Azure RTOS USBX は、OHCI や EHCI などの主要な USB 標準をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-123">Azure RTOS USBX supports major USB standards like OHCI and EHCI.</span></span> <span data-ttu-id="b7956-124">さらに、Azure RTOS USBX は、Atmel、Microchip、Philips、Renesas、ST、TI、およびその他のベンダーの独自の USB ホスト コントローラーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-124">In addition, Azure RTOS USBX supports proprietary discrete USB host controllers from Atmel, Microchip, Philips, Renesas, ST, TI, and other vendors.</span></span> <span data-ttu-id="b7956-125">Azure RTOS USBX は、同じアプリケーション内の複数のホスト コントローラーもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-125">Azure RTOS USBX also supports multiple host controllers in the same application.</span></span>
<span data-ttu-id="b7956-126">USB デバイス コントローラーのサポート。Azure RTOS USBX は、Analog Devices、Atmel、Microchip、NXP、Philips、Renesas、ST、TI、およびその他のベンダーの人気のある USB デバイス コントローラーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-126">USB Device controller support Azure RTOS USBX supports popular USB device controllers from Analog Devices, Atmel, Microchip, NXP, Philips, Renesas, ST, TI, and other vendors.</span></span>

### <a name="extensive-host-class-support"></a><span data-ttu-id="b7956-127">広範なホスト クラスのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-127">Extensive Host Class support</span></span>

<span data-ttu-id="b7956-128">Azure RTOS USBX ホストは、ASIX、AUDIO、CDC/ACM、CDC/ECM、GSER、HID (キーボード、マウス、およびリモート コントロール)、HUB、PIMA (PTP/MTP)、PRINTER、PROLIFIC、STORAGE などの、最も一般的なクラスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-128">Azure RTOS USBX Host provides support for most popular classes, including ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (keyboard, mouse, and remote control), HUB, PIMA (PTP/MTP), PRINTER, PROLIFIC, and STORAGE.</span></span>

### <a name="extensive-usb-device-class-support"></a><span data-ttu-id="b7956-129">広範な USB デバイス クラスのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-129">Extensive USB Device Class support</span></span>

<span data-ttu-id="b7956-130">Azure RTOS USBX デバイスは、CDC/ACM、CDC/ECM、DFU、HID、PIMA (PTP/MTP) (w/MTP)、RNDIS、STORAGE などの最も一般的なクラスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-130">Azure RTOS USBX Device provides support for most popular classes, including CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS, and STORAGE.</span></span> <span data-ttu-id="b7956-131">カスタム クラスのサポートも利用できます。</span><span class="sxs-lookup"><span data-stu-id="b7956-131">Support for custom classes is also available.</span></span>

### <a name="pictbridge-support"></a><span data-ttu-id="b7956-132">Pictbridge のサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-132">Pictbridge support</span></span>

<span data-ttu-id="b7956-133">Azure RTOS USBX では、ホストとデバイスの両方で完全な Pictbridge 実装がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b7956-133">Azure RTOS USBX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="b7956-134">Pictbridge は、両方の側の Azure RTOS USBX PIMA (PTP/MTP) クラスの上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="b7956-134">Pictbridge sits on top of Azure RTOS USBX PIMA (PTP/MTP) class on both sides.</span></span> <span data-ttu-id="b7956-135">PictBridge 標準では、PC を使用せずに、デジタル スチル カメラまたはスマートフォンを直接プリンターに接続できるので、特定の Pictbridge 対応プリンターに直接印刷できます。</span><span class="sxs-lookup"><span data-stu-id="b7956-135">The PictBridge standard allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span> <span data-ttu-id="b7956-136">カメラまたはスマートフォンがプリンターに接続されている場合、プリンターは USB ホストであり、カメラは USB デバイスです。</span><span class="sxs-lookup"><span data-stu-id="b7956-136">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="b7956-137">ただし、Pictbridge では、カメラはホストとして表示され、コマンドはカメラから実行されます。</span><span class="sxs-lookup"><span data-stu-id="b7956-137">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="b7956-138">カメラはストレージ サーバーであり、プリンターはストレージ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="b7956-138">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="b7956-139">カメラはプリント クライアントであり、プリンターはもちろんプリント サーバーです。</span><span class="sxs-lookup"><span data-stu-id="b7956-139">The camera is the print client and the printer is of course the print server.</span></span> <span data-ttu-id="b7956-140">Pictbridge は、トランスポート層として USB を使用しますが、通信プロトコルとしては PTP (Picture Transfer Protocol) に依存します。</span><span class="sxs-lookup"><span data-stu-id="b7956-140">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

### <a name="custom-class-support"></a><span data-ttu-id="b7956-141">カスタム クラスのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-141">Custom class support</span></span>

<span data-ttu-id="b7956-142">Azure RTOS USBX ホストとデバイスはカスタム クラスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b7956-142">Azure RTOS USBX Host and Device support custom classes.</span></span> <span data-ttu-id="b7956-143">カスタム クラスの例は、Azure RTOS USBX ディストリビューションに用意されています。</span><span class="sxs-lookup"><span data-stu-id="b7956-143">An example custom class is provided in the Azure RTOS USBX distribution.</span></span> <span data-ttu-id="b7956-144">この単純なデータ ポンプ クラスは DPUMP と呼ばれ、カスタム アプリケーション クラスのモデルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7956-144">This simple data pump class is called DPUMP and can be used as a model for custom application classes.</span></span>
<span data-ttu-id="b7956-145">高度なテクノロジである Azure RTOS USBX ホストとデバイスはカスタム クラスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b7956-145">Advanced technology Azure RTOS USBX Host and Device support custom classes.</span></span> <span data-ttu-id="b7956-146">カスタム クラスの例は、Azure RTOS USBX ディストリビューションに用意されています。</span><span class="sxs-lookup"><span data-stu-id="b7956-146">An example custom class is provided in the Azure RTOS USBX distribution.</span></span> <span data-ttu-id="b7956-147">Azure RTOS USBX は、次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="b7956-147">Azure RTOS USBX is advanced technology that includes:</span></span>

* <span data-ttu-id="b7956-148">ホスト、デバイス、および OTG のサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-148">Host, Device, and OTG support</span></span>
* <span data-ttu-id="b7956-149">USB の低速、フルスピード、および高速のサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-149">USB low, full, and high-speed support</span></span>
* <span data-ttu-id="b7956-150">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-150">Automatic scaling</span></span>
* <span data-ttu-id="b7956-151">ThreadX、Azure RTOS FileX、Azure RTOS NetX との完全な統合</span><span class="sxs-lookup"><span data-stu-id="b7956-151">Fully integrated with ThreadX, Azure RTOS FileX, and Azure RTOS NetX</span></span>
* <span data-ttu-id="b7956-152">オプションのパフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="b7956-152">Optional performance metrics</span></span>
* <span data-ttu-id="b7956-153">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-153">Azure RTOS TraceX system analysis support</span></span>

## <a name="azure-rtos-usbx-apis"></a><span data-ttu-id="b7956-154">Azure RTOS USBX API</span><span class="sxs-lookup"><span data-stu-id="b7956-154">Azure RTOS USBX APIs</span></span>

### <a name="azure-rtos-usbx-host-api"></a><span data-ttu-id="b7956-155">Azure RTOS USBX Host API</span><span class="sxs-lookup"><span data-stu-id="b7956-155">Azure RTOS USBX Host API</span></span>

<span data-ttu-id="b7956-156">Azure RTOS USBX Host API は、名詞 - 動詞の名前付け規則に従った直感的で一貫性のある API です。</span><span class="sxs-lookup"><span data-stu-id="b7956-156">The Azure RTOS USBX Host API is an intuitive and consistent API, following a noun-verb naming convention.</span></span> <span data-ttu-id="b7956-157">すべての API の先頭を ux_host_\* にして USBX として簡単に識別できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-157">All APIs have leading ux_host_\* to easily identify as USBX.</span></span> <span data-ttu-id="b7956-158">ブロック API には、オプションのスレッド タイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="b7956-158">Any blocking APIs have optional thread timeout.</span></span>

* <span data-ttu-id="b7956-159">ASIX</span><span class="sxs-lookup"><span data-stu-id="b7956-159">ASIX</span></span>
    - <span data-ttu-id="b7956-160">最小 0.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-160">Minimal 0.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-161">自動スケーリング、Azure RTOS TraceX によるシステム レベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-161">Automatic scalingSystem-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-162">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_asix_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-162">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_asix_*\*</span></span>
* <span data-ttu-id="b7956-163">AUDIO</span><span class="sxs-lookup"><span data-stu-id="b7956-163">AUDIO</span></span>
    - <span data-ttu-id="b7956-164">最小 1.2 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-164">Minimal 1.2 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-165">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-165">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-166">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_audio_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-166">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_audio_*\*</span></span>
* <span data-ttu-id="b7956-167">CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="b7956-167">CDC/ACM</span></span>
    - <span data-ttu-id="b7956-168">最小 1.4 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-168">Minimal 1.4 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-169">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-169">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-170">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-170">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-171">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_cdc_acm_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-171">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_cdc_acm_*\*</span></span>
* <span data-ttu-id="b7956-172">HID</span><span class="sxs-lookup"><span data-stu-id="b7956-172">HID</span></span>
    - <span data-ttu-id="b7956-173">最小 0.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-173">Minimal 0.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-174">キーボード、マウス、およびリモート サポート</span><span class="sxs-lookup"><span data-stu-id="b7956-174">Keyboard, mouse, and remote support</span></span>
    - <span data-ttu-id="b7956-175">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-175">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-176">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-176">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-177">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_hid_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-177">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_hid_*\*</span></span> 
* <span data-ttu-id="b7956-178">ハブ</span><span class="sxs-lookup"><span data-stu-id="b7956-178">HUB</span></span>
    - <span data-ttu-id="b7956-179">最小 1.7 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-179">Minimal 1.7 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="b7956-180">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-180">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-181">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-181">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-182">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_hub_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-182">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_hub_*\*</span></span>
* <span data-ttu-id="b7956-183">PIMA (PTP/MTP)</span><span class="sxs-lookup"><span data-stu-id="b7956-183">PIMA (PTP/MTP)</span></span>
    - <span data-ttu-id="b7956-184">最小 0.9 KB のフラッシュ、8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-184">Minimal 0.9 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="b7956-185">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-185">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-186">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-186">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-187">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_pima_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-187">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_pima_*\*</span></span>
* <span data-ttu-id="b7956-188">PRINTER</span><span class="sxs-lookup"><span data-stu-id="b7956-188">PRINTER</span></span>
    - <span data-ttu-id="b7956-189">最小 0.8 KB のフラッシュ、8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-189">Minimal 0.8 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="b7956-190">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-190">Automatic scaling</span></span>
    -  <span data-ttu-id="b7956-191">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-191">System-level trace via Azure RTOS TraceX</span></span>
    -  <span data-ttu-id="b7956-192">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_printer_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-192">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_printer_*\*</span></span>
* <span data-ttu-id="b7956-193">PROLIFIC</span><span class="sxs-lookup"><span data-stu-id="b7956-193">PROLIFIC</span></span>
    - <span data-ttu-id="b7956-194">最小 1.5 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-194">Minimal 1.5 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-195">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-195">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-196">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-196">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-197">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_prolific_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-197">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_prolific_*\*</span></span>
* <span data-ttu-id="b7956-198">STORAG</span><span class="sxs-lookup"><span data-stu-id="b7956-198">STORAG</span></span>
    - <span data-ttu-id="b7956-199">最小 5.6 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-199">Minimal 5.6 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-200">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-200">Automatic scaling</span></span><br> <span data-ttu-id="b7956-201">Azure RTOS FileX との統合</span><span class="sxs-lookup"><span data-stu-id="b7956-201">Integrated with Azure RTOS FileX</span></span>
    - <span data-ttu-id="b7956-202">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-202">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-203">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_storage_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-203">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_storage_*\*</span></span>
* <span data-ttu-id="b7956-204">USB ホスト スタック</span><span class="sxs-lookup"><span data-stu-id="b7956-204">USB Host STACK</span></span>
    - <span data-ttu-id="b7956-205">多くのホスト コントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-205">Supports many host controllers</span></span>
    - <span data-ttu-id="b7956-206">最小 18 KB のフラッシュ、25 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-206">Minimal 18 KB FLASH, 25 KB RAM</span></span>
    - <span data-ttu-id="b7956-207">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-207">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-208">同じプラットフォーム上の複数のホスト コントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-208">Support for multiple host controllers on same platform</span></span>
    -  <span data-ttu-id="b7956-209">USB の低速、フルスピード、および高速のサポート</span><span class="sxs-lookup"><span data-stu-id="b7956-209">USB low, full, and high-speed support</span></span>
    -  <span data-ttu-id="b7956-210">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-210">System-level trace via Azure RTOS TraceX</span></span>
    -  <span data-ttu-id="b7956-211">直観的な Azure RTOS USBX Host API の形式: *ux_host_stack_*  \*</span><span class="sxs-lookup"><span data-stu-id="b7956-211">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_stack_* \*</span></span> 
* <span data-ttu-id="b7956-212">OHCI、EHCI、専用のホスト コントローラー</span><span class="sxs-lookup"><span data-stu-id="b7956-212">OHCI, EHCI, PROPRIETARY Host CONTROLLERS</span></span> 

### <a name="azure-rtos-usbx-device-api"></a><span data-ttu-id="b7956-213">Azure RTOS USBX Device API</span><span class="sxs-lookup"><span data-stu-id="b7956-213">Azure RTOS USBX Device API</span></span>

<span data-ttu-id="b7956-214">Azure RTOS USBX Device API は、名詞 - 動詞の名前付け規則に従った直感的で一貫性のある API です。</span><span class="sxs-lookup"><span data-stu-id="b7956-214">The Azure RTOS USBX Device API is an intuitive and consistent API following a noun-verb naming convention.</span></span> <span data-ttu-id="b7956-215">すべての API の先頭を ux_device_\* にして USBX として簡単に識別できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="b7956-215">All APIs have leading ux_device_\* to easily identify as USBX.</span></span> <span data-ttu-id="b7956-216">ブロック API にオプションのスレッド タイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="b7956-216">Blocking APIs have optional thread timeout.</span></span> <span data-ttu-id="b7956-217">詳細については、[Azure RTOS USBX ホスト ユーザー ガイド](usbx-host-stack-about.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7956-217">Please see [Azure RTOS USBX Host User Guide](usbx-host-stack-about.md) for more details.</span></span>

* <span data-ttu-id="b7956-218">CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="b7956-218">CDC/ACM</span></span>
    - <span data-ttu-id="b7956-219">最小 0.8 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-219">Minimal 0.8 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="b7956-220">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-220">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-221">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-221">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-222">直観的な Azure RTOS USBX Device API の形式: \*ux_device_class_cdc_acm_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b7956-222">Intuitive Azure RTOS USBX device APIs in this form: \*ux_device_class_cdc_acm_\*\*.</span></span>
* <span data-ttu-id="b7956-223">CDC/ECM</span><span class="sxs-lookup"><span data-stu-id="b7956-223">CDC/ECM</span></span>
    - <span data-ttu-id="b7956-224">最小 1.5 KB のフラッシュ、4 KB から 8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-224">Minimal 1.5 KB FLASH, 4 KB to 8 KB RAM</span></span>
    - <span data-ttu-id="b7956-225">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-225">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-226">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-226">System-level trace via Azure RTOS TraceX</span></span><br> <span data-ttu-id="b7956-227">直観的な Azure RTOS USBX Device API の形式: \*ux_device_class_cdc_ecm_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b7956-227">Intuitive Azure RTOS USBX device APIs in this form: \*ux_device_class_cdc_ecm_\*\*.</span></span>
* <span data-ttu-id="b7956-228">DFU</span><span class="sxs-lookup"><span data-stu-id="b7956-228">DFU</span></span>
    - <span data-ttu-id="b7956-229">最小 1.1 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-229">Minimal 1.1 KB FLASH, 2 KB RAM</span></span>
    -  <span data-ttu-id="b7956-230">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-230">Automatic scaling</span></span>
    -  <span data-ttu-id="b7956-231">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-231">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-232">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_dfu_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-232">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_dfu_*\*</span></span> 
* <span data-ttu-id="b7956-233">GSER</span><span class="sxs-lookup"><span data-stu-id="b7956-233">GSER</span></span>
    - <span data-ttu-id="b7956-234">最小 0.6 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-234">Minimal 0.6 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-235">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-235">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-236">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-236">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-237">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_gser_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-237">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_gser_*\*</span></span>
* <span data-ttu-id="b7956-238">HID</span><span class="sxs-lookup"><span data-stu-id="b7956-238">HID</span></span>
    - <span data-ttu-id="b7956-239">最小 0.9 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-239">Minimal 0.9 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="b7956-240">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-240">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-241">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-241">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-242">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_hid_* \* PIMA (PTP/MTP)</span><span class="sxs-lookup"><span data-stu-id="b7956-242">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_hid_*\* PIMA (PTP/MTP)</span></span>
    - <span data-ttu-id="b7956-243">最小 5.2 KB のフラッシュ、8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-243">Minimal 5.2 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="b7956-244">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-244">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-245">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-245">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-246">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_pima_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-246">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_pima_*\*</span></span> 
* <span data-ttu-id="b7956-247">記憶域</span><span class="sxs-lookup"><span data-stu-id="b7956-247">STORAGE</span></span>
    - <span data-ttu-id="b7956-248">最小 2.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-248">Minimal 2.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-249">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-249">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-250">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-250">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-251">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_storage_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-251">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_storage_*\*</span></span>
* <span data-ttu-id="b7956-252">RNDIS</span><span class="sxs-lookup"><span data-stu-id="b7956-252">RNDIS</span></span>
    - <span data-ttu-id="b7956-253">最小 2.3 KB のフラッシュ、4 KB から 8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-253">Minimal 2.3 KB FLASH, 4 KB to 8 KB RAM</span></span>
    - <span data-ttu-id="b7956-254">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-254">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-255">Azure RTOS NetX と Azure RTOS NetX DUO との統合</span><span class="sxs-lookup"><span data-stu-id="b7956-255">Integrated with Azure RTOS NetX and Azure RTOS NetX DUO</span></span>
    - <span data-ttu-id="b7956-256">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-256">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-257">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_rndls_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-257">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_rndls_*\*</span></span>
* <span data-ttu-id="b7956-258">Azure RTOS USBX デバイス スタック</span><span class="sxs-lookup"><span data-stu-id="b7956-258">Azure RTOS USBX Device STACK</span></span>
    - <span data-ttu-id="b7956-259">最小 2.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="b7956-259">Minimal 2.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="b7956-260">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="b7956-260">Automatic scaling</span></span>
    - <span data-ttu-id="b7956-261">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="b7956-261">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="b7956-262">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_storage_* \*</span><span class="sxs-lookup"><span data-stu-id="b7956-262">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_storage_*\*</span></span>
* <span data-ttu-id="b7956-263">専用のホスト コントローラー</span><span class="sxs-lookup"><span data-stu-id="b7956-263">PROPRIETARY Host CONTROLLERS</span></span>

## <a name="next-steps"></a><span data-ttu-id="b7956-264">次のステップ</span><span class="sxs-lookup"><span data-stu-id="b7956-264">Next steps</span></span>

<span data-ttu-id="b7956-265">[ホスト スタック ユーザー ガイド](usbx-host-stack-about.md)または[デバイス スタック ユーザー ガイド](usbx-device-stack-about.md)に関する記事に従って、Azure RTOS USBX ホストおよびデバイス スタックの使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="b7956-265">Start working with the Azure RTOS USBX Host and Device Stack by following our [Host Stack User Guide](usbx-host-stack-about.md) or [Device Stack User Guide](usbx-device-stack-about.md).</span></span>