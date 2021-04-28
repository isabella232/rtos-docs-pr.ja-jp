---
title: チャプター 1 -Azure RTOS NetX Duo Telnet の概要
description: Azure RTOS NetX Duo Telnet は、コマンドと応答をインターネット上の 2 つのノード間で転送するためのプロトコルです。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d25f5ca4a7bf1ecf4c3d0c68ef6c8aeda7800098
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810550"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a><span data-ttu-id="42502-103">チャプター 1 -Azure RTOS NetX Duo Telnet の概要</span><span class="sxs-lookup"><span data-stu-id="42502-103">Chapter 1 - Introduction to the Azure RTOS NetX Duo Telnet</span></span>

<span data-ttu-id="42502-104">Azure RTOS NetX Duo Telnet は、コマンドと応答をインターネット上の 2 つのノード間で転送するためのプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="42502-104">The Azure RTOS NetX Duo Telnet is a protocol designed for transferring commands and responses between two nodes on the Internet.</span></span> <span data-ttu-id="42502-105">Telnet は、信頼性の高い伝送制御プロトコル (TCP) サービスを使用して転送処理を実行する単純なプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="42502-105">Telnet is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its transfer function.</span></span> <span data-ttu-id="42502-106">そのため、Telnet は信頼性の高い転送プロトコルとなっています。</span><span class="sxs-lookup"><span data-stu-id="42502-106">Because of this, Telnet is a highly reliable transfer protocol.</span></span> <span data-ttu-id="42502-107">Telnet は、最も多く使用されているアプリケーション プロトコルの 1 つでもあります。</span><span class="sxs-lookup"><span data-stu-id="42502-107">Telnet is also one of the most used application protocols.</span></span>

## <a name="telnet-requirements"></a><span data-ttu-id="42502-108">Telnet の要件</span><span class="sxs-lookup"><span data-stu-id="42502-108">Telnet Requirements</span></span>

<span data-ttu-id="42502-109">NetX Duo Telnet パッケージが正常に機能するためには、NetX IP インスタンスを前もって作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="42502-109">In order to function properly, the NetX Duo Telnet package requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="42502-110">また、その IP インスタンスで TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="42502-110">In addition, TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="42502-111">NetX Duo Telnet パッケージに含まれる Telnet クライアントには、それ以上の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="42502-111">The Telnet Client portion of the NetX Duo Telnet package has no further requirements.</span></span>

<span data-ttu-id="42502-112">NetX Duo Telnet パッケージに含まれる Telnet サーバーには、1 つ追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="42502-112">The Telnet Server portion of the NetX Duo Telnet package has one additional requirement.</span></span> <span data-ttu-id="42502-113">Telnet サーバーでは、クライアントのすべての Telnet 要求を処理するために、ウェルノウン ポートである TCP *ポート 23* への完全なアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="42502-113">It requires complete access to TCP *well-known port 23* for handling all Client Telnet requests.</span></span>

## <a name="telnet-constraints"></a><span data-ttu-id="42502-114">Telnet の制約</span><span class="sxs-lookup"><span data-stu-id="42502-114">Telnet Constraints</span></span> 

<span data-ttu-id="42502-115">NetX Duo Telnet プロトコルでは Telnet 標準を実装しています。</span><span class="sxs-lookup"><span data-stu-id="42502-115">The NetX Duo Telnet protocol implements the Telnet standard.</span></span> <span data-ttu-id="42502-116">ただし、255 の値を持つバイトで示される Telnet コマンドを解釈してそれに応答するのは、アプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="42502-116">However,the interpretation and response of Telnet commands, indicated by a byte with the value of 255, is the responsibility of the application.</span></span> <span data-ttu-id="42502-117">さまざまな Telnet コマンドおよびコマンドのパラメーターは、*nxd_telnet_client.h および nxd_telnet_server.h* ファイルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="42502-117">The various Telnet commands and command parameters are defined in the *nxd_telnet_client.h and nxd_telnet_server.h* files.</span></span>

## <a name="telnet-communication"></a><span data-ttu-id="42502-118">Telnet 通信</span><span class="sxs-lookup"><span data-stu-id="42502-118">Telnet Communication</span></span>

<span data-ttu-id="42502-119">前述のとおり、Telnet サーバーでは、ウェルノウン ポートである *TCP ポート 23* を使用してクライアントの要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="42502-119">As mentioned previously, the Telnet Server utilizes the *well-known TCP port 23* to field Client requests.</span></span> <span data-ttu-id="42502-120">Telnet クライアントでは、任意の空き TCP ポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="42502-120">Telnet Clients may use any available TCP port.</span></span>

## <a name="telnet-authentication"></a><span data-ttu-id="42502-121">Telnet 認証</span><span class="sxs-lookup"><span data-stu-id="42502-121">Telnet Authentication</span></span>

<span data-ttu-id="42502-122">Telnet 認証は、アプリケーションの Telnet サーバーのコールバック関数で行います。</span><span class="sxs-lookup"><span data-stu-id="42502-122">Telnet authentication is the responsibility of the application’s Telnet Server callback function.</span></span> <span data-ttu-id="42502-123">アプリケーションの Telnet サーバーの “新規接続”コールバックでは通常、名前やパスワードの入力を求めるメッセージをクライアントに表示します。</span><span class="sxs-lookup"><span data-stu-id="42502-123">The application’s Telnet Server “new connection” callback would typically prompt the Client for name and/or password.</span></span> <span data-ttu-id="42502-124">そして、クライアントがその情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="42502-124">The Client would then be responsible for providing the information.</span></span> <span data-ttu-id="42502-125">それから、サーバーが “データ受信” コールバックで情報を処理します。</span><span class="sxs-lookup"><span data-stu-id="42502-125">The Server would then process the information in the “receive data” callback.</span></span> <span data-ttu-id="42502-126">その際、アプリケーションのサーバー コードにより情報を認証して有効性を判断することもできます。</span><span class="sxs-lookup"><span data-stu-id="42502-126">This is where the application Server code would have to authenticate the information and decide whether or not it is valid.</span></span>

## <a name="telnet-new-connection-callback"></a><span data-ttu-id="42502-127">Telnet 新規接続コールバック</span><span class="sxs-lookup"><span data-stu-id="42502-127">Telnet New Connection Callback</span></span>

<span data-ttu-id="42502-128">NetX Duo Telnet サーバーでは、Telnet クライアントから新たな要求を受信するたびに、アプリケーションで指定するコールバック関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="42502-128">The NetX Duo Telnet Server calls the application specified callback function whenever a new Telnet Client request is received.</span></span> <span data-ttu-id="42502-129">このコールバック関数は、アプリケーションで ***nx_telnet_server_create*** 関数を使用して Telnet サーバーを作成するときに指定します。</span><span class="sxs-lookup"><span data-stu-id="42502-129">The application specifies the callback function when the Telnet Server is created via the ***nx_telnet_server_create*** function.</span></span> <span data-ttu-id="42502-130">“新規接続” コールバックでは通常、クライアントにバナーまたはプロンプトを送信します。</span><span class="sxs-lookup"><span data-stu-id="42502-130">Typical actions of the “new connection” callback include sending a banner or prompt to the Client.</span></span> <span data-ttu-id="42502-131">ログイン情報の入力を求めるプロンプトをここに含める場合も多いです。</span><span class="sxs-lookup"><span data-stu-id="42502-131">This could very well include a prompt for login information.</span></span>

### <a name="prototype"></a><span data-ttu-id="42502-132">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="42502-132">Prototype</span></span>

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a><span data-ttu-id="42502-133">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="42502-133">Input Parameters</span></span>

- <span data-ttu-id="42502-134">**server_ptr**: 呼び出し元の Telnet サーバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42502-134">**server_ptr**: Pointer to the calling Telnet Server.</span></span>
- <span data-ttu-id="42502-135">**logical_connection**: Telnet サーバーで使用する、内部の論理的な接続。</span><span class="sxs-lookup"><span data-stu-id="42502-135">**logical_connection**: The internal logical connection for the Telnet Server.</span></span> <span data-ttu-id="42502-136">この接続は、各クライアント接続に固有のバッファーおよびデータ構造体のインデックスとしてアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="42502-136">This can be used by the application as an index into buffers and/or data structures specific for each Client connection.</span></span> <span data-ttu-id="42502-137">取り得る値の範囲は 0 から NX_TELNET_MAX_CLIENTS - 1 です。</span><span class="sxs-lookup"><span data-stu-id="42502-137">Its value ranges from 0 through NX_TELNET_MAX_CLIENTS - 1.</span></span>

## <a name="telnet-receive-data-callback"></a><span data-ttu-id="42502-138">Telnet データ受信コールバック</span><span class="sxs-lookup"><span data-stu-id="42502-138">Telnet Receive Data Callback</span></span>

<span data-ttu-id="42502-139">NetX Duo Telnet サーバーでは、Telnet クライアントの新たなデータを受信するたびに、アプリケーションで指定したコールバック関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="42502-139">The NetX Duo Telnet Server calls the application specified callback function whenever a new Telnet Client data is received.</span></span> <span data-ttu-id="42502-140">このコールバック関数は、アプリケーションで ***nx_telnet_server_create*** 関数を使用して Telnet サーバーを作成するときに指定します。</span><span class="sxs-lookup"><span data-stu-id="42502-140">The application specifies the callback function when the Telnet Server is created via the ***nx_telnet_server_create*** function.</span></span> <span data-ttu-id="42502-141">“新規接続” コールバックでは通常、データのエコー バックや解析を行い、クライアントのコマンドを解釈して得られたデータを返します。</span><span class="sxs-lookup"><span data-stu-id="42502-141">Typical actions of the “new connection” callback include echoing the data back and/or parsing the data and providing data as a result of interpreting a command from the client.</span></span>

<span data-ttu-id="42502-142">このコールバック ルーチンでは、受け取ったパケットを解放する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="42502-142">Note that this callback routine must also release the supplied packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="42502-143">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="42502-143">Prototype</span></span>

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a><span data-ttu-id="42502-144">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="42502-144">Input Parameters</span></span>

- <span data-ttu-id="42502-145">**server_ptr**: 呼び出し元の Telnet サーバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42502-145">**server_ptr**: Pointer to the calling Telnet Server.</span></span>
- <span data-ttu-id="42502-146">**logical_connection**: Telnet サーバーで使用する、内部の論理的な接続。</span><span class="sxs-lookup"><span data-stu-id="42502-146">**logical_connection**: The internal logical connection for the Telnet Server.</span></span> <span data-ttu-id="42502-147">この接続は、各クライアント接続に固有のバッファーおよびデータ構造体のインデックスとしてアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="42502-147">This can be used by the application as an index into buffers and/or data structures specific for each Client connection.</span></span> <span data-ttu-id="42502-148">取り得る値の範囲は 0 から NX_TELNET_MAX_CLIENTS - 1 です。</span><span class="sxs-lookup"><span data-stu-id="42502-148">Its value ranges from 0 through NX_TELNET_MAX_CLIENTS - 1.</span></span>
- <span data-ttu-id="42502-149">**packet_ptr**: クライアントから受け取ったデータを保持するパケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42502-149">**packet_ptr**: Pointer to packet containing the data from the Client.</span></span>

## <a name="telnet-end-connection-callback"></a><span data-ttu-id="42502-150">Telnet 接続終了コールバック</span><span class="sxs-lookup"><span data-stu-id="42502-150">Telnet End Connection Callback</span></span>

<span data-ttu-id="42502-151">NetX Duo Telnet サーバーでは、Telnet クライアントが接続を終了するたびに、アプリケーションで指定したコールバック関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="42502-151">The NetX Duo Telnet Server calls the application specified callback function whenever a Telnet Client ends the connection.</span></span> <span data-ttu-id="42502-152">このコールバック関数は、アプリケーションで ***nx_telnet_server_create*** 関数を使用して Telnet サーバーを作成するときに指定します。</span><span class="sxs-lookup"><span data-stu-id="42502-152">The application specifies the callback function when the Telnet Server is created via the ***nx_telnet_server_create*** function.</span></span> <span data-ttu-id="42502-153">“終了接続” コールバックでは通常、論理的な接続に関連付けられた各クライアント固有のデータ構造体をすべて消去します。</span><span class="sxs-lookup"><span data-stu-id="42502-153">Typical actions of the “end connection” callback include cleaning up any Client specific data structures associated with the logical connection.</span></span>

### <a name="prototype"></a><span data-ttu-id="42502-154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="42502-154">Prototype</span></span>
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a><span data-ttu-id="42502-155">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="42502-155">Input Parameters</span></span>

- <span data-ttu-id="42502-156">**server_ptr** 呼び出し元の Telnet サーバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="42502-156">**server_ptr** Pointer to the calling Telnet Server.</span></span>
- <span data-ttu-id="42502-157">**logical_connection** Telnet サーバーで使用する、内部の論理的な接続。</span><span class="sxs-lookup"><span data-stu-id="42502-157">**logical_connection** The internal logical connection for the Telnet Server.</span></span> <span data-ttu-id="42502-158">この接続は、各クライアント接続に固有のバッファーおよびデータ構造体のインデックスとしてアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="42502-158">This can be used by the application as an index into buffers and/or data structures specific for each Client connection.</span></span> <span data-ttu-id="42502-159">取り得る値の範囲は 0 から NX_TELNET_MAX_CLIENTS - 1 です。</span><span class="sxs-lookup"><span data-stu-id="42502-159">Its value ranges from 0 through NX_TELNET_MAX_CLIENTS - 1.</span></span>

## <a name="telnet-option-negotiation"></a><span data-ttu-id="42502-160">Telnet オプションのネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="42502-160">Telnet Option Negotiation</span></span>

<span data-ttu-id="42502-161">NetX Duo Telnet サーバーは Telnet オプションの一部、Echo と Supress Go Ahead をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="42502-161">The NetX Duo Telnet Server supports a limited set of Telnet options, Echo and Suppress Go Ahead.</span></span>

<span data-ttu-id="42502-162">この機能を有効にするには NX_TELNET_SERVER_OPTION_DISABLE を無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="42502-162">To enable this feature the NX_TELNET_SERVER_OPTION_DISABLE must not be defined.</span></span> <span data-ttu-id="42502-163">これは既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="42502-163">By default it is not defined.</span></span> <span data-ttu-id="42502-164">Telnet サーバーでは、Telnet オプション要求をクライアントに送信するためのパケットを、*nx_telnet_server_create* サービスで作成したパケット プールから割り当てます。</span><span class="sxs-lookup"><span data-stu-id="42502-164">The Telnet Server creates a packet pool in the *nx_telnet_server_create* service from which it allocates packets for sending telnet options requests to the Client.</span></span> <span data-ttu-id="42502-165">このパケット プールのパケットのペイロードのサイズ (NX_TELNET_SERVER_PACKET_PAYLOAD) とパケット プールそのもののサイズ (NX_TELNET_SERVER_PACKET_POOL_SIZE) の設定については「構成オプション」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="42502-165">See “Configuration Options” for setting the packet payload (NX_TELNET_SERVER_PACKET_PAYLOAD) and packet pool size (NX_TELNET_SERVER_PACKET_POOL_SIZE) for this packet pool.</span></span> <span data-ttu-id="42502-166">*nx_telnet_server_delete* サービスをび出すと、このパケット プールは削除されます。</span><span class="sxs-lookup"><span data-stu-id="42502-166">It will delete this packet pool when the *nx_telnet_server_delete* service is called.</span></span>

<span data-ttu-id="42502-167">Telnet クライアントからのオプション要求を受信していない状態で Telnet サーバーがこのクライアントに接続すると、次の Telnet オプションをクライアントに送信します:</span><span class="sxs-lookup"><span data-stu-id="42502-167">Upon making a connection with the Telnet Client, it will send out this set of telnet options to the Client if it has not received option requests from the Client:</span></span>

- <span data-ttu-id="42502-168">エコーする</span><span class="sxs-lookup"><span data-stu-id="42502-168">will echo</span></span>
- <span data-ttu-id="42502-169">エコーしない</span><span class="sxs-lookup"><span data-stu-id="42502-169">dont echo</span></span>
- <span data-ttu-id="42502-170">SGA を行う</span><span class="sxs-lookup"><span data-stu-id="42502-170">will sga</span></span>

<span data-ttu-id="42502-171">クライアントから Telnet データを受信すると、Telnet サーバーは最初のバイトが “IAC” コードであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="42502-171">When it receives Telnet data from the Client, the Telnet Server checks if the first byte is the “IAC” code.</span></span> <span data-ttu-id="42502-172">“IAC” コードである場合は、クライアント パケットにあるすべてのオプションを処理します。</span><span class="sxs-lookup"><span data-stu-id="42502-172">If so, it will process all the options in the Client packet.</span></span> <span data-ttu-id="42502-173">上のリストにないオプションは無視します。</span><span class="sxs-lookup"><span data-stu-id="42502-173">Options not in the list above are ignored.</span></span>

<span data-ttu-id="42502-174">既定では、NX_TELNET_SERVER_OPTION_DISABLE が有効になっていない状態で Telnet オプションのコマンドを送信する必要がある場合、Telnet サーバーは自身専用のパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="42502-174">By default, the Telnet Server creates its own internal packet pool if NX_TELNET_SERVER_OPTION_DISABLE is not defined and it needs to transmit Telnet option commands.</span></span> <span data-ttu-id="42502-175">Telnet サーバーのパケット プールの設定は NX_TELNET_SERVER_PACKET_PAYLOAD と NX_TELNET_SERVER_PACKET_POOLSIZE で行います。</span><span class="sxs-lookup"><span data-stu-id="42502-175">The Telnet Server packet pool is defined by NX_TELNET_SERVER_PACKET_PAYLOAD and NX_TELNET_SERVER_PACKET_POOLSIZE.</span></span> <span data-ttu-id="42502-176">ただし、NX_TELNET_SERVER_USER_CREATE_PACKET_POOL が有効である場合は、アプリケーションで Telnet サーバー用にパケット プールを作成し、 *_nx_telnet_server_packet_pool_set* を呼び出してそれを Telnet サーバーのパケット プールに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42502-176">If, however, NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined, the application must create the Telnet Server packet pool and set it as the Telnet Server packet pool by calling *_nx_telnet_server_packet_pool_set*.</span></span> <span data-ttu-id="42502-177">この関数の詳細は、チャプター 3「Telnet サービスの説明」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="42502-177">See Chapter 3 “Description of Telnet Services” for more details about this function.</span></span>

<span data-ttu-id="42502-178">NetX Duo Telnet サーバーと異なり、NetX Duo Telnet クライアントのタスク スレッドでは、Telnet サーバーから受信したオプションに対して自動で応答しません。</span><span class="sxs-lookup"><span data-stu-id="42502-178">Unlike the NetX Duo Telnet Server, the NetX Duo Telnet Client task thread does not automatically send and respond to received options from the Telnet Server.</span></span> <span data-ttu-id="42502-179">これは Telnet クライアント アプリケーションで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="42502-179">This must be done by the Telnet Client application.</span></span>

## <a name="telnet-multi-thread-support"></a><span data-ttu-id="42502-180">Telnet のマルチスレッド サポート</span><span class="sxs-lookup"><span data-stu-id="42502-180">Telnet Multi-Thread Support</span></span>

<span data-ttu-id="42502-181">NetX Duo Telnet クライアントのサービスは複数のスレッドから同時に呼び出せます。</span><span class="sxs-lookup"><span data-stu-id="42502-181">The NetX Duo Telnet Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="42502-182">ただし、特定の Telnet クライアント インスタンスに対する読み取り、書き込み要求は、1 つずつ同じスレッドから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42502-182">However, read or write requests for a particular Telnet Client instance should be done in sequence from the same thread.</span></span>

## <a name="telnet-rfcs"></a><span data-ttu-id="42502-183">Telnet に関連する RFC</span><span class="sxs-lookup"><span data-stu-id="42502-183">Telnet RFCs</span></span>

<span data-ttu-id="42502-184">NetX Duo Telnet は、RFC 854 とその他の関連 RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="42502-184">NetX Duo Telnet is compliant with RFC854 and related RFCs.</span></span>
