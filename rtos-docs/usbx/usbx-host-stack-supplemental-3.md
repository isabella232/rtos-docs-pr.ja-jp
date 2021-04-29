---
title: USBX DPUMP クラスに関する考慮事項
description: USBX には、ホストとデバイス側の DPUMP クラスが含まれています。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812890"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="58614-103">第 3 章 USBX DPUMP クラスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="58614-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="58614-104">USBX には、ホストとデバイス側の DPUMP クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58614-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="58614-105">このクラスは、それ自体の標準クラスではなく、2 つの一括パイプを使用して単純なデバイスを作成し、これらの 2 つのパイプ上でデータを送受信する方法を示す例です。</span><span class="sxs-lookup"><span data-stu-id="58614-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="58614-106">DPUMP クラスは、カスタム クラスを開始するため、またはレガシ RS232 デバイス用に使用できます。</span><span class="sxs-lookup"><span data-stu-id="58614-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="58614-107">USB DPUMP フロー チャート:</span><span class="sxs-lookup"><span data-stu-id="58614-107">USB DPUMP flow chart:</span></span>

![USB DPUMP フロー チャート](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="58614-109">USBX DPUMP ホスト クラス</span><span class="sxs-lookup"><span data-stu-id="58614-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="58614-110">DPUMP クラスのホスト側には、2 つの関数 (データの送信用に 1 つとデータの受信用に 1 つ) があります。</span><span class="sxs-lookup"><span data-stu-id="58614-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="58614-111">DPUMP アプリケーションを簡単にするために、両方の関数がブロックされています。</span><span class="sxs-lookup"><span data-stu-id="58614-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="58614-112">両方のパイプ (IN と OUT) を同時に実行する必要がある場合、アプリケーションで送信スレッドと受信スレッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58614-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="58614-113">関数を記述するためのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="58614-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="58614-114">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="58614-114">Where:</span></span>

- <span data-ttu-id="58614-115">dpump はクラスのインスタンスです</span><span class="sxs-lookup"><span data-stu-id="58614-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="58614-116">data_pointer は、送信するバッファーへのポインターです</span><span class="sxs-lookup"><span data-stu-id="58614-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="58614-117">requested_length は送信する長さです</span><span class="sxs-lookup"><span data-stu-id="58614-117">requested_length is the length to send</span></span>
- <span data-ttu-id="58614-118">actual_length は、正常に、または部分的に転送が完了した後に送信された長さです。</span><span class="sxs-lookup"><span data-stu-id="58614-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="58614-119">受信側の関数のプロトタイプも同様です。</span><span class="sxs-lookup"><span data-stu-id="58614-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="58614-120">次に、アプリケーションがデバイス側にパケットを書き込み、受信時に同じパケットを受信するホスト DPUMP クラスの例を示します。</span><span class="sxs-lookup"><span data-stu-id="58614-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="58614-121">USBX DPUMP デバイス クラス</span><span class="sxs-lookup"><span data-stu-id="58614-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="58614-122">デバイス DPUMP クラスでは、USB ホストへの接続時に開始されるスレッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="58614-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="58614-123">スレッドは、一括送信エンドポイントに到着するパケットを待機します。</span><span class="sxs-lookup"><span data-stu-id="58614-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="58614-124">パケットが受信されると、そのコンテンツが一括入力エンドポイント バッファーにコピーされ、このエンドポイントにトランザクションがポストされて、ホストがこのエンドポイントからの読み取り要求を発行するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="58614-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="58614-125">これにより、一括出力および一括入力エンドポイント間のループバック メカニズムが提供されます。</span><span class="sxs-lookup"><span data-stu-id="58614-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
