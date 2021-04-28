---
title: 第 3 章 - NetX HTTP サービスの説明
description: この章には、すべての NetX HTTP サービス (以下に記載) の説明がアルファベット順で含まれています。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811528"
---
# <a name="chapter-3---description-of-netx-http-services"></a>第 3 章 - NetX HTTP サービスの説明

この章には、すべての NetX HTTP サービス (以下に記載) の説明がアルファベット順で含まれています。

以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

**HTTP クライアントのサービス:**

- nx_http_client_create *HTTP クライアント インスタンスを作成する*
- nx_http_client_delete *HTTP クライアント インスタンスを削除する*
- nx_http_client_get_start *HTTP GET 要求を開始する*
- nx_http_client_get_start_extended *HTTP GET 要求を開始する*
- nx_http_client_get_packet *次のリソース データ パケットを取得する*
- nx_http_client_put_start *HTTP PUT 要求を開始する*
- nx_http_client_put_start_extended *HTTP PUT 要求を開始する*
- nx_http_client_put_packet *次のリソース データ パケットを送信する*
- *nx_http_client_set_connect_port* *HTTP サーバーに接続するポートを変更する*

**HTTP サーバーのサービス:**

- nx_http_server_cache_info_callback_set *指定された URL の有効期間と最終更新日を取得するコールバックを設定する*
- nx_http_server_callback_data_send *コールバック関数から HTTP データを送信する*
- nx_http_server_callback_generate_response_header *コールバック関数内で応答ヘッダーを作成する*
- nx_http_server_callback_generate_response_header_extended *コールバック関数内で応答ヘッダーを作成する*
- nx_http_server_callback_packet_send *HTTP コールバックから HTTP パケットを送信する*
- nx_http_server_callback_response_send *コールバック関数から応答を送信する*
- nx_http_server_callback_response_send_extended *コールバック関数から応答を送信する*
- nx_http_server_content_get *要求からコンテンツを取得する*
- nx_http_server_content_get_extended *要求からコンテンツを取得する (空 (コンテンツの長さがゼロ) の要求がサポートされます)*
- nx_http_server_content_length_get *要求のコンテンツの長さを取得する*
- nx_http_server_content_length_get_extended *要求のコンテンツの長さを取得する (空 (コンテンツの長さがゼロ) の要求がサポートされます)*
- nx_http_server_create *HTTP サーバー インスタンスを作成する*
- nx_http_server_delete *HTTP サーバー インスタンスを削除する*
- nx_http_server_get_entity_content *URL のエンティティ コンテンツのサイズと場所を返す*
- nx_http_server_get_entity_header *指定されたバッファーに URL エンティティ ヘッダーを抽出する*
- nx_http_server_gmt_callback_set *GMT の日付と時刻を取得するコールバックを設定する*
- nx_http_server_invalid_userpassword_notify_set *クライアント要求で無効なユーザー名とパスワードを受信した場合のコールバックを設定する*
- nx_http_server_mime_maps_additional_set *HTML 用の追加の MIME マップを定義する*
- nx_http_server_packet_content_find *HTTP ヘッダーからコンテンツの長さを抽出し、コンテンツ データの先頭にポインターを設定する*
- nx_http_server_packet_get *クライアント パケットを直接受信する*
- nx_http_server_param_get *要求からパラメーターを取得する*
- nx_http_server_query_get *要求からクエリを取得する*
- nx_http_server_start *HTTP サーバーを起動する*
- nx_http_server_stop *HTTP サーバーを停止する*
- nx_http_server_type_get *ヘッダーから HTTP の種類 (text/plain など) を抽出する*
- nx_http_server_type_get_extended *ヘッダーから HTTP の種類 (text/plain など) を抽出する*
- nx_http_server_digest_authenticate_notify_set *ダイジェスト認証コールバック関数を設定する*
- nx_http_server_authentication_check_set *認証確認コールバック関数を設定する*

## <a name="nx_http_client_create"></a>nx_http_client_create

### <a name="create-an-http-client-instance"></a>HTTP クライアント インスタンスを作成する

**プロトタイプ**

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

**説明**

このサービスは、指定された IP インスタンスに HTTP クライアント インスタンスを作成します。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **client_name** HTTP クライアント インスタンスの名前。
- **ip_ptr** IP インスタンスへのポインター。
- **pool_ptr** 既定のパケット プールへのポインター。 このプール内のパケットはペイロードが応答ヘッダー全体を処理するのに十分な大きさである必要があることに注意してください。 これは *nx_http_client.h* 内の NX_HTTP_CLIENT_MIN_PACKET_SIZE によって定義されています。
- **window_size** クライアントの TCP ソケット受信ウィンドウのサイズ。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP クライアントが正常に作成されました
- NX_PTR_ERROR (0x16) HTTP、ip_ptr、またはパケット プール ポインターが無効です
- NX_HTTP_POOL_ERROR (0xE9) パケット プールのペイロード サイズが無効です

**許可元**

初期化、スレッド

**例**

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

### <a name="delete-an-http-client-instance"></a>HTTP クライアント インスタンスを削除する

**プロトタイプ**

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

**説明**

このサービスは、以前に作成された HTTP クライアント インスタンスを削除します。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP クライアントが正常に削除されました
- NX_PTR_ERROR (0x16) HTTP ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

### <a name="start-an-http-get-request"></a>HTTP GET 要求を開始する

**プロトタイプ**

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

**説明**

このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースの取得を試みます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。

このサービスは推奨されなくなりました。 開発者は *nx_http_client_get_start_extended()* に移行することが推奨されます

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **ip_address** HTTP サーバーの IP アドレス。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **input_ptr** GET 要求の追加データへのポインター。 これは省略可能です。 有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。
- **input_size** input_ptr が指す省略可能な追加入力のバイト数。
- **username** 認証用の省略可能なユーザー名へのポインター。
- **password** 認証用の省略可能なパスワードへのポインター。
-**wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義されます。
  - **タイムアウト値** (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。<br />数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP クライアントの GET 開始メッセージが正常に送信されました
- **NX_HTTP_ERROR** (0xE0) 内部 HTTP クライアント エラー
- **NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません
- **NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー。
- **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です。
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

**許可元**

Threads

**例**

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

### <a name="start-an-http-get-request"></a>HTTP GET 要求を開始する

**プロトタイプ**

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

**説明**

このサービスは、以前に作成された HTTP クライアント インスタンス上にある、"resource" ポインターによって指定されたリソースの取得を試みます。 このルーチンから NX_SUCCESS が返された場合、アプリケーションは *nx_http_client_get_packet* の呼び出しを複数回行って、要求されたリソース コンテンツに対応するデータのパケットを取得することができます。

リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の GET 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。

このサービスは *nx_http_client_get_start()* を置き換えます。 呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **ip_address** HTTP サーバーの IP アドレス。
- **resource** 要求されたリソースの URL 文字列へのポインター。
- **resource_length** 要求されたリソースの URL 文字列の長さ。
- **input_ptr** GET 要求の追加データへのポインター。 これは省略可能です。 有効な場合、指定された入力はメッセージのコンテンツ領域に配置され、GET 操作ではなく POST が使用されます。
- **input_size** input_ptr が指す省略可能な追加入力のバイト数。
- **username** 認証用の省略可能なユーザー名へのポインター。
- **username_length** 認証用の省略可能なユーザー名の長さ。
- **password** 認証用の省略可能なパスワードへのポインター。
- **password_length** 認証用の省略可能なパスワードの長さ。
- **wait_option** サービスが HTTP クライアントの GET 開始要求を待機する時間を定義します。 この待機オプションは次のように定義されます。
  - **タイムアウト値** (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。<br />数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP クライアントの GET 開始メッセージが正常に送信されました
- **NX_HTTP_ERROR** (0xE0) 内部 HTTP クライアント エラー
- **NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません
- **NX_HTTP_FAILED** (0xE2) HTTP クライアントと HTTP サーバーとの通信エラー。
- **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です。
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

**許可元**

Threads

**例**
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

### <a name="get-next-resource-data-packet"></a>次のリソース データ パケットを取得する

**プロトタイプ**

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

**説明**

このサービスは、前の *nx_http_client_get_start* 呼び出しによって要求されたリソースのコンテンツの次のパケットを取得します。 NX_HTTP_GET_DONE という戻りステータスを受け取るまで、このルーチンを連続で呼び出す必要があります。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **packet_ptr** 部分的なリソース コンテンツを含むパケット ポインターのコピー先。
- **wait_option** サービスが HTTP クライアントのパケット取得を待機する時間を定義します。 この待機オプションは次のように定義されます。
  - **タイムアウト値** (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。<br />数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP クライアントのパケット取得が正常に完了しました。
- **NX_HTTP_GET_DONE** (0xEC) HTTP クライアントのパケット取得が完了しました
- **NX_HTTP_NOT_READY** (0xEA) HTTP クライアントが GET モードではありません。
- **NX_HTTP_BAD_PACKET_LENGTH** (0xED) パケット長が無効です
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

### <a name="start-an-http-put-request"></a>HTTP PUT 要求を開始する 

**プロトタイプ**

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

**説明**

このサービスは、指定された IP アドレスの HTTP サーバーへの、指定されたリソースに対する PUT 要求の送信を試みます。 このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。

このサービスは推奨されなくなりました。 開発者は *nx_http_client_put_start_extended()* に移行することが推奨されます。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **ip_address** HTTP サーバーの IP アドレス。
- **resource** サーバーに送信するリソースの URL 文字列へのポインター。
- **username** 認証用の省略可能なユーザー名へのポインター。
- **password** 認証用の省略可能なパスワードへのポインター。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。
- **wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。 この待機オプションは次のように定義されます。
  - **タイムアウト値** (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。<br />数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

**戻り値**

- **NX_SUCCESS** (0x00) PUT 要求が正常に送信されました
- **NX_HTTP_USERNAME_TOO_LONG**
- **(0xF1) ユーザー名がバッファーに対して大きすぎます**
- **NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

### <a name="start-an-http-put-request"></a>HTTP PUT 要求を開始する

**プロトタイプ**

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

**説明**

このサービスは、指定された IP アドレスの HTTP サーバーへの、指定されたリソースに対する PUT 要求の送信を試みます。 このルーチンが成功した場合、アプリケーション コードでは *nx_http_client_put_packet* ルーチンを連続で呼び出して、リソースのコンテンツを HTTP サーバーに実際に送信する必要があります。

リソース文字列では、ローカル ファイルを参照できることに注意してください (例: "/index.htm")。また、HTTP サーバーが参照元の PUT 要求をサポートしていることを示している場合、別の URL を参照することもできます (例: `http://abc.website.com/index.htm`)。

このサービスは *nx_http_client_put_start()* を置き換えます。 呼び出し元でリソースの長さ、ユーザー名、およびパスワードを指定する必要があります。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **ip_address** HTTP サーバーの IP アドレス。
- **resource** サーバーに送信するリソースの URL 文字列へのポインター。
- **resource_length** サーバーに送信するリソースの URL 文字列の長さ。
- **username** 認証用の省略可能なユーザー名へのポインター。
- **username_length** 認証用の省略可能なユーザー名の長さ。
- **password** 認証用の省略可能なパスワードへのポインター。
- **password_length** 認証用の省略可能なパスワードの長さ。
- **total_bytes** 送信されるリソースの合計バイト数。 後続の *nx_http_client_put_packet* の呼び出しを介して送信されるすべてのパケットの合計長がこの値と等しくなる必要があることに注意してください。
- **wait_option** サービスが HTTP クライアントの PUT 開始を待機する時間を定義します。 この待機オプションは次のように定義されます。
  - **タイムアウト値** (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。<br />数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

**戻り値**

- **NX_SUCCESS** (0x00) PUT 要求が正常に送信されました
- **NX_HTTP_USERNAME_TOO_LONG** (0xF1) ユーザー名がバッファーに対して大きすぎます
- **NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_SIZE_ERROR (0x09) リソースの合計サイズが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

### <a name="send-next-resource-data-packet"></a>次のリソース データ パケットを送信する

**プロトタイプ**

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

**説明**

このサービスは、HTTP サーバーへの、リソース コンテンツの次のパケットの送信を試みます。 送信されるパケットの合計長が前の *nx_http_client_put_start()* 呼び出しで指定された "total_bytes" と等しくなるまで、このルーチンを繰り返し呼び出す必要があることに注意してください。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **packet_ptr** HTTP サーバーに送信されるリソースの次のコンテンツへのポインター。
- **wait_option** サービスが HTTP クライアントのパケットの PUT を内部的に処理するのを待機する時間を定義します。 この待機オプションは次のように定義されます。
  - **タイムアウト値** (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF)<br />TX_WAIT_FOREVER を選択すると、HTTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。<br /> 数値 (0x1 から 0xFFFFFFFE) を選択すると、HTTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP クライアントのパケットが正常に送信されました。
- **NX_HTTP_NOT_READY** (0xEA) HTTP クライアントの準備ができていません
- **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) サーバー エラー コードを受信しました ** -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) パケット長が無効です
- **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 名前またはパスワードが無効です
- **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) PUT が完了する前にサーバーが応答しました
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_INVALID_PACKET (0x12) パケットが TCP ヘッダーに対して小さすぎます
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

### <a name="set-the-connection-port-to-the-server"></a>サーバーへの接続ポートを設定する

**プロトタイプ**

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

**説明**

このサービスは、実行時に HTTP サーバーに接続する際の接続ポートを指定されたポートに変更します。 それ以外の場合、接続ポートは既定で 80 に設定されます。 これは、*nx_http_client_get_start()* および *nx_http_client_put_start()* (HTTP クライアントがサーバーに接続する場合など) の前に呼び出す必要があります。

**入力パラメーター**

- **client_ptr** HTTP クライアントの制御ブロックへのポインター。
- **port** サーバーに接続するためのポート。

**戻り値**

- **NX_SUCCESS** (0x00) 接続ポートが正常に変更されました
- **NX_INVALID_PORT** (0x46) ポートが最大値 (0xFFFF) を超えているか、0 です。
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

スレッド、初期化

**例**

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a>URL の最大有効期間と日付を取得するコールバックを設定する

**プロトタイプ**

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

**説明**

このサービスは、指定されたリソースの最大有効期間と最終更新日を取得するために呼び出されるコールバック サービスを設定します。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **cache_info_get** コールバックへのポインター
- **max_age** リソースの最大有効期間へのポインター
- **data** 返された最終更新日へのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です

**許可元**

初期化

**例**

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a>nx_http_server_callback_data_send

### <a name="send-data-from-callback-function"></a>コールバック関数からデータを送信する

**プロトタイプ**

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

**説明**

このサービスは、アプリケーションのコールバック ルーチンから、指定されたパケット内のデータを送信します。 これは通常、GET または POST 要求に関連付けられた動的データを送信するために使用されます。 この関数を使用する場合、コールバック ルーチンから応答全体を適切な形式で送信する必要がある点に注意してください。 また、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要があります。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **data_ptr** 送信するデータへのポインター。
- **data_length** 送信するバイト数。

**戻り値**

- **NX_SUCCESS** (0x00) サーバー データが正常に送信されました
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

### <a name="create-a-response-header-in-a-callback-function"></a>コールバック関数内で応答ヘッダーを作成する

**プロトタイプ**

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

**説明**

このサービスは、HTTP サーバーがクライアントの GET、PUT、DELETE 要求に応答するときに、内部関数 *_nx_http_server_generate_response_header* を呼び出します。 これは、HTTP サーバー アプリケーションがクライアントへのその応答を設計しているときに、HTTP サーバーのコールバック関数内で使用するためのものです。

このサービスは推奨されなくなりました。 開発者は *nxd_http_server_callback_generate_response_header_extended()* に移行することが推奨されます。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター
- **status_code** リソースの状態を示します。 次に例を示します。
- **NX_HTTP_STATUS_OK**
- **NX_HTTP_STATUS_MODIFIED**
- **NX_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** コンテンツのサイズ (バイト単位)
- **content_type** HTTP の種類 (例: "text/plain")
- **additional_header** 追加のヘッダー テキストへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) HTML ヘッダーが正常に作成されました
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
            nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

/* Now send the packet! */
   status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
            resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
/* Let HTTP server know the response has been sent. */
   return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a>nx_http_server_callback_generate_response_header_extended

### <a name="create-a-response-header-in-a-callback-function"></a>コールバック関数内で応答ヘッダーを作成する

**プロトタイプ**

```c
UINT nx_http_server_callback_generate_response_header_extended(
     NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr,
     CHAR *status_code, UINT status_code_length,
     UINT content_length,
     CHAR *content_type, UINT content_type_length,
     CHAR *additional_header,
     UINT additional_header_length);
```

**説明**

このサービスは、HTTP サーバーがクライアントの GET、PUT、DELETE 要求に応答するときに、内部関数 *_nx_http_server_generate_response_header()* を呼び出します。 これは、HTTP サーバー アプリケーションがクライアントへのその応答を設計しているときに、HTTP サーバーのコールバック関数内で使用するためのものです。

このサービスは *nx_http_server_callback_generate_response_header()* を置き換えます。 このバージョンでは、コールバック関数に追加の長さの情報が提供されます。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **packet_pptr** メッセージに割り当てられたパケット ポインターへのポインター
- **status_code** リソースの状態を示します。 次に例を示します。
  - **NX_HTTP_STATUS_OK**
  - **NX_HTTP_STATUS_MODIFIED**
  - **NX_HTTP_STATUS_INTERNAL_ERROR**
- **status_code** 状態コードの長さ
- **content_length** コンテンツのサイズ (バイト単位)
- **content_type** HTTP の種類 (例: "text/plain")
- **content_type_length** HTTP の種類の長さ
- **additional_header** 追加のヘッダー テキストへのポインター
- **additional_header_length** 追加のヘッダー テキストの長さ

**戻り値**

- **NX_SUCCESS** (0x00) ヘッダーが正常に作成されました
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
                       nx_http_server_request_resource, temp_string,
                       sizeof(temp_string));

    /* Null terminate the string. */
       temp_string[temp] = 0;

    /* Now build a response header with server status is OK and no additional header
      info. */
      status = nx_http_server_callback_generate_response_header_extended(
               http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
               sizeof(NX_HTTP_STATUS_OK) - 1, length,
               temp_string, string_length, NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
       status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                length, server_ptr ->
                nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
       status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                   resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
    /* Let HTTP server know the response has been sent. */
       return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_packet_send"></a>nx_http_server_callback_packet_send

### <a name="send-an-http-packet-from-callback-function"></a>コールバック関数から HTTP パケットを送信する

**プロトタイプ**

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

**説明**

このサービスは、HTTP コールバックから完全な HTTP サーバー応答を送信します。 HTTP サーバーは、NX_HTTP_SERVER _TIMEOUT_SEND を使用してパケットを送信します。 HTTP ヘッダーとデータをパケットに追加する必要があります。 戻りステータスがエラーを示している場合、HTTP アプリケーションはパケットを解放する必要があります。

このコールバックは NX_HTTP_CALLBACK_COMPLETED を返す必要があります。

詳細な例については、*nx_http_server_callback_generate_response_header()* を参照してください。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター
- **packet_ptr** 送信するパケットへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバー パケットが正常に送信されました
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

### <a name="send-response-from-callback-function"></a>コールバック関数から応答を送信する

**プロトタイプ**

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

**説明**

このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。 これは通常、GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。 この関数を使用する場合、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要がある点に注意してください。

このサービスは推奨されなくなりました。 開発者は *nx_http_server_callback_response_send_extended()* に移行することが推奨されます。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **header** 応答ヘッダー文字列へのポインター。
- **information** 情報文字列へのポインター。
- **additional_info** 追加の情報文字列へのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバー応答が正常に送信されました

**許可元**

Threads

**例**

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
       {

            /* In this example, we will complete the GET processing with
               a resource not found response. */
               nx_http_server_callback_response_send(server_ptr,
                                                    "HTTP/1.0 404 ",
                                                    "NetX HTTP Server unable to find
                                                    file: ", resource);
            /* Return completion status. */
               return(NX_HTTP_CALLBACK_COMPLETED);
        }
        return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a>nx_http_server_callback_response_send_extended

### <a name="send-response-from-callback-function"></a>コールバック関数から応答を送信する

**プロトタイプ**

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

**説明**

このサービスは、アプリケーションのコールバック ルーチンから、指定された応答情報を送信します。 これは通常、GET または POST 要求に関連付けられたカスタム応答を送信するために使用されます。 この関数を使用する場合、コールバック ルーチンは NX_HTTP_CALLBACK_COMPLETED という状態を返す必要がある点に注意してください。

このサービスは *nx_http_server_callback_response_send()* を置き換えます。 このバージョンでは、入力引数として長さの情報を受け取ります。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **header** 応答ヘッダー文字列へのポインター。
- **header_length** 応答ヘッダー文字列の長さ。
- **information** 情報文字列へのポインター。
- **information_length** 情報文字列の長さ。
- **additional_info** 追加の情報文字列へのポインター。
- **additional_info_length** 追加の情報文字列の長さ。

**戻り値**

- **NX_SUCCESS** (0x00) サーバー応答が正常に送信されました

**許可元**

Threads

**例**

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a>nx_http_server_content_get

### <a name="get-content-from-the-request"></a>要求からコンテンツを取得する

**プロトタイプ**

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

**説明**

このサービスは、POST または PUT HTTP クライアント要求から指定された量のコンテンツの取得を試みます。 これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

このサービスは推奨されなくなりました。 開発者は nx_http_server_content_get_extended() に移行することが推奨されます。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。
- **byte_offset** コンテンツ領域にオフセットするバイト数。
- **destination_ptr** コンテンツのコピー先領域へのポインター。
- **destination_size** コピー先領域の使用可能な最大バイト数。
- **actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーのコンテンツが正常に取得されました
- **NX_HTTP_ERROR** (0xE0) HTTP サーバーの内部エラー
- **NX_HTTP_DATA_END** (0xE7) 要求コンテンツの終わり
- **NX_HTTP_TIMEOUT** (0xE1) HTTP サーバーがコンテンツの次のパケットを取得中にタイムアウトになりました
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a>要求からコンテンツを取得する (長さゼロのコンテンツの長さがサポートされます)

**プロトタイプ**

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

**説明**

このサービスは *nx_http_server_content_get()* とほぼ同じで、POST または PUT HTTP クライアント要求から指定された量のコンテンツの取得を試みます。 ただし、コンテンツの長さがゼロ値の要求 ("空の要求") が有効な要求として処理されます。 これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

このサービスは *nx_http_server_content_get()* を置き換えます。 このバージョンでは、呼び出し元が追加の長さの情報を提供する必要があります。

**入力パラメーター**

- **server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。
- **byte_offset** コンテンツ領域にオフセットするバイト数。
- **destination_ptr** コンテンツのコピー先領域へのポインター。
- **destination_size** コピー先領域の使用可能な最大バイト数。
- **actual_size** コピーされるコンテンツの実際のサイズに設定されるコピー先変数へのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP コンテンツが正常に取得されました
- **NX_HTTP_ERROR** (0xE0) HTTP サーバーの内部エラー
- **NX_HTTP_DATA_END** (0xE7) 要求コンテンツの終わり
- **NX_HTTP_TIMEOUT** (0xE1) HTTP サーバーが次のパケットを取得中にタイムアウトになりました
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

### <a name="get-length-of-content-in-the-request"></a>要求のコンテンツの長さを取得する

**プロトタイプ**

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
**説明**

このサービスは、指定されたパケットの HTTP コンテンツの長さの取得を試みます。 HTTP コンテンツがない場合、このルーチンは値 0 を返します。 これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

このサービスは推奨されなくなりました。 開発者は nx_http_server_content_length_get_extended() に移行することが推奨されます。

**入力パラメーター**

- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。

**戻り値**

- **content length** エラーが発生した場合、値 0 が返されます

**許可元**

Threads

**例**

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a>要求のコンテンツの長さを取得する (ゼロ値のコンテンツの長さがサポートされます)

**プロトタイプ**

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

**説明**

このサービスは、*nx_http_server_content_length_get()* に似ており、指定されたパケットの HTTP コンテンツの長さの取得を試行します。 ただし、戻り値は正常完了状態を示し、実際の長さの値が入力ポインター content_length で返されます。 HTTP コンテンツがない、またはコンテンツの長さが 0 の場合でも、このルーチンは正常完了状態を返し、content_length 入力ポインターは有効な長さ (ゼロ) を指します。 これは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

このサービスは *nx_http_server_content_length_get()* を置き換えます。

**入力パラメーター**

- **packet_ptr** HTTP クライアント要求パケットへのポインター。 このパケットは要求通知コールバックで解放してはならないことに注意してください。
- **content_length** Content Length フィールドから取得した値へのポインター

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーのコンテンツが正常に取得されました
- **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) HTTP ヘッダーの形式が正しくありません
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

### <a name="create-an-http-server-instance"></a>HTTP サーバー インスタンスを作成する

**プロトタイプ**

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
     CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
     VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
     UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, CHAR **name,
     CHAR **password, CHAR **realm),
     UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

**説明**

このサービスは、専用の ThreadX スレッドのコンテキスト内で実行される HTTP サーバー インスタンスを作成します。 オプションの *authentication_check* および *request_notify* アプリケーション コールバック ルーチンを使うと、アプリケーション ソフトウェアから HTTP サーバーの基本的な操作を制御できます。

**入力パラメーター**

- **http_server_ptr** HTTP サーバーの制御ブロックへのポインター。
- **http_server_name** HTTP サーバーの名前へのポインター。
- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **media_ptr** 以前に作成された FileX メディア インスタンスへのポインター。
- **stack_ptr** HTTP サーバーのスレッド スタック領域へのポインター。
- **stack_size** HTTP サーバーのスレッド スタック サイズへのポインター。
- **authentication_check** アプリケーションの認証確認ルーチンへの関数ポインター。 指定した場合、このルーチンは HTTP クライアント要求ごとに呼び出されます。 このパラメーターが null 値の場合、認証は実行されません。
- **request_notify** アプリケーションの要求通知ルーチンへの関数ポインター。 指定した場合、このルーチンは要求の HTTP サーバー処理の前に呼び出されます。 これにより、HTTP クライアント要求が完了する前に、リソース名をリダイレクトしたり、リソース内のフィールドを更新したりすることができます。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーが正常に作成されました。
- NX_PTR_ERROR (0x07) HTTP サーバー、IP、メディア、スタック、またはパケット プール ポインターが無効です。
- NX_HTTP_POOL_ERROR (0xE9) プールのパケット ペイロードが HTTP 要求全体を格納するのに十分な大きさではありません。

**許可元**

初期化、スレッド

**例**

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

### <a name="delete-an-http-server-instance"></a>HTTP サーバー インスタンスを削除する

**プロトタイプ**

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

**説明**

このサービスは、以前に作成された HTTP サーバー インスタンスを削除します。

**入力パラメーター**

- **http_server_ptr** HTTP サーバーの制御ブロックへのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーが正常に削除されました
- NX_PTR_ERROR (0x07) HTTP サーバー ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

### <a name="retrieve-the-location-and-length-of-entity-data"></a>エンティティ データの場所と長さを取得する

**プロトタイプ**

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

**説明**

このサービスは、受信したクライアント メッセージの現在のマルチパート エンティティ内にあるデータの開始位置と、境界文字列を除いたデータの長さを特定します。 複数のエンティティを含むメッセージの同じクライアント データグラムに対してこの関数を再度呼び出すことができるように、HTTP サーバー自体のオフセットが内部的に更新されます。 パケット ポインターは、クライアント メッセージがマルチパケット データグラムである次のパケットに更新されます。

このサービスを使用するには NX_HTTP_MULTIPART_ENABLE を有効にする必要がある点に注意してください。

詳細については、*nx_http_server_get_entity_header* を参照してください。

**入力パラメーター**

- **server_ptr** HTTP サーバーへのポインター
- **packet_pptr** パケット ポインターの位置へのポインター。 アプリケーションでこのパケットを解放しないように注意してください。
- **available_offset** パケットの先頭追加ポインターからのエンティティ データのオフセットへのポインター
- **available_length** エンティティ データの長さへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) エンティティ コンテンツのサイズと場所が正常に取得されました
- **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) HTTP サーバーの内部マルチパート マーカーのコンテンツが既に存在します
- NX_HTTP_ERROR (0xE0) HTTP サーバーの内部エラー
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

### <a name="retrieve-the-contents-of-entity-header"></a>エンティティ ヘッダーのコンテンツを取得する

**プロトタイプ**

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

**説明**

このサービスは、エンティティ ヘッダーを取得して、指定されたバッファーに格納します。 複数のエンティティ ヘッダーを含むクライアント データグラム内の次のマルチパート エンティティを見つけるために、HTTP サーバー自体のポインターが内部的に更新されます。 パケット ポインターは、クライアント メッセージがマルチパケット データグラムである次のパケットに更新されます。

このサービスを使用するには NX_HTTP_MULTIPART_ENABLE を有効にする必要がある点に注意してください。

**入力パラメーター**

- **server_ptr** HTTP サーバーへのポインター
- **packet_pptr** パケット ポインターの位置へのポインター。 アプリケーションでこのパケットを解放しないように注意してください。
- **entity_header_buffer** エンティティ ヘッダーを格納する場所へのポインター
- **buffer_size** 入力バッファーのサイズ

**戻り値**

- **NX_SUCCESS** (0x00) エンティティ ヘッダーが正常に取得されました
- **NX_HTTP_NOT_FOUND** (0xE6) エンティティ ヘッダー フィールドが見つかりません
- **NX_HTTP_TIMEOUT** (0xE1) マルチパケット クライアント メッセージの次のパケットの受信期限が切れました 
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_HTTP_ERROR (0xE0) 内部 HTTP エラー

**許可元**

Threads

**例**

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

/* Process multipart data. */
if(request_type == NX_HTTP_SERVER_POST_REQUEST)
{

    /* Get the content header. */
    while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                          sizeof(buffer)) == NX_SUCCESS)
    {

        /* Header obtained successfully. Get the content data location. */
        while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                               &length) == NX_SUCCESS)
        {

            /* Write content data to buffer. */
            nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
            buffer[length] = 0;
        }
    }
    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
             &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a>GMT の日付と時刻を取得するコールバックを設定する

**プロトタイプ**

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

**説明**

このサービスは、以前に作成された HTTP サーバーを使用して GMT の日付と時刻を取得するコールバックを設定します。 このサービスは、HTTP サーバーがクライアントに対する HTTP サーバー応答のヘッダーを作成しているときに呼び出されます。

**入力パラメーター**

- **server_ptr** HTTP サーバーへのポインター
- **gmt_get** GMT コールバックへのポインター
- **date** 取得した日付へのポインター

**戻り値**

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) パケットまたはパラメーター ポインターが無効です。

**許可元**

Threads

**例**

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a>無効なユーザーとパスワードを処理するコールバックを設定する

**プロトタイプ**

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

**説明**

このサービスは、ダイジェストまたは基本認証のいずれかによって、クライアントの GET、PUT、または DELETE 要求で無効なユーザー名とパスワードを受信したときに呼び出されるコールバックを設定します。 HTTP サーバーを先に作成しておく必要があります。

**入力パラメーター**

- **server_ptr** HTTP サーバーへのポインター
- **invalid_username_password_callback** 無効なユーザーまたはパス コールバックへのポインター
- **resource** クライアントによって指定されたリソースへのポインター
- **client_address** クライアント アドレス
- **request_type** クライアント要求の種類を示します。 次を指定できます。
  - NX_HTTP_SERVER_GET_REQUEST
  - NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST
  - NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST

**戻り値**

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

### <a name="set-additional-mime-maps-for-html"></a>HTML 用の追加の MIME マップを設定する 

**プロトタイプ**

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

**説明**

このサービスを使用すると、HTTP アプリケーション開発者は、NetX HTTP サーバーによって提供される既定の MIME の種類から MIME の種類をさらに追加できます (定義済みの種類の一覧については、*nx_http_server_get_type* を参照してください)。

GET 要求などのクライアント要求を受信すると、HTTP サーバーは、追加の MIME マップ セットを優先的に使用して HTTP ヘッダーから要求されたファイルの種類を解析します。一致するものが見つからない場合は、HTTP サーバーの既定の MIME マップの中で一致するものを検索します。 一致するものが見つからない場合、MIME の種類は既定で "text/plain" になります。

要求通知関数が HTTP サーバーに登録されている場合、要求通知コールバックから *nx_http_server_type_get* を呼び出して、ファイルの種類を解析できます。

**入力パラメーター**

- **server_ptr** HTTP サーバー インスタンスへのポインター
- **mime_maps** MIME マップ配列へのポインター
- **mime_map_num** 配列内の MIME マップの数

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーの MIME マップが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

初期化、スレッド

**例**

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a>コンテンツの長さを抽出し、データの先頭にポインターを設定する

**プロトタイプ**

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

**説明**

このサービスは、HTTP ヘッダーからコンテンツの長さを抽出します。 また、指定されたパケットを次のように更新します。パケットの先頭追加ポインター (書き込み先のパケット バッファーの開始位置) が、HTTP ヘッダーのすぐ先にある HTTP コンテンツ (データ) に設定されます。

コンテンツの先頭が現在のパケット内に見つからない場合、この関数では、NX_HTTP_SERVER_TIMEOUT_RECEIVE 待機オプションを使用して、次のパケットを受信するまで待機します。

これは、先頭追加ポインターをエンティティ ヘッダーの先に変更するため、*nx_http_server_get_entity_header()* を呼び出す前に呼び出さないように注意してください。

**入力パラメーター**

- **server_ptr** HTTP サーバー インスタンスへのポインター
- **packet_ptr** 先頭追加ポインターが更新されたパケットを返すためのパケット ポインターへのポインター
- **content_length** 抽出された content_length へのポインター

**戻り値**

- **NX_SUCCESS** (0x00) HTTP コンテンツの長さが見つかり、パケットが正常に更新されました
- **NX_HTTP_TIMEOUT** (0xE1) 次のパケットを待っている間に時間切れになりました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

### <a name="receive-the-next-http-packet"></a>次の HTTP パケットを受信する

**プロトタイプ**

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

**説明**

このサービスは、HTTP サーバー ソケットで受信した次のパケットを返します。 パケットを受信する際の待機オプションは NX_HTTP_SERVER_TIMEOUT_RECEIVE です。

**入力パラメーター**

- **server_ptr** HTTP サーバー インスタンスへのポインター
- **packet_ptr** 受信したパケットへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) 次の HTTP パケットを正常に受信しました
- **NX_HTTP_TIMEOUT** (0xE1) 次のパケットを待っている間に時間切れになりました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

Threads

**例**

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

### <a name="get-parameter-from-the-request"></a>要求からパラメーターを取得する

**プロトタイプ**

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

**説明**

このサービスは、指定された要求パケット内の指定された HTTP URL パラメーターの取得を試みます。 要求された HTTP パラメーターが存在しない場合、このルーチンでは NX_HTTP_NOT_FOUND という状態が返されます。 このルーチンは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

**入力パラメーター**

- **packet_ptr** HTTP クライアントの要求パケットへのポインター。 アプリケーションでこのパケットを解放しないように注意してください。
- **param_number** パラメーター リストの左から右に向かって 0 から始まるパラメーターの論理番号。
- **param_ptr** パラメーターのコピー先領域。
- **max_param_size** パラメーターのコピー先領域の最大サイズ。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーのパラメーターが正常に取得されました
- **NX_HTTP_NOT_FOUND** (0xE6) 指定されたパラメーターが見つかりません
- **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) 要求パラメーターが正しく終了していません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

### <a name="get-query-from-the-request"></a>要求からクエリを取得する

**プロトタイプ**

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

**説明**

このサービスは、指定された要求パケット内の指定された HTTP URL クエリの取得を試みます。 要求された HTTP クエリが存在しない場合、このルーチンでは NX_HTTP_NOT_FOUND という状態が返されます。 このルーチンは、HTTP サーバーの作成時 (*nx_http_server_create()* ) に指定されたアプリケーションの要求通知コールバックから呼び出す必要があります。

**入力パラメーター**

- **packet_ptr** HTTP クライアントの要求パケットへのポインター。 アプリケーションでこのパケットを解放しないように注意してください。
- **query_number** クエリ リストの左から右に向かって 0 から始まるクエリの論理番号。
- **query_ptr** クエリのコピー先領域。
- **max_query_size** クエリのコピー先領域の最大サイズ。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーのクエリが正常に取得されました
- **NX_HTTP_FAILED** (0xE2) クエリのサイズが小さすぎます。
- **NX_HTTP_NOT_FOUND** (0xE6) 指定されたクエリが見つかりません
- **NX_HTTP_NO_QUERY_PARSED** (0xF2) クライアント要求内にクエリがありません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
nx_http_server_start

### <a name="start-the-http-server"></a>HTTP サーバーを起動する

**プロトタイプ**

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

**説明**

このサービスは、以前に作成された HTTP サーバー インスタンスを起動します。

**入力パラメーター**

- **http_server_ptr** HTTP サーバー インスタンスへのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーが正常に起動しました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

初期化、スレッド

**例**

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

### <a name="stop-the-http-server"></a>HTTP サーバーを停止する

**プロトタイプ**

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

**説明**

このサービスは、以前に作成された HTTP サーバー インスタンスを停止します。 このルーチンは、HTTP サーバー インスタンスを削除する前に呼び出す必要があります。

**入力パラメーター**

- **http_server_ptr** HTTP サーバー インスタンスへのポインター。

**戻り値**

- **NX_SUCCESS** (0x00) HTTP サーバーが正常に停止しました
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

**許可元**

Threads

**例**

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

### <a name="extract-file-type-from-client-http-request"></a>クライアントの HTTP 要求からファイルの種類を抽出する

**プロトタイプ**

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

**説明**

このサービスは、*http_type_string* バッファー内の HTTP 要求の種類と、入力バッファー *name* からの戻り値 (通常は URL) 内のその長さを抽出します。 MIME マップが見つからない場合、既定で "text/plain" という種類に設定されます。 それ以外の場合、抽出された種類を HTTP サーバーの既定の MIME マップと比較して、一致するものを探します。 NetX HTTP サーバーの既定の MIME マップは次のとおりです。

- html text/html
- htm text/html
- txt text/plain
- gif image/gif
- jpg image/jpeg
- ico image/x-icon

指定した場合は、追加の MIME マップのユーザー定義セットも検索されます。 ユーザー定義マップの詳細については、*nx_http_server_mime_maps_addtional_set()* を参照してください。

このサービスは推奨されなくなりました。 開発者は *nx_http_server_type_get_extended()* に移行することが推奨されます。

**入力パラメーター**

- **http_server_ptr** HTTP サーバー インスタンスへのポインター
- **name** 検索するバッファーへのポインター
- **http_type_string** (抽出された HTML の種類へのポインター)

**戻り値**

- **文字列の長さ (バイト単位)** 0 以外の値は成功です
- **0 はエラーを示します**

**許可元**

Application

**例**

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

詳細な例については、

*nx_http_server_callback_generate_response_header* の説明を参照してください。

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

### <a name="extract-file-type-from-client-http-request"></a>クライアントの HTTP 要求からファイルの種類を抽出する

**プロトタイプ**

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

**説明**

このサービスは、*http_type_string* バッファー内の HTTP 要求の種類と、入力バッファー *name* からの戻り値 (通常は URL) 内のその長さを抽出します。 MIME マップが見つからない場合、既定で "text/plain" という種類に設定されます。 それ以外の場合、抽出された種類を HTTP サーバーの既定の MIME マップと比較して、一致するものを探します。 NetX Duo HTTP サーバーの既定の MIME マップは次のとおりです。

- html text/html
- htm text/html
- txt text/plain
- gif image/gif
- jpg image/jpeg
- ico image/x-icon

指定した場合は、追加の MIME マップのユーザー定義セットも検索されます。 ユーザー定義マップの詳細については、*nx_http_server_mime_maps_addtional_set()* を参照してください。

このサービスは *nx_http_server_type_get()* を置き換えます。 このバージョンでは、追加の長さの情報が提供されます。

**入力パラメーター**

- **http_server_ptr** HTTP サーバー インスタンスへのポインター
- **name** 検索するバッファーへのポインター
- **name_length** 検索するバッファーの長さ
- **http_type_string** (抽出された HTML の種類へのポインター)
- **http_type_string_max_size**

*http_type_string* バッファーのサイズ

**戻り値**

- **文字列の長さ (バイト単位)** 0 以外の値は成功です<br />0 はエラーを示します

**許可元**

Application

**例**

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
       my_server.nx_http_server_request_resource, &resource_length,
       sizeof(my_server.nx_http_server_request_resource) - 1))
    {
        return;
    }
/* Extract the HTTP type. */
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

詳細な例については、

*nx_http_server_callback_generate_response_header* の説明を参照してください。

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

### <a name="set-digest-authenticate-callback-function"></a>ダイジェスト認証コールバック関数を設定する

**プロトタイプ**

```c
UINT nx_http_server_digest_authenticate_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                         CHAR *name_ptr,
                                         CHAR *realm_ptr,
                                         CHAR *password_ptr,
                                         CHAR *method,
                                         CHAR *authorization_uri,
                                         CHAR *authorization_nc,
                                         CHAR *authorization_cnonce
                                         ));
```

**説明**

このサービスは、ダイジェスト認証の実行時に呼び出されるコールバックを設定します。

**入力パラメーター**

- **http_server_ptr** HTTP サーバー インスタンスへのポインター
- **digest_authenticate_callback** ダイジェスト認証コールバックへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_NOT_SUPPORTED (0x4B) ダイジェスト認証が有効になっていません

**許可元**

Application

**例**

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

### <a name="set-authentication-checking-callback-function"></a>認証確認コールバック関数を設定する

**プロトタイプ**

```c
UINT nx_http_server_authentication_check_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*authentication_check_extended)(
                                          NX_HTTP_SERVER *server_ptr,
                                          UINT request_type,
                                          CHAR *resource,
                                          CHAR **name,
                                          UINT *name_length,
                                          CHAR **password,
                                          UINT *password_length,
                                          CHAR **realm,
                                          UINT *realm_length
                                          ));
```

**説明**

このサービスは、認証確認のコールバック関数を設定します。

**入力パラメーター**

- **http_server_ptr** HTTP サーバー インスタンスへのポインター
- **authentication_check_extended** アプリケーションの認証確認へのポインター

**戻り値**

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました
- NX_PTR_ERROR (0x07) ポインター入力が無効です

**許可元**

Application

**例**

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```