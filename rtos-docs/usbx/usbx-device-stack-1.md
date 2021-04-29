---
title: 第 1 章 - Azure RTOS USBX デバイス スタックの概要
description: USBX は、深く組み込まれたアプリケーション用のフル機能の USB スタックです。 この章では、USBX の概要と、その応用および利点について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813439"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="be6fe-104">第 1 章 - Azure RTOS USBX デバイス スタックの概要</span><span class="sxs-lookup"><span data-stu-id="be6fe-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="be6fe-105">USBX は、深く組み込まれたアプリケーション用のフル機能の USB スタックです。</span><span class="sxs-lookup"><span data-stu-id="be6fe-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="be6fe-106">この章では、USBX の概要と、その応用および利点について説明します</span><span class="sxs-lookup"><span data-stu-id="be6fe-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="be6fe-107">USBX の機能</span><span class="sxs-lookup"><span data-stu-id="be6fe-107">USBX features</span></span>

<span data-ttu-id="be6fe-108">USBX では、1.1、2.0、OTG という 3 つの既存の USB 仕様がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be6fe-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="be6fe-109">スケーラブルになるように設計されており、デバイスが 1 つしか接続されていないシンプルな USB トポロジにも、複数のデバイスとカスケード ハブを使用する複雑なトポロジにも対応できます。</span><span class="sxs-lookup"><span data-stu-id="be6fe-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="be6fe-110">USBX では、USB プロトコルのあらゆるデータ転送の種類 (コントロール、一括、割り込み、アイソクロナス) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be6fe-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="be6fe-111">USBX では、ホスト側とデバイス側の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be6fe-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="be6fe-112">それぞれの側が 3 つのレイヤーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="be6fe-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="be6fe-113">コントローラー レイヤー</span><span class="sxs-lookup"><span data-stu-id="be6fe-113">Controller layer</span></span>
- <span data-ttu-id="be6fe-114">スタック レイヤー</span><span class="sxs-lookup"><span data-stu-id="be6fe-114">Stack layer</span></span>
- <span data-ttu-id="be6fe-115">クラス レイヤー</span><span class="sxs-lookup"><span data-stu-id="be6fe-115">Class layer</span></span>

<span data-ttu-id="be6fe-116">USB レイヤー間の関係は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be6fe-116">The relationship between the USB layers is as follows:</span></span>

![各 USB レイヤー](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="be6fe-118">製品の特徴</span><span class="sxs-lookup"><span data-stu-id="be6fe-118">Product Highlights</span></span>

- <span data-ttu-id="be6fe-119">ThreadX プロセッサの完全なサポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="be6fe-120">ロイヤリティなし</span><span class="sxs-lookup"><span data-stu-id="be6fe-120">No royalties</span></span>
- <span data-ttu-id="be6fe-121">完全な ANSI C ソース コード</span><span class="sxs-lookup"><span data-stu-id="be6fe-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="be6fe-122">リアルタイムのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="be6fe-122">Real-time performance</span></span>
- <span data-ttu-id="be6fe-123">すばやく対応するテクニカル サポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-123">Responsive technical support</span></span>
- <span data-ttu-id="be6fe-124">複数クラス サポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-124">Multiple class support</span></span>
- <span data-ttu-id="be6fe-125">複数クラス インスタンス</span><span class="sxs-lookup"><span data-stu-id="be6fe-125">Multiple class instances</span></span>
- <span data-ttu-id="be6fe-126">ThreadX、FileX、および NetX とのクラスの統合</span><span class="sxs-lookup"><span data-stu-id="be6fe-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="be6fe-127">複数の構成を持つ USB デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="be6fe-128">USB 複合デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-128">Support for USB composite devices</span></span>
- <span data-ttu-id="be6fe-129">USB 電源管理のサポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-129">Support for USB power management</span></span>
- <span data-ttu-id="be6fe-130">USB OTG のサポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-130">Support for USB OTG</span></span>
- <span data-ttu-id="be6fe-131">TraceX のトレース イベントのエクスポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="be6fe-132">USBX の強力なサービス</span><span class="sxs-lookup"><span data-stu-id="be6fe-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="be6fe-133">USB デバイス フレームワークの完全なサポート</span><span class="sxs-lookup"><span data-stu-id="be6fe-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="be6fe-134">USBX では、複数の構成、複数のインターフェイス、複数の代替設定など、最も要求の厳しい USB デバイスをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="be6fe-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="be6fe-135">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="be6fe-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="be6fe-136">USBX では、わかりやすく使いやすい方法で、最良の深く組み込まれた USB スタックが提供されます。</span><span class="sxs-lookup"><span data-stu-id="be6fe-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="be6fe-137">USBX API を使用すると、サービスが直観的かつ一貫したものになります。</span><span class="sxs-lookup"><span data-stu-id="be6fe-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="be6fe-138">提供された USBX クラス API を使用することにより、ユーザー アプリケーションでは複雑な USB プロトコルを理解する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="be6fe-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
