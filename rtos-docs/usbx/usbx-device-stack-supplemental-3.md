---
title: 第 3 章 - USBX DPUMP クラスに関する考慮事項
description: USBX には、ホストとデバイス側の DPUMP クラスが含まれています。 このクラスは、それ自体の標準クラスではなく、2 つの一括パイプを使用して単純なデバイスを作成し、これらの 2 つのパイプ上でデータを送受信する方法を示す例です
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813430"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="652fd-104">第 3 章 - USBX DPUMP クラスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="652fd-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="652fd-105">USBX には、ホストとデバイス側の **DPUMP** クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="652fd-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="652fd-106">このクラスは、それ自体の標準クラスではなく、2 つの一括パイプを使用して単純なデバイスを作成し、これらの 2 つのパイプ上でデータを送受信する方法を示す例です。</span><span class="sxs-lookup"><span data-stu-id="652fd-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="652fd-107">**DPUMP** クラスは、カスタム クラスを開始するため、またはレガシ RS232 デバイス用に使用できます。</span><span class="sxs-lookup"><span data-stu-id="652fd-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="652fd-108">USB DPUMP フロー チャート:</span><span class="sxs-lookup"><span data-stu-id="652fd-108">USB DPUMP flow chart:</span></span>

![USB DPUMP フロー チャート](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="652fd-110">USBX DPUMP デバイス クラス</span><span class="sxs-lookup"><span data-stu-id="652fd-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="652fd-111">デバイス **DPUMP** クラスではスレッドが使用されます。これは USB ホストへの接続時に開始されます。</span><span class="sxs-lookup"><span data-stu-id="652fd-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="652fd-112">スレッドは、一括送信エンドポイントに到着するパケットを待機します。</span><span class="sxs-lookup"><span data-stu-id="652fd-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="652fd-113">パケットを受信すると、その内容が一括入力エンドポイント バッファーにコピーされ、このエンドポイントにトランザクションがポストされて、ホストがこのエンドポイントからの読み取り要求を発行するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="652fd-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="652fd-114">これにより、一括出力および一括入力エンドポイント間のループバック メカニズムが提供されます。</span><span class="sxs-lookup"><span data-stu-id="652fd-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
