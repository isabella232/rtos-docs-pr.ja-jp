---
title: 第 1 章 - HTTP と HTTPS の概要
description: この章では、Azure RTOS NetX Duo HTTP/HTTPS for Web モジュールの概要について説明します。
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c784843e4d3f11ee306e866223c0a19bfcba3b85
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811810"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>第 1 章 - HTTP と HTTPS の概要

ハイパーテキスト転送プロトコル (HTTP) は、Web 上でコンテンツを転送するために設計されたプロトコルです。 HTTP は、信頼性の高い伝送制御プロトコル (TCP) サービスを利用してコンテンツ転送機能を実行する単純なプロトコルです。 そのため、HTTP は信頼性の高いコンテンツ転送プロトコルです。 HTTP は、最も使用されているアプリケーション プロトコルの 1 つです。 Web 上のすべての操作で HTTP プロトコルが使用されています。

HTTPS は、HTTP プロトコルのセキュリティで保護されたバージョンです。これは、基盤となる TCP 接続をセキュリティで保護するためにトランスポート層セキュリティ (TLS) を使用して HTTP を実装します。 TLS のセットアップに必要な追加の構成を除き、HTTPS の使用方法は基本的に HTTP と同じです。

## <a name="general-http-requirements"></a>HTTP の一般的な要件

NetX Web HTTP パッケージを正常に機能させるためには、NetX Duo (バージョン 5.10 以降) がインストールされている必要があります。 また、IP インスタンスを作成する必要があり、その同じ IP インスタンスで TCP を有効にする必要があります。 HTTPS をサポートするには、NetX Secure TLS (バージョン 5.11 以降) もインストールする必要があります (次のセクションを参照)。 **第 2 章** の「小規模システムの例」セクションのデモ ファイルでは、この方法が示されています。

NetX Web HTTP パッケージの HTTP Client の部分には、その他の要件はありません。

NetX Web HTTP パッケージの HTTP Server の部分には、いくつかの追加要件があります。 まず、すべてのクライアント HTTP 要求を処理するために、TCP の "*ウェルノウンポート 80*" に完全にアクセスできる必要があります (これは、アプリケーションによって他の有効な TCP ポートに変更される可能性があります)。 また、HTTP Server は、FileX 埋め込みファイル システムで使用するように設計されています。 FileX を使用できない場合、ユーザーは、使用される FileX の部分を自分の環境に移植することができます。 これについては、このガイドの後のセクションで説明します。

## <a name="https-requirements"></a>HTTPS の要件

HTTPS を正常に機能されるために、NetX Web HTTP パッケージでは NetX Duo (バージョン 5.10 以降) と NetX Secure TLS (バージョン 5.11 以降) の両方がインストールされていることが求められます。 また、IP インスタンスを作成する必要があり、TLS で使用するために、その同じ IP インスタンスで TCP を有効にする必要があります。 TLS セッションは、適切な暗号化ルーチンと信頼された CA 証明書を使用して初期化する必要があります。また、TLS ハンドシェイク中にリモート サーバー ホストによって提供される証明書のための領域を割り当てる必要があります。 **第 2 章** の「小さな HTTPS システムの例」セクションのデモ ファイルでは、この方法が示されています。

NetX Web HTTP パッケージの HTTPS Client の部分には、その他の要件はありません。

NetX Web HTTP パッケージの HTTPS Server の部分には、いくつかの追加要件があります。 まず、すべてのクライアント HTTPS 要求を処理するために、TCP の "*ウェルノウンポート 443*" に完全にアクセスできる必要があります (プレーンテキスト HTTP と同様に、このポートはアプリケーションによって変更される可能性があります)。 次に、TLS セッションは、適切な暗号化ルーチンとサーバー ID 証明書 (または事前共有キー) を使用して初期化する必要があります。 また、HTTPS Server は、FileX 埋め込みファイル システムで使用するように設計されています。 FileX を使用できない場合、ユーザーは、使用される FileX の部分を自分の環境に移植することができます。 FileX の使用については、このガイドの後のセクションで説明します。

TLS の構成オプションの詳細については、NetX Secure のドキュメントを参照してください。

このドキュメントで説明されているすべての HTTP 機能は、特に記載のない限り、HTTPS にも適用されます。

## <a name="http-and-https-constraints"></a>HTTP および HTTPS の制約

NetX Web HTTP では、HTTP 1.1 標準が実装されます。 ただし、次の制約があります。

1. 要求パイプライン処理はサポートされません
1. HTTP Server では、基本認証と MD5 ダイジェスト認証の両方がサポートされますが、MD5-sess はサポートされません。 現時点では、HTTP Client では基本認証のみがサポートされます。 HTTPS のために TLS を使用する場合でも、HTTP 認証を使用できます。
1. コンテンツの圧縮はサポートされません。
1. TRACE、OPTIONS、CONNECT 要求はサポートされません。
1. HTTP Server またはクライアントに関連付けられるパケット プールは、完全な HTTP ヘッダーを保持するのに十分な大きさである必要があります。
1. HTTP Client サービスは、コンテンツの転送のみを対象としています。このパッケージでは、表示ユーティリティは提供されません。

## <a name="http-url-resource-names"></a>HTTP の URL (リソース名)

HTTP プロトコルは、Web 上でコンテンツを転送するように設計されています。 要求されるコンテンツは、ユニバーサル リソース ロケーター (URL) によって指定されます。 これは、すべての HTTP 要求の主要なコンポーネントです。 URL は必ず "/" 文字で始まり、通常は HTTP Server 上のファイルに対応しています。 一般的な HTTP ファイルの拡張子を以下に示します。

- **.htm** (または **.html**) ハイパーテキスト マークアップ言語 (HTML)
- **.txt** プレーン ASCII テキスト
- **.gif** バイナリ GIF イメージ
- **.xbm** バイナリ Xbitmap イメージ

## <a name="http-client-requests"></a>HTTP Client の要求

HTTP には、Web コンテンツを要求するための単純なメカニズムがあります。 TCP の "*ウェルノウン ポート 80 (HTTPS の場合はポート 443)* " で接続が正常に確立された後に、クライアントによって発行される標準の一連の HTTP コマンドがあります。 基本的な HTTP コマンドの一部を次に示します。

- **GET *resource* HTTP/1.1** 指定されたリソースを取得します
- **POST *resource* HTTP/1.1** 指定されたリソースを取得し、添付された入力を HTTP Server に渡します
- **HEAD *resource* HTTP/1.1** GET のように扱われますが、コンテンツは HTTP Server によって返されません
- **PUT *resource* HTTP/1.1** HTTP Server にリソースを配置します
- **DELETE *resource* HTTP/1.1** HTTP Server 上のリソースを削除します

これらの ASCII コマンドは、HTTP Server で HTTP 操作を実行するために、Web ブラウザーと NetX Web HTTP Client サービスによって内部的に生成されます。

HTTP Client アプリケーションでは、ポート 80 (HTTPS を使用する場合は、ポート 443) を使用する必要があることに注意してください。 クライアントとサーバーの両方の HTTP API では、パラメーターとしてポートを受け取ります。マクロ NX_WEB_HTTP_SERVER_PORT (ポート 80) と NX_WEB_HTTPS_SERVER_PORT (ポート 443) は、利便性のために定義されています。 HTTP Server のポートは、*nx_web_http_client_set_connect_port()* サービスを使用して実行時に変更することもできます。 このサービスの詳細については、第 4 章を参照してください。

## <a name="http-server-responses"></a>HTTP Server の応答

HTTP Server では、同じ "*ウェルノウン TCP ポート 80 (HTTPS の場合は 443)* " を使用して、クライアント コマンドの応答を送信します。 HTTP Server でクライアント コマンドが処理されると、3 桁の数値のステータス コードを含む ASCII 応答文字列が返されます。 この数値の応答は、操作が成功したかまたは失敗したかを判断するために、HTTP Client ソフトウェアによって使用されます。 クライアント コマンドに対するさまざまな HTTP Server の応答の一覧を次に示します。

- **200** 要求は成功しました
- **400** 要求の形式が正しくありませんでした
- **401** 認可されていない要求。クライアントは認証を送信する必要があります
- **404** 要求に指定されたリソースが見つかりませんでした
- **500** 内部 HTTP Server エラー
- **501** HTTP Server によって要求が実装されていません
- **502** サービスを利用できません

たとえば、ファイル "test.htm" を PUT するクライアント要求が成功すると、"HTTP/1.1 200 OK" というメッセージが返されます。

## <a name="http-communication"></a>HTTP 通信

前述のように、HTTP Server では "*ウェルノウン TCP ポート 80 (HTTPS の場合は 443)* " を使用して、クライアント要求が処理されます。 HTTP Client では、送信接続に使用可能な任意の TCP ポートを使用できます。 HTTP イベントの一般的な順序は次のとおりです。

**HTTP GET 要求**:

1. クライアントによって、サーバー ポート 80 (HTTPS の場合は 443) に対して TCP 接続が発行されます。
1. HTTPS が使用されている場合は、TCP 接続の後に TLS ハンドシェイクが行われ、サーバーが認証されて、セキュリティで保護されたチャネルが確立されます。
1. クライアントによって、"**GET *resource* HTTP/1.1**" 要求が (他のヘッダー情報と共に) 送信されます。
1. サーバーによって、"**HTTP/1.1 200 OK**" メッセージが追加情報とその直後のリソース コンテンツ (存在する場合) と共に作成されます。
1. サーバーがクライアントから切断されます (HTTPS が使用されている場合は、TLS が停止されます)。
1. クライアントがソケットから切断されます (サーバーからの切断アラートの後に、TLS が停止されます)。

**HTTP PUT 要求**:

1. クライアントによって、サーバー ポート 80 (または 443) に対して TCP 接続が発行されます。
1. HTTPS が使用されている場合は、TCP 接続の後に TLS ハンドシェイクが行われ、サーバーが認証されて、セキュリティで保護されたチャネルが確立されます。
1. クライアントでは、"PUT resource HTTP/1.1" 要求を他のヘッダー情報とそれに続くリソース コンテンツと共に送信します。
1. サーバーでは、"HTTP/1.1 200 OK" メッセージを追加情報とその直後に続くリソース コンテンツと共に作成します。
1. サーバーによって切断が実行されます。
1. クライアントによって切断が実行されます。

> [!NOTE]
> 前に説明したように、HTTP Server では、別のポートを使用してクライアントに接続する Web サーバーのために、*nx_web_http_client_set_connect_port()* を使用して実行時に既定の接続ポート (80 または 443) を変更できます。

## <a name="http-authentication"></a>HTTP 認証

HTTP 認証は省略可能であり、すべての Web 要求に必須ではありません。 認証には、"*基本*" と "*ダイジェスト*" の 2 種類があります。 基本認証は、多くのプロトコルで使用されている "*名前*" と "*パスワード*" の認証に相当します。 HTTP 基本認証では、名前とパスワードが連結されて base64 形式でエンコードされます。 基本認証の主な短所は、名前とパスワードが要求でオープンに送信されることです。 これにより、名前とパスワードの傍受がいくらか簡単になります。 ダイジェスト認証では、要求で名前とパスワードを送信しないことによって、この問題に対処しています。 代わりに、アルゴリズムを使用して、名前、パスワード、およびその他の情報から 128 ビットのダイジェストを導出します。 NetX Web HTTP Server では、標準の MD5 ダイジェスト アルゴリズムがサポートされます。

認証はいつ必要になるのでしょうか。 HTTP Server では、要求されたリソースで認証が必要とされるかどうかを判断します。 認証が必要で、クライアント要求に適切な認証が含まれていない場合は、"HTTP/1.1 401 未認可" の応答が必要な認証の種類と共にクライアントに送信されます。 クライアントによって適切な認証を使用した新しい要求が作成されることが予期されます。

HTTPS が使用される場合、HTTPS Server でも HTTP 認証を利用できます。 この場合、TLS を使用してすべての HTTP トラフィックが暗号化されるため、HTTP の "*基本*" 認証を使用してもセキュリティ上のリスクはありません。 "*ダイジェスト*" 認証も使用できますが、TLS 経由の基本認証よりもセキュリティが大幅に向上することはありません。

## <a name="http-authentication-callback"></a>HTTP 認証コールバック

前述のように、HTTP 認証は省略可能であり、すべての Web 転送で必要とされるわけではありません。 また、通常、認証はリソースに依存します。 サーバー上の一部のリソースに対するアクセスでは認証が必要となりますが、他のリソースでは必要ありません。 NetX Web HTTP Server パッケージでは、アプリケーションで、各 HTTP Client 要求の処理の開始時に呼び出される認証コールバック ルーチンを (***nx_web_http_server_create*** 呼び出しを使用して) 指定できます。

このコールバック ルーチンによって、リソースに関連付けられているユーザー名、パスワード、領域の文字列が NetX Web HTTP Server に提供され、必要な認証の種類が返されます。 リソースに対して認証が必要ない場合は、認証コールバックによって **NX_WEB_HTTP_DONT_AUTHENTICATE** が値として返されます。 それ以外の場合で、指定されたリソースに対して基本認証が必要なときは、このルーチンによって **NX_WEB_HTTP_BASIC_AUTHENTICATE** が返されます。 最後に、MD5 ダイジェスト認証が必要な場合は、このコールバック ルーチンによって **NX_WEB_HTTP_DIGEST_AUTHENTICATE** が返されます。 HTTP Server によって提供されるリソースに対して認証が不要な場合、このコールバックは必要ありません。また、HTTP Server の作成呼び出しに NULL ポインターを渡すこともできます。

アプリケーション認証のコールバック ルーチンの形式は非常に単純で、以下のように定義します。

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

入力パラメーターは次のように定義します。

- **request_type** HTTP Client 要求を指定します。有効な要求は次のように定義されています。
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **resource** 要求された特定のリソース。
- **name** 必要なユーザー名へのポインターの宛先。
- **password** 必要なパスワードへのポインターの宛先。
- **realm** この認証の領域へのポインターの宛先。

認証ルーチンの戻り値は、認証が必要かどうかを示します。 認証コールバックルーチンによって **NX_WEB_HTTP_DONT_AUTHENTICATE** が返される場合、name、password、realm のポインターは使用されません。 それ以外の場合、HTTP Server の開発者は、*nx_web_http_server.h* で定義される **NX_WEB_HTTP_MAX_USERNAME** と **NX_WEB_HTTP_MAX_PASSWORD** が、認証コールバックに指定されるユーザー名とパスワードに対して十分な大きさであることを確認する必要があります。 これらの両方の既定のサイズは 20 文字です。

## <a name="http-invalid-usernamepassword-callback"></a>HTTP の無効なユーザー名/パスワードのコールバック

HTTP Server がクライアント要求で無効なユーザー名とパスワードの組み合わせを受け取った場合、NetX Web HTTP Server のオプションの無効なユーザー名/パスワードのコールバックが呼び出されます。 HTTP Server アプリケーションでコールバックを HTTP Server に登録する場合は、基本認証またはダイジェスト認証のいずれかが *nx_web_http_server_get_process()* 、*nx_web_http_server_put_process()* 、または *nx_web_http_server_delete_process()* で失敗したときに呼び出されます。

HTTP Server にコールバックを登録するには、NetX Web HTTP Server に次のサービスを定義します。

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

要求の種類は次のように定義されています。

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP GMT 日付ヘッダー挿入コールバック

NetX Web HTTP Server には、応答メッセージに日付ヘッダーを挿入するためのオプションのコールバックがあります。 このコールバックは、HTTP Server で put または get 要求に応答しているときに呼び出されます。

HTTP Server に GMT 日付コールバックを登録するには、次のサービスを定義します。

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

NX_WEB_HTTP_SERVER_DATE のデータ型は次のように定義します。

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP キャッシュ情報取得コールバック

HTTP Server には、特定のリソースについて HTTP アプリケーションから最大有効期間と日付を要求するためのコールバックがあります。 この情報は、クライアントの Get 要求に応答して、HTTP Server でページ全体を送信するかどうかを判断するために使用されます。 クライアント要求に "if modified since" が見つからないか、キャッシュ取得コールバックによって返された "最終更新日" の日付と一致しない場合は、ページ全体が送信されます。

HTTP Server にコールバックを登録するには、次のサービスを定義します。

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>HTTP チャンク転送コーディングのサポート

送信する前に HTTP メッセージの合計長を判別できない場合は、チャンク転送コーディング機能を使用して、"Content-length" ヘッダー フィールドなしで一連のチャンクとしてメッセージを送信できます。 この機能は、すべての HTTP 要求メッセージと応答メッセージでサポートされます。 受信側では、この機能がサポートされており、チャンク ヘッダーは内部ロジックによって透過的に処理されます。 送信側では、API *nx_web_http_client_request_chunked_set* と *nx_web_http_server_response_chunked_set* がクライアントとサーバーによってそれぞれ呼び出される必要があります。

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

これらのサービスの詳細については、第 3 章「HTTP サービスの説明」を参照してください。

## <a name="http-multipart-support"></a>HTTP マルチパートのサポート

Multipurpose Internet Mail Extensions (MIME) は当初は SMTP プロトコルを対象としていましたが、HTTP でも使用されるようになりました。 MIME を使用すると、同じメッセージ内に混在したメッセージの種類 (image/jpg、text/plain など) を含めることができます。 NetX Web HTTP Server には、クライアントからの MIME を含む HTTP メッセージのコンテンツの種類を判別するサービスがあります。 HTTP マルチパートのサポートを有効にしてこれらのサービスを使用するには、構成オプション **NX_WEB_HTTP_MULTIPART_ENABLE** を定義する必要があります。

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

これらのサービスの使用方法の詳細については、第 3 章「HTTP サービスの説明」を参照してください。

## <a name="http-multi-thread-support"></a>HTTP マルチスレッドのサポート

NetX Web HTTP Client サービスは、複数のスレッドから同時に呼び出すことができます。 ただし、特定の HTTP Client インスタンスの読み取り要求または書き込み要求は、同じスレッドから順番に実行する必要があります。

HTTPS を使用する場合、複数のスレッドから NetX Web HTTP Client サービスを呼び出すことができますが、基になる TLS 機能が複雑になるため、各スレッドには独立した HTTP Client インスタンス (NX_WEB_HTTP_CLIENT 制御構造) が 1 つある必要があります。

## <a name="http-rfcs"></a>HTTP の RFC

NetX Web HTTP は、RFC1945 "ハイパーテキスト転送プロトコル/1.0"、RFC 2616 "ハイパーテキスト転送プロトコル – HTTP/1.1"、RFC 2581 "TCP の輻輳制御"、RFC 1122 "インターネット ホストの要件"、および関連する RFC に準拠しています。

HTTPS の場合、NetX Web HTTP は RFC 2818 "HTTP over TLS" に準拠しています。
