---
title: 第 3 章 - LWM2M クライアントの機能の説明
description: この章では、LWM2M クライアントの機能について説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810754"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>第 3 章  LWM2M クライアントの機能の説明

> この章では、LWM2M クライアントの機能について説明します。

## <a name="lwm2m-client-initialization"></a>LWM2M クライアントの初期化

LWM2M クライアントは、***nx_lwm2m_client_create*** サービスを呼び出すことによって初期化されます。 LWM2M クライアントは独自のスレッドで実行され、コールバックを使用するか、アプリケーションによって実装されたカスタム オブジェクトのメソッドを呼び出すことによって、アプリケーションにいくつかのイベントを報告できます。

さらに、1 つ以上のサーバーとの通信を有効にするために、***nx_lwm2m_client_session_create*** を呼び出すことによって、LWM2M クライアント セッションを作成する必要があります。 セッションは、ブートストラップ サーバーまたは LWM2M サーバー (デバイス管理) という 2 つの異なる種類のサーバーと通信できます。

### <a name="bootstrap-server-session"></a>ブートストラップ サーバー セッション

ブートストラップ サーバーとの通信セッションを使用して、LWM2M クライアントに重要な情報を提供し、LWM2M クライアントが 1 つ以上の LWM2M サーバーに対して "登録" 操作を実行できるようにします。 この種類のサーバーは、クライアントによって開始され、サーバーによって開始されたブートストラップ モードで使用されます。

アプリケーションから ***nx_lwm2m_client_session_bootstrap** _ または _*_nx_lwm2m_client_session_bootstrap_dtls_*_ を呼び出すことによってブートストラップ セッションを開始できます。サーバーの IP アドレスとポート番号、およびオプションのセキュリティ オブジェクト インスタンス ID を指定する必要があります。 _*_nx_lwm2m_client_session_bootstrap_*_ 関数は、セキュリティで保護されていない通信を使用します。一方、_ *_nx_lwm2m_client_session_bootstrap_dtls_** は、サーバーとのセキュリティで保護された dtls 接続を確立します。

ブートストラップ操作が成功した場合、ブートストラップ サーバーでは、ブートストラップ サーバーと LWM2M サーバーのセキュリティ オブジェクト インスタンス、および LWM2M サーバーのサーバー オブジェクト インスタンスが作成されている必要があります。 アプリケーションから ***nx_lwm2m_client_session_register_info_get*** が呼び出されて LWM2M サーバーの情報が取得され、この情報を使用して LWM2M サーバーとのセッションが確立されます。

ブートストラップ データは、デバイスの次回の再起動時に LWM2M クライアントを構成するために、アプリケーションによって不揮発性メモリに保存される必要があります。

### <a name="lwm2m-server-session"></a>LWM2M サーバー セッション

LWM2M サーバーとの通信セッションは、登録、デバイス管理、およびサービスの有効化に使用されます。

アプリケーションから ***nx_lwm2m_client_session_register** _ または _*_nx_lwm2m_client_session_register_dtls_*_ が呼び出されることによって LWM2M クライアントがサーバーに登録されます。また、サーバーの IP アドレスとポート番号、および既存のサーバー オブジェクト インスタンスに対応する短いサーバー ID を指定する必要があります。 _*_nx_lwm2m_client_session_register_*_ 関数では、セキュリティで保護されていない通信が使用されます。一方、_ *_nx_lwm2m_client_session_register_dtls_** によって、サーバーとのセキュリティで保護された dtls 接続が確立されます。

アプリケーションから ***nx_lwm2m_client_session_deregister** _ が呼び出されて LWM2M クライアントが登録解除され、_*_nx_lwm2m_client_session_update_** が呼び出されて、クライアントに "更新" メッセージを送信するように要求されます。

### <a name="session-state-callback"></a>セッション状態のコールバック

アプリケーションは、セッションの作成時にコールバックを登録します。これは、セッションの状態が更新されたときに呼び出されます。コールバック関数 **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** には、次のプロトタイプがあります。

typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);

次の状態が定義されます。

| Session&nbsp;State | 説明 |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | セッション作成後の初期状態です。 |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | クライアントは、"Hold Off" タイマーまたはサーバー開始ブートストラップの有効期限が切れるのを待機しています。 |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | クライアントが "要求" メッセージをブートストラップ サーバー (クライアントが開始したブートストラップ) に送信しました。 |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | クライアントがブートストラップ サーバーからデータを受信しています。 |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | ブートストラップ サーバーから "完了" メッセージが送信されました。 |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | ブートストラップ セッションが失敗しました。 |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | クライアントから LWM2M サーバーに "登録" メッセージが送信されました。 |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | クライアントが LWM2M サーバーに登録されました。 |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | クライアントから LWM2M サーバーに "更新" メッセージが送信されました。 |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | クライアントから LWM2M サーバーに "登録解除" メッセージが送信されました。 |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | クライアントが、LWM2M サーバーから登録解除されました。 |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | LWM2M サーバーが無効になっています。 無効化タイマーの有効期限が切れると、'Register' が送信されます。 |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | LWM2M サーバーへの登録または更新操作に失敗しました。 |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | LWM2M サーバーに対応するサーバー オブジェクト インスタンスが削除されました。 |

エラーが発生した場合、アプリケーションから ***nx_lwm2m_client_session_error_get*** が呼び出されることによってエラーの原因を取得できます。

## <a name="local-device-management"></a>ローカル デバイス管理

アプリケーションからは、ローカル デバイス管理機能を使用して、LWM2M クライアントのオブジェクトにアクセスできます。 次の関数が提供されています。

| 関数&nbsp;名 | 説明 |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | オブジェクト インスタンスからリソースを読み取ります。 |
| ***nx_lwm2m_client_object_discover*** | オブジェクト インスタンスのリソースのリストを取得します。
| ***nx_lwm2m_client_object_write*** | オブジェクト インスタンスにリソースを書き込みます。 |
| ***nx_lwm2m_client_object_execute*** | オブジェクト インスタンスのリソースに対して実行操作を実行します。 |
| ***nx_lwm2m_client_object_create*** | 新しいオブジェクト インスタンスを作成します。 |
| ***nx_lwm2m_client_object_delete*** | 既存のオブジェクト インスタンスを削除します。 |
| ***nx_lwm2m_client_object_next_get*** | LWM2M クライアントによって次のオブジェクト ID を取得します。 |
| ***nx_lwm2m_client_object_instance_next_get*** | オブジェクトの次のインスタンスを取得します。 |

## <a name="resource-information"></a>リソース情報

オブジェクトへの読み取りと書き込みを行う場合、リソースは NX_LWM2M_CLIENT_RESOURCE 構造体によって表されます。 この構造体には、リソースまたはインスタンスの ID とその値が含まれています。

リソースの情報と値を設定するために、次の関数が用意されています。

| 関数&nbsp;名 | 説明 |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | リソース情報の設定: リソース ID と操作: 読み取り、書き込み、実行可能。 |
| ***nx_lwm2m_client_resource_string_set*** | リソース値を文字列として設定します。 |
| ***nx_lwm2m_client_resource_integer32_set*** | リソース値を 32 ビット整数として設定します。 |
| ***nx_lwm2m_client_resource_integer64_set*** | リソース値を 64 ビット整数として設定します。 |
| ***nx_lwm2m_client_resource_float32_set*** | リソース値を 32 ビット浮動小数点数として設定します。 |
| ***nx_lwm2m_client_resource_float64_set*** | リソース値を 64 ビット浮動小数点数として設定します。 |
| ***nx_lwm2m_client_resource_boolean_set*** | リソース値をブール値として設定します。 |
| ***nx_lwm2m_client_resource_objlnk_set*** | リソース値をオブジェクト リンクとして設定します。 |
| ***nx_lwm2m_client_resource_opaque_set*** | リソース値を不透明として設定します。 |
| ***nx_lwm2m_client_resource_instance_set*** | リソース値を複数のリソースのインスタンスとして設定します。 |
| ***nx_lwm2m_client_resource_dim_set*** | 検出する複数のリソースのリソース ディメンションを設定します。 |

リソースの情報と値を取得するために、次の関数が用意されています。

| 関数&nbsp;名 | 説明 |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | リソース情報の取得: リソース ID と操作: 読み取り、書き込み、実行可能。 |
| ***nx_lwm2m_client_resource_string_get*** | 文字列リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_integer32_get*** | 32 ビット整数リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_integer64_get*** | 64 ビット整数リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_float32_get*** | 32 ビット浮動小数点数リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_float64_get*** | 64 ビット浮動小数点数リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_boolean_get*** | ブール値リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_objlnk_get*** | オブジェクト リンク リソースの値を取得します。 |
| ***nx_lwm2m_client_resource_opaque_get*** | 不透明なリソースの値を取得します。 |
| ***nx_lwm2m_client_resource_instance_get*** | 複数のリソースのリソース インスタンスを取得します。 |
| ***nx_lwm2m_client_resource_dim_get*** | 複数のリソースのリソース ディメンションを取得します。 |

## <a name="object-implementation"></a>オブジェクトの実装

LWM2M クライアントによって、必須の OMA LWM2M オブジェクトが実装されます: セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)。 その他のデバイス固有のオブジェクトは、アプリケーションによって実装される必要があります。

オブジェクトを定義するには、2 つのデータ構造体を使用します。NX_LWM2M_CLIENT_OBJECT 構造体は、オブジェクト ID とオブジェクト メソッドを含むオブジェクトの実装を定義し、NX_LWM2M_CLIENT_OBJECT_INSTANCE 構造体はオブジェクト インスタンスのデータを含んでいます。

次の関数が提供されています。

| 関数&nbsp;名 | 説明 |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | オブジェクトの実装を LwM2M クライアントに追加します。 |
| ***nx_lwm2m_client_object_remove*** | オブジェクトの実装を LwM2M クライアントから削除します。 |
| ***nx_lwm2m_client_object_instance_add*** | オブジェクト インスタンスをオブジェクトに追加します。 |
| ***nx_lwm2m_client_object_instance_remove*** | オブジェクト インスタンスをオブジェクトから削除します。 |

オブジェクト メソッドのコールバック関数には、次に示すシグネチャがあります。

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>"Read" メソッド

"Read" メソッドは、オブジェクト インスタンスからリソース値を読み取るために使用されます。 パラメーターは次のように定義します。

| パラメーター | 説明 |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | オブジェクトの実装へのポインター。 |
| **instance_ptr** | オブジェクト インスタンスへのポインター。 |
| **resource** | 読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。 返されると、配列には対応する型と値が格納されます。 |
| **resource_count** | 読み取るリソースの数へのポインター。 |
| **args_ptr** | 読み取り用の未使用のパラメーターです。 |
| **args_length** | 読み取り用の未使用のパラメーターです。 |

### <a name="the-discover-method"></a>"Discover" メソッド

"Discover" メソッドは、オブジェクトによって実装されているすべてのリソースのリスト取得するために使用されます。 パラメーターは次のように定義します。

| パラメーター | 説明 |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | オブジェクトの実装へのポインター。 |
| **instance_ptr** | オブジェクト インスタンスへのポインター。 |
| **resource** | NX_LWM2M_CLIENT_RESOURCE の配列へのポインター。 返されると、配列には対応するリソース情報が格納されます。 |
| **resource_count** | 検出するリソースの数へのポインター。 戻り時には、このパラメーターを true 値として更新する必要があります。 |
| **args_ptr** | 検出用の未使用のパラメーターです。 |
| **args_length** | 検出用の未使用のパラメーターです。 |

### <a name="the-write-method"></a>"Write" メソッド

"Write" メソッドは、オブジェクト インスタンスのリソースを更新または置換するために使用されます。 パラメーターは次のように定義します。

| パラメーター  | 説明 |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | オブジェクトの実装へのポインター。 |
| **instance_ptr** | オブジェクト インスタンスへのポインター。 |
| **resource** | 読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。 返されると、配列には対応する型と値が格納されます。 |
| **resource_count** | 検出するリソースの数へのポインター。 |
| **args_ptr** | 書き込みフラグ。 |
| **args_length** | 引数の長さ。 |

次の書き込み操作を *flag* パラメーターに対して指定できます。

| Operation | アクション | 説明 |
| --- | ---| --- |
| 0 | 部分更新 | 新しい値で提供されるリソースを追加または更新し、他の既存のリソースを変更せずにそのままにします。
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | インスタンスの置換 | オブジェクト インスタンスを、提供された新しいリソース値に置き換えます。
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  リソースの置換 | リソースを、提供された新しいリソース値に置き換えます (複数のリソースを置き換えるために使用されます)。 |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Create Instance]\(基本モード: インスタンスの作成\) | 指定されたリソース値を使用して、新しく作成されたオブジェクト インスタンスを初期化します (**_nx_lwm2m_object_create_** メソッドから呼び出されます)。 |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | ブートストラップ書き込み | ブートストラップ シーケンス中に呼び出されます。 |

### <a name="the-execute-method"></a>"Execute" メソッド

"Execute" メソッドは、オブジェクト リソースの実行を実装します。

入力パラメーターは次のように定義します。

| パラメーター  | 説明 |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | オブジェクトの実装へのポインター。 |
| **instance_ptr** | オブジェクト インスタンスへのポインター。 |
| **resource** | 読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。 返されると、配列には対応する型と値が格納されます。 |
| **resource_count** | 検出するリソースの数へのポインター。 |
| **args_ptr** | 引数へのポインター。 |
| **args_length** | 引数の長さ。  |

関数は、リソース ID が存在しない場合は **NX_LWM2M_CLIENT_NOT_FOUND** を返し、実行をサポートしていない場合は **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** を返す必要があります。

### <a name="the-create-method"></a>"Create" メソッド

"Create" メソッドは、新しいオブジェクト インスタンスの作成を実装します。

入力パラメーターは次のように定義します。

| パラメーター  | 説明 |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | オブジェクトの実装へのポインター。 |
| **instance_ptr** | 未使用のパラメーター。 |
| **resource** | 読み取るリソースの ID が格納されている **NX_LWM2M_CLIENT_RESOURCE** の配列へのポインター。 返されると、配列には対応する型と値が格納されます。 |
| **resource_count** | 検出するリソースの数へのポインター。 |
| **args_ptr** | オブジェクト インスタンス ID。 |
| **args_length** | 引数の長さ。 |

### <a name="the-delete-method"></a>"Delete" メソッド

"Delete" メソッドは、オブジェクト インスタンスの削除を実装します。入力パラメーターは次のように定義されています。

| パラメーター  | 説明 |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | オブジェクトの実装へのポインター。 |
| **instance_ptr** | オブジェクト インスタンスへのポインター。 |
| **resource** | 未使用のパラメーター。 |
| **resource_count** | 未使用のパラメーター。 |
| **args_ptr** | 未使用のパラメーター。 |
| **args_length** | 未使用のパラメーター。 |

成功した場合、オブジェクトはオブジェクト インスタンスのデータおよびインスタンスによって割り当てられたその他のリソースを解放する必要があります。

## <a name="example-of-lwm2m-client-application"></a>LWM2M クライアント アプリケーションの例

次のコードは、温度センサーとライト スイッチで構成されるカスタム デバイスを実装する単純な LWM2M クライアント アプリケーションの例です。

このデバイスを使用すると、サーバーは、温度センサーの値とライト スイッチのブール値を読み取り、ライトスイッチのオン/オフに設定できます。

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```