---
title: 第 3 章 - Azure RTOS NetX LWM2M の機能の説明
description: この章では、Azure RTOS NetX LWM2M の機能について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6424023a02aedf43c7433c9adc09231b8c146af13b9bddc15ebd1f2fc02e8c8a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784939"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>第 3 章 - Azure RTOS NetX LWM2M の機能の説明

この章では、Azure RTOS NetX LWM2M の機能について説明します。

## <a name="lwm2m-client-initialization"></a>LWM2M クライアントの初期化

LWM2M クライアントは、***nx_lwm2m_client_create*** サービスを呼び出すことによって初期化されます。 LWM2M クライアントは独自のスレッドで実行され、コールバックを使用するか、アプリケーションによって実装されたカスタム オブジェクトのメソッドを呼び出すことによって、アプリケーションにイベントをレポートできます。

また、1 つ以上のサーバーとの通信を有効にするために、***nx_lwm2m_client_session_create*** を呼び出して、LWM2M クライアント セッションを作成する必要があります。 セッションでは、ブートストラップ サーバーおよび LWM2M サーバー (デバイス管理) の 2 種類のサーバーと通信できます。

### <a name="bootstrap-server-session"></a>ブートストラップ サーバー セッション

ブートストラップ サーバーとの通信セッションは、LWM2M クライアントが 1 つ以上の LWM2M サーバーへの "登録" 操作を実行できるように、LWM2M クライアントに必須情報をプロビジョニングするために使用されます。 この種類のサーバーは、クライアントおよびサーバーが開始したブートストラップ モード中に使用されます。

アプリケーションでは、***nx_lwm2m_client_session_bootstrap** _ または _*_nx_lwm2m_client_session_bootstrap_dtls_*_ を呼び出すことによってブートストラップ セッションを開始できます。サーバーの IP アドレスとポート番号、およびオプションのセキュリティ オブジェクト インスタンス ID を指定する必要があります。 _*_nx_lwm2m_client_session_bootstrap_*_ 関数では、セキュリティで保護されていない通信が使用されます。一方、_ *_nx_lwm2m_client_session_bootstrap_dtls_** では、サーバーとのセキュリティで保護された DTLS 接続が確立されます。

ブートストラップ操作が成功した場合、ブートストラップ サーバーによって、ブートストラップ サーバーと LWM2M サーバーのセキュリティ オブジェクト インスタンス、および LWM2M サーバーのサーバー オブジェクト インスタンスが作成されている必要があります。 アプリケーションでは、この情報を使用して、LWM2M サーバーとのセッションを確立する必要があります。

デバイスの次回の再起動時に LWM2M クライアントを構成するために、アプリケーションはブートストラップ データを不揮発性メモリに保存する必要があります。

### <a name="lwm2m-server-session"></a>LWM2M サーバー セッション

LWM2M サーバーとの通信セッションは、登録、デバイス管理、サービスの有効化に使用されます。

アプリケーションでは、***nx_lwm2m_client_session_register** _ または _*_nx_lwm2m_client_session_register_dtls_*_ を呼び出すことによって、LWM2M クライアントをサーバーに登録できます。サーバーの IP アドレスとポート番号、および既存のサーバー オブジェクト インスタンスに対応する短いサーバー ID を指定する必要があります。 _*_nx_lwm2m_client_session_register_*_ 関数では、セキュリティで保護されていない通信が使用されます。一方、_ *_nx_lwm2m_client_session_register_dtls_** では、サーバーとのセキュリティで保護された DTLS 接続が確立されます。

アプリケーションでは、***nx_lwm2m_client_session_deregister** _ を呼び出して LWM2M クライアントを登録解除し、_*_nx_lwm2m_client_session_update_** を呼び出して、"Update" メッセージを送信するようクライアントに要求できます。

### <a name="session-state-callback"></a>セッション状態のコールバック

アプリケーションではセッションの作成時に、セッションの状態が更新されたときに呼び出されるコールバックを登録します。コールバック関数 NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK のプロトタイプを次に示します。

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

次の状態が定義されています。

- **NX_LWM2M_CLIENT_SESSION_INIT**: セッション作成後の初期状態です。

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: クライアントは、"Hold Off" タイマーまたはサーバーが開始したブートストラップの有効期限が切れるのを待機しています。

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: クライアントがブートストラップ サーバーに "Request" メッセージを送信しました (クライアントが開始したブートストラップ)。

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: クライアントがブートストラップ サーバーからデータを受信しています。

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: ブートストラップ サーバーが "Finished" メッセージを送信しました。

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: ブートストラップ セッションが失敗しました。

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: クライアントが LWM2M サーバーに "Register" メッセージを送信しました。

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: クライアントが LWM2M サーバーに登録されました。

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: クライアントが LWM2M サーバーに "Update" メッセージを送信しました。

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: クライアントが LWM2M サーバーに "De-register" メッセージを送信しました。

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: クライアントが LWM2M サーバーから登録解除されました。

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: LWM2M サーバーが無効になりました。 無効化タイマーの有効期限が切れると、"Register" が送信されます。

- **NX_LWM2M_CLIENT_SESSION_ERROR**: LWM2M サーバーに対する登録または更新操作が失敗しました。

- **NX_LWM2M_CLIENT_SESSION_DELETED**: LWM2M サーバーに対応するサーバー オブジェクト インスタンスが削除されました。 エラーが発生した場合、アプリケーションで **_nx_lwm2m_client_session_error_get_** を呼び出すことによってエラーの原因を取得できます。

## <a name="local-device-management"></a>ローカル デバイス管理

アプリケーションでは、ローカル デバイス管理関数を使用して、LWM2M クライアントのオブジェクトにアクセスできます。 次の関数が用意されています。

- ***nx_lwm2m_client_object_read***: オブジェクト インスタンスからリソースを読み取ります。

- ***nx_lwm2m_client_object_discover***: オブジェクト インスタンスのリソースのリストを取得します。

- ***nx_lwm2m_client_object_write***: オブジェクト インスタンスにリソースを書き込みます。

- ***nx_lwm2m_client_object_execute***: オブジェクト インスタンスのリソースに対して Execute 操作を実行します。

- ***nx_lwm2m_client_object_create***: 新しいオブジェクト インスタンスを作成します。

- ***nx_lwm2m_client_object_delete***: 既存のオブジェクト インスタンスを削除します。

- ***nx_lwm2m_client_object_get_next***: LWM2M クライアントで実装されている次のオブジェクト ID を取得します。

- ***nx_lwm2m_client_object_instance_get_next***: オブジェクトの次のインスタンスを取得します。

## <a name="resource-information"></a>リソース情報

オブジェクトに対して読み取りおよび書き込みを行うう場合、リソースは NX_LWM2M_RESOURCE 構造体で表されます。 この構造体には、リソースまたはインスタンスの ID とその値が格納されます。 値のエンコードは、値の型とソース (アプリケーションまたはネットワーク) によって異なります。

NX_LWM2M_RESOURCE 構造体の定義を次に示します。

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id**: リソースまたはインスタンスの ID。
- **nx_lwm2m_resource_type**: 値の型 (下記を参照)。
- **nx_lwm2m_resource_value**: リソースの値。値の型によって異なります。

次の型の値が定義されています。

- **NX_LWM2M_RESOURCE_NONE**: 空のリソース。

- **NX_LWM2M_RESOURCE_STRING**: *nx_lwm2m_resource_stringdata* に格納される null で終わる UTF-8 文字列値。

- **NX_LWM2M_RESOURCE_INTEGER32**: *nx_lwm2m_resource_integer32data* に格納される 32 ビット整数値。

- **NX_LWM2M_RESOURCE_INTEGER64**: *nx_lwm2m_resource_integer64data* に格納される 64 ビット整数値。

- **NX_LWM2M_RESOURCE_FLOAT32**: *nx_lwm2m_resource_float32data* に格納される 32 ビット浮動小数点値。

- **NX_LWM2M_RESOURCE_FLOAT64**: *nx_lwm2m_resource_float64data* に格納される 64 ビット浮動小数点値。

- **NX_LWM2M_RESOURCE_BOOLEAN**: *nx_lwm2m_resource_booleandata* に格納されるブール値。

- **NX_LWM2M_RESOURCE_OPAQUE**: *nx_lwm2m_resource_bufferdata* で定義される Opaque 値。

- **NX_LWM2M_RESOURCE_OBJLNK**: *nx_lwm2m_resource_objlnkdata* に格納されるオブジェクト リンク値。

- **NX_LWM2M_RESOURCE_TLV**: *nx_lwm2m_resource_bufferdata* で定義される TLV エンコードされた値。

- **NX_LWM2M_RESOURCE_TEXT**: *nx_lwm2m_resource_bufferdata* で定義されるプレーンテキスト エンコードされた値。

- **NX_LWM2M_RESOURCE_MULTIPLE**: *nx_lwm2m_resource_multipledata* で定義される複数リソース。 *nx_lwm2m_resource_multiple_ptr* は、各リソース インスタンスに関する情報を格納する **NX_LWM2M_RESOURCE** 構造体の配列へのポインターです。

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: *nx_lwm2m_resource_multipledata* で定義される複数リソース。 *nx_lwm2m_resource_multiple_ptr* は、TLV エンコードされたバッファーへのポインターです。

値を取得し、その型を確認するための便利な関数が用意されています。アプリケーションで NX_LWM2M_RESOURCE 構造体から値を取得するときに、*nx_lwm2m_resource_value* フィールドに直接アクセスしないでください。 次の関数が定義されています。

- ***nx_lwm2m_resource_get_***: 指定された型の値を取得します。
- ***nx_lwm2m_resource_multiple_get_***: 複数リソースから指定された型の値を取得します。

マクロ **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) を使用して、リソースの種類が複数リソースかどうかを確認できます。

## <a name="object-implementation"></a>オブジェクトの実装

LWM2M クライアントは、必須の OMA LWM2M オブジェクト (セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)) を実装します。 デバイス固有の他のオブジェクトは、アプリケーションによって実装する必要があります。

オブジェクトを定義するには、2 つのデータ構造体を使用します。NX_LWM2M_OBJECT 構造体では、オブジェクト ID やオブジェクト メソッドなど、オブジェクト実装を定義し、NX_LWM2M_OBJECT_INSTANCE 構造体には、オブジェクト インスタンスのデータが格納されます。

NX_LWM2M_OBJECT 構造体の定義を次に示します。

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next**: リスト内の次のオブジェクト。
- **nx_lwm2m_object_id**: オブジェクト ID。
- **nx_lwm2m_object_read**: "Read" メソッド (下記を参照)。
- **nx_lwm2m_object_discover**: "Discover" メソッド (下記を参照)。
- **nx_lwm2m_object_write**: "Write" メソッド (下記を参照)。
- **nx_lwm2m_object_execute**: "Execute" メソッド (下記を参照)。
- **nx_lwm2m_object_create**: "Create" メソッド (下記を参照)。
- **nx_lwm2m_object_delete**: "Delete" メソッド (下記を参照)。
- **nx_lwm2m_object_instances**: オブジェクト インスタンスの NULL で終わるリスト。

NX_LWM2M_OBJECT_INSTANCE 構造体の定義を次に示します。

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next**: リスト内の次のインスタンス。
- **nx_lwm2m_object_instance_id**: オブジェクト インスタンス ID。

オブジェクトでは、LWM2M デバイス管理インターフェイスで定義されている操作 ("Read"、"Discover"、"Write"、"Execute"、"Create"、"Delete") に対応するメソッドを実装する必要があります。 オブジェクトでインスタンスの動的作成がサポートされていない場合は、"Create" および "Delete" メソッドを NULL に設定できます。

### <a name="the-read-method"></a>"Read" メソッド

"Read" メソッドを使用して、オブジェクト インスタンスからリソース値を読み取ります。関数の定義を次に示します。

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

入力パラメーターは次のように定義されています。

- **object_ptr**: オブジェクト実装へのポインター。

- **instance_ptr**: オブジェクト インスタンスへのポインター。

- **num_values**: 読み取るリソースの数。

- **values_ptr**: 読み取るリソースの ID を格納する NX_LWM2M_RESOURCE の配列へのポインター。 戻り時に、配列には対応する型と値が格納されます。

### <a name="the-discover-method"></a>"Discover" メソッド

"Discover" メソッドを使用して、オブジェクトで実装されているすべてのリソースのリストを取得します。関数の定義を次に示します。

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

入力パラメーターは次のように定義されています。

- **object_ptr**: オブジェクト実装へのポインター。

- **instance_ptr**: オブジェクト インスタンスへのポインター。

- **num_resources_ptr**: 入力時はターゲット バッファーのサイズ、出力時はバッファーに書き込まれた要素の数。

- **resources_ptr**: 宛先バッファーへのポインター。

リソース情報は、次のように定義された NX_LWM2M_RESOURCE_INFO 構造体で返されます。

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id**: リソースの ID。

- **nx_lwm2m_resource_info_flags**: 下記を参照してください。

- **nx_lwm2m_resource_info_dim**: 複数リソースのディメンション (NX_LWM2M_RESOURCE_INFO_MULTIPLE フラグが設定されている場合)。

*nx_lwm2m_resource_flags* フィールドには、次の値を設定できます。

- 0: 読み取り可能な単一リソース。

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE**: 複数リソース。*nx_lwm2m_resource_info_dim* を定義する必要があります。

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: 実行可能ファイルまたは読み取り不可能なリソース。

### <a name="the-write-method"></a>"Write" メソッド

"Write" メソッドを使用して、オブジェクト インスタンスのリソースを更新または置換します。関数の定義を次に示します。

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

入力パラメーターは次のように定義されています。

- **object_ptr**: オブジェクト実装へのポインター。
- **instance_ptr**: オブジェクト インスタンスへのポインター。
- **num_values**: 書き込むリソースの数。
- **values_ptr**: リソース値へのポインター。
- **write_op**: 書き込み操作の種類。

*write_op* パラメーターには、次の書き込み操作を指定できます。

- 0 &mdash; 部分更新: 新しい値で提供されるリソースを追加または更新し、他の既存のリソースはそのままにしておきます。

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; インスタンスの置換: オブジェクト インスタンスを、指定された新しいリソース値に置き換えます。

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; リソースの置換: リソースを、指定された新しいリソース値に置き換えます (複数リソースを置き換えるために使用されます)。

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; インスタンスの作成: 指定されたリソース値を使用して、新しく作成されたオブジェクト インスタンスを初期化します (*nx_lwm2m_object_create* メソッドから呼び出されます)。

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; ブートストラップ書き込み: ブートストラップ シーケンス中に呼び出されます。

### <a name="the-execute-method"></a>"Execute" メソッド

"Execute" メソッドは、オブジェクト リソースの実行を実装します。関数の定義を次に示します。

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

入力パラメーターは次のように定義されています。

- **object_ptr**: オブジェクト実装へのポインター
- **instance_ptr**: オブジェクト インスタンスへのポインター。
- **resource_id**: リソース ID。
- **arguments_ptr**: 実行操作の引数へのポインター。 *arguments_length* が 0 の場合は、NULL を指定できます。
- **arguments_length**: 引数の長さ。

この関数では、リソース ID が存在しない場合は NX_LWM2M_NOT_FOUND を返し、実行をサポートしていない場合は NX_LWM2M_METHOD_NOT_ALLOWED を返す必要があります。

### <a name="the-create-method"></a>"Create" メソッド

"Create" メソッドは、新しいオブジェクト インスタンスの作成を実装します。関数の定義を次に示します。

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

入力パラメーターは次のように定義されています。

- **object_ptr**: オブジェクト実装へのポインター。
- **instance_id**: 新しいインスタンスの ID。
- **num_values**: 初期化するリソースの数。
- **values_ptr**: リソース値へのポインター。
- **instance_ptr**: 作成されたインスタンスの宛先ポインターへのポインター。
- **bootstrap**: ブートストラップ シーケンスから呼び出される場合は True。

オブジェクトは、リソース値の指定されたリストを使用して、新しいオブジェクト インスタンスを割り当てて初期化する必要があります。

### <a name="the-delete-method"></a>"Delete" メソッド

"Delete" メソッドは、オブジェクト インスタンスの削除を実装します。関数の定義を次に示します。

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

入力パラメーターは次のように定義されています。

- **object_ptr**: オブジェクト実装へのポインター。
- **instance_ptr**: オブジェクト インスタンスへのポインター。

成功した場合、オブジェクトはオブジェクト インスタンス データとインスタンスによって割り当てられたその他のリソースを解放する必要があります。

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>LWM2M クライアントへのオブジェクト実装およびインスタンスの追加

アプリケーションでは、***nx_lwm2m_client_object_add*** サービスを呼び出すことによって、新しいオブジェクト実装を LWM2M クライアントに追加できます。

オブジェクトでインスタンスの動的作成がサポートされていない場合 (単一インスタンスのみのオブジェクトの場合など)、オブジェクト構造体の *nx_lwm2m_object_instances* フィールドは、静的インスタンス構造体のリストを指している必要があります。

オブジェクトでインスタンスの動的作成がサポートされている場合は、オブジェクトの "Create" メソッドを呼び出すために、*nx_lwm2m_object_instances* を NULL に設定し、代わりに ***nx_lwm2m_client_object_create*** サービスを使用する必要があります。

## <a name="example-of-lwm2m-client-application"></a>LWM2M クライアント アプリケーションの例

次のコードは、温度センサーとライト スイッチで構成されるカスタム デバイスを実装する単純な LWM2M クライアント アプリケーションの例です。

このデバイスを使用すると、サーバーは、温度センサーの値とライト スイッチのブール値を読み取り、ライト スイッチをオン/オフに設定できます。

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
