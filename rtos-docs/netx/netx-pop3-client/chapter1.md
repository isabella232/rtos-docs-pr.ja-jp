---
title: 第 1 章 - Azure RTOS NetX POP3 クライアントの概要
description: Azure RTOS NetX POP3 クライアント API は、小規模なワークステーションから POP3 サーバー上のクライアント メールドロップにアクセスしてクライアント メールを取得するためのメール転送システムを提供します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811486"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a><span data-ttu-id="f4727-103">第 1 章 - Azure RTOS NetX POP3 クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="f4727-103">Chapter 1 - Introduction to Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="f4727-104">Post Office Protocol Version 3 (POP3) は、小規模なワークステーションから POP3 サーバー上のクライアント メールドロップにアクセスしてクライアント メールを取得するためのメール転送システムを提供することを目的としたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="f4727-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="f4727-105">POP3 では、伝送制御プロトコル (TCP) サービスを利用してメール転送を実行します。</span><span class="sxs-lookup"><span data-stu-id="f4727-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="f4727-106">そのため、POP3 は信頼性の高いコンテンツ転送プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="f4727-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="f4727-107">ただし、POP3 ではメール処理に関する広範な操作は提供されません。</span><span class="sxs-lookup"><span data-stu-id="f4727-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="f4727-108">通常、メールはクライアントによってダウンロードされた後、サーバーのメールドロップから削除されます。</span><span class="sxs-lookup"><span data-stu-id="f4727-108">Typically, mail is downloaded by the Client and then deleted from the Server's maildrop.</span></span>

## <a name="netx-pop3-client-requirements"></a><span data-ttu-id="f4727-109">NetX POP3 クライアントの要件</span><span class="sxs-lookup"><span data-stu-id="f4727-109">NetX POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="f4727-110">クライアントの要件</span><span class="sxs-lookup"><span data-stu-id="f4727-110">Client Requirements</span></span>

<span data-ttu-id="f4727-111">Azure RTOS NetX POP3 クライアント API には、*nx_ip_create* を使用して以前に作成した NetX IP インスタンスと、*nx_packet_pool_create* を使用して以前に作成した NetX パケット プールが必要です。</span><span class="sxs-lookup"><span data-stu-id="f4727-111">The Azure RTOS NetX POP3 Client API requires a previously created NetX IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="f4727-112">NetX POP3 クライアントでは TCP サービスを利用するため、その同じ IP インスタンスで NetX POP3 クライアント サービスを使用する前に、*nx_tcp_enable* 呼び出しを使用して TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4727-112">Because the NetX POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX POP3 Client services on that same IP instance.</span></span> <span data-ttu-id="f4727-113">POP3 クライアントでは TCP ソケットを使用して、サーバーの POP3 ポートで POP3 サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="f4727-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server's POP3 port.</span></span> <span data-ttu-id="f4727-114">通常、これは "*ウェルノウン ポート 110 に設定されていますが、POP3 クライアントもサーバーも、このポートの使用は必須ではありません。* "</span><span class="sxs-lookup"><span data-stu-id="f4727-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server is required to use this port.*</span></span>

<span data-ttu-id="f4727-115">POP3 クライアントの作成に使用されるパケット プールのサイズは、パケット ペイロードと使用可能なパケットの数に関してユーザーが構成できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="f4727-116">パケットが POP3 クライアント作成サービスでのみ使用される場合、ユーザー名とパスワードの長さ、または APOP ダイジェストの長さに応じて、パケット ペイロードは 100 から 120 バイト以上である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f4727-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="f4727-117">ローカル ホストのユーザー名を使用する USER コマンドが、POP3 クライアントから送信される最大のメッセージであると考えられます。</span><span class="sxs-lookup"><span data-stu-id="f4727-117">The USER command with the local host's user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="f4727-118">IP 内部操作では、TCP 制御データの送受信にそれほど大きいパケット ペイロードを必要としないため、nx_ip_create (IP の既定のパケット プール) で同じパケット プールを共有できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operations do not require a very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="f4727-119">ただし、ネットワーク ドライバーで POP3 クライアントのパケット プールと同じパケット プールを使用するのは得策ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4727-119">However, it may not be advantageous for the network driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="f4727-120">一般に、受信パケット プールのペイロードは、ネットワーク インターフェイスの IP インスタンスの MTU (通常は 1,500 バイト) に設定されます。これは、POP3 クライアント メッセージよりもはるかに大きなサイズです。</span><span class="sxs-lookup"><span data-stu-id="f4727-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="f4727-121">通常、受信 POP3 メッセージは、送信 POP3 クライアント メッセージよりもデータがはるかに大きくなります。</span><span class="sxs-lookup"><span data-stu-id="f4727-121">Incoming POP3 messages would usually be much larger data then outgoing POP3 Client messages</span></span>

## <a name="netx-pop3-client-creation"></a><span data-ttu-id="f4727-122">NetX POP3 クライアントの作成</span><span class="sxs-lookup"><span data-stu-id="f4727-122">NetX POP3 Client Creation</span></span>

<span data-ttu-id="f4727-123">POP3 クライアント作成サービスの *nx_pop3_client_create* では、TCP ソケットを作成し、POP3 サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="f4727-123">The POP3 Client create service, *nx_pop3_client_create* create the TCP socket and connect with the POP3 server.</span></span>

<span data-ttu-id="f4727-124">POP3 サーバーに接続したら、POP3 クライアント アプリケーションで *nx_pop3_client_mail_items_get* を呼び出して、メールドロップ ボックスにあるメール アイテムの数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-124">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

<span data-ttu-id="f4727-125">クライアントのメールドロップに 1 つ以上のアイテムがある場合は、アプリケーションで *nx_pop3_client_get_mail_item* サービスを使用して、特定のメール アイテムのサイズを取得できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-125">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

<span data-ttu-id="f4727-126">メールドロップの最初のメール アイテムはインデックス 1 にあります。</span><span class="sxs-lookup"><span data-stu-id="f4727-126">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="f4727-127">実際のメール メッセージを取得するには、アプリケーションで *nx_pop3_client_mail_item_get_message_data* サービスを呼び出して、final_packet 入力引数によって最後のパケットを受信したことが示されるまで、メール メッセージ パケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="f4727-127">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

<span data-ttu-id="f4727-128">特定のメール アイテムを削除するには、前の *nx_pop3_client_get_mail_item* 呼び出しで使用したものと同じインデックスを使用して、*nx_pop3_client_mail_item_delete* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f4727-128">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="f4727-129">クライアントは、*nx_pop3_client_delete* サービスを使用して削除できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-129">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="f4727-130">POP3 クライアントのパケット プールが不要になった場合、*nx_packet_pool_delete* サービスを使用してそれを削除するのはアプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="f4727-130">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-pop3-client-constraints"></a><span data-ttu-id="f4727-131">NetX POP3 クライアントの制約</span><span class="sxs-lookup"><span data-stu-id="f4727-131">NetX POP3 Client Constraints</span></span>

<span data-ttu-id="f4727-132">NetX POP3 クライアント実装には、いくつかの制約があります。</span><span class="sxs-lookup"><span data-stu-id="f4727-132">There are some constraints in the NetX POP3 Client implementation:</span></span>

1. <span data-ttu-id="f4727-133">NetX POP3 クライアントは、クライアント サーバー認証交換に DIGEST-MD5 を使用する APOP 認証を実装していますが、AUTH コマンドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f4727-133">The NetX POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>

1. <span data-ttu-id="f4727-134">NetX POP3 クライアントは、すべての POP3 コマンド (TOP コマンドや UIDL コマンドなど) を実装しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f4727-134">NetX POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="f4727-135">サポートされているコマンドの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f4727-135">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="f4727-136">NOOP</span><span class="sxs-lookup"><span data-stu-id="f4727-136">NOOP</span></span>
   - <span data-ttu-id="f4727-137">RSET</span><span class="sxs-lookup"><span data-stu-id="f4727-137">RSET</span></span>

## <a name="netx-pop3-client-login"></a><span data-ttu-id="f4727-138">NetX POP3 クライアントのログイン</span><span class="sxs-lookup"><span data-stu-id="f4727-138">NetX POP3 Client Login</span></span>

<span data-ttu-id="f4727-139">NetX POP3 クライアントは、メールドロップにアクセスするために、POP3 サーバーに対して認証 (ログイン) を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4727-139">A NetX POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="f4727-140">これを行うには、USER および PASS コマンドを使用し、POP3 サーバーに認識されているユーザー名とパスワードを指定するか、後述する APOP コマンドと MD5 ダイジェストを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4727-140">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="f4727-141">通常、ユーザー名は完全修飾ドメイン名です ("@" 文字で区切られた、ローカル部分とドメイン名が含まれます)。</span><span class="sxs-lookup"><span data-stu-id="f4727-141">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an '@' character).</span></span> <span data-ttu-id="f4727-142">POP3 コマンドの USER と PASS を使用する場合、クライアントは暗号化されていないユーザー名とパスワードをインターネット経由で送信します。</span><span class="sxs-lookup"><span data-stu-id="f4727-142">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="f4727-143">クリア テキストのユーザー名とパスワードのセキュリティ リスクを回避するために、*nx_pop3_client_create* サービスで *APOP_authentication* パラメーターを設定して、APOP 認証を使用するように NetX POP3 クライアントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-143">To avoid the security risk of clear texting username and password, the NetX POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nx_pop3_client_create* service:</span></span>

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="f4727-144">IPv4 専用アプリケーションの場合、*nx_pop3_client_create* サービスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f4727-144">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="f4727-145">クライアントは、APOP コマンドを送信したときに、サーバー接続時のメッセージから抽出されたサーバー ドメイン、ローカル時刻、およびプロセス ID と、クライアント パスワードを含む MD5 ダイジェストを取得します。</span><span class="sxs-lookup"><span data-stu-id="f4727-145">When the Client sends the APOP command, it takes an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="f4727-146">POP3 サーバーでは、同じ情報を含む MD5 ダイジェストを作成します。その MD5 ダイジェストがクライアントの MD5 ダイジェストと一致すれば、クライアントは認証されます。</span><span class="sxs-lookup"><span data-stu-id="f4727-146">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client's MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="f4727-147">APOP 認証が失敗した場合、NetX POP3 クライアントは USER および PASS 認証を試みます。</span><span class="sxs-lookup"><span data-stu-id="f4727-147">If APOP authentication fails, NetX POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="f4727-148">POP3 クライアントのメールドロップ</span><span class="sxs-lookup"><span data-stu-id="f4727-148">The POP3 Client Maildrop</span></span>

<span data-ttu-id="f4727-149">クライアント メールは、POP3 サーバー上のメールボックス ("メールドロップ") に保存されます。</span><span class="sxs-lookup"><span data-stu-id="f4727-149">Client mail is stored on a POP3 Server in a mailbox or "maildrop."</span></span> <span data-ttu-id="f4727-150">POP3 サーバー上のクライアント メールドロップは、メール アイテムの 1 から始まるリストとして表されます。</span><span class="sxs-lookup"><span data-stu-id="f4727-150">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="f4727-151">つまり、各メールはメールドロップ リストのインデックスで参照されます。最初のメール アイテムがインデックス 1 にあります (0 ではありません)。</span><span class="sxs-lookup"><span data-stu-id="f4727-151">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="f4727-152">POP3 コマンドは、このリストのインデックスで特定のメール アイテムを参照します。</span><span class="sxs-lookup"><span data-stu-id="f4727-152">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="f4727-153">POP3 プロトコル ステート マシン</span><span class="sxs-lookup"><span data-stu-id="f4727-153">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="f4727-154">POP3 プロトコルでは、クライアントとサーバーの両方が POP3 セッションの状態を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4727-154">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="f4727-155">まず、クライアントが POP3 サーバーへの接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="f4727-155">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="f4727-156">成功すると、RFC 1939 で 3 つの異なる状態が定義されている POP3 プロトコルが開始されます。</span><span class="sxs-lookup"><span data-stu-id="f4727-156">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="f4727-157">初期状態である承認状態では、サーバーに対して身元を証明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4727-157">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="f4727-158">承認状態では、POP3 クライアントが発行できるのは、USER および PASS コマンド (この順序で発行)、または APOP コマンドだけです。</span><span class="sxs-lookup"><span data-stu-id="f4727-158">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="f4727-159">POP3 クライアントが認証されると、クライアント セッションはトランザクション状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="f4727-159">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="f4727-160">この状態では、クライアントはメールをダウンロードし、メールの削除を要求できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-160">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="f4727-161">トランザクション状態で許可されているコマンドは、LIST、STAT、RETR、DELE、RSET、QUIT です。</span><span class="sxs-lookup"><span data-stu-id="f4727-161">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="f4727-162">通常、POP3 クライアントは、STAT コマンドの後に一連の RETR コマンド (メールドロップ内のメール アイテムごとに 1 つ) を送信します。</span><span class="sxs-lookup"><span data-stu-id="f4727-162">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="f4727-163">クライアントが QUIT コマンドを発行すると、POP3 セッションは更新状態に移行し、サーバーからの TCP 切断が開始されます。</span><span class="sxs-lookup"><span data-stu-id="f4727-163">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="f4727-164">メールを後でダウンロードする場合は、POP3 クライアント アプリケーションで `nx_pop3_client_mail_items_get` をいつでも呼び出して、メールドロップに新着メールがあるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4727-164">To download mail later, the POP3 Client application may call `nx_pop3_client_mail_items_get` at any time to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="f4727-165">POP3 サーバーの応答コード</span><span class="sxs-lookup"><span data-stu-id="f4727-165">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="f4727-166">**+OK**: サーバーでは、この応答を使用してクライアント コマンドを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="f4727-166">**+OK**: The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="f4727-167">サーバーは "+OK" の後に追加情報を含めることができますが、クライアントがこの情報を処理するとは限りません。ただし、メール メッセージ データのダウンロードや LIST または DELE コマンドの場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="f4727-167">The Server can include additional information after the '+OK' but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="f4727-168">後者の場合、コマンドの後の "引数" は、クライアント メールドロップ内のメール アイテムのインデックスを参照します。</span><span class="sxs-lookup"><span data-stu-id="f4727-168">In the latter case, the 'argument' after the command references the index of the mail item in the Client maildrop.</span></span>

- <span data-ttu-id="f4727-169">**-ERR**: サーバーでは、この応答を使用してクライアント コマンドを拒否します。</span><span class="sxs-lookup"><span data-stu-id="f4727-169">**-ERR**: The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="f4727-170">サーバーは "-ERR" の後に追加情報を送信できますが、クライアントがこの情報を処理するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f4727-170">The Server may send additional information following the '-ERR' but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="f4727-171">POP3 クライアント - サーバー セッションのサンプル</span><span class="sxs-lookup"><span data-stu-id="f4727-171">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="f4727-172">**USER および PASS を使用した基本的な POP3 の例:**</span><span class="sxs-lookup"><span data-stu-id="f4727-172">**Basic POP3 example using USER/PASS:**</span></span>

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

<span data-ttu-id="f4727-173">**APOP (および STAT ではなく LIST) を使用した基本的な POP3 の例:**</span><span class="sxs-lookup"><span data-stu-id="f4727-173">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

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

## <a name="rfcs-supported-by-netx-pop3-client"></a><span data-ttu-id="f4727-174">NetX POP3 クライアントでサポートされる RFC</span><span class="sxs-lookup"><span data-stu-id="f4727-174">RFCs Supported by NetX POP3 Client</span></span>

<span data-ttu-id="f4727-175">NetX POP3 クライアントは、RFC 1939 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="f4727-175">NetX Client POP3 is compliant with RFC 1939.</span></span>
