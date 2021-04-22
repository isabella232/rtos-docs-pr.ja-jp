---
title: USBX ホスト クラス API
description: この章では、USBX ホスト クラスの公開されているすべての API について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812929"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="50378-103">第 2 章: USBX ホスト クラス API</span><span class="sxs-lookup"><span data-stu-id="50378-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="50378-104">この章では、USBX ホスト クラスの公開されているすべての API について説明します。</span><span class="sxs-lookup"><span data-stu-id="50378-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="50378-105">クラスごとに次の API について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="50378-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="50378-106">Printer クラス</span><span class="sxs-lookup"><span data-stu-id="50378-106">Printer class</span></span>
- <span data-ttu-id="50378-107">Audio クラス</span><span class="sxs-lookup"><span data-stu-id="50378-107">Audio class</span></span>
- <span data-ttu-id="50378-108">Asix クラス</span><span class="sxs-lookup"><span data-stu-id="50378-108">Asix class</span></span>
- <span data-ttu-id="50378-109">Pima/PTP クラス</span><span class="sxs-lookup"><span data-stu-id="50378-109">Pima/PTP class</span></span>
- <span data-ttu-id="50378-110">Prolific クラス</span><span class="sxs-lookup"><span data-stu-id="50378-110">Prolific class</span></span>
- <span data-ttu-id="50378-111">Generic Serial クラス</span><span class="sxs-lookup"><span data-stu-id="50378-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="50378-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="50378-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="50378-113">プリンター インターフェイスから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="50378-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-114">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-115">説明</span><span class="sxs-lookup"><span data-stu-id="50378-115">Description</span></span>

<span data-ttu-id="50378-116">この関数では、プリンター インターフェイスから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="50378-116">This function reads from the printer interface.</span></span> <span data-ttu-id="50378-117">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="50378-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="50378-118">読み取りは、双方向プリンターでのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="50378-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-119">Parameters</span></span>

- <span data-ttu-id="50378-120">**printer**: printer クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="50378-121">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="50378-122">**requested_length**: 受信される長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="50378-123">**actual_length**: 実際に受信された長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-124">Return Value</span></span>

- <span data-ttu-id="50378-125">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) プリンターが双方向ではないため、関数がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="50378-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="50378-127">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、読み取りが完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="50378-128">例</span><span class="sxs-lookup"><span data-stu-id="50378-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="50378-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="50378-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="50378-130">プリンター インターフェイスに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="50378-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-131">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-132">説明</span><span class="sxs-lookup"><span data-stu-id="50378-132">Description</span></span>

<span data-ttu-id="50378-133">この関数では、プリンター インターフェイスに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="50378-133">This function writes to the printer interface.</span></span> <span data-ttu-id="50378-134">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="50378-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-135">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-135">Parameters</span></span>

- <span data-ttu-id="50378-136">**printer**: printer クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="50378-137">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="50378-138">**requested_length**: 送信される長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="50378-139">**actual_length**: 実際に送信された長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-140">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-140">Return Value</span></span>

- <span data-ttu-id="50378-141">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-142">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、書き込みが完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="50378-143">例</span><span class="sxs-lookup"><span data-stu-id="50378-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="50378-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="50378-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="50378-145">プリンターへのソフト リセットを実行します。</span><span class="sxs-lookup"><span data-stu-id="50378-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-146">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="50378-147">説明</span><span class="sxs-lookup"><span data-stu-id="50378-147">Description</span></span>

<span data-ttu-id="50378-148">この関数では、プリンターへのソフト リセットが実行されます。</span><span class="sxs-lookup"><span data-stu-id="50378-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="50378-149">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-149">Input Parameter</span></span>

- <span data-ttu-id="50378-150">**printer**: printer クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-151">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-151">Return Value</span></span>

- <span data-ttu-id="50378-152">**UX_SUCCESS**: (0x00) リセットが完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="50378-153">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、リセットが完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="50378-154">例</span><span class="sxs-lookup"><span data-stu-id="50378-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="50378-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="50378-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="50378-156">プリンターの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-157">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="50378-158">説明</span><span class="sxs-lookup"><span data-stu-id="50378-158">Description</span></span>

<span data-ttu-id="50378-159">この関数では、プリンターの状態が取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-159">This function obtains the printer status.</span></span> <span data-ttu-id="50378-160">プリンターの状態は、LPT の状態 (1284 標準) に似ています。</span><span class="sxs-lookup"><span data-stu-id="50378-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-161">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-161">Parameters</span></span>

- <span data-ttu-id="50378-162">**printer**: printer クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="50378-163">**printer_status**: 返される状態のアドレス。</span><span class="sxs-lookup"><span data-stu-id="50378-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-164">Return Value</span></span>

- <span data-ttu-id="50378-165">**UX_SUCCESS**: (0x00) リセットが完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="50378-166">**UX_MEMORY_INSUFFICIENT**: (0x12) 操作を実行するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="50378-167">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、リセットが完了していません</span><span class="sxs-lookup"><span data-stu-id="50378-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="50378-168">例</span><span class="sxs-lookup"><span data-stu-id="50378-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="50378-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="50378-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="50378-170">プリンター デバイス ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-171">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="50378-172">説明</span><span class="sxs-lookup"><span data-stu-id="50378-172">Description</span></span>

<span data-ttu-id="50378-173">この関数では、プリンターの IEEE 1284 デバイス ID 文字列 (ビッグ エンディアン形式の最初の 2 バイトの長さを含む) が取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-174">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-174">Parameters</span></span>

- <span data-ttu-id="50378-175">**printer**: printer クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="50378-176">**descriptor_buffer**: IEEE 1284 デバイス ID 文字列 (BE 形式での最初の 2 バイトの長さを含む) を格納するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="50378-177">**length**: バッファーの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="50378-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-178">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-178">Return Value</span></span>

- <span data-ttu-id="50378-179">**UX_SUCCESS** (0x00) 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="50378-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="50378-180">**UX_MEMORY_INSUFFICIENT**: (0x12) 操作を実行するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="50378-181">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、要求が完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="50378-182">**UX_TRANSFER_NOT_READY**: (0x25) デバイスが無効な状態でした (ATTACHED、ADDRESSED、または CONFIGURED である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="50378-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="50378-183">**UX_TRANSFER_STALL**: (0x21) 転送が停止しました。</span><span class="sxs-lookup"><span data-stu-id="50378-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="50378-184">**TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。</span><span class="sxs-lookup"><span data-stu-id="50378-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="50378-185">**TX_SEMAPHORE_ERROR** (0x0C) 計数セマフォ ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="50378-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="50378-186">**TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="50378-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="50378-187">例</span><span class="sxs-lookup"><span data-stu-id="50378-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="50378-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="50378-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="50378-189">オーディオ インターフェイスから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="50378-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-190">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="50378-191">説明</span><span class="sxs-lookup"><span data-stu-id="50378-191">Description</span></span>

<span data-ttu-id="50378-192">この関数では、オーディオ インターフェイスから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="50378-192">This function reads from the audio interface.</span></span> <span data-ttu-id="50378-193">呼び出しは非ブロックです。</span><span class="sxs-lookup"><span data-stu-id="50378-193">The call is non-blocking.</span></span> <span data-ttu-id="50378-194">オーディオ ストリーミング インターフェイスに適切な代替設定が選択されていることをアプリケーションで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50378-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-195">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-195">Parameters</span></span>

- <span data-ttu-id="50378-196">**audio**: audio クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="50378-197">**audio_transfer_request**: オーディオ転送構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-198">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-198">Return Value</span></span>

- <span data-ttu-id="50378-199">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="50378-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="50378-200">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="50378-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="50378-201">例</span><span class="sxs-lookup"><span data-stu-id="50378-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="50378-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="50378-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="50378-203">オーディオ インターフェイスに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="50378-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-204">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="50378-205">説明</span><span class="sxs-lookup"><span data-stu-id="50378-205">Description</span></span>

<span data-ttu-id="50378-206">この関数では、オーディオ インターフェイスに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="50378-206">This function writes to the audio interface.</span></span> <span data-ttu-id="50378-207">呼び出しは非ブロックです。</span><span class="sxs-lookup"><span data-stu-id="50378-207">The call is non-blocking.</span></span> <span data-ttu-id="50378-208">オーディオ ストリーミング インターフェイスに適切な代替設定が選択されていることをアプリケーションで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50378-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-209">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-209">Parameters</span></span>

- <span data-ttu-id="50378-210">**audio**: audio クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="50378-211">**audio_transfer_request**: オーディオ転送構造体へのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-212">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-212">Return Value</span></span>

- <span data-ttu-id="50378-213">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-214">**UX_FUNCTION_NOT_SUPPORTED** (0x54) 関数がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="50378-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="50378-215">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="50378-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="50378-216">例</span><span class="sxs-lookup"><span data-stu-id="50378-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="50378-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="50378-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="50378-218">オーディオ コントロール インターフェイスから特定のコントロールを取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-219">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="50378-220">説明</span><span class="sxs-lookup"><span data-stu-id="50378-220">Description</span></span>

<span data-ttu-id="50378-221">この関数では、オーディオ コントロール インターフェイスから特定のコントロールが取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-222">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-222">Parameters</span></span>

- <span data-ttu-id="50378-223">**audio**: audio クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="50378-224">**audio_control**: オーディオ コントロール構造体へのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-225">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-225">Return Value</span></span>

- <span data-ttu-id="50378-226">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="50378-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="50378-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="50378-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="50378-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="50378-229">例</span><span class="sxs-lookup"><span data-stu-id="50378-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="50378-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="50378-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="50378-231">オーディオ コントロール インターフェイスに特定のコントロールを設定します。</span><span class="sxs-lookup"><span data-stu-id="50378-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-232">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="50378-233">\*\* 説明 \*\*</span><span class="sxs-lookup"><span data-stu-id="50378-233">\*\*Description \*\*</span></span>

<span data-ttu-id="50378-234">この関数では、オーディオ コントロール インターフェイスに特定のコントロールが設定されます。</span><span class="sxs-lookup"><span data-stu-id="50378-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-235">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-235">Parameters</span></span>

- <span data-ttu-id="50378-236">**audio**: audio クラス インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="50378-237">**audio_control**: オーディオ コントロール構造体へのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-238">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-238">Return Value</span></span>

- <span data-ttu-id="50378-239">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="50378-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="50378-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="50378-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="50378-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="50378-242">例</span><span class="sxs-lookup"><span data-stu-id="50378-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="50378-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="50378-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="50378-244">オーディオ ストリーミング インターフェイスの代替設定インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="50378-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-245">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="50378-246">説明</span><span class="sxs-lookup"><span data-stu-id="50378-246">Description</span></span>

<span data-ttu-id="50378-247">この関数では、特定のサンプリング構造体に従って、オーディオ ストリーミング インターフェイスの適切な代替設定インターフェイスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="50378-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-248">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-248">Parameters</span></span>

- <span data-ttu-id="50378-249">**audio**: audio クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="50378-250">**audio_sampling**: オーディオ サンプリング構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-251">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-251">Return Value</span></span>

- <span data-ttu-id="50378-252">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="50378-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="50378-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="50378-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="50378-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="50378-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) サンプリング値の代替設定がありません</span><span class="sxs-lookup"><span data-stu-id="50378-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="50378-256">例</span><span class="sxs-lookup"><span data-stu-id="50378-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="50378-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="50378-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="50378-258">オーディオ ストリーミング インターフェイスの可能なサンプリング設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-259">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="50378-260">説明</span><span class="sxs-lookup"><span data-stu-id="50378-260">Description</span></span>

<span data-ttu-id="50378-261">この関数では、オーディオ ストリーミング インターフェイスの各代替設定で可能なすべてのサンプリング設定が 1 つずつ取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="50378-262">初めて関数を使用するときは、呼び出し元の構造体ポインターのフィールドをすべてリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="50378-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="50378-263">この関数では、代替設定の終了に達していない限り、戻り時にストリーミング値の特定のセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="50378-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="50378-264">この関数が再利用されると、以前のサンプリング値を使用して次のサンプリング値が検索されます。</span><span class="sxs-lookup"><span data-stu-id="50378-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-265">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-265">Parameters</span></span>

- <span data-ttu-id="50378-266">**audio**: audio クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="50378-267">**audio_sampling**: オーディオ サンプリング構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-268">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-268">Return Value</span></span>

- <span data-ttu-id="50378-269">**UX_SUCCESS**: (0x00) データ転送が完了しました</span><span class="sxs-lookup"><span data-stu-id="50378-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="50378-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません</span><span class="sxs-lookup"><span data-stu-id="50378-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="50378-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="50378-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) サンプリング値の代替設定がありません</span><span class="sxs-lookup"><span data-stu-id="50378-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="50378-273">例</span><span class="sxs-lookup"><span data-stu-id="50378-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="50378-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="50378-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="50378-275">asix インターフェイスから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="50378-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-276">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-277">説明</span><span class="sxs-lookup"><span data-stu-id="50378-277">Description</span></span>

<span data-ttu-id="50378-278">この関数では、asix インターフェイスから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="50378-278">This function reads from the asix interface.</span></span> <span data-ttu-id="50378-279">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="50378-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-280">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-280">Parameters</span></span>

- <span data-ttu-id="50378-281">**asix**: .asix クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="50378-282">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="50378-283">**requested_length**: 受信される長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="50378-284">**actual_length**: 実際に受信された長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-285">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-285">Return Value</span></span>

- <span data-ttu-id="50378-286">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-287">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、読み取りが完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="50378-288">例</span><span class="sxs-lookup"><span data-stu-id="50378-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="50378-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="50378-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="50378-290">asix インターフェイスに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="50378-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-291">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="50378-292">説明</span><span class="sxs-lookup"><span data-stu-id="50378-292">Description</span></span>

<span data-ttu-id="50378-293">この関数では、asix インターフェイスに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="50378-293">This function writes to the asix interface.</span></span> <span data-ttu-id="50378-294">呼び出しは非ブロックです。</span><span class="sxs-lookup"><span data-stu-id="50378-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-295">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-295">Parameters</span></span>

- <span data-ttu-id="50378-296">**asix**: .asix クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="50378-297">**packet**: Netx データ パケット</span><span class="sxs-lookup"><span data-stu-id="50378-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-298">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-298">Return Value</span></span>

- <span data-ttu-id="50378-299">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-300">**UX_ERROR**: (0Xff) 転送を要求できませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="50378-301">例</span><span class="sxs-lookup"><span data-stu-id="50378-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="50378-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="50378-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="50378-303">イニシエーターとレスポンダー間のセッションを開きます。</span><span class="sxs-lookup"><span data-stu-id="50378-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-304">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="50378-305">説明</span><span class="sxs-lookup"><span data-stu-id="50378-305">Description</span></span>

<span data-ttu-id="50378-306">この関数では、PIMA イニシエーターと PIMA レスポンダー間のセッションが開かれます。</span><span class="sxs-lookup"><span data-stu-id="50378-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="50378-307">正常にセッションが開かれると、ほとんどの PIMA コマンドを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="50378-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-308">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-308">Parameters</span></span>

- <span data-ttu-id="50378-309">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-310">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-311">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-311">Return Value</span></span>

- <span data-ttu-id="50378-312">**UX_SUCCESS**: (0X00) セッションが正常に開かれました</span><span class="sxs-lookup"><span data-stu-id="50378-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="50378-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201e) 既にセッションが開かれています</span><span class="sxs-lookup"><span data-stu-id="50378-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="50378-314">例</span><span class="sxs-lookup"><span data-stu-id="50378-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="50378-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="50378-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="50378-316">イニシエーターとレスポンダー間のセッションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="50378-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-317">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="50378-318">説明</span><span class="sxs-lookup"><span data-stu-id="50378-318">Description</span></span>

<span data-ttu-id="50378-319">この関数では、PIMA イニシエーターと PIMA レスポンダー間で以前に開かれたセッションが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="50378-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="50378-320">セッションが閉じられると、ほとんどの PIMA コマンドを実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="50378-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-321">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-321">Parameters</span></span>

- <span data-ttu-id="50378-322">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-323">**pima_session**: PIMA セッションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-324">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-324">Return Value</span></span>

- <span data-ttu-id="50378-325">**UX_SUCCESS**: (0x00) セッションが閉じられました。</span><span class="sxs-lookup"><span data-stu-id="50378-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="50378-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="50378-327">例</span><span class="sxs-lookup"><span data-stu-id="50378-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="50378-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="50378-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="50378-329">レスポンダーからストレージ ID の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-330">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="50378-331">説明</span><span class="sxs-lookup"><span data-stu-id="50378-331">Description</span></span>

<span data-ttu-id="50378-332">この関数では、レスポンダーからストレージ ID の配列が取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-333">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-333">Parameters</span></span>

- <span data-ttu-id="50378-334">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-335">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-336">**storage_ids_array**: ストレージ ID が返される配列</span><span class="sxs-lookup"><span data-stu-id="50378-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="50378-337">**storage_id_length**: ストレージ アレイの長さ</span><span class="sxs-lookup"><span data-stu-id="50378-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-338">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-338">Return Value</span></span>

- <span data-ttu-id="50378-339">**UX_SUCCESS**: (0x00) ストレージ ID の配列が事前設定されました</span><span class="sxs-lookup"><span data-stu-id="50378-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="50378-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-341">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-342">例</span><span class="sxs-lookup"><span data-stu-id="50378-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="50378-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="50378-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="50378-344">レスポンダーからストレージ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-345">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="50378-346">説明</span><span class="sxs-lookup"><span data-stu-id="50378-346">Description</span></span>

<span data-ttu-id="50378-347">この関数では、*storage_id* 値のストレージ コンテナーに関するストレージ情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-348">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-348">Parameters</span></span>

- <span data-ttu-id="50378-349">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-350">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-351">**storage_id**: ストレージ コンテナーの ID</span><span class="sxs-lookup"><span data-stu-id="50378-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="50378-352">**ID**: ストレージ情報コンテナーへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-353">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-353">Return Value</span></span>

- <span data-ttu-id="50378-354">**UX_SUCCESS**: (0x00) ストレージ情報が取得されました</span><span class="sxs-lookup"><span data-stu-id="50378-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="50378-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-356">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-357">例</span><span class="sxs-lookup"><span data-stu-id="50378-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="50378-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="50378-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="50378-359">レスポンダーからストレージ コンテナー上のオブジェクトの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-360">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="50378-361">説明</span><span class="sxs-lookup"><span data-stu-id="50378-361">Description</span></span>

<span data-ttu-id="50378-362">この関数では、特定の形式コードに一致する storage_id 値の特定のストレージ コンテナーに格納されているオブジェクトの数が取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="50378-363">オブジェクトの数は、pima_session 構造体の ux_host_class_pima_session_nb_objects フィールドに返されます。</span><span class="sxs-lookup"><span data-stu-id="50378-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-364">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-364">Parameters</span></span>

- <span data-ttu-id="50378-365">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-366">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-367">**storage_id**: ストレージ コンテナーの ID</span><span class="sxs-lookup"><span data-stu-id="50378-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="50378-368">**object_format_code**: オブジェクト形式コード フィルター。</span><span class="sxs-lookup"><span data-stu-id="50378-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="50378-369">オブジェクト形式コードには、次の値のいずれかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="50378-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="50378-370">オブジェクト形式コード</span><span class="sxs-lookup"><span data-stu-id="50378-370">Object Format Code</span></span>               | <span data-ttu-id="50378-371">説明</span><span class="sxs-lookup"><span data-stu-id="50378-371">Description</span></span>   |     <span data-ttu-id="50378-372">USBX コード</span><span class="sxs-lookup"><span data-stu-id="50378-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="50378-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="50378-373">0x3000</span></span>                           | <span data-ttu-id="50378-374">未定義の非イメージ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="50378-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="50378-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="50378-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="50378-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="50378-376">0x3001</span></span>                           | <span data-ttu-id="50378-377">関連付け (フォルダーなど)</span><span class="sxs-lookup"><span data-stu-id="50378-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="50378-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="50378-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="50378-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="50378-379">0x3002</span></span>                           | <span data-ttu-id="50378-380">スクリプト デバイス モデル固有のスクリプト</span><span class="sxs-lookup"><span data-stu-id="50378-380">Script Device-model specific script</span></span> | <span data-ttu-id="50378-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="50378-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="50378-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="50378-382">0x3003</span></span>                           | <span data-ttu-id="50378-383">実行可能デバイス モデル固有のバイナリ実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="50378-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="50378-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="50378-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="50378-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="50378-385">0x3004</span></span>                           | <span data-ttu-id="50378-386">テキスト ファイル</span><span class="sxs-lookup"><span data-stu-id="50378-386">Text Text file</span></span>  |   <span data-ttu-id="50378-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="50378-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="50378-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="50378-388">0x3005</span></span>                           | <span data-ttu-id="50378-389">HTML ハイパー テキスト マークアップ言語ファイル (テキスト)</span><span class="sxs-lookup"><span data-stu-id="50378-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="50378-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="50378-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="50378-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="50378-391">0x3006</span></span>                           | <span data-ttu-id="50378-392">DPOF (Digital Print Order Format) ファイル (テキスト)</span><span class="sxs-lookup"><span data-stu-id="50378-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="50378-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="50378-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="50378-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="50378-394">0x3007</span></span>                           | <span data-ttu-id="50378-395">AIFF オーディオ クリップ</span><span class="sxs-lookup"><span data-stu-id="50378-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="50378-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="50378-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="50378-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="50378-397">0x3008</span></span>                           | <span data-ttu-id="50378-398">WAV オーディオ クリップ</span><span class="sxs-lookup"><span data-stu-id="50378-398">WAV Audio clip</span></span>   |  <span data-ttu-id="50378-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="50378-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="50378-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="50378-400">0x3009</span></span>                           | <span data-ttu-id="50378-401">MP3 オーディオ クリップ</span><span class="sxs-lookup"><span data-stu-id="50378-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="50378-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="50378-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="50378-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="50378-403">0x300A</span></span>                           | <span data-ttu-id="50378-404">AVI ビデオ クリップ</span><span class="sxs-lookup"><span data-stu-id="50378-404">AVI Video clip</span></span>   |  <span data-ttu-id="50378-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="50378-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="50378-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="50378-406">0x300B</span></span>                           | <span data-ttu-id="50378-407">MPEG ビデオ クリップ</span><span class="sxs-lookup"><span data-stu-id="50378-407">MPEG Video clip</span></span>  |  <span data-ttu-id="50378-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="50378-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="50378-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="50378-409">0x300C</span></span>                           | <span data-ttu-id="50378-410">Microsoft ASF (Advanced Streaming Format) (ビデオ)</span><span class="sxs-lookup"><span data-stu-id="50378-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="50378-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="50378-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="50378-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="50378-412">0x3800</span></span>                           | <span data-ttu-id="50378-413">未定義の不明なイメージ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="50378-413">Undefined Unknown image object</span></span> | <span data-ttu-id="50378-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="50378-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="50378-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="50378-415">0x3801</span></span>                           | <span data-ttu-id="50378-416">EXIF/JPEG (Exchangeable File Format)、JEIDA 標準</span><span class="sxs-lookup"><span data-stu-id="50378-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="50378-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="50378-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="50378-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="50378-418">0x3802</span></span>                           | <span data-ttu-id="50378-419">TIFF/EP (Tag Image File Format for Electronic Photography)</span><span class="sxs-lookup"><span data-stu-id="50378-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="50378-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="50378-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="50378-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="50378-421">0x3803</span></span>                           | <span data-ttu-id="50378-422">FlashPix (構造化ストレージ イメージ形式)</span><span class="sxs-lookup"><span data-stu-id="50378-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="50378-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="50378-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="50378-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="50378-424">0x3804</span></span>                           | <span data-ttu-id="50378-425">BMP (Microsoft Windows Bitmap Image) ファイル</span><span class="sxs-lookup"><span data-stu-id="50378-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="50378-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="50378-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="50378-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="50378-427">0x3805</span></span>                           | <span data-ttu-id="50378-428">CIFF (Canon Camera Image File Format)</span><span class="sxs-lookup"><span data-stu-id="50378-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="50378-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="50378-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="50378-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="50378-430">0x3806</span></span>                           | <span data-ttu-id="50378-431">未定義、予約済み</span><span class="sxs-lookup"><span data-stu-id="50378-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="50378-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="50378-432">0x3807</span></span>                           | <span data-ttu-id="50378-433">GIF (Graphics Interchange Format)</span><span class="sxs-lookup"><span data-stu-id="50378-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="50378-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="50378-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="50378-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="50378-435">0x3808</span></span>                           | <span data-ttu-id="50378-436">JFIF (JPEG File Interchange Format)</span><span class="sxs-lookup"><span data-stu-id="50378-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="50378-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="50378-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="50378-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="50378-438">0x3809</span></span>                           | <span data-ttu-id="50378-439">PCD (PhotoCD Image Pac)</span><span class="sxs-lookup"><span data-stu-id="50378-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="50378-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="50378-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="50378-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="50378-441">0x380A</span></span>                           | <span data-ttu-id="50378-442">PICT (Quickdraw イメージ形式)</span><span class="sxs-lookup"><span data-stu-id="50378-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="50378-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="50378-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="50378-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="50378-444">0x380B</span></span>                           | <span data-ttu-id="50378-445">PNG (Portable Network Graphics)</span><span class="sxs-lookup"><span data-stu-id="50378-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="50378-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="50378-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="50378-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="50378-447">0x380C</span></span>                           | <span data-ttu-id="50378-448">未定義、予約済み</span><span class="sxs-lookup"><span data-stu-id="50378-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="50378-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="50378-449">0x380D</span></span>                           | <span data-ttu-id="50378-450">TIFF (Tag Image File Format)</span><span class="sxs-lookup"><span data-stu-id="50378-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="50378-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="50378-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="50378-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="50378-452">0x380E</span></span>                           | <span data-ttu-id="50378-453">TIFF/IT (Tag Image File Format for Information Technology) (グラフィック アート)</span><span class="sxs-lookup"><span data-stu-id="50378-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="50378-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="50378-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="50378-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="50378-455">0x380F</span></span>                           | <span data-ttu-id="50378-456">JP2 JPEG2000 ベースライン ファイル形式</span><span class="sxs-lookup"><span data-stu-id="50378-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="50378-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="50378-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="50378-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="50378-458">0x3810</span></span>                           | <span data-ttu-id="50378-459">JP2 JPEG2000 拡張ファイル形式</span><span class="sxs-lookup"><span data-stu-id="50378-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="50378-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="50378-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="50378-461">MSN 0011 を使用したその他のすべてのコード</span><span class="sxs-lookup"><span data-stu-id="50378-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="50378-462">未定義、将来使用するために予約済み</span><span class="sxs-lookup"><span data-stu-id="50378-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="50378-463">MSN 1011 を使用したその他のすべてのコード</span><span class="sxs-lookup"><span data-stu-id="50378-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="50378-464">ベンダー定義型: イメージ</span><span class="sxs-lookup"><span data-stu-id="50378-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="50378-465">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-465">Return Value</span></span>

- <span data-ttu-id="50378-466">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-468">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-469">例</span><span class="sxs-lookup"><span data-stu-id="50378-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="50378-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="50378-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="50378-471">レスポンダーからオブジェクト ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-472">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="50378-473">説明</span><span class="sxs-lookup"><span data-stu-id="50378-473">Description</span></span>

<span data-ttu-id="50378-474">storage_id パラメーターで示されたストレージ コンテナーに存在するオブジェクト ハンドルの配列が返されます。</span><span class="sxs-lookup"><span data-stu-id="50378-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="50378-475">すべてのストアにわたって集約されたリストが必要な場合は、この値を 0xFFFFFFFF に設定してください。</span><span class="sxs-lookup"><span data-stu-id="50378-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-476">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-476">Parameters</span></span>

- <span data-ttu-id="50378-477">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-478">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-479">**object_handes_array**: ハンドルが返される配列</span><span class="sxs-lookup"><span data-stu-id="50378-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="50378-480">**storage_id_length**: 配列の長さ</span><span class="sxs-lookup"><span data-stu-id="50378-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="50378-481">**storage_id**: ストレージ コンテナーの ID</span><span class="sxs-lookup"><span data-stu-id="50378-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="50378-482">**object_format_code**: オブジェクトの形式コード (関数 ux_host_class_pima_num_objects_get の表を参照)</span><span class="sxs-lookup"><span data-stu-id="50378-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="50378-483">**object_handle_association**: 省略可能なオブジェクトの関連付け値</span><span class="sxs-lookup"><span data-stu-id="50378-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="50378-484">オブジェクト ハンドルの関連付けには、次の表に示す値のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="50378-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="50378-485">AssociationCode</span><span class="sxs-lookup"><span data-stu-id="50378-485">AssociationCode</span></span>                        | <span data-ttu-id="50378-486">AssociationType</span><span class="sxs-lookup"><span data-stu-id="50378-486">AssociationType</span></span>      | <span data-ttu-id="50378-487">解釈</span><span class="sxs-lookup"><span data-stu-id="50378-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="50378-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="50378-488">0x0000</span></span>                                 | <span data-ttu-id="50378-489">未定義。</span><span class="sxs-lookup"><span data-stu-id="50378-489">Undefined</span></span>            | <span data-ttu-id="50378-490">未定義。</span><span class="sxs-lookup"><span data-stu-id="50378-490">Undefined</span></span>            |
| <span data-ttu-id="50378-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="50378-491">0x0001</span></span>                                 | <span data-ttu-id="50378-492">GenericFolder</span><span class="sxs-lookup"><span data-stu-id="50378-492">GenericFolder</span></span>        | <span data-ttu-id="50378-493">未使用</span><span class="sxs-lookup"><span data-stu-id="50378-493">Unused</span></span>               |
| <span data-ttu-id="50378-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="50378-494">0x0002</span></span>                                 | <span data-ttu-id="50378-495">アルバム</span><span class="sxs-lookup"><span data-stu-id="50378-495">Album</span></span>                | <span data-ttu-id="50378-496">予約済み</span><span class="sxs-lookup"><span data-stu-id="50378-496">Reserved</span></span>             |
| <span data-ttu-id="50378-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="50378-497">0x0003</span></span>                                 | <span data-ttu-id="50378-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="50378-498">TimeSequence</span></span>         | <span data-ttu-id="50378-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="50378-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="50378-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="50378-500">0x0004</span></span>                                 | <span data-ttu-id="50378-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="50378-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="50378-502">未使用</span><span class="sxs-lookup"><span data-stu-id="50378-502">Unused</span></span>               |
| <span data-ttu-id="50378-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="50378-503">0x0005</span></span>                                 | <span data-ttu-id="50378-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="50378-504">VerticalPanoramic</span></span>    | <span data-ttu-id="50378-505">未使用</span><span class="sxs-lookup"><span data-stu-id="50378-505">Unused</span></span>               |
| <span data-ttu-id="50378-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="50378-506">0x0006</span></span>                                 | <span data-ttu-id="50378-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="50378-507">2DPanoramic</span></span>          | <span data-ttu-id="50378-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="50378-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="50378-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="50378-509">0x0007</span></span>                                 | <span data-ttu-id="50378-510">AncillaryData</span><span class="sxs-lookup"><span data-stu-id="50378-510">AncillaryData</span></span>        | <span data-ttu-id="50378-511">未定義。</span><span class="sxs-lookup"><span data-stu-id="50378-511">Undefined</span></span>            |
| <span data-ttu-id="50378-512">ビット 15 が 0 に設定されたその他のすべての値</span><span class="sxs-lookup"><span data-stu-id="50378-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="50378-513">予約済み</span><span class="sxs-lookup"><span data-stu-id="50378-513">Reserved</span></span>             | <span data-ttu-id="50378-514">未定義。</span><span class="sxs-lookup"><span data-stu-id="50378-514">Undefined</span></span>            |
| <span data-ttu-id="50378-515">ビット 15 が 1 に設定されたその他のすべての値</span><span class="sxs-lookup"><span data-stu-id="50378-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="50378-516">ベンダー定義</span><span class="sxs-lookup"><span data-stu-id="50378-516">Vendor-Defined</span></span>       | <span data-ttu-id="50378-517">ベンダー定義</span><span class="sxs-lookup"><span data-stu-id="50378-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="50378-518">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-518">Return Value</span></span>

- <span data-ttu-id="50378-519">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-521">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-522">例</span><span class="sxs-lookup"><span data-stu-id="50378-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="50378-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="50378-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="50378-524">レスポンダーからオブジェクト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-525">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="50378-526">説明</span><span class="sxs-lookup"><span data-stu-id="50378-526">Description</span></span>

<span data-ttu-id="50378-527">この関数では、オブジェクト ハンドルに関するオブジェクト情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-528">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-528">Parameters</span></span>

- <span data-ttu-id="50378-529">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-530">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-531">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="50378-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="50378-532">**object**: オブジェクト情報コンテナーへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-533">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-533">Return Value</span></span>

- <span data-ttu-id="50378-534">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-536">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-537">例</span><span class="sxs-lookup"><span data-stu-id="50378-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="50378-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="50378-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="50378-539">レスポンダーにオブジェクト情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="50378-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-540">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="50378-541">説明</span><span class="sxs-lookup"><span data-stu-id="50378-541">Description</span></span>

<span data-ttu-id="50378-542">この関数では、storage_id 値のストレージ コンテナーに関するストレージ情報が送信されます。</span><span class="sxs-lookup"><span data-stu-id="50378-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="50378-543">レスポンダーにオブジェクトを送信する前に、このコマンドがイニシエーターで使用される必要があります。</span><span class="sxs-lookup"><span data-stu-id="50378-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-544">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-544">Parameters</span></span>

- <span data-ttu-id="50378-545">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-546">**pima_session**: PIMA セッションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="50378-547">**storage_id**: 宛先ストレージ ID。</span><span class="sxs-lookup"><span data-stu-id="50378-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="50378-548">**parent_object_id**: オブジェクトを配置する必要があるレスポンダー上の親 ObjectHandle。</span><span class="sxs-lookup"><span data-stu-id="50378-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="50378-549">**object**: オブジェクト情報コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-550">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-550">Return Value</span></span>

- <span data-ttu-id="50378-551">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-553">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-554">例</span><span class="sxs-lookup"><span data-stu-id="50378-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="50378-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="50378-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="50378-556">レスポンダーに格納されているオブジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="50378-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-557">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="50378-558">説明</span><span class="sxs-lookup"><span data-stu-id="50378-558">Description</span></span>

<span data-ttu-id="50378-559">この関数では、読み取りまたは書き込み前にレスポンダーのオブジェクトが開かれます。</span><span class="sxs-lookup"><span data-stu-id="50378-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-560">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-560">Parameters</span></span>

- <span data-ttu-id="50378-561">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-562">**pima_session**: PIMA セッションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="50378-563">**object_handle**: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="50378-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="50378-564">**object**: オブジェクト情報コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-565">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-565">Return Value</span></span>

- <span data-ttu-id="50378-566">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) 既にオブジェクトが開かれています。</span><span class="sxs-lookup"><span data-stu-id="50378-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="50378-569">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-570">例</span><span class="sxs-lookup"><span data-stu-id="50378-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="50378-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="50378-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="50378-572">レスポンダーに格納されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-573">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-574">説明</span><span class="sxs-lookup"><span data-stu-id="50378-574">Description</span></span>

<span data-ttu-id="50378-575">この関数では、レスポンダーのオブジェクトが取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-576">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-576">Parameters</span></span>

- <span data-ttu-id="50378-577">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-578">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-579">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="50378-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="50378-580">**object**: オブジェクト情報コンテナーへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="50378-581">**object_buffer**: オブジェクト データのアドレス</span><span class="sxs-lookup"><span data-stu-id="50378-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="50378-582">**object_buffer_length**: 要求されたオブジェクトの長さ</span><span class="sxs-lookup"><span data-stu-id="50378-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="50378-583">**object_actual_length**: 返されたオブジェクトの長さ</span><span class="sxs-lookup"><span data-stu-id="50378-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-584">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-584">Return Value</span></span>

- <span data-ttu-id="50378-585">**UX_SUCCESS**: (0x00) オブジェクトが転送されました</span><span class="sxs-lookup"><span data-stu-id="50378-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="50378-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="50378-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトへのアクセスが拒否されました</span><span class="sxs-lookup"><span data-stu-id="50378-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="50378-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 転送が完了していません</span><span class="sxs-lookup"><span data-stu-id="50378-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="50378-590">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="50378-591">**UX_TRANSFER_ERROR**: (0x23) オブジェクトの読み取り中に転送エラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="50378-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="50378-592">例</span><span class="sxs-lookup"><span data-stu-id="50378-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="50378-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="50378-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="50378-594">レスポンダーに格納されているオブジェクトを送信します。</span><span class="sxs-lookup"><span data-stu-id="50378-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-595">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="50378-596">説明</span><span class="sxs-lookup"><span data-stu-id="50378-596">Description</span></span>

<span data-ttu-id="50378-597">この関数では、レスポンダーにオブジェクトが送信されます。</span><span class="sxs-lookup"><span data-stu-id="50378-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-598">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-598">Parameters</span></span>

- <span data-ttu-id="50378-599">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-600">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-601">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="50378-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="50378-602">**object**: オブジェクト情報コンテナーへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="50378-603">**object_buffer**: オブジェクト データのアドレス</span><span class="sxs-lookup"><span data-stu-id="50378-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="50378-604">**object_buffer_length**: 要求されたオブジェクトの長さ</span><span class="sxs-lookup"><span data-stu-id="50378-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-605">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-605">Return Value</span></span>

- <span data-ttu-id="50378-606">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした</span><span class="sxs-lookup"><span data-stu-id="50378-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="50378-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="50378-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトへのアクセスが拒否されました</span><span class="sxs-lookup"><span data-stu-id="50378-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="50378-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 転送が完了していません</span><span class="sxs-lookup"><span data-stu-id="50378-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="50378-611">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="50378-612">**UX_TRANSFER_ERROR**: (0x23) オブジェクトの書き込み中に転送エラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="50378-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="50378-613">例</span><span class="sxs-lookup"><span data-stu-id="50378-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="50378-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="50378-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="50378-615">レスポンダーに格納されている thumb オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="50378-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-616">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-617">説明</span><span class="sxs-lookup"><span data-stu-id="50378-617">Description</span></span>

<span data-ttu-id="50378-618">この関数では、レスポンダーの thumb オブジェクトが取得されます。</span><span class="sxs-lookup"><span data-stu-id="50378-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-619">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-619">Parameters</span></span>

- <span data-ttu-id="50378-620">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-621">**pima_session**: PIMA セッションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="50378-622">**object_handle**: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="50378-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="50378-623">**object**: オブジェクト情報コンテナーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="50378-624">**thumb_buffer**: thumb オブジェクト データのアドレス。</span><span class="sxs-lookup"><span data-stu-id="50378-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="50378-625">**thumb_buffer_length**: 要求された thumb オブジェクトの長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="50378-626">**thumb_actual_length**: 返された thumb オブジェクトの長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-627">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-627">Return Value</span></span>

- <span data-ttu-id="50378-628">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="50378-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="50378-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトへのアクセスが拒否されました。</span><span class="sxs-lookup"><span data-stu-id="50378-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="50378-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 転送が完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="50378-633">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="50378-634">**UX_TRANSFER_ERROR**: (0x23) オブジェクトの読み取り中に転送エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="50378-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="50378-635">例</span><span class="sxs-lookup"><span data-stu-id="50378-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="50378-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="50378-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="50378-637">レスポンダーに格納されているオブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="50378-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-638">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="50378-639">説明</span><span class="sxs-lookup"><span data-stu-id="50378-639">Description</span></span>

<span data-ttu-id="50378-640">この関数では、レスポンダーのオブジェクトが削除されます。</span><span class="sxs-lookup"><span data-stu-id="50378-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-641">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-641">Parameters</span></span>

- <span data-ttu-id="50378-642">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-643">**pima_session**: PIMA セッションへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="50378-644">**object_handle**: オブジェクトのハンドル</span><span class="sxs-lookup"><span data-stu-id="50378-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-645">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-645">Return Value</span></span>

- <span data-ttu-id="50378-646">**UX_SUCCESS**: (0x00) オブジェクトが削除されました。</span><span class="sxs-lookup"><span data-stu-id="50378-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="50378-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="50378-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトを削除できません。</span><span class="sxs-lookup"><span data-stu-id="50378-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="50378-649">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-650">例</span><span class="sxs-lookup"><span data-stu-id="50378-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="50378-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="50378-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="50378-652">レスポンダーに格納されているオブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="50378-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-653">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="50378-654">説明</span><span class="sxs-lookup"><span data-stu-id="50378-654">Description</span></span>

<span data-ttu-id="50378-655">この関数では、レスポンダーのオブジェクトが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="50378-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-656">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-656">Parameters</span></span>

- <span data-ttu-id="50378-657">**pima**: pima クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="50378-658">**pima_session**: PIMA セッションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="50378-659">**object_handle**: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="50378-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="50378-660">**object**: オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-661">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-661">Return Value</span></span>

- <span data-ttu-id="50378-662">**UX_SUCCESS**: (0x00) オブジェクトが閉じられました。</span><span class="sxs-lookup"><span data-stu-id="50378-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="50378-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="50378-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。</span><span class="sxs-lookup"><span data-stu-id="50378-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="50378-665">**UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="50378-666">例</span><span class="sxs-lookup"><span data-stu-id="50378-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="50378-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="50378-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="50378-668">汎用シリアル インターフェイスから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="50378-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-669">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-670">説明</span><span class="sxs-lookup"><span data-stu-id="50378-670">Description</span></span>

<span data-ttu-id="50378-671">この関数では、汎用シリアル インターフェイスから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="50378-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="50378-672">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="50378-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-673">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-673">Parameters</span></span>

- <span data-ttu-id="50378-674">**gser**: gser クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="50378-675">**interface_index** 読み取り元のインターフェイス インデックス。</span><span class="sxs-lookup"><span data-stu-id="50378-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="50378-676">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="50378-677">**requested_length**: 受信される長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="50378-678">**actual_length**: 実際に受信された長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-679">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-679">Return Value</span></span>

- <span data-ttu-id="50378-680">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-681">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、読み取りが完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="50378-682">例</span><span class="sxs-lookup"><span data-stu-id="50378-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="50378-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="50378-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="50378-684">汎用シリアル インターフェイスに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="50378-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-685">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="50378-686">説明</span><span class="sxs-lookup"><span data-stu-id="50378-686">Description</span></span>

<span data-ttu-id="50378-687">この関数では、汎用シリアル インターフェイスに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="50378-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="50378-688">呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="50378-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-689">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-689">Parameters</span></span>

- <span data-ttu-id="50378-690">**gser**: gser クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="50378-691">**interface_index**: 書き込み先のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="50378-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="50378-692">**data_pointer**: データ ペイロードのバッファー アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="50378-693">**requested_length**: 送信される長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="50378-694">**actual_length**: 実際に送信された長さ。</span><span class="sxs-lookup"><span data-stu-id="50378-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-695">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-695">Return Value</span></span>

- <span data-ttu-id="50378-696">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-697">**UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、書き込みが完了していません。</span><span class="sxs-lookup"><span data-stu-id="50378-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="50378-698">例</span><span class="sxs-lookup"><span data-stu-id="50378-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="50378-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="50378-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="50378-700">汎用シリアル インターフェイスへの IOCTL 関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="50378-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-701">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="50378-702">説明</span><span class="sxs-lookup"><span data-stu-id="50378-702">Description</span></span>

<span data-ttu-id="50378-703">この関数では、gser インターフェイスへの特定の ioctl 関数が実行されます。</span><span class="sxs-lookup"><span data-stu-id="50378-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="50378-704">呼び出しはブロック状態であり、エラーが発生した場合またはコマンドが完了した場合にのみ復帰します。</span><span class="sxs-lookup"><span data-stu-id="50378-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-705">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-705">Parameters</span></span>

- <span data-ttu-id="50378-706">**gser**: gser クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="50378-707">**ioctl_function**: 実行される ioctl 関数。</span><span class="sxs-lookup"><span data-stu-id="50378-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="50378-708">許可されている ioctl 関数については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50378-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="50378-709">**parameter**: ioctl に固有のパラメーターへのポインター</span><span class="sxs-lookup"><span data-stu-id="50378-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-710">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-710">Return Value</span></span>

- <span data-ttu-id="50378-711">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-712">**UX_MEMORY_INSUFFICIENT**: (0x12) 十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="50378-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="50378-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) クラス インスタンスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="50378-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 不明な IOCTL 関数です。</span><span class="sxs-lookup"><span data-stu-id="50378-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="50378-715">IOCTL 関数</span><span class="sxs-lookup"><span data-stu-id="50378-715">IOCTL functions</span></span>

- <span data-ttu-id="50378-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="50378-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="50378-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="50378-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="50378-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="50378-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="50378-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="50378-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="50378-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="50378-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="50378-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="50378-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="50378-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="50378-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="50378-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="50378-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="50378-724">例</span><span class="sxs-lookup"><span data-stu-id="50378-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="50378-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="50378-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="50378-726">汎用シリアル インターフェイスで受信を開始します。</span><span class="sxs-lookup"><span data-stu-id="50378-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-727">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="50378-728">説明</span><span class="sxs-lookup"><span data-stu-id="50378-728">Description</span></span>

<span data-ttu-id="50378-729">この関数では、汎用シリアル クラス インターフェイスで受信が開始されます。</span><span class="sxs-lookup"><span data-stu-id="50378-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="50378-730">この関数では、非ブロック受信が許可されています。</span><span class="sxs-lookup"><span data-stu-id="50378-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="50378-731">バッファーが受信されると、アプリケーションへのコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="50378-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-732">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-732">Parameters</span></span>

- <span data-ttu-id="50378-733">**gser**: gser クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="50378-734">**gser_reception**: 受信パラメーターを含む構造体</span><span class="sxs-lookup"><span data-stu-id="50378-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-735">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-735">Return Value</span></span>

- <span data-ttu-id="50378-736">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-737">**UX_HOST_CLASS_UNKNOWN**: (0x59) クラス インスタンスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="50378-738">**UX_ERROR** (0X01) エラー</span><span class="sxs-lookup"><span data-stu-id="50378-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="50378-739">例</span><span class="sxs-lookup"><span data-stu-id="50378-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="50378-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="50378-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="50378-741">汎用シリアル インターフェイスで受信を停止します。</span><span class="sxs-lookup"><span data-stu-id="50378-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="50378-742">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="50378-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="50378-743">説明</span><span class="sxs-lookup"><span data-stu-id="50378-743">Description</span></span>

<span data-ttu-id="50378-744">この関数では、汎用シリアル クラス インターフェイスで受信が停止されます。</span><span class="sxs-lookup"><span data-stu-id="50378-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="50378-745">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50378-745">Parameters</span></span>

- <span data-ttu-id="50378-746">**gser**: gser クラス インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50378-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="50378-747">**gser_reception**: 受信パラメーターを含む構造体</span><span class="sxs-lookup"><span data-stu-id="50378-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="50378-748">戻り値</span><span class="sxs-lookup"><span data-stu-id="50378-748">Return Value</span></span>

- <span data-ttu-id="50378-749">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="50378-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="50378-750">**UX_HOST_CLASS_UNKNOWN**: (0x59) クラス インスタンスが正しくありません</span><span class="sxs-lookup"><span data-stu-id="50378-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="50378-751">**UX_ERROR** (0X01) エラー</span><span class="sxs-lookup"><span data-stu-id="50378-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="50378-752">例</span><span class="sxs-lookup"><span data-stu-id="50378-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
