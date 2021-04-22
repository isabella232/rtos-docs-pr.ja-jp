---
title: 第 3 章 - Azure RTOS NetX POP3 クライアント サービスの説明
description: この章では、Azure RTOS NetX POP3 エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811477"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a>第 3 章 - Azure RTOS NetX POP3 クライアント サービスの説明

この章では、Azure RTOS NetX POP3 エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- nx_pop3_client_create: *Pop3 クライアント インスタンスを作成する*
- nx_pop3_client_delete: *Pop3 クライアント インスタンスを削除する*
- nx_pop3_client_ mail_item_get: *サーバー maildrop からクライアント メール アイテムを削除する*
- nx_pop3_client_mail_item_get: *特定サイズのメール メッセージを取得する*
- nx_pop3_client_mail_items_get: *maildrop でメール アイテムの数を取得する*
- nx_pop3_client_mail_item_message _get: *特定のメール メッセージをダウンロードする*
- nx_pop3_client_mail_item_size_get: *特定のメール アイテムのサイズを取得する*

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

POP3 クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>説明

このサービスでは、POP3 クライアントのインスタンスを作成し、入力パラメーターを使用してその構成を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: 作成するクライアントへのポインター
- **APOP_authentication**: APOP 認証を有効にする
- **ip_ptr** IP インスタンスへのポインター
- **packet_pool_ptr** クライアントのパケット プールへのポインター
- **server_ip_address**: POP3 サーバーのアドレス
- **server_port**: POP3 サーバー ポート
- **client_name**: クライアント名へのポインター
- **client_password**: クライアント パスワードへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に作成されました
- **status**: NetX および ThreadX サービス呼び出しの完了状態
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です
- NX_POP3_PARAM_ERROR: (0xB1) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

POP3 クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a>説明

このサービスでは、以前に作成された POP3 クライアントを削除します。 このサービスでは、POP3 クライアントのパケット プールは削除されません。 パケット プールを使用しなくなった場合は、デバイス アプリケーションでこのリソースを個別に削除する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: 削除するクライアントへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアントが正常に削除されました
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

指定されたメール アイテムをクライアントの maildrop から削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a>説明

このサービスでは、指定されたメール アイテムをクライアントの maildrop から削除します。 これはメール アイテムのダウンロード後を対象としていますが、クライアントから要求された後にメール アイテムを自動的に削除する POP3 サーバーもあります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **mail_index**: クライアントの maildrop へのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 削除要求が成功しました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

指定されたメール アイテムを取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a>説明

このサービスでは RETR 要求を行って、クライアントの maildrop から、インデックス mail_item で指定されたメール アイテムを取得します。 RETR 要求を行い、サーバーから肯定応答を受信したら、クライアントは *nx_pop3_client_mail_item_message_get* サービスを使用して、メール メッセージのダウンロードを開始できます。 このサービスでは、サーバーの応答から抽出された、要求されたメール アイテムのサイズも提供します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **mail_item**: クライアントの maildrop へのインデックス
- **item_size**: メール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

maildrop 内のメール アイテムの数を取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a>説明

このサービスでは STAT 要求を行って、クライアントの maildrop からメール アイテムの数とメール メッセージ データの合計サイズを取得します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **number_mail_item**: クライアントの maildrop 内のメール数
- **maildrop_total_size**: すべてのメール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました 
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

指定されたメール アイテム メッセージを取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a>説明

このサービスでは、メール アイテム メッセージ、メール メッセージのサイズ、メール メッセージの最後のパケットかどうかを取得します。 `final_packet` が NX_TRUE の場合、`recv_packet_ptr` によってポイントされるパケットは、メール アイテム メッセージの最後のパケットです。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **recv_packet_ptr**: メッセージ データの受信パケット
- **number_mail_item**: クライアントの maildrop 内のメール数
- **maildrop_total_size**: すべてのメール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_CLIENT_INVALID_STATE**: (0xB7) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます。
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

指定されたメール アイテムのサイズを取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a>説明

このサービスでは LIST 要求を行って、指定されたメール アイテムのサイズを取得します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr**: クライアント インスタンスへのポインター
- **mail_item**: クライアントの maildrop へのインデックス
- **size**: メール メッセージのサイズへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
