---
title: '第 5 章: USBX ホスト クラス API'
description: USBX ホスト クラス API について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813436"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="60df6-103">第 5 章: USBX ホスト クラス API</span><span class="sxs-lookup"><span data-stu-id="60df6-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="60df6-104">この章では、USBX ホスト クラスの公開されているすべての API について説明します。</span><span class="sxs-lookup"><span data-stu-id="60df6-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="60df6-105">クラスごとに次の API について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="60df6-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="60df6-106">HID クラス</span><span class="sxs-lookup"><span data-stu-id="60df6-106">HID class</span></span>
- <span data-ttu-id="60df6-107">CDC-ACM クラス</span><span class="sxs-lookup"><span data-stu-id="60df6-107">CDC-ACM class</span></span>
- <span data-ttu-id="60df6-108">CDC-ECM クラス</span><span class="sxs-lookup"><span data-stu-id="60df6-108">CDC-ECM class</span></span>
- <span data-ttu-id="60df6-109">ストレージ クラス</span><span class="sxs-lookup"><span data-stu-id="60df6-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="60df6-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="60df6-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="60df6-111">HID クラスに HID クライアントを登録します。</span><span class="sxs-lookup"><span data-stu-id="60df6-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-112">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="60df6-113">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-113">Description</span></span>

<span data-ttu-id="60df6-114">この関数は、HID クラスに HID クライアントを登録するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="60df6-115">HID クラスは、このデバイスからデータを要求する前に、HID デバイスと HID クライアントの一致を検出する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60df6-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="60df6-116">hid_client_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH** よりも大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="60df6-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-117">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-117">Parameters</span></span>

- <span data-ttu-id="60df6-118">**hid_client_name**: HID クライアント名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="60df6-119">**hid_client_handler** HID クライアント ハンドラーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-120">Return Values</span></span>

- <span data-ttu-id="60df6-121">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="60df6-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="60df6-122">**UX_MEMORY_INSUFFICIENT**: (0x12) クライアントへのメモリ割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="60df6-123">**UX_MEMORY_ARRAY_FULL**: (0x1a) の最大数のクライアントが既に登録されています。</span><span class="sxs-lookup"><span data-stu-id="60df6-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="60df6-124">**UX_HOST_CLASS_ALREADY_INSTALLED**: (0x58) このクラスは既に存在します</span><span class="sxs-lookup"><span data-stu-id="60df6-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="60df6-125">例</span><span class="sxs-lookup"><span data-stu-id="60df6-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="60df6-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="60df6-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="60df6-127">HID クラスからのコールバックを登録します。</span><span class="sxs-lookup"><span data-stu-id="60df6-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-128">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="60df6-129">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-129">Description</span></span>

<span data-ttu-id="60df6-130">この関数は、レポートの受信時に HID クラスから HID クライアントにコールバックを登録するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-131">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-131">Parameters</span></span>

- <span data-ttu-id="60df6-132">**hid**: HID クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="60df6-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="60df6-133">**call_back**: call_back 構造体へのポインター</span><span class="sxs-lookup"><span data-stu-id="60df6-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-134">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-134">Return values</span></span>

- <span data-ttu-id="60df6-135">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="60df6-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="60df6-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="60df6-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="60df6-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) レポート コールバックの登録でエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-138">例</span><span class="sxs-lookup"><span data-stu-id="60df6-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="60df6-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="60df6-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="60df6-140">HID クラス インスタンスの定期的なエンドポイントを開始します。</span><span class="sxs-lookup"><span data-stu-id="60df6-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-141">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="60df6-142">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-142">Description</span></span>

<span data-ttu-id="60df6-143">この関数は、この HID クライアントにバインドされている HID クラスのインスタンスに対して定期的な (割り込み) エンドポイントを開始するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="60df6-144">HID クラスは、HID クライアントがアクティブになるまで定期的なエンドポイントを開始できないため、このエンドポイントの起動とレポートの受信は、HID クライアントに委ねられます。</span><span class="sxs-lookup"><span data-stu-id="60df6-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="60df6-145">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-145">Input Parameter</span></span>

- <span data-ttu-id="60df6-146">**hid**: HID クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-147">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-147">Return Values</span></span>

- <span data-ttu-id="60df6-148">**UX_SUCCESS**: (0x00) 定期レポートが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="60df6-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR**: (0x7a) 定期レポートでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="60df6-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-151">例</span><span class="sxs-lookup"><span data-stu-id="60df6-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="60df6-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="60df6-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="60df6-153">HID クラス インスタンスの定期的なエンドポイントを停止します。</span><span class="sxs-lookup"><span data-stu-id="60df6-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="60df6-155">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-155">Description</span></span>

<span data-ttu-id="60df6-156">この関数は、この HID クライアントにバインドされている HID クラスのインスタンスに対して定期的な (割り込み) エンドポイントを停止するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="60df6-157">HID クラスは、HID クライアントが非アクティブ化され、そのすべてのリソースが解放されるまで、定期的なエンドポイントを停止できません。そのため、このエンドポイントの停止は HID クライアントに委ねられます。</span><span class="sxs-lookup"><span data-stu-id="60df6-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="60df6-158">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-158">Input Parameter</span></span>

- <span data-ttu-id="60df6-159">**hid**: HID クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-160">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-160">Return Values</span></span>

- <span data-ttu-id="60df6-161">**UX_SUCCESS**: (0x00) 定期レポートが正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="60df6-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR**: (0x7a) 定期レポートでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="60df6-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません</span><span class="sxs-lookup"><span data-stu-id="60df6-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="60df6-164">例</span><span class="sxs-lookup"><span data-stu-id="60df6-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="60df6-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="60df6-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="60df6-166">HID クラス インスタンスからレポートを取得します。</span><span class="sxs-lookup"><span data-stu-id="60df6-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-167">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="60df6-168">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-168">Description</span></span>

<span data-ttu-id="60df6-169">この関数は、定期的なエンドポイントに依存せずに、デバイスから直接レポートを受信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="60df6-170">このレポートはコントロール エンドポイントから生成されますが、その処理は、定期的なエンドポイントで生成される場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="60df6-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-171">Parameters</span></span>

- <span data-ttu-id="60df6-172">**hid**: HID クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="60df6-173">**client_report**: HID クライアント レポートへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-174">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-174">Return Values</span></span>

- <span data-ttu-id="60df6-175">**UX_SUCCESS**: (0x00) レポートが正常に受信されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="60df6-176">**UX_HOST_CLASS_HID_REPORT_ERROR**: (0x70) クライアント レポートが無効か、転送中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="60df6-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="60df6-178">**UX_BUFFER_OVERFLOW**: (0x5d) 指定されたバッファーは、圧縮されていないレポートを格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-179">例</span><span class="sxs-lookup"><span data-stu-id="60df6-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="60df6-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="60df6-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="60df6-181">要求を送信します</span><span class="sxs-lookup"><span data-stu-id="60df6-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-182">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="60df6-183">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-183">Description</span></span>

<span data-ttu-id="60df6-184">この関数は、デバイスに直接レポートを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-185">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-185">Parameters</span></span>

- <span data-ttu-id="60df6-186">**hid**: HID クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="60df6-187">**client_report**: HID クライアント レポートへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-188">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-188">Return Values</span></span>

- <span data-ttu-id="60df6-189">**UX_SUCCESS**: (0x00) レポートが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="60df6-190">**UX_HOST_CLASS_HID_REPORT_ERROR**: (0x70) クライアント レポートが無効か、転送中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="60df6-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="60df6-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW**: (0x5d) 指定されたバッファーは、圧縮されていないレポートを格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-193">例</span><span class="sxs-lookup"><span data-stu-id="60df6-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="60df6-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="60df6-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="60df6-195">マウス ボタンを取得します。</span><span class="sxs-lookup"><span data-stu-id="60df6-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-196">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="60df6-197">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-197">Description</span></span>

<span data-ttu-id="60df6-198">この関数は、マウス ボタンを取得するために使用されます</span><span class="sxs-lookup"><span data-stu-id="60df6-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-199">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-199">Parameters</span></span>

- <span data-ttu-id="60df6-200">**mouse_instance**: HID マウス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="60df6-201">**mouse_buttons**: 戻りボタンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-202">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-202">Return Values</span></span>

- <span data-ttu-id="60df6-203">**UX_SUCCESS**: (0x00) マウス ボタンが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="60df6-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-205">例</span><span class="sxs-lookup"><span data-stu-id="60df6-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="60df6-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="60df6-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="60df6-207">マウスの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="60df6-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-208">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="60df6-209">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-209">Description</span></span>

<span data-ttu-id="60df6-210">この関数は、X & Y 座標でマウス位置を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-211">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-211">Parameters</span></span>

- <span data-ttu-id="60df6-212">**mouse_instance**: HID マウス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="60df6-213">**mouse_x_position**: X 座標へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="60df6-214">**mouse_y_position**: Y 座標へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-215">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-215">Return Values</span></span>

- <span data-ttu-id="60df6-216">**UX_SUCCESS**: (0x00) X &amp; Y 座標が正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="60df6-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-218">例</span><span class="sxs-lookup"><span data-stu-id="60df6-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="60df6-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="60df6-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="60df6-220">キーボードのキーと状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="60df6-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-221">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="60df6-222">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-222">Description</span></span>

<span data-ttu-id="60df6-223">この関数は、キーボードのキーと状態を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-224">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-224">Parameters</span></span>

- <span data-ttu-id="60df6-225">**keyboard_instance**: HID キーボード インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="60df6-226">**keyboard_key**: キーボードのキー コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="60df6-227">**keyboard_state**: キーボード状態コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-228">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-228">Return Values</span></span>

- <span data-ttu-id="60df6-229">**UX_SUCCESS**: (0x00) キーと状態が正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="60df6-230">**UX_ERROR**: (0xff) レポートする内容はありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="60df6-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="60df6-232">キーボードの状態は、次の値のいずれかを取ります。</span><span class="sxs-lookup"><span data-stu-id="60df6-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="60df6-233">**UX_HID_KEYBOARD_STATE_KEY_UP**: 0x10000</span><span class="sxs-lookup"><span data-stu-id="60df6-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="60df6-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK**: 0x0001</span><span class="sxs-lookup"><span data-stu-id="60df6-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="60df6-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK**: 0x0002</span><span class="sxs-lookup"><span data-stu-id="60df6-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="60df6-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK**: 0x0004</span><span class="sxs-lookup"><span data-stu-id="60df6-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="60df6-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK**: 0x0007</span><span class="sxs-lookup"><span data-stu-id="60df6-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="60df6-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT**: 0x0100</span><span class="sxs-lookup"><span data-stu-id="60df6-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="60df6-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT**: 0x0200</span><span class="sxs-lookup"><span data-stu-id="60df6-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="60df6-240">**UX_HID_KEYBOARD_STATE_SHIFT**: 0x0300</span><span class="sxs-lookup"><span data-stu-id="60df6-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="60df6-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT**: 0x0400</span><span class="sxs-lookup"><span data-stu-id="60df6-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="60df6-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT**: 0x0800</span><span class="sxs-lookup"><span data-stu-id="60df6-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="60df6-243">**UX_HID_KEYBOARD_STATE_ALT**: 0x0a00</span><span class="sxs-lookup"><span data-stu-id="60df6-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="60df6-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL**: 0x1000</span><span class="sxs-lookup"><span data-stu-id="60df6-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="60df6-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL**: 0x2000</span><span class="sxs-lookup"><span data-stu-id="60df6-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="60df6-246">**UX_HID_KEYBOARD_STATE_CTRL**: 0x3000</span><span class="sxs-lookup"><span data-stu-id="60df6-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="60df6-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI**: 0x4000</span><span class="sxs-lookup"><span data-stu-id="60df6-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="60df6-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI**: 0x8000</span><span class="sxs-lookup"><span data-stu-id="60df6-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="60df6-249">**UX_HID_KEYBOARD_STATE_GUI**: 0xa000</span><span class="sxs-lookup"><span data-stu-id="60df6-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="60df6-250">例</span><span class="sxs-lookup"><span data-stu-id="60df6-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="60df6-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="60df6-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="60df6-252">HID キーボードに対して IOCTL 関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-253">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="60df6-254">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-254">Description</span></span>

<span data-ttu-id="60df6-255">この関数は、HID キーボードに対する特定の ioctl 関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="60df6-256">呼び出しはブロック状態であり、エラーが発生した場合またはコマンドが完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="60df6-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-257">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-257">Parameters</span></span>

- <span data-ttu-id="60df6-258">**keyboard_instance**: HID キーボード インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="60df6-259">**ioctl_function**: 実行される ioctl 関数。</span><span class="sxs-lookup"><span data-stu-id="60df6-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="60df6-260">許可されている ioctl 関数については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60df6-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="60df6-261">**parameter**: ioctl に固有のパラメーターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-262">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-262">Return Values</span></span>

- <span data-ttu-id="60df6-263">**UX_SUCCESS**: (0x00) Ioctl 関数が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="60df6-264">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 不明な IOCTL 関数です</span><span class="sxs-lookup"><span data-stu-id="60df6-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="60df6-265">IOCTL 関数</span><span class="sxs-lookup"><span data-stu-id="60df6-265">IOCTL functions</span></span>

- <span data-ttu-id="60df6-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="60df6-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="60df6-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="60df6-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="60df6-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="60df6-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="60df6-269">例 – キーボード レイアウトを変更する</span><span class="sxs-lookup"><span data-stu-id="60df6-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="60df6-270">例 – キーボードのキー デコードを無効にする</span><span class="sxs-lookup"><span data-stu-id="60df6-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="60df6-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="60df6-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="60df6-272">リモート コントロールの使用状況を取得します</span><span class="sxs-lookup"><span data-stu-id="60df6-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-273">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="60df6-274">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-274">Description</span></span>

<span data-ttu-id="60df6-275">この関数は、リモート コントロールの使用状況を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60df6-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-276">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-276">Parameters</span></span>

- <span data-ttu-id="60df6-277">**remote_control_instance**: HID リモート コントロール インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="60df6-278">**usage**: 使用状況へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="60df6-279">**value**: 使用状況の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-280">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-280">Return Values</span></span>

- <span data-ttu-id="60df6-281">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="60df6-282">**UX_ERROR**: (0xff) レポートする内容はありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="60df6-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="60df6-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="60df6-284">想定されるすべての使用状況のリストは、長すぎるためこのユーザー ガイドには掲載できません。</span><span class="sxs-lookup"><span data-stu-id="60df6-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="60df6-285">詳細な説明については、想定される値の完全な一覧が ux_host_class_hid.h にあります。</span><span class="sxs-lookup"><span data-stu-id="60df6-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-286">例</span><span class="sxs-lookup"><span data-stu-id="60df6-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="60df6-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="60df6-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="60df6-288">cdc_acm インターフェイスからの読み取りを実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-289">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="60df6-290">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-290">Description</span></span>

<span data-ttu-id="60df6-291">この関数は、cdc_acm インターフェイスからの読み取りを実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="60df6-292">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="60df6-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-293">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-293">Parameters</span></span>

- <span data-ttu-id="60df6-294">**cdc_acm**: cdc_acm クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="60df6-295">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="60df6-296">**requested_length**: 受信される長さ。</span><span class="sxs-lookup"><span data-stu-id="60df6-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="60df6-297">**actual_length**: 実際に受信された長さ。</span><span class="sxs-lookup"><span data-stu-id="60df6-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-298">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-298">Return Values</span></span>

- <span data-ttu-id="60df6-299">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="60df6-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) cdc_acm インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="60df6-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="60df6-301">**UX_TRANSFER_TIMEOUT**: (0x5c) 転送がタイムアウトし、読み取りは完了していません。</span><span class="sxs-lookup"><span data-stu-id="60df6-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-302">例</span><span class="sxs-lookup"><span data-stu-id="60df6-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="60df6-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="60df6-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="60df6-304">cdc_acm インターフェイスへの書き込みを実行します</span><span class="sxs-lookup"><span data-stu-id="60df6-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-305">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="60df6-306">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-306">Description</span></span>

<span data-ttu-id="60df6-307">この関数は、cdc_acm インターフェイスへの書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="60df6-308">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="60df6-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-309">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-309">Parameters</span></span>

- <span data-ttu-id="60df6-310">**cdc_acm**: cdc_acm クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="60df6-311">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="60df6-312">**requested_length**: 送信される長さ。</span><span class="sxs-lookup"><span data-stu-id="60df6-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="60df6-313">**actual_length**: 実際に送信された長さ。</span><span class="sxs-lookup"><span data-stu-id="60df6-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="60df6-314">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-314">Return Values</span></span>

- <span data-ttu-id="60df6-315">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="60df6-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) cdc_acm インスタンスが無効です。</span><span class="sxs-lookup"><span data-stu-id="60df6-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="60df6-317">**UX_TRANSFER_TIMEOUT**: (0x5c) 転送がタイムアウトし、書き込みは完了していません。</span><span class="sxs-lookup"><span data-stu-id="60df6-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="60df6-318">例</span><span class="sxs-lookup"><span data-stu-id="60df6-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="60df6-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="60df6-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="60df6-320">cdc_acm インターフェイスに対して IOCTL 関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-321">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="60df6-322">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-322">Description</span></span>

<span data-ttu-id="60df6-323">この関数は、cdc_acm インターフェイスに対して特定の ioctl 関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="60df6-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="60df6-324">呼び出しはブロック状態であり、エラーが発生した場合またはコマンドが完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="60df6-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-325">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-325">Parameters</span></span>

- <span data-ttu-id="60df6-326">**cdc_acm**: cdc_acm クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="60df6-327">**ioctl_function**: 実行される ioctl 関数。</span><span class="sxs-lookup"><span data-stu-id="60df6-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="60df6-328">許可されている ioctl 関数については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60df6-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="60df6-329">**parameter**: ioctl に固有のパラメーターへのポインター</span><span class="sxs-lookup"><span data-stu-id="60df6-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="60df6-330">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-330">Return Value</span></span>

- <span data-ttu-id="60df6-331">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="60df6-332">**UX_MEMORY_INSUFFICIENT**: (0x12) 十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="60df6-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) CDC-ACM インスタンスが無効な状態です。</span><span class="sxs-lookup"><span data-stu-id="60df6-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="60df6-334">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 不明な IOCTL 関数です。</span><span class="sxs-lookup"><span data-stu-id="60df6-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="60df6-335">IOCTL 関数:</span><span class="sxs-lookup"><span data-stu-id="60df6-335">IOCTL functions:</span></span>

- <span data-ttu-id="60df6-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="60df6-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="60df6-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="60df6-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="60df6-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="60df6-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="60df6-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="60df6-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="60df6-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="60df6-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="60df6-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="60df6-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="60df6-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="60df6-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="60df6-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="60df6-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="60df6-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="60df6-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="60df6-345">デバイスからのデータのバックグラウンド受信を開始します。</span><span class="sxs-lookup"><span data-stu-id="60df6-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-346">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="60df6-347">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-347">Description</span></span>

<span data-ttu-id="60df6-348">この関数によって USBX が、バックグラウンドでデバイスから継続的にデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="60df6-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="60df6-349">各トランザクションが完了すると、 **cdc_acm_reception** で指定されたコールバックが呼び出され、アプリケーションがトランザクションのデータの後続処理を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="60df6-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="60df6-350">バックグラウンド受信が使用されている間は、**ux_host_class_cdc_acm_read** を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="60df6-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-351">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-351">Parameters</span></span>

- <span data-ttu-id="60df6-352">**cdc_acm**: cdc_acm クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="60df6-353">**cdc_acm_reception**: バックグラウンド受信の動作を定義する値を格納するパラメーターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="60df6-354">このパラメーターのレイアウトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="60df6-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="60df6-355">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-355">Return Value</span></span>

- <span data-ttu-id="60df6-356">**UX_SUCCESS**: (0x00) バックグラウンド受信が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="60df6-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="60df6-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN**: (0x5b) クラス インスタンスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="60df6-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="60df6-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="60df6-359">バックグラウンドでのパケット受信を停止します。</span><span class="sxs-lookup"><span data-stu-id="60df6-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="60df6-360">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="60df6-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="60df6-361">説明</span><span class="sxs-lookup"><span data-stu-id="60df6-361">Description</span></span>

<span data-ttu-id="60df6-362">この関数によって USBX は、**ux_host_class_cdc_acm_reception_start** によって以前に開始されたバックグラウンド受信を停止します。</span><span class="sxs-lookup"><span data-stu-id="60df6-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="60df6-363">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60df6-363">Parameters</span></span>

- <span data-ttu-id="60df6-364">**cdc_acm**: cdc_acm クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="60df6-365">**cdc_acm_reception**: バックグラウンド受信を開始するために使用されたのと同じパラメーターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="60df6-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="60df6-366">このパラメーターのレイアウトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="60df6-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="60df6-367">戻り値</span><span class="sxs-lookup"><span data-stu-id="60df6-367">Return Value</span></span>

- <span data-ttu-id="60df6-368">**UX_SUCCESS**: (0x00) バックグラウンド受信が正常に停止しました。</span><span class="sxs-lookup"><span data-stu-id="60df6-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="60df6-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN**: (0x5b) クラス インスタンスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="60df6-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
