---
title: 第 3 章 - POP3 クライアント サービスの説明
description: この章では、すべての NetX Duo POP3 クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810658"
---
# <a name="chapter-3---description-of-pop3-client-services"></a>第 3 章 - POP3 クライアント サービスの説明

この章では、すべての NetX Duo POP3 クライアント サービス (以下に記載) をアルファベット順に説明します。

> [!NOTE]
> 以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

IPv4 用の POP3 クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>説明

このサービスは、POP3 クライアントのインスタンスを作成します。 IPv4 POP3 サーバー アドレスのみがサポートされています。

デバイス アプリケーションでは、POP3 クライアントがパケットを送信するための IP インスタンスとパケット プールを最初に作成する必要があります。 POP3 クライアント タスク専用のパケット プールを作成するか、IP インスタンスの作成に使用したものと同じパケット プールを使用します。 パケット プールはイーサネット ドライバーのパケット プールと共有することもできますが、これには欠点があります。POP3 クライアントが比較的小さな POP3 メッセージ パケットをサーバーに送信するために、サイズが大きい可能性のあるパケット ペイロードを受信することを目的とした大きなパケット プールを使用することになります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: 作成するクライアントへのポインター
- **APOP_authentication**: APOP 認証を有効にします
- **ip_ptr**: IP インスタンスへのポインター
- **packet_pool_ptr**: クライアントのパケット プールへのポインター
- **server_ip_address**: POP3 サーバーの IPv4 アドレス
- **server_port**: POP3 サーバー ポート
- **client_name**: クライアント名へのポインター
- **client_password**: クライアント パスワードへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
- **status**: NetX Duo および ThreadX サービス呼び出しの完了状態
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
- NX_POP3_PARAM_ERROR: (0xB1) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a>nxd_pop3_client_create

IPv4 または IPv6 用の POP3 クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>説明

このサービスは、POP3 クライアントのインスタンスを作成します。 IPv4 と IPv6 の両方の POP3 サーバー アドレスがサポートされています。 POP3 クライアントの作成プロセスの詳細については、前述の *nx_pop3_client_create* サービスを参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: 作成するクライアントへのポインター
- **APOP_authentication**: APOP 認証を有効にします
- **ip_ptr**: IP インスタンスへのポインター
- **packet_pool_ptr**: クライアントのパケット プールへのポインター
- **server_ip_address**: POP3 サーバーの IPv6 または IPv4 アドレス
- **server_port**: POP3 サーバー ポート
- **client_name**: クライアント名へのポインター
- **client_password**: クライアント パスワードへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
- **status**: NetX Duo および ThreadX サービス呼び出しの完了状態
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
- NX_POP3_PARAM_ERROR: (0xB1) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

POP3 クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された POP3 クライアントを削除します。 このサービスでは、POP3 クライアントのパケット プールは削除されません。 パケット プールを使用しなくなった場合は、デバイス アプリケーションでこのリソースを個別に削除する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: 削除するクライアントへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に削除されました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

指定されたメール アイテムをクライアントのメールドロップから削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a>説明

このサービスは、指定されたメール アイテムをクライアントのメールドロップから削除します。 これはメール アイテムのダウンロード後を対象としていますが、クライアントから要求された後にメール アイテムを自動的に削除する POP3 サーバーもあります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **mail_index**: クライアントのメールドロップへのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 削除要求が成功しました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

指定されたメール アイテムを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a>説明

このサービスは RETR 要求を行って、クライアントのメールドロップから、インデックス mail_item で指定されたメール アイテムを取得します。 RETR 要求を行い、サーバーから肯定応答を受信したら、クライアントは *nx_pop3_client_mail_item_message_get* サービスを使用して、メール メッセージのダウンロードを開始できます。 このサービスは、サーバーの応答から抽出された、要求されたメール アイテムのサイズも提供します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **mail_item**: クライアントのメールドロップへのインデックス
- **item_size**: メール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

メールドロップ内のメール アイテムの数を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a>説明

このサービスは STAT 要求を行って、クライアントのメールドロップからメール アイテムの数とメール メッセージ データの合計サイズを取得します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **number_mail_item**: クライアントのメールドロップ内のメール数
- **maildrop_total_size**: すべてのメール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

指定されたメール アイテム メッセージを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a>説明

このサービスは、メール アイテム メッセージ、メール メッセージのサイズ、メール メッセージの最後のパケットかどうかを取得します。 final_packet が NX_TRUE の場合、recv_packet_ptr が指すパケットは、メール アイテム メッセージの最後のパケットになります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **recv_packet_ptr**: メッセージ データの受信パケット
- **number_mail_item**: クライアントのメールドロップ内のメール数
- **maildrop_total_size**: すべてのメール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_CLIENT_INVALID_STATE**: (0xB7) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

指定されたメール アイテムのサイズを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a>説明

このサービスは LIST 要求を行って、指定されたメール アイテムのサイズを取得します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **mail_item**: クライアントのメールドロップへのインデックス
- **size**: メール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
