---
title: 第 2 章 - Azure RTOS NetX Duo DHCP サーバーのインストールと使用
description: この章では、NetX Duo DHCP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 201e8b7e245539c1780ace4c3af4bc063a8485b3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810928"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-dhcp-server"></a><span data-ttu-id="0d573-103">第 2 章 - Azure RTOS NetX Duo DHCP サーバーのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="0d573-103">Chapter 2 - Installation and use of the Azure RTOS NetX Duo DHCP server</span></span>

<span data-ttu-id="0d573-104">この章では、NetX Duo DHCP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d573-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="0d573-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="0d573-105">Product Distribution</span></span>

<span data-ttu-id="0d573-106">NetX Duo DHCP サーバーは、[https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="0d573-106">The NetX Duo DHCP Server is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="0d573-107">このパッケージにはソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています。次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0d573-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="0d573-108">**nxd_dhcp_server.h** NetX Duo DHCP サーバーのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="0d573-108">**nxd_dhcp_server.h** Header file for NetX Duo DHCP Server</span></span>
- <span data-ttu-id="0d573-109">**nxd_dhcp_server.c** NetX Duo DHCP サーバーの C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="0d573-109">**nxd_dhcp_server.c** C Source file for NetX Duo DHCP Server</span></span>
- <span data-ttu-id="0d573-110">**nxd_dhcp_server.pdf** NetX Duo DHCP サーバーのユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="0d573-110">**nxd_dhcp_server.pdf** User Guide for NetX Duo DHCP Server</span></span>
- <span data-ttu-id="0d573-111">**demo_netxduo_dhcp.c** NetX Duo DHCP サーバーのデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="0d573-111">**demo_netxduo_dhcp.c** NetX Duo DHCP Server demonstration</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="0d573-112">DHCP のインストール</span><span class="sxs-lookup"><span data-stu-id="0d573-112">DHCP Installation</span></span>

<span data-ttu-id="0d573-113">NetX Duo DHCP サーバーを使用するには、NetX Duo がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーします。</span><span class="sxs-lookup"><span data-stu-id="0d573-113">In order to use NetX Duo DHCP Server, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="0d573-114">たとえば、NetX Duo が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nxd_dhcp_server.h* および *nxd_dhpc_server.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-114">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcp_server.h* and *nxd_dhpc_server.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-dhcp-server"></a><span data-ttu-id="0d573-115">NetX Duo DHCP サーバーの使用</span><span class="sxs-lookup"><span data-stu-id="0d573-115">Using NetX Duo DHCP Server</span></span>

<span data-ttu-id="0d573-116">NetX Duo DHCP サーバーの使用方法は簡単です。</span><span class="sxs-lookup"><span data-stu-id="0d573-116">Using NetX Duo DHCP Server is easy.</span></span> <span data-ttu-id="0d573-117">基本的に、ThreadX と NetX を使用するためには、アプリケーションのコードに *tx_api.h* と *nx_api.h* をインクルードしてから *nx_dhcp_server.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-117">Basically, the application code must include *nx_dhcp_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="0d573-118">*nxd_dhcp_server.h* をインクルードすると、このガイドで後述する DHCP 関数を、そのアプリケーションのコードで呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="0d573-118">Once *nxd_dhcp_server.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="0d573-119">また、アプリケーションをビルドするときに *nxd_dhcp_server.c* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-119">The application must also include *nxd_dhcp_server.c* in the build process.</span></span> <span data-ttu-id="0d573-120">このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="0d573-121">NetX Duo DHCP サーバーの使用方法の詳細は、後の「**NetX Duo DHCP サーバーの** **要件**」および「**NetX Duo DHCP サーバーの制約**」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d573-121">For more details on using NetX Duo DHCP Server, see the following sections **Requirements of the NetX Duo DHCP** **Server** and **Constraints of the NetX Duo DHCP Server**.</span></span>

<span data-ttu-id="0d573-122">DHCP では NetX Duo UDP サービスを利用するため、DHCP を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0d573-122">Note that since DHCP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

## <a name="requirements-of-the-netx-duo-dhcp-server"></a><span data-ttu-id="0d573-123">NetX Duo DHCP サーバーの要件</span><span class="sxs-lookup"><span data-stu-id="0d573-123">Requirements of the NetX Duo DHCP Server</span></span>

<span data-ttu-id="0d573-124">NetX Duo DHCP サーバーを使用するには、UDP ソケットのポートを DHCP のウェルノウン ポート 67 に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-124">The NetX Duo DHCP Server requires a UDP socket port assigned to the well known DHCP port 67.</span></span> <span data-ttu-id="0d573-125">DHCP サーバーを作成するには、少なくとも 548 バイトのペイロードと IP、UDP、イーサネット ヘッダー (4 バイトのアライメントで合計 44 バイト) を含むパケットのプールを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-125">To create the DHCP Server, the application must create a packet pool with packet payload at least 548 bytes plus IP, UDP and Ethernet headers (which total 44 bytes with 4 byte alignment).</span></span>

<span data-ttu-id="0d573-126">サーバーとクライアントがどちらもイーサネット ハードウェア アドレスを使用することを前提にしています:</span><span class="sxs-lookup"><span data-stu-id="0d573-126">It is assumed that the Server and Client are both using Ethernet hardware address settings:</span></span>

- <span data-ttu-id="0d573-127">ハードウェアの種類: 1</span><span class="sxs-lookup"><span data-stu-id="0d573-127">Hardware type 1</span></span>
- <span data-ttu-id="0d573-128">ハードウェア アドレス長: 6</span><span class="sxs-lookup"><span data-stu-id="0d573-128">Hardware length 6</span></span>
- <span data-ttu-id="0d573-129">ホップ数: 0</span><span class="sxs-lookup"><span data-stu-id="0d573-129">Hops 0</span></span>

### <a name="multiple-client-sessions"></a><span data-ttu-id="0d573-130">複数のクライアント セッション</span><span class="sxs-lookup"><span data-stu-id="0d573-130">Multiple Client Sessions</span></span>

<span data-ttu-id="0d573-131">NetX Duo DHCP サーバーでは、アクティブな DHCP クライアントとその "状態" をテーブルで管理することにより、複数のクライアント セッションを処理することができます (DHCP の状態の例: INIT、BOOT、SELECTING、REQUESTING、RENEWING)。次のクライアント メッセージを受け取る前にセッションがタイムアウトした場合、クライアントが IP アドレスのリースにバインドされている場合を除いて、サーバーによりクライアント セッションのデータが削除され、割り当てられていた IP アドレスが使用可能なプールに戻されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-131">The NetX Duo DHCP Server can handles multiple Client sessions by keeping a table of active DHCP clients and what ‘state’ the Client is in e.g. DHCP states INIT, BOOT, SELECTING, REQUESTING, RENEWING etc. If the session time out expires before receiving the next Client message, unless that Client is bound to an IP lease, the Server will clear the Client session data and return the assigned IP address back to the available pool.</span></span> <span data-ttu-id="0d573-132">クライアントから複数の DISCOVER メッセージを受信した場合、サーバーはセッションの経過時間をリセットし、その IP アドレスを予約して、クライアントが後の REQUEST メッセージでその IP アドレスを受け入れられるようにします。</span><span class="sxs-lookup"><span data-stu-id="0d573-132">If the Server receives multiple DISCOVER messages from the same Client the Server resets the session time out and keeps the IP address reserved for the Client to accept in a subsequent REQUEST message.</span></span>

<span data-ttu-id="0d573-133">NetX Duo DHCP サーバーは、クライアントによる単一の状態の DHCP 要求も受け入れます。たとえば、クライアントが REQUEST メッセージしか送信しない場合が考えられます。</span><span class="sxs-lookup"><span data-stu-id="0d573-133">The NetX Duo DHCP Server also accepts the single state Client DHCP request e.g. the Client only sends a REQUEST message.</span></span> <span data-ttu-id="0d573-134">これは、クライアントに既に DHCP サーバーから IP アドレスのリースを割り当てられていることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="0d573-134">This assumes the Client has been previously assigned an IP lease from the DHCP server.</span></span>

### <a name="setting-interface-specific-network-parameters-server-responses"></a><span data-ttu-id="0d573-135">ネットワーク パラメーター サーバー応答をインターフェイスごとに設定する</span><span class="sxs-lookup"><span data-stu-id="0d573-135">Setting Interface Specific Network Parameters Server Responses</span></span>

<span data-ttu-id="0d573-136">アプリケーションでは、*nx_dhcp_set_interface_network_parameters* サービスを使用して、DHCP クライアント要求を処理するインターフェイスごとに、ルーター、サブネット マスク、DNS サーバーのパラメーターを設定できます。</span><span class="sxs-lookup"><span data-stu-id="0d573-136">The application can set the router, subnet mask and DNS server parameters for each interface it handles DHCP Client requests, using the *nx_dhcp_set_interface_network_parameters* service.</span></span> <span data-ttu-id="0d573-137">そうでない場合、これらのパラメーターには、それぞれ、サーバーのプライマリ インターフェイスの IP ゲートウェイ、DHCP ネットワークのサブネット、DHCP サーバーの IP アドレスが既定値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-137">Otherwise these parameters are defaulted to the IP gateway on the Server’s primary interface, its DHCP network subnet, and DHCP Server IP address, respectively.</span></span>

<span data-ttu-id="0d573-138">DHCP サーバーから DHCP クライアントに送信される DHCP メッセージのオプション データには、これらのパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d573-138">The DHCP server includes these parameters in the option data of DHCP messages it sends to DHCP clients.</span></span>

### <a name="assigning-ip-addresses-to-the-client"></a><span data-ttu-id="0d573-139">クライアントに IP アドレスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="0d573-139">Assigning IP addresses to the Client</span></span>

<span data-ttu-id="0d573-140">クライアントの DISCOVER メッセージに IP アドレスを指定する要求がない場合、DHCP サーバーは自身のプールにあるアドレスを 1 つ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d573-140">If the Client DISCOVER message does not specify a requested IP address, the DHCP Server can use one from its own pool.</span></span> <span data-ttu-id="0d573-141">使用できる IP アドレスがサーバーにない場合は、クライアントに NACK メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-141">If the Server has no available IP addresses it will send the Client a NACK message.</span></span>

<span data-ttu-id="0d573-142">その IP アドレスが使用可能で、サーバーの IP アドレス データベースに存在する場合、NetX Duo DHCP サーバーによって、クライアントの REQUEST メッセージで要求された IP アドレスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-142">The NetX Duo DHCP Server will grant the requested IP address in the Client REQUEST message as long as the IP address is available and can be found in the Server IP address database.</span></span> <span data-ttu-id="0d573-143">アプリケーションでは、*nx_dhcp_create_server_ip_address_list* サービスを使用して、DHCP クライアントに割り当てることができるサーバーの IP アドレスのリストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-143">The application creates the Server’s list of available IP addresses for assigning to DHCP Clients using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="0d573-144">要求された IP アドレスがサーバーに存在しないか別のホストに割り当てられている場合は、クライアントに NACK メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-144">If the Server does not have the requested IP addresses or it is assigned to another host it will send the Client a NACK message.</span></span>

<span data-ttu-id="0d573-145">クライアント要求を受信した DHCP サーバーにより、DHCP メッセージのクライアント MAC アドレス フィールドにあるクライアントの MAC アドレス使用して、クライアントが一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-145">When the DHCP Server receives a Client request, it identifies that Client uniquely using the Client MAC address in the Client MAC address field in the DHCP message.</span></span> <span data-ttu-id="0d573-146">クライアントが MAC アドレスを変更するか別のサブネットに移動した場合、そのクライアントはサーバーに RELEASE メッセージを送信し、使用可能なアドレスのプールに IP アドレスを戻し、INIT 状態の新たな IP アドレスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-146">If the Client changes it’s MAC address or is moved elsewhere onto another subnet it should send a RELEASE message to the Server to return the IP address back to the available pool, and request a new IP address in the INIT state.</span></span>

<span data-ttu-id="0d573-147">詳細については、「**小さなシステムの例**」セクションの図 1.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d573-147">See Figure 1.1 of the **Small Example System** section for details.</span></span> <span data-ttu-id="0d573-148">DHCP サーバー インスタンスに保存される IP アドレスの数は、DHCP サーバー制御ブロックにあるサーバー アドレスの配列で指定された数に限定され、構成可能なオプション NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-148">The number of IP addresses saved to the DHCP Server instance is limited to the size of the server address array in the DHCP Server control block, and defined by the configurable option NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span></span>

### <a name="ip-address-lease-times"></a><span data-ttu-id="0d573-149">IP アドレスのリース時間</span><span class="sxs-lookup"><span data-stu-id="0d573-149">IP Address Lease Times</span></span>

<span data-ttu-id="0d573-150">要求されたクライアントのリース時間が、構成可能なオプション NX_DHCP_DEFAULT_LEASE_TIME で指定されているサーバーの既定のリース時間より短い場合も、そのリース時間の要求は DHCP サーバーによって受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="0d573-150">The DHCP Server will also accept the request Client lease time if that lease time is less than the Server default lease time which is defined in configurable option NX_DHCP_DEFAULT_LEASE_TIME.</span></span> <span data-ttu-id="0d573-151">リース時間が無期限 (0xFFFFFFFF) である場合を除き、クライアントに割り当てられる更新時間と再バインド時間はそれぞれリース時間の 50% と 85% です。リース時間が無期限である場合は、更新時間と再バインド時間も無期限に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-151">Renewal and rebind times assigned to the Client are 50% and 85% of the lease time, respectively, unless the lease time is infinity (0xFFFFFFFF), in which case renewal and rebind times are also set to infinity.</span></span>

### <a name="dhcp-server-timeouts"></a><span data-ttu-id="0d573-152">DHCP サーバーのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="0d573-152">DHCP Server Timeouts</span></span>

<span data-ttu-id="0d573-153">DHCP サーバーには、セッションが終了していない場合に次の DHCP クライアントメッセージを待つための、ユーザーが構成可能なセッション タイムアウトのオプション NX_DHCP_CLIENT_SESSION_TIMEOUT があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-153">The DHCP Server has a user configurable session timeout, NX_DHCP_CLIENT_SESSION_TIMEOUT, for waiting for the next DHCP Client message unless the session is completed.</span></span> <span data-ttu-id="0d573-154">サーバーがクライアントから次のメッセージを受け取ると、それが以前送信されたメッセージと同じかどうかにかかわらず、タイムアウトのタイマーがリセットされます。</span><span class="sxs-lookup"><span data-stu-id="0d573-154">The time out is reset when the Server receives the next message from the Client regardless if is the same message previously sent.</span></span>

### <a name="internal-error-handling"></a><span data-ttu-id="0d573-155">内部エラーの処理</span><span class="sxs-lookup"><span data-stu-id="0d573-155">Internal error handling</span></span>

<span data-ttu-id="0d573-156">DHCP サーバーは *nx_dhcp_listen_for_messages* 関数で DHCP クライアント パケットを受信して処理します。</span><span class="sxs-lookup"><span data-stu-id="0d573-156">The DHCP Server receives and processes DHCP Client packets in the *nx_dhcp_listen_for_messages* function.</span></span> <span data-ttu-id="0d573-157">パケットが無効である場合、または DHCP サーバーで内部エラーが発生した場合、この関数による現在の DHCP クライアント パケットの処理は中止されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-157">This function will discontinue processing the current DHCP Client packet if the packet is invalid, or the DHCP Server encounters an internal error.</span></span> <span data-ttu-id="0d573-158">*nx_dhcp_listen_for_messages* からはエラー状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-158">n *x_dhcp_listen_for_messages* returns an error status.</span></span> <span data-ttu-id="0d573-159">DHCP サーバースレッドは、ThreadX スケジューラの制御を一時的に放棄し、その後でこの関数を呼び出して次の DHCP クライアント メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="0d573-159">The DHCP Server thread relinquishes control briefly of the ThreadX scheduler before calling this function to receive the next DHCP Client message.</span></span> <span data-ttu-id="0d573-160">現在のリリースは *nx_dhcp_listen_for_messages* がエラー ステータスを返した場合のログをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0d573-160">In the current release there is no logging support for error status returns from *nx_dhcp_listen_for_messages.*</span></span>

### <a name="option-55-parameter-request-list"></a><span data-ttu-id="0d573-161">オプション 55: パラメーター要求リスト</span><span class="sxs-lookup"><span data-stu-id="0d573-161">Option 55: Parameter Request List</span></span>

<span data-ttu-id="0d573-162">NetX Duo DHCP サーバーは、クライアントに返送される OFFER および DHCPACK メッセージにパラメーター要求オプション (55) のリストが読み込まれるように、オプションのセットで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-162">The NetX Duo DHCP Server must be configured with a set of options to load to Parameter Request Option (55) list in the OFFER and DHCPACK messages it transmits back to the Client.</span></span> <span data-ttu-id="0d573-163">クライアント ネットワークに不可欠な構成データをこれらのオプションに含める必要があります。既定のオプションはルーターの IP アドレス、サブネット マスク、DNS サーバーです。</span><span class="sxs-lookup"><span data-stu-id="0d573-163">These options should include network critical configuration data for the Client network and by default is defined to be router IP address, subnet mask, and DNS server.</span></span> <span data-ttu-id="0d573-164">オプションのリストは、スペース区切り形式で、ユーザーが構成可能な NX_DHCP_DEFAULT_SERVER_OPTION_LIST に指定されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-164">The option list is a space delimited list and defined in the user configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span></span> <span data-ttu-id="0d573-165">このリストに指定するオプションの数は、同じくユーザーが指定する NX_DHCP_DEFAULT_OPTION_LIST_SIZE と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-165">Note the number of options specified in this list must equal NX_DHCP_DEFAULT_OPTION_LIST_SIZE which is also user defined.</span></span>

## <a name="constraints-of-the-netx-duo-dhcp-server"></a><span data-ttu-id="0d573-166">NetX Duo DHCP サーバーの制約</span><span class="sxs-lookup"><span data-stu-id="0d573-166">Constraints of the NetX Duo DHCP Server</span></span>

### <a name="dhcp-messages"></a><span data-ttu-id="0d573-167">DHCP のメッセージ</span><span class="sxs-lookup"><span data-stu-id="0d573-167">DHCP Messages</span></span>

<span data-ttu-id="0d573-168">NetX Duo DHCP サーバーによって IP アドレスがクライアントに割り当てられる前に、その IP アドレスがネットワークの他の場所で割り当てられていないことの確認は行われません。</span><span class="sxs-lookup"><span data-stu-id="0d573-168">The NetX Duo DHCP Server does not verify that an IP address has not been assigned elsewhere on the network before granting the IP address to the Client.</span></span> <span data-ttu-id="0d573-169">複数の DHCP サーバーがある場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="0d573-169">If there are multiple DHCP servers, this can indeed be the case.</span></span> <span data-ttu-id="0d573-170">"*RFC 2131 によると、IP アドレスがネットワーク上で一意であることの確認は、クライアントで行う必要があります*" (たとえば、アドレスに ping を送信します)。</span><span class="sxs-lookup"><span data-stu-id="0d573-170">*As per RFC 2131, it is the Client’s responsibility to verify the IP address is unique on its network* (e.g. pinging the address).</span></span> <span data-ttu-id="0d573-171">そうでない場合、サーバーは、そのデータベースを更新するための IP アドレスが含まれる DECLINE メッセージを、クライアントから受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d573-171">If it is not, the Server should receive a DECLINE message with the IP address to update its database from the Client.</span></span>

<span data-ttu-id="0d573-172">NetX Duo DHCP サーバーによって FORCE_RENEW メッセージが発行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0d573-172">The NetX Duo DHCP Server does not issue FORCE_RENEW messages.</span></span> <span data-ttu-id="0d573-173">IP アドレスのリースを更新するかどうかは DHCP クライアントに任されています。</span><span class="sxs-lookup"><span data-stu-id="0d573-173">It is up to the DHCP Client to renew its IP address lease.</span></span> <span data-ttu-id="0d573-174">ただし、DHCP サーバーにより、そのデータベース内にあるすべての割り当て済み IP アドレスの残り時間が監視されています。</span><span class="sxs-lookup"><span data-stu-id="0d573-174">However, the DHCP Server monitors the time remaining on all the assigned IP addresses in its database.</span></span> <span data-ttu-id="0d573-175">IP アドレスのリース期限が切れると、その IP アドレスは使用可能な IP アドレスのプールに戻されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-175">When an IP address lease expires that IP address is returned to the pool of available IP addresses.</span></span> <span data-ttu-id="0d573-176">そのため、IP アドレスのリースを能動的に更新または再バインドするかどうかはクライアントに任されています。</span><span class="sxs-lookup"><span data-stu-id="0d573-176">Hence it is up to the Client to actively renew/rebind its IP address lease.</span></span>

<span data-ttu-id="0d573-177">クライアントに IP アドレスのリースが割り当てられる ("バインド" される) と (または既存のリースが更新されると)、セッションのデータはすぐに削除されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-177">Session data is cleared as soon as the Client either is granted (“bound”) to an IP lease (or an existing one is renewed).</span></span> <span data-ttu-id="0d573-178">クライアントのパケットが偽りである場合、または応答間にクライアントがタイムアウトした場合、セッションのデータは削除されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-178">If a Client packet proves bogus, or the Client times out between responses, session data is cleared.</span></span>

### <a name="saving-data-between-reboots"></a><span data-ttu-id="0d573-179">再起動間にデータを保存する</span><span class="sxs-lookup"><span data-stu-id="0d573-179">Saving Data Between Reboots</span></span>

<span data-ttu-id="0d573-180">DHCP 要求パラメーターなどのクライアントのデータは、NetX Duo DHCP サーバーによってクライアント レコード テーブルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-180">The NetX Duo DHCP Server saves Client data including DHCP request parameters in a Client record table.</span></span> <span data-ttu-id="0d573-181">このテーブルは不揮発性メモリには保存されないため、DHCP サーバー ホストを再起動する必要がある場合、そうした情報は再起動間で保存されません。</span><span class="sxs-lookup"><span data-stu-id="0d573-181">This table is not stored in non-volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

<span data-ttu-id="0d573-182">IP アドレスのリースのデータは、NetX Duo DHCP サーバーによって IP アドレス テーブルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-182">The NetX Duo DHCP Server saves IP address lease data in a IP address table.</span></span> <span data-ttu-id="0d573-183">このテーブルは不揮発性メモリには保存されないため、DHCP サーバー ホストを再起動する必要がある場合、そうした情報は再起動間で保存されません。</span><span class="sxs-lookup"><span data-stu-id="0d573-183">This table is not stored in non-volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

### <a name="relay-agents"></a><span data-ttu-id="0d573-184">リレー エージェント</span><span class="sxs-lookup"><span data-stu-id="0d573-184">Relay Agents</span></span>

<span data-ttu-id="0d573-185">NetX Duo DHCP サーバーではネットワーク外の DHCP 要求がサポートされていないため、その "リレー エージェント" フィールドにはすべて 0 の IP アドレスが構成されています。</span><span class="sxs-lookup"><span data-stu-id="0d573-185">The NetX Duo DHCP Server is configured with a zero IP address for the ‘Relay agent’ field because it does not support out of network DHCP requests.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="0d573-186">小さなシステムの例</span><span class="sxs-lookup"><span data-stu-id="0d573-186">Small Example System</span></span>

<span data-ttu-id="0d573-187">下の図 1.1 は、NetX Duo DHCP サーバーを簡単に使用する例を説明したものです。</span><span class="sxs-lookup"><span data-stu-id="0d573-187">An example of how easy it is to use the NetX Duo DHCP Server is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="0d573-188">この例では、DHCP のインクルード ファイル *nxd_dhcp_server.h* が 5 行目で取り込まれています。</span><span class="sxs-lookup"><span data-stu-id="0d573-188">In this example, the DHCP include file *nxd_dhcp_server.h* is brought in at line 5.</span></span> <span data-ttu-id="0d573-189">DHCP サーバー スレッドのスタック サイズ、IP スレッドのスタック サイズ、テスト スレッドのスタック サイズはすべて、7 から 13 行目で指定されています。</span><span class="sxs-lookup"><span data-stu-id="0d573-189">DHCP Server thread stack size, IP thread stack size and test thread stack size are all defined in lines 7-13.</span></span>

<span data-ttu-id="0d573-190">最初に、"*test_thread_entry*" 関数で、DHCP サーバーの停止、再起動、その後の削除を行うための、オプションのテスト スレッド タスクが作成されます (57 行目)。</span><span class="sxs-lookup"><span data-stu-id="0d573-190">First, an optional test thread task for stopping, restarting and eventually deleting the DHCP server is created with the “*test_thread_entry*” function at line 57.</span></span> <span data-ttu-id="0d573-191">DHCP サーバー制御ブロック "*dhcp_server*" が、グローバル変数として定義されます (20 行目)。</span><span class="sxs-lookup"><span data-stu-id="0d573-191">A DHCP Server control block “*dhcp_server*” is defined as a global variable at line 20.</span></span> <span data-ttu-id="0d573-192">サーバーのパケット プールは、ペイロードが少なくとも標準の DHCP メッセージと同じ大きさ (548 バイト + IP と UDP ヘッダー) のパケットで作成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0d573-192">Note that the server packet pool is created with packets having a payload at least as large as the standard DHCP message (548 bytes plus IP and UDP header bytes).</span></span> <span data-ttu-id="0d573-193">DHCP サーバー用の IP インスタンスが正常に作成された後、アプリケーションによって DHCP サーバーが作成されます (96 行目)。</span><span class="sxs-lookup"><span data-stu-id="0d573-193">After successfully creating an IP instance for the DHCP Server, the application creates the DHCP Server in line 96.</span></span> <span data-ttu-id="0d573-194">次に、アプリケーションによって、そのサーバーの IP インスタンスで UDP が有効にされます。</span><span class="sxs-lookup"><span data-stu-id="0d573-194">Next, the application enables the Server IP instance to be UDP enabled.</span></span> <span data-ttu-id="0d573-195">DHCP サーバーを起動する前に、**nx_dhcp_create_server_ip_address_list** サービスを使用して、使用可能な IP アドレスのリストが作成されます (137 行目)。</span><span class="sxs-lookup"><span data-stu-id="0d573-195">Before starting the DHCP Server, the available IP address list is created in line 137 using the **nx_dhcp_create_server_ip_address_list** service.</span></span> <span data-ttu-id="0d573-196">**nx_dhcp_set_interface_network_parameters** サービスを使用してネットワーク構成パラメーターが設定され (138 行目)、アプリケーションによって *nx_dhcp_server_start* が呼び出されると DHCP サーバーのサービスが使用可能になります (141 行目)。</span><span class="sxs-lookup"><span data-stu-id="0d573-196">The network configuration parameters are set in the following line 138 using the **nx_dhcp_set_interface_network_parameters** service, DHCP Server services become available when the application calls the *nx_dhcp_server_start* at line 141.</span></span> <span data-ttu-id="0d573-197">テスト スレッド タスクによって、DHCP サーバーの停止と再起動のデモンストレーションが行われます。</span><span class="sxs-lookup"><span data-stu-id="0d573-197">The test thread task demonstrates the use of stopping and restarting the DHCP server.</span></span>

```C
/* This is a small demo of NetX Duo DHCP Server for the high-performance NetX Duo TCP/IP stack.  */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE         2048
#define     DEMO_SERVER_STACK_SIZE  2048
#define     SERVER_IP_ADDRESS_LIST  "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD          1000
#define     PACKET_POOL_SIZE        (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK    2048


/* Define the ThreadX and NetX Duo Duo object control blocks...  */

TX_THREAD test_thread;
NX_PACKET_POOL server_pool;
NX_IP server_ip;
NX_DHCP_SERVER dhcp_server;


/* Define the counters used in the demo application...  */

ULONG state_changes;


/* Define thread prototypes.  */

void test_thread_entry(ULONG thread_input);
void nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define main entry point.  */

int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{
    CHAR    *pointer;
    UINT    status;


    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the test thread.  */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
            pointer, TEST_STACK_SIZE,  1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duosystem.  */
    nx_system_initialize();

    /* Create the DHCP Server packet pool.  */
    status =  nx_packet_pool_create(&server_pool, "NetX Main Packet Pool", PACKET_PAYLOAD,
        pointer, PACKET_POOL_SIZE);
    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error.  */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance.  */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
        0xFFFFFF00UL,  &server_pool, nx_etherDriver_mcf5485, pointer,
        R_IP_THREAD_STACK, 1);

    pointer =  pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors.  */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance.  */
    status =  nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                                     DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic.  */
    status =  nx_udp_enable(&server_ip);

    /* Check for UDP enable errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility.  */
    status =  nx_icmp_enable(&server_ip);

    /* Check for errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

   status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                                 START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

   status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                               NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                               IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server.  */
   status =  nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread.  */
void    test_thread_entry(ULONG thread_input)
{
    UINT status;
    UINT keep_spinning;


    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }


    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);


    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}

```

<span data-ttu-id="0d573-198">**図 1.1 NetX Duo DHCP サーバー アプリケーションの例**</span><span class="sxs-lookup"><span data-stu-id="0d573-198">**Figure 1.1 Example NetX Duo DHCP Server application**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="0d573-199">構成オプション</span><span class="sxs-lookup"><span data-stu-id="0d573-199">Configuration Options</span></span>

<span data-ttu-id="0d573-200">NetX Duo DHCP サーバーを構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="0d573-200">There are several configuration options for building NetX Duo DHCP Server.</span></span> <span data-ttu-id="0d573-201">次の一覧で、それぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="0d573-201">The following list describes each in detail:</span></span>

- <span data-ttu-id="0d573-202">**NX_DISABLE_ERROR_CHECKING**: このオプションを使用すると、基本的な DHCP エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-202">**NX_DISABLE_ERROR_CHECKING**: This option removes the basic DHCP error checking.</span></span> <span data-ttu-id="0d573-203">通常は、アプリケーションがデバッグされた後で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-203">It it typically used after the application is debugged.</span></span>
- <span data-ttu-id="0d573-204">**NX_DHCP_SERVER_THREAD_PRIORITY**: このオプションを使用すると、DHCP サーバー スレッドの優先順位が指定されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-204">**NX_DHCP_SERVER_THREAD_PRIORITY**: This option specifies the priority of the DHCP Server thread.</span></span> <span data-ttu-id="0d573-205">既定では、この値により DHCP スレッドは優先順位 2 で実行するように指定されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-205">By default, this value specifies that the DHCP thread runs at priority 2.</span></span>
- <span data-ttu-id="0d573-206">**NX_DHCP_TYPE_OF_SERVICE**: このオプションを使用すると、DHCP UDP 要求に必要なサービスの種類が指定されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-206">**NX_DHCP_TYPE_OF_SERVICE**: This option specifies the type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="0d573-207">既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。</span><span class="sxs-lookup"><span data-stu-id="0d573-207">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="0d573-208">**NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 要求の断片化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0d573-208">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="0d573-209">既定値は、UDP 断片化を無効にする NX_DONT_FRAGMENT です。</span><span class="sxs-lookup"><span data-stu-id="0d573-209">By default, this value is set to NX_DONT_FRAGMENT to disable UDP fragmenting.</span></span>
- <span data-ttu-id="0d573-210">**NX_DHCP_TIME_TO_LIVE**: パケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="0d573-210">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers the packet can pass before it is discarded.</span></span> <span data-ttu-id="0d573-211">既定値は 0x80 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-211">The default value is 0x80.</span></span>
- <span data-ttu-id="0d573-212">**NX_DHCP_QUEUE_DEPTH**: DHCP サーバーのソケットに保持できるパケットの数を指定します。この数を超えるとキューをフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="0d573-212">**NX_DHCP_QUEUE_DEPTH**: Specifies the number of packets that the DHCP Server socket keeps before flushing the queue.</span></span> <span data-ttu-id="0d573-213">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-213">The default value is 5.</span></span>
- <span data-ttu-id="0d573-214">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: 自身のパケット プールからパケットが割り当てられるのを待機する NetX DHCP サーバーのタイムアウト時間をタイマー ティック単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0d573-214">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: Specifies the timeout in timer ticks for the NetX DHCP Server to wait for allocate a packet from its packet pool.</span></span> <span data-ttu-id="0d573-215">既定値は NX_IP_PERIODIC_RATE です。</span><span class="sxs-lookup"><span data-stu-id="0d573-215">The default value is set to NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="0d573-216">**NX_DHCP_SUBNET_MASK**: DHCP クライアントの構成で使用するサブネット マスクです。</span><span class="sxs-lookup"><span data-stu-id="0d573-216">**NX_DHCP_SUBNET_MASK** This is the subnet mask the DHCP Client should be configured with.</span></span> <span data-ttu-id="0d573-217">既定値は 0xFFFFFF00 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-217">The default value is set to 0xFFFFFF00.</span></span>
- <span data-ttu-id="0d573-218">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: DHCP サーバーの高速タイマーがセッションの残り時間を確認し、タイムアウトしたセッションを処理するためのタイムアウト時間です。タイマー ティック単位です。</span><span class="sxs-lookup"><span data-stu-id="0d573-218">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server fast timer to check on session time remaining and handle sessions that have timed out.</span></span>
- <span data-ttu-id="0d573-219">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: DHCP サーバーの低速タイマーが IP アドレスのリースの残り時間を確認し、タイムアウトしたリースを処理するためのタイムアウト時間です。タイマー ティック単位です。</span><span class="sxs-lookup"><span data-stu-id="0d573-219">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server slow timer to check on IP address lease time remaining and handle lease that have timed out.</span></span>
- <span data-ttu-id="0d573-220">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: DHCP サーバーが次の DHCP クライアント メッセージの受信を待つ際のタイムアウト時間です。タイマー ティック単位です。</span><span class="sxs-lookup"><span data-stu-id="0d573-220">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: This is timeout period in timer ticks the DHCP Server will wait to receive the next DHCP Client message.</span></span>
- <span data-ttu-id="0d573-221">**NX_DHCP_DEFAULT_LEASE_TIME**: DHCP クライアントに割り当てる IP アドレスの秒単位のリース時間です。クライアントに割り当てる更新時間と再バインド時間を計算する際の基準でもあります。</span><span class="sxs-lookup"><span data-stu-id="0d573-221">**NX_DHCP_DEFAULT_LEASE_TIME**: This is IP Address lease time in seconds assigned to the DHCP Client, and the basis for computing the renewal and rebind times also assigned to the Client.</span></span> <span data-ttu-id="0d573-222">既定値は 0xFFFFFFFF (無期限) です。</span><span class="sxs-lookup"><span data-stu-id="0d573-222">The default value is set to 0xFFFFFFFF (infinity).</span></span>
- <span data-ttu-id="0d573-223">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: クライアントに割り当てることができる IP アドレスを保持する DHCP サーバーの配列のサイズです。</span><span class="sxs-lookup"><span data-stu-id="0d573-223">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: This is size of the DHCP Server array for holding available IP addresses for assigning to the Client.</span></span> <span data-ttu-id="0d573-224">既定値は 20 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-224">The default value is 20.</span></span>
- <span data-ttu-id="0d573-225">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: クライアントのレコードを保持する DHCP サーバーの配列のサイズです。</span><span class="sxs-lookup"><span data-stu-id="0d573-225">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: This is size of the DHCP Server array for holding Client records.</span></span> <span data-ttu-id="0d573-226">既定値は 50 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-226">The default value is 50.</span></span>
- <span data-ttu-id="0d573-227">**NX_DHCP_CLIENT_OPTIONS_MAX**: パラメーター要求リストにあるすべてのオプションを現在のセッションに保持するための DHCP クライアント インスタンス上の配列のサイズです。</span><span class="sxs-lookup"><span data-stu-id="0d573-227">**NX_DHCP_CLIENT_OPTIONS_MAX**: This is size of the array in the DHCP Client instance for holding the all the requested options in the parameter request list in the current session.</span></span> <span data-ttu-id="0d573-228">既定値は 12 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-228">The default value is 12.</span></span>
- <span data-ttu-id="0d573-229">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: 現在の DHCP クライアントに渡す DHCP サーバーの既定のオプションのリストをパラメーター要求リストに保持するバッファーです。</span><span class="sxs-lookup"><span data-stu-id="0d573-229">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: This is the buffer holding the DHCP Server’s default list of options to supply to the current DHCP Client in the parameter request list.</span></span> <span data-ttu-id="0d573-230">既定値は "1 3 6" です。</span><span class="sxs-lookup"><span data-stu-id="0d573-230">The default is “1 3 6.”</span></span>
- <span data-ttu-id="0d573-231">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: DHCP サーバーの既定のオプションのリストを保持する配列のサイズです。</span><span class="sxs-lookup"><span data-stu-id="0d573-231">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: This is the size of the array to hold the DHCP Server’s default list of options.</span></span> <span data-ttu-id="0d573-232">既定値は、3 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-232">The default value is 3.</span></span>
- <span data-ttu-id="0d573-233">**NX_DHCP_SERVER_HOSTNAME_MAX**: サーバーのホスト名を保持するバッファーのサイズです。</span><span class="sxs-lookup"><span data-stu-id="0d573-233">**NX_DHCP_SERVER_HOSTNAME_MAX**: This is size of the buffer for holding the Server host name.</span></span> <span data-ttu-id="0d573-234">既定値は 32 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-234">The default value is 32.</span></span>
- <span data-ttu-id="0d573-235">**NX_DHCP_CLIENT_HOSTNAME_MAX**: DHCP サーバーの現在のクライアント セッションにクライアント ホスト名を保持するバッファーのサイズです。</span><span class="sxs-lookup"><span data-stu-id="0d573-235">**NX_DHCP_CLIENT_HOSTNAME_MAX**: This is size of the buffer for holding the Client host name in the current DHCP Server Client session.</span></span> <span data-ttu-id="0d573-236">既定値は 32 です。</span><span class="sxs-lookup"><span data-stu-id="0d573-236">The default value is 32.</span></span>
