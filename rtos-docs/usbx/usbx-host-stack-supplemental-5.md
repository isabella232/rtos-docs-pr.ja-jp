---
title: USBX OTG
description: OTG 対応 USB コントローラーをハードウェア設計に使用できる場合、USBX が USB の OTG 機能をサポートします。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bb9a0b98ed3f843ee690dfe419a3684562f1255e6839ddb06ded9d8f6023adcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798267"
---
# <a name="chapter-5-usbx-otg"></a>第 5 章: USBX OTG

OTG 対応 USB コントローラーをハードウェア設計に使用できる場合、USBX が USB の OTG 機能をサポートします。

USBX では、コア USB スタック内で OTG をサポートしています。 しかし、OTG が機能するには、特定の USB コントローラーが必要です。 USBX OTG コントローラー関数は、***usbx_otg*** ディレクトリにあります。 現在の USBX バージョンでは、完全な OTG 機能を備える NXP LPC3131 のみがサポートされています。

通常のコントローラー ドライバー関数 (ホストまたはデバイス) は従来どおりに標準の USBX usbx_device_controllers と usbx_host_controllers にありますが、***usbx_otg*** ディレクトリには、USB コントローラーに関連付けられている特定の OTG 関数が含まれています。

通常のホストやデバイスの関数に加えて、OTG コントローラー対応関数には次の 4 つの種類があります。

- VBUS 固有関数
- コントローラーの起動と停止
- USB ロール マネージャー
- 割り込みハンドラー

## <a name="vbus-functions"></a>VBUS 関数

各コントローラーには、電力管理要件に基づいて VBUS の状態を変更する VBUS マネージャーを搭載する必要があります。 通常、この関数は VBUS のオン/オフの切り替えのみを実行します

## <a name="start-and-stop-the-controller"></a>コントローラーの起動と停止

通常の USB 実装とは異なり、OTG では、ロールを変更するときにホストやデバイス スタック (またはそのいずれか) をアクティブ化/非アクティブ化する必要があります。

## <a name="usb-role-manager"></a>USB ロール マネージャー

USB ロール マネージャーは、USB の状態を変更するコマンドを受け取ります。 次の表に示すように、遷移を必要とする状態がいくつかあります。

| State                    | 値 | 説明                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | デバイスはアイドル状態です。 何にも接続していません |
| UX_OTG_IDLE_TO_HOST  | 1     | デバイスはタイプ A コネクタに接続しています             |
| UX_OTG_IDLE_TO_SLAVE | 2     | デバイスはタイプ B コネクタに接続しています             |
| UX_OTG_HOST_TO_IDLE  | 3     | ホスト デバイスが切断されました                          |
| UX_OTG_HOST_TO_SLAVE | 4     | ホストからスレーブにロールが切り替えられます                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | スレーブ デバイスが切断しています                          |
| UX_OTG_SLAVE_TO_HOST | 6     | スレーブからホストにロールが切り替えられます                          |

## <a name="interrupt-handlers"></a>割り込みハンドラー

OTG 用のホストとデバイスのコントローラー ドライバーには、従来の USB 割り込みを超える信号 (特に SRP や VBUS による信号) を監視するために、別の割り込みハンドラーが必要です。

ここでは、USB OTG コントローラーを初期化する方法の例として、 NXP LPC3131 を使用します。

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

この例では、VBUS 関数とモード変更のコールバック (ホストからスレーブ、またはその逆) を渡すことによって、LPC3131 を OTG モードで初期化します。

コールバック関数は、新しいモードを記録し、保留中のスレッドを新しい状態でウェイクアップするだけです。

```C
void tx_demo_change_mode_callback(ULONG mode)
{
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

渡されるモード値には、次の値を指定できます。

- UX_OTG_MODE_IDLE
- UX_OTG_MODE_SLAVE
- UX_OTG_MODE_HOST

アプリケーションでは、次の変数を調べることで、常にデバイスの種類を確認できます。

```C
ux_system_otg ->ux_system_otg_device_type
```

値は次のいずれかです。

- UX_OTG_DEVICE_A
- UX_OTG_DEVICE_B
- UX_OTG_DEVICE_IDLE

USB OTG ホスト デバイスは、次のコマンドを発行することによって、常にロール スワップを要求できます。

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */

ux_host_stack_role_swap(storage ->ux_host_class_storage_device);
```

スレーブ デバイスの場合、発行するコマンドはありませんが、ロールを変更する状態を設定できます。ホストが GET_STATUS を発行したときに、この状態がホストによって取得されて、スワップが開始されます。

```C
/* We are a B device, ask for role swap. The next GET_STATUS from the host will get the status change and do the HNP. */

ux_system_otg ->ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
