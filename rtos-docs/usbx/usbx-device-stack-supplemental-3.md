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
# <a name="chapter-3---usbx-dpump-class-considerations"></a>第 3 章 - USBX DPUMP クラスに関する考慮事項

USBX には、ホストとデバイス側の **DPUMP** クラスが含まれています。 このクラスは、それ自体の標準クラスではなく、2 つの一括パイプを使用して単純なデバイスを作成し、これらの 2 つのパイプ上でデータを送受信する方法を示す例です。 **DPUMP** クラスは、カスタム クラスを開始するため、またはレガシ RS232 デバイス用に使用できます。

USB DPUMP フロー チャート:

![USB DPUMP フロー チャート](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>USBX DPUMP デバイス クラス

デバイス **DPUMP** クラスではスレッドが使用されます。これは USB ホストへの接続時に開始されます。 スレッドは、一括送信エンドポイントに到着するパケットを待機します。 パケットを受信すると、その内容が一括入力エンドポイント バッファーにコピーされ、このエンドポイントにトランザクションがポストされて、ホストがこのエンドポイントからの読み取り要求を発行するのを待機します。 これにより、一括出力および一括入力エンドポイント間のループバック メカニズムが提供されます。
