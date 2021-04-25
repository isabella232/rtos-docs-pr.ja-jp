---
title: 第 4 章 - LWM2M クライアント サービスの説明
description: この章では、すべての LWM2M クライアント サービスをアルファベット順に説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810745"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>第 4 章 LWM2M クライアント サービスの説明

この章では、以下に記載したすべての LWM2M クライアント サービスをアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

**LWM2M クライアント管理:**

- nx_lwm2m_client_create: *LWM2M クライアントを作成します*

- nx_lwm2m_client_delete: *LWM2M クライアントを削除します*

- nx_lwm2m_client_lock: *LWM2M クライアントをロックします*

- nx_lwm2m_client_unlock: *LWM2M クライアントをロック解除します*

**LWM2M クライアント セッション管理:**

- nx_lwm2m_client_session_create: *LWM2M クライアント セッションを作成します*

- nx_lwm2m_client_session_delete: *LWM2M クライアント セッションを削除します*

- nx_lwm2m_client_session_bootstrap: *ブートストラップ サーバーとのセッションを開始します*

- nx_lwm2m_client_session_bootstrap_dtls: *ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します*

- nx_lwm2m_client_session_register_info_get: *LWM2M サーバーの登録情報を取得します*

- nx_lwm2m_client_session_register: *LWM2M Server とのセッションを開始します*

- nx_lwm2m_client_session_register_dtls: *LWM2M サーバーとのセキュアなセッションを開始します*

- nx_lwm2m_client_session_update: *LWM2M サーバーとのセッションを更新します*

- nx_lwm2m_client_session_deregister: *LWM2M サーバーとのセッションを終了します*

- nx_lwm2m_client_session_error_get: *セッションの最後のエラーを取得します*

**デバイス オブジェクトの実装:**

- nx_lwm2m_client_device_callbacks_set: *デバイス オブジェクトのアプリケーションのコールバックを設定します*

- nx_lwm2m_client_device_error_push:*デバイス オブジェクトにエラー コードを追加します*

- nx_lwm2m_client_device_error_reset: *デバイス オブジェクトのエラー コードをリセットします*

- nx_lwm2m_client_device_resource_changed: *デバイス オブジェクト リソースのシグナルを変更します*

**ファームウェア更新オブジェクトの実装:**

- nx_lwm2m_firmware_create: *ファームウェア更新オブジェクトを作成します*

- nx_lwm2m_firmware_package_info_set: *ファームウェア更新パッケージの情報を設定します*

- nx_lwm2m_firmware_result_set: *ファームウェア更新の結果を設定します*

- nx_lwm2m_firmware_state_set: *ファームウェアの更新状態を設定します*

**カスタム オブジェクトの実装:**

- nx_lwm2m_client_object_add: *LWM2M クライアントにオブジェクトの実装を追加します*

- nx_lwm2m_client_object_remove: *LWM2M クライアントからオブジェクトの実装を削除します*

- nx_lwm2m_client_object_instance_add: *LWM2M クライアントにオブジェクト インスタンスを追加します*

- nx_lwm2m_client_object_instance_remove: *LWM2M クライアントからオブジェクト インスタンスを削除します*

- nx_lwm2m_object_resource_changed: *オブジェクト インスタンスのリソース値のシグナルを変更します*

**ローカル デバイス管理**

- nx_lwm2m_client_object_create: *新しいオブジェクト インスタンスを作成します*

- nx_lwm2m_client_object_delete: *オブジェクト インスタンスを削除します*

- nx_lwm2m_client_object_discover: *オブジェクト インスタンスのリソースを検出します*

- nx_lwm2m_client_object_execute: *オブジェクト インスタンスのリソースを実行します*

- nx_lwm2m_client_object_next_get: *LWM2M クライアントによって実装されているオブジェクトのリストを取得します*

- nx_lwm2m_client_object_instance_next_get: *オブジェクトのインスタンスのリストを取得します*

- nx_lwm2m_client_object_read: *オブジェクト インスタンスのリソース値を読み取ります*

- nx_lwm2m_client_object_write: *オブジェクト インスタンスのリソース値を変更します*

**リソースの情報と値の設定:**

- nx_lwm2m_client_resource_info_set: *リソース情報を設定します*

- nx_lwm2m_client_resource_info_set: *リソース値を文字列として設定します*

- nx_lwm2m_client_resource_integer32_set: *リソース値を 32 ビット整数として設定します*

- nx_lwm2m_client_resource_integer64_set: *リソース値を 64 ビット整数として設定します*

- nx_lwm2m_client_resource_float32_set: *リソース値を 32 ビット浮動小数点数として設定します*

- nx_lwm2m_client_resource_float64_set: *リソース値を 64 ビット浮動小数点数として設定します*

- nx_lwm2m_client_resource_boolean_set: *リソース値をブール値として設定します*

- nx_lwm2m_client_resource_objlnk_set: *リソース値をオブジェクト リンクとして設定します*

- nx_lwm2m_client_resource_opaque_set: *リソース値を不透明な値として設定します*

- nx_lwm2m_client_resource_instance_set: *リソース値を複数のリソースのインスタンスとして設定します*
-
- nx_lwm2m_client_resource_dim_set: *複数のリソースのリソース ディメンションを設定します。*

**リソースの情報と値の取得:**

- nx_lwm2m_client_resource_info_get: *リソース情報を取得します*

- nx_lwm2m_client_resource_string_get: *文字列リソースの値を取得します*

- nx_lwm2m_client_resource_integer32_get: *32 ビット整数リソースの値を取得します*

- nx_lwm2m_client_resource_integer64_get: *64 ビット整数リソースの値を取得します*

- nx_lwm2m_client_resource_float32_get: *32 ビット浮動小数点リソースの値を取得します*

- nx_lwm2m_client_resource_float64_get: *64 ビット浮動小数点リソースの値を取得します*

- nx_lwm2m_client_resource_boolean_get: *ブール値リソースの値を取得します*

- nx_lwm2m_client_resource_objlnk_get: *オブジェクト リンク リソースの値を取得します*

- nx_lwm2m_client_resource_opaque_get: *不透明なリソースの値を取得します*

- nx_lwm2m_client_resource_instance_get: *複数のリソースのリソース インスタンスを取得します*

- nx_lwm2m_client_resource_dim_get: *複数のリソースのリソース ディメンションを取得します。*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

LWM2M クライアントを作成します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>説明

このサービスを使用すると、専用の ThreadX スレッドのコンテキスト内で実行される LWM2M クライアント インスタンスが作成されます。

LWM2M クライアントは、次の OMA LWM2M オブジェクトを実装します: セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)。 その他のオブジェクトの実装は、アプリケーションによって追加される必要があります。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **packet_pool_ptr** この LWM2M クライアントの既定のパケット プールへのポインター。
- **name_ptr** LWM2M クライアント エンドポイント名へのポインター。
- **name_length** LWM2M クライアント エンドポイント名の長さ。
- **msisdn_ptr** SMS バインディングで使用するために LWM2M クライアントに到達できる MSISDN へのポインター。SMS バインディングがサポートされていない場合は、NULL にすることができます。
- **msisdn_length** MSISDN 番号の長さ。
- **binding_modes** LWM2M クライアントでサポートされているバインディングとモードは、NX_LWM2M_BINDING_U、NX_LWM2M_BINDING_UQ、NX_LWM2M_BINDING_S、および NX_LWM2M_BINDING_SQ フラグの組み合わせになっている必要があります。
- **stack_ptr** LWM2M クライアント スレッド スタック領域へのポインター。
- **stack_size** LWM2M クライアント スレッド スタック サイズへのポインター。
- **priority** LWM2M クライアントの優先順位。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** LWM2M クライアントの作成に成功しました。
- **NX_LWM2M_CLIENT_ERROR** LWM2M クライアントの作成エラー。
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。
- **NX_PTR_ERROR** ポインターが無効です。
- **NX_SIZE_ERROR** スタック サイズが無効です。
- **NX_OPTION_ERROR** 優先順位が無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

LWM2M クライアントを削除します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、以前に作成された LWM2M クライアント インスタンスが削除されます。

現在クライアントにアタッチされているすべてのセッションも、この呼び出しによって削除されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** LWM2M クライアントの削除に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

デバイス オブジェクトのアプリケーション コールバックを設定します。

### <a name="prototype"></a>プロトタイプ

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントによって処理されない LWM2M デバイス オブジェクト リソースの操作を実装するためのアプリケーション コールバックがインストールされます。

LWM2M クライアントは、次のリソースを実装します: エラー コード (11)、リセット エラー コード (12)、サポートされているバインドとモード (16)。他のリソースに対する操作は、アプリケーションにリダイレクトされます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **operation_callback** "読み取り"、"検出"、"書き込み"、および "実行" の操作コールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作コールバックの設定に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
デバイス オブジェクトにエラー コードを追加します。

### <a name="prototype"></a>プロトタイプ

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>説明

このサービスを使用すると、オブジェクト デバイスのエラー コード (11) リソースに新しいインスタンスが追加されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **code** 新しいエラー コード。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

格納されているエラー コードの最大数に

達しました。

NX_PTR_ERROR ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

デバイス オブジェクトのエラー コードをリセットします。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、すべてのエラー コード リソース インスタンスがデバイス オブジェクトから削除されます。 これは、リソース リセット エラー コード (12) を実行することと同じです。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

デバイス オブジェクト リソースの変更を通知します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>説明

このサービスは、アプリケーションによって、オブジェクト デバイスのリソースが変更されたことを LWM2M クライアントに通知するために使用されます。 LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **resource** 変更されたリソースを記述する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

LWM2M クライアント ファームウェア オブジェクトを作成します。 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによってファームウェア オブジェクトを作成するために使用されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。
- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **protocols** サポートされているプロトコル。
- **package_callback** パッケージのコールバック。
- **package_uri_callback** パッケージ URI のコールバック。
- **update_callback** 更新コールバック。

### <a name="return-values"></a>戻り値

**NX_SUCCESS** 操作に成功しました。
**NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

LWM2M クライアント ファームウェア パッケージ情報を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって、ファームウェア更新オブジェクトのパッケージ情報リソースを設定するために使用されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。
- **name** ファームウェア パッケージの名前。
- **name_length** 名前の長さ。
- **version** ファームウェア パッケージのバージョン。
- **version_length** バージョンの長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

ファームウェア更新オブジェクトの更新結果のリソースを設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって、ファームウェア更新オブジェクトの更新結果リソースを設定するために使用されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。
- **result** 更新結果。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

ファームウェア更新オブジェクトの更新結果のリソースを設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって、ファームウェア更新オブジェクトの状態を設定するために使用されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。
- **state** ファームウェア オブジェクトの状態。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

LWM2M クライアントをロックします。

### <a name="prototype"></a>プロトタイプ

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、サーバーまたは別のアプリケーション スレッドからの LWM2M オブジェクトへの同時アクセスを防ぐために、LWM2M クライアントがロックされます。

LWM2M クライアントが現在別のスレッドによってロックされている場合、この関数は LWM2M クライアントがロック解除されるまでブロックします。

***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** ペアへの呼び出しは入れ子にすることができます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

オブジェクトの実装を LWM2M クライアントに追加します。

### <a name="prototype"></a>プロトタイプ

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>説明

このサービスを使用すると、新しいオブジェクトの実装が LWM2M クライアントに追加されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_ptr** オブジェクトの実装を定義する構造体へのポインター。
- **object_id** オブジェクト ID。
- **object_operation** オブジェクト操作のコールバック関数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

新しいオブジェクト インスタンスを作成します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクトに対して "作成" 操作を実行して、新しいオブジェクト インスタンスが作成されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id_ptr** 新しいインスタンスの ID へのポインター。LWM2M クライアントによってインスタンス ID を割り当てる必要がある場合は、**NULL** にすることができます。 ID が予約値 65535 の場合、LWM2M クライアントによってインスタンス ID が割り当てられます。 NULL 以外の場合は、割り当てられた ID が呼び出しの後に返されます。
- **num_values** 設定する値の数。
- **values_ptr** 新しいオブジェクト インスタンスを初期化するためのリソース値の配列へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト インスタンス ID は既に存在しています。
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** オブジェクトはインスタンスの作成をサポートしていません。
- **NX_LWM2M_CLIENT_NO_MEMORY** 新しいインスタンスを格納するためのメモリを割り当てることができません。
- **NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID が存在していません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

オブジェクト インスタンスを削除します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "削除" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id** オブジェクト インスタンス ID。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** オブジェクトはインスタンスの削除をサポートしていません。
- **NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID またはオブジェクト インスタンス ID が存在していません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

オブジェクト インスタンスのリソースを検出します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "検出" 操作が実行されます。これにより、オブジェクトによって実装されたリソースのリストが返されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id** オブジェクト インスタンス ID。
- **num_resources_ptr**: 入力時は宛先バッファーのサイズ、出力時はバッファーに書き込まれた要素の数。
- **resources_ptr**: 宛先バッファーへのポインター。

### <a name="return-values"></a>戻り値

- *NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** リソース バッファーが小さすぎて、リソースのリストを格納できません。
- **NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID またはオブジェクト インスタンス ID が存在していません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

オブジェクト インスタンスのリソースに対して "実行" 操作を実行します。

### <a name="prototype"></a>プロトタイプ

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンス リソースの "実行" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id** オブジェクト インスタンス ID。
- **resource_id**: リソース ID。
- **arguments_ptr**: 実行操作の引数へのポインター。 arguments_length が 0 の場合は、NULL を指定できます。
- **arguments_length**: 引数の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** リソース バッファーが小さすぎて、リソースのリストを格納できません。
- **NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID またはオブジェクト インスタンス ID が存在していません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

オブジェクト インスタンスの実装をオブジェクトに追加します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、新しいオブジェクト インスタンスの実装が LWM2M クライアントに追加されます。 instance_id_ptr の値が **NX_LWM2M_CLIENT_RESERVED_ID** である場合は、LWM2M クライアントによって未使用のインスタンス ID が自動的に割り当てられ、それ以外の場合、LWM2M クライアントではアプリケーションで設定された値が使用されます。 新しいインスタンスが正常に追加されると、instance_id が instance_id_ptr に入力され、アプリケーションに戻されます。

### <a name="parameters"></a>パラメーター

- **object_ptr** オブジェクトの実装を定義する構造体へのポインター。
- **instance_ptr** オブジェクト インスタンスの実装を定義する構造体へのポインター。
- **instance_id_ptr** オブジェクト インスタンス ID へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

オブジェクトの次のインスタンスを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたオブジェクトの次のオブジェクト インスタンスの ID が返されます。 現在のインスタンス ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合は、最初のインスタンスの ID が返されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id_ptr** 現在のオブジェクト インスタンス ID へのポインター。 戻り値には、オブジェクトの次のインスタンス ID が含まれます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_CLIENT_LWM2M_NOT_FOUND** 指定されたインスタンス ID がオブジェクトの最後か、オブジェクト ID が実装されていません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

オブジェクトからオブジェクト インスタンスの実装を削除します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、オブジェクトからオブジェクト インスタンスが削除されます。

### <a name="parameters"></a>パラメーター

- ***object_ptr*** オブジェクトの実装を定義する構造体へのポインター。
- **instance_ptr** オブジェクト インスタンスの実装を定義する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

LWM2M クライアントの次のオブジェクトを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントによって実装される次のオブジェクトの ID が返されます。 現在のオブジェクト ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合、最初のオブジェクト ID が返されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id_ptr** 現在のオブジェクト ID へのポインター。 戻り値には、LWM2M クライアントによって実装される次のオブジェクト ID が含まれます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_NOT_FOUND** 指定されたオブジェクト ID は、データベースの最後です。
**NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

オブジェクト インスタンスのリソースの値を読み取ります。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "読み取り" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id** オブジェクト インスタンス ID。
- **num_values** 読み取るリソースの数。
- **values_ptr** 読み取るリソースの ID を格納する NX_LWM2M_RESOURCE の配列へのポインター。 返されると、配列に対応する型と値が格納されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** リソースで読み取り操作がサポートされていません。
- **NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

オブジェクトからオブジェクト インスタンスの実装を削除します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントからオブジェクトが削除されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_ptr** オブジェクトの実装を定義する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。
- **NX_PTR_ERROR** ポインターが無効です。
- **NX_LWM2M_CLIENT_FORBIDDEN** 内部オブジェクトの削除は禁止されています。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

オブジェクト リソースの変更を通知します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって、オブジェクトのリソースが変更されたことを LWM2M クライアントに通知するために使用されます。 LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。

### <a name="parameters"></a>パラメーター

- **object_ptr** オブジェクトの実装を定義する構造体へのポインター。
- ***instance_ptr*** オブジェクト インスタンスの実装を定義する構造体へのポインター。
- **resource** 変更されたリソースを記述する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

オブジェクト インスタンスのリソースの値を変更します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "書き込み" 操作が実行されます。

*write_op* パラメーターには、次の書き込み操作を指定できます。

| 値 | 書き込み&nbsp;操作 | 説明 |
| --- | ---| --- |
| 0 | 部分更新 | 新しい値で提供されるリソースを追加または更新し、他の既存のリソースを変更せずにそのままにします。 |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | インスタンスの置換 | オブジェクト インスタンスを、提供された新しいリソース値に置き換えます。 |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | リソースの置換 | リソースを、提供された新しいリソース値に置き換えます (複数のリソースを置き換えるために使用されます)。 |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | ブートストラップ書き込み | ブートストラップ シーケンスからの呼び出しを示します。 |

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。
- **object_id** オブジェクト ID。
- **instance_id** オブジェクト インスタンス ID。
- **num_values**: 書き込むリソースの数。
- **values_ptr** リソースの ID、および書き込む型と値を格納する NX_LWM2M_RESOURCE の配列へのポインター。
- **write_op**: 書き込み操作の種類。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソースの型が無効です。
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 値の長さが大きすぎてインスタンスに格納できません。
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** リソースが読み書き込み操作をサポートしていません。
- **NX_LWM2M_CLIENT_NO_MEMORY** リソース値を格納するためのメモリを割り当てることができません。
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** リソースの値が無効です。
- **NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。
- **NX_OPTION_ERROR** 書き込み操作の種類が無効です。 
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

ブール値リソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>説明

このサービスを使用するとブール値リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **リソース** リソース値の説明へのポインター。
- **bool_ptr** 宛先のブール値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

ブール値リソースの値を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>説明

このサービスを使用するとブール値リソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **bool_data** ブール値のデータ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

複数のリソースのリソース ディメンションを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>説明

このサービスを使用すると、複数のリソースのリソース ディメンションが取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **dim** 宛先のディメンションへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

複数のリソースのリソース ディメンションを設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>説明

このサービスを使用すると、複数のリソースのリソース ディメンションが設定されます。

### <a name="parameters"></a>パラメーター

- **value** リソース値の説明へのポインター。
- **dim** ディメンション値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

32 ビット **浮動小数点数** リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、32 ビットの **浮動小数点数** リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **float32_ptr** 宛先の 32 ビット **浮動小数点数** 値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

32 ビット **浮動小数点数** リソースの値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>説明

32 ビット **浮動小数点数** リソースの値を設定します。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **float32_data** 32 ビットの **浮動小数点数** データ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

64 ビット浮動小数点数リソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、64 ビットの **浮動小数点数** リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **float64_ptr** 宛先の 64 ビット **浮動小数点数** 値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が浮動小数点数値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

64 ビット **浮動小数点数** リソースの値を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>説明

このサービスによって 64 ビット **浮動小数点数** リソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **float64_data** 64 ビットの **浮動小数点数** データ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

リソース情報を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>説明

このサービスを使用するとリソースのリソース情報が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **resource_id** 宛先リソース ID へのポインター。
- **操作** 宛先リソース操作へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

リソース情報を設定します。

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>説明

このサービスを使用するとリソース情報が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **resource_id** リソースの ID。
- **operation** リソースの操作。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

複数のリソースのインスタンスを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>説明

このサービスを使用するとリソースのリソース情報が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **resource_id** 宛先リソース ID へのポインター。
- **count** カウントへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。
- **NX_LWM2M_CLIENT_NO_MEMORY** インスタンスに入力するためのメモリがありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

リソース インスタンスを設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>説明

このサービスを使用すると、複数のリソースのリソース インスタンスが設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **resource_instance** リソース インスタンスへのポインター。
- **count** リソース インスタンスの数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

32 ビット整数リソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、32 ビット整数リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **integer32_ptr** 32 ビット整数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が整数値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

32 ビット整数リソースの値を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>説明

このサービスを使用すると、32 ビット整数リソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **integer32_data** 32 ビット整数データ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

64 ビット整数リソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、64 ビット整数リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **integer64_ptr** 64 ビット整数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が 64 ビット整数値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>64 ビット整数リソースの値を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>説明

このサービスを使用すると、64 ビット整数リソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **integer64_data** 64 ビット整数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

オブジェクト リンク リソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>説明

このサービスを使用すると、オブジェクト リンクの値が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **object_id** オブジェクト ID へのポインター。
- **instance_id** オブジェクト インスタンス ID へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がオブジェクト リンク値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

リソース インスタンスを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>説明

このサービスを使用すると、オブジェクト リンク リソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **object_id** オブジェクト ID。
- **instance_id** オブジェクト インスタンス ID。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

不透明なリソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>説明

このサービスを使用すると、不透明なリソースの値が取得されます。 不透明なリソース値は、バッファーへのポインターと長さで構成されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **opaque_ptr** 不透明なデータへのポインター。
- **opaque_ptr** 不透明なデータ長へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が不透明なリソースではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

不透明なリソースの値を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>説明

このサービスを使用すると、不透明なリソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **opaque_ptr** 不透明なデータへのポインター。
- **opaque_length** 不透明なデータの長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

文字列リソースの値を取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>説明

このサービスを使用すると、文字列リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **string_ptr** 宛先文字列ポインターへのポインター。
- **string_ptr** 宛先文字列長へのポインター。 文字列が null で終わる場合は **NULL** を指定できます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が文字列値ではありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

文字列リソースの値を設定します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>説明

このサービスを使用すると、64 ビット整数リソースの値が設定されます。

### <a name="parameters"></a>パラメーター

- **resource** リソースへのポインター。
- **string_ptr** 文字列へのポインター。
- **string_length** 文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

ブートストラップ サーバーとのセッションを開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>説明

このサービスを使用すると、ブートストラップ サーバーとのセッションが開始されます。 サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。

このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。
- **security_id** ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を NX_LWM2M_RESERVED_ID (65535) に設定する必要があります。
- **ip_address** サーバーの IP アドレス。
- **port** サーバーの UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、ブートストラップ サーバーとのセッションが開始されます。 サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。

この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。 **NX_SECURE_ENABLE_DTLS** を定義する必要があります。

このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。 

現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。
- **security_id** ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を **NX_LWM2M_RESERVED_ID** (65535) に設定する必要があります。
- **ip_address** サーバーの IP アドレス。
- **port** サーバーの UDP ポート。
- **dtls_session_ptr** ブートストラップ セッションに使用する DTLS セッション。
- **dtls_local_port** DTLS セッションに使用されるローカル UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

LWM2M クライアント セッションを作成します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>説明

このサービスを使用すると、既存の LWM2M クライアントにアタッチされた新しい LWM2M クライアント セッションが作成されます。 セッションは、ブートストラップ サーバーまたは LWM2M サーバーと通信するために LWM2M クライアントによって使用されます。 

アプリケーションは、セッションの状態が更新されたときに呼び出されるコールバック関数を提供する必要があります。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。
- **client_ptr** 以前に作成した LWM2M クライアントへのポインター。
- **state_callback** セッションの状態が変更されたときに呼び出されるアプリケーション コールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

LWM2M クライアント セッションを削除します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると LWM2M クライアント セッションが削除されます。

nx_lwm2m_client_delete を呼び出して LWM2M クライアントを削除すると、クライアントにアタッチされているすべてのセッションも削除されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

LWM2M サーバーとのセッションを終了します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M サーバーに対して "登録解除" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_NOT_REGISTERED** クライアントがサーバーに登録されていません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

セッションの最後のエラーを取得します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、セッションがエラー状態のときにセッションのエラー コードが返されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** セッションがエラー状態ではありません。
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** サーバー アドレスが無効です。
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** 要求のペイロードがネットワーク バッファーに収まりません。
- **NX_LWM2M_ CLIENT_DTLS_ERROR** サーバーとのセキュリティで保護された接続を確立できませんでした。
- **NX_LWM2M_ CLIENT_ERROR** 指定されていないエラー。
- **NX_LWM2M_ CLIENT_FORBIDDEN** サーバーによって登録が拒否されました。
- **NX_LWM2M_ CLIENT_NOT_FOUND** 更新または登録解除するときに、サーバーがクライアントを見つけることができませんでした。
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED**: セッションに対応するサーバー オブジェクト インスタンスが削除されました。
- **NX_LWM2M_ CLIENT_TIMED_OUT** サーバーからの応答がありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

LWM2M サーバーとのセッションを開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>説明

このサービスを使用すると、LWM2M サーバーに対して "登録" 操作が実行されます。 サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。

登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。
- **server_id** LWM2M サーバーの短いサーバー ID。
- **ip_address** サーバーの IP アドレス。
- **port** サーバーの UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

LWM2M サーバーとのセキュリティで保護されたセッションを開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、LWM2M サーバーへの "登録" 操作が実行されます。 サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。

この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。 **NX_SECURE_ENABLE_DTLS** を定義する必要があります。

登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。
- **server_id** LWM2M サーバーの短いサーバー ID。
- **ip_address** サーバーの IP アドレス。
- **port** サーバーの UDP ポート。
- **dtls_session_ptr** LWM2M セッションに使用する DTLS セッション。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

LWM2M サーバーとのセキュリティで保護されたセッションを開始します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>説明

ブートストラップ サーバーとの通信セッションが確立された後。 アプリケーションからこの API を呼び出して、次の登録ステップのためにサーバーとセキュリティ情報を取得できます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。
- **security_instance_id** セキュリティ インスタンス ID。
- **server_id** 宛先サーバー ID へのポインター。
- **server_uri** 宛先サーバー URI へのポインター。
- **server_uri_len** 宛先サーバー URI 長へのポインター。
- **security_mode** 宛先セキュリティ モードへのポインター。
- **pub_key_or_id** 宛先の公開キーまたは ID へのポインター。
- **pub_key_or_id_len** 宛先の公開キーまたは ID 長へのポインター。
- **server_pub_key** 宛先サーバーの公開キーへのポインター。
- **server_pub_key_len** 宛先サーバーの公開キー長へのポインター。
- **secret_key** 宛先の秘密キーへのポインター。
- **secret_key_len** 宛先の秘密キー長へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_NOT_FOUND** セキュリティ オブジェクト インスタンスがありません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

LWM2M サーバーとのセッションを更新します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M サーバーに対して "更新" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_LWM2M_CLIENT_NOT_REGISTERED** クライアントがサーバーに登録されていません。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

LWM2M クライアントをロック解除します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、***nx_lwm2m_client_unlock*** の呼び出しによって以前にロックされていた LWM2M クライアントのロックが解除されます。

### <a name="parameters"></a>パラメーター

- **client_ptr** LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** 操作に成功しました。
- **NX_PTR_ERROR** ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```