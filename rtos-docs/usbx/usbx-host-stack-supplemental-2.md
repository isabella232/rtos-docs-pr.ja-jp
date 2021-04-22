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
# <a name="chapter-2-usbx-host-classes-api"></a>第 2 章: USBX ホスト クラス API

この章では、USBX ホスト クラスの公開されているすべての API について説明します。 クラスごとに次の API について詳しく説明します。

- Printer クラス
- Audio クラス
- Asix クラス
- Pima/PTP クラス
- Prolific クラス
- Generic Serial クラス

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

プリンター インターフェイスから読み取ります。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>説明

この関数では、プリンター インターフェイスから読み取られます。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。 読み取りは、双方向プリンターでのみ許可されます。

### <a name="parameters"></a>パラメーター

- **printer**: printer クラス インスタンスへのポインター。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 受信される長さ。
- **actual_length**: 実際に受信された長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) プリンターが双方向ではないため、関数がサポートされません。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、読み取りが完了していません。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

プリンター インターフェイスに書き込みます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>説明

この関数では、プリンター インターフェイスに書き込まれます。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **printer**: printer クラス インスタンスへのポインター。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 送信される長さ。
- **actual_length**: 実際に送信された長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、書き込みが完了していません。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

プリンターへのソフト リセットを実行します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>説明

この関数では、プリンターへのソフト リセットが実行されます。

### <a name="input-parameter"></a>入力パラメーター

- **printer**: printer クラス インスタンスへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) リセットが完了しました。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、リセットが完了していません。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

プリンターの状態を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>説明

この関数では、プリンターの状態が取得されます。 プリンターの状態は、LPT の状態 (1284 標準) に似ています。

### <a name="parameters"></a>パラメーター

- **printer**: printer クラス インスタンスへのポインター。
- **printer_status**: 返される状態のアドレス。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) リセットが完了しました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) 操作を実行するのに十分なメモリがありません。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、リセットが完了していません

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

プリンター デバイス ID を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>説明

この関数では、プリンターの IEEE 1284 デバイス ID 文字列 (ビッグ エンディアン形式の最初の 2 バイトの長さを含む) が取得されます。

### <a name="parameters"></a>パラメーター

- **printer**: printer クラス インスタンスへのポインター。
- **descriptor_buffer**: IEEE 1284 デバイス ID 文字列 (BE 形式での最初の 2 バイトの長さを含む) を格納するバッファーへのポインター 
- **length**: バッファーの長さ (バイト単位)。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS** (0x00) 操作に成功しました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) 操作を実行するのに十分なメモリがありません。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、要求が完了していません。
- **UX_TRANSFER_NOT_READY**: (0x25) デバイスが無効な状態でした (ATTACHED、ADDRESSED、または CONFIGURED である必要があります)。
- **UX_TRANSFER_STALL**: (0x21) 転送が停止しました。
- **TX_WAIT_ABORTED** (0x1A) 別のスレッド、タイマー、または ISR によって中断が中止されました。
- **TX_SEMAPHORE_ERROR** (0x0C) 計数セマフォ ポインターが無効です。
- **TX_WAIT_ERROR** (0x04) 非スレッドからの呼び出し時に、TX_NO_WAIT 以外の待機オプションが指定されました。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

オーディオ インターフェイスから読み取ります。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>説明

この関数では、オーディオ インターフェイスから読み取られます。 呼び出しは非ブロックです。 オーディオ ストリーミング インターフェイスに適切な代替設定が選択されていることをアプリケーションで確認する必要があります。

### <a name="parameters"></a>パラメーター

- **audio**: audio クラス インスタンスへのポインター。
- **audio_transfer_request**: オーディオ転送構造体へのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません

### <a name="example"></a>例

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

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

オーディオ インターフェイスに書き込みます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>説明

この関数では、オーディオ インターフェイスに書き込まれます。 呼び出しは非ブロックです。 オーディオ ストリーミング インターフェイスに適切な代替設定が選択されていることをアプリケーションで確認する必要があります。

### <a name="parameters"></a>パラメーター

- **audio**: audio クラス インスタンスへのポインター
- **audio_transfer_request**: オーディオ転送構造体へのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) 関数がサポートされていません。
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

オーディオ コントロール インターフェイスから特定のコントロールを取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>説明

この関数では、オーディオ コントロール インターフェイスから特定のコントロールが取得されます。

### <a name="parameters"></a>パラメーター

- **audio**: audio クラス インスタンスへのポインター
- **audio_control**: オーディオ コントロール構造体へのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません

### <a name="example"></a>例

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

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

オーディオ コントロール インターフェイスに特定のコントロールを設定します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

** 説明 **

この関数では、オーディオ コントロール インターフェイスに特定のコントロールが設定されます。

### <a name="parameters"></a>パラメーター

- **audio**: audio クラス インスタンスへのポインター
- **audio_control**: オーディオ コントロール構造体へのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません

### <a name="example"></a>例

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

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

オーディオ ストリーミング インターフェイスの代替設定インターフェイスを設定します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>説明

この関数では、特定のサンプリング構造体に従って、オーディオ ストリーミング インターフェイスの適切な代替設定インターフェイスが設定されます。

### <a name="parameters"></a>パラメーター

- **audio**: audio クラス インスタンスへのポインター。
- **audio_sampling**: オーディオ サンプリング構造体へのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません
- **UX_NO_ALTERNATE_SETTING**: (0x5e) サンプリング値の代替設定がありません

### <a name="example"></a>例

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

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

オーディオ ストリーミング インターフェイスの可能なサンプリング設定を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>説明

この関数では、オーディオ ストリーミング インターフェイスの各代替設定で可能なすべてのサンプリング設定が 1 つずつ取得されます。 初めて関数を使用するときは、呼び出し元の構造体ポインターのフィールドをすべてリセットする必要があります。 この関数では、代替設定の終了に達していない限り、戻り時にストリーミング値の特定のセットが返されます。 この関数が再利用されると、以前のサンプリング値を使用して次のサンプリング値が検索されます。

### <a name="parameters"></a>パラメーター

- **audio**: audio クラス インスタンスへのポインター。
- **audio_sampling**: オーディオ サンプリング構造体へのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 関数がサポートされていません
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0X81) インターフェイスが正しくありません
- **UX_NO_ALTERNATE_SETTING**: (0x5e) サンプリング値の代替設定がありません

### <a name="example"></a>例

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

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

asix インターフェイスから読み取ります。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>説明

この関数では、asix インターフェイスから読み取られます。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **asix**: .asix クラス インスタンスへのポインター。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 受信される長さ。
- **actual_length**: 実際に受信された長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、読み取りが完了していません。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

asix インターフェイスに書き込みます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>説明

この関数では、asix インターフェイスに書き込まれます。 呼び出しは非ブロックです。

### <a name="parameters"></a>パラメーター

- **asix**: .asix クラス インスタンスへのポインター。
- **packet**: Netx データ パケット

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_ERROR**: (0Xff) 転送を要求できませんでした。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

イニシエーターとレスポンダー間のセッションを開きます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>説明

この関数では、PIMA イニシエーターと PIMA レスポンダー間のセッションが開かれます。 正常にセッションが開かれると、ほとんどの PIMA コマンドを実行できるようになります。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0X00) セッションが正常に開かれました
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201e) 既にセッションが開かれています

### <a name="example"></a>例

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

イニシエーターとレスポンダー間のセッションを閉じます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>説明

この関数では、PIMA イニシエーターと PIMA レスポンダー間で以前に開かれたセッションが閉じられます。 セッションが閉じられると、ほとんどの PIMA コマンドを実行できなくなります。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) セッションが閉じられました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。

### <a name="example"></a>例

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

レスポンダーからストレージ ID の配列を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>説明

この関数では、レスポンダーからストレージ ID の配列が取得されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **storage_ids_array**: ストレージ ID が返される配列
- **storage_id_length**: ストレージ アレイの長さ

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) ストレージ ID の配列が事前設定されました
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

レスポンダーからストレージ情報を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>説明

この関数では、*storage_id* 値のストレージ コンテナーに関するストレージ情報が取得されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **storage_id**: ストレージ コンテナーの ID
- **ID**: ストレージ情報コンテナーへのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) ストレージ情報が取得されました
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

レスポンダーからストレージ コンテナー上のオブジェクトの数を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>説明

この関数では、特定の形式コードに一致する storage_id 値の特定のストレージ コンテナーに格納されているオブジェクトの数が取得されます。 オブジェクトの数は、pima_session 構造体の ux_host_class_pima_session_nb_objects フィールドに返されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **storage_id**: ストレージ コンテナーの ID
- **object_format_code**: オブジェクト形式コード フィルター。

オブジェクト形式コードには、次の値のいずれかを設定できます。

| オブジェクト形式コード               | 説明   |     USBX コード                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | 未定義の非イメージ オブジェクト | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | 関連付け (フォルダーなど) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | スクリプト デバイス モデル固有のスクリプト | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | 実行可能デバイス モデル固有のバイナリ実行可能ファイル | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | テキスト ファイル  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | HTML ハイパー テキスト マークアップ言語ファイル (テキスト) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | DPOF (Digital Print Order Format) ファイル (テキスト) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | AIFF オーディオ クリップ  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | WAV オーディオ クリップ   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | MP3 オーディオ クリップ   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | AVI ビデオ クリップ   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | MPEG ビデオ クリップ  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | Microsoft ASF (Advanced Streaming Format) (ビデオ) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | 未定義の不明なイメージ オブジェクト | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | EXIF/JPEG (Exchangeable File Format)、JEIDA 標準 | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | TIFF/EP (Tag Image File Format for Electronic Photography) | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | FlashPix (構造化ストレージ イメージ形式) | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP (Microsoft Windows Bitmap Image) ファイル | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | CIFF (Canon Camera Image File Format) | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | 未定義、予約済み |  |
| 0x3807                           | GIF (Graphics Interchange Format) | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | JFIF (JPEG File Interchange Format) | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD (PhotoCD Image Pac) | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | PICT (Quickdraw イメージ形式) | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | PNG (Portable Network Graphics) | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | 未定義、予約済み |   |
| 0x380D                           | TIFF (Tag Image File Format) | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | TIFF/IT (Tag Image File Format for Information Technology) (グラフィック アート) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | JP2 JPEG2000 ベースライン ファイル形式 | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | JP2 JPEG2000 拡張ファイル形式 | UX_HOST_CLASS_PIMA_OFC_JPX         |
| MSN 0011 を使用したその他のすべてのコード | 未定義、将来使用するために予約済み |                                    |
| MSN 1011 を使用したその他のすべてのコード | ベンダー定義型: イメージ |                                    |

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

レスポンダーからオブジェクト ハンドルを取得します。

### <a name="prototype"></a>プロトタイプ

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

### <a name="description"></a>説明

storage_id パラメーターで示されたストレージ コンテナーに存在するオブジェクト ハンドルの配列が返されます。 すべてのストアにわたって集約されたリストが必要な場合は、この値を 0xFFFFFFFF に設定してください。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **object_handes_array**: ハンドルが返される配列
- **storage_id_length**: 配列の長さ
- **storage_id**: ストレージ コンテナーの ID
- **object_format_code**: オブジェクトの形式コード (関数 ux_host_class_pima_num_objects_get の表を参照)
- **object_handle_association**: 省略可能なオブジェクトの関連付け値

オブジェクト ハンドルの関連付けには、次の表に示す値のいずれかを指定できます。

| AssociationCode                        | AssociationType      | 解釈       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | 未定義。            | 未定義。            |
| 0x0001                                 | GenericFolder        | 未使用               |
| 0x0002                                 | アルバム                | 予約済み             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | 未使用               |
| 0x0005                                 | VerticalPanoramic    | 未使用               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | AncillaryData        | 未定義。            |
| ビット 15 が 0 に設定されたその他のすべての値  | 予約済み             | 未定義。            |
| ビット 15 が 1 に設定されたその他のすべての値        | ベンダー定義       | ベンダー定義       |

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

レスポンダーからオブジェクト情報を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>説明

この関数では、オブジェクト ハンドルに関するオブジェクト情報が取得されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **object_handle**: オブジェクトのハンドル
- **object**: オブジェクト情報コンテナーへのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

レスポンダーにオブジェクト情報を送信します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>説明

この関数では、storage_id 値のストレージ コンテナーに関するストレージ情報が送信されます。 レスポンダーにオブジェクトを送信する前に、このコマンドがイニシエーターで使用される必要があります。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター。
- **storage_id**: 宛先ストレージ ID。
- **parent_object_id**: オブジェクトを配置する必要があるレスポンダー上の親 ObjectHandle。
- **object**: オブジェクト情報コンテナーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

レスポンダーに格納されているオブジェクトを開きます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>説明

この関数では、読み取りまたは書き込み前にレスポンダーのオブジェクトが開かれます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター。
- **object_handle**: オブジェクトのハンドル。
- **object**: オブジェクト情報コンテナーへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) 既にオブジェクトが開かれています。
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

レスポンダーに格納されているオブジェクトを取得します。

### <a name="prototype"></a>プロトタイプ

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

### <a name="description"></a>説明

この関数では、レスポンダーのオブジェクトが取得されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **object_handle**: オブジェクトのハンドル
- **object**: オブジェクト情報コンテナーへのポインター
- **object_buffer**: オブジェクト データのアドレス
- **object_buffer_length**: 要求されたオブジェクトの長さ
- **object_actual_length**: 返されたオブジェクトの長さ

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) オブジェクトが転送されました
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトへのアクセスが拒否されました
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 転送が完了していません
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。
- **UX_TRANSFER_ERROR**: (0x23) オブジェクトの読み取り中に転送エラーが発生しました

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

レスポンダーに格納されているオブジェクトを送信します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>説明

この関数では、レスポンダーにオブジェクトが送信されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **object_handle**: オブジェクトのハンドル
- **object**: オブジェクト情報コンテナーへのポインター
- **object_buffer**: オブジェクト データのアドレス
- **object_buffer_length**: 要求されたオブジェクトの長さ

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトへのアクセスが拒否されました
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 転送が完了していません
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。
- **UX_TRANSFER_ERROR**: (0x23) オブジェクトの書き込み中に転送エラーが発生しました

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

レスポンダーに格納されている thumb オブジェクトを取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>説明

この関数では、レスポンダーの thumb オブジェクトが取得されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター。
- **object_handle**: オブジェクトのハンドル。
- **object**: オブジェクト情報コンテナーへのポインター。
- **thumb_buffer**: thumb オブジェクト データのアドレス。
- **thumb_buffer_length**: 要求された thumb オブジェクトの長さ。
- **thumb_actual_length**: 返された thumb オブジェクトの長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトへのアクセスが拒否されました。
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 転送が完了していません。
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。
- **UX_TRANSFER_ERROR**: (0x23) オブジェクトの読み取り中に転送エラーが発生しました。

### <a name="example"></a>例

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

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

レスポンダーに格納されているオブジェクトを削除します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>説明

この関数では、レスポンダーのオブジェクトが削除されます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター
- **object_handle**: オブジェクトのハンドル

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) オブジェクトが削除されました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) オブジェクトを削除できません。
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

レスポンダーに格納されているオブジェクトを閉じます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>説明

この関数では、レスポンダーのオブジェクトが閉じられます。

### <a name="parameters"></a>パラメーター

- **pima**: pima クラス インスタンスへのポインター。
- **pima_session**: PIMA セッションへのポインター。
- **object_handle**: オブジェクトのハンドル。
- **object**: オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) オブジェクトが閉じられました。
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) セッションが開かれませんでした。
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) オブジェクトが開かれませんでした。
- **UX_MEMORY_INSUFFICIENT**: (0x12) PIMA コマンドを作成するのに十分なメモリがありません。

### <a name="example"></a>例

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

汎用シリアル インターフェイスから読み取ります。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>説明

この関数では、汎用シリアル インターフェイスから読み取られます。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **gser**: gser クラス インスタンスへのポインター。
- **interface_index** 読み取り元のインターフェイス インデックス。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 受信される長さ。
- **actual_length**: 実際に受信された長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、読み取りが完了していません。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

汎用シリアル インターフェイスに書き込みます。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>説明

この関数では、汎用シリアル インターフェイスに書き込まれます。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **gser**: gser クラス インスタンスへのポインター。
- **interface_index**: 書き込み先のインターフェイス。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 送信される長さ。
- **actual_length**: 実際に送信された長さ。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_TRANSFER_TIMEOUT**: (0X5c) 転送がタイムアウトし、書き込みが完了していません。

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

汎用シリアル インターフェイスへの IOCTL 関数を実行します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>説明

この関数では、gser インターフェイスへの特定の ioctl 関数が実行されます。 呼び出しはブロック状態であり、エラーが発生した場合またはコマンドが完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **gser**: gser クラス インスタンスへのポインター。
- **ioctl_function**: 実行される ioctl 関数。 許可されている ioctl 関数については、次の表を参照してください。
- **parameter**: ioctl に固有のパラメーターへのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) 十分なメモリがありません。
- **UX_HOST_CLASS_UNKNOWN**: (0x59) クラス インスタンスが正しくありません
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 不明な IOCTL 関数です。

### <a name="ioctl-functions"></a>IOCTL 関数

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>例

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

汎用シリアル インターフェイスで受信を開始します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>説明

この関数では、汎用シリアル クラス インターフェイスで受信が開始されます。 この関数では、非ブロック受信が許可されています。 バッファーが受信されると、アプリケーションへのコールバックが呼び出されます。

### <a name="parameters"></a>パラメーター

- **gser**: gser クラス インスタンスへのポインター。
- **gser_reception**: 受信パラメーターを含む構造体

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_UNKNOWN**: (0x59) クラス インスタンスが正しくありません
- **UX_ERROR** (0X01) エラー

### <a name="example"></a>例

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

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

汎用シリアル インターフェイスで受信を停止します。

### <a name="prototype"></a>プロトタイプ

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>説明

この関数では、汎用シリアル クラス インターフェイスで受信が停止されます。

### <a name="parameters"></a>パラメーター

- **gser**: gser クラス インスタンスへのポインター。
- **gser_reception**: 受信パラメーターを含む構造体

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_UNKNOWN**: (0x59) クラス インスタンスが正しくありません
- **UX_ERROR** (0X01) エラー

### <a name="example"></a>例

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
