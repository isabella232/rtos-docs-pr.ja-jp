---
title: 第 3 章 - Azure RTOS NetX PPPoE クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX PPPoE クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8310006b7c188fa63402c931459ffd84ebb776c207dc520959208449862fe27f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790209"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>第 3 章 - Azure RTOS NetX PPPoE クライアント サービスの説明

この章では、すべての Azure RTOS NetX PPPoE クライアント サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

- **nx_pppoe_client_create**: "*PPPoE クライアント インスタンスを作成する*"
- **nx_pppoe_client_delete**: "*PPPoE クライアント インスタンスを削除する*"
- **nx_pppoe_client_host_uniq_set**: "*PPPoE クライアントの Host-Uniq を設定する*"
- **nx_pppoe_client_host_uniq_set_extended**: "*PPPoE クライアントの Host-Uniq を設定する*"
- **nx_pppoe_client_service_name_set**: "*PPPoE クライアントのサービス名を設定する*"
- **nx_pppoe_client_service_name_set_extended**: "*PPPoE クライアントのサービス名を設定する*"
- **nx_pppoe_client_session_connect**: "*PPPoE クライアント セッションを PPPoE サーバーに接続する*"
- **nx_pppoe_client_session_packet_send**: "*PPPoE セッション パケットを送信する*"
- **nx_pppoe_client_session_terminate**: "*PPPoE セッションを終了する*"
- **nx_pppoe_client_session_get**: "*指定された PPPoE セッション情報を取得する*"

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

PPPoE クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>説明

このサービスは、指定された NetX IP インスタンスのユーザー指定のリンク ドライバーを使用して、PPPoE クライアント インスタンスを作成します。 リンク ドライバーが初期化されておらず、有効になっていない場合は、PPPoE クライアント ソフトウェアがリンク ドライバーを初期化する役割を担います。

また、アプリケーションでは、PPPoE クライアント インスタンスが内部パケット割り当てに使用するために、以前に作成されたパケット プールを提供する必要があります。

> [!NOTE]
> 一般に、PPPoE クライアント スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。 IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **name**: この PPPoE クライアント インスタンスの名前。
 - **ip_ptr**: IP インスタンスの制御ブロックへのポインター。
 - **interface_index**: インターフェイス インデックス。
 - **pool_ptr**: パケット プールへのポインター。
 - **stack_ptr**: PPPoE クライアント スレッドのスタック領域の先頭へのポインター。
 - **stack_size**: スレッドのスタックのサイズ (バイト単位)。
 - **priority**: 内部 PPPoE クライアント スレッドの優先順位 (1 - 31)。
 - **pppoe_link_driver**: ユーザー指定のリンク ドライバー。
 - **pppoe_packet_receive**: ユーザー指定のパケット受信関数。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントが正常に作成されました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント、IP、パケット プール、またはスタック ポインターが無効です。
 - NX_PPPOE_CLIENT_INVALID_INTERFACE: (0xD2) インターフェイスが無効です。
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR: (0xD3) パケット プールのペイロード サイズが無効です。
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR: (0xD4) メモリ サイズが無効です。
 - NX_PPPOE_CLIENT_PRIORITY_ERROR: (0xD5) PPPoE クライアント スレッドの優先順位が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

PPPoE クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された PPPoE クライアント インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントが正常に削除されました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

PPPoE クライアントの Host-Uniq を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>説明

このサービスは、PPPoE クライアントの Host-Uniq を設定します。 Host-Uniq は、アクセス コンセントレーターを特定のホスト要求に一意に関連付けるためにホストによって使用されます。
これは、ホストが選択した任意の値と長さのバイナリ データになります。

> [!NOTE]
> Host-Uniq は Null 終端文字列である必要があります。

> [!NOTE]
> このサービスは推奨されなくなりました。 開発者は、*nx_pppoe_client_host_uniq_set_extended()* に移行することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **host_uniq**: Host-Uniq へのポインター。 Host-Uniq は Null 終端文字列である必要があります。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントの Host-Uniq が正常に設定されました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

PPPoE クライアントの Host-Uniq を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>説明

このサービスは、PPPoE クライアントの Host-Uniq を設定します。 Host-Uniq は、アクセス コンセントレーターを特定のホスト要求に一意に関連付けるためにホストによって使用されます。
これは、ホストが選択した任意の値と長さのバイナリ データになります。

> [!NOTE]
> Host-Uniq は Null 終端文字列である必要があります。

> [!NOTE]
> このサービスは、*nx_pppoe_client_host_uniq_set()* に代わるものです。 このバージョンでは、長さの情報もサービスに提供されます。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **host_uniq**: Host-Uniq へのポインター。 Host-Uniq は Null 終端文字列である必要があります。
 - **host_uniq_length**: host_uniq の長さ。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアントの Host-Uniq が正常に設定されました。
 - **NX_PPPOE_CLIENT_PTR_ERROR**: (0xD1) PPPoE クライアント ポインターが無効です。
 - **NX_SIZE_ERROR**: (0x09) host_uniq_length のチェックに失敗しました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

PPPoE クライアント サービス名を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>説明

このサービスは、PPPoE クライアント サービス名を設定します。 Service-Name は、ホストが要求しているサービスを示します。 Service-Name が設定されていない場合は、ホストが任意の数のサービスを受け入れることを示します。

> [!NOTE]
> サービス名は Null 終端文字列である必要があります。

> [!NOTE]
> このサービスは推奨されなくなりました。 開発者は、*nx_pppoe_client_service_name_set_extended()* に移行することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **service_name**: サービス名へのポインター。 サービス名は Null 終端文字列である必要があります。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント サービス名が正常に設定されました。
 - **NX_PPPOE_CLIENT_PTR_ERROR**: (0xD1) PPPoE クライアント ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

PPPoE クライアント サービス名を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>説明

このサービスは、PPPoE クライアント サービス名を設定します。 Service-Name は、ホストが要求しているサービスを示します。 Service-Name が設定されていない場合は、ホストが任意の数のサービスを受け入れることを示します。

> [!NOTE]
> サービス名は Null 終端文字列である必要があります。

> [!NOTE]
> このサービスは、*nx_pppoe_client_service_name_set()* に代わるものです。 このバージョンでは、サービス名の長さの情報も関数に提供されます。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **service_name**: サービス名へのポインター。 サービス名は Null 終端文字列である必要があります。
 - **service_name_length**: service_name の長さ。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント サービス名が正常に設定されました。
 - **NX_PPPOE_CLIENT_PTR_ERROR**: (0xD1) PPPoE クライアント ポインターが無効です。
 - **NX_SIZE_ERROR**: (0x09) service_name_length のチェックに失敗しました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

PPPoE クライアント セッションを接続する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、以前に作成された PPPoE クライアントを使用して、指定された PPPoE サーバーへの PPPoE セッション接続を行います。

> [!NOTE]
> この関数は、*nx_pppoe_client_create*、*nx_pppoe_client_host_uniq_set*、*nx_pppoe_client_service_name_set* の後に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **wait_option**: 接続が確立されている間の待機オプション。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント セッションが正常に接続されました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

指定されたセッションに PPPoE クライアント パケットを送信する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたセッション ID を使用して PPPoE パケットを送信します。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **packet_ptr**: PPPoE パケットへのポインター。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント パケットが正常に送信されました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR: (0xD3) PPPoE クライアント パケットが無効です。
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED: (0xD8) PPPoE セッションが確立されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

PPPoE クライアント セッションを終了する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>説明

このサービスは、指定された PPPoE セッションを終了します。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_client_ptr**: PPPoE クライアント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント セッションが正常に終了しました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

指定された PPPoE セッション情報を取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>説明

このサービスは、指定された PPPoE セッション情報、サーバーの物理アドレス、セッション ID を取得します。

### <a name="input-parameters"></a>入力パラメーター

 - **pppoe_server_ptr**: PPPoE クライアント制御ブロックへのポインター。
 - **server_mac_msw**: サーバーの物理アドレス MSW ポインター。
 - **server_mac_lsw**: サーバーの物理アドレス LSW ポインター。
 - **session_id**: セッション ID ポインター。

### <a name="return-values"></a>戻り値

 - **NX_PPPOE_CLIENT_SUCCESS**: (0x00) PPPoE クライアント セッションが正常に取得されました。
 - NX_PPPOE_CLIENT_PTR_ERROR: (0xD1) PPPoE クライアント ポインターが無効です。
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED: (0xD8) PPPoE セッションが確立されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
