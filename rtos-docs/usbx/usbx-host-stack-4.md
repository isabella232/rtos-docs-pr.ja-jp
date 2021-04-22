---
title: 第 4 章 - USBX ホスト サービスの説明
description: USBX ホスト サービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813271"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>第 4 章 - USBX ホスト サービスの説明

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

ホスト操作のために USBX を初期化します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>説明

この関数は、USB ホスト スタックを初期化します。 USBX 内部で使用するために、指定されたメモリ領域が設定されます。 UX_SUCCESS が返された場合、USBX はホスト コントローラーとクラス登録ができるようになっています。

### <a name="input-parameter"></a>入力パラメーター

- **system_change_function**: デバイスの変更をアプリケーションに通知する省略可能なコールバック ルーチンへのポインター。

### <a name="return-value"></a>戻り値

- **NX_SUCCESS**: (0x00) 初期化に成功しました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) メモリの割り当てに失敗しました。

### <a name="example"></a>例

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

エンドポイントの転送要求にアタッチされているすべてのトランザクションを中止します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>説明

この関数は、エンドポイントにアタッチされている特定の転送要求の、アクティブまたは保留中のすべてのトランザクションをキャンセルします。 転送要求にコールバック関数がアタッチされている場合、コールバック関数は UX_TRANSACTION_ABORTED 状態で呼び出されます。

### <a name="input-parameter"></a>入力パラメーター

- **endpoint**: エンドポイントへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) エラーはありません。
- **UX_ENDPOINT_HANDLE_UNKNOWN**: (0x53) エンドポイント ハンドルが無効です。

### <a name="example"></a>例

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

クラス コンテナーへのポインターを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>説明

この関数は、クラス コンテナーへのポインターを返します。 クラスまたはアプリケーションがデバイスを開くとき、クラスはインスタンスを検索するために、そのコンテナーを USB スタックから取得する必要があります。

> [!NOTE]
> class_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は UX_MAX_CLASS_NAME_LENGTH よりも大きくすることはできません。

### <a name="parameters"></a>パラメーター

- **class_name**: クラス名へのポインター。
- **class**: クラスの名前のクラス コンテナーを含む関数呼び出しによって更新されるポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) エラーはありません。返されるとき、クラス フィールドにはクラス コンテナーへのポインターが登録されます。
- **UX_HOST_CLASS_UNKNOWN**: (0x59) クラスがスタックによって認識されていません。

### <a name="example"></a>例

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

USB クラスを USB スタックに登録します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>説明

この関数は、USB クラスを USB スタックに登録します。 クラスには、USB スタックが次のようなコマンドを送信するためのエントリ ポイントを指定する必要があります。

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> *class_name* という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_MAX_CLASS_NAME_LENGTH** よりも大きくすることはできません。

### <a name="parameters"></a>パラメーター

- **class_name**: クラスの名前へのポインター。有効なエントリは、USBX の USB クラスの下にあるファイル ux_system_initialize.c にあります。
- **class_entry_address**: クラスのエントリ関数のアドレス。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) クラスが正常にインストールされました。
- **UX_MEMORY_ARRAY_FULL**: (0x1a) このクラスを格納するためのメモリが不足しています。
- **UX_HOST_CLASS_ALREADY_INSTALLED**: (0x58) ホスト クラスは既にインストールされています。

### <a name="example"></a>例:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

クラス コンテナーの新しいクラス インスタンスを作成します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>説明

この関数は、クラス コンテナーの新しいクラス インスタンスを作成します。 クラスの複雑さを軽減するために、このクラス インスタンスは、クラス コードに含まれません。 代わりに、各クラス インスタンスは、メイン スタックに存在するクラス コンテナーにアタッチされます。

### <a name="parameters"></a>パラメーター

- **class**: クラス コンテナーへのポインター。
- **class_instance**: 作成されるクラス インスタンスへのポインター。

### <a name="return-value"></a>戻り値

- **UX_SUCCESS**: (0x00) クラス コンテナーにクラス インスタンスがアタッチされました。

### <a name="example"></a>例

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

クラス コンテナーのクラス インスタンスを破棄します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>説明

この関数は、クラス コンテナーのクラス インスタンスを破棄します。

### <a name="parameters"></a>パラメーター

- **class**: クラス コンテナーへのポインター。
- **class_instance**: 破棄するインスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) クラス インスタンスが破棄されました。
- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) クラス コンテナーにクラス インスタンスがアタッチされていません。

### <a name="example"></a>例

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

特定のクラスのクラス インスタンス ポインターを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>説明

この関数は、特定のクラスのクラス インスタンス ポインターを返します。 クラスの複雑さを軽減するために、このクラス インスタンスは、クラス コードに含まれません。 代わりに、各クラス インスタンスはクラス コンテナーにアタッチされます。 この関数は、クラス コンテナー内のクラス インスタンスを検索するために使用されます。

### <a name="parameters"></a>パラメーター

- **class**: クラス コンテナーへのポインター。
- **class_index**: コンテナーにアタッチされたクラスのリスト内で、関数呼び出しによって使用されるインデックス。
- **class_instance**: 関数呼び出しによって返されるインスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) クラス インスタンスが見つかりました。

- **UX_HOST_CLASS_INSTANCE_UNKNOWN**: (0x5b) クラス コンテナーにアタッチされているクラス インスタンスはありません。

### <a name="example"></a>例

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

構成コンテナーへのポインターを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>説明

この関数は、デバイス ハンドルと構成インデックスに基づいて構成コンテナーを返します。

### <a name="parameters"></a>パラメーター

- **device**: 要求された構成を所有しているデバイス コンテナーへのポインター。
- **configuration_index**: 検索される構成のインデックス。
- **configuration**: 返される構成コンテナーへのポインターのアドレス。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) 構成が見つかりました。
- **UX_DEVICE_HANDLE_UNKNOWN**: (0x50) デバイス コンテナーが存在しません。
- **UX_CONFIGURATION_HANDLE_UNKNOWN**: (0x51) インデックスの構成ハンドルが存在しません。

### <a name="example"></a>例

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

デバイスの特定の構成を選択します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>説明

この関数は、デバイスの特定の構成を選択します。 この構成がデバイスに設定されている場合、既定では、各デバイス インターフェイスとそれに関連付けられている代替設定 0 がデバイスでアクティブになります。 デバイス/インターフェイス クラスで特定のインターフェイスの設定を変更する場合は、**ux_host_stack_interface_setting_select** サービス呼び出しを発行する必要があります。

### <a name="parameters"></a>パラメーター

- **configuration**: このデバイスに対して有効にする構成コンテナーへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) 構成が正常に選択されました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN**: (0x51) 構成ハンドルが存在しません。
- **UX_OVER_CURRENT_CONDITION**: (0x43) この構成は、バスに過電流の状態が存在します。

### <a name="example"></a>例

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

デバイス コンテナーへのポインターを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>説明

この関数は、インデックスに基づいてデバイス コンテナーを返します。 デバイス インデックスは 0 から始まります。 コントローラーが複数あってバイト インデックスが十分でない可能性もあるため、インデックスは ULONG です。 デバイス インデックスを、バス固有のデバイス アドレスと混同しないようにしてください。

### <a name="parameters"></a>パラメーター

- **device_index**: デバイスのインデックス。
- **device**: 返されるデバイス コンテナーのポインターのアドレス。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) デバイス コンテナーが存在し、返されます
- **UX_DEVICE_HANDLE_UNKNOWN**: (0X50) デバイスが不明です

### <a name="example"></a>例

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

エンドポイント コンテナーを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>説明

この関数は、インターフェイス ハンドルとエンドポイント インデックスに基づいて、エンドポイント コンテナーを返します。 エンドポイントを検索する前に、インターフェイスの代替設定が選択されている、または既定の設定が使用されていることを前提にしています。

### <a name="parameters"></a>パラメーター

- **interface**: 要求されたエンドポイントを含むインターフェイス コンテナーへのポインター。
- **endpoint_index**: このインターフェイス内のエンドポイントのインデックス。
- **endpoint**: 返されるエンドポイント コンテナーのアドレス。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) エンドポイント コンテナーが存在し、返されます。
- **UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) 指定されたインターフェイスが存在しません。
- **UX_ENDPOINT_HANDLE_UNKNOWN**: (0x53) エンドポイント インデックスが存在しません。

### <a name="example"></a>例

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

USB コントローラーを USB スタックに登録します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>説明

この関数は、USB コントローラーを USB スタックに登録します。 主として、このコントローラーによって使用されるメモリを割り当て、コントローラーに初期化コマンドを渡します。

### <a name="parameters"></a>パラメーター

- **hcd_name**: ホスト コントローラーの名前
- **hcd_function**: ホスト コントローラー内で初期化を実行する関数。
- **hcd_param1**: hcd によって使用される IO またはメモリ リソース。
- **hcd_param2**: ホスト コントローラーによって使用される IRQ。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) コントローラーが適切に初期化されました。
- **UX_MEMORY_INSUFFICIENT**: (0x12) このコントローラーに十分なメモリがありません。
- **UX_PORT_RESET_FAILED**: (0x31) コントローラーのリセットに失敗しました。
- **UX_CONTROLLER_INIT_FAILED**: (0x32) コントローラーを適切に初期化できませんでした。

### <a name="example"></a>例

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

インターフェイス コンテナーのポインターを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>説明

この関数は、構成ハンドル、インターフェイス インデックス、代替設定インデックスに基づいて、インターフェイス コンテナーを返します。

### <a name="parameters"></a>パラメーター

- **configuration**: インターフェイスを所有する構成コンテナーへのポインター。
- **interface_index**: 検索するインターフェイス インデックス。
- **alternate_setting_index**: 検索するインターフェイス内の代替設定。
- **interface**: 返されるインターフェイス コンテナー ポインターのアドレス。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00)、インターフェイス インデックスと代替設定のインターフェイス コンテナーが検出され、返されました。
- **UX_CONFIGURATION_HANDLE_UNKNOWN** : (0x51) 構成が存在しません。
- **UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) インターフェイスが存在しません。

### <a name="example"></a>例

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

インターフェイスの代替設定を選択します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>説明

この関数は、選択した構成に属する特定のインターフェイスの特定の代替設定を選択します。 この関数を使用すると、既定の代替設定から新しい設定に変更したり、既定の代替設定に戻したりすることができます。 新しい代替設定を選択すると、以前のエンドポイントの特性は無効になり、再度読み込む必要があります。

### <a name="input-parameter"></a>入力パラメーター

- **interface**: 代替設定を選択するインターフェイス コンテナーへのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) このインターフェイスの代替設定が正常に選択されました。
- **UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) インターフェイスが存在しません。

### <a name="example"></a>例

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

保留中の転送要求を中止します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>説明

この関数は、以前に送信されて保留中になっている転送要求を中止します。 この関数で取り消されるのは、特定の転送要求のみです。 この関数へのコールバックは、UX_TRANSFER REQUEST_STATUS_ABORT の状態になります。

### <a name="parameters"></a>パラメーター

- **transfer_request**: 中止する転送要求へのポインター。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この転送要求の USB 転送が取り消されました。

### <a name="example"></a>例

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

USB 転送を要求します。

### <a name="prototype"></a>プロトタイプ

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>説明

この関数は、USB トランザクションを実行します。 実行されると、この転送要求によって、このトランザクションに対してエンドポイント パイプが選択され、パラメーター (データ ペイロード、トランザクションの長さ) が転送に関連付けられます。 制御パイプの場合、トランザクションはブロック状態になり、制御転送の 3 つのフェーズが完了したとき、または前のエラーがある場合にのみ復帰します。 他のパイプの場合、USB スタックは USB 上のトランザクションをスケジュールしますが、完了するまで待機はしません。 ブロックしないパイプに対する各転送要求には、完了ルーチン ハンドラーを指定する必要があります。

関数呼び出しから制御が戻ったら、トランザクションの結果が含まれているかどうか、転送要求の状態を確認する必要があります。

### <a name="input-parameter"></a>入力パラメーター

- **transfer_request**: 転送要求へのポインター。 転送要求には、転送に必要なすべての情報が含まれています。

### <a name="return-values"></a>戻り値

- **UX_SUCCESS**: (0x00) この転送要求の USB 転送が適切にスケジュールされました。 転送要求の完了時には、転送要求の状態コードを確認する必要があります。
- **UX_MEMORY_INSUFFICIENT**: (0x12) 必要なコントローラー リソースを割り当てるのに十分なメモリがありません。
- **UX_TRANSFER_NOT_READY**: (0x25) デバイスが無効な状態でした。ATTACHED、ADDRESSED、または CONFIGURED である必要があります。

### <a name="example"></a>例:

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
