---
title: 第 1 章 - Azure RTOS NetX Duo HTTP の概要
description: この章では、Azure RTOS NetX Duo HTTP モジュールの概要について説明します。
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 442149536ac6847808fbba183b96ac78832a82c0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810787"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-http"></a>第 1 章 - Azure RTOS NetX Duo HTTP の概要

ハイパーテキスト転送プロトコル (HTTP) は、Web 上でコンテンツを転送するために設計されたプロトコルです。 HTTP は、信頼性の高い伝送制御プロトコル (TCP) サービスを利用してコンテンツ転送機能を実行する単純なプロトコルです。 そのため、HTTP は信頼性の高いコンテンツ転送プロトコルです。 HTTP は、最も使用されているアプリケーション プロトコルの 1 つです。 Web 上のすべての操作で HTTP プロトコルが使用されています。 Azure RTOS NetX Duo HTTP は、IPv4 と IPv6 両方のネットワークに対応しています。 IPv6 によって HTTP プロトコルが直接変更されることはありませんが、IPv6 に対応するために元の Azure RTOS NetX HTTP API にいくつかの変更が必要となります。これについては、このドキュメントで説明します。

## <a name="http-requirements"></a>HTTP の要件

NetX Duo HTTP パッケージを正常に機能させるためには、NetX Duo (バージョン 5.2 以降) がインストールされている必要があります。 また、IP インスタンスが既に作成されている必要があり、その同じ IP インスタンスで TCP が有効にされている必要があります。 IPv6 ホスト アプリケーションでは、IPv6 API または DHCPv6、あるいはその両方を使用して、リンクローカルおよびグローバル IPv6 アドレスを設定する必要があります。 **第 2 章** の「小規模のシステム例」セクションのデモ ファイルでは、この方法が示されています。

NetX Duo HTTP パッケージの HTTP クライアントの部分には、その他の要件はありません。

NetX Duo HTTP パッケージの HTTP サーバーの部分には、いくつかの追加要件があります。 まず、クライアントのすべての HTTP 要求を処理するために、TCP のウェルノウン ポート 80 への完全なアクセスが必要です。 また、HTTP サーバーは、File 埋め込みファイル システムで使用するように設計されています。 FileX が使用できない場合、ユーザーは、使用されている FileX の一部を自分自身の環境に移植することもできます。 これについては、このガイドの後のセクションで説明します。

## <a name="http-constraints"></a>HTTP に関する制約

NetX Duo HTTP プロトコルには、HTTP 1.0 標準が実装されています。 ただし、次の制約があります。

1.  永続的な接続はサポートされていません
2.  要求パイプライン処理はサポートされません
3.  HTTP サーバーでは、基本認証と MD5 ダイジェスト認証の両方がサポートされますが、MD5-sess はサポートされません。 現時点では、HTTP クライアントでは基本認証のみがサポートされます。
4.  コンテンツの圧縮はサポートされません。
5.  TRACE、OPTIONS、CONNECT 要求はサポートされません。
6.  HTTP サーバーまたはクライアントに関連付けられるパケット プールは、完全な HTTP ヘッダーを保持するのに十分な大きさである必要があります。
7.  HTTP クライアントのサービスは、コンテンツの転送のみを対象としています。このパッケージでは、表示ユーティリティは提供されません。

## <a name="http-url-resource-names"></a>HTTP の URL (リソース名)

HTTP プロトコルは、Web 上でコンテンツを転送するように設計されています。 要求されるコンテンツは、Universal Resource Locator (URL) によって指定されます。 これは、すべての HTTP 要求の主要なコンポーネントです。 URL は必ず *"/"* 文字で始まり、通常は HTTP サーバー上のファイルに対応しています。 一般的な HTTP ファイルの拡張子を以下に示します。

| 拡張子 | 意味 |
| --------- | ------- |
| .htm (または .html) | ハイパーテキスト マークアップ言語 (HTML : Hypertext Markup Language) |
| .txt | プレーン ASCII テキスト |
| .gif | バイナリ GIF 画像 |
| .xbm | バイナリ Xbitmap 画像 |

## <a name="http-client-requests"></a>HTTP クライアントの要求

HTTP には、Web コンテンツを要求するための単純なメカニズムがあります。 基本的には、TCP の "*ウェルノウン ポート 80*" で接続が正常に確立された後に、クライアントによって発行される一連の標準の HTTP コマンドがあります。 基本的な HTTP コマンドの一部を次に示します。

| HTTP コマンド | 意味 |
| ------------ | ------- |
| GET resource HTTP/1.0 | *指定されたリソースを取得します* |
| POST resource HTTP/1.0 | *指定されたリソースを取得し、添付された入力を HTTP サーバーに渡します* |
| HEAD resource HTTP/1.0 | *GET のように扱われますが、コンテンツは HTTP サーバーによって返されません* |
| PUT resource HTTP/1.0 | *HTTP サーバーにリソースを配置します* |
| DELETE resource HTTP/1.0 | *サーバー上のリソースを削除します* |

これらの ASCII コマンドは、HTTP サーバーで HTTP 操作を実行するために、Web ブラウザーと NetX HTTP クライアント サービスによって内部的に生成されます。

> [!NOTE]
> HTTP クライアント アプリケーションの既定の接続ポートは 80 です。 ただし、nx_http_client_set_connect_port サービスを使用して HTTP サーバーへの接続ポートを実行時に変更することができます。 このサービスの詳細については、第 4 章を参照してください。 これは、クライアント接続に代替ポートを使用する場合がある Web サーバーに対応するためのものです。

## <a name="http-server-responses"></a>HTTP サーバーの応答

HTTP サーバーでは、同じ "*ウェルノウン TCP ポート 80*" を使用して、クライアントのコマンドの応答が送信されます。 HTTP サーバーによってクライアントのコマンドが処理された後、3 桁の数値の状態コードを含む ASCII 応答文字列が返されます。 この数値の応答は、操作が成功したかまたは失敗したかを判断するために、HTTP クライアント ソフトウェアによって使用されます。 クライアントのコマンドに対する HTTP サーバーのさまざまな応答の一覧を次に示します。

| 数値フィールド | 意味 |
| ------------- | ------- |
| *200* | *要求は成功しました* |
| *400* |   *要求が正しい形式ではありませんでした* |
| *401* | *承認されていない要求です。クライアントは認証を送信する必要があります* |
| *404* | *要求で指定されたリソースが見つかりませんでした* |
| *500* | *内部 HTTP サーバー エラー* |
| *501* | *HTTP サーバーによって要求が実装されていません* |
| *502* | *サービスを利用できません* |

たとえば、ファイル "test.htm" を PUT するクライアント要求が成功すると、"HTTP/1.0 200 OK" というメッセージが返されます。

## <a name="http-communication"></a>HTTP 通信

前述のとおり、HTTP サーバーによるクライアントの要求の処理には、TCP のウェルノウン ポート 80 が使用されます。 HTTP クライアントでは、使用可能な任意の TCP ポートを使用できます。 HTTP イベントの一般的な順序は次のとおりです。

### <a name="http-get-request"></a>HTTP GET 要求:

1.  クライアントによって、サーバーのポート 80 への TCP 接続が発行されます。
2.  クライアントによって、"**GET resource HTTP/1.0**" 要求が (他のヘッダー情報と共に) 送信されます。
3.  サーバーによって、"**HTTP/1.0 200 OK**" メッセージと追加情報およびその直後のリソース コンテンツ (存在する場合) が作成されます。
4.  サーバーによって切断が実行されます。
5.  クライアントによって切断が実行されます。

### <a name="http-put-request"></a>HTTP PUT 要求:

1.  クライアントによって、サーバーのポート 80 への TCP 接続が発行されます。
2.  クライアントによって、"**PUT resource HTTP/1.0**" 要求、他のヘッダー情報、およびそれに続くリソース コンテンツが送信されます。
3.  サーバーにより、"**HTTP/1.0 200 OK**" メッセージと追加情報およびその直後のリソース コンテンツが作成されます。
4.  サーバーによって切断が実行されます。
5.  クライアントによって切断が実行されます。

> [!NOTE]
>前に説明したように、HTTP クライアントでは、クライアントへの接続に別のポートを使用する Web サーバー用に、*nx_web_http_client_set_connect_port* を使用して、既定の接続ポートを 80 から別のポートに変更できます。

## <a name="http-authentication"></a>HTTP 認証

HTTP 認証は省略可能であり、すべての Web 要求に必須ではありません。 認証には、基本とダイジェストの 2 種類があります。 基本認証は、多くのプロトコルで使用されている名前とパスワードの認証に相当します。 HTTP 基本認証では、名前とパスワードが連結されて base64 形式でエンコードされます。 基本認証の主な短所は、名前とパスワードが要求でオープンに送信されることです。 これにより、名前とパスワードの傍受がいくらか簡単になります。 ダイジェスト認証では、要求で名前とパスワードを送信しないことによって、この問題に対処しています。 代わりに、アルゴリズムを使用して、名前、パスワード、その他の情報から 128 ビットのキーつまりダイジェストが導出されます。 NetX HTTP サーバーは、標準の MD5 ダイジェスト アルゴリズムに対応しています。

認証はいつ必要になるのでしょうか。 基本的に、要求されたリソースに認証が必要かどうかは、HTTP サーバーによって判断されます。 認証が必要で、クライアントの要求に適切な認証が含まれていなかった場合、"HTTP/1.0 401 未承認" という応答と必要な認証の種類が、クライアントに送信されます。 その後、クライアントには、適切な認証を使用した新しい要求を作成することが望まれます。

## <a name="http-authentication-callback"></a>HTTP 認証コールバック

前述のように、HTTP 認証は省略可能であり、すべての Web 転送で必要とされるわけではありません。 また、通常、認証はリソースに依存します。 サーバー上の一部のリソースのアクセスには認証が必要ですが、他のリソースでは必要ありません。 NetX HTTP サーバー パッケージを使用すると、アプリケーションで、各 HTTP クライアント要求の処理の開始時に呼び出される認証コールバック ルーチンを (*nx_http_server_create* 呼び出しを使用して) 指定できます。

このコールバック ルーチンによって、リソースに関連付けられているユーザー名、パスワード、領域の文字列が NetX HTTP サーバーに提供され、必要な認証の種類が返されます。 リソースに認証が必要ない場合は、認証コールバックによって値 **NX_HTTP_DONT_AUTHENTICATE** が返されます。 それ以外の場合で、指定されたリソースに基本認証が必要な場合は、このルーチンから **NX_HTTP_BASIC_AUTHENTICATE** が返されます。 最後に、MD5 ダイジェスト認証が必要な場合は、コールバック ルーチンから **NX_HTTP_DIGEST_AUTHENTICATE** が返されます。 HTTP サーバーによって提供されるリソースに認証が不要な場合、このコールバックは必要なく、HTTP サーバーの作成呼び出しに NULL ポインターを渡すことができます。

アプリケーション認証コールバック ルーチンの形式は非常に単純で、以下のように定義されます。

```c
UINT nx_http_server_authentication_check(NX_HTTP_SERVER *server_ptr,
                                          UINT request_type, CHAR *resource,
                                          CHAR **name, CHAR **password,
                                          CHAR **realm);
```
入力パラメーターは次のように定義されます。

| パラメーター | 意味 |
| --------- | --------|
| *request_type* | HTTP クライアント要求を指定します。有効な要求は次のように定義されています。 <br/> **NX_HTTP_SERVER_GET_REQUEST**<br/>**NX_HTTP_SERVER_POST_REQUEST**<br/>**NX_HTTP_SERVER_HEAD_REQUEST**<br/>**NX_HTTP_SERVER_PUT_REQUEST**<br/>**NX_HTTP_SERVER_DELETE_REQUEST** |
| *resource* | 要求された特定のリソース。 |
| *name* | 必要なユーザー名へのポインターの格納先。 |
| *password* | 必要なパスワードへのポインターの格納先。 |
| *realm* | この認証の領域へのポインターの格納先。 |

認証が必要かどうかは、認証ルーチンの戻り値によって指定されます。 認証コールバック ルーチンによって **NX_HTTP_DONT_AUTHENTICATE** が返される場合、```name, password, and realm``` の各ポインターは使用されません。 それ以外の場合、HTTP サーバーの開発者は、*nxd_http_server.h* で定義されている **NX_HTTP_MAX_USERNAME** と **NX_HTTP_MAX_PASSWORD** が、認証コールバックで指定されるユーザー名とパスワードに十分な大きさであることを確認する必要があります。 どちらも、既定のサイズは 20 文字です。

## <a name="http-invalid-usernamepassword-callback"></a>HTTP の無効なユーザー名とパスワードのコールバック

HTTP サーバーがクライアント要求で無効なユーザー名とパスワードの組み合わせを受け取った場合、NetX HTTP サーバーでオプションの無効なユーザー名とパスワードのコールバックが呼び出されます。 HTTP サーバー アプリケーションによってコールバックが HTTP サーバーに登録されている場合、基本認証またはダイジェスト認証のいずれかが *nx_http_server_get_process*、*nx_http_server_put_process*、または *nx_http_server_delete_process* で失敗すると、それが呼び出されます。

HTTP サーバーにコールバックを登録するため、NetX Duo HTTP サーバーで次のサービスが定義されています。

```c
UINT nx_http_server_invalid_userpassword_notify_set(
                   NX_HTTP_SERVER *http_server_ptr,
                   UINT *invalid_username_password_callback)
                            (CHAR *resource,
                             NXD_ADDRESS *client_nxd_address,
                             UINT request_type))
```

要求の種類は次のように定義されています。
 - **NX_HTTP_SERVER_GET_REQUEST**
 - **NX_HTTP_SERVER_POST_REQUEST**
 - **NX_HTTP_SERVER_HEAD_REQUEST**
 - **NX_HTTP_SERVER_PUT_REQUEST**
 - **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP GMT 日付ヘッダー挿入コールバック

NetX Duo HTTP サーバーには、応答メッセージに日付ヘッダーを挿入するためのオプションのコールバックがあります。 このコールバックは、HTTP サーバーが PUT または GET 要求に応答しているときに呼び出されます

NetX Duo HTTP サーバーには、応答メッセージに日付ヘッダーを挿入するためのオプションのコールバックがあります。 このコールバックは、HTTP サーバーが PUT または GET 要求に応答しているときに呼び出されます

HTTP サーバーに GMT 日付コールバックを登録するため、NetX Duo HTTP サーバーで次のサービスが定義されています。

```c
UINT  _nx_http_server_gmt_callback_set(
                    NX_HTTP_SERVER *server_ptr,
                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date)
```

NX_HTTP_SERVER_DATE のデータ型は次のように定義されています。

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT          nx_http_server_year;           /* Year                 */
    UCHAR           nx_http_server_month;          /* Month                */
    UCHAR           nx_http_server_day;            /* Day                  */
    UCHAR           nx_http_server_hour;           /* Hour              */
    UCHAR           nx_http_server_minute;         /* Minute               */
    UCHAR           nx_http_server_second;         /* Second               */
    UCHAR           nx_http_server_weekday;        /* Weekday              */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP キャッシュ情報取得コールバック

HTTP サーバーには、特定のリソースについて HTTP アプリケーションから最大有効期間と日付を要求するためのコールバックがあります。 この情報は、クライアントの Get 要求に応答して、HTTP サーバーでページ全体を送信するかどうかを判断するために使用されます。 クライアント要求に "if modified since" が見つからないか、キャッシュ取得コールバックによって返された "last modified" の日付と一致しない場合は、ページ全体が送信されます。

HTTP サーバーにコールバックを登録するには、次のサービスを定義します。

```c
UINT  _nx_http_server_cache_info_callback_set(
                              NX_HTTP_SERVER *server_ptr,
                              UINT (*cache_info_get)
                                    (CHAR *, UINT *, NX_HTTP_SERVER_DATE *))
```

## <a name="http-multipart-support"></a>HTTP マルチパートのサポート

Multipurpose Internet Mail Extensions (MIME) は当初は SMTP プロトコルを対象としていましたが、HTTP でも使用されるようになりました。 MIME を使用すると、同じメッセージ内に混在したメッセージの種類 (image/jpg、text/plain など) を含めることができます。 NetX Duo HTTP サーバーには、クライアントからの MIME を含む HTTP メッセージのコンテンツの種類を判別するサービスが追加されています。 HTTP マルチパートのサポートを有効にしてこれらのサービスを使用するには、構成オプション **NX_HTTP_MULTIPART_ENABLE** を定義する必要があります。

```c
UINT  nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       UCHAR *entity_header_buffer,
                                       ULONG buffer_size);

UINT  nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_pptr,
                                        ULONG *available_offset,
                                        ULONG *available_length)
```

これらのサービスの使用方法の詳細については、HTTP サービスの説明に関する第 3 章を参照してください。

## <a name="http-multi-thread-support"></a>HTTP マルチスレッドのサポート

NetX HTTP クライアント サービスは、複数のスレッドから同時に呼び出すことができます。 ただし、特定の HTTP クライアント インスタンスの読み取り要求または書き込み要求は、同じスレッドから順番に実行する必要があります。

## <a name="http-rfcs"></a>HTTP の RFC

NetX HTTP は、RFC1945 "ハイパーテキスト転送プロトコル/1.0"、RFC 2581 "TCP の輻輳制御"、RFC 1122 "インターネット ホストの要件"、および関連する RFC に準拠しています。
