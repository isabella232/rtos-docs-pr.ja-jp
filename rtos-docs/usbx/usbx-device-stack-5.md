---
title: 第 5 章 - USBX デバイス クラスに関する考慮事項
description: USBX のデバイス クラスに関する考慮事項について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811357"
---
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="0a734-103">第 5 章 - USBX デバイス クラスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="0a734-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="0a734-104">デバイス クラスの登録</span><span class="sxs-lookup"><span data-stu-id="0a734-104">Device Class registration</span></span>

<span data-ttu-id="0a734-105">各デバイス クラスは、登録について同じ原則に従います。</span><span class="sxs-lookup"><span data-stu-id="0a734-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="0a734-106">特定のクラス パラメーターを含む構造体が、クラス初期化関数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

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

<span data-ttu-id="0a734-107">必要に応じて、各クラスで、クラスのインスタンスがアクティブ化されたときのコールバック関数を登録できます。</span><span class="sxs-lookup"><span data-stu-id="0a734-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="0a734-108">インスタンスが作成されたことをアプリケーションに通知するため、デバイス スタックによってコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="0a734-109">次の例で示すように、アプリケーションの本体には、アクティブ化と非アクティブ化のための 2 つの関数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a734-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

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

<span data-ttu-id="0a734-110">これらの関数内では何も行わず、クラスのインスタンスを記憶して、アプリケーションの他の部分と同期することだけが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="0a734-111">USB デバイス ストレージ クラス</span><span class="sxs-lookup"><span data-stu-id="0a734-111">USB Device Storage Class</span></span>

<span data-ttu-id="0a734-112">USB デバイス ストレージ クラスを使用すると、システムに埋め込まれている記憶装置を USB ホストに認識させることができます。</span><span class="sxs-lookup"><span data-stu-id="0a734-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="0a734-113">USB デバイス ストレージ クラス自体によっては、ストレージ ソリューションは提供されません。</span><span class="sxs-lookup"><span data-stu-id="0a734-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="0a734-114">ホストからの SCSI 要求を受け入れて解釈するだけです。</span><span class="sxs-lookup"><span data-stu-id="0a734-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="0a734-115">これらの要求の 1 つが読み取りまたは書き込みコマンドである場合、ATA デバイス ドライバーやフラッシュ デバイス ドライバーなど、実際の記憶装置ハンドラーに対して事前に定義されたコールバックを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a734-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="0a734-116">デバイス ストレージ クラスを初期化すると、必要な情報がすべて格納されているクラスにポインター構造が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="0a734-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-117">An example is given below.</span></span>

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

<span data-ttu-id="0a734-118">この例では、ドライバー ストレージ文字列が、対応するパラメーターへの文字列ポインターを割り当てることによって、カスタマイズされています。</span><span class="sxs-lookup"><span data-stu-id="0a734-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="0a734-119">文字列ポインターのいずれかが UX_NULL のままになっている場合は、Azure RTOS の既定の文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="0a734-120">この例では、ドライブの最後のブロック アドレス (LBA) が、論理セクター サイズと共に指定されています。</span><span class="sxs-lookup"><span data-stu-id="0a734-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="0a734-121">LBA は、メディアで使用可能なセクターの数から 1 を引いた値です。</span><span class="sxs-lookup"><span data-stu-id="0a734-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="0a734-122">通常のストレージ メディアでは、ブロックの長さは 512 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="0a734-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="0a734-123">光学ドライブの場合は、2048 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="0a734-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="0a734-124">ストレージ クラスでメディアの状態の読み取り、書き込み、取得を行うことができるよう、アプリケーションで 3 つのコールバック関数ポインターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="0a734-125">読み取りおよび書き込み関数のプロトタイプの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-125">The prototypes for the read and write functions are shown in the example below.</span></span>

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

<span data-ttu-id="0a734-126">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="0a734-126">Where:</span></span>

- <span data-ttu-id="0a734-127">*storage* は、ストレージ クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="0a734-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="0a734-128">*lun* は、コマンドの送信先の LUN です。</span><span class="sxs-lookup"><span data-stu-id="0a734-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="0a734-129">*data_pointer* は、読み取りまたは書き込みに使用されるバッファーのアドレスです。</span><span class="sxs-lookup"><span data-stu-id="0a734-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="0a734-130">*number_blocks* は、読み取りまたは書き込みを行うセクターの数です。</span><span class="sxs-lookup"><span data-stu-id="0a734-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="0a734-131">*lba* は、読み取るセクターのアドレスです。</span><span class="sxs-lookup"><span data-stu-id="0a734-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="0a734-132">*media_status* には、メディア ステータス コールバックの戻り値を正確に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="0a734-133">戻り値は、操作の成功または失敗を示す値 UX_SUCCESS または UX_ERROR です。</span><span class="sxs-lookup"><span data-stu-id="0a734-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="0a734-134">これらの操作で他のエラー コードを返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="0a734-135">いずれかの操作でエラーが発生した場合は、ストレージ クラスによってステータス コールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="0a734-136">この関数のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0a734-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="0a734-137">呼び出し元パラメーター media_id は現在使用されておらず、常に 0 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="0a734-138">今後、複数の記憶装置または複数の SCSI LUN を持つ記憶装置を区別するために使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="0a734-139">このバージョンのストレージ クラスでは、ストレージ クラスの複数のインスタンスまたは複数の SCSI LUN を持つ記憶装置はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="0a734-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="0a734-140">戻り値の SCSI エラー コードの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0a734-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="0a734-141">**ビット 0 - 7**: Sense_key</span><span class="sxs-lookup"><span data-stu-id="0a734-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="0a734-142">**ビット 8 - 15**: その他の意味のあるコード</span><span class="sxs-lookup"><span data-stu-id="0a734-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="0a734-143">**ビット 16 - 23**: その他の意味のあるコードの修飾子</span><span class="sxs-lookup"><span data-stu-id="0a734-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="0a734-144">次の表に、可能性のある Sense/ASC/ASCQ の組み合わせを示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="0a734-145">Sense キー</span><span class="sxs-lookup"><span data-stu-id="0a734-145">Sense Key</span></span> | <span data-ttu-id="0a734-146">ASC</span><span class="sxs-lookup"><span data-stu-id="0a734-146">ASC</span></span> | <span data-ttu-id="0a734-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="0a734-147">ASCQ</span></span> | <span data-ttu-id="0a734-148">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="0a734-149">00</span><span class="sxs-lookup"><span data-stu-id="0a734-149">00</span></span>        | <span data-ttu-id="0a734-150">00</span><span class="sxs-lookup"><span data-stu-id="0a734-150">00</span></span>  | <span data-ttu-id="0a734-151">00</span><span class="sxs-lookup"><span data-stu-id="0a734-151">00</span></span>   | <span data-ttu-id="0a734-152">センスなし</span><span class="sxs-lookup"><span data-stu-id="0a734-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="0a734-153">01</span><span class="sxs-lookup"><span data-stu-id="0a734-153">01</span></span>        | <span data-ttu-id="0a734-154">17</span><span class="sxs-lookup"><span data-stu-id="0a734-154">17</span></span>  | <span data-ttu-id="0a734-155">01</span><span class="sxs-lookup"><span data-stu-id="0a734-155">01</span></span>   | <span data-ttu-id="0a734-156">再試行で回復されたデータ</span><span class="sxs-lookup"><span data-stu-id="0a734-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="0a734-157">01</span><span class="sxs-lookup"><span data-stu-id="0a734-157">01</span></span>        | <span data-ttu-id="0a734-158">18</span><span class="sxs-lookup"><span data-stu-id="0a734-158">18</span></span>  | <span data-ttu-id="0a734-159">00</span><span class="sxs-lookup"><span data-stu-id="0a734-159">00</span></span>   | <span data-ttu-id="0a734-160">ECC で回復されたデータ</span><span class="sxs-lookup"><span data-stu-id="0a734-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="0a734-161">02</span><span class="sxs-lookup"><span data-stu-id="0a734-161">02</span></span>        | <span data-ttu-id="0a734-162">04</span><span class="sxs-lookup"><span data-stu-id="0a734-162">04</span></span>  | <span data-ttu-id="0a734-163">01</span><span class="sxs-lookup"><span data-stu-id="0a734-163">01</span></span>   | <span data-ttu-id="0a734-164">論理ドライブの準備ができていない - 準備中</span><span class="sxs-lookup"><span data-stu-id="0a734-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="0a734-165">02</span><span class="sxs-lookup"><span data-stu-id="0a734-165">02</span></span>        | <span data-ttu-id="0a734-166">04</span><span class="sxs-lookup"><span data-stu-id="0a734-166">04</span></span>  | <span data-ttu-id="0a734-167">02</span><span class="sxs-lookup"><span data-stu-id="0a734-167">02</span></span>   | <span data-ttu-id="0a734-168">論理ドライブの準備ができていない - 初期化が必要</span><span class="sxs-lookup"><span data-stu-id="0a734-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="0a734-169">02</span><span class="sxs-lookup"><span data-stu-id="0a734-169">02</span></span>        | <span data-ttu-id="0a734-170">04</span><span class="sxs-lookup"><span data-stu-id="0a734-170">04</span></span>  | <span data-ttu-id="0a734-171">04</span><span class="sxs-lookup"><span data-stu-id="0a734-171">04</span></span>   | <span data-ttu-id="0a734-172">論理ユニットの準備ができていない - フォーマット進行中</span><span class="sxs-lookup"><span data-stu-id="0a734-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="0a734-173">02</span><span class="sxs-lookup"><span data-stu-id="0a734-173">02</span></span>        | <span data-ttu-id="0a734-174">04</span><span class="sxs-lookup"><span data-stu-id="0a734-174">04</span></span>  | <span data-ttu-id="0a734-175">FF</span><span class="sxs-lookup"><span data-stu-id="0a734-175">FF</span></span>   | <span data-ttu-id="0a734-176">論理ドライブの準備ができていない - デバイスがビジー状態</span><span class="sxs-lookup"><span data-stu-id="0a734-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="0a734-177">02</span><span class="sxs-lookup"><span data-stu-id="0a734-177">02</span></span>        | <span data-ttu-id="0a734-178">06</span><span class="sxs-lookup"><span data-stu-id="0a734-178">06</span></span>  | <span data-ttu-id="0a734-179">00</span><span class="sxs-lookup"><span data-stu-id="0a734-179">00</span></span>   | <span data-ttu-id="0a734-180">参照位置が見つからない</span><span class="sxs-lookup"><span data-stu-id="0a734-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="0a734-181">02</span><span class="sxs-lookup"><span data-stu-id="0a734-181">02</span></span>        | <span data-ttu-id="0a734-182">08</span><span class="sxs-lookup"><span data-stu-id="0a734-182">08</span></span>  | <span data-ttu-id="0a734-183">00</span><span class="sxs-lookup"><span data-stu-id="0a734-183">00</span></span>   | <span data-ttu-id="0a734-184">論理ユニットの通信エラー</span><span class="sxs-lookup"><span data-stu-id="0a734-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="0a734-185">02</span><span class="sxs-lookup"><span data-stu-id="0a734-185">02</span></span>        | <span data-ttu-id="0a734-186">08</span><span class="sxs-lookup"><span data-stu-id="0a734-186">08</span></span>  | <span data-ttu-id="0a734-187">01</span><span class="sxs-lookup"><span data-stu-id="0a734-187">01</span></span>   | <span data-ttu-id="0a734-188">論理ユニットの通信タイムアウト</span><span class="sxs-lookup"><span data-stu-id="0a734-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="0a734-189">02</span><span class="sxs-lookup"><span data-stu-id="0a734-189">02</span></span>        | <span data-ttu-id="0a734-190">08</span><span class="sxs-lookup"><span data-stu-id="0a734-190">08</span></span>  | <span data-ttu-id="0a734-191">80</span><span class="sxs-lookup"><span data-stu-id="0a734-191">80</span></span>   | <span data-ttu-id="0a734-192">論理ユニットの通信オーバーラン</span><span class="sxs-lookup"><span data-stu-id="0a734-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="0a734-193">02</span><span class="sxs-lookup"><span data-stu-id="0a734-193">02</span></span>        | <span data-ttu-id="0a734-194">3A</span><span class="sxs-lookup"><span data-stu-id="0a734-194">3A</span></span>  | <span data-ttu-id="0a734-195">00</span><span class="sxs-lookup"><span data-stu-id="0a734-195">00</span></span>   | <span data-ttu-id="0a734-196">メディアが存在しない</span><span class="sxs-lookup"><span data-stu-id="0a734-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="0a734-197">02</span><span class="sxs-lookup"><span data-stu-id="0a734-197">02</span></span>        | <span data-ttu-id="0a734-198">54</span><span class="sxs-lookup"><span data-stu-id="0a734-198">54</span></span>  | <span data-ttu-id="0a734-199">00</span><span class="sxs-lookup"><span data-stu-id="0a734-199">00</span></span>   | <span data-ttu-id="0a734-200">USB からホスト システムへのインターフェイス エラー</span><span class="sxs-lookup"><span data-stu-id="0a734-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="0a734-201">02</span><span class="sxs-lookup"><span data-stu-id="0a734-201">02</span></span>        | <span data-ttu-id="0a734-202">80</span><span class="sxs-lookup"><span data-stu-id="0a734-202">80</span></span>  | <span data-ttu-id="0a734-203">00</span><span class="sxs-lookup"><span data-stu-id="0a734-203">00</span></span>   | <span data-ttu-id="0a734-204">リソース不足</span><span class="sxs-lookup"><span data-stu-id="0a734-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="0a734-205">02</span><span class="sxs-lookup"><span data-stu-id="0a734-205">02</span></span>        | <span data-ttu-id="0a734-206">FF</span><span class="sxs-lookup"><span data-stu-id="0a734-206">FF</span></span>  | <span data-ttu-id="0a734-207">FF</span><span class="sxs-lookup"><span data-stu-id="0a734-207">FF</span></span>   | <span data-ttu-id="0a734-208">不明なエラーです</span><span class="sxs-lookup"><span data-stu-id="0a734-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="0a734-209">03</span><span class="sxs-lookup"><span data-stu-id="0a734-209">03</span></span>        | <span data-ttu-id="0a734-210">02</span><span class="sxs-lookup"><span data-stu-id="0a734-210">02</span></span>  | <span data-ttu-id="0a734-211">00</span><span class="sxs-lookup"><span data-stu-id="0a734-211">00</span></span>   | <span data-ttu-id="0a734-212">シークが完了していない</span><span class="sxs-lookup"><span data-stu-id="0a734-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="0a734-213">03</span><span class="sxs-lookup"><span data-stu-id="0a734-213">03</span></span>        | <span data-ttu-id="0a734-214">03</span><span class="sxs-lookup"><span data-stu-id="0a734-214">03</span></span>  | <span data-ttu-id="0a734-215">00</span><span class="sxs-lookup"><span data-stu-id="0a734-215">00</span></span>   | <span data-ttu-id="0a734-216">書き込みエラー</span><span class="sxs-lookup"><span data-stu-id="0a734-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="0a734-217">03</span><span class="sxs-lookup"><span data-stu-id="0a734-217">03</span></span>        | <span data-ttu-id="0a734-218">10</span><span class="sxs-lookup"><span data-stu-id="0a734-218">10</span></span>  | <span data-ttu-id="0a734-219">00</span><span class="sxs-lookup"><span data-stu-id="0a734-219">00</span></span>   | <span data-ttu-id="0a734-220">ID CRC エラー</span><span class="sxs-lookup"><span data-stu-id="0a734-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="0a734-221">03</span><span class="sxs-lookup"><span data-stu-id="0a734-221">03</span></span>        | <span data-ttu-id="0a734-222">11</span><span class="sxs-lookup"><span data-stu-id="0a734-222">11</span></span>  | <span data-ttu-id="0a734-223">00</span><span class="sxs-lookup"><span data-stu-id="0a734-223">00</span></span>   | <span data-ttu-id="0a734-224">回復不可能な読み取りエラー</span><span class="sxs-lookup"><span data-stu-id="0a734-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="0a734-225">03</span><span class="sxs-lookup"><span data-stu-id="0a734-225">03</span></span>        | <span data-ttu-id="0a734-226">12</span><span class="sxs-lookup"><span data-stu-id="0a734-226">12</span></span>  | <span data-ttu-id="0a734-227">00</span><span class="sxs-lookup"><span data-stu-id="0a734-227">00</span></span>   | <span data-ttu-id="0a734-228">ID フィールドのアドレス マークが見つからない</span><span class="sxs-lookup"><span data-stu-id="0a734-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="0a734-229">03</span><span class="sxs-lookup"><span data-stu-id="0a734-229">03</span></span>        | <span data-ttu-id="0a734-230">13</span><span class="sxs-lookup"><span data-stu-id="0a734-230">13</span></span>  | <span data-ttu-id="0a734-231">00</span><span class="sxs-lookup"><span data-stu-id="0a734-231">00</span></span>   | <span data-ttu-id="0a734-232">データ フィールドのアドレス マークが見つからない</span><span class="sxs-lookup"><span data-stu-id="0a734-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="0a734-233">03</span><span class="sxs-lookup"><span data-stu-id="0a734-233">03</span></span>        | <span data-ttu-id="0a734-234">14</span><span class="sxs-lookup"><span data-stu-id="0a734-234">14</span></span>  | <span data-ttu-id="0a734-235">00</span><span class="sxs-lookup"><span data-stu-id="0a734-235">00</span></span>   | <span data-ttu-id="0a734-236">記録されたエンティティが見つからない</span><span class="sxs-lookup"><span data-stu-id="0a734-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="0a734-237">03</span><span class="sxs-lookup"><span data-stu-id="0a734-237">03</span></span>        | <span data-ttu-id="0a734-238">30</span><span class="sxs-lookup"><span data-stu-id="0a734-238">30</span></span>  | <span data-ttu-id="0a734-239">01</span><span class="sxs-lookup"><span data-stu-id="0a734-239">01</span></span>   | <span data-ttu-id="0a734-240">メディアを読み取ることができない - 不明な形式</span><span class="sxs-lookup"><span data-stu-id="0a734-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="0a734-241">03</span><span class="sxs-lookup"><span data-stu-id="0a734-241">03</span></span>        | <span data-ttu-id="0a734-242">31</span><span class="sxs-lookup"><span data-stu-id="0a734-242">31</span></span>  | <span data-ttu-id="0a734-243">01</span><span class="sxs-lookup"><span data-stu-id="0a734-243">01</span></span>   | <span data-ttu-id="0a734-244">FORMAT コマンド失敗</span><span class="sxs-lookup"><span data-stu-id="0a734-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="0a734-245">04</span><span class="sxs-lookup"><span data-stu-id="0a734-245">04</span></span>        | <span data-ttu-id="0a734-246">40</span><span class="sxs-lookup"><span data-stu-id="0a734-246">40</span></span>  | <span data-ttu-id="0a734-247">NN</span><span class="sxs-lookup"><span data-stu-id="0a734-247">NN</span></span>   | <span data-ttu-id="0a734-248">コンポーネント NN (80H - FFH) の診断エラー</span><span class="sxs-lookup"><span data-stu-id="0a734-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="0a734-249">05</span><span class="sxs-lookup"><span data-stu-id="0a734-249">05</span></span>        | <span data-ttu-id="0a734-250">1A</span><span class="sxs-lookup"><span data-stu-id="0a734-250">1A</span></span>  | <span data-ttu-id="0a734-251">00</span><span class="sxs-lookup"><span data-stu-id="0a734-251">00</span></span>   | <span data-ttu-id="0a734-252">パラメーター リスト長エラー</span><span class="sxs-lookup"><span data-stu-id="0a734-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="0a734-253">05</span><span class="sxs-lookup"><span data-stu-id="0a734-253">05</span></span>        | <span data-ttu-id="0a734-254">20</span><span class="sxs-lookup"><span data-stu-id="0a734-254">20</span></span>  | <span data-ttu-id="0a734-255">00</span><span class="sxs-lookup"><span data-stu-id="0a734-255">00</span></span>   | <span data-ttu-id="0a734-256">無効なコマンド操作コード</span><span class="sxs-lookup"><span data-stu-id="0a734-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="0a734-257">05</span><span class="sxs-lookup"><span data-stu-id="0a734-257">05</span></span>        | <span data-ttu-id="0a734-258">21</span><span class="sxs-lookup"><span data-stu-id="0a734-258">21</span></span>  | <span data-ttu-id="0a734-259">00</span><span class="sxs-lookup"><span data-stu-id="0a734-259">00</span></span>   | <span data-ttu-id="0a734-260">論理ブロック アドレスが範囲外</span><span class="sxs-lookup"><span data-stu-id="0a734-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="0a734-261">05</span><span class="sxs-lookup"><span data-stu-id="0a734-261">05</span></span>        | <span data-ttu-id="0a734-262">24</span><span class="sxs-lookup"><span data-stu-id="0a734-262">24</span></span>  | <span data-ttu-id="0a734-263">00</span><span class="sxs-lookup"><span data-stu-id="0a734-263">00</span></span>   | <span data-ttu-id="0a734-264">コマンド パケットのフィールドが無効</span><span class="sxs-lookup"><span data-stu-id="0a734-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="0a734-265">05</span><span class="sxs-lookup"><span data-stu-id="0a734-265">05</span></span>        | <span data-ttu-id="0a734-266">25</span><span class="sxs-lookup"><span data-stu-id="0a734-266">25</span></span>  | <span data-ttu-id="0a734-267">00</span><span class="sxs-lookup"><span data-stu-id="0a734-267">00</span></span>   | <span data-ttu-id="0a734-268">論理ユニットがサポートされていない</span><span class="sxs-lookup"><span data-stu-id="0a734-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="0a734-269">05</span><span class="sxs-lookup"><span data-stu-id="0a734-269">05</span></span>        | <span data-ttu-id="0a734-270">26</span><span class="sxs-lookup"><span data-stu-id="0a734-270">26</span></span>  | <span data-ttu-id="0a734-271">00</span><span class="sxs-lookup"><span data-stu-id="0a734-271">00</span></span>   | <span data-ttu-id="0a734-272">パラメーター リストのフィールドが無効</span><span class="sxs-lookup"><span data-stu-id="0a734-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="0a734-273">05</span><span class="sxs-lookup"><span data-stu-id="0a734-273">05</span></span>        | <span data-ttu-id="0a734-274">26</span><span class="sxs-lookup"><span data-stu-id="0a734-274">26</span></span>  | <span data-ttu-id="0a734-275">01</span><span class="sxs-lookup"><span data-stu-id="0a734-275">01</span></span>   | <span data-ttu-id="0a734-276">サポートされていないパラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="0a734-277">05</span><span class="sxs-lookup"><span data-stu-id="0a734-277">05</span></span>        | <span data-ttu-id="0a734-278">26</span><span class="sxs-lookup"><span data-stu-id="0a734-278">26</span></span>  | <span data-ttu-id="0a734-279">02</span><span class="sxs-lookup"><span data-stu-id="0a734-279">02</span></span>   | <span data-ttu-id="0a734-280">値が無効なパラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="0a734-281">05</span><span class="sxs-lookup"><span data-stu-id="0a734-281">05</span></span>        | <span data-ttu-id="0a734-282">39</span><span class="sxs-lookup"><span data-stu-id="0a734-282">39</span></span>  | <span data-ttu-id="0a734-283">00</span><span class="sxs-lookup"><span data-stu-id="0a734-283">00</span></span>   | <span data-ttu-id="0a734-284">パラメーターの保存はサポートされていない</span><span class="sxs-lookup"><span data-stu-id="0a734-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="0a734-285">06</span><span class="sxs-lookup"><span data-stu-id="0a734-285">06</span></span>        | <span data-ttu-id="0a734-286">28</span><span class="sxs-lookup"><span data-stu-id="0a734-286">28</span></span>  | <span data-ttu-id="0a734-287">00</span><span class="sxs-lookup"><span data-stu-id="0a734-287">00</span></span>   | <span data-ttu-id="0a734-288">準備完了への移行の準備ができていない - メディアが変更された</span><span class="sxs-lookup"><span data-stu-id="0a734-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="0a734-289">06</span><span class="sxs-lookup"><span data-stu-id="0a734-289">06</span></span>        | <span data-ttu-id="0a734-290">29</span><span class="sxs-lookup"><span data-stu-id="0a734-290">29</span></span>  | <span data-ttu-id="0a734-291">00</span><span class="sxs-lookup"><span data-stu-id="0a734-291">00</span></span>   | <span data-ttu-id="0a734-292">電源オン リセットまたはバス デバイスのリセットが発生した</span><span class="sxs-lookup"><span data-stu-id="0a734-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="0a734-293">06</span><span class="sxs-lookup"><span data-stu-id="0a734-293">06</span></span>        | <span data-ttu-id="0a734-294">2F</span><span class="sxs-lookup"><span data-stu-id="0a734-294">2F</span></span>  | <span data-ttu-id="0a734-295">00</span><span class="sxs-lookup"><span data-stu-id="0a734-295">00</span></span>   | <span data-ttu-id="0a734-296">別のイニシエーターによってクリアされたコマンド</span><span class="sxs-lookup"><span data-stu-id="0a734-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="0a734-297">07</span><span class="sxs-lookup"><span data-stu-id="0a734-297">07</span></span>        | <span data-ttu-id="0a734-298">27</span><span class="sxs-lookup"><span data-stu-id="0a734-298">27</span></span>  | <span data-ttu-id="0a734-299">00</span><span class="sxs-lookup"><span data-stu-id="0a734-299">00</span></span>   | <span data-ttu-id="0a734-300">書き込み保護されたメディア</span><span class="sxs-lookup"><span data-stu-id="0a734-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="0a734-301">0B</span><span class="sxs-lookup"><span data-stu-id="0a734-301">0B</span></span>        | <span data-ttu-id="0a734-302">4E</span><span class="sxs-lookup"><span data-stu-id="0a734-302">4E</span></span>  | <span data-ttu-id="0a734-303">00</span><span class="sxs-lookup"><span data-stu-id="0a734-303">00</span></span>   | <span data-ttu-id="0a734-304">重複するコマンドが試行された</span><span class="sxs-lookup"><span data-stu-id="0a734-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="0a734-305">さらに 2 つのオプションのコールバックをアプリケーションで実装できます。1 つは **GET_STATUS_NOTIFICATION** コマンドに応答するためのもので、もう 1 つは **SYNCHRONIZE_CACHE** コマンドに応答するためのものです。</span><span class="sxs-lookup"><span data-stu-id="0a734-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="0a734-306">アプリケーションでホストからの GET_STATUS_NOTIFICATION コマンドを処理する場合は、次のプロトタイプを持つコールバックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="0a734-307">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="0a734-307">Where:</span></span>

- <span data-ttu-id="0a734-308">*storage* は、ストレージ クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="0a734-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="0a734-309">*media_id* は現在使用されていません。</span><span class="sxs-lookup"><span data-stu-id="0a734-309">*media_id* is not currently used.</span></span> <span data-ttu-id="0a734-310">notification_class は、通知のクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a734-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="0a734-311">*media_notification* には、通知への応答が格納されているバッファーをアプリケーションで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="0a734-312">*media_notification_length* には、応答バッファーの長さをアプリケーションで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="0a734-313">戻り値では、コマンドが成功したかどうかが示されます。**UX_SUCCESS** または **UX_ERROR** のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0a734-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="0a734-314">アプリケーションでこのコールバックが実装されていない場合、**GET_STATUS_NOTIFICATION** コマンドを受け取ると、コマンドが実装されていないことが USBX によってホストに通知されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="0a734-315">ホストからの書き込みのためにアプリケーションでキャッシュが利用されている場合は、**SYNCHRONIZE_CACHE** コマンドを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="0a734-316">記憶装置が切断されようとしていることをホストが認識した合、ホストによりこのコマンドが送信されることがあります。たとえば、Windows では、ユーザーがツール バーのフラッシュ ドライブ アイコンを右クリックして、[<記憶装置名> の取り出し] を選択すると、Windows によって **SYNCHRONIZE_CACHE** コマンドがそのデバイスに発行されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="0a734-317">アプリケーションでホストからの **GET_STATUS_NOTIFICATION** コマンドを処理する場合は、次のプロトタイプを持つコールバックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="0a734-318">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="0a734-318">Where:</span></span>

- <span data-ttu-id="0a734-319">*storage* は、ストレージ クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="0a734-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="0a734-320">*lun* パラメーターは、コマンドの送信先の LUN を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a734-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="0a734-321">*number_blocks* は、同期するブロックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a734-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="0a734-322">*lba* は、同期する最初のブロックのセクター アドレスです。</span><span class="sxs-lookup"><span data-stu-id="0a734-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="0a734-323">*media_status* には、メディア ステータス コールバックの戻り値を正確に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="0a734-324">戻り値では、コマンドが成功したかどうかが示されます。**UX_SUCCESS** または **UX_ERROR** のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0a734-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="0a734-325">複数の SCSI LUN</span><span class="sxs-lookup"><span data-stu-id="0a734-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="0a734-326">USBX デバイス ストレージ クラスでは、複数の LUN がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0a734-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="0a734-327">したがって、同時に CD-ROM とフラッシュ ディスクとして機能する記憶装置を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0a734-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="0a734-328">このような場合、初期化は少し異なります。</span><span class="sxs-lookup"><span data-stu-id="0a734-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="0a734-329">フラッシュ ディスクと CD-ROM の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

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

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="0a734-330">USB デバイスの CDC-ACM クラス</span><span class="sxs-lookup"><span data-stu-id="0a734-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="0a734-331">USB デバイスの CDC-ACM クラスを使用することで、USB ホスト システムは、シリアル デバイスとしてデバイスと通信できます。</span><span class="sxs-lookup"><span data-stu-id="0a734-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="0a734-332">このクラスは、USB 規格に基づいており、CDC 標準のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="0a734-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="0a734-333">CDC-ACM 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="0a734-334">例については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a734-334">An example is found here below.</span></span>

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

<span data-ttu-id="0a734-335">インターフェイス (制御とデータ) は、CDC-ACM クラスにより、複合デバイス フレームワークを使用してグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="0a734-336">そのため、デバイス記述子を定義するときは注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="0a734-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="0a734-337">USBX は IAD 記述子を使用して、インターフェイスのバインド方法を内部で認識します。</span><span class="sxs-lookup"><span data-stu-id="0a734-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="0a734-338">インターフェイスの前に IAD 記述子を宣言し、CDC-ACM クラスの最初のインターフェイスと、アタッチされるインターフェイスの数を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="0a734-339">また、CDC-ACM クラスでは、新しい IAD 記述子と同じ機能を実行する結合機能記述子も使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="0a734-340">結合機能記述子は歴史的な理由と、ホスト側との互換性のために宣言する必要がありますが、USBX では使用されません。</span><span class="sxs-lookup"><span data-stu-id="0a734-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="0a734-341">CDC-ACM クラスの初期化には、次のパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a734-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="0a734-342">定義されている 2 つのパラメーターは、スタックによってこのクラスがアクティブ化または非アクティブ化されると呼び出される、ユーザー アプリケーションへのコールバック ポインターです。</span><span class="sxs-lookup"><span data-stu-id="0a734-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="0a734-343">3 番目に定義されているパラメーターは、ライン コードまたはライン状態のパラメーターが変更されたときに呼び出される、ユーザー アプリケーションへのコールバック ポインターです。</span><span class="sxs-lookup"><span data-stu-id="0a734-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="0a734-344">たとえば、ホストから DTR 状態を **TRUE** に変更する要求があると、コールバックが呼び出されます。そのユーザー アプリケーションでは、IOCTL 関数を使用してラインの状態をチェックし、ホストで通信の準備ができていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="0a734-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="0a734-345">CDC-ACM は、USB-IF 規格に基づいており、macOS と Linux のオペレーティング システムによって自動的に認識されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="0a734-346">Windows 10 より前のバージョンでは、このクラスには .inf ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a734-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="0a734-347">Windows 10 では、.inf ファイルは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="0a734-348">CDC-ACM クラス用のテンプレートが用意されており、***usbx_windows_host_files*** ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="0a734-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="0a734-349">新しいバージョンの Windows では、CDC_ACM_Template_Win7_64bit.inf ファイルを使用する必要があります (Win10 を除く)。</span><span class="sxs-lookup"><span data-stu-id="0a734-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="0a734-350">このファイルを変更して、デバイスによって使用される PID/VID を反映させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="0a734-351">この PID/VID は、会社と製品が USB-IF に登録されたときに、最終的な顧客に固有のものになります。</span><span class="sxs-lookup"><span data-stu-id="0a734-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="0a734-352">inf ファイル内の変更対象のフィールドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="0a734-353">CDC-ACM デバイスのデバイス フレームワーク内で、PID/VID はデバイス記述子に格納されます (上記の宣言されたデバイス記述子を参照)。</span><span class="sxs-lookup"><span data-stu-id="0a734-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="0a734-354">USB ホスト システムによって USB CDC-ACM デバイスが検出されると、シリアル クラスがマウントされ、任意のシリアル ターミナル プログラムでデバイスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a734-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="0a734-355">詳細については、ホスト オペレーティング システムを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a734-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="0a734-356">CDC-ACM クラスの API 関数の定義を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="0a734-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="0a734-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="0a734-358">CDC-ACM インターフェイスで IOCTL を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-359">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-360">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-360">Description</span></span>

<span data-ttu-id="0a734-361">この関数は、アプリケーションで cdc acm インターフェイスに対してさまざまな ioctl 呼び出しを実行する必要がある場合に呼び出されます</span><span class="sxs-lookup"><span data-stu-id="0a734-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-362">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-362">Parameters</span></span>

- <span data-ttu-id="0a734-363">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-364">**ioctl_function**: 実行される ioctl 関数。</span><span class="sxs-lookup"><span data-stu-id="0a734-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="0a734-365">**parameter**: ioctl の呼び出しに固有のパラメーターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="0a734-366">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-366">Return Value</span></span>

- <span data-ttu-id="0a734-367">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-368">**UX_ERROR** (0xFF) 関数からのエラー</span><span class="sxs-lookup"><span data-stu-id="0a734-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="0a734-369">例</span><span class="sxs-lookup"><span data-stu-id="0a734-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="0a734-370">Ioctl 関数:</span><span class="sxs-lookup"><span data-stu-id="0a734-370">Ioctl functions:</span></span>

| <span data-ttu-id="0a734-371">Function</span><span class="sxs-lookup"><span data-stu-id="0a734-371">Function</span></span>                                        | <span data-ttu-id="0a734-372">値</span><span class="sxs-lookup"><span data-stu-id="0a734-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="0a734-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0a734-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="0a734-374">1</span><span class="sxs-lookup"><span data-stu-id="0a734-374">1</span></span> |
| <span data-ttu-id="0a734-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0a734-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="0a734-376">2</span><span class="sxs-lookup"><span data-stu-id="0a734-376">2</span></span> |
| <span data-ttu-id="0a734-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0a734-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="0a734-378">3</span><span class="sxs-lookup"><span data-stu-id="0a734-378">3</span></span> |
| <span data-ttu-id="0a734-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="0a734-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="0a734-380">4</span><span class="sxs-lookup"><span data-stu-id="0a734-380">4</span></span> |
| <span data-ttu-id="0a734-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0a734-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="0a734-382">5</span><span class="sxs-lookup"><span data-stu-id="0a734-382">5</span></span> |
| <span data-ttu-id="0a734-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="0a734-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="0a734-384">6</span><span class="sxs-lookup"><span data-stu-id="0a734-384">6</span></span> |
| <span data-ttu-id="0a734-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="0a734-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="0a734-386">7</span><span class="sxs-lookup"><span data-stu-id="0a734-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="0a734-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0a734-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="0a734-388">CDC-ACM インターフェイスで IOCTL のライン コーディング設定を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-389">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-390">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-390">Description</span></span>

<span data-ttu-id="0a734-391">この関数は、アプリケーションでライン コーディング パラメーターを設定する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-392">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-392">Parameters</span></span>

- <span data-ttu-id="0a734-393">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0a734-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="0a734-395">**parameter**: ライン パラメーター構造体へのポインター:</span><span class="sxs-lookup"><span data-stu-id="0a734-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="0a734-396">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-396">Return Value</span></span>

<span data-ttu-id="0a734-397">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-398">例</span><span class="sxs-lookup"><span data-stu-id="0a734-398">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="0a734-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0a734-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="0a734-400">CDC-ACM インターフェイスで IOCTL のライン コーディング取得を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-401">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-402">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-402">Description</span></span>

<span data-ttu-id="0a734-403">この関数は、アプリケーションでライン コーディング パラメーターを取得する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-404">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-404">Parameters</span></span>

- <span data-ttu-id="0a734-405">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0a734-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="0a734-407">**parameter**: ライン パラメーター構造体へのポインター:</span><span class="sxs-lookup"><span data-stu-id="0a734-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="0a734-408">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-408">Return Value</span></span>

- <span data-ttu-id="0a734-409">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-410">例</span><span class="sxs-lookup"><span data-stu-id="0a734-410">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="0a734-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0a734-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="0a734-412">CDC-ACM インターフェイスで IOCTL のライン状態取得を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="0a734-413">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-414">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-414">Description</span></span>

<span data-ttu-id="0a734-415">この関数は、アプリケーションでライン状態パラメーターを取得する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-416">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-416">Parameters</span></span>

- <span data-ttu-id="0a734-417">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0a734-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="0a734-419">**parameter**: ライン パラメーター構造体へのポインター:</span><span class="sxs-lookup"><span data-stu-id="0a734-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="0a734-420">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-420">Return Value</span></span>

- <span data-ttu-id="0a734-421">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-422">例</span><span class="sxs-lookup"><span data-stu-id="0a734-422">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="0a734-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0a734-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="0a734-424">CDC-ACM インターフェイスで IOCTL のライン状態設定を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-425">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-426">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-426">Description</span></span>

<span data-ttu-id="0a734-427">この関数は、アプリケーションでライン状態パラメーターを取得する必要がある場合に呼び出されます</span><span class="sxs-lookup"><span data-stu-id="0a734-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-428">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-428">Parameters</span></span>

- <span data-ttu-id="0a734-429">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0a734-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="0a734-431">**parameter**: ライン パラメーター構造体へのポインター:</span><span class="sxs-lookup"><span data-stu-id="0a734-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="0a734-432">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-432">Return Value</span></span>

- <span data-ttu-id="0a734-433">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-434">例</span><span class="sxs-lookup"><span data-stu-id="0a734-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="0a734-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="0a734-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="0a734-436">CDC-ACM インターフェイスで IOCTL のパイプ中止を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-437">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-438">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-438">Description</span></span>

<span data-ttu-id="0a734-439">この関数は、アプリケーションでパイプを中止する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="0a734-440">たとえば、実行中の書き込みを中止するには、UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT をパラメーターとして渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-441">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-441">Parameters</span></span>

- <span data-ttu-id="0a734-442">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="0a734-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="0a734-444">**parameter**: パイプの方向:</span><span class="sxs-lookup"><span data-stu-id="0a734-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="0a734-445">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-445">Return Value</span></span>

- <span data-ttu-id="0a734-446">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) パイプの方向が無効です。</span><span class="sxs-lookup"><span data-stu-id="0a734-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-448">例</span><span class="sxs-lookup"><span data-stu-id="0a734-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="0a734-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="0a734-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="0a734-450">CDC-ACM インターフェイスで IOCTL の送信開始を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-451">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-452">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-452">Description</span></span>

<span data-ttu-id="0a734-453">この関数は、アプリケーションによりコールバックで送信を使用する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-454">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-454">Parameters</span></span>

- <span data-ttu-id="0a734-455">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="0a734-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="0a734-457">**parameter**: 送信開始パラメーター構造体へのポインター:</span><span class="sxs-lookup"><span data-stu-id="0a734-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="0a734-458">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-458">Return Value</span></span>

- <span data-ttu-id="0a734-459">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-460">**UX_ERROR** (0xFF) 送信は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="0a734-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="0a734-461">**UX_MEMORY_INSUFFICIENT**: (0x12) メモリの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-462">例</span><span class="sxs-lookup"><span data-stu-id="0a734-462">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="0a734-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="0a734-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="0a734-464">CDC-ACM インターフェイスで IOCTL の送信停止を実行します</span><span class="sxs-lookup"><span data-stu-id="0a734-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-465">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0a734-466">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-466">Description</span></span>

<span data-ttu-id="0a734-467">この関数は、アプリケーションによりコールバックでの送信の使用を停止する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-468">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-468">Parameters</span></span>

- <span data-ttu-id="0a734-469">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span><span class="sxs-lookup"><span data-stu-id="0a734-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="0a734-471">**parameter**: 使用されていません</span><span class="sxs-lookup"><span data-stu-id="0a734-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="0a734-472">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-472">Return Value</span></span>

- <span data-ttu-id="0a734-473">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-474">**UX_ERROR** (0xFF) 実行中の送信がありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-475">例</span><span class="sxs-lookup"><span data-stu-id="0a734-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="0a734-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="0a734-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="0a734-477">CDC-ACM パイプから読み取ります</span><span class="sxs-lookup"><span data-stu-id="0a734-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-478">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="0a734-479">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-479">Description</span></span>

<span data-ttu-id="0a734-480">この関数は、アプリケーションで OUT データ パイプから読み取る必要があるときに呼び出されます (OUT はホストから、IN はデバイスから)。</span><span class="sxs-lookup"><span data-stu-id="0a734-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="0a734-481">ブロッキングです。</span><span class="sxs-lookup"><span data-stu-id="0a734-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-482">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-482">Parameters</span></span>

- <span data-ttu-id="0a734-483">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-484">**buffer**: データが格納されるバッファー アドレス。</span><span class="sxs-lookup"><span data-stu-id="0a734-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="0a734-485">**requested_length**: 予想される最大長。</span><span class="sxs-lookup"><span data-stu-id="0a734-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="0a734-486">**actual_length**: バッファーに返された長さ。</span><span class="sxs-lookup"><span data-stu-id="0a734-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="0a734-487">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-487">Return Value</span></span>

- <span data-ttu-id="0a734-488">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) デバイスは、構成されている状態ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0a734-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="0a734-490">**UX_TRANSFER_NO_ANSWER** (0x22) デバイスから応答がありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="0a734-491">転送の保留中に、デバイスが切断された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-492">例</span><span class="sxs-lookup"><span data-stu-id="0a734-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="0a734-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="0a734-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="0a734-494">CDC-ACM パイプに書き込みます</span><span class="sxs-lookup"><span data-stu-id="0a734-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-495">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="0a734-496">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-496">Description</span></span>

<span data-ttu-id="0a734-497">この関数は、アプリケーションで IN データ パイプに書き込む必要があるときに呼び出されます (IN はホストから、OUT はデバイスから)。</span><span class="sxs-lookup"><span data-stu-id="0a734-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="0a734-498">ブロッキングです。</span><span class="sxs-lookup"><span data-stu-id="0a734-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-499">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-499">Parameters</span></span>

- <span data-ttu-id="0a734-500">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-501">**buffer**: データが格納されているバッファー アドレス。</span><span class="sxs-lookup"><span data-stu-id="0a734-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="0a734-502">**requested_length**: 書き込むバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="0a734-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="0a734-503">**actual_length**: 書き込みが実行された後でバッファーに返された長さ。</span><span class="sxs-lookup"><span data-stu-id="0a734-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="0a734-504">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-504">Return Value</span></span>
- <span data-ttu-id="0a734-505">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) デバイスは、構成されている状態ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0a734-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="0a734-507">**UX_TRANSFER_NO_ANSWER** (0x22) デバイスから応答がありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="0a734-508">転送の保留中に、デバイスが切断された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-509">例</span><span class="sxs-lookup"><span data-stu-id="0a734-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="0a734-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="0a734-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="0a734-511">コールバックで CDC-ACM パイプに書き込みます</span><span class="sxs-lookup"><span data-stu-id="0a734-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-512">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="0a734-513">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-513">Description</span></span>

<span data-ttu-id="0a734-514">この関数は、アプリケーションで IN データ パイプに書き込む必要があるときに呼び出されます (IN はホストから、OUT はデバイスから)。</span><span class="sxs-lookup"><span data-stu-id="0a734-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="0a734-515">この関数は非ブロッキングであり、完了は UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START で設定されているコールバックを通して行われます。</span><span class="sxs-lookup"><span data-stu-id="0a734-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-516">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-516">Parameters</span></span>

- <span data-ttu-id="0a734-517">**cdc_acm**: cdc クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="0a734-518">**buffer**: データが格納されているバッファー アドレス。</span><span class="sxs-lookup"><span data-stu-id="0a734-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="0a734-519">**requested_length**: 書き込むバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="0a734-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="0a734-520">**actual_length**: 書き込みが実行された後でバッファーに返された長さ</span><span class="sxs-lookup"><span data-stu-id="0a734-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="0a734-521">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-521">Return Value</span></span>

- <span data-ttu-id="0a734-522">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) デバイスは、構成されている状態ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0a734-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="0a734-524">**UX_TRANSFER_NO_ANSWER** (0x22) デバイスから応答がありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="0a734-525">転送の保留中に、デバイスが切断された可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-526">例</span><span class="sxs-lookup"><span data-stu-id="0a734-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="0a734-527">USB デバイスの CDC-ECM クラス</span><span class="sxs-lookup"><span data-stu-id="0a734-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="0a734-528">USB デバイス CDC-ECM クラスにより、USB ホスト システムが、イーサネット デバイスとしてデバイスと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a734-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="0a734-529">このクラスは、USB 規格に基づいており、CDC 標準のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="0a734-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="0a734-530">CDC-ACM 準拠のデバイス フレームワークは、デバイス スタックによって宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="0a734-531">例については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a734-531">An example is found here below.</span></span>

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

<span data-ttu-id="0a734-532">CDC-ECM クラスには、CDC-ACM とよく似たデバイス記述子アプローチが採用されており、IAD 記述子も必要です。</span><span class="sxs-lookup"><span data-stu-id="0a734-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="0a734-533">定義については、CDC-ACM クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a734-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="0a734-534">通常のデバイス フレームワークに加えて、CDC-ECM には特別な文字列記述子が必要です。</span><span class="sxs-lookup"><span data-stu-id="0a734-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="0a734-535">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0a734-535">An example is given below.</span></span>

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

<span data-ttu-id="0a734-536">MAC アドレス文字列記述子は、CDC-ECM クラスによって、デバイスが TCP/IP プロトコルで応答している MAC アドレスに関するホスト クエリに応答するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="0a734-537">デバイスで選択したものに設定できますが、ここで定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="0a734-538">CDC-ECM クラスの初期化は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0a734-538">The initialization of the CDC-ECM class is as follows.</span></span>

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

<span data-ttu-id="0a734-539">このクラスの初期化では、アクティブ化と非アクティブ化のために同じ関数コールバックが必要ですが、ここでは演習として、コールバックが実行されないように NULL に設定されています。</span><span class="sxs-lookup"><span data-stu-id="0a734-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="0a734-540">次のパラメーターは、ノード ID の定義用です。</span><span class="sxs-lookup"><span data-stu-id="0a734-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="0a734-541">CDC-ECM には、ローカル ノードとリモート ノードの 2 つのノードが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a734-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="0a734-542">ローカル ノードではデバイスの MAC アドレスが指定され、リモート ノードではホストの MAC アドレスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="0a734-543">リモート ノードは、デバイス フレームワークの文字列記述子で宣言されているものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="0a734-544">CDC-ECM クラスには、両方の方法でデータを転送するための組み込み API が用意されていますが、ユーザー アプリケーションは NetX 経由で USB イーサネット デバイスと通信するため、アプリケーションには表示されません。</span><span class="sxs-lookup"><span data-stu-id="0a734-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="0a734-545">USBX CDC-ECM クラスは、Azure RTOS NetX ネットワーク スタックに緊密に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="0a734-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="0a734-546">NetX と USBX の両方の CDC-ECM クラスを使用するアプリケーションは、通常の方法で NetX ネットワークスタックを起動しますが、それに加えて次のように USB ネットワーク スタックをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="0a734-547">USB ネットワーク スタックは 1 回だけアクティブにする必要があり、CDC-ECM に固有ではありませんが、NetX サービスを必要とするすべての USB クラスで必要になります。</span><span class="sxs-lookup"><span data-stu-id="0a734-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="0a734-548">CDC-ECM クラスは、MAC OS と Linux ホストによって認識されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="0a734-549">ただし、Microsoft Windows からは、CDC-ECM をネイティブに認識するためのドライバーは提供されていません。</span><span class="sxs-lookup"><span data-stu-id="0a734-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="0a734-550">一部の商用製品には、Windows プラットフォーム用のものが存在しており、独自の .inf ファイルが提供されています。</span><span class="sxs-lookup"><span data-stu-id="0a734-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="0a734-551">このファイルを、USB ネットワーク デバイスの PID/VID と一致するように、CDC-ACM の inf テンプレートと同じ方法で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="0a734-552">USB デバイスの HID クラス</span><span class="sxs-lookup"><span data-stu-id="0a734-552">USB Device HID Class</span></span>

<span data-ttu-id="0a734-553">USB デバイスの HID クラスを使用することで、USB ホスト システムから、特定の HID クライアント機能を持つ HID デバイスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="0a734-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="0a734-554">USBX の HID デバイス クラスは、ホスト側と比較して比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="0a734-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="0a734-555">それは、デバイスとその HID 記述子の動作に密接に結び付けられています。</span><span class="sxs-lookup"><span data-stu-id="0a734-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="0a734-556">次の例に示すように、HID クライアントでは、最初に HID デバイス フレームワークを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

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

<span data-ttu-id="0a734-557">HID フレームワークには、HID クラスと HID デバイス サブクラスについて記述されているインターフェイス記述子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a734-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="0a734-558">HID インターフェイスは、スタンドアロン クラスでも複合デバイスの一部でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="0a734-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="0a734-559">現在、USBX HID クラスは複数のレポート ID に対応していません。ほとんどのアプリケーションでは、必要な ID は 1 つだけです (ID ゼロ)。</span><span class="sxs-lookup"><span data-stu-id="0a734-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="0a734-560">複数のレポート ID の機能に関心がある場合は、お問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="0a734-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="0a734-561">HID クラスの初期化は次のようになります。例として USB キーボードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="0a734-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

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

<span data-ttu-id="0a734-562">アプリケーションでは、HID レポート記述子とその長さを HID クラスに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a734-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="0a734-563">レポート記述子は、デバイスについて記述されている項目のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="0a734-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="0a734-564">HID の文法の詳細については、HID USB クラスの仕様を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a734-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="0a734-565">アプリケーションからは、レポート記述子に加えて、HID イベントが発生したときのコールバックを渡します。</span><span class="sxs-lookup"><span data-stu-id="0a734-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="0a734-566">ホストからの次の標準 HID コマンドが、USBX HID クラスによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0a734-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="0a734-567">[コマンド名]</span><span class="sxs-lookup"><span data-stu-id="0a734-567">Command name</span></span>                             | <span data-ttu-id="0a734-568">値</span><span class="sxs-lookup"><span data-stu-id="0a734-568">Value</span></span> | <span data-ttu-id="0a734-569">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="0a734-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="0a734-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="0a734-571">0x01</span><span class="sxs-lookup"><span data-stu-id="0a734-571">0x01</span></span>  | <span data-ttu-id="0a734-572">デバイスからレポートを取得します</span><span class="sxs-lookup"><span data-stu-id="0a734-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="0a734-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="0a734-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="0a734-574">0x02</span><span class="sxs-lookup"><span data-stu-id="0a734-574">0x02</span></span>  | <span data-ttu-id="0a734-575">割り込みエンドポイントのアイドル周期を取得します</span><span class="sxs-lookup"><span data-stu-id="0a734-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="0a734-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="0a734-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="0a734-577">0x03</span><span class="sxs-lookup"><span data-stu-id="0a734-577">0x03</span></span>  | <span data-ttu-id="0a734-578">デバイスで実行されているプロトコルを取得します</span><span class="sxs-lookup"><span data-stu-id="0a734-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="0a734-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="0a734-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="0a734-580">0x09</span><span class="sxs-lookup"><span data-stu-id="0a734-580">0x09</span></span>  | <span data-ttu-id="0a734-581">デバイスにレポートを設定します</span><span class="sxs-lookup"><span data-stu-id="0a734-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="0a734-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="0a734-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="0a734-583">0x0a</span><span class="sxs-lookup"><span data-stu-id="0a734-583">0x0a</span></span>  | <span data-ttu-id="0a734-584">割り込みエンドポイントのアイドル周期を設定します</span><span class="sxs-lookup"><span data-stu-id="0a734-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="0a734-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="0a734-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="0a734-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="0a734-586">0x0b</span></span>  | <span data-ttu-id="0a734-587">デバイスで実行されているプロトコルを取得します</span><span class="sxs-lookup"><span data-stu-id="0a734-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="0a734-588">レポートの取得と設定は、ホストとデバイスの間でデータをやり取りするために、HID によって最もよく使用されるコマンドです。</span><span class="sxs-lookup"><span data-stu-id="0a734-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="0a734-589">ホストは、ほとんどの場合は制御エンドポイントでデータを送信しますが、割り込みエンドポイントでデータを受信したり、GET_REPORT コマンドを発行して制御エンドポイント上のデータをフェッチしたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0a734-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="0a734-590">HID クラスの ux_device_class_hid_event_set 関数を使用すると、割り込みエンドポイントでホストにデータを送り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="0a734-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="0a734-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="0a734-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="0a734-592">HID クラスにイベントを設定します</span><span class="sxs-lookup"><span data-stu-id="0a734-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-593">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="0a734-594">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-594">Description</span></span>

<span data-ttu-id="0a734-595">この関数は、アプリケーションで HID イベントをホストに返送する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="0a734-596">この関数はブロッキングではなく、レポートを循環キューに格納するだけで、アプリケーションに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="0a734-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-597">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-597">Parameters</span></span>

- <span data-ttu-id="0a734-598">**hid**: HID クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="0a734-599">**hid_event**: HID イベントの構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="0a734-600">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a734-600">Return Value</span></span>

- <span data-ttu-id="0a734-601">**UX_SUCCESS** (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="0a734-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="0a734-602">**UX_ERROR** (0xFF) エラー、循環キューに空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="0a734-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-603">例</span><span class="sxs-lookup"><span data-stu-id="0a734-603">Example</span></span>

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

<span data-ttu-id="0a734-604">HID クラスの初期化時に定義されたコールバックにより、イベント送信の逆の処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="0a734-605">ホストによって送信されたイベントを入力として取得します。</span><span class="sxs-lookup"><span data-stu-id="0a734-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="0a734-606">コールバックのプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0a734-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="0a734-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="0a734-607">hid_callback</span></span>

<span data-ttu-id="0a734-608">HID クラスからイベントを取得します</span><span class="sxs-lookup"><span data-stu-id="0a734-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="0a734-609">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0a734-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="0a734-610">説明</span><span class="sxs-lookup"><span data-stu-id="0a734-610">Description</span></span>

<span data-ttu-id="0a734-611">この関数は、ホストによって HID レポートがアプリケーションに送信されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a734-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="0a734-612">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a734-612">Parameters</span></span>

- <span data-ttu-id="0a734-613">**hid**: HID クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="0a734-614">**hid_event**: HID イベントの構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a734-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="0a734-615">例</span><span class="sxs-lookup"><span data-stu-id="0a734-615">Example</span></span>

<span data-ttu-id="0a734-616">次の例では、HID キーボードのイベントを解釈する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="0a734-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

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
