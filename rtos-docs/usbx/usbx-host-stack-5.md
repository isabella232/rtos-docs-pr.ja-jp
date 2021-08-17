---
title: '第 5 章: USBX ホスト クラス API'
description: USBX ホスト クラス API について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 62750ab4a5540b243665a7a7d9000a0d60c4435313b6de2e1579ae7f1c20fe55
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790668"
---
# <a name="chapter-5---usbx-host-classes-api"></a>第 5 章: USBX ホスト クラス API

この章では、USBX ホスト クラスの公開されているすべての API について説明します。 クラスごとに次の API について詳しく説明します。

- HID クラス
- CDC-ACM クラス
- CDC-ECM クラス
- ストレージ クラス

## <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

HID クラスに HID クライアントを登録します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a>説明

この関数は、HID クラスに HID クライアントを登録するために使用されます。 HID クラスは、このデバイスからデータを要求する前に、HID デバイスと HID クライアントの一致を検出する必要があります。

> [!NOTE]
> hid_client_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH** よりも大きくすることはできません。

### <a name="parameters"></a>パラメーター

- **hid_client_name**: HID クライアント名へのポインター。
- **hid_client_handler** HID クライアント ハンドラーへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_MEMORY_INSUFFICIENT**: (0x12) クライアントへのメモリ割り当てに失敗しました。
- **UX_MEMORY_ARRAY_FULL**: (0x1a) の最大数のクライアントが既に登録されています。
- **UX_HOST_CLASS_ALREADY_INSTALLED**: (0x58) このクラスは既に存在します

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a>ux_host_class_hid_report_callback_register

HID クラスからのコールバックを登録します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a>説明

この関数は、レポートの受信時に HID クラスから HID クライアントにコールバックを登録するために使用されます。

### <a name="parameters"></a>パラメーター

- **hid**: HID クラス インスタンスへのポインター
- **call_back**: call_back 構造体へのポインター

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID インスタンスが無効です。
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) レポート コールバックの登録でエラーが発生しました。

### <a name="example"></a>例

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

## <a name="ux_host_class_hid_periodic_report_start"></a>ux_host_class_hid_periodic_report_start

HID クラス インスタンスの定期的なエンドポイントを開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>説明

この関数は、この HID クライアントにバインドされている HID クラスのインスタンスに対して定期的な (割り込み) エンドポイントを開始するために使用されます。 HID クラスは、HID クライアントがアクティブになるまで定期的なエンドポイントを開始できないため、このエンドポイントの起動とレポートの受信は、HID クライアントに委ねられます。

### <a name="input-parameter"></a>入力パラメーター

- **hid**: HID クラス インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) 定期レポートが正常に開始されました。
- **ux_host_class_hid_PERIODIC_REPORT_ERROR**: (0x7a) 定期レポートでエラーが発生しました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a>ux_host_class_hid_periodic_report_stop

HID クラス インスタンスの定期的なエンドポイントを停止します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>説明

この関数は、この HID クライアントにバインドされている HID クラスのインスタンスに対して定期的な (割り込み) エンドポイントを停止するために使用されます。 HID クラスは、HID クライアントが非アクティブ化され、そのすべてのリソースが解放されるまで、定期的なエンドポイントを停止できません。そのため、このエンドポイントの停止は HID クライアントに委ねられます。

### <a name="input-parameter"></a>入力パラメーター

- **hid**: HID クラス インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) 定期レポートが正常に停止されました。
- **ux_host_class_hid_PERIODIC_REPORT_ERROR**: (0x7a) 定期レポートでエラーが発生しました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

HID クラス インスタンスからレポートを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>説明

この関数は、定期的なエンドポイントに依存せずに、デバイスから直接レポートを受信するために使用されます。 このレポートはコントロール エンドポイントから生成されますが、その処理は、定期的なエンドポイントで生成される場合と同じです。

### <a name="parameters"></a>パラメーター

- **hid**: HID クラス インスタンスへのポインター。
- **client_report**: HID クライアント レポートへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) レポートが正常に受信されました。
- **UX_HOST_CLASS_HID_REPORT_ERROR**: (0x70) クライアント レポートが無効か、転送中にエラーが発生しました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。
- **UX_BUFFER_OVERFLOW**: (0x5d) 指定されたバッファーは、圧縮されていないレポートを格納するのに十分な大きさではありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

要求を送信します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>説明

この関数は、デバイスに直接レポートを送信するために使用されます。

### <a name="parameters"></a>パラメーター

- **hid**: HID クラス インスタンスへのポインター。
- **client_report**: HID クライアント レポートへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) レポートが正常に送信されました。
- **UX_HOST_CLASS_HID_REPORT_ERROR**: (0x70) クライアント レポートが無効か、転送中にエラーが発生しました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。
- **UX_HOST_CLASS_HID_REPORT_OVERFLOW**: (0x5d) 指定されたバッファーは、圧縮されていないレポートを格納するのに十分な大きさではありません。

### <a name="example"></a>例

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

## <a name="ux_host_class_hid_mouse_buttons_get"></a>ux_host_class_hid_mouse_buttons_get

マウス ボタンを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a>説明

この関数は、マウス ボタンを取得するために使用されます

### <a name="parameters"></a>パラメーター

- **mouse_instance**: HID マウス インスタンスへのポインター。
- **mouse_buttons**: 戻りボタンへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) マウス ボタンが正常に取得されました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。

### <a name="example"></a>例

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a>ux_host_class_hid_mouse_position_get

マウスの位置を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a>説明

この関数は、X & Y 座標でマウス位置を取得するために使用されます。

### <a name="parameters"></a>パラメーター

- **mouse_instance**: HID マウス インスタンスへのポインター。
- **mouse_x_position**: X 座標へのポインター。
- **mouse_y_position**: Y 座標へのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) X &amp; Y 座標が正常に取得されました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。

### <a name="example"></a>例

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a>ux_host_class_hid_keyboard_key_get

キーボードのキーと状態を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a>説明

この関数は、キーボードのキーと状態を取得するために使用されます。

### <a name="parameters"></a>パラメーター

- **keyboard_instance**: HID キーボード インスタンスへのポインター。
- **keyboard_key**: キーボードのキー コンテナーへのポインター。
- **keyboard_state**: キーボード状態コンテナーへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) キーと状態が正常に取得されました。
- **UX_ERROR**: (0xff) レポートする内容はありません。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。

キーボードの状態は、次の値のいずれかを取ります。

- **UX_HID_KEYBOARD_STATE_KEY_UP**: 0x10000
- **UX_HID_KEYBOARD_STATE_NUM_LOCK**: 0x0001
- **UX_HID_KEYBOARD_STATE_CAPS_LOCK**: 0x0002
- **UX_HID_KEYBOARD_STATE_SCROLL_LOCK**: 0x0004
- **UX_HID_KEYBOARD_STATE_MASK_LOCK**: 0x0007
- **UX_HID_KEYBOARD_STATE_LEFT_SHIFT**: 0x0100
- **UX_HID_KEYBOARD_STATE_RIGHT_SHIFT**: 0x0200
- **UX_HID_KEYBOARD_STATE_SHIFT**: 0x0300
- **UX_HID_KEYBOARD_STATE_LEFT_ALT**: 0x0400
- **UX_HID_KEYBOARD_STATE_RIGHT_ALT**: 0x0800
- **UX_HID_KEYBOARD_STATE_ALT**: 0x0a00
- **UX_HID_KEYBOARD_STATE_LEFT_CTRL**: 0x1000
- **UX_HID_KEYBOARD_STATE_RIGHT_CTRL**: 0x2000
- **UX_HID_KEYBOARD_STATE_CTRL**: 0x3000
- **UX_HID_KEYBOARD_STATE_LEFT_GUI**: 0x4000
- **UX_HID_KEYBOARD_STATE_RIGHT_GUI**: 0x8000
- **UX_HID_KEYBOARD_STATE_GUI**: 0xa000

### <a name="example"></a>例

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

## <a name="ux_host_class_hid_keyboard_ioctl"></a>ux_host_class_hid_keyboard_ioctl

HID キーボードに対して IOCTL 関数を実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a>説明

この関数は、HID キーボードに対する特定の ioctl 関数を実行します。 呼び出しはブロック状態であり、エラーが発生した場合またはコマンドが完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **keyboard_instance**: HID キーボード インスタンスへのポインター。
- **ioctl_function**: 実行される ioctl 関数。 許可されている ioctl 関数については、次の表を参照してください。
- **parameter**: ioctl に固有のパラメーターへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) Ioctl 関数が正常に完了しました。
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 不明な IOCTL 関数です

### <a name="ioctl-functions"></a>IOCTL 関数

- UX_HID_KEYBOARD_IOCTL_SET_LAYOUT
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE

### <a name="example--change-keyboard-layout"></a>例 – キーボード レイアウトを変更する

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

### <a name="example--disable-keyboard-key-decode"></a>例 – キーボードのキー デコードを無効にする

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a>ux_host_class_hid_remote_control_usage_get

リモート コントロールの使用状況を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a>説明

この関数は、リモート コントロールの使用状況を取得するために使用されます。

### <a name="parameters"></a>パラメーター

- **remote_control_instance**: HID リモート コントロール インスタンスへのポインター。
- **usage**: 使用状況へのポインター。
- **value**: 使用状況の値へのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_ERROR**: (0xff) レポートする内容はありません。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) HID クラス インスタンスが存在しません。

想定されるすべての使用状況のリストは、長すぎるためこのユーザー ガイドには掲載できません。 詳細な説明については、想定される値の完全な一覧が ux_host_class_hid.h にあります。

### <a name="example"></a>例

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

### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

cdc_acm インターフェイスからの読み取りを実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a>説明

この関数は、cdc_acm インターフェイスからの読み取りを実行します。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。

> [!Note]
> この関数により、デバイスから生の一括データが読み取られます。したがって、バッファーがいっぱいになるか、デバイスで短いパケット (長さ 0 のパケットを含む) による転送が終了するまで、保留状態が維持されます。 詳細については、「[**一括転送に関する一般的な考慮事項**](usbx-device-stack-5.md#general-considerations-for-bulk-transfer)」を参照してください。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc_acm クラス インスタンスへのポインター。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 受信される長さ。
- **actual_length**: 実際に受信された長さ。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) cdc_acm インスタンスが無効です。
- **UX_TRANSFER_TIMEOUT**: (0x5c) 転送がタイムアウトし、読み取りは完了していません。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a>ux_host_class_cdc_acm_write

cdc_acm インターフェイスへの書き込みを実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a>説明

この関数は、cdc_acm インターフェイスへの書き込みを実行します。 呼び出しはブロック状態であり、エラーが発生した場合または転送が完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc_acm クラス インスタンスへのポインター。
- **data_pointer**: データ ペイロードのバッファー アドレスへのポインター。
- **requested_length**: 送信される長さ。
- **actual_length**: 実際に送信された長さ。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) cdc_acm インスタンスが無効です。
- **UX_TRANSFER_TIMEOUT**: (0x5c) 転送がタイムアウトし、書き込みは完了していません。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a>ux_host_class_cdc_acm_ioctl

cdc_acm インターフェイスに対して IOCTL 関数を実行します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、cdc_acm インターフェイスに対して特定の ioctl 関数を実行します。 呼び出しはブロック状態であり、エラーが発生した場合またはコマンドが完了した場合にのみ復帰します。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc_acm クラス インスタンスへのポインター。
- **ioctl_function**: 実行される ioctl 関数。 許可されている ioctl 関数については、次の表を参照してください。
- **parameter**: ioctl に固有のパラメーターへのポインター

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) 十分なメモリがありません。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) CDC-ACM インスタンスが無効な状態です。
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 不明な IOCTL 関数です。

### <a name="ioctl-functions"></a>IOCTL 関数:

- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

デバイスからのデータのバックグラウンド受信を開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>説明

この関数によって USBX が、バックグラウンドでデバイスから継続的にデータを読み取ります。 各トランザクションが完了すると、 **cdc_acm_reception** で指定されたコールバックが呼び出され、アプリケーションがトランザクションのデータの後続処理を実行できるようになります。

> [!NOTE]
> バックグラウンド受信が使用されている間は、**ux_host_class_cdc_acm_read** を使用しないでください。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc_acm クラス インスタンスへのポインター。
- **cdc_acm_reception**: バックグラウンド受信の動作を定義する値を格納するパラメーターへのポインター。 このパラメーターのレイアウトは次のとおりです。

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

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) バックグラウンド受信が正常に開始されました。
- **UX_HOST_CLASS_INSTANCE _UNKNOWN**: (0x5b) クラス インスタンスが正しくありません。

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

## <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

バックグラウンドでのパケット受信を停止します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>説明

この関数によって USBX は、**ux_host_class_cdc_acm_reception_start** によって以前に開始されたバックグラウンド受信を停止します。

### <a name="parameters"></a>パラメーター

- **cdc_acm**: cdc_acm クラス インスタンスへのポインター。
- **cdc_acm_reception**: バックグラウンド受信を開始するために使用されたのと同じパラメーターへのポインター。 このパラメーターのレイアウトは次のとおりです。

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

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) バックグラウンド受信が正常に停止しました。
- **UX_HOST_CLASS_INSTANCE _UNKNOWN**: (0x5b) クラス インスタンスが正しくありません。

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
