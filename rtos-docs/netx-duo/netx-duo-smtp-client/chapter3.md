---
title: 3 章 - SMTP クライアント サービスのクライアントの説明
description: この章では、一般的な SMTP クライアント アプリケーションでの使用順に、すべての NetX Duo SMTP クライアント サービス (以下の一覧を参照) について説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bc54e7763c4a3977ef4d760bc92025b1cda792b979d741fc7b82f8f1a3f2901b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797808"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>3 章 - SMTP クライアント サービスのクライアントの説明

この章では、一般的な SMTP クライアント アプリケーションでの使用順に、すべての NetX Duo SMTP クライアント サービス (以下の一覧を参照) について説明します。

> [!NOTE]
> 以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **_NX_DISABLE_ERROR_CHECKING_** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

SMTP クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスに SMTP クライアント インスタンスが作成されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SMTP クライアントの制御ブロックへのポインター。
- **ip_ptr** IP インスタンスへのポインター。
- **packet_pool_ptr** クライアントのパケット プールへのポインター。
- **username** NULL で終了する** 認証用のユーザー名
- **password** NULL で終了する認証用のパスワード
- **from_address** NULL で終了する送信者のアドレス
- **client_domain** NULL で終了するドメイン名
- **authentication_type** クライアント認証の種類。 サポートされる種類は、
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** SMTP サーバーの IP アドレスへのポインター
- **server_port** SMTP サーバーの TCP ポート

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SMTP クライアントが正常に作成されました。 TCP ソケット作成状態
- NX_SMTP_INVALID_PARAM (0xA5) 非ポインター入力が無効です
- NX_IP_ADDRESS_ERROR (0x21) IP アドレスの種類が無効です
- NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

SMTP クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された SMTP クライアント インスタンスが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SMTP クライアント インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に削除されました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

SMTP メール アイテムを作成して送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>説明

このサービスでは、SMTP メール アイテムを作成して送信します。 SMTP クライアントでは、SMTP サーバーとの TCP 接続を確立し、一連の SMTP コマンドを送信します。 エラーが発生しなかった場合は、メール メッセージをサーバーに送信します。 メールが正常に送信されたかどうかに関係なく、TCP 接続を終了し、メール送信の結果を示す状態を返します。 アプリケーションでは、制限なく送信するために、メール メッセージの数に応じてこのサービスを何度でも呼び出すことができます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** SMTP クライアントへのポインター
- **recipient_address** NULL で終了する受信者アドレス。
- **subject** NULL で終了する件名行のテキスト。
- **priority** メールが配信される優先度レベル
- **mail_body** メール メッセージへのポインター
- **mail_body_length** メール メッセージのサイズ

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) メールが正常に送信されました
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP クライアント インスタンスは、SMTP セッションの状態の結果に対して初期化されていません
- NX_PTR_ERROR (0x07) ポインター パラメーターが無効です
- NX_SMTP_INVALID_PARAM (0xA5) 非ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
