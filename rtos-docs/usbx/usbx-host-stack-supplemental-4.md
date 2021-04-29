---
title: USBX Pictbridge の実装
description: USBX は、ホストとデバイスの両方で Pictbridge の完全な実装をサポートしています。 どちら側でも、Pictbridge は USBX PIMA クラス上に配置されます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ce291f794cbc458d402cbefa3fd81dcc6f371b57
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812854"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a><span data-ttu-id="939d1-104">第 4 章: USBX Pictbridge の実装</span><span class="sxs-lookup"><span data-stu-id="939d1-104">Chapter 4: USBX Pictbridge implementation</span></span>

<span data-ttu-id="939d1-105">USBX は、ホストとデバイスの両方で Pictbridge の完全な実装をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="939d1-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="939d1-106">どちら側でも、Pictbridge は USBX PIMA クラス上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span> 

<span data-ttu-id="939d1-107">PictBridge 標準では、PC を使用せずにデジタル スチル カメラまたはスマート フォンを直接プリンターに接続できるので、特定の Pictbridge 対応プリンターに直接印刷できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="939d1-108">カメラまたはスマート フォンがプリンターに接続されると、プリンターは USB ホストとなり、カメラは USB デバイスとなります。</span><span class="sxs-lookup"><span data-stu-id="939d1-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="939d1-109">ただし、Pictbridge では、カメラはホストとして表示され、コマンドはカメラから実行されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="939d1-110">カメラはストレージ サーバーであり、プリンターはストレージ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="939d1-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="939d1-111">カメラはプリント クライアントであり、プリンターは (もちろん) プリント サーバーです。</span><span class="sxs-lookup"><span data-stu-id="939d1-111">The camera is the print client and the printer is, of course, the print server.</span></span>

<span data-ttu-id="939d1-112">Pictbridge は、トランスポート層として USB を使用しますが、通信プロトコルとしては PTP (Picture Transfer Protocol) に依存します。</span><span class="sxs-lookup"><span data-stu-id="939d1-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="939d1-113">印刷ジョブが発生したときの DPS クライアントと DPS サーバー間のコマンドと応答を、次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="939d1-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs.</span></span>

![印刷ジョブが発生したときの DPS クライアントと DPS サーバー間のコマンドと応答の図。](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="939d1-115">Pictbridge クライアントの実装</span><span class="sxs-lookup"><span data-stu-id="939d1-115">Pictbridge client implementation</span></span>

<span data-ttu-id="939d1-116">クライアント上の Pictbridge には、USBX デバイス スタックが必要です。また、PIMA クラスを最初に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="939d1-117">デバイス フレームワークでは、PIMA クラスを次のように記述します。</span><span class="sxs-lookup"><span data-stu-id="939d1-117">A device framework describes the PIMA class in the following way.</span></span>

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

<span data-ttu-id="939d1-118">PIMA クラスでは ID フィールド 0x06 を使用しており、そのサブクラスは静止画像用の 0x01、プロトコルは PIMA 15740 用の 0x01 となっています。</span><span class="sxs-lookup"><span data-stu-id="939d1-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="939d1-119">このクラスでは、データの送受信用に 2 つのバルク エンドポイント、イベント用に 1 つの割り込みエンドポイントの、合計 3 つのエンドポイントが定義されています。</span><span class="sxs-lookup"><span data-stu-id="939d1-119">3 endpoints are defined in this class, 2 bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="939d1-120">他の USBX デバイスの実装とは異なり、Pictbridge アプリケーションではクラス自体を定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="939d1-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="939d1-121">代わりに、関数 ***ux_pictbridge_dpsclient_start*** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="939d1-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="939d1-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="939d1-122">An example is below:</span></span>

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "Azure RTOS",10);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.
    ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="939d1-123">Pictbridge クライアントに渡されるパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="939d1-123">The parameters passed to the pictbridge client are as follows:</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="939d1-124">次の手順では、デバイスとホストを同期させ、情報を交換できるようにします。</span><span class="sxs-lookup"><span data-stu-id="939d1-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="939d1-125">そのために、次のようにイベント フラグを待機します。</span><span class="sxs-lookup"><span data-stu-id="939d1-125">This is done by waiting on an event flag as follows:</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="939d1-126">状態機械が **DISCOVERY_COMPLETE** 状態の場合、カメラ側 (DPS クライアント) ではプリンターとその機能に関する情報が収集されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="939d1-127">DPS クライアントが印刷ジョブを受け入れる準備ができている場合は、その状態が **UX_PICTBRIDGE_NEW_JOB_TRUE** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="939d1-128">これは次のように確認できます。</span><span class="sxs-lookup"><span data-stu-id="939d1-128">It can be checked below:</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

<span data-ttu-id="939d1-129">次に、いくつかの印刷ジョブ記述子に以下のように入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="939d1-129">Next some print joib descriptors need to be filled as follows:</span></span>

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo ->ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo ->ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo ->ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo ->ux_pictbridge_jobinfo_object_data_read =
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
object ->ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object ->ux_device_class_pima_object_compressed_size = IMAGE_LEN; object ->ux_device_class_pima_object_offset = 0;
object ->ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object ->ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

<span data-ttu-id="939d1-130">これで、Pictbridge クライアントに実行する印刷ジョブが渡されたので、フィールドで定義されているコールバックを介して、アプリケーションから一度にイメージ ブロックをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="939d1-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field.</span></span>

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="939d1-131">その関数のプロトタイプは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-131">The prototype of that function is defined as follows.</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="939d1-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="939d1-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="939d1-133">印刷用にユーザー領域からデータ ブロックをコピーします。</span><span class="sxs-lookup"><span data-stu-id="939d1-133">Copying a block of data from user space for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="939d1-134">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="939d1-134">Prototype</span></span>

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="939d1-135">説明</span><span class="sxs-lookup"><span data-stu-id="939d1-135">Description</span></span>

<span data-ttu-id="939d1-136">この関数は、DPS クライアントがターゲットの Pictbridge プリンターに印刷するデータ ブロックを取得する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="939d1-137">パラメーター</span><span class="sxs-lookup"><span data-stu-id="939d1-137">Parameters</span></span>

- <span data-ttu-id="939d1-138">**pictbridge**: Pictbridge クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="939d1-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="939d1-139">**object_buffer**: オブジェクト バッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="939d1-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="939d1-140">**object_offset**: データ ブロックの読み取りを始める場所</span><span class="sxs-lookup"><span data-stu-id="939d1-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="939d1-141">**object_length**: 返される長さ</span><span class="sxs-lookup"><span data-stu-id="939d1-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="939d1-142">**actual_length**: 実際に返された長さ</span><span class="sxs-lookup"><span data-stu-id="939d1-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="939d1-143">戻り値</span><span class="sxs-lookup"><span data-stu-id="939d1-143">Return Value</span></span>

- <span data-ttu-id="939d1-144">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="939d1-144">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="939d1-145">**UX_ERROR**: (0x01) アプリケーションがデータを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="939d1-145">**UX_ERROR**: (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="939d1-146">例</span><span class="sxs-lookup"><span data-stu-id="939d1-146">Example</span></span>

```C
/* Copy the object data. */

UINT ux_demo_object_data_copy(UX_PICTBRIDGE *pictbridge,UCHAR *object_buffer,
    ULONG object_offset, ULONG object_length, ULONG *actual_length)
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

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="939d1-147">Pictbridge ホストの実装</span><span class="sxs-lookup"><span data-stu-id="939d1-147">Pictbridge host implementation</span></span>

<span data-ttu-id="939d1-148">Pictbridge のホスト実装は、クライアントとは異なります。</span><span class="sxs-lookup"><span data-stu-id="939d1-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="939d1-149">Pictbridge ホスト環境で最初に行うのは、次の例に示すように PIMA クラスを登録することです。</span><span class="sxs-lookup"><span data-stu-id="939d1-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="939d1-150">このクラスは、USB ホスト スタックと Pictbridge レイヤーの間にある汎用 PTP レイヤーです。</span><span class="sxs-lookup"><span data-stu-id="939d1-150">This class is the generic PTP layer sitting between the USB host stack and the Pictbridge layer.</span></span>

<span data-ttu-id="939d1-151">次に、印刷サービス用の Pictbridge の既定値を以下のように初期化します。</span><span class="sxs-lookup"><span data-stu-id="939d1-151">The next step is to initialize the Pictbridge default values for print services as follows.</span></span>

| <span data-ttu-id="939d1-152">Pictbridge フィールド</span><span class="sxs-lookup"><span data-stu-id="939d1-152">Pictbridge field</span></span>       | <span data-ttu-id="939d1-153">値</span><span class="sxs-lookup"><span data-stu-id="939d1-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="939d1-154">DpsVersion[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-154">DpsVersion[0]</span></span>          | <span data-ttu-id="939d1-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="939d1-155">0x00010000</span></span>                             |
| <span data-ttu-id="939d1-156">DpsVersion[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-156">DpsVersion[1]</span></span>          | <span data-ttu-id="939d1-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="939d1-157">0x00010001</span></span>                             |
| <span data-ttu-id="939d1-158">DpsVersion[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-158">DpsVersion[2]</span></span>          | <span data-ttu-id="939d1-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="939d1-159">0x00000000</span></span>                             |
| <span data-ttu-id="939d1-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="939d1-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="939d1-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="939d1-161">0x00010000</span></span>                             |
| <span data-ttu-id="939d1-162">PrintServiceAvailable</span><span class="sxs-lookup"><span data-stu-id="939d1-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="939d1-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="939d1-163">0x30010000</span></span>                             |
| <span data-ttu-id="939d1-164">Qualities[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-164">Qualities[0]</span></span>           | <span data-ttu-id="939d1-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="939d1-166">Qualities[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-166">Qualities[1]</span></span>           | <span data-ttu-id="939d1-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="939d1-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="939d1-168">Qualities[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-168">Qualities[2]</span></span>           | <span data-ttu-id="939d1-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="939d1-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="939d1-170">Qualities[3]</span><span class="sxs-lookup"><span data-stu-id="939d1-170">Qualities[3]</span></span>           | <span data-ttu-id="939d1-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="939d1-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="939d1-172">PaperSizes[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-172">PaperSizes[0]</span></span>          | <span data-ttu-id="939d1-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="939d1-174">PaperSizes[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-174">PaperSizes[1]</span></span>          | <span data-ttu-id="939d1-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="939d1-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="939d1-176">PaperSizes[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-176">PaperSizes[2]</span></span>          | <span data-ttu-id="939d1-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="939d1-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="939d1-178">PaperSizes[3]</span><span class="sxs-lookup"><span data-stu-id="939d1-178">PaperSizes[3]</span></span>          | <span data-ttu-id="939d1-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="939d1-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="939d1-180">PaperSizes[4]</span><span class="sxs-lookup"><span data-stu-id="939d1-180">PaperSizes[4]</span></span>          | <span data-ttu-id="939d1-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="939d1-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="939d1-182">PaperTypes[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-182">PaperTypes[0]</span></span>          | <span data-ttu-id="939d1-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="939d1-184">PaperTypes[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-184">PaperTypes[1]</span></span>          | <span data-ttu-id="939d1-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="939d1-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="939d1-186">PaperTypes[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-186">PaperTypes[2]</span></span>          | <span data-ttu-id="939d1-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="939d1-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="939d1-188">FileTypes[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-188">FileTypes[0]</span></span>           | <span data-ttu-id="939d1-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="939d1-190">FileTypes[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-190">FileTypes[1]</span></span>           | <span data-ttu-id="939d1-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="939d1-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="939d1-192">FileTypes[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-192">FileTypes[2]</span></span>           | <span data-ttu-id="939d1-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="939d1-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="939d1-194">FileTypes[3]</span><span class="sxs-lookup"><span data-stu-id="939d1-194">FileTypes[3]</span></span>           | <span data-ttu-id="939d1-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="939d1-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="939d1-196">DatePrints[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-196">DatePrints[0]</span></span>          | <span data-ttu-id="939d1-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="939d1-198">DatePrints[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-198">DatePrints[1]</span></span>          | <span data-ttu-id="939d1-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="939d1-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="939d1-200">DatePrints[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-200">DatePrints[2]</span></span>          | <span data-ttu-id="939d1-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="939d1-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="939d1-202">FileNamePrints[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="939d1-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="939d1-204">FileNamePrints[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="939d1-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="939d1-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="939d1-206">FileNamePrints[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="939d1-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="939d1-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="939d1-208">ImageOptimizes[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="939d1-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="939d1-210">ImageOptimizes[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="939d1-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="939d1-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="939d1-212">ImageOptimizes[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="939d1-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="939d1-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="939d1-214">Layouts[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-214">Layouts[0]</span></span>             | <span data-ttu-id="939d1-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="939d1-216">Layouts[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-216">Layouts[1]</span></span>             | <span data-ttu-id="939d1-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="939d1-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="939d1-218">Layouts[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-218">Layouts[2]</span></span>             | <span data-ttu-id="939d1-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="939d1-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="939d1-220">Layouts[3]</span><span class="sxs-lookup"><span data-stu-id="939d1-220">Layouts[3]</span></span>             | <span data-ttu-id="939d1-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="939d1-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="939d1-222">FixedSizes[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-222">FixedSizes[0]</span></span>          | <span data-ttu-id="939d1-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="939d1-224">FixedSizes[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-224">FixedSizes[1]</span></span>          | <span data-ttu-id="939d1-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="939d1-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="939d1-226">FixedSizes[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-226">FixedSizes[2]</span></span>          | <span data-ttu-id="939d1-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="939d1-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="939d1-228">FixedSizes[3]</span><span class="sxs-lookup"><span data-stu-id="939d1-228">FixedSizes[3]</span></span>          | <span data-ttu-id="939d1-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="939d1-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="939d1-230">FixedSizes[4]</span><span class="sxs-lookup"><span data-stu-id="939d1-230">FixedSizes[4]</span></span>          | <span data-ttu-id="939d1-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="939d1-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="939d1-232">FixedSizes[5]</span><span class="sxs-lookup"><span data-stu-id="939d1-232">FixedSizes[5]</span></span>          | <span data-ttu-id="939d1-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="939d1-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="939d1-234">FixedSizes[6]</span><span class="sxs-lookup"><span data-stu-id="939d1-234">FixedSizes[6]</span></span>          | <span data-ttu-id="939d1-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="939d1-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="939d1-236">Croppings[0]</span><span class="sxs-lookup"><span data-stu-id="939d1-236">Croppings[0]</span></span>           | <span data-ttu-id="939d1-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="939d1-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="939d1-238">Croppings[1]</span><span class="sxs-lookup"><span data-stu-id="939d1-238">Croppings[1]</span></span>           | <span data-ttu-id="939d1-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="939d1-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="939d1-240">Croppings[2]</span><span class="sxs-lookup"><span data-stu-id="939d1-240">Croppings[2]</span></span>           | <span data-ttu-id="939d1-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="939d1-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="939d1-242">DPS ホストの状態機械はアイドルに設定され、新しい印刷ジョブを受け入れる準備が整います。</span><span class="sxs-lookup"><span data-stu-id="939d1-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="939d1-243">次の例に示すように、Pictbridge のホスト部分を開始できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="939d1-243">The host portion of Pictbridge can now be started as the example below shows.</span></span>

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="939d1-244">データを印刷する準備が整ったら、Pictbridge ホスト関数にはコールバックが必要になります。</span><span class="sxs-lookup"><span data-stu-id="939d1-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="939d1-245">これは、次のように pictbridge ホスト構造体に関数ポインターを渡すことで実現します。</span><span class="sxs-lookup"><span data-stu-id="939d1-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="939d1-246">この関数には、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="939d1-246">This function has the following properties:</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="939d1-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="939d1-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="939d1-248">印刷用にデータ ブロックを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="939d1-248">Writing a block of data for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="939d1-249">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="939d1-249">Prototype</span></span>

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="939d1-250">説明</span><span class="sxs-lookup"><span data-stu-id="939d1-250">Description</span></span>

<span data-ttu-id="939d1-251">この関数は、ローカル プリンターに印刷するために DPS サーバーが DPS クライアントからデータ ブロックを取得する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="939d1-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="939d1-252">パラメーター</span><span class="sxs-lookup"><span data-stu-id="939d1-252">Parameters</span></span>

- <span data-ttu-id="939d1-253">**pictbridge**: Pictbridge クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="939d1-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="939d1-254">**object_buffer**: オブジェクト バッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="939d1-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="939d1-255">**object_offset**: データ ブロックの読み取りを始める場所</span><span class="sxs-lookup"><span data-stu-id="939d1-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="939d1-256">**total_length**: オブジェクトの全長</span><span class="sxs-lookup"><span data-stu-id="939d1-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="939d1-257">**length**: このバッファーの長さ</span><span class="sxs-lookup"><span data-stu-id="939d1-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="939d1-258">戻り値</span><span class="sxs-lookup"><span data-stu-id="939d1-258">Return Value</span></span>

- <span data-ttu-id="939d1-259">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="939d1-259">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="939d1-260">**UX_ERROR**: (0x01) アプリケーションがデータを印刷できませんでした。</span><span class="sxs-lookup"><span data-stu-id="939d1-260">**UX_ERROR**: (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="939d1-261">例</span><span class="sxs-lookup"><span data-stu-id="939d1-261">Example</span></span>

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
