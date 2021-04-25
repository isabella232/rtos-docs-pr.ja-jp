---
title: Azure RTOS USBX を理解する
description: Azure RTOS USBX は、ハイパフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。Azure RTOS USBX は Azure RTOS ThreadX と完全に統合されており、すべての Azure RTOS ThreadX でサポートされているプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 87eb6ee9f8733db3201280d377aa832b87131871
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813286"
---
# <a name="overview-of-azure-rtos-usbx"></a><span data-ttu-id="21c65-103">Azure RTOS USBX の概要</span><span class="sxs-lookup"><span data-stu-id="21c65-103">Overview of Azure RTOS USBX</span></span>

<span data-ttu-id="21c65-104">Azure RTOS USBXは、ハイ パフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。</span><span class="sxs-lookup"><span data-stu-id="21c65-104">Azure RTOS USBX is a high-performance USB host, device, and on-the-go (OTG) embedded stack.</span></span> <span data-ttu-id="21c65-105">Azure RTOS USBX は Azure RTOS ThreadX と完全に統合されており、ThreadX でサポートされているすべてのプロセッサで利用できます。</span><span class="sxs-lookup"><span data-stu-id="21c65-105">Azure RTOS USBX is fully integrated with Azure RTOS ThreadX and available for all ThreadX–supported processors.</span></span> <span data-ttu-id="21c65-106">ThreadX と同様に、Azure RTOS USBX は、小さいフットプリントでハイパフォーマンスを実現するように設計されているため、USB デバイスとのインターフェイスを必要とする深い埋め込み型のアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="21c65-106">Like ThreadX, Azure RTOS USBX is designed to have a small footprint and high performance, making it ideal for deeply embedded applications that require an interface with USB devices.</span></span>

## <a name="host-device-otg--extensive-class-support"></a><span data-ttu-id="21c65-107">ホスト、デバイス、OTG、および広範なクラスのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-107">Host, Device, OTG & Extensive Class Support</span></span>

<span data-ttu-id="21c65-108">Azure RTOS USBX ホストまたはデバイス埋め込み USB プロトコル スタックは、リアルタイムの深い埋め込み型 IoT アプリケーション用に設計された産業用埋め込み USB ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="21c65-108">Azure RTOS USBX Host/Device embedded USB protocol stack is an Industrial Grade embedded USB solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="21c65-109">Azure RTOS USBX は、ホスト、デバイス、および OTG のサポートに加えて、広範なクラスのサポートを提供しています。</span><span class="sxs-lookup"><span data-stu-id="21c65-109">Azure RTOS USBX provides host, device, and OTG support, as well as extensive class support.</span></span> <span data-ttu-id="21c65-110">Azure RTOS USBX は、ThreadX Real-Time オペレーティング システム、Azure RTOS FileX 埋め込み FAT 互換ファイル システム、Azure RTOS NetX、および Azure RTOS NetX Duo 埋め込み TCP/IP スタックと完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-110">Azure RTOS USBX is fully integrated with ThreadX Real-Time Operating System, Azure RTOS FileX embedded FAT-compatible file system, Azure RTOS NetX, and Azure RTOS NetX Duo embedded TCP/IP stacks.</span></span> <span data-ttu-id="21c65-111">これらすべてを非常に小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS USBX は、USB 接続を必要とする最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="21c65-111">All of this, combined with an extremely small footprint, fast execution and superior ease-of-use, make Azure RTOS USBX the ideal choice for the most demanding embedded IoT applications requiring USB connectivity.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="21c65-112">小さなフットプリント</span><span class="sxs-lookup"><span data-stu-id="21c65-112">Small-footprint</span></span>

<span data-ttu-id="21c65-113">Azure RTOS USBX では、Azure RTOS USBX デバイスの CDC/ACM サポートのために、10.5 KB のフラッシュと 5.1 KB の RAM という非常に小さなフットプリントを実現しています。</span><span class="sxs-lookup"><span data-stu-id="21c65-113">Azure RTOS USBX has a remarkably small minimal footprint of 10.5 KB of FLASH and 5.1 KB RAM for Azure RTOS USBX Device CDC/ACM support.</span></span> <span data-ttu-id="21c65-114">Azure RTOS USBX ホストには、CDC/ACM のサポートのために最低 18 KB のフラッシュと 25 KB の RAM が必要です。</span><span class="sxs-lookup"><span data-stu-id="21c65-114">Azure RTOS USBX Host requires a minimum of 18 KB of FLASH and 25 KB of RAM for CDC/ACM support.</span></span>

<span data-ttu-id="21c65-115">TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="21c65-115">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="21c65-116">Azure RTOS USBX の RAM の使用率は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた分になります。</span><span class="sxs-lookup"><span data-stu-id="21c65-116">Azure RTOS USBX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span>

<span data-ttu-id="21c65-117">ThreadX と同様に、Azure RTOS USBX のサイズは、アプリケーションで実際に使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="21c65-117">Like ThreadX, the size of Azure RTOS USBX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="21c65-118">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="21c65-118">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="21c65-119">高速実行</span><span class="sxs-lookup"><span data-stu-id="21c65-119">Fast execution</span></span>

<span data-ttu-id="21c65-120">Azure RTOS USBX は、速度を重視して設計されており、最小限の内部関数呼び出しのレイヤーを備え、キャッシュと DMA の使用率をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-120">Azure RTOS USBX is designed for speed and has minimal internal function call layering and support for cache and DMA utilization.</span></span> <span data-ttu-id="21c65-121">このように設計された一般的な考え方はすべて、Azure RTOS USBX が最高のパフォーマンスを実現するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="21c65-121">All of this and a general performance-oriented design philosophy helps Azure RTOS USBX achieve the fastest possible performance.</span></span>

### <a name="simple-easy-to-use"></a><span data-ttu-id="21c65-122">シンプルで優れた操作性</span><span class="sxs-lookup"><span data-stu-id="21c65-122">Simple, easy-to-use</span></span>

<span data-ttu-id="21c65-123">Azure RTOS USBX は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="21c65-123">Azure RTOS USBX is simple to use.</span></span> <span data-ttu-id="21c65-124">Azure RTOS USBX API は直感的で高機能です。</span><span class="sxs-lookup"><span data-stu-id="21c65-124">The Azure RTOS USBX API is both intuitive and highly functional.</span></span> <span data-ttu-id="21c65-125">API 名は、略語や、他のファイル システム製品で一般的な大幅に省略された名前ではなく、実際の言葉で構成されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-125">The API names are made of real words and not the "alphabet soup" or highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="21c65-126">すべての Azure RTOS USBX API は、先頭に "ux_" が付き、名詞 - 動詞の名前付け規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="21c65-126">All Azure RTOS USBX APIs have a leading "ux_" and follow a noun-verb naming convention.</span></span> <span data-ttu-id="21c65-127">さらに、API 全体で機能に一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="21c65-127">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="21c65-128">たとえば、中断を実行するすべての API には、API 用の同様に機能するオプションのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="21c65-128">For example, all APIs that suspend have an optional timeout that functions in an identical manner for APIs.</span></span>

### <a name="usb-interoperability-verification"></a><span data-ttu-id="21c65-129">USB 相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="21c65-129">USB Interoperability verification</span></span>

<span data-ttu-id="21c65-130">Azure RTOS USBX デバイス スタックは、USB IF 標準テスト ツール USBCV で厳格にテストされ、USB 仕様に完全に準拠し、さまざまなホスト システムと相互運用性があることが確認されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-130">Azure RTOS USBX Device Stack has been rigorously tested with the USB IF standard testing tool USBCV to ensure full compliance with the USB specifications and interoperability with different host systems.</span></span>
<span data-ttu-id="21c65-131">さらに、Azure RTOS USBX OTG スタックは、台湾の独立テスト ラボ Allion によって検証および認定されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-131">In addition, Azure RTOS USBX OTG stack has been verified and certified by the independent test lab Allion in Taiwan.</span></span>

### <a name="usb-host-controller-support"></a><span data-ttu-id="21c65-132">USB ホスト コントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-132">USB Host controller support</span></span>

<span data-ttu-id="21c65-133">Azure RTOS USBX は、OHCI や EHCI などの主要な USB 標準をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-133">Azure RTOS USBX supports major USB standards like OHCI and EHCI.</span></span> <span data-ttu-id="21c65-134">さらに、Azure RTOS USBX は、Atmel、Microchip、Philips、Renesas、ST、TI、およびその他のベンダーの独自の USB ホスト コントローラーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-134">In addition, Azure RTOS USBX supports proprietary discrete USB host controllers from Atmel, Microchip, Philips, Renesas, ST, TI, and other vendors.</span></span> <span data-ttu-id="21c65-135">Azure RTOS USBX は、同じアプリケーション内の複数のホスト コントローラーもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-135">Azure RTOS USBX also supports multiple host controllers in the same application.</span></span>
<span data-ttu-id="21c65-136">USB デバイス コントローラーのサポート。Azure RTOS USBX は、Analog Devices、Atmel、Microchip、NXP、Philips、Renesas、ST、TI、およびその他のベンダーの人気のある USB デバイス コントローラーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-136">USB Device controller support Azure RTOS USBX supports popular USB device controllers from Analog Devices, Atmel, Microchip, NXP, Philips, Renesas, ST, TI, and other vendors.</span></span>

### <a name="extensive-host-class-support"></a><span data-ttu-id="21c65-137">広範なホスト クラスのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-137">Extensive Host Class support</span></span>

<span data-ttu-id="21c65-138">Azure RTOS USBX ホストは、ASIX、AUDIO、CDC/ACM、CDC/ECM、GSER、HID (キーボード、マウス、およびリモート コントロール)、HUB、PIMA (PTP/MTP)、PRINTER、PROLIFIC、STORAGE などの、最も一般的なクラスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-138">Azure RTOS USBX Host provides support for most popular classes, including ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (keyboard, mouse, and remote control), HUB, PIMA (PTP/MTP), PRINTER, PROLIFIC, and STORAGE.</span></span>

### <a name="extensive-usb-device-class-support"></a><span data-ttu-id="21c65-139">広範な USB デバイス クラスのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-139">Extensive USB Device Class support</span></span>

<span data-ttu-id="21c65-140">Azure RTOS USBX デバイスは、CDC/ACM、CDC/ECM、DFU、HID、PIMA (PTP/MTP) (w/MTP)、RNDIS、STORAGE などの最も一般的なクラスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-140">Azure RTOS USBX Device provides support for most popular classes, including CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS, and STORAGE.</span></span> <span data-ttu-id="21c65-141">カスタム クラスのサポートも利用できます。</span><span class="sxs-lookup"><span data-stu-id="21c65-141">Support for custom classes is also available.</span></span>

### <a name="pictbridge-support"></a><span data-ttu-id="21c65-142">Pictbridge のサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-142">Pictbridge support</span></span>

<span data-ttu-id="21c65-143">Azure RTOS USBX では、ホストとデバイスの両方で完全な Pictbridge 実装がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="21c65-143">Azure RTOS USBX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="21c65-144">Pictbridge は、両方の側の Azure RTOS USBX PIMA (PTP/MTP) クラスの上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="21c65-144">Pictbridge sits on top of Azure RTOS USBX PIMA (PTP/MTP) class on both sides.</span></span> <span data-ttu-id="21c65-145">PictBridge 標準では、PC を使用せずに、デジタル スチル カメラまたはスマートフォンを直接プリンターに接続できるので、特定の Pictbridge 対応プリンターに直接印刷できます。</span><span class="sxs-lookup"><span data-stu-id="21c65-145">The PictBridge standard allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span> <span data-ttu-id="21c65-146">カメラまたはスマートフォンがプリンターに接続されている場合、プリンターは USB ホストであり、カメラは USB デバイスです。</span><span class="sxs-lookup"><span data-stu-id="21c65-146">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="21c65-147">ただし、Pictbridge では、カメラはホストとして表示され、コマンドはカメラから取得されます。</span><span class="sxs-lookup"><span data-stu-id="21c65-147">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="21c65-148">カメラはストレージ サーバーであり、プリンターはストレージ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="21c65-148">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="21c65-149">カメラはプリント クライアントであり、プリンターはもちろんプリント サーバーです。</span><span class="sxs-lookup"><span data-stu-id="21c65-149">The camera is the print client and the printer is of course the print server.</span></span> <span data-ttu-id="21c65-150">Pictbridge は、トランスポート層として USB を使用しますが、通信プロトコルとしては PTP (Picture Transfer Protocol) に依存します。</span><span class="sxs-lookup"><span data-stu-id="21c65-150">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

### <a name="custom-class-support"></a><span data-ttu-id="21c65-151">カスタム クラスのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-151">Custom class support</span></span>

<span data-ttu-id="21c65-152">Azure RTOS USBX ホストとデバイスはカスタム クラスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="21c65-152">Azure RTOS USBX Host and Device support custom classes.</span></span> <span data-ttu-id="21c65-153">カスタム クラスの例は、Azure RTOS USBX ディストリビューションに用意されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-153">An example custom class is provided in the Azure RTOS USBX distribution.</span></span> <span data-ttu-id="21c65-154">この単純なデータ ポンプ クラスは DPUMP と呼ばれ、カスタム アプリケーション クラスのモデルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="21c65-154">This simple data pump class is called DPUMP and can be used as a model for custom application classes.</span></span>
<span data-ttu-id="21c65-155">高度なテクノロジである Azure RTOS USBX ホストとデバイスはカスタム クラスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="21c65-155">Advanced technology Azure RTOS USBX Host and Device support custom classes.</span></span> <span data-ttu-id="21c65-156">カスタム クラスの例は、Azure RTOS USBX ディストリビューションに用意されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-156">An example custom class is provided in the Azure RTOS USBX distribution.</span></span> <span data-ttu-id="21c65-157">Azure RTOS USBX は、次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="21c65-157">Azure RTOS USBX is advanced technology that includes:</span></span>

* <span data-ttu-id="21c65-158">ホスト、デバイス、および OTG のサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-158">Host, Device, and OTG support</span></span>
* <span data-ttu-id="21c65-159">USB の低速、フルスピード、および高速のサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-159">USB low, full, and high-speed support</span></span>
* <span data-ttu-id="21c65-160">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-160">Automatic scaling</span></span>
* <span data-ttu-id="21c65-161">ThreadX、Azure RTOS FileX、Azure RTOS NetX との完全な統合</span><span class="sxs-lookup"><span data-stu-id="21c65-161">Fully integrated with ThreadX, Azure RTOS FileX, and Azure RTOS NetX</span></span>
* <span data-ttu-id="21c65-162">オプションのパフォーマンス メトリック</span><span class="sxs-lookup"><span data-stu-id="21c65-162">Optional performance metrics</span></span>
* <span data-ttu-id="21c65-163">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-163">Azure RTOS TraceX system analysis support</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="21c65-164">市場投入までの時間を最短化</span><span class="sxs-lookup"><span data-stu-id="21c65-164">Fastest time-to-market</span></span>

<span data-ttu-id="21c65-165">Azure RTOS USBX では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-165">Azure RTOS USBX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="21c65-166">Azure RTOS USBX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。</span><span class="sxs-lookup"><span data-stu-id="21c65-166">Azure RTOS USBX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="21c65-167">その結果、Azure RTOS USBX は、埋め込み IoT デバイス向けの最も普及している USB ソリューションの 1 つになっています。</span><span class="sxs-lookup"><span data-stu-id="21c65-167">As a result, Azure RTOS USBX is one of the most popular USB solutions for embedded IoT devices.</span></span> <span data-ttu-id="21c65-168">一貫した市場投入までの時間の優位性は、次の要素を基にして構築されています。</span><span class="sxs-lookup"><span data-stu-id="21c65-168">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="21c65-169">品質のドキュメント – Azure RTOS USBX ホストとデバイスのユーザー ガイドを参照して確認してください。</span><span class="sxs-lookup"><span data-stu-id="21c65-169">Quality documentation – please review our Azure RTOS USBX Host and Device User Guides and see for yourself!</span></span>
* <span data-ttu-id="21c65-170">完全なソース コードを使用可能</span><span class="sxs-lookup"><span data-stu-id="21c65-170">Complete source code availability</span></span>
* <span data-ttu-id="21c65-171">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="21c65-171">Easy-to-use API</span></span>
* <span data-ttu-id="21c65-172">包括的かつ高度な機能セット</span><span class="sxs-lookup"><span data-stu-id="21c65-172">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="21c65-173">シンプルな 1 つのライセンス</span><span class="sxs-lookup"><span data-stu-id="21c65-173">One Simple License</span></span>

<span data-ttu-id="21c65-174">ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスのコストもかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="21c65-174">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="21c65-175">最高品質の完全なソース コード</span><span class="sxs-lookup"><span data-stu-id="21c65-175">Full, highest-quality source code</span></span>

<span data-ttu-id="21c65-176">長年にわたり、Azure RTOS NetX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="21c65-176">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="21c65-177">また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。</span><span class="sxs-lookup"><span data-stu-id="21c65-177">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

### <a name="supports-most-popular-architectures"></a><span data-ttu-id="21c65-178">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-178">Supports most popular architectures</span></span>

<span data-ttu-id="21c65-179">Azure RTOS USBX は、すぐに利用可能で完全なテストとサポートが実現されている、次のような最も一般的な 32/64 ビットのマイクロプロセッサで動作します。</span><span class="sxs-lookup"><span data-stu-id="21c65-179">Azure RTOS USBX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="21c65-180">**Analog Devices**: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="21c65-180">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="21c65-181">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="21c65-181">**Andes Core**: RISC-V</span></span>
* <span data-ttu-id="21c65-182">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="21c65-182">**Ambiqmicro**: Apollo MCUs</span></span>
* <span data-ttu-id="21c65-183">**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="21c65-183">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="21c65-184">**Cadence**: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="21c65-184">**Cadence**: Xtensa, Diamond</span></span>
* <span data-ttu-id="21c65-185">**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="21c65-185">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="21c65-186">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="21c65-186">**Cypress**: RISC-V</span></span>
* <span data-ttu-id="21c65-187">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="21c65-187">**EnSilica**: eSi-RISC</span></span>
* <span data-ttu-id="21c65-188">**Infineon**: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="21c65-188">**Infineon**: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="21c65-189">**Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="21c65-189">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="21c65-190">**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="21c65-190">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="21c65-191">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="21c65-191">**Microsemi**: RISC-V</span></span>
* <span data-ttu-id="21c65-192">**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="21c65-192">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="21c65-193">**Renesas**: SH、HS、V850、RX、RZ、Synergy Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="21c65-193">**Renesas**: SH, HS, V850, RX, RZ, Synergy Silicon Labs: EFM32</span></span>
* <span data-ttu-id="21c65-194">**Synopsys**: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="21c65-194">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="21c65-195">**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="21c65-195">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="21c65-196">**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="21c65-196">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="21c65-197">**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class **Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="21c65-197">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="azure-rtos-usbx-apis"></a><span data-ttu-id="21c65-198">Azure RTOS USBX API</span><span class="sxs-lookup"><span data-stu-id="21c65-198">Azure RTOS USBX APIs</span></span>

### <a name="azure-rtos-usbx-host-api"></a><span data-ttu-id="21c65-199">Azure RTOS USBX Host API</span><span class="sxs-lookup"><span data-stu-id="21c65-199">Azure RTOS USBX Host API</span></span>

<span data-ttu-id="21c65-200">Azure RTOS USBX Host API は、名詞 - 動詞の名前付け規則に従った直感的で一貫性のある API です。</span><span class="sxs-lookup"><span data-stu-id="21c65-200">The Azure RTOS USBX Host API is an intuitive and consistent API, following a noun-verb naming convention.</span></span> <span data-ttu-id="21c65-201">すべての API の先頭を ux_host_\* にして USBX として簡単に識別できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-201">All APIs have leading ux_host_\* to easily identify as USBX.</span></span> <span data-ttu-id="21c65-202">ブロック API には、オプションのスレッド タイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="21c65-202">Any blocking APIs have optional thread timeout.</span></span>

* <span data-ttu-id="21c65-203">ASIX</span><span class="sxs-lookup"><span data-stu-id="21c65-203">ASIX</span></span>
    - <span data-ttu-id="21c65-204">最小 0.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-204">Minimal 0.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-205">自動スケーリング、Azure RTOS TraceX によるシステム レベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-205">Automatic scalingSystem-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-206">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_asix_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-206">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_asix_*\*</span></span>
* <span data-ttu-id="21c65-207">AUDIO</span><span class="sxs-lookup"><span data-stu-id="21c65-207">AUDIO</span></span>
    - <span data-ttu-id="21c65-208">最小 1.2 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-208">Minimal 1.2 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-209">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-209">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-210">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_audio_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-210">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_audio_*\*</span></span>
* <span data-ttu-id="21c65-211">CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="21c65-211">CDC/ACM</span></span>
    - <span data-ttu-id="21c65-212">最小 1.4 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-212">Minimal 1.4 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-213">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-213">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-214">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-214">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-215">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_cdc_acm_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-215">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_cdc_acm_*\*</span></span>
* <span data-ttu-id="21c65-216">HID</span><span class="sxs-lookup"><span data-stu-id="21c65-216">HID</span></span>
    - <span data-ttu-id="21c65-217">最小 0.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-217">Minimal 0.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-218">キーボード、マウス、およびリモート サポート</span><span class="sxs-lookup"><span data-stu-id="21c65-218">Keyboard, mouse, and remote support</span></span>
    - <span data-ttu-id="21c65-219">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-219">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-220">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-220">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-221">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_hid_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-221">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_hid_*\*</span></span> 
* <span data-ttu-id="21c65-222">ハブ</span><span class="sxs-lookup"><span data-stu-id="21c65-222">HUB</span></span>
    - <span data-ttu-id="21c65-223">最小 1.7 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-223">Minimal 1.7 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="21c65-224">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-224">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-225">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-225">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-226">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_hub_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-226">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_hub_*\*</span></span>
* <span data-ttu-id="21c65-227">PIMA (PTP/MTP)</span><span class="sxs-lookup"><span data-stu-id="21c65-227">PIMA (PTP/MTP)</span></span>
    - <span data-ttu-id="21c65-228">最小 0.9 KB のフラッシュ、8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-228">Minimal 0.9 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="21c65-229">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-229">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-230">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-230">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-231">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_pima_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-231">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_pima_*\*</span></span>
* <span data-ttu-id="21c65-232">PRINTER</span><span class="sxs-lookup"><span data-stu-id="21c65-232">PRINTER</span></span>
    - <span data-ttu-id="21c65-233">最小 0.8 KB のフラッシュ、8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-233">Minimal 0.8 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="21c65-234">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-234">Automatic scaling</span></span>
    -  <span data-ttu-id="21c65-235">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-235">System-level trace via Azure RTOS TraceX</span></span>
    -  <span data-ttu-id="21c65-236">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_printer_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-236">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_printer_*\*</span></span>
* <span data-ttu-id="21c65-237">PROLIFIC</span><span class="sxs-lookup"><span data-stu-id="21c65-237">PROLIFIC</span></span>
    - <span data-ttu-id="21c65-238">最小 1.5 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-238">Minimal 1.5 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-239">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-239">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-240">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-240">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-241">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_prolific_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-241">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_prolific_*\*</span></span>
* <span data-ttu-id="21c65-242">STORAG</span><span class="sxs-lookup"><span data-stu-id="21c65-242">STORAG</span></span>
    - <span data-ttu-id="21c65-243">最小 5.6 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-243">Minimal 5.6 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-244">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-244">Automatic scaling</span></span><br> <span data-ttu-id="21c65-245">Azure RTOS FileX との統合</span><span class="sxs-lookup"><span data-stu-id="21c65-245">Integrated with Azure RTOS FileX</span></span>
    - <span data-ttu-id="21c65-246">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-246">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-247">直観的な Azure RTOS USBX Host API の形式: *ux_host_class_storage_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-247">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_storage_*\*</span></span>
* <span data-ttu-id="21c65-248">USB ホスト スタック</span><span class="sxs-lookup"><span data-stu-id="21c65-248">USB Host STACK</span></span>
    - <span data-ttu-id="21c65-249">多くのホスト コントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-249">Supports many host controllers</span></span>
    - <span data-ttu-id="21c65-250">最小 18 KB のフラッシュ、25 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-250">Minimal 18 KB FLASH, 25 KB RAM</span></span>
    - <span data-ttu-id="21c65-251">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-251">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-252">同じプラットフォーム上の複数のホスト コントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-252">Support for multiple host controllers on same platform</span></span>
    -  <span data-ttu-id="21c65-253">USB の低速、フルスピード、および高速のサポート</span><span class="sxs-lookup"><span data-stu-id="21c65-253">USB low, full, and high-speed support</span></span>
    -  <span data-ttu-id="21c65-254">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-254">System-level trace via Azure RTOS TraceX</span></span>
    -  <span data-ttu-id="21c65-255">直観的な Azure RTOS USBX Host API の形式: *ux_host_stack_*  \*</span><span class="sxs-lookup"><span data-stu-id="21c65-255">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_stack_* \*</span></span> 
* <span data-ttu-id="21c65-256">OHCI、EHCI、専用のホスト コントローラー</span><span class="sxs-lookup"><span data-stu-id="21c65-256">OHCI, EHCI, PROPRIETARY Host CONTROLLERS</span></span> 

### <a name="azure-rtos-usbx-device-api"></a><span data-ttu-id="21c65-257">Azure RTOS USBX Device API</span><span class="sxs-lookup"><span data-stu-id="21c65-257">Azure RTOS USBX Device API</span></span>

<span data-ttu-id="21c65-258">Azure RTOS USBX Device API は、名詞 - 動詞の名前付け規則に従った直感的で一貫性のある API です。</span><span class="sxs-lookup"><span data-stu-id="21c65-258">The Azure RTOS USBX Device API is an intuitive and consistent API following a noun-verb naming convention.</span></span> <span data-ttu-id="21c65-259">すべての API の先頭を ux_device_\* にして USBX として簡単に識別できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="21c65-259">All APIs have leading ux_device_\* to easily identify as USBX.</span></span> <span data-ttu-id="21c65-260">ブロック API にオプションのスレッド タイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="21c65-260">Blocking APIs have optional thread timeout.</span></span> <span data-ttu-id="21c65-261">詳細については、[Azure RTOS USBX ホスト ユーザー ガイド](usbx-host-stack-about.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21c65-261">Please see [Azure RTOS USBX Host User Guide](usbx-host-stack-about.md) for more details.</span></span>

* <span data-ttu-id="21c65-262">CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="21c65-262">CDC/ACM</span></span>
    - <span data-ttu-id="21c65-263">最小 0.8 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-263">Minimal 0.8 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="21c65-264">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-264">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-265">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-265">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-266">直観的な Azure RTOS USBX Device API の形式: \*ux_device_class_cdc_acm_\*\*.</span><span class="sxs-lookup"><span data-stu-id="21c65-266">Intuitive Azure RTOS USBX device APIs in this form: \*ux_device_class_cdc_acm_\*\*.</span></span>
* <span data-ttu-id="21c65-267">CDC/ECM</span><span class="sxs-lookup"><span data-stu-id="21c65-267">CDC/ECM</span></span>
    - <span data-ttu-id="21c65-268">最小 1.5 KB のフラッシュ、4 KB から 8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-268">Minimal 1.5 KB FLASH, 4 KB to 8 KB RAM</span></span>
    - <span data-ttu-id="21c65-269">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-269">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-270">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-270">System-level trace via Azure RTOS TraceX</span></span><br> <span data-ttu-id="21c65-271">直観的な Azure RTOS USBX Device API の形式: \*ux_device_class_cdc_ecm_\*\*.</span><span class="sxs-lookup"><span data-stu-id="21c65-271">Intuitive Azure RTOS USBX device APIs in this form: \*ux_device_class_cdc_ecm_\*\*.</span></span>
* <span data-ttu-id="21c65-272">DFU</span><span class="sxs-lookup"><span data-stu-id="21c65-272">DFU</span></span>
    - <span data-ttu-id="21c65-273">最小 1.1 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-273">Minimal 1.1 KB FLASH, 2 KB RAM</span></span>
    -  <span data-ttu-id="21c65-274">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-274">Automatic scaling</span></span>
    -  <span data-ttu-id="21c65-275">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-275">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-276">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_dfu_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-276">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_dfu_*\*</span></span> 
* <span data-ttu-id="21c65-277">GSER</span><span class="sxs-lookup"><span data-stu-id="21c65-277">GSER</span></span>
    - <span data-ttu-id="21c65-278">最小 0.6 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-278">Minimal 0.6 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-279">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-279">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-280">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-280">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-281">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_gser_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-281">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_gser_*\*</span></span>
* <span data-ttu-id="21c65-282">HID</span><span class="sxs-lookup"><span data-stu-id="21c65-282">HID</span></span>
    - <span data-ttu-id="21c65-283">最小 0.9 KB のフラッシュ、2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-283">Minimal 0.9 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="21c65-284">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-284">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-285">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-285">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-286">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_hid_* \* PIMA (PTP/MTP)</span><span class="sxs-lookup"><span data-stu-id="21c65-286">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_hid_*\* PIMA (PTP/MTP)</span></span>
    - <span data-ttu-id="21c65-287">最小 5.2 KB のフラッシュ、8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-287">Minimal 5.2 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="21c65-288">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-288">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-289">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-289">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-290">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_pima_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-290">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_pima_*\*</span></span> 
* <span data-ttu-id="21c65-291">記憶域</span><span class="sxs-lookup"><span data-stu-id="21c65-291">STORAGE</span></span>
    - <span data-ttu-id="21c65-292">最小 2.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-292">Minimal 2.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-293">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-293">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-294">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-294">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-295">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_storage_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-295">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_storage_*\*</span></span>
* <span data-ttu-id="21c65-296">RNDIS</span><span class="sxs-lookup"><span data-stu-id="21c65-296">RNDIS</span></span>
    - <span data-ttu-id="21c65-297">最小 2.3 KB のフラッシュ、4 KB から 8 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-297">Minimal 2.3 KB FLASH, 4 KB to 8 KB RAM</span></span>
    - <span data-ttu-id="21c65-298">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-298">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-299">Azure RTOS NetX と Azure RTOS NetX DUO との統合</span><span class="sxs-lookup"><span data-stu-id="21c65-299">Integrated with Azure RTOS NetX and Azure RTOS NetX DUO</span></span>
    - <span data-ttu-id="21c65-300">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-300">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-301">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_rndls_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-301">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_rndls_*\*</span></span>
* <span data-ttu-id="21c65-302">Azure RTOS USBX デバイス スタック</span><span class="sxs-lookup"><span data-stu-id="21c65-302">Azure RTOS USBX Device STACK</span></span>
    - <span data-ttu-id="21c65-303">最小 2.3 KB のフラッシュ、4 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="21c65-303">Minimal 2.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="21c65-304">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="21c65-304">Automatic scaling</span></span>
    - <span data-ttu-id="21c65-305">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="21c65-305">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="21c65-306">直観的な Azure RTOS USBX Device API の形式: *ux_device_class_storage_* \*</span><span class="sxs-lookup"><span data-stu-id="21c65-306">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_storage_*\*</span></span>
* <span data-ttu-id="21c65-307">専用のホスト コントローラー</span><span class="sxs-lookup"><span data-stu-id="21c65-307">PROPRIETARY Host CONTROLLERS</span></span>

## <a name="next-steps"></a><span data-ttu-id="21c65-308">次のステップ</span><span class="sxs-lookup"><span data-stu-id="21c65-308">Next steps</span></span>

<span data-ttu-id="21c65-309">[ホスト スタック ユーザー ガイド](usbx-host-stack-about.md)または[デバイス スタック ユーザー ガイド](usbx-device-stack-about.md)に関する記事に従って、Azure RTOS USBX ホストおよびデバイス スタックの使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="21c65-309">Start working with the Azure RTOS USBX Host and Device Stack by following our [Host Stack User Guide](usbx-host-stack-about.md) or [Device Stack User Guide](usbx-device-stack-about.md).</span></span>