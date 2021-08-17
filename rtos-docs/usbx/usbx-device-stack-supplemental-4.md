---
title: 第 4 章 - USBX Pictbridge の実装
description: USBX は、デバイスとホストの両方で Pictbridge の完全な実装をサポートしています。 どちら側でも、Pictbridge は USBX PIMA クラス上に配置されます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5a1bab2cb60ce5df6c0662eb1a31f542a3b1d7a87d4584d485cbd621e3342abc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791119"
---
# <a name="chapter-4---usbx-pictbridge-implementation"></a>第 4 章 - USBX Pictbridge の実装

USBX は、ホストとデバイスの両方で Pictbridge の完全な実装をサポートしています。 どちら側でも、Pictbridge は USBX PIMA クラス上に配置されます。

PictBridge 標準では、PC を使用せずにデジタル スチル カメラまたはスマート フォンを直接プリンターに接続できるので、特定の Pictbridge 対応プリンターに直接印刷できます。

カメラまたはスマート フォンがプリンターに接続されると、プリンターは USB ホストとなり、カメラは USB デバイスとなります。 ただし、Pictbridge では、カメラはホストとして表示され、コマンドはカメラから実行されます。 カメラはストレージ サーバーであり、プリンターはストレージ クライアントです。 カメラはプリント クライアントであり、プリンターはもちろんプリント サーバーです。

Pictbridge は、トランスポート層として USB を使用しますが、通信プロトコルとしては PTP (Picture Transfer Protocol) に依存します。

印刷ジョブが発生したときの DPS クライアントと DPS サーバー間のコマンドと応答を、次の図に示します。

![DPS コマンドと応答](./media/usbx-device-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>Pictbridge クライアントの実装

クライアント上の Pictbridge には、USBX デバイス スタックが必要です。また、PIMA クラスを最初に実行する必要があります。

デバイス フレームワークでは、PIMA クラスを次のように記述します。

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
    0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,
    /* Configuration descriptor */
    0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

PIMA クラスでは ID フィールド 0x06 を使用しており、そのサブクラスは静止画像用の 0x01、プロトコルは PIMA 15740 用の 0x01 となっています。

このクラスでは、データの送受信用に 2 つのバルク エンドポイント、イベント用に 1 つの割り込みエンドポイントの、合計 3 つのエンドポイントが定義されています。

他の USBX デバイスの実装とは異なり、Pictbridge アプリケーションではクラス自体を定義する必要はありません。 代わりに、関数 ***ux_pictbridge_dpsclient_start*** を呼び出します。 次に例を示します。

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "ExpressLogic",13);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

Pictbridge クライアントに渡されるパラメーターは次のとおりです。

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no
    : String of serial number
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

次の手順では、デバイスとホストを同期させ、情報を交換できるようにします。

そのために、次のようにイベント フラグを待機します。

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get(&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR,
    &actual_flags, UX_PICTBRIDGE_EVENT_TIMEOUT);
```

状態機械が **DISCOVERY_COMPLETE** 状態の場合、カメラ側 (DPS クライアント) はプリンターとその機能に関する情報を収集します。

DPS クライアントが印刷ジョブを受け入れる準備ができている場合は、その状態が **UX_PICTBRIDGE_NEW_JOB_TRUE** に設定されます。 これは次のように確認できます。

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)
/* We can print something … */
```

次に、いくつかの印刷ジョブ記述子に以下のように入力する必要があります。

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo -> ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo -> ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo -> ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo -> ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */
printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object -> ux_device_class_pima_object_compressed_size = IMAGE_LEN;
object -> ux_device_class_pima_object_offset = 0;
object -> ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object -> ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

これで、Pictbridge クライアントに実行する印刷ジョブが渡されたので、フィールドで定義されているコールバックを介して、アプリケーションから一度にイメージ ブロックをフェッチします。

```C
jobinfo -> ux_pictbridge_jobinfo_object_data_read
```

その関数のプロトタイプは次のように定義されます。

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

印刷用にユーザー領域からデータ ブロックをコピーする

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_pictbridge_jobinfo_object_data_read( 
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,  
    ULONG object_offset,  
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>説明

この関数は、DPS クライアントがターゲットの Pictbridge プリンターに印刷するデータ ブロックを取得する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pictbridge**: Pictbridge クラス インスタンスへのポインター。
- **object_buffer**: オブジェクト バッファーへのポインター
- **object_offset**: データ ブロックの読み取りを始める場所
- **object_length**: 返される長さ
- **actual_length**: 実際に返された長さ

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0x01) アプリケーションがデータを取得できませんでした。

### <a name="example"></a>例

```C
/* Copy the object data. */
UINT ux_demo_object_data_copy(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);
    /* Update the actual length. */
    *actual_length = object_length;
    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a>Pictbridge ホストの実装

Pictbridge のホスト実装は、クライアントとは異なります。

Pictbridge ホスト環境で最初に行うのは、次の例に示すように PIMA クラスを登録することです。

```C
status = ux_host_stack_class_register(_ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

このクラスは、USB スタックと Pictbridge レイヤーの間にある汎用 PTP レイヤーです。

次に、印刷サービス用の Pictbridge の既定値を以下のように初期化します。

| Pictbridge フィールド       | 値                                  |
|------------------------|----------------------------------------|
| DpsVersion[0]          | 0x00010000                             |
| DpsVersion[1]          | 0x00010001                             |
| DpsVersion[2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| PrintServiceAvailable  | 0x30010000                             |
| Qualities[0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Qualities[1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Qualities[2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Qualities[3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| PaperSizes[0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| PaperSizes[1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| PaperSizes[2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| PaperSizes[3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| PaperSizes[4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| PaperTypes[0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| PaperTypes[1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| PaperTypes[2]           | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| FileTypes[0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| FileTypes[1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| FileTypes[2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| FileTypes[3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DatePrints[0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DatePrints[1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DatePrints[2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints[0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints[1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints[2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimizes[0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimizes[1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimizes[2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Layouts[0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Layouts[1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Layouts[2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Layouts[3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| FixedSizes[0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| FixedSizes[1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| FixedSizes[2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| FixedSizes[3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| FixedSizes[4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| FixedSizes[5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| FixedSizes[6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Croppings[0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Croppings[1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Croppings[2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

DPS ホストの状態機械はアイドルに設定され、新しい印刷ジョブを受け入れる準備が整います。

次の例に示すように、Pictbridge のホスト部分を開始できるようになりました。

```C
/* Activate the pictbridge dpshost. */
status = ux_pictbridge_dpshost_start(&pictbridge, pima);

if (status != UX_SUCCESS)
    return;
```

データを印刷する準備が整ったら、Pictbridge ホスト関数にはコールバックが必要になります。 これは、次のように pictbridge ホスト構造体に関数ポインターを渡すことで実現します。

```C
/* Set a callback when an object is being received. */
pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

この関数には、次のプロパティがあります。

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

印刷用にデータ ブロックを書き込む

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge, 
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>説明

この関数は、ローカル プリンターに印刷するために DPS サーバーが DPS クライアントからデータ ブロックを取得する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **pictbridge**: Pictbridge クラス インスタンスへのポインター。
- **object_buffer**: オブジェクト バッファーへのポインター
- **object_offset**: データ ブロックの読み取りを始める場所
- **total_length**: オブジェクトの全長
- **length**: このバッファーの長さ

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) この操作は成功しました。
- **UX_ERROR** (0x01) アプリケーションがデータを印刷できませんでした。

### <a name="example"></a>例

```C
/* Copy the object data. */
UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;
    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
