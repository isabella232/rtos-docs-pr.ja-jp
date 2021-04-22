---
title: 第 4 章 - USBX デバイス サービスの説明
description: USBX デバイス サービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812953"
---
# <a name="description-of-usbx-device-services"></a>USBX デバイス サービスの説明

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

インターフェイス値の現在の代替設定を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>説明

この関数は、特定のインターフェイス値の現在の代替設定を取得するために、USB ホストによって使用されます。 **GET_INTERFACE** 要求を受信すると、コントローラー ドライバーによって呼び出されます。

### <a name="input-parameter"></a>入力パラメーター

- **Interface_value**: 現在の代替設定に対してクエリを行う対象のインターフェイスの値

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_ERROR**: (0xFF) インターフェイス値が正しくありません。

### <a name="example"></a>例

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

インターフェイス値の現在の代替設定を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>説明

この関数は、特定のインターフェイス値の現在の代替設定を設定するために、USB ホストによって使用されます。 **SET_INTERFACE** 要求を受信すると、コントローラー ドライバーによって呼び出されます。 **SET_INTERFACE** が完了すると、代替設定の値がクラスに適用されます。

デバイス スタックは、このインターフェイスを所有するクラスに **UX_SLAVE_CLASS_COMMAND_CHANGE** を発行して、代替設定の変更を反映します。

### <a name="parameters"></a>パラメーター

- **Interface_value** 現在の代替設定を設定する対象のインターフェイスの値。
- **alternate_setting_value**: 新しい代替設定値。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) インターフェイスがアタッチされていません。
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) デバイスが構成されていません。
- **UX_ERROR**: (0xFF) インターフェイス値が正しくありません。

### <a name="example"></a>例

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

新しい USB デバイス クラスを登録します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>説明

この関数は、新しい USB デバイス クラスを登録するために、アプリケーションによって使用されます。 この登録によって、クラスのインスタンスではなく、クラス コンテナーが開始されます。 クラスはアクティブなスレッドを持ち、特定のインターフェイスにアタッチされている必要があります。

パラメーターまたはパラメーター リストを必要とするクラスもあります。 たとえば、デバイス ストレージ クラスは、エミュレートしようとしているストレージ デバイスのジオメトリを必要とします。 したがって、パラメーター フィールドはクラスの要件に依存しており、値になる場合も、またクラス値が設定された構造体へのポインターになる場合もあります。

> [!NOTE]
> class_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_MAX_CLASS_NAME_LENGTH** よりも大きくすることはできません。

### <a name="parameters"></a>パラメーター

- **class_name**: クラス名
- **class_entry_function**: クラスのエントリ関数。
- **configuration_number**: このクラスがアタッチされている構成番号。
- **interface_number**: このクラスがアタッチされているインターフェイス番号。
- **parameter**: クラス固有のパラメーター リストへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) クラスが登録されました
- **UX_MEMORY_INSUFFICIENT**: (0x12) クラス テーブルにエントリが残っていません。
- **UX_THREAD_ERROR**: (0x16) クラス スレッドを作成できません。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

USB デバイス クラスを登録解除します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>説明

この関数は、USB デバイス クラスを登録解除するために、アプリケーションによって使用されます。

> [!NOTE]
> class_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_MAX_CLASS_NAME_LENGTH** よりも大きくすることはできません。

### <a name="parameters"></a>パラメーター

- **class_name**: クラス名
- **class_entry_function**: クラスのエントリ関数。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) クラスが登録解除されました。
- **UX_NO_CLASS_MATCH**: (0x57) クラスが登録されていません。

### <a name="example"></a>例

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

現在の構成を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>説明

この関数は、デバイスで実行されている現在の構成を取得するために、ホストによって使用されます。

### <a name="input-parameter"></a>入力パラメーター

なし

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

現在の構成を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>説明

この関数は、デバイスで実行されている現在の構成を設定するために、ホストによって使用されます。 このコマンドを受信すると、USB デバイス スタックは、この構成に接続されている各インターフェイスの代替設定 0 をアクティブにします。

### <a name="input-parameter"></a>入力パラメーター

- **configuration_value**: ホストによって選択された構成値。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) 構成が正常に設定された。

### <a name="example"></a>例

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

記述子をホストに送信します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>説明

この関数は、ホストに記述子を返すためにデバイス側で使用されます。 この記述子は、デバイス記述子、構成記述子、文字列記述子のいずれでもかまいません。

### <a name="parameters"></a>パラメーター

- **descriptor_type**: 記述子のタイプ。 次のいずれかの値を指定する必要があります。
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index**: 記述子のインデックス。
- **host_length**: ホストが必要とする長さ。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) データ転送が完了しました。
- **UX_ERROR**: (0xFF) 転送が完了しませんでした。

### <a name="example"></a>例

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

デバイス スタックを切断します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>説明

VBUS マネージャーは、デバイスの切断時にこの関数を呼び出します。 デバイス スタックによって、このデバイスに登録されているすべてのクラスに通知され、その後すべてのデバイス リソースが解放されます。

### <a name="input-parameter"></a>入力パラメーター

なし

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) デバイスが切断されました。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

エンドポイント停止条件を要求します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>説明

この関数は、エンドポイントがホストに停止条件を返す必要がある場合に、USB デバイス クラスによって呼び出されます。

### <a name="input-parameter"></a>入力パラメーター

- **endpoint**: 停止条件が要求されるエンドポイント。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。
- **UX_ERROR**: (0xFF) デバイスが無効な状態です。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

ホストをウェイク アップします

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>説明

この関数は、デバイスがホストをウェイク アップするときに呼び出されます。 このコマンドは、デバイスが一時停止モードの場合にのみ有効です。 USB ホストをウェイク アップするタイミングの決定は、デバイス アプリケーション次第です。 たとえば、USB モデムは、電話回線で RING 信号を検出したときにホストをウェイク アップできます。

### <a name="input-parameter"></a>入力パラメーター

なし

### <a name="return-values"></a>戻り値

- **UX_SUCCESS** (0x00) 呼び出しに成功しました。
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) 呼び出しに失敗しました (デバイスが一時停止モードではなかった可能性があります)。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

USB デバイス スタックを初期化します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>説明

この関数は、USB デバイス スタックを初期化するために、アプリケーションによって呼び出されます。 クラスやコントローラーは初期化されません。 これは、個別の関数呼び出しを使用して行う必要があります。 この呼び出しでは主に、USB 関数のデバイス フレームワークがスタックに提供されます。 高速と全速の両方の速度がサポートされるので、速度ごとにデバイス フレームワークを完全に分けることができます。 文字列フレームワークと複数言語がサポートされています。

### <a name="parameters"></a>パラメーター

- **device_framework_high_speed**: 高速フレームワークへのポインター。
- **device_framework_length_high_speed**: 高速フレームワークの長さ。
- **device_framework_full_speed**: 全速フレームワークへのポインター。
- **device_framework_length_full_speed**: 全速フレームワークの長さ。
- **string_framework**: 文字列フレームワークへのポインター。
- **string_framework_length**: 文字列フレームワークの長さ。
- **language_id_framework**: 文字列言語フレームワークへのポインター。
- **language_id_framework_length**: 文字列言語フレームワークの長さ。
- **ux_system_slave_change_function**: デバイスの状態が変化するときに呼び出される関数。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) スタックを初期化できる十分なメモリがありません。
- **UX_DESCRIPTOR_CORRUPTED**: (0x42) 記述子が無効です。

### <a name="example"></a>例

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

アプリケーションは、コントローラーの状態が変化するときにコールバックを要求できます。 コントローラーの主な状態は次の 2 つです。

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

アプリケーションが一時停止/再開信号を必要としない場合は、UX_NULL 関数を送信します。

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

ネットワーク インターフェイスを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>説明

この関数は、インターフェイスの削除が必要なときに呼び出されます。 インターフェイスが削除されるのは、デバイスが抽出されるとき、バスがリセットされた後、または新しい代替設定があるときです。

### <a name="input-parameter"></a>入力パラメーター

- **interface**: 削除するインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

現在のインターフェイス値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>説明

この関数は、ホストが現在のインターフェイスに対してクエリを行うときに呼び出されます。 デバイスは現在のインターフェイス値を返します。

> [!NOTE]
> この関数の使用は非推奨とされます。 レガシ ソフトウェアには使用できますが、新しいソフトウェアでは、代わりに ***ux_device_stack_alternate_setting_get*** 関数を使用する必要があります。

### <a name="input-parameter"></a>入力パラメーター

- **interface_value**: 返されるインターフェイスの値。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。
- **UX_ERROR**: (0xFF) インターフェイスが存在しません。

### <a name="example"></a>例

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

インターフェイスの代替設定を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>説明

この関数は、ホストがインターフェイスの代替設定の変更を要求するときに呼び出されます。

### <a name="parameters"></a>パラメーター

- **device_framework**: このインターフェイスのデバイス フレームワークのアドレス。
- **device_framework_length**: デバイス フレームワークの長さ。
- **alternate_setting_value**: このインターフェイスによって使用される代替設定値。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。
- **UX_ERROR**: (0xFF) インターフェイスが存在しません。

### <a name="example"></a>例

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

インターフェイス インスタンスを所有するクラスの検索を開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>説明

この関数は、ホストによってインターフェイスが選択され、デバイス スタックがこのインターフェイス インスタンスを所有するデバイス クラスを検索する必要があるときに呼び出されます。

### <a name="input-parameter"></a>入力パラメーター

- **interface**: 作成されたインターフェイスへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。
- **UX_NO_CLASS_MATCH**: (0x57) このインターフェイスにはクラスが存在しません。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

ホストにデータ転送を要求します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>説明

この関数は、クラスまたはスタックがデータをホストに転送するときに呼び出されます。 ホストは常にデバイスをポーリングしますが、デバイスでは事前にデータを準備することができます。

### <a name="parameters"></a>パラメーター

- **transfer_request**: 転送要求へのポインター。
- **slave_length**: デバイスが返す必要がある長さ。
- **host_length**: ホストが要求した長さ。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。
- **UX_TRANSFER_NOT_READY**: (0x25) デバイスが無効な状態です (**ATTACHED**、**CONFIGURED**、**ADDRESSED** のいずれかである必要があります)。
- **UX_ERROR**: (0xFF) 転送エラー。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

譲渡要求のキャンセル

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>説明

この関数は、アプリケーションが転送要求をキャンセルする必要がある場合、またはスタックがエンドポイントに関連する転送要求を中止する必要がある場合に呼び出されます。

### <a name="parameters"></a>パラメーター

- **transfer_request**: 転送要求へのポインター。
- **completion_code**: この転送要求の完了を待機しているクラスに返されるエラー コード。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) この操作は成功しました。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

スタックを初期化解除します

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>説明

この関数は、アプリケーションが USBX デバイス スタックを初期化解除する必要がある場合に呼び出されます。すべてのデバイス スタック リソースが解放されます。 これは、ux_device_stack_class_unregister を使用してすべてのクラスを登録解除した後で呼び出す必要があります。

### <a name="parameters"></a>パラメーター

なし

### <a name="return-value"></a>戻り値

**UX_SUCCESS**: (0x00) この操作は成功しました。
