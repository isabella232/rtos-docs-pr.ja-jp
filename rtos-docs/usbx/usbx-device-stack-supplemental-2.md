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
# <a name="chapter-2---usbx-device-class-considerations"></a>第 2 章 - USBX デバイス クラスに関する考慮事項

## <a name="usb-device-rndis-class"></a>USB デバイス RNDIS クラス

USB デバイス RNDIS クラスにより、USB ホスト システムが、イーサネット デバイスとしてデバイスと通信できるようになります。 このクラスは Microsoft 独自の実装に基づいており、Windows プラットフォームに固有です。

RNDIS 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。 次に例を示します。

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

RNDIS クラスは、CDC-ACM および CDC-ECM とよく似たデバイス記述子アプローチを採用しており、IAD 記述子も必要とします。 デバイス記述子の定義と要件については、「CDC-ACM クラス」をご覧ください。

RNDIS クラスのアクティブ化は次のとおりです。

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

CDC-ECM の場合、RNDIS クラスにはローカルとリモートの 2 つのノードが必要ですが、リモート ノードを記述する文字列記述子は必要はありません。

ただし、Microsoft 独自のメッセージング メカニズムにより、追加パラメーターがいくつか必要です。 まず、ベンダー ID を渡す必要があります。 同様に、RNDIS のドライバー バージョンも必要です。 ベンダー文字列を指定する必要もあります。

RNDIS クラスには、両方の方法でデータを転送するための組み込み API が用意されていますが、ユーザー アプリケーションは NetX 経由で USB イーサネット デバイスと通信するため、アプリケーションには表示されません。

USBX RNDIS クラスは、Azure RTOS NetX ネットワーク スタックに緊密に関連付けられています。 NetX と USBX の両方の RNDIS クラスを使用するアプリケーションは、通常の方法で NetX ネットワークスタックを起動しますが、それに加えて次のように USB ネットワーク スタックをアクティブにする必要があります。

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB ネットワーク スタックは 1 回だけアクティブにする必要があり、RNDIS に固有ではありませんが、NetX サービスを必要とするすべての USB クラスで必要になります。

RNDIS クラスは、Microsoft オペレーティング システムに固有であるため、MAC OS や Linux ホストによって認識されません。 Windows プラットフォーム上で、.inf ファイルが、デバイス記述子と一致するホスト上に存在している必要があります。 Microsoft は RNDIS クラスのテンプレートを提供しており、これは usbx_windows_host_files ディレクトリにあります。 新しいバージョンの Windows の場合は、RNDIS_Template ファイルを使用します。 このファイルを変更して、デバイスによって使用される PID/VID を反映させる必要があります。 この PID/VID は、会社と製品が USB-IF に登録されたときに、最終的な顧客に固有のものになります。 inf ファイル内の変更対象のフィールドを次に示します。

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

RNDIS デバイスのデバイス フレームワーク内で、PID/VID はデバイス記述子に格納されます (上記の宣言されたデバイス記述子を参照)

USB ホスト システムによって USB RNDIS デバイスが検出されると、ネットワーク インターフェイスがマウントされ、デバイスは、ネットワーク プロトコル スタックと共に使用できます。 詳細については、「ホスト オペレーティング システム」をご覧ください。

## <a name="usb-device-dfu-class"></a>USB デバイス DFU クラス

USB デバイス DFU クラスにより、USB ホスト システムが、ホスト アプリケーションに基づいてデバイス ファームウェアを更新できるようになります。 DFU クラスは、USB-IF 標準クラスです。

USBX DFU クラスは比較的シンプルです。 そのデバイス記述子には、コントロール エンドポイント以外は必要ありません。 ほとんどの場合、このクラスは USB 複合デバイスに埋め込まれます。 デバイスは、ストレージ デバイスや通信デバイスなど何でも構いません。また、追加された DFU インターフェイスは、デバイスが即座にファームウェアを更新できることをホストに通知できます。

DFU クラスは 3 つの手順で動作します。 まず、エクスポートされたクラスを使用して、デバイスが通常どおりにマウントされます。 ホスト (Windows または Linux) 上のアプリケーションが、DFU クラスを実行し、デバイスを DFU モードにリセットするように要求を送信します。 デバイスは、短時間 (ホストとデバイスが RESET シーケンスを検出できるだけの時間) だけバスから非表示になります。そして再起動時にデバイスは排他的に DFU モードになり、ホスト アプリケーションがファームウェアのアップグレードを送信するのを待ちます。 ファームウェアのアップグレードが完了すると、デバイスはホスト アプリケーションによってリセットされ、再列挙時に新しいファームウェアで通常の動作に戻ります。

DFU デバイス フレームワークは、次のようになります。

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

この例では、DFU 記述子は他のクラスには関連付けられていません。 単純なインターフェイス記述子があり、その他のエンドポイントはアタッチされていません。 デバイスの DFU 機能の詳細について説明する機能記述子があります。

DFU 機能の説明は次のとおりです。

| 名前             | Offset  | サイズ | type      | 説明 |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | ビット フィールド | ビット 3: デバイスは、DFU_DETACH 要求を受信すると、バス デタッチ-アタッチ シーケンスを実行します。 ホストは、USB リセットを実行することはできません。 (bitWillDetach) 0 = いいえ 1 = はい ビット 2: デバイスは明示フェーズ後に USB 経由で通信できます。 (bitManifestationTolerant) 0 = いいえ、バス リセット確認要 1 = はい ビット 1: アップロード対応 (bitCanUpload) 0 = いいえ 1 = はい ビット 0: ダウンロード対応 (bitCanDnload) 0 = いいえ 1 = はい  |
| wDetachTimeOut  | 3      | 2  | number    | DFU_DETACH 要求の受信後にデバイスが待機する時間 (ミリ秒単位)。 USB リセットせずにこの時間が経過すると、デバイスは再構成フェーズを終了し、通常の操作に戻ります。 これは、デバイスが待機できる最大時間を表します (タイマーなどによって異なります)。 この値は、USBX によって 1000 ミリ秒に設定されます。  |
| wTransferSize  | 5      | 2  | number    | デバイスが受け入れることができる制御\-書き込み操作あたりの最大バイト数。 この値は、USBX によって 64 バイトに設定されます。 |

DFU クラスの宣言は次のとおりです。

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

DFU クラスは、ターゲットに固有のデバイス ファームウェア アプリケーションを処理する必要があります。 このため、ファームウェアのブロックの読み取りおよび書き込みを行い、ファームウェア更新アプリケーションから状態を取得するために、コールバックがいくつか定義されます。 また、DFU クラスには、ファームウェアの転送の開始と終了が発生したときにアプリケーションに通知する、通知コールバック関数もあります。

一般的な DFU アプリケーション フローの説明を次に示します。

![DFU アプリケーション フロー](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

DFU クラスの主な課題は、ファームウェアのダウンロードを実行するための適切なアプリケーションをホスト上で取得することです。 Microsoft または USB-IF によって提供されるアプリケーションはありません。 シェアウェアがいくつか存在し、それらは Linux 上では適切に動作し、Windows 上でも程度の差はありますが、それなりに機能します。

Linux 上では、[https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) にある dfu-utils を使用できます。また、次のリンクには dfu utils に関する情報が多数記載されています: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

ホストとデバイスの間のリセット シーケンスは、DFU の Linux 実装によって正しく実行されます。したがって、デバイスは、この処理を実行する必要がありません。 Linuxは、bmAttributes *bitWillDetach* 0 を受け入れることができます。 一方、Window の場合は、デバイスがリセットを実行する必要があります。

Windows 上で、USB レジストリは、USB デバイスと、その PID/VID、および DFU アプリケーションによって使用される USB ライブラリを関連付けられる必要があります。 これは、[https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) にある無料のユーティリティ Zadig を使って簡単に実行できます。

Zadig を初めて実行すると、次のスクリーンが表示されます。

![Zadig の初回の実行](./media/usbx-device-stack-supplemental/zadig.png)

デバイスの一覧からデバイスを見つけて、libusb Windows ドライバーに関連付けます。 これにより、デバイスの PID/VID が DFU ユーティリティによって使用される Windows USB ライブラリにバインドされます。

DFU コマンドを操作するには、zip 圧縮された dfu ユーティリティをディレクトリに展開するだけです。また、libusb dll が、その同じディレクトリに存在することも確認します。 DFU ユーティリティは、コマンド ラインを使用して DOS ボックスから実行する必要があります。

まず、**dfu-util –l** コマンドを入力して、デバイスが一覧に表示されているかどうかを確認します。 表示されていない場合は、Zadig を実行して、デバイスが一覧表示され、USB ライブラリに関連付けられていることを確認します。 次のスクリーンが表示されます。

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

次の手順で、ダウンロードするファイルを準備します。 USBX DFU クラスは、このファイルに対して何の検証も実行せず、その内部形式には依存していません。 このファームウェア ファイルはターゲットに対して非常に限定的なものですが、DFU または USBX 固有ではありません。

その後、次のコマンドを入力すると、ファイルを送信するように dfu-util に指示できます。

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

dfu-util により、ファームウェアが完全にダウンロードされるまでのファイルのダウンロード プロセスが表示されます。

## <a name="usb-device-pima-class-ptp-responder"></a>USB デバイス PIMA クラス (PTP レスポンダー)

USB デバイス PIMA クラスにより、USB ホスト システム (イニシエーター) が、

メディア ファイルを転送するための PIMA デバイス (レスポンダー) に接続できるようになります。 USBX Pima クラスは、PTP (画像転送プロトコル) クラスとも呼ばれる USB-IF PIMA 15740 クラスに準拠しています。

USBX デバイス側の PIMA クラスは、次の操作をサポートしています。

| 操作コード                                    | 値 | 説明                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | デバイスでサポートされている操作とイベントを取得します                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | ホストとデバイスの間のセッションを開きます                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | ホストとデバイスの間のセッションを閉じます                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | デバイスのストレージ ID を返します。 USBX PIMA は 1 つのストレージ ID のみを使用します |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | 最大容量および空き領域などのストレージ オブジェクトに関する情報を返します                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | ストレージ デバイス内に含まれるオブジェクトの数を返します                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | ストレージ デバイス上のオブジェクトのハンドルの配列を返します                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | オブジェクトの名前、その作成日、変更日などのオブジェクトに関する情報を返します |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | 特定のオブジェクトに関連するデータを返します                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | オブジェクトに関するサムネイル (使用できる場合) を送信します                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | メディア上のオブジェクトを削除します                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | メディア上にオブジェクトを作成するためのオブジェクト情報をデバイスに送信します                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | オブジェクトのデータをデバイスに送信します                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | デバイス メディアをクリーンします                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | ターゲット デバイスをリセットします                                                                                   |

| 操作コード                                         | 値 | 説明 |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | 現在のトランザクションを取り消します                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | オブジェクトがデバイス メディアに追加されました。これはホストによって取得できます。 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | オブジェクトがデバイス メディアから削除されました                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | メディアがデバイスに追加されました                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | メディアがデバイスから削除されました                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | デバイスのプロパティが変更されました                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | オブジェクト情報が変更されました                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | デバイスが変更されました                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | デバイスはオブジェクトの転送をホストに要求します                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | デバイスはメディアがいっぱいであることを報告します                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | デバイスは自身がリセットされたことを報告します                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | デバイス上でストレージ情報が変更されました                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | キャプチャが完了しました                                                            |

USBX PIMA デバイス クラスは、TX スレッドを使用して、ホストからの PIMA コマンドをリッスンします。

PIMA コマンドは、コマンド ブロック、データ ブロック、および状態フェーズで構成されます。

関数 ux_device_class_pima_thread は、要求をスタックにポストして、ホスト側から PIMA コマンドを受信します。 PIMA コマンドがデコードされ、コンテンツに対して検証されます。 コマンド ブロックが有効な場合は、適切なコマンド ハンドラーに分岐します。

PIMA コマンドのほとんどは、セッションがホストによって開かれた場合にのみ実行できます。 唯一の例外は、**UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO** コマンドです。 USBX PIMA 実装を使用する場合、イニシエーターとレスポンダーの間で開くことができるセッションはいつでも 1 つだけです。 1 つのセッション内のすべてのトランザクションがブロックとなり、前のトランザクションが完了するまで、新しいトランザクションを開始することはできません。

PIMA トランザクションは、コマンド フェーズ、オプションのデータ フェーズと応答フェーズの 3 つのフェーズで構成されています。 データ フェーズが存在する場合は、一方向のみになります。

PIMA 操作のフローを決定するのは常にイニシエーターですが、レスポンダーはセッション中に発生した状態の変更を通知するために、イニシエーターに対するイベントを開始することができます。

次の図は、ホストと PIMA デバイス クラスの間のデータ オブジェクトの転送を示しています。

![PIMA トランザクション](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>PIMA デバイス クラスの初期化

PIMA デバイス クラスには、初期化中、アプリケーションによって提供されたパラメーターがいくつか必要です。

次のパラメーターは、デバイスとストレージの情報について説明します。

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

また、PIMA クラスにはアプリケーションへのコールバック登録が必要で、これによって特定のイベントをアプリケーションに通知したり、ローカル メディアとの間でデータを取得/保存したりします。 コールバックを次に示します。

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

次の例は、PIMA のクライアント側を初期化する方法を示しています。 この例は、PIMA に対するクライアントとして Pictbridge を使用します。

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

## <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

オブジェクトの追加と、ホストへのイベントの送信

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>説明

この関数は、PIMA クラスがオブジェクトを追加し、ホストに通知する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター
- **object_handle**: オブジェクトのハンドル。

### <a name="example"></a>例

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

アプリケーションからのオブジェクト番号の取得

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>説明

この関数は、PIMA クラスがローカル システム内のオブジェクト数を取得し、ホストに送り返す必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター
- **object_number**: 返されるオブジェクト数のアドレス

### <a name="example"></a>例

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a>ux_device_class_pima_object_handles_get

オブジェクト ハンドル配列を返します

### <a name="prototype"></a>プロトタイプ

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>説明

この関数は、PIMA クラスがローカル システム内のオブジェクト ハンドル配列を取得し、ホストに送り返す必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **object_handles_format_code**: ハンドルの表示形式コード
- **object_handles_association**: オブジェクトの関連付けコード
- **object_handle_array**: ハンドルを格納する場所のアドレス
- **object_handles_max_number**: 配列内のハンドルの最大数

### <a name="example"></a>例

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

## <a name="ux_device_class_pima_object_info_get"></a>ux_device_class_pima_object_info_get

オブジェクト情報を返します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>説明

この関数は、PIMA クラスがローカル システム内のオブジェクト ハンドル配列を取得し、ホストに送り返す必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **object_handles**: オブジェクトのハンドル
- **object**: オブジェクト ポインターのアドレス

### <a name="example"></a>例

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

## <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

オブジェクト データを返します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a>説明

この関数は、PIMA クラスがローカル システム内のオブジェクト データを取得し、ホストに送り返す必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **object_handle**: オブジェクトのハンドル
- **object_buffer**: オブジェクト バッファー アドレス
- **object_length_requested**: クライアントからアプリケーションに対して要求されたオブジェク トデータの長さ
- **object_actual_length**: アプリケーションによって返されたオブジェクト データの長さ

### <a name="example"></a>例

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

## <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

ホストがオブジェクト情報を送信します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>説明

この関数は、PIMA クラスが、今後のストレージ用にローカル システム内のオブジェクト情報を受け取る必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター
- **object**: オブジェクトへのポインター
- **object_handle**: オブジェクトのハンドル

### <a name="example"></a>例

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

## <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

ホストがオブジェクト データを送信します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a>説明

この関数は、PIMA クラスが、ストレージ用にローカル システム内のオブジェクト データを受け取る必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター
- **object_handle**: オブジェクトのハンドル
- **phase**: 転送のフェーズ (アクティブまたは完了)
- **object_buffer**: オブジェクト バッファー アドレス
- **object_offset**: データのアドレス
- **object_length**: アプリケーションによって送信されたオブジェクト データの長さ

### <a name="example"></a>例

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

## <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

ローカル オブジェクトを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a>説明

この関数は、PIMA クラスがローカル ストレージ上のオブジェクトを削除する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター
- **object_handle**: オブジェクトのハンドル

### <a name="example"></a>例

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>USB デバイス Audio クラス

USB デバイス Audio クラスにより、USB ホスト システムが、オーディオ デバイスとしてデバイスと通信できるようになります。 このクラスは、USB 標準および USB Audio クラス 1.0 または2.0 標準に基づいています。

USB Audio 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。 Audio 2.0 スピーカーの例を次に示します。

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

Audio クラスは、複合デバイス フレームワークを使用して、インターフェイス (コントロールとストリーミング) をグループ化します。 そのため、デバイス記述子を定義するときは注意が必要です。 USBX は IAD 記述子を使用して、インターフェイスのバインド方法を内部で認識します。 IAD 記述子は、インターフェイスの前に宣言する必要があり (AudioControl インターフェイスの後に 1 つ以上の AudioStreaming インターフェイスが続きます)、Audio クラスの最初のインターフェイス (AudioControl インターフェイス) と、アタッチされているインターフェイスの数が含まれています。

Audio クラスの動作は、デバイスがオーディオを送信するか受信するかによって異なりますが、どちらの場合も、オーディオ フレーム バッファーの格納に FIFO が使用されます。デバイスがホストにオーディオを送信している場合は、アプリケーションが、オーディオ フレーム バッファーを FIFO に追加し、これが後で USBX によってホストに送信されます。デバイスがホストからオーディオを受信している場合は、USBX が、ホストから受信したオーディオ フレーム バッファーを FIFO に追加し、これが後でアプリケーションによって読み取られます。 各オーディオ ストリームには独自の FIFO があり、各オーディオ フレーム バッファーは複数のサンプルで構成されています。

Audio クラスの初期化には、次の部分が必要です。

1. Audio クラスには、次のストリーミング パラメーターが必要です。

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

2. Audio クラスには、次の関数パラメーターが必要です。

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

   アプリケーションで定義された制御要求コールバック (前の例で設定された ***ux_device_class_audio_control_process***) は、スタックがホストから制御要求を受け取ったときに呼び出されます。 要求が受け入れられ、処理 (確認または停止) された場合、コールバックは成功を返す必要があります。それ以外の場合は、エラーが返されます。

   クラス固有の制御要求プロセスは、アプリケーション定義のコールバックとして定義されます。これは、制御要求が USB Audio バージョンによって大きく異なり、要求プロセスの大部分がデバイス フレームワークに関連するためです。 アプリケーションは、デバイスを動作させるために、要求を正しく処理する必要があります。

   オーディオ デバイスの場合、ボリューム、ミュート、およびサンプリング頻度は一般的な制御要求であるため、さまざまな USB オーディオ バージョン用の内部定義されたシンプルなコールバックが、アプリケーションの後のセクション内で使用されるように導入されています。 詳細については、***ux_device_class_audio10_control_process** _ および _ *_ux_device_class_audio_control_request_** をご覧ください。

Audio デバイスのデバイス フレームワーク内で、PID/VID はデバイス記述子に格納されます (上記の宣言されたデバイス記述子を参照)。

USB ホスト システムによって USB Audio デバイスが検出され、Audio クラスがマウントされている場合、デバイスは、任意のオーディオ プレーヤーまたはレコーダー (フレームワークによって異なります) と共に使用できます。 詳細については、「ホスト オペレーティング システム」をご覧ください。

Audio クラス API は以下のように定義されます。

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Audio 関数のデータを読み取るためのスレッド エントリ。

### <a name="prototype"></a>プロトタイプ

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>説明

この関数は、ホストからのオーディオの読み取りが必要な場合に、オーディオ ストリーム初期化パラメーターに渡されます。 内部的には、スレッドがこの関数によってエントリ関数として作成され、スレッド自体は、Audio 関数内のアイソクロナス OUT エンドポイントを介してオーディオ データを読み取ります。

### <a name="parameters"></a>パラメーター

- **audio_stream**: オーディオ ストリーム インスタンスへのポインター。

### <a name="example"></a>例

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Audio 関数のデータ書き込むためのスレッド エントリ

### <a name="prototype"></a>プロトタイプ

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>説明

この関数は、ホストへのオーディオの書き込みが必要な場合に、オーディオ ストリーム初期化パラメーターに渡されます。 内部的には、スレッドがこの関数によってエントリ関数として作成され、スレッド自体は、Audio 関数内のアイソクロナス IN エンドポイントを介してオーディオ データを書き込みます。

### <a name="parameters"></a>パラメーター

- **audio_stream**: オーディオ ストリーム インスタンスへのポインター。

### <a name="example"></a>例

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Audio 関数の特定のストリーム インスタンスを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>説明

この関数は、Audio クラスのストリームインスタンスを取得するために使用されます。

### <a name="parameters"></a>パラメーター

- **audio**: オーディオ インスタンスへのポインター
- **stream_index**: 0 に基づくストリーム インスタンス インデックス
- **stream**: オーディオ ストリーム インスタンス ポインターを格納するバッファーへのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

オーディオ ストリームのオーディオ データの受信を開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>説明

この関数は、オーディオ ストリーム内でのオーディオ データの読み取りを開始するために使用されます。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

オーディオ ストリームから 8 ビットのサンプルを読み取ります

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>説明

この関数は、指定したストリームから 8 ビットのオーディオ サンプル データを読み取ります。

具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。 オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **buffer**: サンプル バイトが保存されるバッファーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

オーディオ ストリームから 16 ビットのサンプルを読み取ります

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>説明

この関数は、指定したストリームから 16 ビットのオーディオ サンプル データを読み取ります。

具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。 オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **buffer**: 16 ビットのサンプルが保存されるバッファーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

オーディオ ストリームから 24 ビットのサンプルを読み取ります

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>説明

この関数は、指定したストリームから 24 ビットのオーディオ サンプル データを読み取ります。

具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。 オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **buffer**: 3 バイトのサンプルが保存されるバッファーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

オーディオ ストリームから 32 ビットのサンプルを読み取ります

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>説明

この関数は、指定したストリームから 32 ビットのオーディオ サンプル データを読み取ります。

具体的には、FIFO 内の現在のオーディオ フレーム バッファーからサンプル データを読み取ります。 オーディオ フレームの最後のサンプルの読み取りが完了すると、フレームは自動的に解放されるため、これを使用して、ホストからより多くのデータを受け入れられるようになります。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **buffer**: 4 バイトのデータが保存されるバッファーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

オーディオ ストリーム内のオーディオ フレームにアクセスします

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>説明

この関数は、指定したストリームの FIFO 内の最初のオーディオ フレーム バッファーとその長さを返します。 アプリケーションによるデータの処理が完了したら、ux_device_class_audio_read_frame_free を使用して、FIFO 内のフレーム バッファーを解放する必要があります。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **frame_data**: データ ポインターを返すデータ ポインターへのポインター。
- **frame_length**: フレームの長さがバイト単位で保存されるバッファーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

オーディオ ストリーム内のオーディオ フレーム バッファーを解放します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>説明

この関数は、ホストからデータを受信できるように、指定したストリームの FIFO の前にあるオーディオ フレーム バッファーを解放します。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

オーディオ ストリームのオーディオ データ転送を開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>説明

この関数は、Audio クラス内での FIFO に書き込まれたオーディオ データの送信を開始するために使用されます。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

オーディオ フレームをオーディオ ストリームに書き込みます

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>説明

この関数は、フレームをオーディオ ストリームの FIFO に書き込みます。 フレーム データは、ホストに送信できるように、FIFO 内の使用可能なバッファーにコピーされます。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **frame**: フレーム データへのポインター。
- **frame_length**: フレームの長さ (バイト数)。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

オーディオ ストリーム内のオーディオ フレームにアクセスします

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>説明

この関数は、FIFO の最後のオーディオ フレーム バッファーのアドレスを取得します。また、オーディオ フレーム バッファーの長さも取得します。 アプリケーションによるオーディオ フレーム バッファーへの必要なデータ入力が完了したら、***ux_device_class_audio_write_frame_commit*** を使用して、フレーム バッファーを FIFO に追加/コミットする必要があります。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **frame_data**: フレーム データ ポインターを返すフレーム データ ポインターへのポインター。
- **frame_length**: フレームの長さがバイト単位で保存されるバッファーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

オーディオ ストリーム内のオーディオ フレーム バッファーをコミットします。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>説明

この関数は、最後のオーディオ フレーム バッファーを FIFO に追加/コミットし、バッファーをホストに転送できるようにします。最後のオーディオ フレーム バッファーは、ux_device_class_write_frame_get によって入力されている必要があることに注意してください。

### <a name="parameters"></a>パラメーター

- **stream**: オーディオ ストリーム インスタンスへのポインター。
- **length**: バッファー内で準備ができているバイト数。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) インターフェイスがダウンしています。
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO バッファーがいっぱいです。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

USB Audio 1.0 制御要求を処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>説明

この関数は、USB Audio 1.0 固有の種類を使用して、制御エンドポイント上のホストによって送信された基本要求を管理します。

音量およびミュート要求の Audio 1.0 機能が、関数内で処理されます。 要求の処理中、最後のパラメーター (group) によって渡された事前定義済みデータが、要求に応答し、制御の変更を格納するために使用されます。

### <a name="parameters"></a>パラメーター

- **audio**: オーディオ インスタンスへのポインター。
- **transfer**: 転送要求インスタンスへのポインター。
- **group**: 要求プロセスのデータ グループ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

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

## <a name="ux_device_class_audio20_control_process"></a>ux_device_class_audio20_control_process

USB Audio 1.0 制御要求を処理します

### <a name="prototype"></a>プロトタイプ
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>説明

この関数は、USB Audio 2.0 固有の種類を使用して、制御エンドポイント上のホストによって送信された基本要求を管理します。

Audio 2.0 サンプリング レート (単一の固定周波数を想定) と、音量およびミュート要求の機能が、関数内で処理されます。 要求の処理中、最後のパラメーター (group) によって渡された事前定義済みデータが、要求に応答し、制御の変更を格納するために使用されます。

### <a name="parameters"></a>パラメーター

- **audio**: オーディオ インスタンスへのポインター。
- **transfer**: 転送要求インスタンスへのポインター。
- **group**: 要求プロセスのデータ グループ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

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
