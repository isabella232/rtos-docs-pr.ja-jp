---
title: 第 4 章 - Azure RTOS NetX LWM2M サービスの説明
description: この章では、すべての Azure RTOS NetX LWM2M サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 171f8577d252027548c24ec92f11f03c1fae768f1676f476256c13b8e8dc4175
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799083"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>第 4 章 - Azure RTOS NetX LWM2M サービスの説明

この章では、すべての Azure RTOS NetX LWM2M サービス (以下に記載) をアルファベット順に説明します。

次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

### <a name="lwm2m-client-management"></a>LWM2M クライアント管理

- **nx_lwm2m_client_create**: *LWM2M クライアントを作成します*
- **nx_lwm2m_client_delete**: *LWM2M クライアントを削除します*
- **nx_lwm2m_client_lock**: *LWM2M クライアントをロックします*
- **nx_lwm2m_client_object_add**: *LWM2M クライアントにオブジェクトの実装を追加します*
- **nx_lwm2m_client_unlock**: *LWM2M クライアントをロック解除します*

### <a name="lwm2m-client-session-management"></a>LWM2M クライアント セッション管理

- **nx_lwm2m_client_session_bootstrap**: *ブートストラップ サーバーとのセッションを開始します*
- **nx_lwm2m_client_session_bootstrap_dtls**: *ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します*
- **nx_lwm2m_client_session_create**: *LWM2M クライアント セッションを作成します*
- **nx_lwm2m_client_session_delete**: *LWM2M クライアント セッションを削除します*
- **nx_lwm2m_client_session_deregister**: *LWM2M サーバーとのセッションを終了します*
- **nx_lwm2m_client_session_error_get**: *セッションの最後のエラーを取得します*
- **nx_lwm2m_client_session_register**: *LWM2M Server とのセッションを開始します*
- **nx_lwm2m_client_session_register_dtls**: *LWM2M サーバーとのセキュアなセッションを開始します*
- **nx_lwm2m_client_session_update**: *LWM2M サーバーとのセッションを更新します*

### <a name="security-object-implementation"></a>セキュリティ オブジェクトの実装

- **nx_lwm2m_client_security_key_callbacks_set**: *セキュリティ キー管理コールバックを設定します*

### <a name="device-object-implementation"></a>デバイス オブジェクトの実装

- **nx_lwm2m_client_device_callbacks_set**: *デバイス オブジェクトのアプリケーションのコールバックを設定します*
- **nx_lwm2m_client_device_error_push**: *デバイス オブジェクトにエラー コードを追加します*
- **nx_lwm2m_client_device_error_reset**: *デバイス オブジェクトのエラー コードをリセットします*
- **nx_lwm2m_client_device_resource_changed**: *デバイス オブジェクト リソースのシグナルを変更します*

### <a name="custom-objects-implementation"></a>カスタム オブジェクトの実装

- **nx_lwm2m_object_resource_changed**: *オブジェクト インスタンスのリソース値のシグナルを変更します*

### <a name="local-device-management"></a>ローカル デバイスの管理

- **nx_lwm2m_client_object_create**: *新しいオブジェクト インスタンスを作成します*
- **nx_lwm2m_client_object_delete**: *オブジェクト インスタンスを削除します*
- **nx_lwm2m_client_object_discover**: *オブジェクト インスタンスのリソースを検出します*
- **nx_lwm2m_client_object_execute**: *オブジェクト インスタンスのリソースを実行します*
- **nx_lwm2m_client_object_get_next**: *LWM2M クライアントによって実装されているオブジェクトのリストを取得します*
- **nx_lwm2m_client_object_instance_get_next**: *オブジェクトのインスタンスのリストを取得します*
- **nx_lwm2m_client_object_read**: *オブジェクト インスタンスのリソース値を読み取ります*
- **nx_lwm2m_client_object_write**: *オブジェクト インスタンスのリソース値を変更します*

### <a name="resources-values-decoding"></a>リソース値のデコード

- **nx_lwm2m_resource_get_boolean**: *ブール型リソースの値を取得します*
- **nx_lwm2m_resource_get_float32**: *32 ビット浮動小数点リソースの値を取得します*
- **nx_lwm2m_resource_get_float64**: *64 ビット浮動小数点リソースの値を取得します*
- **nx_lwm2m_resource_get_integer32**: *32 ビット整数リソースの値を取得します*
- **nx_lwm2m_resource_get_integer64**: *64 ビット整数リソースの値を取得します*
- **nx_lwm2m_resource_get_objlnk**: *オブジェクト リンク リソースの値を取得します*
- **nx_lwm2m_resource_get_opaque**: *非透過リソースの値を取得します*
- **nx_lwm2m_resource_get_string**: *文字列リソースの値を取得します*
- **nx_lwm2m_resource_multiple_get_boolean**: *ブール型リソースの複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_float32**: *32 ビット浮動小数点の複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_float64**: *64 ビット浮動小数点の複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_integer32**: *32 ビット整数の複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_integer64**: *64 ビット整数の複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_objlnk**: *オブジェクト リンクの複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_opaque**: *非透過複数リソース インスタンスの値を取得します*
- **nx_lwm2m_resource_multiple_get_string**: *文字列の複数リソース インスタンスの値を取得します*

### <a name="firmware-update-object"></a>ファームウェア更新オブジェクト

- **nx_lwm2m_firmware_create**: *ファームウェア更新オブジェクトを作成します*
- **nx_lwm2m_firmware_package_info_set**: *ファームウェア更新パッケージの情報を設定します*
- **nx_lwm2m_firmware_result_set**: *ファームウェアの更新結果を設定します*
- **nx_lwm2m_firmware_state_set**: *ファームウェアの更新状態を設定します*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

LWM2M クライアントを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>説明

このサービスを使用すると、専用の ThreadX スレッドのコンテキスト内で実行される LWM2M クライアント インスタンスが作成されます。

LWM2M クライアントには、次の OMA LWM2M オブジェクトが実装されています: セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)。 その他のオブジェクトの実装は、アプリケーションによって追加される必要があります。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **ip_ptr**: 以前に作成された IP インスタンスへのポインター。
- **packet_pool_ptr**: この LWM2M クライアントの既定のパケット プールへのポインター。
- **local_port**: セキュリティで保護されていない通信に使用されるローカル UDP ポート。
- **name_ptr**: LWM2M クライアント エンドポイント名へのポインター。
- **msisdn_ptr**: SMS バインディングで使用するために LWM2M クライアントに到達できる MSISDN へのポインター。SMS バインディングがサポートされていない場合は、NULL にすることができます。
- **binding_modes**: LWM2M クライアントでサポートされているバインディングとモードは、NX_LWM2M_BINDING_U、NX_LWM2M_BINDING_UQ、NX_LWM2M_BINDING_S、および NX_LWM2M_BINDING_SQ フラグの組み合わせになっている必要があります。
- **stack_ptr**: LWM2M クライアント スレッド スタック領域へのポインター。
- **stack_size**: LWM2M クライアント スレッド スタック サイズへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: LWM2M クライアントの作成に成功しました。
- **NX_LWM2M_ERROR**: LWM2M クライアントの作成エラー。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

LWM2M クライアントを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、以前に作成された LWM2M クライアント インスタンスが削除されます。

現在クライアントにアタッチされているすべてのセッションも、この呼び出しによって削除されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: LWM2M クライアントの削除に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

デバイス オブジェクト アプリケーションのコールバックを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントによって処理されない LWM2M デバイス オブジェクト リソースの操作を実装するためのアプリケーション コールバックがインストールされます。

LWM2M クライアントは、次のリソースを実装します: エラー コード (11)、リセット エラー コード (12)、サポートされているバインドとモード (16)。他のリソースに対する操作は、アプリケーションにリダイレクトされます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **read_callback**: "Read" メソッドのコールバック。
- **discover_callback**: "Discover" メソッドのコールバック。
- **write_callback**: "Write" メソッドのコールバック。
- **execute_callback**: "Execute" メソッドのコールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

デバイス オブジェクトにエラー コードを追加します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>説明

このサービスを使用すると、オブジェクト デバイスのエラー コード (11) リソースに新しいインスタンスが追加されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **code**: 新しいエラー コード。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BUFFER_TOO_SMALL**: 格納されているエラー コードの最大数に達しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

デバイス オブジェクトのエラー コードをリセットします

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、すべてのエラー コード リソース インスタンスがデバイス オブジェクトから削除されます。 これは、リソース リセット エラー コード (12) を実行することと同じです。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

デバイス オブジェクト リソースのシグナルを変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって、オブジェクト デバイスのリソースが変更されたことを LWM2M クライアントに通知するために使用されます。 LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **resource**: 変更されたリソースを記述する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

LWM2M クライアントをロックします

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、サーバーまたは別のアプリケーション スレッドからの LWM2M オブジェクトへの同時アクセスを防ぐために、LWM2M クライアントがロックされます。

LWM2M クライアントが現在別のスレッドによってロックされている場合、この関数は LWM2M クライアントがロック解除されるまでブロックします。

nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() ペアへの呼び出しは入れ子にすることができます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

オブジェクトの実装を LWM2M クライアントに追加します。

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、新しいオブジェクトの実装が LWM2M クライアントに追加されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_ptr**: オブジェクトの実装を定義する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_ALREADY_EXIST**: オブジェクト ID は既に存在しています。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

新しいオブジェクト インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクトに対して "作成" 操作を実行して、新しいオブジェクト インスタンスが作成されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id_ptr**: 新しいインスタンスの ID へのポインター。LWM2M クライアントによってインスタンス ID を割り当てる必要がある場合は、NULL にすることができます。 ID が予約値 65535 の場合、LWM2M クライアントによってインスタンス ID が割り当てられます。 NULL 以外の場合は、割り当てられた ID が呼び出しの後に返されます。
- **num_values**: 設定する値の数。
- **values_ptr**: 新しいオブジェクト インスタンスを初期化するためのリソース値の配列へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_ALREADY_EXIST**: オブジェクト インスタンス ID は既に存在しています。
- **NX_LWM2M_METHOD_NOT_ALLOWED**: オブジェクトはインスタンスの作成をサポートしていません。
- **NX_LWM2M_NO_MEMORY**: 新しいインスタンスを格納するためのメモリを割り当てることができません。
- **NX_LWM2M_NOT_FOUND**: オブジェクト ID が存在していません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

オブジェクト インスタンスを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "削除" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id**: オブジェクト インスタンス ID。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_METHOD_NOT_ALLOWED**: オブジェクトはインスタンスの削除をサポートしていません。
- **NX_LWM2M_NOT_FOUND**: オブジェクト ID またはオブジェクト インスタンス ID が存在していません。
- NX_PTR_ERROR ポインターが無効です。

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

オブジェクト インスタンスのリソースを検出します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "検出" 操作が実行されます。これにより、オブジェクトによって実装されたリソースのリストが返されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id**: オブジェクト インスタンス ID。
- **num_resources_ptr**: 入力時は宛先バッファーのサイズ、出力時はバッファーに書き込まれた要素の数。
- **resources_ptr**: 宛先バッファーへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BUFFER_TOO_SMALL**: リソース バッファーが小さすぎて、リソースのリストを格納できません。
- **NX_LWM2M_NOT_FOUND**: オブジェクト ID またはオブジェクト インスタンス ID が存在していません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

オブジェクト インスタンスのリソースを実行します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンス リソースの "実行" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id**: オブジェクト インスタンス ID。
- **resource_id**: リソース ID。
- **arguments_ptr**: 実行操作の引数へのポインター。 arguments_length が 0 の場合は、NULL を指定できます。
- **arguments_length**: 引数の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_METHOD_NOT_ALLOWED**: リソースは実行操作をサポートしていません。
- **NX_LWM2M_NOT_FOUND**: オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

LWM2M クライアントによって実装されたオブジェクトの一覧を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントによって実装される次のオブジェクトの ID が返されます。 現在のオブジェクト ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合、最初のオブジェクト ID が返されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id_ptr**: 現在のオブジェクト ID へのポインター。 戻り値には、LWM2M クライアントによって実装される次のオブジェクト ID が含まれます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_FOUND**: 指定されたオブジェクト ID は、データベースの最後です。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

オブジェクトのインスタンスの一覧を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたオブジェクトの次のオブジェクト インスタンスの ID が返されます。 現在のインスタンス ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合は、最初のインスタンスの ID が返されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id_ptr**: 現在のオブジェクト インスタンス ID へのポインター。 戻り値には、オブジェクトの次のインスタンス ID が含まれます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_FOUND**: 指定されたインスタンス ID がオブジェクトの最後か、オブジェクト ID が実装されていません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

オブジェクト インスタンスのリソース値を読み取ります

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "読み取り" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id**: オブジェクト インスタンス ID。
- **num_values**: 読み取るリソースの数。
- **values_ptr**: 読み取るリソースの ID を格納する NX_LWM2M_RESOURCE の配列へのポインター。 返されると、配列に対応する型と値が格納されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_METHOD_NOT_ALLOWED**: リソースで読み取り操作がサポートされていません。
- **NX_LWM2M_NOT_FOUND**: オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

オブジェクト インスタンスのリソース値を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "書き込み" 操作が実行されます。

*write_op* パラメーターには、次の書き込み操作を指定できます。

- **0** &mdash; 部分更新: 新しい値で提供されるリソースを追加または更新し、他の既存のリソースはそのままにしておきます。

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; インスタンスの置換: オブジェクト インスタンスを、指定された新しいリソース値に置き換えます。

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; リソースの置換: リソースを、指定された新しいリソース値に置き換えます (複数リソースを置き換えるために使用されます)。

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; ブートストラップ書き込み: ブートストラップ シーケンスからの呼び出しを示します。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **object_id**: オブジェクト ID。
- **instance_id**: オブジェクト インスタンス ID。
- **num_values**: 書き込むリソースの数。
- **values_ptr**: リソースの ID、および書き込む型と値を格納する NX_LWM2M_RESOURCE の配列へのポインター。
- **write_op**: 書き込み操作の種類。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソースの型が無効です。
- **NX_LWM2M_BUFFER_TOO_SMALL**: 値の長さが大きすぎてインスタンスに格納できません。
- **NX_LWM2M_METHOD_NOT_ALLOWED**: リソースが読み書き込み操作をサポートしていません。
- **NX_LWM2M_NO_MEMORY**: リソース値を格納するためのメモリを割り当てることができません。
- **NX_LWM2M_NOT_ACCEPTABLE**: リソースの値が無効です。
- **NX_LWM2M_NOT_FOUND**: オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。
- NX_OPTION_ERROR: 書き込み操作の種類が無効です。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

セキュリティ オブジェクト キー管理のコールバックを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>説明

このサービスを使用すると、セキュリティ キーに関連する LWM2M セキュリティ オブジェクト リソースに対する操作を実装するためのアプリケーションのコールバックがインストールされます。

ブートストラップ セッション中は、LWM2M クライアントからアプリケーションにセキュリティ キー管理が委任されます。ブートストラップ サーバーによりセキュリティ オブジェクト インスタンスに次のリソースが書き込まれるか削除されると、コールバックが呼び出されます: 公開キーまたは ID (3)、サーバー公開キー (4)、秘密キー (5)。

アプリケーションは、キー データの格納と、LWM2M クライアントに使用される DTLS セッションの構成を担当します。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。
- **write_callback**: "Write" キー メソッドのコールバック。
- **delete_callback**: "Delete" キー メソッドのコールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

ブートストラップ サーバーとのセッションを開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>説明

このサービスを使用すると、ブートストラップ サーバーとのセッションが開始されます。 サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。

このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。
- **security_id**: ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を NX_LWM2M_RESERVED_ID (65535) に設定する必要があります。
- **ip_address**: サーバーの IP アドレス。
- **port**: サーバーの UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_FOUND**: セキュリティ インスタンス ID に対応するセキュリティ オブジェクト インスタンスがありません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>説明

このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、ブートストラップ サーバーとのセッションが開始されます。 サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。

この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。 NX_SECURE_ENABLE_DTLS を定義する必要があります。

このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。
- **security_id**: ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を NX_LWM2M_RESERVED_ID (65535) に設定する必要があります。
- **ip_address**: サーバーの IP アドレス。
- **port**: サーバーの UDP ポート。
- **dtls_session_ptr**: ブートストラップ セッションに使用する DTLS セッション。
- **dtls_local_port**: DTLS セッションに使用されるローカル UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_FOUND**: セキュリティ インスタンス ID に対応するセキュリティ オブジェクト インスタンスがありません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

LWM2M クライアント セッションを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>説明

このサービスを使用すると、既存の LWM2M クライアントにアタッチされた新しい LWM2M クライアント セッションが作成されます。 セッションは、ブートストラップ サーバーまたは LWM2M サーバーと通信するために LWM2M クライアントによって使用されます。

アプリケーションは、セッションの状態が更新されたときに呼び出されるコールバック関数を提供する必要があります。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。
- **client_ptr**: 以前に作成した LWM2M クライアントへのポインター。
- **state_callback**: セッションの状態が変更されたときに呼び出されるアプリケーション コールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

LWM2M クライアント セッションを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると LWM2M クライアント セッションが削除されます。

nx_lwm2m_client_delete を呼び出して LWM2M クライアントを削除すると、クライアントにアタッチされているすべてのセッションも削除されます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

LWM2M サーバーとのセッションを終了します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M サーバーに対して "登録解除" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_REGISTERED**: クライアントがサーバーに登録されていません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

セッションの最後のエラーを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、セッションがエラー状態のときにセッションのエラー コードが返されます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: セッションがエラー状態ではありません。
- **NX_LWM2M_ADDRESS_ERROR**: サーバー アドレスが無効です。
- **NX_LWM2M_BUFFER_TOO_SMALL**: 要求のペイロードがネットワーク バッファーに収まりません。
- **NX_LWM2M_DTLS_ERROR**: サーバーとのセキュリティで保護された接続を確立できませんでした。
- **NX_LWM2M_ERROR**: 特定できないエラー。
- **NX_LWM2M_FORBIDDEN**: サーバーによって登録が拒否されました。
- **NX_LWM2M_NOT_FOUND**: 更新または登録解除するときに、サーバーがクライアントを見つけることができませんでした。
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: セッションに対応するサーバー オブジェクト インスタンスが削除されました。
- **NX_LWM2M_TIMED_OUT**: サーバーからの応答がありません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

LWM2M サーバーとのセッションを開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M サーバーに対して "登録" 操作が実行されます。 サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。

登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。
- **server_id**: LWM2M サーバーの短いサーバー ID。
- **ip_address**: サーバーの IP アドレス。
- **port**: サーバーの UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_FOUND**: 短いサーバー ID に対応するサーバー オブジェクト インスタンスがありません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

LWM2M サーバーとのセキュリティで保護されたセッションを開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>説明

このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、LWM2M サーバーへの "登録" 操作が実行されます。 サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。

この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。 NX_SECURE_ENABLE_DTLS を定義する必要があります。

各 DTLS セッションは通信に独自の UDP ソケットを使用されているため、アプリケーションによって複数のセキュリティで保護されたセッションが作成される場合、セッションごとに異なるローカル ポート dtls_local_port にする必要があります。

登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。

現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。
- **server_id**: LWM2M サーバーの短いサーバー ID。
- **ip_address**: サーバーの IP アドレス。
- **port**: サーバーの UDP ポート。
- **dtls_session_ptr**: LWM2M セッションに使用する DTLS セッション。
- **dtls_local_port**: DTLS セッションに使用されるローカル UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_FOUND**: 短いサーバー ID に対応するサーバー オブジェクト インスタンスがありません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

LWM2M サーバーとのセッションを更新します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、LWM2M サーバーに対して "更新" 操作が実行されます。

### <a name="parameters"></a>パラメーター

- **session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_NOT_REGISTERED**: クライアントがサーバーに登録されていません。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

LWM2M クライアントのロックを解除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、nx_lwm2m_client_unlock() の呼び出しによって以前にロックされていた LWM2M クライアントのロックが解除されます。

### <a name="parameters"></a>パラメーター

- **client_ptr**: LWM2M クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

ファームウェア更新オブジェクトを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>説明

このサービスを使用すると、ファームウェア更新オブジェクトが初期化され、以前に作成した LWM2M クライアントにオブジェクトが追加されます。 ファームウェア更新オブジェクトには、LWM2M サーバーと通信するためのリソースが実装されていますが、アプリケーションには、ファームウェアに対する実際の操作 (ファームウェアのダウンロード、格納、および更新) を実装するためのコールバックを用意する必要があります。

このプロトコル パラメーターは、"パッケージ URI" リソースを使用してファームウェアを取得する場合に、アプリケーションでサポートされているプロトコルを示します。次のフラグが定義されています:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP、NX_LWM2M_FIRMWARE_PROTOCOL_COAPS、NX_LWM2M_FIRMWARE_PROTOCOL_HTTP、NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS。

### <a name="parameters"></a>パラメーター

- **firmware_ptr**: ファームウェア オブジェクト制御ブロックへのポインター。
- **client_ptr**: 以前に作成した LWM2M クライアントへのポインター。
- **protocols**: パッケージ URI リソースでサポートされているプロトコルを示すフラグ。
- **package_callback**: NULL にする必要があります [TBD]。
- **package_uri_callback**: パッケージ URI リソースの実装に使用されるコールバック。
- **update_callback**: 更新リソースの実装に使用されるコールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

ファームウェア更新パッケージ情報を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>説明

このサービスを使用すると、ファームウェア更新オブジェクトの "PkgName" (6) および "PkgVersion" (7) リソースの値が変更されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr**: ファームウェア更新オブジェクトへのポインター。
- **name**: パッケージ名の新しい値。
- **version**: パッケージ バージョンの新しい値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

ファームウェアの更新結果を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>説明

このサービスを使用すると、ファームウェア更新オブジェクトの "更新結果" (5) リソースの値が変更されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr**: ファームウェア更新オブジェクトへのポインター。
- **result**: 更新結果リソースの新しい値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

ファームウェア更新状態を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>説明

このサービスを使用すると、ファームウェア更新オブジェクトの "状態" (3) リソースの値が変更されます。

### <a name="parameters"></a>パラメーター

- **firmware_ptr**: ファームウェア更新オブジェクトへのポインター。
- **state**: 状態リソースの新しい値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

オブジェクト インスタンスのリソース値のシグナルを変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>説明

このサービスは、リソース値の 1 つが変更されたことを LWM2M クライアントに通知するために、オブジェクトの実装によって使用されます。 LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。

### <a name="parameters"></a>パラメーター

- **object_ptr**: オブジェクト実装へのポインター。
- **instance_ptr**: オブジェクト インスタンスへのポインター。
- **resource**: 変更されたリソースを記述する構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- NX_PTR_ERROR: ポインターが無効です。

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

ブール値リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>説明

このサービスを使用するとブール値リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **bool_ptr**: 宛先ブール値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値がブール値ではありません。

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

32 ビット浮動小数点リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、32 ビット浮動小数点リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **float32_ptr**: 宛先 32 ビット浮動小数点数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値は浮動小数点値ではありません。

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

64 ビット浮動小数点リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、64 ビット浮動小数点リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **float64_ptr**: 宛先 64 ビット浮動小数点数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値は浮動小数点値ではありません。

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

32 ビット整数リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、32 ビット整数リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **int32_ptr**: 宛先 32 ビット整数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値が整数値でないか、整数値が 32 ビットの数値に収まりません。

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

64 ビット整数リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、64 ビット整数リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **int64_ptr**: 宛先 64 ビット整数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値が整数値ではありません。

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

オブジェクト リンク リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、オブジェクト リンク リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **objlnk_ptr**: 宛先オブジェクト リンク値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値がオブジェクト リンク値ではありません。

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

非透過リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、非透過リソースの値が取得されます。

非透過リソース値は、バッファーへのポインターと長さで構成されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **opaque_ptr_ptr**: 宛先の非透過バッファー ポインターへのポインター。
- **opaque_length_ptr**: 宛先の非透過バッファー長へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値が非透過値ではありません。

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

文字列リソースの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、文字列リソースの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: リソース値の説明へのポインター。
- **string_ptr_ptr**: 宛先文字列ポインターへのポインター。
- **string_length_ptr**: 宛先文字列長へのポインター。 文字列が null で終わる場合は NULL を指定できます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_ENCODING**: リソース値が文字列値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

ブール型リソースの複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースからブール値のリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **bool_ptr**: 宛先ブール値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値がブール値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

32 ビット浮動小数点の複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースから 32 ビット浮動小数点のリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **float32_ptr**: 宛先 32 ビット浮動小数点数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が浮動小数点値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

64 ビット浮動小数点の複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースから 64 ビット浮動小数点型のリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **float64_ptr**: 宛先 64 ビット浮動小数点数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が浮動小数点値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

32 ビット整数の複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースから 32 ビット整数のリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **int32_ptr**: 宛先 32 ビット整数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が整数値ではないか、整数値が 32 ビットの数値に収まりません。

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

64 ビット整数の複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースから 64 ビット整数のリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **int64_ptr**: 宛先 64 ビット整数値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が整数値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

オブジェクト リンクの複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースからオブジェクト リンクのリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **objlnk_ptr**: 宛先オブジェクト リンク値へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値がオブジェクト リンク値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

非透過複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースから非透過のリソース インスタンスの値が取得されます。

非透過リソース値は、バッファーへのポインターと長さで構成されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **opaque_ptr_ptr**: 宛先の非透過バッファー ポインターへのポインター。
- **opaque_length_ptr**: 宛先の非透過バッファー長へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が非透過値ではありません。

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

文字列の複数リソース インスタンスの値を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、複数リソースから文字列のリソース インスタンスの値が取得されます。

### <a name="parameters"></a>パラメーター

- **value**: 複数リソース値の説明へのポインター。
- **index**: リソース値の配列で取得するインスタンスのインデックス。
- **instance_id_ptr**: 宛先インスタンス ID へのポインター。
- **string_ptr_ptr**: 宛先文字列ポインターへのポインター。
- **string_length_ptr**: 宛先文字列長へのポインター。 文字列が null で終わる場合は NULL を指定できます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: 操作に成功しました。
- **NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。
- **NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、インスタンス値が文字列値ではありません。
