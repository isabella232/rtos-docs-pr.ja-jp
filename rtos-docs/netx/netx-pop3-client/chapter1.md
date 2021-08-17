---
title: 第 1 章 - Azure RTOS NetX POP3 クライアントの概要
description: Azure RTOS NetX POP3 クライアント API は、小規模なワークステーションから POP3 サーバー上のクライアント メールドロップにアクセスしてクライアント メールを取得するためのメール転送システムを提供します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6abaa778da6203d0df367894165cb29ca629ab5e24403a35af1995f032cf0d4c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798811"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a>第 1 章 - Azure RTOS NetX POP3 クライアントの概要

Post Office Protocol Version 3 (POP3) は、小規模なワークステーションから POP3 サーバー上のクライアント メールドロップにアクセスしてクライアント メールを取得するためのメール転送システムを提供することを目的としたプロトコルです。 POP3 では、伝送制御プロトコル (TCP) サービスを利用してメール転送を実行します。 そのため、POP3 は信頼性の高いコンテンツ転送プロトコルです。

ただし、POP3 ではメール処理に関する広範な操作は提供されません。 通常、メールはクライアントによってダウンロードされた後、サーバーのメールドロップから削除されます。

## <a name="netx-pop3-client-requirements"></a>NetX POP3 クライアントの要件

### <a name="client-requirements"></a>クライアントの要件

Azure RTOS NetX POP3 クライアント API には、*nx_ip_create* を使用して以前に作成した NetX IP インスタンスと、*nx_packet_pool_create* を使用して以前に作成した NetX パケット プールが必要です。 NetX POP3 クライアントでは TCP サービスを利用するため、その同じ IP インスタンスで NetX POP3 クライアント サービスを使用する前に、*nx_tcp_enable* 呼び出しを使用して TCP を有効にする必要があります。 POP3 クライアントでは TCP ソケットを使用して、サーバーの POP3 ポートで POP3 サーバーに接続します。 通常、これは "*ウェルノウン ポート 110 に設定されていますが、POP3 クライアントもサーバーも、このポートの使用は必須ではありません。* "

POP3 クライアントの作成に使用されるパケット プールのサイズは、パケット ペイロードと使用可能なパケットの数に関してユーザーが構成できます。 パケットが POP3 クライアント作成サービスでのみ使用される場合、ユーザー名とパスワードの長さ、または APOP ダイジェストの長さに応じて、パケット ペイロードは 100 から 120 バイト以上である必要はありません。 ローカル ホストのユーザー名を使用する USER コマンドが、POP3 クライアントから送信される最大のメッセージであると考えられます。 IP 内部操作では、TCP 制御データの送受信にそれほど大きいパケット ペイロードを必要としないため、nx_ip_create (IP の既定のパケット プール) で同じパケット プールを共有できます。

ただし、ネットワーク ドライバーで POP3 クライアントのパケット プールと同じパケット プールを使用するのは得策ではない場合があります。 一般に、受信パケット プールのペイロードは、ネットワーク インターフェイスの IP インスタンスの MTU (通常は 1,500 バイト) に設定されます。これは、POP3 クライアント メッセージよりもはるかに大きなサイズです。 通常、受信 POP3 メッセージは、送信 POP3 クライアント メッセージよりもデータがはるかに大きくなります。

## <a name="netx-pop3-client-creation"></a>NetX POP3 クライアントの作成

POP3 クライアント作成サービスの *nx_pop3_client_create* では、TCP ソケットを作成し、POP3 サーバーに接続します。

POP3 サーバーに接続したら、POP3 クライアント アプリケーションで *nx_pop3_client_mail_items_get* を呼び出して、メールドロップ ボックスにあるメール アイテムの数を取得できます。

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

クライアントのメールドロップに 1 つ以上のアイテムがある場合は、アプリケーションで *nx_pop3_client_get_mail_item* サービスを使用して、特定のメール アイテムのサイズを取得できます。

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

メールドロップの最初のメール アイテムはインデックス 1 にあります。

実際のメール メッセージを取得するには、アプリケーションで *nx_pop3_client_mail_item_get_message_data* サービスを呼び出して、final_packet 入力引数によって最後のパケットを受信したことが示されるまで、メール メッセージ パケットを取得します。

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

特定のメール アイテムを削除するには、前の *nx_pop3_client_get_mail_item* 呼び出しで使用したものと同じインデックスを使用して、*nx_pop3_client_mail_item_delete* を呼び出します。

クライアントは、*nx_pop3_client_delete* サービスを使用して削除できます。 POP3 クライアントのパケット プールが不要になった場合、*nx_packet_pool_delete* サービスを使用してそれを削除するのはアプリケーションの役割です。

## <a name="netx-pop3-client-constraints"></a>NetX POP3 クライアントの制約

NetX POP3 クライアント実装には、いくつかの制約があります。

1. NetX POP3 クライアントは、クライアント サーバー認証交換に DIGEST-MD5 を使用する APOP 認証を実装していますが、AUTH コマンドはサポートされていません。

1. NetX POP3 クライアントは、すべての POP3 コマンド (TOP コマンドや UIDL コマンドなど) を実装しているわけではありません。 サポートされているコマンドの一覧を次に示します。
   - NOOP
   - RSET

## <a name="netx-pop3-client-login"></a>NetX POP3 クライアントのログイン

NetX POP3 クライアントは、メールドロップにアクセスするために、POP3 サーバーに対して認証 (ログイン) を行う必要があります。 これを行うには、USER および PASS コマンドを使用し、POP3 サーバーに認識されているユーザー名とパスワードを指定するか、後述する APOP コマンドと MD5 ダイジェストを使用します。

通常、ユーザー名は完全修飾ドメイン名です ("@" 文字で区切られた、ローカル部分とドメイン名が含まれます)。 POP3 コマンドの USER と PASS を使用する場合、クライアントは暗号化されていないユーザー名とパスワードをインターネット経由で送信します。

クリア テキストのユーザー名とパスワードのセキュリティ リスクを回避するために、*nx_pop3_client_create* サービスで *APOP_authentication* パラメーターを設定して、APOP 認証を使用するように NetX POP3 クライアントを構成できます。

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

IPv4 専用アプリケーションの場合、*nx_pop3_client_create* サービスは次のようになります。

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

クライアントは、APOP コマンドを送信したときに、サーバー接続時のメッセージから抽出されたサーバー ドメイン、ローカル時刻、およびプロセス ID と、クライアント パスワードを含む MD5 ダイジェストを取得します。 POP3 サーバーでは、同じ情報を含む MD5 ダイジェストを作成します。その MD5 ダイジェストがクライアントの MD5 ダイジェストと一致すれば、クライアントは認証されます。

APOP 認証が失敗した場合、NetX POP3 クライアントは USER および PASS 認証を試みます。

## <a name="the-pop3-client-maildrop"></a>POP3 クライアントのメールドロップ

クライアント メールは、POP3 サーバー上のメールボックス ("メールドロップ") に保存されます。 POP3 サーバー上のクライアント メールドロップは、メール アイテムの 1 から始まるリストとして表されます。 つまり、各メールはメールドロップ リストのインデックスで参照されます。最初のメール アイテムがインデックス 1 にあります (0 ではありません)。 POP3 コマンドは、このリストのインデックスで特定のメール アイテムを参照します。

## <a name="the-pop3-protocol-state-machine"></a>POP3 プロトコル ステート マシン

POP3 プロトコルでは、クライアントとサーバーの両方が POP3 セッションの状態を維持する必要があります。 まず、クライアントが POP3 サーバーへの接続を試みます。 成功すると、RFC 1939 で 3 つの異なる状態が定義されている POP3 プロトコルが開始されます。 初期状態である承認状態では、サーバーに対して身元を証明する必要があります。 承認状態では、POP3 クライアントが発行できるのは、USER および PASS コマンド (この順序で発行)、または APOP コマンドだけです。

POP3 クライアントが認証されると、クライアント セッションはトランザクション状態に移行します。 この状態では、クライアントはメールをダウンロードし、メールの削除を要求できます。 トランザクション状態で許可されているコマンドは、LIST、STAT、RETR、DELE、RSET、QUIT です。 通常、POP3 クライアントは、STAT コマンドの後に一連の RETR コマンド (メールドロップ内のメール アイテムごとに 1 つ) を送信します。

クライアントが QUIT コマンドを発行すると、POP3 セッションは更新状態に移行し、サーバーからの TCP 切断が開始されます。 メールを後でダウンロードする場合は、POP3 クライアント アプリケーションで `nx_pop3_client_mail_items_get` をいつでも呼び出して、メールドロップに新着メールがあるかどうかを確認できます。

### <a name="pop3-server-reply-codes"></a>POP3 サーバーの応答コード

- **+OK**: サーバーでは、この応答を使用してクライアント コマンドを受け入れます。 サーバーは "+OK" の後に追加情報を含めることができますが、クライアントがこの情報を処理するとは限りません。ただし、メール メッセージ データのダウンロードや LIST または DELE コマンドの場合を除きます。 後者の場合、コマンドの後の "引数" は、クライアント メールドロップ内のメール アイテムのインデックスを参照します。

- **-ERR**: サーバーでは、この応答を使用してクライアント コマンドを拒否します。 サーバーは "-ERR" の後に追加情報を送信できますが、クライアントがこの情報を処理するとは限りません。

### <a name="sample-pop3-client---server-session"></a>POP3 クライアント - サーバー セッションのサンプル

**USER および PASS を使用した基本的な POP3 の例:**

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

**APOP (および STAT ではなく LIST) を使用した基本的な POP3 の例:**

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-pop3-client"></a>NetX POP3 クライアントでサポートされる RFC

NetX POP3 クライアントは、RFC 1939 に準拠しています。
