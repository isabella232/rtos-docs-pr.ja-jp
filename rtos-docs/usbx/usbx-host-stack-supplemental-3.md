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
# <a name="chapter-3-usbx-dpump-class-considerations"></a>第 3 章 USBX DPUMP クラスに関する考慮事項

USBX には、ホストとデバイス側の DPUMP クラスが含まれています。 このクラスは、それ自体の標準クラスではなく、2 つの一括パイプを使用して単純なデバイスを作成し、これらの 2 つのパイプ上でデータを送受信する方法を示す例です。 DPUMP クラスは、カスタム クラスを開始するため、またはレガシ RS232 デバイス用に使用できます。

USB DPUMP フロー チャート:

![USB DPUMP フロー チャート](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>USBX DPUMP ホスト クラス

DPUMP クラスのホスト側には、2 つの関数 (データの送信用に 1 つとデータの受信用に 1 つ) があります。

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

DPUMP アプリケーションを簡単にするために、両方の関数がブロックされています。 両方のパイプ (IN と OUT) を同時に実行する必要がある場合、アプリケーションで送信スレッドと受信スレッドを作成する必要があります。

関数を記述するためのプロトタイプは次のとおりです。

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

各値の説明:

- dpump はクラスのインスタンスです
- data_pointer は、送信するバッファーへのポインターです
- requested_length は送信する長さです
- actual_length は、正常に、または部分的に転送が完了した後に送信された長さです。

受信側の関数のプロトタイプも同様です。

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

次に、アプリケーションがデバイス側にパケットを書き込み、受信時に同じパケットを受信するホスト DPUMP クラスの例を示します。

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

## <a name="usbx-dpump-device-class"></a>USBX DPUMP デバイス クラス

デバイス DPUMP クラスでは、USB ホストへの接続時に開始されるスレッドが使用されます。 スレッドは、一括送信エンドポイントに到着するパケットを待機します。 パケットが受信されると、そのコンテンツが一括入力エンドポイント バッファーにコピーされ、このエンドポイントにトランザクションがポストされて、ホストがこのエンドポイントからの読み取り要求を発行するのを待機します。 これにより、一括出力および一括入力エンドポイント間のループバック メカニズムが提供されます。
