---
title: 第 3 章 - Azure RTOS NetX PPPoE サーバー サービスの説明
description: この章では、すべての Azure RTOS NetX PPPoE サーバー サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d184fc3c5e6ed74ef25045561b1613e280672f77385fbb13b8e84bccf051b301
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782813"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>第 3 章 - Azure RTOS NetX PPPoE サーバー サービスの説明

この章では、すべての Azure RTOS NetX PPPoE サーバー サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nx_pppoe_server_create**: "*PPPoE サーバー インスタンスを作成する*"

- **nx_pppoe_server_ac_name_set**: "*アクセス コンセントレーター名を設定する*"

- **nx_pppoe_server_delete**: "*PPPoE サーバー インスタンスを削除する*"

- **nx_pppoe_server_enable**: "*PPPoE サーバー サービスを有効にする*"

- **nx_pppoe_server_disable**: "*PPPoE サーバー サービスを無効にする*"

- **nx_pppoe_server_callback_notify_set**: "*PPPoE サーバーのコールバック通知関数を設定する*"

- **nx_pppoe_server_service_name_set**: "*PPPoE サーバー サービス名を設定する*"

- **nx_pppoe_server_session_send**: "*指定されたセッションに PPPoE サーバー データを送信する*"

- **nx_pppoe_server_session_packet_send**: "*指定されたセッションに PPPoE サーバー パケットを送信する*"

- **nx_pppoe_server_session_terminate**: "*指定された PPPoE セッションを終了する*"

- **nx_pppoe_server_session_get**: "*指定されたセッション情報を取得する*"

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

PPPoE サーバー インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>説明

このサービスでは、指定された NetX IP インスタンスのユーザー指定のリンク ドライバーを使用して、PPPoE サーバー インスタンスを作成します。 リンク ドライバーが初期化されておらず、有効になっていない場合は、PPPoE サーバー ソフトウェアがリンク ドライバーを初期化する役割を担います。

また、PPPoE サーバー インスタンスで内部パケット割り当てに使用できるように、以前に作成されたパケット プールがアプリケーションによって提供される必要があります。

一般に、PPPoE サーバー スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。 IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **name**: この PPPoE サーバー インスタンスの名前。
- **ip_ptr**: IP インスタンスの制御ブロックへのポインター。
- **interface_index**: インターフェイス インデックス。
- **pppoe_link_driver**: ユーザー指定のリンク ドライバー。
- **pool_ptr**: パケット プールへのポインター。
- **stack_ptr**: PPPoE サーバー スレッドのスタック領域の先頭へのポインター。
- **stack_size**: スレッドのスタックのサイズ (バイト単位)。
- **priority**: 内部 PPPoE サーバー スレッドの優先順位 (1 から 31)。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に作成されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー、IP、パケット プール、またはスタック ポインターが無効です。
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) インターフェイスが無効です。
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) パケット プールのペイロード サイズが無効です。
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) メモリ サイズが無効です。
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) PPPoE サーバー スレッドの優先順位が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

PPPoE サーバー インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された PPPoE サーバー インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

PPPoE サーバー サービスを有効にする

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>説明

このサービスは、PPPoE サーバー サービスを有効にします。

> [!NOTE]
> この関数は、*nx_pppoe_server_create* および *nx_pppoe_server_callback_notify_set* の後に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

PPPoE サーバー サービスを無効にする

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>説明

このサービスは、PPPoE サーバー サービスを無効にします。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

PPPoE サーバーのコールバック通知関数を設定する 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>説明

このサービスは、PPPoE サーバーのコールバック通知関数を設定します。

> [!NOTE]
> この関数は *nx_pppoe_server_enable* の前に呼び出す必要があり、pppoe_data_receive_notify 関数ポインターを設定する必要があります。そうしないと、*nx_pppoe_server_enable* は失敗します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **pppoe_discover_initiation_notify**: PPPoE 検出開始メッセージを受信するたびに呼び出されるアプリケーション関数。 この値が NULL の場合、検出開始コールバック関数は無効になります。
- **pppoe_discover_request_notify**: PPPoE 検出要求メッセージを受信するたびに呼び出されるアプリケーション関数。 この値が NULL の場合、検出要求コールバック関数は無効になります。
- **pppoe_discover_terminate_notify**: PPPoE 検出終了メッセージを受信するたびに呼び出されるアプリケーション関数。 この値が NULL の場合、検出終了コールバック関数は無効になります。
- **pppoe_discover_terminate_confirm**: PPPoE 検出終了メッセージを送信するたびに呼び出されるアプリケーション関数。 この値が NULL の場合、検出終了コールバック関数は無効になります。
- **pppoe_data_receive_notify**: PPPoE データ メッセージを受信するたびに呼び出されるアプリケーション関数。 この値を 0 にすることはできません。
- **pppoe_data_send_notify**: PPPoE データ メッセージを送信するたびに呼び出されるアプリケーション関数。 この値が NULL の場合、データ送信コールバック関数は無効になります。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターまたは関数ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

アクセス コンセントレーター名を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>説明

この関数は、アクセス コンセントレーター名関数呼び出しを設定します。

> [!NOTE]
> ac_name の文字列は NULL で終わる必要があり、ac_name の長さは引数リストで指定された長さと一致する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **ac_name**: アクセス コンセントレーター名。
- **ac_name_length**: ac_name の長さ。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に設定されました。
- **NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) PPPoE サーバー、IP、パケット プール、またはスタック ポインターが無効です。
- **NX_SIZE_ERROR**: (0x09) name_length のチェックに失敗しました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

PPPoE サーバー サービス名を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>説明

このサービスは、PPPoE サーバー サービス名を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

指定されたセッションに PPPoE サーバー データを送信する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>説明

このサービスでは、指定されたセッション ID を使用して PPPoE フレームを送信します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **session_index**: セッションのインデックス。
- **data_ptr**: PPPoE サーバー データ フレームの先頭へのポインター。
- **data_length**: PPPoE サーバー データ フレームの長さ。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE サーバー サービスが有効になっていません。
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

指定されたセッションに PPPoE サーバー パケットを送信する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたセッション ID を使用して PPPoE パケットを送信します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **session_index**: セッションのインデックス。
- **packet_ptr**: PPPoE パケットへのポインター。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) PPPoE サーバー パケットが無効です。
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE サーバー サービスが有効になっていません。
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

指定された PPPoE セッションを終了する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>説明

このサービスは、指定された PPPoE セッションを終了します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **session_index**: セッションのインデックス。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE サーバー サービスが有効になっていません。
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

指定された PPPoE セッション情報を取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>説明

このサービスは、指定された PPPoE セッション情報、クライアントの物理アドレス、セッション ID を取得します。

### <a name="input-parameters"></a>入力パラメーター

- **pppoe_server_ptr**: PPPoE サーバー制御ブロックへのポインター。
- **session_index**: セッションのインデックス。
- **client_mac_msw**: クライアントの物理アドレス MSW ポインター。
- **client_mac_lsw**: クライアントの物理アドレス LSW ポインター。
- **session_id**: セッション ID ポインター。

### <a name="return-values"></a>戻り値

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE サーバーが正常に削除されました。
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) PPPoE サーバー ポインターが無効です。
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) PPPoE セッション インデックスが無効です。
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE セッションが確立されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

既定のサービス名を構成する

### <a name="prototype"></a>プロトタイプ

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>説明

受信 PADI 要求をフィルター処理するために PPPoE で使用される "既定のサービス名" を TTP のソフトウェアが構成できるように、PPPoE ソフトウェアはこの関数を公開します。 PPPoE ソフトウェアはこの情報を記憶しておく必要があり、一致するサービス名を含む PADI パケットを受信した場合に、PppDiscoverReq を呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **length**: 既定のサービス名の長さ。
- **aData**: 既定のサービス名。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

PADO パケットの Service Name フィールドを定義する

### <a name="prototype"></a>プロトタイプ

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>説明

PPPoE ソフトウェアは、TTP のソフトウェアが PADO パケットの Service Name フィールドを定義できるように、この関数を公開します。 PPPoE ソフトウェアは、PppDiscoverCnf が呼び出されるまで PADO を送信しないようにする必要があります。

PADO パケットには、PPPoE ソフトウェアの初期化時に定義されたアクセス コンセントレーター名 (RFC 2516 で定義されているタグ ID 0x0102 を使用) が含まれている必要があります。

複数のサービス名を aData に渡すことができます。各名前は null で終了します。

サービス名の一部として他のコマンドを渡す必要がある場合に最大限の柔軟性を提供するために、null 文字は区切り文字として使用されます。

### <a name="input-parameters"></a>入力パラメーター

- **length**: 既定のサービス名の長さ。
- **aData**: 既定のサービス名。
- **interfaceHandle**: インターフェイス ハンドル。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpenCnf

PPPoE セッションを受け入れるか拒否する

### <a name="prototype"></a>プロトタイプ

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>説明

PPPoE ソフトウェアは、TTP のソフトウェアが PPPoE セッションを受け入れるか拒否できるように、この関数を公開します。  これに応じて、PPPoE スタックは接続を受け入れ、interfaceHandle に関連付けられた一意の PPPoE Session_ID 番号を割り当てる必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **accept**: 接続を受け入れる場合は NX_TRUE。
- **interfaceHandle**: インターフェイス ハンドル。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

PPPoE セッションを閉じる

### <a name="prototype"></a>プロトタイプ

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>説明

PPPoE ソフトウェアは、TTP のソフトウェアが PPPoE セッションを閉じることができるように、この関数を公開します。

PPPoE ソフトウェアは、PADT メッセージの Generic-Error タグ (0x0203) に原因コード文字列を示します。

### <a name="input-parameters"></a>入力パラメーター

- **interfaceHandle**: インターフェイス ハンドル。
- **causeCode**: PPPoE サーバーからの接続を閉じる理由に関する情報を送信するための null 終端文字列。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

ハンドルが解放されたことを確認する

### <a name="prototype"></a>プロトタイプ

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>説明

PPPoE ソフトウェアは、ハンドルが解放されたことを TTP のソフトウェアが確認できるように、この関数を公開します。

### <a name="input-parameters"></a>入力パラメーター

- **interfaceHandle**: インターフェイス ハンドル。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

先行する PPP データの受信確認を可能にする

### <a name="prototype"></a>プロトタイプ

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>説明

PPPoE ソフトウェアは、先行する PppTransmitDataReq の受信確認を可能にするために、この関数を公開します。  これは、TTP のソフトウェアが PPPoE から新しい PPP フレームを受け入れる準備ができていることを意味します。

### <a name="input-parameters"></a>入力パラメーター

- **interfaceHandle**: インターフェイス ハンドル。
- **aData**: 受け入れられた PPP データ バッファーへのポインター。
- **Packet_id**: パケット識別子。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

イーサネット経由で送信されたデータを受信する

### <a name="prototype"></a>プロトタイプ

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>説明

PPPoE ソフトウェアは、イーサネット経由で送信されたデータを受信するために、この関数を公開します。

### <a name="input-parameters"></a>入力パラメーター

- **interfaceHandle**: インターフェイス ハンドル。
- **length**: aData のバイト数。
- **aData**: PPP データのフレームを格納するデータ バッファー。

### <a name="return-values"></a>戻り値

**なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```