---
title: 第 5 章 - USBX デバイス クラスに関する考慮事項
description: USBX のデバイス クラスに関する考慮事項について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b8fcfa251df9140d23b50a99f13f2755d2bdfae0ca6b9529633f25e263c7edcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798742"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>第 5 章 - USBX デバイス クラスに関する考慮事項

## <a name="device-class-registration"></a>デバイス クラスの登録

各デバイス クラスは、登録について同じ原則に従います。 特定のクラス パラメーターを含む構造体が、クラス初期化関数に渡されます。

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

必要に応じて、各クラスで、クラスのインスタンスがアクティブ化されたときのコールバック関数を登録できます。 インスタンスが作成されたことをアプリケーションに通知するため、デバイス スタックによってコールバックが呼び出されます。

次の例で示すように、アプリケーションの本体には、アクティブ化と非アクティブ化のための 2 つの関数が含まれます。

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

これらの関数内では何も行わず、クラスのインスタンスを記憶して、アプリケーションの他の部分と同期することだけが推奨されます。

## <a name="general-considerations-for-bulk-transfer"></a>一括転送に関する一般的な考慮事項

USB 2.0 仕様に従って、エンドポイントでは、エンドポイントの報告された wMaxPacketSize 値以下のデータ フィールを含むデータ ペイロードを常に送信する必要があります。 データ パケットのサイズは bMaxPacketSize に制限されています。 転送は、次の場合に完了できます。
1. エンドポイントで、必要なデータ量が正確に転送された場合。
2. デバイスまたはホストのエンドポイントで、最大パケット サイズ (wMaxPacketSize) よりも小さいサイズのパケットが受信された場合。 この短いパケットは、残っているデータ パケットがなくなり、転送が完了したことを示します。または、転送されるデータ パケットがすべて wMaxPacketSize に等しい場合は、転送の終了を特定できません。 転送を完了するために、長さ 0 のパケット (ZLP) を送信する必要があります。短いパケットと長さ 0 のパケットは、一括データ転送の終了を示します。 上記の考慮事項は、生の一括データ転送 API (ux_device_class_cdc_acm_read() など) に適用されます。

## <a name="usb-device-storage-class"></a>USB デバイス ストレージ クラス

USB デバイス ストレージ クラスを使用すると、システムに埋め込まれている記憶装置を USB ホストに認識させることができます。

USB デバイス ストレージ クラス自体によっては、ストレージ ソリューションは提供されません。 ホストからの SCSI 要求を受け入れて解釈するだけです。 これらの要求の 1 つが読み取りまたは書き込みコマンドである場合、ATA デバイス ドライバーやフラッシュ デバイス ドライバーなど、実際の記憶装置ハンドラーに対して事前に定義されたコールバックを呼び出します。

デバイス ストレージ クラスを初期化すると、必要な情報がすべて格納されているクラスにポインター構造が提供されます。 次に例を示します。

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

この例では、ドライバー ストレージ文字列が、対応するパラメーターへの文字列ポインターを割り当てることによって、カスタマイズされています。 文字列ポインターのいずれかが UX_NULL のままになっている場合は、Azure RTOS の既定の文字列が使用されます。

この例では、ドライブの最後のブロック アドレス (LBA) が、論理セクター サイズと共に指定されています。 LBA は、メディアで使用可能なセクターの数から 1 を引いた値です。 通常のストレージ メディアでは、ブロックの長さは 512 に設定されています。 光学ドライブの場合は、2048 に設定できます。

ストレージ クラスでメディアの状態の読み取り、書き込み、取得を行うことができるよう、アプリケーションで 3 つのコールバック関数ポインターを渡す必要があります。

読み取りおよび書き込み関数のプロトタイプの例を次に示します。

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

各値の説明:

- *storage* は、ストレージ クラスのインスタンスです。
- *lun* は、コマンドの送信先の LUN です。
- *data_pointer* は、読み取りまたは書き込みに使用されるバッファーのアドレスです。
- *number_blocks* は、読み取りまたは書き込みを行うセクターの数です。
- *lba* は、読み取るセクターのアドレスです。
- *media_status* には、メディア ステータス コールバックの戻り値を正確に設定する必要があります。

戻り値は、操作の成功または失敗を示す値 UX_SUCCESS または UX_ERROR です。 これらの操作で他のエラー コードを返す必要はありません。 いずれかの操作でエラーが発生した場合は、ストレージ クラスによってステータス コールバック関数が呼び出されます。

この関数のプロトタイプは次のとおりです。

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

呼び出し元パラメーター media_id は現在使用されておらず、常に 0 である必要があります。 今後、複数の記憶装置または複数の SCSI LUN を持つ記憶装置を区別するために使用される可能性があります。 このバージョンのストレージ クラスでは、ストレージ クラスの複数のインスタンスまたは複数の SCSI LUN を持つ記憶装置はサポートされていません。

戻り値の SCSI エラー コードの形式は次のとおりです。

- **ビット 0 - 7**: Sense_key
- **ビット 8 - 15**: その他の意味のあるコード
- **ビット 16 - 23**: その他の意味のあるコードの修飾子

次の表に、可能性のある Sense/ASC/ASCQ の組み合わせを示します。

| Sense キー | ASC | ASCQ | 説明                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | センスなし                                          |
| 01        | 17  | 01   | 再試行で回復されたデータ                       |
| 01        | 18  | 00   | ECC で回復されたデータ                           |
| 02        | 04  | 01   | 論理ドライブの準備ができていない - 準備中          |
| 02        | 04  | 02   | 論理ドライブの準備ができていない - 初期化が必要 |
| 02        | 04  | 04   | 論理ユニットの準備ができていない - フォーマット進行中       |
| 02        | 04  | FF   | 論理ドライブの準備ができていない - デバイスがビジー状態          |
| 02        | 06  | 00   | 参照位置が見つからない                       |
| 02        | 08  | 00   | 論理ユニットの通信エラー                |
| 02        | 08  | 01   | 論理ユニットの通信タイムアウト               |
| 02        | 08  | 80   | 論理ユニットの通信オーバーラン                |
| 02        | 3A  | 00   | メディアが存在しない                                |
| 02        | 54  | 00   | USB からホスト システムへのインターフェイス エラー              |
| 02        | 80  | 00   | リソース不足                            |
| 02        | FF  | FF   | 不明なエラーです                                     |
| 03        | 02  | 00   | シークが完了していない                                  |
| 03        | 03  | 00   | 書き込みエラー                                       |
| 03        | 10  | 00   | ID CRC エラー                                      |
| 03        | 11  | 00   | 回復不可能な読み取りエラー                            |
| 03        | 12  | 00   | ID フィールドのアドレス マークが見つからない               |
| 03        | 13  | 00   | データ フィールドのアドレス マークが見つからない             |
| 03        | 14  | 00   | 記録されたエンティティが見つからない                         |
| 03        | 30  | 01   | メディアを読み取ることができない - 不明な形式               |
| 03        | 31  | 01   | FORMAT コマンド失敗                             |
| 04        | 40  | NN   | コンポーネント NN (80H - FFH) の診断エラー      |
| 05        | 1A  | 00   | パラメーター リスト長エラー                       |
| 05        | 20  | 00   | 無効なコマンド操作コード                    |
| 05        | 21  | 00   | 論理ブロック アドレスが範囲外                |
| 05        | 24  | 00   | コマンド パケットのフィールドが無効                   |
| 05        | 25  | 00   | 論理ユニットがサポートされていない                        |
| 05        | 26  | 00   | パラメーター リストのフィールドが無効                   |
| 05        | 26  | 01   | サポートされていないパラメーター                           |
| 05        | 26  | 02   | 値が無効なパラメーター                           |
| 05        | 39  | 00   | パラメーターの保存はサポートされていない                     |
| 06        | 28  | 00   | 準備完了への移行の準備ができていない - メディアが変更された     |
| 06        | 29  | 00   | 電源オン リセットまたはバス デバイスのリセットが発生した       |
| 06        | 2F  | 00   | 別のイニシエーターによってクリアされたコマンド             |
| 07        | 27  | 00   | 書き込み保護されたメディア                             |
| 0B        | 4E  | 00   | 重複するコマンドが試行された                      |

さらに 2 つのオプションのコールバックをアプリケーションで実装できます。1 つは **GET_STATUS_NOTIFICATION** コマンドに応答するためのもので、もう 1 つは **SYNCHRONIZE_CACHE** コマンドに応答するためのものです。

アプリケーションでホストからの GET_STATUS_NOTIFICATION コマンドを処理する場合は、次のプロトタイプを持つコールバックを実装する必要があります。

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

各値の説明:

- *storage* は、ストレージ クラスのインスタンスです。
- *media_id* は現在使用されていません。 notification_class は、通知のクラスを指定します。
- *media_notification* には、通知への応答が格納されているバッファーをアプリケーションで設定する必要があります。
- *media_notification_length* には、応答バッファーの長さをアプリケーションで設定する必要があります。

戻り値では、コマンドが成功したかどうかが示されます。**UX_SUCCESS** または **UX_ERROR** のいずれかです。

アプリケーションでこのコールバックが実装されていない場合、**GET_STATUS_NOTIFICATION** コマンドを受け取ると、コマンドが実装されていないことが USBX によってホストに通知されます。

ホストからの書き込みのためにアプリケーションでキャッシュが利用されている場合は、**SYNCHRONIZE_CACHE** コマンドを処理する必要があります。 記憶装置が切断されようとしていることをホストが認識した合、ホストによりこのコマンドが送信されることがあります。たとえば、Windows では、ユーザーがツール バーのフラッシュ ドライブ アイコンを右クリックして、[<記憶装置名> の取り出し] を選択すると、Windows によって **SYNCHRONIZE_CACHE** コマンドがそのデバイスに発行されます。

アプリケーションでホストからの **GET_STATUS_NOTIFICATION** コマンドを処理する場合は、次のプロトタイプを持つコールバックを実装する必要があります。

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

各値の説明:

- *storage* は、ストレージ クラスのインスタンスです。
- *lun* パラメーターは、コマンドの送信先の LUN を指定します。
- *number_blocks* は、同期するブロックの数を指定します。
- *lba* は、同期する最初のブロックのセクター アドレスです。
- *media_status* には、メディア ステータス コールバックの戻り値を正確に設定する必要があります。

戻り値では、コマンドが成功したかどうかが示されます。**UX_SUCCESS** または **UX_ERROR** のいずれかです。

### <a name="multiple-scsi-lun"></a>複数の SCSI LUN

USBX デバイス ストレージ クラスでは、複数の LUN がサポートされています。 したがって、同時に CD-ROM とフラッシュ ディスクとして機能する記憶装置を作成することができます。 このような場合、初期化は少し異なります。 フラッシュ ディスクと CD-ROM の例を次に示します。

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a>USB デバイスの CDC-ACM クラス

USB デバイスの CDC-ACM クラスを使用することで、USB ホスト システムは、シリアル デバイスとしてデバイスと通信できます。 このクラスは、USB 規格に基づいており、CDC 標準のサブセットです。

CDC-ACM 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。 例については、以下を参照してください。

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

インターフェイス (制御とデータ) は、CDC-ACM クラスにより、複合デバイス フレームワークを使用してグループ化されます。 そのため、デバイス記述子を定義するときは注意が必要です。 USBX は IAD 記述子を使用して、インターフェイスのバインド方法を内部で認識します。 インターフェイスの前に IAD 記述子を宣言し、CDC-ACM クラスの最初のインターフェイスと、アタッチされるインターフェイスの数を格納する必要があります。

また、CDC-ACM クラスでは、新しい IAD 記述子と同じ機能を実行する結合機能記述子も使用されます。 結合機能記述子は歴史的な理由と、ホスト側との互換性のために宣言する必要がありますが、USBX では使用されません。

CDC-ACM クラスの初期化には、次のパラメーターが必要です。

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

定義されている 2 つのパラメーターは、スタックによってこのクラスがアクティブ化または非アクティブ化されると呼び出される、ユーザー アプリケーションへのコールバック ポインターです。

3 番目に定義されているパラメーターは、ライン コードまたはライン状態のパラメーターが変更されたときに呼び出される、ユーザー アプリケーションへのコールバック ポインターです。 たとえば、ホストから DTR 状態を **TRUE** に変更する要求があると、コールバックが呼び出されます。そのユーザー アプリケーションでは、IOCTL 関数を使用してラインの状態をチェックし、ホストで通信の準備ができていることを確認できます。

CDC-ACM は、USB-IF 規格に基づいており、macOS と Linux のオペレーティング システムによって自動的に認識されます。 Windows 10 より前のバージョンでは、このクラスには .inf ファイルが必要です。 Windows 10 では、.inf ファイルは必要ありません。 CDC-ACM クラス用のテンプレートが用意されており、***usbx_windows_host_files*** ディレクトリにあります。 新しいバージョンの Windows では、CDC_ACM_Template_Win7_64bit.inf ファイルを使用する必要があります (Win10 を除く)。 このファイルを変更して、デバイスによって使用される PID/VID を反映させる必要があります。 この PID/VID は、会社と製品が USB-IF に登録されたときに、最終的な顧客に固有のものになります。 inf ファイル内の変更対象のフィールドを次に示します。

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

CDC-ACM デバイスのデバイス フレームワーク内で、PID/VID はデバイス記述子に格納されます (上記の宣言されたデバイス記述子を参照)。

USB ホスト システムによって USB CDC-ACM デバイスが検出されると、シリアル クラスがマウントされ、任意のシリアル ターミナル プログラムでデバイスを使用できるようになります。 詳細については、ホスト オペレーティング システムを参照してください。

CDC-ACM クラスの API 関数の定義を以下に示します。

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

CDC-ACM インターフェイスで IOCTL を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションで cdc acm インターフェイスに対してさまざまな ioctl 呼び出しを実行する必要がある場合に呼び出されます

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: 実行される ioctl 関数。
- **parameter**: ioctl の呼び出しに固有のパラメーターへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0xFF) 関数からのエラー

### <a name="example"></a>例

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Ioctl 関数:

| Function                                        | 値 |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

CDC-ACM インターフェイスで IOCTL のライン コーディング設定を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションでライン コーディング パラメーターを設定する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parameter**: ライン パラメーター構造体へのポインター:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>戻り値

**UX_SUCCESS** (0x00) この操作は成功しました。

### <a name="example"></a>例

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

CDC-ACM インターフェイスで IOCTL のライン コーディング取得を実行します

### <a name="prototype"></a>プロトタイプ

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションでライン コーディング パラメーターを取得する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING
- **parameter**: ライン パラメーター構造体へのポインター:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。

### <a name="example"></a>例

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

CDC-ACM インターフェイスで IOCTL のライン状態取得を実行します

## <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションでライン状態パラメーターを取得する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parameter**: ライン パラメーター構造体へのポインター:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。

### <a name="example"></a>例

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

CDC-ACM インターフェイスで IOCTL のライン状態設定を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションでライン状態パラメーターを取得する必要がある場合に呼び出されます

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parameter**: ライン パラメーター構造体へのポインター:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。

### <a name="example"></a>例

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

CDC-ACM インターフェイスで IOCTL のパイプ中止を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションでパイプを中止する必要がある場合に呼び出されます。 たとえば、実行中の書き込みを中止するには、UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT をパラメーターとして渡す必要があります。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parameter**: パイプの方向:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) パイプの方向が無効です。

### <a name="example"></a>例

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

CDC-ACM インターフェイスで IOCTL の送信開始を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションによりコールバックで送信を使用する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parameter**: 送信開始パラメーター構造体へのポインター:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0xFF) 送信は既に開始されています。
- **UX_MEMORY_INSUFFICIENT**: (0x12) メモリの割り当てに失敗しました。

### <a name="example"></a>例

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

CDC-ACM インターフェイスで IOCTL の送信停止を実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、アプリケーションによりコールバックでの送信の使用を停止する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parameter**: 使用されていません

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0xFF) 実行中の送信がありません。

### <a name="example"></a>例

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

CDC-ACM パイプから読み取ります

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>説明

この関数は、アプリケーションで OUT データ パイプから読み取る必要があるときに呼び出されます (OUT はホストから、IN はデバイスから)。 ブロッキングです。

> [!Note]
> この関数により、ホストから生の一括データが読み取られます。したがって、バッファーがいっぱいになるか、ホストで短いパケット (長さ 0 のパケットを含む) による転送が終了するまで、保留状態が維持されます。 詳細については、「[**一括転送に関する一般的な考慮事項**](#general-considerations-for-bulk-transfer)」セクションを参照してください。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **buffer**: データが格納されるバッファー アドレス。
- **requested_length**: 予想される最大長。
- **actual_length**: バッファーに返された長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) デバイスは、構成されている状態ではなくなりました。
- **UX_TRANSFER_NO_ANSWER** (0x22) デバイスから応答がありません。 転送の保留中に、デバイスが切断された可能性があります。

### <a name="example"></a>例

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

CDC-ACM パイプに書き込みます

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>説明

この関数は、アプリケーションで IN データ パイプに書き込む必要があるときに呼び出されます (IN はホストから、OUT はデバイスから)。 ブロッキングです。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **buffer**: データが格納されているバッファー アドレス。
- **requested_length**: 書き込むバッファーの長さ。
- **actual_length**: 書き込みが実行された後でバッファーに返された長さ。

### <a name="return-value"></a>戻り値
- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) デバイスは、構成されている状態ではなくなりました。
- **UX_TRANSFER_NO_ANSWER** (0x22) デバイスから応答がありません。 転送の保留中に、デバイスが切断された可能性があります。

### <a name="example"></a>例

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

コールバックで CDC-ACM パイプに書き込みます

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>説明

この関数は、アプリケーションで IN データ パイプに書き込む必要があるときに呼び出されます (IN はホストから、OUT はデバイスから)。 この関数は非ブロッキングであり、完了は UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START で設定されているコールバックを通して行われます。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc クラス インスタンスへのポインター。
- **buffer**: データが格納されているバッファー アドレス。
- **requested_length**: 書き込むバッファーの長さ。
- **actual_length**: 書き込みが実行された後でバッファーに返された長さ

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) デバイスは、構成されている状態ではなくなりました。
- **UX_TRANSFER_NO_ANSWER** (0x22) デバイスから応答がありません。 転送の保留中に、デバイスが切断された可能性があります。

### <a name="example"></a>例

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>USB デバイスの CDC-ECM クラス

USB デバイス CDC-ECM クラスにより、USB ホスト システムが、イーサネット デバイスとしてデバイスと通信できるようになります。 このクラスは、USB 規格に基づいており、CDC 標準のサブセットです。

CDC-ACM 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。 例については、以下を参照してください。

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

CDC-ECM クラスには、CDC-ACM とよく似たデバイス記述子アプローチが採用されており、IAD 記述子も必要です。 定義については、CDC-ACM クラスを参照してください。

通常のデバイス フレームワークに加えて、CDC-ECM には特別な文字列記述子が必要です。 次に例を示します。

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

MAC アドレス文字列記述子は、CDC-ECM クラスによって、デバイスが TCP/IP プロトコルで応答している MAC アドレスに関するホスト クエリに応答するために使用されます。 デバイスで選択したものに設定できますが、ここで定義する必要があります。

CDC-ECM クラスの初期化は次のとおりです。

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

このクラスの初期化では、アクティブ化と非アクティブ化のために同じ関数コールバックが必要ですが、ここでは演習として、コールバックが実行されないように NULL に設定されています。

次のパラメーターは、ノード ID の定義用です。 CDC-ECM には、ローカル ノードとリモート ノードの 2 つのノードが必要です。 ローカル ノードではデバイスの MAC アドレスが指定され、リモート ノードではホストの MAC アドレスが指定されます。 リモート ノードは、デバイス フレームワークの文字列記述子で宣言されているものと同じである必要があります。

CDC-ECM クラスには、両方の方法でデータを転送するための組み込み API が用意されていますが、ユーザー アプリケーションは NetX 経由で USB イーサネット デバイスと通信するため、アプリケーションには表示されません。

USBX CDC-ECM クラスは、Azure RTOS NetX ネットワーク スタックに緊密に関連付けられています。 NetX と USBX の両方の CDC-ECM クラスを使用するアプリケーションは、通常の方法で NetX ネットワークスタックを起動しますが、それに加えて次のように USB ネットワーク スタックをアクティブにする必要があります。

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB ネットワーク スタックは 1 回だけアクティブにする必要があり、CDC-ECM に固有ではありませんが、NetX サービスを必要とするすべての USB クラスで必要になります。

CDC-ECM クラスは、MAC OS と Linux ホストによって認識されます。 ただし、Microsoft Windows からは、CDC-ECM をネイティブに認識するためのドライバーは提供されていません。 一部の商用製品には、Windows プラットフォーム用のものが存在しており、独自の .inf ファイルが提供されています。 このファイルを、USB ネットワーク デバイスの PID/VID と一致するように、CDC-ACM の inf テンプレートと同じ方法で変更する必要があります。

## <a name="usb-device-hid-class"></a>USB デバイスの HID クラス

USB デバイスの HID クラスを使用することで、USB ホスト システムから、特定の HID クライアント機能を持つ HID デバイスに接続できます。

USBX の HID デバイス クラスは、ホスト側と比較して比較的簡単です。 それは、デバイスとその HID 記述子の動作に密接に結び付けられています。

次の例に示すように、HID クライアントでは、最初に HID デバイス フレームワークを定義する必要があります。

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

HID フレームワークには、HID クラスと HID デバイス サブクラスについて記述されているインターフェイス記述子が含まれます。 HID インターフェイスは、スタンドアロン クラスでも複合デバイスの一部でもかまいません。

現在、USBX HID クラスは複数のレポート ID に対応していません。ほとんどのアプリケーションでは、必要な ID は 1 つだけです (ID ゼロ)。 複数のレポート ID の機能に関心がある場合は、お問い合わせください。

HID クラスの初期化は次のようになります。例として USB キーボードを使用しています。

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

アプリケーションでは、HID レポート記述子とその長さを HID クラスに渡す必要があります。 レポート記述子は、デバイスについて記述されている項目のコレクションです。 HID の文法の詳細については、HID USB クラスの仕様を参照してください。

アプリケーションからは、レポート記述子に加えて、HID イベントが発生したときのコールバックを渡します。

ホストからの次の標準 HID コマンドが、USBX HID クラスによってサポートされています。

| [コマンド名]                             | 値 | 説明                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | デバイスからレポートを取得します                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | 割り込みエンドポイントのアイドル周期を取得します |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | デバイスで実行されているプロトコルを取得します           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | デバイスにレポートを設定します                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | 割り込みエンドポイントのアイドル周期を設定します |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | デバイスで実行されているプロトコルを取得します           |

レポートの取得と設定は、ホストとデバイスの間でデータをやり取りするために、HID によって最もよく使用されるコマンドです。 ホストは、ほとんどの場合は制御エンドポイントでデータを送信しますが、割り込みエンドポイントでデータを受信したり、GET_REPORT コマンドを発行して制御エンドポイント上のデータをフェッチしたりすることもできます。

HID クラスの ux_device_class_hid_event_set 関数を使用すると、割り込みエンドポイントでホストにデータを送り返すことができます。

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

HID クラスにイベントを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>説明

この関数は、アプリケーションで HID イベントをホストに返送する必要がある場合に呼び出されます。 この関数はブロッキングではなく、レポートを循環キューに格納するだけで、アプリケーションに制御を戻します。

### <a name="parameters"></a>パラメーター

- **hid**: HID クラス インスタンスへのポインター。
- **hid_event**: HID イベントの構造体へのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0xFF) エラー、循環キューに空き領域がありません。

### <a name="example"></a>例

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

HID クラスの初期化時に定義されたコールバックにより、イベント送信の逆の処理が実行されます。 ホストによって送信されたイベントを入力として取得します。 コールバックのプロトタイプは次のとおりです。

### <a name="hid_callback"></a>hid_callback

HID クラスからイベントを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>説明

この関数は、ホストによって HID レポートがアプリケーションに送信されるときに呼び出されます。

### <a name="parameters"></a>パラメーター

- **hid**: HID クラス インスタンスへのポインター。
- **hid_event**: HID イベントの構造体へのポインター。

### <a name="example"></a>例

次の例では、HID キーボードのイベントを解釈する方法が示されています。

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
