---
title: 章 3 章 - HTTP サービスの説明
description: この章では、すべての NetX Web HTTP サービス (以下に記載) をアルファベット順で説明します。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f7d711a67b6e129b87dc08bfd54857ffc4bc3d26c34001fe336d2b673fc53752
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801735"
---
# <a name="chapter-3---description-of-http-services"></a>章 3 章 - HTTP サービスの説明

この章では、すべての NetX Web HTTP サービス (以下に記載) をアルファベット順で説明します。

> [!NOTE]
> 次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

## <a name="http-and-https-client-api"></a>HTTP および HTTPS Client の API

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

カスタム要求のために HTTP Server へのプレーンテキスト ソケットを開く

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、HTTP Server に対してプレーンテキストの TCP ソケットが開かれますが、要求は送信されません。 要求は、*nx_web_http_client_request_initialize()* を使用して作成され、*nx_web_http_client_request_send()* を使用して送信されます。 カスタム HTTP ヘッダーを要求に追加するには、*nx_web_http_client_request_header_add()* を使用します。

このサービスを使用すると、アプリケーションで任意の数のカスタム ヘッダーを要求に追加できます。 **これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。**

> [!NOTE]
> nx_web_http_client_*_start メソッドは、利便性のために用意されており (*nx_web_http_client_get_start*() など)、要求の生成とソケットの接続が処理されます。 要求にカスタム HTTP ヘッダーが不要な場合は、*nx_web_http_client_connect()* や関連するルーチンの代わりに、これらのサービスを使用できます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **server_ip** リモート HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート (HTTP の場合は 80 など)。
- **wait_option** 基になるネットワーク操作をサービスで待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TCP ソケットが正常に接続されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_WEB_HTTP_NOT_READY (0x3000A) 別の要求が既に進行中です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

HTTP Client インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスに HTTP Client インスタンスが作成されます。 このクライアント インスタンスは、HTTP または HTTPS のいずれかに使用できます。 HTTP または HTTPS インスタンスの開始の詳細については、サービス *nx_web_http_client_connect()* および *nx_web_http_client_secure_connect()* を参照してください。 また、GET、PUT、POST メソッドの単純な呼び出しについては、*nx_web_http_client_get_**、*nx_web_http_client_put_**、*nx_web_http_client_post_** の API を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **client_name** HTTP クライアント インスタンスの名前。
- **ip_ptr** IP インスタンスへのポインター。
- **pool_ptr** 既定のパケット プールへのポインター。 このプール内のパケットはペイロードが応答ヘッダー全体を処理するのに十分な大きさである必要があることに注意してください。 これは *nx_web_http_client.h* の *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* によって定義されます。
- **window_size** クライアントの TCP ソケット受信ウィンドウのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP クライアントが正常に作成されました
- NX_PTR_ERROR (0x16) HTTP、ip_ptr、またはパケット プール ポインターが無効です
- NX_WEB_HTTP_POOL_ERROR (0x30009) パケット プールのペイロードのサイズが無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

HTTP Client インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された HTTP クライアント インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP クライアントが正常に削除されました
- NX_PTR_ERROR (0x16) HTTP ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

プレーンテキストの HTTP DELETE 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。 このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

この API は非推奨です。 開発者には、*nx_web_http_client_delete_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

プレーンテキストの HTTP DELETE 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。 このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_delete_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

暗号化された HTTPS DELETE 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。 このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_delete_secure_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。 リソースは NULL 終端である必要があります。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

暗号化された HTTPS DELETE 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースに対する DELETE 要求の送信が試みられます。 このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、サーバーの応答を取得できます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_delete_secure_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。 リソースは NULL 終端である必要があります。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の DELETE 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

プレーンテキストの HTTP GET 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_get_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

プレーンテキストの HTTP GET 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_get_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

暗号化された HTTPS GET 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_get_secure_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

暗号化された HTTPS GET 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、以前に作成された HTTP Client インスタンスで "resource" ポインターによって指定されたリソースを GET することが試みられます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_secure_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の GET 開始メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

プレーンテキストの HTTP HEAD 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。 このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、応答を取得できます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_head_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

プレーンテキストの HTTP HEAD 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。 このルーチンによって NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、応答を取得できます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_head_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

暗号化された HTTPS HEAD 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、要求されたリソース コンテンツに対応するサーバーの応答を取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_head_secure_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

暗号化された HTTPS HEAD 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、以前に作成された HTTP Client インスタンス上の "リソース" ポインターによって指定されたリソースの HEAD メタデータの取得が試みられます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションでは *nx_web_http_client_response_body_get()* を呼び出して、要求されたリソース コンテンツに対応するサーバーの応答を取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で GET 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_head_secure_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server のポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client の HEAD 要求メッセージが正常に送信されました
- **NX_WEB_HTTP_ERROR** (0x30000) 内部 HTTP Client エラー
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Server との通信で HTTP Client エラーが発生しました。
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

HTTP(S) パケットを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、クライアントの HTTP(S) にパケットを割り当てることが試みられます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **packet_ptr** 割り当てられるパケットへのポインター。
- **wait_option** パケット プールに使用可能なパケットがない場合の待機時間をティックで定義します。 この待機オプションは次のように定義します。
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **タイムアウト (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットが正常に割り当てられました
- **NX_NO_PACKET** (0x01) 使用可能なパケットがありません
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。
- **NX_INVALID_PARAMETERS** (0x4D) プロトコルをサポートできないパケット サイズです。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

HTTP POST 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する POST 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_post_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** サーバーに送信するリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) POST 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

HTTP POST 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する POST 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_post_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) POST 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

暗号化された HTTPS POST 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する POST 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_post_secure_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** サーバーに送信するリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) POST 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_post_secure_start_extended

暗号化された HTTPS POST 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する POST 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_post_secure_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) POST 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

HTTP PUT 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する PUT 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_put_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** サーバーに送信するリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) PUT 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_put_start_extended

HTTP PUT 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは、**プレーンテキスト** の HTTP 用です。

このサービスでは、指定された IP アドレスとポートの HTTP Server への、指定されたリソースに対する PUT 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_put_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) PUT 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

暗号化された HTTPS PUT 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する PUT 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_put_secure_start_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** サーバーに送信するリソースの URL 文字列へのポインター。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **password** 省略可能な認証用のパスワードへのポインター。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) PUT 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

暗号化された HTTPS PUT 要求を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、指定された IP アドレスとポートの HTTPS Server への、指定されたリソースに対する PUT 要求の送信が試みられます。 このルーチンが正常に終了した場合、アプリケーション コードで *nx_web_http_client_put_packet()* ルーチンを連続して呼び出し、リソースのコンテンツを HTTP Server に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください ("/index.htm" など)。また、HTTP Server で PUT 要求の参照がサポートされていることが示されている場合は、別の URL を参照することもできます (`http://abc.website.com/index.htm` など)。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_put_secure_start*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **ip_address** HTTP Server の IP アドレス。
- **server_port** リモート HTTP Server 上の TCP ポート。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_web_http_client_put_packet()* の呼び出しを介して送信されるすべてのパケットの合計長が、この値と等しくなる必要があることに注意してください。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) PUT 要求が正常に送信されました
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) ユーザー名がバッファーに対して大きすぎます
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

次のリソース データ パケットを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、PUT 操作と POST 操作でリソース コンテンツの次のパケットを HTTP Server に送信することが試みられます。 このルーチンは、送信されたパケットの合計長が先行する *nx_web_http_client_put_start()* または *nx_web_http_client_post_start()* の呼び出し (または対応するセキュリティで保護されたバージョン) で指定された "total_bytes" と同じになるまで、繰り返し呼び出す必要があることに注意してください。

また、このサービスでは、HTTP (または HTTPS) 接続の確立で問題が発生した場合のために、サーバーからの応答がチェックされます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **packet_ptr** HTTP Server に送信されるリソースの次のコンテンツへのポインター。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client のパケットが正常に送信されました。
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client の準備ができていません
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) サーバー エラー コードを受信しました**
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) パケットの長さが無効です
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 名前またはパスワード (あるいはその両方) が無効です
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) PUT が完了する前にサーバーが応答しました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_INVALID_PACKET (0x12) パケットが TCP ヘッダーに対して小さすぎます
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

HTTP(S) 要求にチャンク転送を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>説明

このサービスでは、リモート ホストへのソケット接続をあらかじめ確立した *nx_web_http_client_connect()* または *nx_web_http_client_secure_connect()* 呼び出しで指定されたサーバーに、チャンク転送コーディングを使用してカスタム HTTP(S) 要求が送信されます。

> [!NOTE]
> アプリケーションでチャンク転送コーディングを使用して要求データ パケットを送信する場合は、*nx_web_http_client_request_packet_allocate*() を呼び出した後にこのサービスを呼び出し、その後、*nx_web_http_client_reqeust_packet_send*() を呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **chunk_size** チャンクデータのサイズ (オクテット単位)。
- **packet_ptr** HTTP(S) 要求データ パケットへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) チャンクが正常に設定されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

カスタム HTTP 要求にカスタム ヘッダーを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>説明

このサービスでは、*nx_web_http_client_request_initialize()* で作成されたカスタム HTTP 要求に (フィールド名と値の形式で) カスタム ヘッダーが追加されます。

このサービスを使用すると、アプリケーションで任意の数のカスタム ヘッダーを要求に追加できます。 **これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。**

> [!NOTE]
> nx_web_http_client_\*_start メソッドは、利便性のために提供されています。 これらのすべての関数では、このルーチンを (*nx_web_http_client_request_initialize()* と共に) 内部で使用し、HTTP 要求を作成して送信します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **field_name** フィールド名の文字列 ("Content-type" など)。
- **name_length** フィールド名文字列の長さ (バイト単位)。
- **field_value** フィールド値の文字列 ("application/octet-stream" など)。
- **value_length** 値の文字列の長さ (バイト単位)。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求にヘッダーが正常に追加されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

カスタム HTTP 要求を初期化する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>説明

このサービスでは、カスタム HTTP 要求が作成され、HTTP Client インスタンスに関連付けられます。 より単純な *nx_web_http_client_get_start()* (および PUT、POST とそれらの API に関連付けられたセキュリティで保護されたバージョンのメソッド) とは異なり、カスタム要求は、*nx_web_http_client_request_send()* サービスが呼び出されるまで送信されません。

このサービスを使用すると、アプリケーションでは、***nx_web_http_client_request_header_add()*** サービスを使用して、要求に任意の数のカスタム ヘッダーを追加できます。 これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。

> [!NOTE]
> nx_web_http_client_\*_start メソッドは、利便性のために提供されています。 これらのすべての関数では、このルーチンを (*nx_web_http_client_request_send()* と共に) 内部で使用し、HTTP 要求を作成して送信します。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_client_request_initialize_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **method** 使用する HTTP 要求メソッド。 オプションは次のように定義されています。
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource** 転送されるリソースの名前。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **input_size** PUT および POST の入力データのサイズ。 他の操作の場合は 0 を渡します。
- **transfer_encoding_trunked** 将来のトランク転送のサポートのために予約されているパラメーター。
- **username** 保護されたリソースのユーザー名。
- **password** 保護されたリソースのパスワード。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求が正常に初期化されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_WEB_HTTP_METHOD_ERROR (0x30014) 一部の必須の情報がありませんでした (PUT または POST の input_size など)。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

カスタム HTTP 要求を初期化する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a>説明

このサービスでは、カスタム HTTP 要求が作成され、HTTP Client インスタンスに関連付けられます。 より単純な *nx_web_http_client_get_start()* (および PUT、POST とそれらの API に関連付けられたセキュリティで保護されたバージョンのメソッド) とは異なり、カスタム要求は、*nx_web_http_client_request_send()* サービスが呼び出されるまで送信されません。

このサービスを使用すると、アプリケーションでは、***nx_web_http_client_request_header_add()*** サービスを使用して、要求に任意の数のカスタム ヘッダーを追加できます。 これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。

> [!NOTE]
> nx_web_http_client_\*_start メソッドは、利便性のために提供されています。 これらのすべての関数では、このルーチンを (*nx_web_http_client_request_send()* と共に) 内部で使用し、HTTP 要求を作成して送信します。

resource、host、username、password の文字列は NULL 終端である必要があり、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_client_request_initialize*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **method** 使用する HTTP 要求メソッド。 オプションは次のように定義されています。
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource** 転送されるリソースの名前。
- **resource_length** 要求されたリソースの文字列の長さ。
- **host** サーバーのドメイン名の Null 終端の文字列。 この文字列は、HTTP ホスト ヘッダー フィールドで送信されます。 ホスト文字列を NULL にすることはできません。
- **host_length** ホストの文字列の長さ。
- **input_size** PUT および POST の入力データのサイズ。 他の操作の場合は 0 を渡します。
- **transfer_encoding_trunked** 将来のトランク転送のサポートのために予約されているパラメーター。
- **username** 省略可能な認証用のユーザー名へのポインター。
- **username_length** 認証用のユーザー名の文字列の長さ。
- **password** 省略可能な認証用のパスワードへのポインター。
- **password_length** 認証用のパスワードの文字列の長さ。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求が正常に初期化されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_WEB_HTTP_METHOD_ERROR (0x30014) 一部の必須の情報がありませんでした (PUT または POST の input_size など)。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

HTTP(S) 要求データ パケットをリモート サーバーに送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、リモート ホストへのソケット接続をあらかじめ確立した *nx_web_http_client_connect()* または *nx_web_http_client_secure_connect()* 呼び出しで指定されたサーバーに、*nx_web_http_client_request_packet_allocate*() で作成されたカスタム HTTP(S) 要求データ パケットが送信されます。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **packet_ptr** HTTP(S) 要求データ パケットへのポインター。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求データ パケットが正常に送信されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

カスタム HTTP 要求を送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>説明

このサービスでは、リモート ホストへのソケット接続をあらかじめ確立した *nx_web_http_client_connect()* または *nx_web_http_client_secure_connect()* で指定されたサーバーに、*nx_web_http_client_request_initialize*() で作成されたカスタム HTTP 要求が送信されます。

このサービスを使用すると、アプリケーションでは、***nx_web_http_client_request_header_add()*** サービスを使用して、要求に任意の数のカスタム ヘッダーを追加できます。 これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。

> [!NOTE]
> nx_web_http_client_\*_start メソッドは、利便性のために提供されています。 これらのすべての関数では、このルーチンを (*nx_web_http_client_request_initialize()* と共に) 内部で使用し、HTTP 要求を作成して送信します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求が正常に送信されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

次のリソース データ パケットを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>説明

このサービスにより、前に要求されたリソースのコンテンツの次のパケットが取得されます。 NX_WEB_HTTP_GET_DONE という戻りステータスを受け取るまで、このルーチンを連続して呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **packet_ptr** 部分的なリソース コンテンツを含むパケット ポインターの宛先。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Client パケットが正常に取得されました。
- **NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client のパケット取得が完了しました
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client が GET モードではありません。
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) パケットの長さが無効です
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP 状態コード 100 - 継続
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP 状態コード 101 - プロトコルの切り替え
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP 状態コード 201 - 作成
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP 状態コード 202 - 受理
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP 状態コード 203 - 信頼できない情報
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP 状態コード 204 - 内容なし
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP 状態コード 205 - 内容のリセット
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP 状態コード 206 - 部分的内容
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP 状態コード 300 - 複数の選択
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP 状態コード 301 - 恒久的に移動
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP 状態コード 302 - 発見
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP 状態コード 303 - 他を参照せよ
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP 状態コード 304 - 未更新
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP 状態コード 305 - プロキシを使用せよ
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP 状態コード 307 - 一時的リダイレクト
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP 状態コード 400 - 不正な要求
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP 状態コード 401 - 認証が必要
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP 状態コード 402 - 支払いが必要
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP 状態コード 403 - 拒否
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP 状態コード 404 - 未検出
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP 状態コード 405 - 未許可のメソッド
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP 状態コード 406 - 受理不可
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP 状態コード 407 - プロキシ認証が必要
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP 状態コード 408 - タイムアウト
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP 状態コード 409 - 競合
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP 状態コード 410 - 消滅
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP 状態コード 411 - 長さが必要
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP 状態コード 412 - 前提条件が失敗
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP 状態コード 413 - リクエスト エンティティが膨大
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP 状態コード 414 - 要求 URL が長すぎる
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP 状態コード 415 - サポートされていないメディア タイプ
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP 状態コード 416 - 要求したレンジが範囲外
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP 状態コード 417 - Expect ヘッダーによる拡張が失敗
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP 状態コード 500 - 内部サーバー エラー
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP 状態コード 501 - 実装されていない
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP 状態コード 502 - 不正なゲートウェイ
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP 状態コード 503 - サービス利用不可
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP 状態コード 504 - ゲートウェイ タイムアウト
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP 状態コード 505 - サポートされていない HTTP バージョン
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

HTTP ヘッダーが処理されるときに呼び出されるコールバックを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>説明

このサービスでは、リモート HTTP Server からの受信応答の HTTP ヘッダーが NetX Web HTTP Client で処理されるたびに呼び出されるコールバックが割り当てられます。 このコールバックは、応答が処理されるときに応答の各ヘッダーに対して 1 回ずつ呼び出されます。 このコールバックを使用すると、HTTP Client アプリケーションでは HTTP Server の応答の各ヘッダーにアクセスし、NetX Web HTTP Client によって行われる基本的な処理以外の必要なアクションを実行できます。

### <a name="input-parameters"></a>入力パラメーター

**client_ptr** HTTP Client の制御ブロックへのポインター。

**callback_function** 応答ヘッダーの処理中に呼び出すコールバック。 このコールバックは、フィールドの名前と値の文字列 (およびその長さ) を使用して呼び出されます。 たとえば、ヘッダー "Content-Length: 100" を指定すると、*field_name* に "Content-Length"、*field_value* に文字列 "100" が指定されて関数が呼び出されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に割り当てられました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

カスタム要求のために HTTPS Server への TLS セッションを開く

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>説明

このメソッドは **TLS で保護された** HTTPS 用です。

このサービスでは、HTTPS Server へのセキュリティで保護された TLS セッションが開かれますが、要求は送信されません。 要求は、*nx_web_http_client_request_initialize()* を使用して作成され、*nx_web_http_client_request_send()* を使用して送信されます。 カスタム HTTP ヘッダーを要求に追加するには、*nx_web_http_client_request_header_add()* を使用します。

このサービスを使用すると、アプリケーションで任意の数のカスタム ヘッダーを要求に追加できます。 **これにより、特定のアプリケーション用にカスタマイズされた HTTP 要求を作成できます。**

> [!NOTE]
> nx_web_http_client_\*_start メソッドは、利便性のために提供されています。 これらのすべての関数では、このルーチンを (*nx_web_http_client_request_initialize()* と共に) 内部で使用し、HTTP 要求を作成して送信します。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **server_ip** リモート HTTPS Server の IP アドレス。
- **server_port** リモート HTTPS Server のポート (HTTPS の場合は 443 など)。
- **tls_setup** TLS 構成を設定するために使用されるコールバック。 アプリケーションでは、このコールバックを定義して TLS の暗号化と資格情報 (証明書など) を初期化します。
- **wait_option** サービスで HTTP Client の GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義します。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TLS セッションが正常に接続されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_WEB_HTTP_NOT_READY (0x3000A) 別の要求が既に進行中です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>HTTP および HTTPS Server の API

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

URL の最大有効期間と日付を取得するコールバックを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>説明

このサービスは、指定されたリソースの最大有効期間と最終更新日を取得するために呼び出されるコールバック サービスを設定します。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **cache_info_get** コールバックへのポインター
- **max_age** リソースの最大有効期間へのポインター
- **data** 返された最終更新日へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- **NX_PTR_ERROR** (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

初期化

### <a name="example"></a>例

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

コールバック関数からデータを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>説明

このサービスは、アプリケーションのコールバック ルーチンから、指定されたパケット内のデータを送信します。 これは通常、GET または POST 要求に関連付けられた動的データを送信するために使用されます。 この関数を使用する場合、応答全体を適切な形式で送信するのはコールバック ルーチンの責任であることに注意してください。 また、コールバック ルーチンによって NX_WEB_HTTP_CALLBACK_COMPLETED という状態が返される必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **data_ptr** 送信するデータへのポインター。
- **data_length** 送信するバイト数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバー データが正常に送信されました
- **NX_PTR_ERROR** (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

コールバック関数で応答ヘッダーを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>説明

このサービスは、HTTP 応答ヘッダーを生成するために、HTTP(S) サーバー コールバック ルーチン (アプリケーションで定義します) で使用されます。 サーバー コールバック ルーチンは、HTTP 応答を必要とするクライアントの GET、PUT、DELETE 要求に対して HTTP Server が応答するときに呼び出されます。 この関数では、アプリケーションから応答情報を受け取り、適切な応答ヘッダーが生成されます。 サーバー要求コールバック ルーチンの詳細については、サービス *nx_web_http_server_create()* を参照してください。

この API は非推奨です。 開発者には、*nx_web_http_server_callback_generate_response_header_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター
- **status_code** リソースの状態を示します。 次に例を示します。
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** コンテンツのサイズ (バイト単位)
- **content_type** HTTP の種類 ("text/plain" など)
- **additional_header** 追加のヘッダー テキストへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTML ヘッダーが正常に作成されました
- **NX_PTR_ERROR** (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

コールバック関数で応答ヘッダーを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>説明

このサービスは、HTTP 応答ヘッダーを生成するために、HTTP(S) サーバー コールバック ルーチン (アプリケーションで定義します) で使用されます。 サーバー コールバック ルーチンは、HTTP 応答を必要とするクライアントの GET、PUT、DELETE 要求に対して HTTP Server が応答するときに呼び出されます。 この関数では、アプリケーションから応答情報を受け取り、適切な応答ヘッダーが生成されます。 サーバー要求コールバック ルーチンの詳細については、サービス *nx_web_http_server_create()* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター
- **status_code** リソースの状態を示します。 次に例を示します。
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** 状態コードの文字列の長さ
- **content_length** コンテンツのサイズ (バイト単位)
- **content_type** HTTP の種類 ("text/plain" など)
- **content_type_length** コンテンツの種類の文字列の長さ
- **additional_header** 追加のヘッダー テキストへのポインター
- **additional_header_length** 追加のヘッダー テキストの長さ

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTML ヘッダーが正常に作成されました
- **NX_PTR_ERROR** (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

コールバック関数から HTTP パケットを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>説明

このサービスでは、HTTP コールバックから完全な HTTP Server の応答が送信されます。 HTTP Server では、NX_WEB_HTTP_SERVER _TIMEOUT_SEND を使用してパケットが送信されます。 HTTP のヘッダーとデータをパケットに追加する必要があります。 戻りステータスがエラーを示している場合、HTTP アプリケーションでパケットを解放する必要があります。

このコールバックによって NX_WEB_HTTP_CALLBACK_COMPLETED が返される必要があります。

詳細な例については、*nx_web_http_server_callback_generate_response_header()* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター
- **packet_ptr** 送信するパケットへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server のパケットが正常に送信されました
- **NX_PTR_ERROR** (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

コールバック関数から応答を送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>説明

このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。 通常、これは GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。 この関数を使用する場合、コールバック ルーチンによって NX_WEB_HTTP_CALLBACK_COMPLETED という状態が返される必要がある点に注意してください。

このサービスは推奨されなくなりました。 開発者には、*nx_web_http_server_callback_response_send_extended()* を使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **header** 応答ヘッダー文字列へのポインター。
- **information** 情報の文字列へのポインター。
- **additional_info** 追加の情報の文字列へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server の応答が正常に送信されました

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

コールバック関数から応答を送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>説明

このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。 通常、これは GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。 この関数を使用する場合、コールバック ルーチンによって NX_WEB_HTTP_CALLBACK_COMPLETED という状態が返される必要がある点に注意してください。

header、information、additional_info の文字列は NULL 終端で、各文字列の長さは引数リストで指定された長さと一致している必要があります。

このサービスによって *nx_web_http_server_callback_response_send*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **header** 応答ヘッダー文字列へのポインター。
- **header_length** 応答ヘッダー文字列の長さ。
- **information** 情報の文字列へのポインター。
- **information_length** 情報の文字列の長さ。
- **additional_info** 追加の情報の文字列へのポインター。
- **additional_info_length** 追加の情報文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server の応答が正常に送信されました

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

要求からコンテンツを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>説明

このサービスでは、POST または PUT の HTTP Client 要求から指定された量のコンテンツを取得することが試みられます。 これは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。
- **byte_offset** コンテンツ領域にオフセットするバイト数。
- **destination_ptr** コンテンツのコピー先領域へのポインター。
- **destination_size** コピー先領域の使用可能な最大バイト数。
- **actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server のコンテンツが正常に取得されました
- **NX_WEB_HTTP_ERROR** (0x30000) HTTP Server の内部エラー
- **NX_WEB_HTTP_DATA_END** (0x30007) 要求コンテンツの終わり
- **NX_WEB_HTTP_TIMEOUT** (0x30001) コンテンツの次のパケットを取得しているときに HTTP Server がタイムアウトになりました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

要求からコンテンツを取得する (長さゼロのコンテンツの長さがサポートされます)

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>説明

このサービスは *nx_web_http_server_content_get()* とほぼ同じで、POST または PUT の HTTP Client 要求から指定された量のコンテンツを取得することが試みられます。 ただし、コンテンツの長さがゼロ値の要求 ("空の要求") が有効な要求として処理されます。 これは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

このサービスによって *nx_web_http_server_content_get*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。
- **byte_offset** コンテンツ領域にオフセットするバイト数。
- **destination_ptr** コンテンツのコピー先領域へのポインター。
- **destination_size** コピー先領域の使用可能な最大バイト数。
- **actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP コンテンツが正常に取得されました
- **NX_WEB_HTTP_ERROR** (0x30000) HTTP Server の内部エラー
- **NX_WEB_HTTP_DATA_END** (0x30007) 要求コンテンツの終わり
- **NX_WEB_HTTP_TIMEOUT** (0x30001) 次のパケットを取得しているときに HTTP Server がタイムアウトになりました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

要求のコンテンツの長さを取得する (ゼロ値のコンテンツの長さがサポートされます)

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>説明

このサービスでは、指定されたパケットの HTTP コンテンツの長さの取得が試みられます。 戻り値では正常な完了状態が示され、実際の長さの値が入力ポインター content_length で返されます。 HTTP コンテンツがないか、コンテンツの長さが 0 の場合でも、このルーチンでは正常な完了状態が返され、content_length 入力ポインターは有効な長さ (ゼロ) を指します。 これは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。
- **content_length** Content Length フィールドから取得した値へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server のコンテンツの長さが正常に取得されました
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) HTTP ヘッダーの形式が正しくありません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

HTTP Server インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>説明

このサービスは、専用の ThreadX スレッドのコンテキスト内で実行される HTTP サーバー インスタンスを作成します。 オプションの *authentication_check* および *request_notify* アプリケーション コールバック ルーチンを使用すると、アプリケーション ソフトウェアから HTTP Server の基本的な操作を制御できます。

このサービスは、プレーンテキストの HTTP Server と TLS で保護された HTTPS Server の両方を作成するために使用されます。 TLS を使用して HTTPS を有効にする方法については、サービス *nx_web_http_server_secure_configure()* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **http_server_name** HTTP サーバーの名前へのポインター。
- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **server_port** サーバー インスタンスの TCP リスニング ポート。
- **media_ptr** 以前に作成された FileX メディア インスタンスへのポインター。
- **stack_ptr** HTTP サーバーのスレッド スタック領域へのポインター。
- **stack_size** HTTP サーバーのスレッド スタック サイズへのポインター。
- **authentication_check** アプリケーションの認証確認ルーチンへの関数ポインター。 指定した場合、このルーチンは HTTP クライアント要求ごとに呼び出されます。 このパラメーターが null 値の場合、認証は実行されません。 このパラメーターは非推奨となりました。 代わりに *nx_web_http_server_authenticate_check_set*() を呼び出してください。
- **request_notify** アプリケーションの要求通知ルーチンへの関数ポインター。 指定した場合、このルーチンは要求の HTTP サーバー処理の前に呼び出されます。 これにより、HTTP クライアント要求が完了する前に、リソース名をリダイレクトしたり、リソース内のフィールドを更新したりすることができます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP サーバーが正常に作成されました。
- NX_PTR_ERROR (0x07) HTTP Server、IP、メディア、スタック、またはパケット プール ポインターが無効です。
- NX_WEB_HTTP_POOL_ERROR (0x30009) プールのパケット ペイロードが HTTP 要求全体を格納するのに十分な大きさではありません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

HTTP Server インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された HTTP サーバー インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP サーバーが正常に削除されました
- NX_PTR_ERROR (0x07) HTTP サーバー ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

エンティティ データの場所と長さを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>説明

このサービスでは、受信したクライアント メッセージの現在のマルチパート エンティティ内にあるデータの開始位置と、境界文字列を除いたデータの長さが判別されます。 複数のエンティティを含むメッセージの同じクライアント データグラムに対してこの関数を再度呼び出すことができるように、HTTP Server 自体のオフセットが内部的に更新されます。 クライアント メッセージはマルチパケット データグラムであり、パケット ポインターが次のパケットに更新されます。

このサービスを使用するには NX_WEB_HTTP_MULTIPART_ENABLE を有効にする必要があることに注意してください。 また、packet_pptr が指しているパケットをアプリケーションで解放しないようにしてください。 これは、HTTP Server によって内部的に行われます。

詳細については、*nx_web_http_server_get_entity_header()* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバーへのポインター
- **packet_pptr** パケット ポインターの位置へのポインター。 アプリケーションでこのパケットを解放しないように注意してください
- **available_offset** パケットのプリペンド ポインターからのエンティティ データのオフセットへのポインター
- **available_length** エンティティ データの長さへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) エンティティ コンテンツのサイズと場所が正常に取得されました
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) HTTP Server の内部マルチパート マーカーのコンテンツが既に存在します
- NX_WEB_HTTP_ERROR (0x30000) HTTP Server の内部エラー
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

エンティティ ヘッダーのコンテンツを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>説明

このサービスは、エンティティ ヘッダーを取得して、指定されたバッファーに格納します。 複数のエンティティ ヘッダーを含むクライアント データグラム内の次のマルチパート エンティティを見つけるために、HTTP サーバー自体のポインターが内部的に更新されます。 クライアント メッセージはマルチパケット データグラムであり、パケット ポインターが次のパケットに更新されます。

このサービスを使用するには NX_WEB_HTTP_MULTIPART_ENABLE を有効にする必要があることに注意してください。 また、packet_pptr が指しているパケットをアプリケーションで解放しないようにしてください。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバーへのポインター
- **packet_pptr** パケット ポインターの位置へのポインター。 アプリケーションでこのパケットを解放しないように注意してください
- **entity_header_buffer** エンティティ ヘッダーを格納する場所へのポインター
- **buffer_size** 入力バッファーのサイズ

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) エンティティ ヘッダーが正常に取得されました
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) エンティティ ヘッダー フィールドが見つかりません
- **NX_WEB_HTTP_TIMEOUT** (0x30001) マルチパケット クライアント メッセージの次のパケットの受信期限が切れました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_WEB_HTTP_ERROR (0x30000) 内部 HTTP エラー

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

GMT の日付と時刻を取得するコールバックを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>説明

このサービスは、以前に作成された HTTP サーバーを使用して GMT の日付と時刻を取得するコールバックを設定します。 このサービスは、HTTP サーバーがクライアントに対する HTTP サーバー応答のヘッダーを作成しているときに呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバーへのポインター
- **gmt_get** GMT コールバックへのポインター
- **date** 取得される日付へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) パケットまたはパラメーター ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

無効なユーザー/パスワードを処理するコールバックを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>説明

このサービスは、ダイジェストまたは基本認証のいずれかによって、クライアントの GET、PUT、または DELETE 要求で無効なユーザー名とパスワードを受信したときに呼び出されるコールバックを設定します。 HTTP サーバーを先に作成しておく必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバーへのポインター
- **invalid_username_password_callback** 無効なユーザーまたはパス コールバックへのポインター
- **resource** クライアントによって指定されたリソースへのポインター
- **client_address** クライアント アドレス
- **request_type** クライアント要求の種類を示します。 次を指定できます。
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

HTML 用の追加の MIME マップを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>説明

このサービスを使用すると、HTTP アプリケーション開発者は、NetX Web HTTP Server によって提供される既定の MIME の種類から MIME の種類を追加できます。 定義されている種類の一覧については、*nx_web_http_server_get_type()* を参照してください。

GET 要求などのクライアント要求を受信すると、HTTP Server では、追加の MIME マップ セットを優先的に使用して HTTP ヘッダーから要求されたファイルの種類が解析されます。一致するものが見つからない場合は、HTTP Server の既定の MIME マップの中で一致するものが検索されます。 一致するものが見つからない場合、MIME の種類は既定で "text/plain" になります。

要求通知関数が HTTP Server に登録されている場合、要求通知コールバックから *nx_web_http_server_type_get_extended()* を呼び出して、ファイルの種類を解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバー インスタンスへのポインター
- **mime_maps** MIME マップ配列へのポインター
- **mime_map_num** 配列内の MIME マップの数

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP サーバーの MIME マップが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

HTTP(S) パケットを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、HTTP(S) サーバーにパケットを割り当てることが試みられます。

このパケットを入力として使用する以降の NetX または HTTP Server API (nx_packet_data_append や **nx_web_http_server_callback_packet_send など) が **失敗** した場合、パケットを解放するのはアプリケーションの責任であることに注意してください。 **

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP Server の制御ブロックへのポインター。
- **packet_ptr** 割り当てられるパケットへのポインター。
- **wait_option** パケット プールに使用可能なパケットがない場合の待機時間をティックで定義します。 この待機オプションは次のように定義します。
  - **NX_NO_WAIT** (0x00000000) NX_NO_WAIT を選択すると、要求が履行されない場合、呼び出し元のスレッドによって直ちに制御が戻されます。
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER を選択すると、HTTP Server で要求に対して応答が行われるまで、呼び出し元のスレッドが無期限に一時停止になります。
  - **timeout value** (0x00000001 から 0xFFFFFFFE) 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP Server の応答を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットが正常に割り当てられました
- **NX_NO_PACKET** (0x01) 使用可能なパケットがありません
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が *tx_thread_wait_abort* への呼び出しによって中止されました。
- **NX_INVALID_PARAMETERS** (0x4D) プロトコルをサポートできないパケット サイズです。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

コンテンツの長さを抽出し、データの先頭にポインターを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>説明

このサービスは、HTTP ヘッダーからコンテンツの長さを抽出します。 また、指定されたパケットを次のように更新します。パケットのプリペンド ポインター (書き込み先のパケット バッファーの開始位置) が、HTTP ヘッダーのすぐ先にある HTTP コンテンツ (データ) に設定されます。

コンテンツの先頭が現在のパケット内に見つからない場合、この関数では、NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE 待機オプションを使用して、次のパケットを受信するまで待機します。

これにより、パケットのプリペンド ポインターがエンティティ ヘッダーの先に変更されるため、*nx_web_http_server_get_entity_header()* を呼び出す前に呼び出さないように注意してください。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバー インスタンスへのポインター
- **packet_ptr** 先頭追加ポインターが更新されたパケットを返すためのパケット ポインターへのポインター
- **content_length** 抽出される content_length へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP コンテンツの長さが見つかり、パケットが正常に更新されました
- **NX_WEB_HTTP_TIMEOUT** (0x30001) 次のパケットを待機している間に時間切れになりました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

次の HTTP パケットを受信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>説明

このサービスでは、HTTP Server のソケットで受信された次のパケットが返されます。 パケットを受信する際の待機オプションは NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE です。

正常に実行された場合、パケットを解放するのはアプリケーションの責任であることに注意してください。

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** HTTP サーバー インスタンスへのポインター
- **packet_ptr** 受信したパケットへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 次の HTTP パケットを正常に受信しました
- **NX_WEB_HTTP_TIMEOUT** (0x30001) 次のパケットを待機している間に時間切れになりました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

要求からパラメーターを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>説明

このサービスでは、指定された要求パケット内の指定された HTTP URL パラメーターを取得することが試みられます。 要求された HTTP パラメーターが存在しない場合、このルーチンでは NX_WEB_HTTP_NOT_FOUND という状態が返されます。 このルーチンは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **packet_ptr** HTTP クライアントの要求パケットへのポインター。 アプリケーションでこのパケットを解放しないように注意してください。
- **param_number** パラメーター リストの左から右に向かって 0 から始まるパラメーターの論理番号。
- **param_ptr** パラメーターのコピー先領域。
- **param_size** パラメーター データの合計長 (バイト単位) が返されます。
- **max_param_size** パラメーターのコピー先領域の最大サイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server のパラメーターが正常に取得されました
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) 指定されたパラメーターが見つかりません
- **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) 要求パラメーターが正しく終了されていません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

要求からクエリを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>説明

このサービスでは、指定された要求パケット内の指定された HTTP URL クエリを取得することが試みられます。 要求された HTTP クエリが存在しない場合、このルーチンでは NX_WEB_HTTP_NOT_FOUND という状態が返されます。 このルーチンは、HTTP Server の作成時 (*nx_web_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **packet_ptr** HTTP クライアントの要求パケットへのポインター。 アプリケーションでこのパケットを解放しないように注意してください。
- **query_number** クエリ リストの左から右に向かって 0 から始まるクエリの論理番号。
- **query_ptr** クエリのコピー先領域。
- **query_size** クエリ データのサイズ (バイト単位) が返されます。
- **max_query_size** クエリのコピー先の最大サイズ

できます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server のクエリが正常に取得されました
- **NX_WEB_HTTP_FAILED** (0x30002) クエリのサイズが小さすぎます。
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) 指定されたクエリが見つかりません
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) クライアント要求内にクエリがありません
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

HTTP(S) 応答にチャンク転送を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>説明

このサービスでは、*nx_web_http_server_response_packet_allocate*() で作成されたカスタム HTTP(S) 応答データ パケットが、チャンク転送コーディングを使用してクライアントに送信されます。

> [!NOTE]
> アプリケーションでチャンク転送コーディングを使用して応答データ パケットを送信する場合は、*nx_web_http_server_response_packet_allocate*() を呼び出した後にこのサービスを呼び出し、その後、*nx_web_http_server_callback_packet_send*() を呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **client_ptr** HTTP Client の制御ブロックへのポインター。
- **chunk_size** チャンクデータのサイズ (オクテット単位)。
- **packet_ptr** HTTP(S) 要求データ パケットへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) チャンクが正常に設定されました。
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

HTTPS をセキュリティで保護するために TLS を使用するように HTTP Server を構成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>説明

このサービスでは、セキュリティで保護された HTTPS 通信にするために TLS を使用するように、以前に作成された NetX Web HTTP Server インスタンスが構成されます。 使用されるすべての TLS セッションを同じ状態に構成するためにパラメーターが使用され、各受信 HTTPS Client が一貫した動作で実行されるようになります。 TLS セッションの数は、マクロ NX_WEB_HTTP_SESSION_MAX を使用して制御されます。

暗号化ルーチン テーブル (暗号スイート テーブル) は、関数ポインターが含まれているだけなので、すべての TLS セッション間で共有されます。

メタデータ バッファーとパケット再構築バッファーはそれぞれ、すべての TLS セッション間で均等に分割されます。 バッファー サイズがセッション数で均等に割り切れない場合、残りは使用されません。

渡された ID 証明書は、すべてのセッションで使用されます。 TLS 操作中は、サーバー ID 証明書のみが読み取られるため、セッションごとにコピーは必要ありません。

信頼された証明書は、HTTPS Server の各 TLS セッションに追加されます。 これらは、リモート証明書の領域が提供されている場合に自動的に有効になるクライアント証明書の認証に使用されます。

リモート証明書の配列とバッファーは、既定ですべての TLS セッション間で共有されます。 リモート証明書は、クライアント証明書の認証に使用されます。これは、リモート証明書の数が 0 以外の場合に自動的に有効になります。 バッファーは共有されているため、証明書の検証中に一部のセッションがブロックされることがあります。

クライアント証明書の認証を無効にするには、remote_certificates パラメーターに NX_NULL、remote_certs_num パラメーターに値 0 を渡します。

戻り値には、TLS セッションの構成で発生した問題の結果として得られる TLS エラー コードが含まれています。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP Server インスタンスへのポインター。
- **crypto_table** TLS 暗号スイート テーブルへのポインター。
- **metadata_buffer** 暗号化メタデータ バッファーへのポインター。
- **metadata_size** 暗号化メタデータ バッファーのサイズ。
- **packet_buffer** TLS パケット再構築バッファー。
- **packet_buffer** TLS パケット バッファーのサイズ – (<必要な TLS バッファーのサイズ * NX_WEB_HTTP_SESSION_MAX) と同じである必要があります。
- **identity_certificate** TLS サーバー ID 証明書 – すべての HTTPS Server セッションに使用されます。
- **trusted_certificates** *Remote_certs_num* パラメーターに 0 以外の値を渡すことによってクライアント証明書の認証が有効になっている場合に、受信クライアント証明書を検証するために使用される NX_SECURE_X509_CERT オブジェクトの配列へのポインター。
- **trusted_certs_num** *Trusted_certificates* 配列内の信頼された証明書の数。
- **remote_certificates** 受信クライアント証明書に使用される NX_SECURE_X509_CERT オブジェクトの配列へのポインター。
- **remote_certs_num** リモート証明書の数。 クライアントからの予想される証明書の最大数である必要があります。 この値が 0 以外の場合、クライアント証明書の認証が自動的に有効になります。
- **remote_certificate_buffer** クライアント証明書の認証が有効になっている場合に、クライアントからの受信リモート証明書が格納されるバッファー。 remote_cert_buffer_size リモート証明書のバッファーのサイズ。 (<予想される証明書の最大サイズ \* remote_certs_num) と同じである必要があります。


### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** （0x102） 受信した TLS メッセージの種類が正しくありません。
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** （0x106） リモート ホストによって提供された暗号はサポートされていません。
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS ハンドシェイク中のメッセージの処理に失敗しました。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 受信メッセージのハッシュ MAC チェックに失敗しました。
- **NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) 基になる TCP ソケットの送信に失敗しました。
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 受信メッセージに無効な長さのフィールドがありました。
- **NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) 受信 ChangeCipherSpec メッセージが正しくありませんでした。
- **NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) 受信 TLS 証明書を、リモート TLS サーバーの識別に使用できません。
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) リモート ホストによって提供された公開キー暗号はサポートされていません。
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** （0x10E） リモート ホストは、NetX Secure TLS スタックによってサポートされている暗号スイートがないことを示しています。
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信した TLS メッセージのヘッダーに不明な TLS バージョンがありました。
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** （0x110） 受信した TLS メッセージのヘッダーに既知だがサポートされていない TLS バージョンがありました。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 内部 TLS パケットの割り当てに失敗しました。
- **NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） リモート ホストが無効な証明書を提供しました。
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) リモート ホストによって、エラーを通知して TLS セッションを終了するアラートが送信されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターを使用することが試みられました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

HTTP Server を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された HTTP または HTTPS Server インスタンスが開始されます。

HTTPS Server では、HTTP と同じ API が共有されます。 HTTP Server で TLS を使用して HTTPS を有効にする方法については、サービス *nx_web_http_server_secure_configure()* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server が正常に開始されました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

HTTP Server を停止する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された HTTP サーバー インスタンスを停止します。 このルーチンは、HTTP サーバー インスタンスを削除する前に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) HTTP Server が正常に停止されました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

クライアントの HTTP 要求からファイルの種類を抽出する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>説明

> [!NOTE]
> このサービスは推奨されなくなりました。 ユーザーには、サービス *nx_web_http_server_type_get_extended()* を使用することをお勧めします。

このサービスでは、入力バッファー *name* (通常は URL) から HTTP 要求の種類がバッファー *http_type_string* に、その長さが *string_size* に抽出されます。 MIME マップが見つからない場合、既定では種類に "text/plain" が設定されます。 それ以外の場合、抽出された種類を HTTP Server の既定の MIME マップと比較して、一致するものが見つけられます。 NetX Web HTTP Server の既定の MIME マップは次のとおりです。

- html text/html
- htm text/html
- txt text/plain
- gif image/gif
- jpg image/jpeg
- ico image/x-icon

指定した場合は、ユーザーが定義した一連の追加の MIME マップも検索されます。 ユーザー定義マップの詳細については、*nx_web_http_server_mime_maps_addtional_set()* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP Server インスタンスへのポインター
- **name** 検索するバッファーへのポインター
- **http_type_string** 抽出される HTML の種類の文字列へのポインター
- **string_size** 抽出された HTML の種類の文字列長を返すためのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 種類が正常に抽出されました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 既定の "text/plain" が返されました。

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

クライアントの HTTP 要求からファイルの種類を抽出する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>説明

このサービスでは、入力バッファー *name* (通常は URL) から HTTP 要求の種類がバッファー *http_type_string* に、その長さが *string_size* に抽出されます。 MIME マップが見つからない場合、既定では種類に "text/plain" が設定されます。 それ以外の場合、抽出された種類を HTTP Server の既定の MIME マップと比較して、一致するものが見つけられます。 NetX Web HTTP Server の既定の MIME マップは次のとおりです。

- html text/html
- htm text/html
- txt text/plain
- gif image/gif
- jpg image/jpeg
- ico image/x-icon

指定した場合は、ユーザーが定義した一連の追加の MIME マップも検索されます。 ユーザー定義マップの詳細については、*nx_web_http_server_mime_maps_addtional_set()* を参照してください。

このサービスによって *nx_web_http_server_type_get*() が置き換えられます。 このバージョンでは、呼び出し元で関数に長さの情報を提供する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP Server インスタンスへのポインター
- **name** 検索するバッファーへのポインター
- **name_length** 名前の長さ
- **http_type_string** 抽出される HTML の種類の文字列へのポインター
- **http_type_string_max_size** http_type_string バッファーのサイズ
- **string_size** 抽出される HTML の種類の文字列長を返すための

ポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 種類が正常に抽出されました
- NX_PTR_ERROR: (0x07) ポインターの入力が無効です
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 既定の "text/plain" が返されました。

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

ダイジェスト認証のコールバック関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>説明

このサービスは、ダイジェスト認証の実行時に呼び出されるコールバックを設定します。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP Server インスタンスへのポインター
- **digest_authenticate_callback** ダイジェスト認証コールバックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_NOT_SUPPORTED (0x4B) ダイジェスト認証が有効になっていません

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

ダイジェスト認証のコールバック関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>説明

このサービスでは、認証チェックの実行時に呼び出されるコールバックが設定されます。

### <a name="input-parameters"></a>入力パラメーター

- **http_server_ptr** HTTP Server インスタンスへのポインター
- **authenticate_check_externded** 認証チェックのコールバックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
